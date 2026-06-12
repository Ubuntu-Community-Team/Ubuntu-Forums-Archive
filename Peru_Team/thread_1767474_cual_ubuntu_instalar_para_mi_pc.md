---
title: "cual ubuntu instalar para mi pc"
date: 2011-05-25
forum: Peru Team
---

### Post by virgoxs on 2011-05-25
tengo 3 maquinas y todas estan red en base de windows. a medida de problema de virus y el bendito antivirus que te consume ram y otros diversos problemas etc. me quiero cambiar un distro de  linux pero no se que distro. 

primero que maquinas tengo .
1 pentium 4 de 2.4ghz con 768 de ram y 64 de video integrado intel (audio integrado relateck y red)  a y tengo 2 particiones de los juales tengo 12 gb en al c y 136 gb en la d ( de lo cual no quiero hacer nada en la D porque estan mis datos importantes  video fotos documentos etc etc ) solo quiero volar la C ey utilizarla solo con linux . a driver para la impresora multifuncional Cx5900 . a aparte es necesario que este con el office 2007 (por motivos que la pc usan varias personas) y de preferencia que funcione Stepmania ese es mi juego de ocio

2 es una pentium 3 900 mghz (celeron) 320 de ram y 32 de video intel y 40 de disco duro  (tarjeta de red Dlinck lo detecta automatica el windows ) a ese que linux ponerle si se puede usar el open office ?¿ o caulquier editor de texto que funcione en red y si es posible que inicie el stepmania XD 

3 es una pentium 3  intel 500mghz (512 de cache) real con 128 de ram e video 32 intel graphic y con 5gb de disco duro (tengo otro de 5 gb en caso que suceda algo ) a esta maquina que linux poner ? y que procesador de texto darle ( y si es posible aunque lo dudo que ejecute stepmania tambien XD) 

estas reliquias  (ya se que son antiguedades) quiero que esten en red y compartiendo con la impresora  por eso una recomendacion que Linux poner y que se comparten archivos me seria una gran ayuda y muchas gracias

---

### Post by korleon on 2011-05-27
A mi me gusta Ubunutu 10.04, pero Linux Mint tambien funciona bien y no es un gran salto en el caso que debes compartir maquinas con usarios acustombrados al w*****s.   Si tienes bandwidth puedes probar varios Live CDs para ver qual te gustas mas.

DistroWatch es mi hueco favorito:

[http://distrowatch.com/index.php?language=ES](http://distrowatch.com/index.php?language=ES)

No puedo decirte exacamente qual seria el mejor para ti. pero tengo un red pequeño de maquinas simialres.  Todos tienen Ubuntu 10.04 LTS.  La maquina con conexion al www tiene apt-cacher-ng asi solo descarga actualizaciones una vez...

---

### Post by genelyk on 2011-05-27
tus maquinas no son rapidas, asi q  para la primera recomendaria XUBUNTU 8.04 y le instalas el openoffice.  no funciona stepmania  por mas q instales el direct9x  y para las otras instalale el lubuntu 10.10  y le instalas abiword eso haria yo.. y seguro si pones youtube los v ideos sonaran mas agudoss

---

### Post by Artemis3 on 2011-05-27
No entiendo porqué te recomiendan versiones tan viejas, ve con Xubuntu 11.04 (o por lo menos 10.04 LTS) para la p4 y Lubuntu 11.04 para las p3.

Si quieres jugar stepmania consigue una tarjeta nvidia, con el video intel no vas a poder.

Office 2007 funciona con wine 1.2+, pero hay que configurar un par de cosas. Es mejor que uses Libreoffice y ofrecer copias al que no lo tenga.

Las p3 son demasiado antiguas para cualquier cosa que no sea Abiword y gnumeric (el problema es la poca ram). Podrían servir para internet con Midori... Si logras aumentar la memoria de la que tiene 128m, de podrás usar Xubuntu en las 3.

Alternativamente puedes usar la imagen de [Ubuntu Minimal](https://help.ubuntu.com/community/Installation/MinimalCD), para instalar la base, y luego solamente instalar el paquete XFCE, que resultará en una distribución mas liviana.

---

### Post by virgoxs on 2011-05-27
> **Artemis3 said:**
> No entiendo porqué te recomiendan versiones tan viejas, ve con Xubuntu 11.04 (o por lo menos 10.04 LTS) para la p4 y Lubuntu 11.04 para las p3.

Si quieres jugar stepmania consigue una tarjeta nvidia, con el video intel no vas a poder.

Office 2007 funciona con wine 1.2+, pero hay que configurar un par de cosas. Es mejor que uses Libreoffice y ofrecer copias al que no lo tenga.

Las p3 son demasiado antiguas para cualquier cosa que no sea Abiword y gnumeric (el problema es la poca ram). Podrían servir para internet con Midori... Si logras aumentar la memoria de la que tiene 128m, de podrás usar Xubuntu en las 3.

Alternativamente puedes usar la imagen de [Ubuntu Minimal]("https://help.ubuntu.com/community/Installation/MinimalCD"), para instalar la base, y luego solamente instalar el paquete XFCE, que resultará en una distribución mas liviana.

a Gracias por la prontra respuesta en cuestion de la ram de 128 lo veo muy verde aumentarle XD, el ubuntu minimal pesa 9 mb ?lo gravo y se conecta internet automaticamente (lo primero que voy hacer es la prueba en la pentium 3 ) pero aparte de esta solucion e investigado algo sobre esta distribucion el archbang es realmente bueno ? como dicen algunos  pero en fin descargare los dos.
Acierto y si esoty jgadno normlamente con graficos minimos el stepmania en la pentium 4 (vere si se puede en linux)

---

### Post by genelyk on 2011-05-28
a mi parecer la  version 8.04 es mas ligera, q  la 10.04 ,  ya acabo el soporte eso si, pero  tampoco tiene un servidor q es objetivos de ataque, salvo q  tenga la NASA  en su cpu, la diferencia  entre  versiones  mayormente es el  Kernel y algunas aplicaciones, x ejemplo entre el 2.6.31 al 2.6.33 es  el driver noveu( solo sirve si tiene tarjeta nvidia), se agrega DRDB ( sirve para crear clusters de alta velocidad en AHCI), TCP Cookie Transactions, y muchas otras cosas mas q una p4 no se puede dar el lujo de correr por q son tecnologias nuevas. a  el  8.04 trae el nucleo 2.6.24 si lo actualizas lelga al 2.6.28,  ahora si quiere usar el wine 1.2 tiene q saltar a la version 10.04 , la pregunta q te haces es q ¿por q versiones antiguas? el x q las versiones cuanod salen salen con varios bugs y huecos  q no se and escubierto, asiq  con el uso  y el tiempo se van parchando y  corrigiendo esos bugs, en cambio al ser nueva la version aun falta por descubrir las fallas.
 con respecto a las rollings  release, es similiar,  siempre van a la ultima,  pero eso no indican q lo optimizan para pcs antiguas llegara el momento en que te quedes corto  de cpu, y para tus pcs, no es recomendable estar actualizando cada poco tiempo por q simplemente no es necesario.

---

### Post by JC Cheloven on 2011-05-28
> **virgoxs said:**
> 
1 pentium 4 de 2.4ghz con 768 de ram y 64 de video integrado intel (...)

2 es una pentium 3 900 mghz (celeron) 320 de ram y 32 de video intel y 40 de disco duro  (...)

3 es una pentium 3  intel 500mghz (512 de cache) real con 128 de ram e video 32 intel graphic y con 5gb de disco duro (...)



Hola, me gusta hacer funcionar ordenadores viejos. Creo que Artemis3 te ha dado buenos consejos. Te doy unas opiniones adicionales:

pc 1º.- Correrá ubuntu normal sin muchos problemas, especialmente si deshabilitas los efectos gráficos, o usas la versión 2D de unity en su caso. Podrá con libreoffice y firefox si quieres. No obstante puedes considerar xubuntu o lubuntu, que son escritorios más ligeros que gnome. En contra de ellos está el que no tienen nautilus como gestor de archivos, que te simplificaría la compartición de archivos (asumo que los archivos a compartir estarán en este pc porque es el único en que tienes espacio de disco abundante). Por otra parte, si usas lubuntu puedes instalar nautilus en él. O puedes usar lubuntu e instalar una aplicación sencilla de compartición de archivos, como por ejemplo giver.

pc 2º.- Con 320 de ram seguramente vas a tener una experiencia pobre con el ubuntu normal. Si quieres probarlo, instala usando el alternate cd, que requiere menos ram que un live cd. Si va mal, piensa en otra cosa de las que te sugiero para los otros dos pc's. Ah, y no creo que openoffice pueda correr bien aquí. Tampoco firefox, mejor piensa en epiphany, chrome o midori.

pc 3º.- Este empieza a ser un reto. Con 128 de ram y 5gb de disco duro, te recomiendo que empieces por instalar un sistema de linea de comandos (desde un alternate cd de cualquier versión de ubuntu), y luego vayas añadiendo con la conexión a red un entorno ligero de escritorio, un navegador, y las (pocas y ligeras) aplicaciones que quieras. [Aquí tienes buenas ideas]("https://help.ubuntu.com/community/Installation/LowMemorySystems"). De todas formas, en éste puede ser más adecuado algo como puppy linux. A mi me gusta mucho.

Y que no se te olvide poner swap, tanta como ram al menos (en el pc 3º mejor pon unos 300 o 400Mb).

EDIT: sobre el "ubuntu minimal image cd", no te equivoques, te instalará ubuntu normal. Sólo que en vez de tomar los paquetes de tu cd, se baja las versiones más recientes de internet. No conduce a una instalación más ligera.

---

### Post by Artemis3 on 2011-05-29
> **JC Cheloven said:**
> "ubuntu minimal image cd", no te equivoques, te instalará ubuntu normal.

Solo si lo seleccionas, Usa F4 al iniciar el CD...

[img]http://4.bp.blogspot.com/_A3pAfmaZt-Q/THicvMl1whI/AAAAAAAAAbM/Nfz96R7lXqE/s800/03-InstallCommandLineSystem.png[/img]


La versión 8.04 ya perdió soporte en el escritorio, y en el servidor en abril 2013 (desaparece el repositorio). La versión mínima para instalar debe ser la LTS actual, la 10.04. Sin embargo, Xubuntu 11.04 trae XFCE 4.8, cuyo thunar soporta gvfs a diferencia de la 4.6, que depende de gigolo. Pero también se puede instalar nautilus sin problema (aunque es mas pesado agregar cosas de gnome).

Esto es para facilidad de ver los archivos compartidos.

Yo creo que se puede instalar con el ubuntu minimal solo el paquete XFCE en las 3 PCs y le andará bien, esto para minimizar las diferencias; pero LXDE es aun mas liviano para la que tiene 128m.

El stepmania no es tan pesado, si consigues una vieja gforce4 por ahí debe servir hasta en el p3, incluso juegos 3d livianos como el Assault Cube (fps).

[img]http://assault.cubers.net/screenshots/screenshot-table.jpg[/img]

---

### Post by genelyk on 2011-05-30
yo tengo un p3 de 1Ghz con 384 Mb d ram, y tras varias pruebas me e dado cuenta q  la 8.04 era mas rapido q la 10.04 , kisas el thunar 4.8 se a mas comodo,  pero  me acuerdo q ay cosas q en el nautilus es mas pesado  en el  procesamiento.  ahora  el de red si es verdad, pero en ese tiempo se solucionaba con smbmount y se montaba una carpeta en otra ps, ahora si linux trabaha en nfs..  yo creoq es cuestion de acostumbrarse, ahora si quieres algo mas ligero  ps  a probar debian xfce  es mas leigero q xubuntu eso si te demoraras un poco mas  configurandolo pero de hay nunk se malogra XD!

---

### Post by virgoxs on 2011-05-31
hoy por ahoy ya prrobe el mandriva (este es pesado pero en fin se ve bonito a comparacion del ubuntu) el puppy me encanto su interface grafica (provando el pentium 3 con 500 mghz 128 de ram y 32 video intel graphic el ubuntu minimla me falta probarlo que version me recomendaria del ubuntu porque veo bastante y el minimal? pesa 19 gmb ? o me estoy confundiendo ? 

bueno gracias por sus pronta respuesta pero tambien dudo mucho de poner tarjea de video todas son pci y ninguna tiene agp (aunque consiga video pci son caras realmente caras ) 

a por cierto el ubuntu minimal se podra instalar o solo es un disco live (se ejecuta en el disco ) o si tambien tiene soporte para moouse serial porque el linux Archbang no lo tinene (el puppy si lo tinene)

---

### Post by genelyk on 2011-06-01
el minimal es un ubuntu nucleo , solo lo esencial  kernel y el apt-get,  ai instalalas loq necesitas

---

