---
title: "problem apt-getting libxext"
date: 2006-03-09
forum: Repositories &amp; Backports
---

### Post by ]Nbx*cmD[ on 2006-03-09
I've triyed all ways to install qt3 and all end in a requirement of removing the core or the fs from my system
this is the answer of "apt-get install libxext-dev " that is the last step to run qt3 correctly

```

Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
Se instalarán los siguientes paquetes extras:
  debianutils e2fslibs e2fsprogs gcc-4.0-base initscripts libc6 libc6-dev libc6-i686 libgcc1
  libstdc++6 libxext6 lsb-base x-dev
Paquetes sugeridos:
  gpart e2fsck-static glibc-doc manpages-dev
Los siguientes paquetes se ELIMINARÁN:
  locales lsb
Se instalarán los siguientes paquetes NUEVOS:
  gcc-4.0-base libstdc++6 libxext-dev x-dev
Se actualizarán los siguientes paquetes:
  debianutils e2fslibs e2fsprogs initscripts libc6 libc6-dev libc6-i686 libgcc1 libxext6 lsb-base
10 actualizados, 4 se instalarán, 2 para eliminar y 523 no actualizados.
Se necesita descargar 754kB/10,8MB de archivos.
Se liberarán 4313kB después de desempaquetar.
¿Desea continuar? [S/n] S
Des:1 http://ftp.funet.fi testing/main libxext6 6.9.0.dfsg.1-4 [211kB]
Des:2 http://ftp.funet.fi testing/main x-dev 6.9.0.dfsg.1-4 [251kB]
Des:3 http://ftp.funet.fi testing/main libxext-dev 6.9.0.dfsg.1-4 [292kB]
Descargados 754kB en 2s (264kB/s)
W: No se puede leer la lista de paquetes fuente http://mail.linuxvar.it testing/main Packages (/var/lib/apt/lists/mail.linuxvar.it_%7egianluca_athlon-xp_dists_testing_main_binary-i386_Packages) - stat (2 No existe el fichero o el directorio)
W: No se puede leer la lista de paquetes fuente http://mail.linuxvar.it unstable/main Packages (/var/lib/apt/lists/mail.linuxvar.it_%7egianluca_athlon-xp_dists_unstable_main_binary-i386_Packages) - stat (2 No existe el fichero o el directorio)
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas
E: Esta ejecución de la instalación requiere eliminar temporalmente el
paquete  esencial e2fsprogs debido a un bucle de Conflictos/Pre-Dependencias.
Esto  generalmente es malo, pero si realmente quiere hacerlo, active
la opción  APT::Force-LoopBreak.
E: Internal Error, Could not early remove e2fsprogs


```

and this are my sources.list


```

#deb http://ftp.funet.fi/pub/linux/mirrors/debian/ sarge main
deb http://mail.linuxvar.it/~gianluca/athlon-xp testing main
deb http://mail.linuxvar.it/~gianluca/athlon-xp unstable main
deb http://ftp.funet.fi/pub/linux/mirrors/debian/ testing main
#deb-src http://ftp.funet.fi/pub/linux/mirrors/debian/ testing main

deb http://security.debian.org/ stable/updates main

#deb http://ftp.funet.fi/pub/linux/mirrors/debian/ testing contrib

# MPLAYER
#deb http://debian.tu-bs.de/mplayer/ testing main
#deb ftp://ftp.nerim.net/debian-marillat/ testing main
#deb http://okki666.nerim.net/debian ./
#deb ftp://ftp2.de.freesbie.org/mirror/mplayer/ testing main
#deb http://tonelli.sns.it/pub/mplayer/sarge ./
deb ftp://ftp.nerim.net/debian-marillat/ testing main

# MythTV
#deb http://debian.blenke.com sarge all
#deb ftp://ftp.heise.de/pub/ct/projekte/vdr/stable/binary base/
#deb http://dijkstra.csh.rit.edu:8088/~mdz/debian unstable mythtv
#deb-src http://dijkstra.csh.rit.edu:8088/~mdz/debian unstable mythtv
deb http://dijkstra.csh.rit.edu/~mdz/debian/ unstable mythtv
deb-src http://dijkstra.csh.rit.edu/~mdz/debian/ unstable mythtv
deb http://cedar-solutions.com/ftp/debian/ stable main

deb ftp://ftp.mowgli.ch/pub/debian/ ./
deb-src ftp://ftp.mowgli.ch/pub/debian/ ./



##
deb-src http://archive.ubuntu.com/ubuntu/ warty main restricted
deb-src http://security.ubuntu.com/ubuntu/ warty-security main restricted


##
# otros mirrors debian
#deb http://ftp.freenet.de/debian-non-US/ testing main
#deb http://ftp.rediris.es/debian-non-US/ testing main
deb http://ftp.uk.debian.org/debian/ testing main
#deb http://ftp.uk.debian.org/debian/ unstable main

# PPTP
deb http://quozl.netrek.org/pptp/pptpconfig ./

```

if anybody can help me...
thanks

---

