---
title: "Software center error"
date: 2013-06-16
forum: New to Ubuntu
---

### Post by Dedalo on 2013-06-16
Hi there. I'm new with ubuntu and with Linux. I'm using ubuntu 11.10. Today I've tried to install furius isomount from the terminal, while reading something on the internet. So I tiped sudo apt-get install furiusisomount. An error occurred. So I tried to get it from the software center. And I found this:

Can't install or uninstall elements until you repair the package catalogue. Do you want to repair it now?

So I put yes, and then I get this error:

The operation with the package failed.

You can see it in the images.

[ATTACH=CONFIG]243868[/ATTACH]


[ATTACH=CONFIG]243867[/ATTACH]

I don't know what happened. The details in the error window says: "nstallArchives() failed: Can't exec "locale": 

No existe el archivo o el directorio at /usr/share/perl5/Debconf/Encoding.pm line 16.Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Preconfigurando paquetes ...
Can't exec "locale": No existe el archivo o el directorio at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Preconfigurando paquetes ...
Can't exec "locale": No existe el archivo o el directorio at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Preconfigurando paquetes ...
dpkg: warning: 'ldconfig' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)
dpkg: aviso: `ldconfig' no se ha encontrado en el PATH o no es ejecutable.

I'm sorry its in spanish

---

### Post by user_of_gnomes on 2013-06-16
What happens when you: 

```
sudo apt-get update
```

And then

```
 Sudo apt-get -f install
```

---

### Post by Dedalo on 2013-06-16
Hi. Thank you for your help first at all.

This is what I get after it downloaded the packages, and I think installed some, then returned an error:

```
Se instalarán los siguientes paquetes NUEVOS:  libc-bin
Se actualizarán los siguientes paquetes:
  libc6
1 actualizados, 1 se instalarán, 0 para eliminar y 499 no actualizados.
2 no instalados del todo o eliminados.
Se necesita descargar 0 B/5.296 kB de archivos.
Se utilizarán 3.273 kB de espacio de disco adicional después de esta operación.
¿Desea continuar [S/n]? s
Can't exec "locale": No existe el archivo o el directorio at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Preconfigurando paquetes ...
dpkg: aviso: `ldconfig' no se ha encontrado en el PATH o no es ejecutable.
dpkg: error: 1 programa esperado no encontrado en la RUTA o no es ejecutable.
Nota: la RUTA de root por lo general debe contener /usr/local/sbin, /usr/sbin y /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)
enzo@enzo-Inspiron-3420:~$ 
[/quote]

I can transelate the spanish part if you need it.

This is all the command sequence, just in case:
[spoiler]
[quote]enzo@enzo-Inspiron-3420:~$ sudo apt-get update[sudo] password for enzo: 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports InRelease                      
Obj [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://dell.archive.canonical.com](http://dell.archive.canonical.com) oneiric-dell InRelease                   
Obj [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                           
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg                              
Obj [http://dl.google.com](http://dl.google.com) stable Release                                        
Obj [http://dell.archive.canonical.com](http://dell.archive.canonical.com) oneiric-dell Release.gpg                 
Obj [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release.gpg                      
Obj [http://dell.archive.canonical.com](http://dell.archive.canonical.com) oneiric-dell Release                     
Obj [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Obj [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources                       
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports Release.gpg                    
Obj [http://dell.archive.canonical.com](http://dell.archive.canonical.com) oneiric-dell/public Sources              
Obj [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Obj [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner amd64 Packages                
Obj [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release                                  
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Obj [http://dell.archive.canonical.com](http://dell.archive.canonical.com) oneiric-dell/public amd64 Packages       
Obj [http://dell.archive.canonical.com](http://dell.archive.canonical.com) oneiric-dell/public i386 Packages        
Ign [http://dell.archive.canonical.com](http://dell.archive.canonical.com) oneiric-dell/public TranslationIndex     
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release                          
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports Release                        
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Sources                             
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Sources                       
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Sources                         
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Sources                       
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main amd64 Packages                      
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted amd64 Packages                
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe amd64 Packages                  
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse amd64 Packages                
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages                       
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted i386 Packages                 
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe i386 Packages                   
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse i386 Packages                 
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main TranslationIndex                    
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse TranslationIndex              
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted TranslationIndex              
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe TranslationIndex                
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Sources                     
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Sources               
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Sources                 
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Sources               
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main amd64 Packages              
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted amd64 Packages        
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe amd64 Packages          
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse amd64 Packages        
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main i386 Packages               
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted i386 Packages         
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe i386 Packages           
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse i386 Packages         
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main TranslationIndex            
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex      
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted TranslationIndex      
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe TranslationIndex        
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main Sources                   
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted Sources             
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe Sources               
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse Sources             
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main amd64 Packages            
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted amd64 Packages      
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe amd64 Packages        
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse amd64 Packages      
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main i386 Packages             
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted i386 Packages       
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe i386 Packages         
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse i386 Packages       
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main TranslationIndex          
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex    
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted TranslationIndex    
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe TranslationIndex      
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-es                      
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en                      
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-es                
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-es_AR                         
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-en                
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-es                
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-en                
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-es                  
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en                  
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Translation-en              
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Translation-en        
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Translation-en        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-es                            
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Translation-en          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-es_AR             
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main Translation-en            
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse Translation-en
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted Translation-en
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-es
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en
Ign [http://dell.archive.canonical.com](http://dell.archive.canonical.com) oneiric-dell/public Translation-es_AR
Ign [http://dell.archive.canonical.com](http://dell.archive.canonical.com) oneiric-dell/public Translation-es
Ign [http://dell.archive.canonical.com](http://dell.archive.canonical.com) oneiric-dell/public Translation-en
Leyendo listas de paquetes... Hecho
enzo@enzo-Inspiron-3420:~$ sudo apt-get -f install
Leyendo listas de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Corrigiendo dependencias... Listo
Los paquetes indicados a continuación se instalaron de forma automática y ya no son necesarios.
  gir1.2-timezonemap-1.0 gir1.2-gstreamer-0.10 efibootmgr libtimezonemap1
  libdmraid1.0.0.rc16 libdebconfclient0 user-setup rdate python-argparse
  libdebian-installer4 btrfs-tools apt-clone localechooser-data
  python-xklavier archdetect-deb dmraid python-pyicu
Utilice «apt-get autoremove» para eliminarlos.
Se instalarán los siguientes paquetes extras:
  libc-bin libc6
Paquetes sugeridos:
  glibc-doc
Se instalarán los siguientes paquetes NUEVOS:
  libc-bin
Se actualizarán los siguientes paquetes:
  libc6
1 actualizados, 1 se instalarán, 0 para eliminar y 499 no actualizados.
2 no instalados del todo o eliminados.
Se necesita descargar 0 B/5.296 kB de archivos.
Se utilizarán 3.273 kB de espacio de disco adicional después de esta operación.
¿Desea continuar [S/n]? s
Can't exec "locale": No existe el archivo o el directorio at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Preconfigurando paquetes ...
dpkg: aviso: `ldconfig' no se ha encontrado en el PATH o no es ejecutable.
dpkg: error: 1 programa esperado no encontrado en la RUTA o no es ejecutable.
Nota: la RUTA de root por lo general debe contener /usr/local/sbin, /usr/sbin y /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by arpanaut on 2013-06-16
11.10 has passed End of Life, It is no longer supported through the regular repositories.
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Your best bet would be to reinstall with 12.04 or enable the EOL repos and do an upgrade to 12.04
Whatever, backup your important data first.

---

### Post by Dedalo on 2013-06-16
Well, I bought the computer two days ago with Ubuntu, so there is no much trouble about the data. What should I do? I have never installed ubuntu before.

PS: Love Hendrix BTW.

---

### Post by fantab on 2013-06-16
> **Dedalo said:**
> Well, I bought the computer two days ago with Ubuntu, so there is no much trouble about the data. What should I do? I have never installed ubuntu before.

PS: Love Hendrix BTW.

Then no issues. Install the latest versions of Ubuntu which are: 

[Ubuntu 12.04 LTS]("http://www.ubuntu.com/download/desktop") (supported until 2017)
[Ubuntu 13.04]("http://www.ubuntu.com/download/desktop") (supported till january 2014.)

Download 64bit or 32bit depending on your processor, then check the integrity of the downloaded .iso with [MD5Sum check]("https://help.ubuntu.com/community/HowToMD5SUM") and use the recommended tool to burn it to a media of your choice DVD/USB.

Its quite easy if you only have Ubuntu. 

Good Luck...

---

### Post by arpanaut on 2013-06-16
Another option, who/where did you purchase the machine, did they offer any warranty or support?

If you are not up to the task maybe they can do the upgrade for you, but as fantab says it is actually quite easy if dealing with Ubuntu only.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by Dedalo on 2013-06-16
Yes, but I bought it through internet, to someone many kilometers away in Buenos Aires. I'm travelling to Buenos Aires in a few wakes, but if I can fix it on my own will be better. I'll be learning on the way, I want to familiarize with ubuntu, so the challenge is fine to me. Besides, with your help I think I can do it :)

I have a few questions. I downloaded a program that weights 5gb, so, it would be nice if I can save it. When I install this new version of Ubuntu, I  necessarily will lost it from the hard drive? I mean, I have to format the hd before I install it? if so, I will save it before in a dvd or something. The other thing is, what is the difference between the LTS ubuntu and the other? why one has support until 2017 and the other only till 2014? both are free? I have an intel i5, 3th generation, so I think I should download the 64bit version. Not sure. I'm sorry I'm such an ignorant about this, but I want to learn.

Thanks.

arpanaut, you will like this: [http://www.youtube.com/watch?v=kKhSHXIXmc4](http://www.youtube.com/watch?v=kKhSHXIXmc4)

---

### Post by user_of_gnomes on 2013-06-16
> I mean, I have to format the hd before I install it? if so, I will save it before in a dvd or something.

Check out CloneZilla for that. Although why do you want to save the old operating system? 11.10 is still available for download if you absolutely must have it. (Just not receiving updates any more)

> 
The other thing is, what is the difference between the LTS ubuntu and the other? why one has support until 2017 and the other only till 2014? both are free? 


Both are free. LTS means the operating system will receive updates in its current shape for 5 years, after those 5 years there will be a new version that receives 5 years of support. This is sort of aimed at (business) users for whom rapid change might mean compatibility issues arise with the software they use.

The other one is supported for 9 months, then you have to upgrade and that'll be supported for 9 months and so on. Once a new version is released, you'll be notified and asked to update. 

> I have an intel i5, 3th generation, so I think I should download the 64bit version. Not sure. I'm sorry I'm such an ignorant about this, but I want to learn.

Yes. On top of that you'll need the 64-bit version if you want to address more than 4GB of memory.

---

### Post by Dedalo on 2013-06-16
No no, it's not the OS what I want to save. I've downloaded octave, and I don't want to download it again. I'll try to do as you say and I'll install the new version, I think I'll pick up the LTS.

When I do this I'll probably come back for more support. Thank you verymuch.

---

