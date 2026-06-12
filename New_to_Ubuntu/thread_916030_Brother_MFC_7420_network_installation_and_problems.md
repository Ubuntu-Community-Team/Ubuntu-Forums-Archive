---
title: "Brother MFC 7420 network installation and problems afterwards"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by morocog on 2008-09-10
I need some HELP to [SIZE="4"]install[/SIZE] my Multifunction Center, specifying that [COLOR="DarkRed"][SIZE="5"]the printer is not connected to my PC,but to a windows based PC in my network[/SIZE][/COLOR], the MFC is shared and available but I follow everything STEP BY STEP but it won't work. I'm really new to Ubuntu and I have no clue on how to install my Brother MFC 7420.

[SIZE="4"]This thread is way thorough and detailed, but it won't work for me. Maybe because the MFC is connected to the network and not to my PC, who knows?![/SIZE]
[COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=105703](http://ubuntuforums.org/showthread.php?t=105703)[/COLOR]

Besides that, I've tried to install the MFC, using all the stuff in the link above, but First, I **[SIZE="4"]don't[/SIZE]** have the printer working AND every time I install something it appears this text in the Terminal:

"> 
Se encontraron errores al procesar:
 cupswrappermfc7420
E: Sub-process /usr/bin/dpkg returned an error code (1)
Un paquete no se pudo instalar. Intentado recuperarse:
Configurando cupswrappermfc7420 (2.0.1-2) ...
/usr/local/Brother/cupswrapper/cupswrapperMFC7420-2.0.1: 64: cannot create /usr/share/cups/model/MFC7420.ppd: Directory nonexistent
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
cp: no se puede efectuar `stat' sobre «/usr/share/cups/model/MFC7420.ppd»: No existe el fichero ó directorio
dpkg: error al procesar cupswrappermfc7420 (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
Se encontraron errores al procesar:
 cupswrappermfc7420
Leyendo lista de paquetes... Hecho                   
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido       
Inicializando el estado de los paquetes... Hecho
lpadmin: No existe el fichero ó directorio
Escribiendo información de estado extendido... Hecho
Construir la base de datos de etiquetas... Hecho     
familia@ale-desktop:~$ 
"
Everything goes fine with the new program but it keeps on showing this problem with the installation of the MFC.

I guess i need to clean this mess first, but I don't know how to do it,please help me at least to correct that problem with the Terminal.

---

### Post by plucky on 2008-09-11
/> usr/local/Brother/cupswrapper/cupswrapperMFC7420-2.0.1: 64: cannot create /usr/share/cups/model/MFC7420.ppd: Directory nonexistent

To fix this problem,create an empty directory ```
gksudo gedit /usr/share/cups/model/MFC7420.ppd
``` save the file and exit from gedit.

Then from the terminal run ```
sudo apt-get -f install
```

Not sure about printing to a Windows box,but found this [page](https://help.ubuntu.com/community/WindowsXPPrinter)

and this [page](https://wiki.ubuntu.com/BrotherDriverPackaging?highlight=(brother)).
 See near the bottom of page for info on network printing.


Good Luck

---

