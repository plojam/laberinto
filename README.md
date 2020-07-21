# Laberinto

Para la generación del laberinto se usaron las paredes proporcionadas en la práctica, replicándolas para formar la siguiente estructura:

![img1](/Imagenes/i1.png)

# Crear la GVR Camera Rig

Para este punto se agrego el objeto GvrEditorEmularor como padre de la cámara agregada a la escena, ubicados en la misma posición.

![img2](/Imagenes/i2.png)

# Preparando la escena para la interacción

Para esto se agrego el objeto GvrReticlePointer a la escena como hijo de la cámara, también se agrego otro objeto a la escena llamado GvrEventSystem en donde se le agregó un script llamado GvrPointerPhysicsRaycaster como componente.

![img3](/Imagenes/i3.png)

En el juego se ve de la siguiente forma:

![img4](/Imagenes/i4.png)

#Hacer que los objetos del juego sean interactivos

Para este punto se seleccionaron todos los objetos con los que se debían seleccionar (coin, key y door).

![img5](/Imagenes/i5.png)

Luego de verificar que tienen el componente collider, se agregregaron los scripts respectivos a cada objeto proporcionados en la práctica.

![img6](/Imagenes/i6.png)

Luego, a cada objeto se le agrego un evento Trigger, en donde se agrego el script al campo de este componente y se especificó que método se activara al momento de hacer click sobre el objeto.

![img7](/Imagenes/i7.png)

# Hacer la interfaz de usuario interactiva

Para este punto, se eliminó el componente Graphic Raycaster y se agregó el componente GvrPointerGraphicRaycaster proporcionado por Google VR en el objetoSingPost, luego se agregó un script con el mismo nombre del componente, además un evento trigger para activar este script cuando se de click sobre el objeto. El fin de este objeto es ser un texto que indica el fin del juego, pero, también da la posibilidad de reiniciar el juego reiniciando todo lo que se ha hecho.

![img8](/Imagenes/i8.png)

#Programar el comprometimiento de la moneda

Para esto, se ingresó al código del script coin, donde se agregaron variables del tipo GameObject con los nombres sugeridos por la práctica, luego se agrego un efecto que hace que la moneda rote sobre su eje, esto con la ayuda de Tieme.DeltaTime dentro del método update, para que la rotación sea constante. Luego, en el método llamado al momento de dar click sobre la moneda, se instancio un el efecto de la moneda proporcionado y posteriormente se elimina la moneda con el método Destroy, visualmente viéndose como la moneda hace un efecto y desaparece de la escena.

![img9](/Imagenes/i9.png)

# Programar el comportamiento de la llave

Para agregar el comportamiento de la llave al momento de ejecutar la escena, se lo hizo de la misma forma que al programar el comportamiento de la moneda, con la diferencia de utilizar los elementos respectivos de este objeto, además se agrego una variable del tipo Door, esto para referirnos al script de la puerta, donde, al momento de dar click sobre la llave, el metodo correspondiente llama a otro metodo del script Door para indicar que la puerta del tempo esta desbloqueada.

![img10](/Imagenes/i10.png)

#Programar el comportamiento de la puerta

Para programar el movimiento de la puerta, se crearon varias variables, 2 GameObject (para la puerta izquierda y la derecha), 2 AudioSource (audio de cuando la puerta está bloqueada y cuando la puerta se está abriendo), 3 variables booleanas (indicar que la puerta está bloqueada, otra que indica que se está abriendo y otra que indica que ya está abierta), 4 quaternion (posicion inicial y final de la puerta izquierda y derecha) y 2 float (tiempos que se utilizaran al momento de rotar las puertas)

![img11](/Imagenes/i11.png)

Antes de esto, se agregaron AudioSource al objeto DoorMain, estos audios indican si la puerta está bloqueada o no.

![img12](/Imagenes/i12.png)

Al momento de que este objeto es instanciado, se asignara un componente audioSource a la variable con el mismo nombre, también se definen las posiciones rotacionales de las puertas izquierda y derecha, tomando en cuenta que sus ejes de rotación tienen 90(grados para la puerta izquierda) y  -90(grados para la puerta derecha).

![img13](/Imagenes/i13.png)

También, se tiene un método Unlock que permitirá cambiar el estado de la variable locked, este método es llamado cuando la llave es recogida.

![img14](/Imagenes/i14.png)

Se tiene un método que permite reproducir el sonido cuando se intenta abrir la puerta, esto se lo logra con el método Play() propio de la variable del tipo AudioSource, cambia el estado de las variables opening y abierta, esto para que el sonido de la puerta abierta no se vuelva a reproducir y  permitir el movimiento para que la puerta se abra.

![img15](/Imagenes/i15.png)

Para finalizar con este script, en el método update se encuentra un condicional que compruebe si la puerta puede abrirse o no, si se puede abrir la puerta, se modifican las posiciones de la puerta izquierda y derecha con el comando Quaternion.Slerp, indicando la posición inicial y la final  y el tiempo que se demora en girar.

![img16](/Imagenes/i16.png)

#Programar el comportamiento SignPost

Para programar el reinicio de la escena cuando se da click sobre el objeto SignPost, se agrego un SceneManagement, con esto, se usa un metodo llamado LoadScene y se indica que escena se se debe cargar.

![img17](/Imagenes/i17.png)

Para que esto sea posible, se debe añadir la escena en el menú donde se permite realizar un build del proyecto.

![img18](/Imagenes/i18.png)