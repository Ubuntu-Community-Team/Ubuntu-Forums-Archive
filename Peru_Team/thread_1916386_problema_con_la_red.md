---
title: "problema con la red"
date: 2012-01-27
forum: Peru Team
---

### Post by lizardo21 on 2012-01-27
Buenas, les escribo porque desde ayer que no puedo entrar a la pagina de wikipedia, mozilla y yahoo. Uso lubuntu 11.04 con speedy 50 (la mas barata) con instalación dual de win 7 (nunca lo uso) y tampoco funciona. En la cabina de mi barrio si funciona la wiki asi que trate de activar ipv6 configurando networkmanager desactivando ipv4 pero ni siquiera conectaba internet, despues active ipv6 mediante gogoc y nada.
No se si soy el unico con ese problema o si hay solucion. Las paginas de google y hotmail funcionan normalmente.
Con ifconfig me dice que mi router soporta ipv6 y con gogoc supuestamente trabaja con traceroute6 a ipv6.google.com pero ping6 no me deja.
Cada vez que trato de entrar en esas paginas me manda a un servidor en ucrania (lo rastree) lo que indicaria fallo de ipv6 pero no entiendo como no funciona con gogoc.
Espero una pronta respuesta y mi agradecimiento por anticipado.
Atentamente

---

### Post by genelyk on 2012-01-27
no comprendo nada  de lo q dice el problema,  por q activas el ipv6 si telefonica trabaja con el ipv4,  o crees q en el pakete de 50 soles te lo daran activado ?
la verdad si no entra  por q no simplemente tratast de cambiar los servidores DNS ?  o hacer ping a la de wikipedia? o por q no tratas de entrar a travez de un proxy ?? para  ver  q es telefonica quien bloquea o es la navegacion, no creo  tengas un filtro para q exactamente no te dejen entrar a esas paginas,

---

### Post by lizardo21 on 2012-01-28
Muchas gracias por la respuesta.
Muy buena información !!!!
No sabia que solo trabajaba ipv4, yo creía que este año se pasaban a ipv6
Cuando hago ping a wikipedia me sale:

PING [www.wikipedia.org](www.wikipedia.org) (212.113.36.83) 56(84) bytes of data.
64 bytes from 212.113.36.83: icmp_req=1 ttl=44 time=252 ms
64 bytes from 212.113.36.83: icmp_req=2 ttl=44 time=279 ms

que es la ip del servidor en ucrania según el ip-adress.
Tengo chromium y firefox y con los dos pasa lo mismo.
Traté a traves de la pagina server2.kproxy.com y me mostró la wikipedia, mozilla y yahoo.com.ar.
No se mucho de internet y voy a cambiar las DNS a ver que pasa.
Me olvidaba que uso la version de 64 bits, no se si eso influirá porque siempre recomiendan 32.
Y no se si será relevante pero tengo 5.74 gb de descarga de los 6 permitidos (por bajar un CD y DVD de debian 6) y no creo que me estén reduciendo la velocidad de la conexion, aunque eso no afecta la entrada a esas páginas.
Otra vez muchas gracias y perdón por ser tan desordenado.
No es mi intención molestar, sólo que me preocupó el fallo cuando antes de ayer estaba todo normal y no poder usar mi correo yahoo.
Atentamente.

---

### Post by genelyk on 2012-01-28
dices q tienes windows 7, intenta abrirlo desde ay, si funciona hay  entonces puede q mozilla  haya sido configurado para restringir esos sitios, pero si no entra entonces es problema de movistar, caballero nomas tendras q llamarlos

---

