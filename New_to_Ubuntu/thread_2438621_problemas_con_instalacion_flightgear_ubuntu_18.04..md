---
title: "problemas con instalacion flightgear ubuntu 18.04.3"
date: 2020-03-15
forum: New to Ubuntu
---

### Post by jimyjim on 2020-03-15
Hola soy mateo, tengo 12 años y soy nuevo en ubuntu. Tengo un ordenador con:
Ubuntu 18.04.3 LTS,
memoria 7,7 GiB,
procesador Intel® Core™ i5-3570 CPU @ 3.40GHz × 4, 
graficos Intel® Ivybridge Desktop,
gnome 3.28.2,
os type 64-bit,
491,2 GB.


 Mi padre dice que si quiero usar el ordenador tengo que buscarme la vida, aqui estoy con mi primer problema:  

 Instale con ubuntu software flightgear 2017.1 y funciono.
Lo desinstale usando el software tambien

 instale flightgear 2019.1.1 con terminal y tambien funciono.

 instale una version mayor  2019.2.0 con la terminal y entonces llegaron los problemas 

 Al arrancar el programa me presenta lo siguiente:
This copy of flightgear does not include the base data files. Select a suitable folder containig a previosly download set of files.

 El lugar que sugiere la aplicacion me lleva a la pagina donde se puede bajar la aplicacion y eso me lleva a un loop.
 Queria empezar de nuevo limpio y para ello he intentado eliminar todas las previas instalaciones con todos los comandos que encontre como por ejemplo
 
sudo apt remove --autoremove flightgear

 sudo add-apt-repository -r ppa:saiarcot895/flightgear
sudo apt-get purge flightgear
sudo apt-get purge --auto-remove flightgear

 Pero sigo teniendo el icono en el escritorio y me imagino que hay mas detras porque me abre el mensaje de error de arriba.

 Y ademas ahora me da error en el terminal al instalar la version 2019.1.1 que antes no daba problemas. Esto me devuelve la terminal:

 
sudo apt-get install flightgear

 Reading package lists... Done

 Building dependency tree        
 Reading state information... Done
 You might want to run 'apt --fix-broken install' to correct these.
 The following packages have unmet dependencies:
  flightgear-data-all : Depends: flightgear-data-base (= 1:2019.2.0~9125+gitf707840b1+dfsg-0ubuntu1~ppa1) but 1:2019.1.1+dfsg-0ubuntu1~ppa1 is to be installed
                        Depends: flightgear-data-aircrafts (= 1:2019.2.0~9125+gitf707840b1+dfsg-0ubuntu1~ppa1) but it is not going to be installed
 E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
 
 
 
 
 
 
 Gracias por vuestra ayuda y paciencia

---

