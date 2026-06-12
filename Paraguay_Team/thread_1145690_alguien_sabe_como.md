---
title: "alguien sabe como?"
date: 2009-05-01
forum: Paraguay Team
---

### Post by oscarozuna on 2009-05-01
buenas noches senores, la verdad que ya he leido muchiiiiiiiiiiiiiisimo en todos los foros y ya he intentado de todo, sinceramente estoy a punto de darme por vencido.. jeje.. el tema es que quiero montar un servidor en mi casa, un servidor web y ftp para ser mas especifico.. aparte de eso necesito acceder remotamente a mi pc y a la red local (LAN) para poder tener acceso a una IPCAM, pero parece imposible, ya que todo lo que hago no me resulta.. trato de conectarme via ssh, escritorio remoto y nada de nada.. estoy muy cabisbajo porque veo que muchas personas si consiguen conectarse.. me gustaria que me guien paso a paso como hacerlo desde cero acompanandome en todas mis burradas y errores.. para comenzar, de tanto que ya he tratado de conectarme hasta estoy dudando cual es mi ip (solo para que tengan una idea de lo frustrante que esta siendo). les paso lo que tengo..

-pc intel pentium 4 con 2gb de ram y 250 de disco duro (para el servidor)
-ubuntu 8.10
-router kaiomy apr-4p
-ipcam airlive
-2 laptops (que se conectaran via wifi al router)

me gustaria que el servido web, tambien pueda ser utilizado como servidor en la red local si es posible, o todavia mejor si internet llegase a este servidor via lan y este distribuyese internet a los demas ordenadores de la red via wifi, que se conecte al router y los demas pcs al router.. o de la forma que sea mas conveniente..

les pido encarecidamente ayuda, ya que son mi unica esperanza.. un abrazo gente y espero respuestas..

---

### Post by PhrygianCat on 2009-05-01
Lo que tiene que hacer todo esto paso a paso. No se puede pedir a todas esas preguntas a la vez. ¿Cuál quieres hacer primero?

---

### Post by oscarozuna on 2009-05-01
muchas gracias por responder tan rapido..

bueno, primero me gustaria poder acceder a mi pc y a mi red local via internet..

---

### Post by PhrygianCat on 2009-05-01
Ir a sistema, preferencias de escritorio remoto. Luego de escritorio remoto para permitir a su equipo. Después de eso, lo que tiene que hacer asignación de puertos en tu router para el equipo en casa. Esto es asumiendo que usted tiene una IP estática para su red de conexión a Internet.

---

### Post by oscarozuna on 2009-05-01
la verdad que si fuese tan simple ya lo habria logrado.. el escritorio remoto consigo utilizar dentro de la red local, el problema es al querer acceder desde internet, mira, supongamos que no tenga un router, que mi pc este directamente a internet.. mi ip seria aquella que puse en la configuracion de red como mi ip vd? por ejemplo

ip: 10.201.115.xxx

o a cual ip es la que me tengo que conectar? empecemos por ahi, llegar a mi equipo desde afuera y comprobar que realmente estoy consiguiendo llegar, o sino es lo mismo que nada al final.. quiero mas detalles, hasta los minimos si se puede.. gracias por la paciencia..

---

### Post by PhrygianCat on 2009-05-01
Si desea saber qué dirección IP usar, usted puede ir a [http://whatismyipaddress.com/](http://whatismyipaddress.com/)

---

### Post by oscarozuna on 2009-05-02
muchas gracias por la respuesta.. bueno, cuando voy a esa direccion me pasa una ip que no es la que yo he configurado en mi maquina, parece una mezcla de la ip que configure con el dns.. pero es a esa que me muestra en esa pagina la ip a la que me tengo que conectar?

---

### Post by PhrygianCat on 2009-05-02
Es el equipo configurado para utilizar DHCP? Si la dirección IP que vea en [http://whatismyipaddress.com](http://whatismyipaddress.com) no es la misma con lo que se obtiene a partir de ifconfig, entonces es un dispositivo que funciona como un router en su LAN.

---

