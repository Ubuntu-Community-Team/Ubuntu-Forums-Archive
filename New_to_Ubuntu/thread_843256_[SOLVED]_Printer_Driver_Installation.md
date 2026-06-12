---
title: "[SOLVED] Printer Driver Installation"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by uzzo2 on 2008-06-28
hello all, i'm carrying this over from another thread because i'm still having problems getting my printer working, it's a brother mfc 420-cn. here's the link i followed from another post.
Here are installation instructions for your printer:
[https://help.ubuntu.com/community/Pr...rotherMfc420cn](https://help.ubuntu.com/community/Pr...rotherMfc420cn)
i did everything it told me to do and i still can't get it to work, so i went back and did it over now i'm getting what looks like some error messages so i'll post them here.
maybe the main issue is one of the drivers didn't install "cupswrappermfc420cn-1.0.2-3.i386.deb"
failed to install package it says
lpadmin: the printer or class was not found
also having trouble viewing some of my web pages, i think everything is way to big so it's getting all jumbled up. is there a way to change this?

---

### Post by plucky on 2008-06-28
uzzo2,


Are you running Hardy 8.04?

Open a terminal and post output of ```
cat /etc/lsb-release
```This will show you what version of Ubuntu you have installed.

In Hardy the Brother printer drivers are in the repositories.

Open Synaptic and search for "brother" and mark for install the boxes for "brother-cups-wrapper-extra" and "brother-lpr-drivers-extra" which are the drivers for your printer.Then Apply.

This worked for my brother DCP120C printer.

If you are running a previous version of Ubuntu then use this thread for [Installing Brother Printers[](http://ubuntuforums.org/showthread.php?t=590793)

Good Luck



Good Luck

---

### Post by uzzo2 on 2008-06-28
> **plucky said:**
> uzzo2,


Are you running Hardy 8.04?

Open a terminal and post output of ```
cat /etc/lsb-release
```This will show you what version of Ubuntu you have installed.

In Hardy the Brother printer drivers are in the repositories.

Open Synaptic and search for "brother" and mark for install the boxes for "brother-cups-wrapper-extra" and "brother-lpr-drivers-extra" which are the drivers for your printer.Then Apply.

This worked for my brother DCP120C printer.

If you are running a previous version of Ubuntu then use this thread for [Installing Brother Printers[](http://ubuntuforums.org/showthread.php?t=590793)

Good Luck



Good Luck

thanks, i performed this task and then went to my printer configuration and tried to print a test page, here is the error i received.
CUPS Server Error
There was an error during the cups operation:'client-error-document-format-not-supported'.

---

### Post by eotakos on 2008-06-28
hello everyone - i have my hp printer working but i can't find a way to print 2 sheets per page - front and back. Any ideas?

i actually tried to create another thread for this under the "howto" subforum but for some reason it isn't displayed;  that's why i'm posting here - sorry for that!

---

### Post by plucky on 2008-06-28
1)Did CUPS find the printer? 
2)And install it correctly?
3)Are you connected via USB? or Network?

Open Firefox and input into address bar ```
http://localhost:631/
```
This will open the CUPS home page and should allow you to set up your printer.
> client-error-document-format-not-supported

You might have to set up the document type.

Good Luck

---

### Post by plucky on 2008-06-28
> **eotakos said:**
> hello everyone - i have my hp printer working but i can't find a way to print 2 sheets per page - front and back. Any ideas?

i actually tried to create another thread for this under the "howto" subforum but for some reason it isn't displayed;  that's why i'm posting here - sorry for that!

Just create a **New Thread** in this forum by selecting the box "New Thread" at the top of the Index Page.

Also include some information like the model of the printer,OS version etc, so that owners of the same printer can help.Not all printers support double sided (duplex) printing.

Good Luck

---

### Post by uzzo2 on 2008-06-28
> **plucky said:**
> 1)Did CUPS find the printer? 
2)And install it correctly?
3)Are you connected via USB? or Network?

Open Firefox and input into address bar ```
http://localhost:631/
```
This will open the CUPS home page and should allow you to set up your printer.


You might have to set up the document type.

Good Luck
thanks a heap, that seemed to solve the problem, now i think i have to download the scanner driver.

---

### Post by uzzo2 on 2008-06-28
ok, downloaded the driver for the scanner and got this error when i opened it up.
Could not open "brscan2-0.2.4-0.i386.rpm"
Archive type not supported

---

### Post by plucky on 2008-06-28
> **uzzo2 said:**
> ok, downloaded the driver for the scanner and got this error when i opened it up.
Could not open "brscan2-0.2.4-0.i386.rpm"
Archive type not supported

You need the .deb file not the .rpm file.

---

### Post by uzzo2 on 2008-06-28
> **plucky said:**
> You need the .deb file not the .rpm file.
alright, that seemed to do the trick. now on to my camera and photos.

---

### Post by usafe7ret on 2008-07-14
> **plucky said:**
> uzzo2,


Are you running Hardy 8.04?

Open a terminal and post output of ```
cat /etc/lsb-release
```This will show you what version of Ubuntu you have installed.

In Hardy the Brother printer drivers are in the repositories.

Open Synaptic and search for "brother" and mark for install the boxes for "brother-cups-wrapper-extra" and "brother-lpr-drivers-extra" which are the drivers for your printer.Then Apply.

This worked for my brother DCP120C printer.

If you are running a previous version of Ubuntu then use this thread for [Installing Brother Printers[](http://ubuntuforums.org/showthread.php?t=590793)

Good Luck



Good Luck
This was exactly what I needed to read!!!  Thanks Plucky for the tip about the Synaptic search for the ...cups wrapper.

I have been struggling with getting my Brother MFC 5860CN printer connected for 2 days and this solved the issue within 3 minutes.

---

### Post by Saja on 2008-09-27
Hello,
I've got a problem with installing my Brother DCP 120c. I'm a new user and have no experiences with using ubuntu. I read a lot on the internet and I followed the instructions on this page: 

[http://eeewiki.de/index.php/Brother_DCP120C_(und_andere)_Installation](http://eeewiki.de/index.php/Brother_DCP120C_(und_andere)_Installation) 

but it is not working, I get this message in the terminal:

sabrina@Filou:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"
sabrina@Filou:~$ sudo apt-get install csh
[sudo] password for sabrina: 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Reading state information... Fertig
csh ist schon die neueste Version.
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.

sabrina@Filou:~$ sudo mkdir /var/spool/lpd
mkdir: kann Verzeichnis „/var/spool/lpd“ nicht anlegen: File exists

sabrina@Filou:~$ sudo mkdir /var/spool/lpd/MFC210C
mkdir: kann Verzeichnis „/var/spool/lpd/MFC210C“ nicht anlegen: File exists

sabrina@Filou:~$ sudo dpkg -i --force-all --force-architecture mfc210clpr-1.0.2-1.i386.deb
dpkg: Fehler beim Bearbeiten von mfc210clpr-1.0.2-1.i386.deb (--install):
 Kann auf das Archiv nicht zugreifen: No such file or directory
Fehler traten auf beim Bearbeiten von:
 mfc210clpr-1.0.2-1.i386.deb


I think the installation of the LPR driver is not correct, but I don't know what to do. I tried to remove this driver via synaptic but this is also not working, I got a message like: 

E: mfc210clpr: Unterprozess pre-removal script gab den Fehlerwert 127 zurück

I hope than anyone can help me with this!
Thanks a lot
Sabrina

---

### Post by plucky on 2008-09-28
Open a terminal and input ```
sudo apt-get remove mfc210clpr
```

The Brother printer drivers are packaged in Synaptic,so all you have to do to install them is from a terminal ```
sudo apt-get install brother-lpr-drivers-extra
sudo apt-get install brother-cups-wrapper-extra
```

Then turn on printer and go to **System > Administration > Printing** and add new printer.If it doesn't see the printer,reboot and try again.


For the scanner you have to install the .deb package from the brother website located [here](http://solutions.brother.com/linux/en_us/download_scn.html#brscan)


Good Luck

---

### Post by Saja on 2008-09-29
Hej,
thanks for the answer, but I'm afraid that it is still not working. I trid to remove the LPR driver, but this is not possible. 
I tried to install a new package on the old one but this is also not working. I still get this message:

> sabrina@Filou:~$ sudo apt-get remove mfc210clpr
[sudo] password for sabrina: 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Reading state information... Fertig
Die folgenden Pakete werden ENTFERNT:
  mfc210clpr
0 aktualisiert, 0 neu installiert, 1 zu entfernen und 0 nicht aktualisiert.
After this operation, 0B of additional disk space will be used.
Möchten Sie fortfahren [J/n]? j
(Lese Datenbank ... 129528 Dateien und Verzeichnisse sind derzeit installiert.)
Entferne mfc210clpr ...
/var/lib/dpkg/info/mfc210clpr.prerm: 3: /usr/local/Brother/inf/setupPrintcapij: not found
dpkg: Fehler beim Bearbeiten von mfc210clpr (--remove):
 [COLOR="Red"]Unterprozess pre-removal script gab den Fehlerwert 127 zurück[/COLOR]
/var/lib/dpkg/info/mfc210clpr.postinst: 3: /usr/local/Brother/inf/setupPrintcapij: not found
ln: Erzeuge symbolische Verknüpfung „/usr/lib/libbrcompij2.so.1.0“: File exists
ln: Erzeuge symbolische Verknüpfung „/usr/lib/libbrcompij2.so.1“: File exists
ln: Erzeuge symbolische Verknüpfung „/usr/lib/libbrcompij2.so“: File exists
Fehler traten auf beim Bearbeiten von:
 mfc210clpr
[COLOR="Red"]E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]
sabrina@Filou:~$ sudo apt-get install brother-lpr-drivers-extra
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Reading state information... Fertig
Die folgenden zusätzlichen Pakete werden installiert:
  a2ps brother-lpr-drivers-common psutils
Vorgeschlagene Pakete:
  emacsen-common graphicsmagick-imagemagick-compat imagemagick groff gv
  html2ps t1-cyrillic texlive-base-bin
Empfohlene Pakete:
  wdiff
Die folgenden Pakete werden ENTFERNT:
  mfc210clpr
Die folgenden NEUEN Pakete werden installiert:
  a2ps brother-lpr-drivers-common brother-lpr-drivers-extra psutils
0 aktualisiert, 4 neu installiert, 1 zu entfernen und 0 nicht aktualisiert.
Es müssen noch 0B von 3082kB Archiven geholt werden.
After this operation, 9671kB of additional disk space will be used.
Möchten Sie fortfahren [J/n]? j
(Lese Datenbank ... 129528 Dateien und Verzeichnisse sind derzeit installiert.)
Entferne mfc210clpr ...
/var/lib/dpkg/info/mfc210clpr.prerm: 3: /usr/local/Brother/inf/setupPrintcapij: not found
dpkg: Fehler beim Bearbeiten von mfc210clpr (--remove):
 Unterprozess pre-removal script gab den Fehlerwert 127 zurück
/var/lib/dpkg/info/mfc210clpr.postinst: 3: /usr/local/Brother/inf/setupPrintcapij: not found
ln: Erzeuge symbolische Verknüpfung „/usr/lib/libbrcompij2.so.1.0“: File exists
ln: Erzeuge symbolische Verknüpfung „/usr/lib/libbrcompij2.so.1“: File exists
ln: Erzeuge symbolische Verknüpfung „/usr/lib/libbrcompij2.so“: File exists
Fehler traten auf beim Bearbeiten von:
 mfc210clpr
E: Sub-process /usr/bin/dpkg returned an error code (1)
sabrina@Filou:~$ sudo apt-get install brother-cups-wrapper-extra
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Reading state information... Fertig
Die folgenden zusätzlichen Pakete werden installiert:
  a2ps brother-cups-wrapper-common brother-lpr-drivers-common
  brother-lpr-drivers-extra psutils
Vorgeschlagene Pakete:
  emacsen-common graphicsmagick-imagemagick-compat imagemagick groff gv
  html2ps t1-cyrillic texlive-base-bin
Empfohlene Pakete:
  wdiff
Die folgenden Pakete werden ENTFERNT:
  cupswrappermfc210c mfc210clpr
Die folgenden NEUEN Pakete werden installiert:
  a2ps brother-cups-wrapper-common brother-cups-wrapper-extra
  brother-lpr-drivers-common brother-lpr-drivers-extra psutils
0 aktualisiert, 6 neu installiert, 2 zu entfernen und 0 nicht aktualisiert.
Es müssen noch 0B von 3131kB Archiven geholt werden.
After this operation, 11,0MB of additional disk space will be used.
Möchten Sie fortfahren [J/n]? j
(Lese Datenbank ... 129528 Dateien und Verzeichnisse sind derzeit installiert.)
Entferne cupswrappermfc210c ...
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
Entferne mfc210clpr ...
/var/lib/dpkg/info/mfc210clpr.prerm: 3: /usr/local/Brother/inf/setupPrintcapij: not found
dpkg: Fehler beim Bearbeiten von mfc210clpr (--remove):
 Unterprozess pre-removal script gab den Fehlerwert 127 zurück
/var/lib/dpkg/info/mfc210clpr.postinst: 3: /usr/local/Brother/inf/setupPrintcapij: not found
ln: Erzeuge symbolische Verknüpfung „/usr/lib/libbrcompij2.so.1.0“: File exists
ln: Erzeuge symbolische Verknüpfung „/usr/lib/libbrcompij2.so.1“: File exists
ln: Erzeuge symbolische Verknüpfung „/usr/lib/libbrcompij2.so“: File exists
Fehler traten auf beim Bearbeiten von:
 mfc210clpr
E: Sub-process /usr/bin/dpkg returned an error code (1)
sabrina@Filou:~$ 


I'm not sure how to go on with this problem...anyone any ideas?
Thanks a lot!

---

### Post by plucky on 2008-09-29
> sabrina@Filou:~$ sudo dpkg -i --force-all --force-architecture mfc210clpr-1.0.2-1.i386.deb
dpkg: Fehler beim Bearbeiten von mfc210clpr-1.0.2-1.i386.deb (--install):
Kann auf das Archiv nicht zugreifen: No such file or directory
Fehler traten auf beim Bearbeiten von:
mfc210clpr-1.0.2-1.i386.deb

I just realised that from this command,it didn't actually install anything as it did not find the file.So I don't know why you cannot install from synaptic.

Perhaps try to repair apt-get with ```
sudo apt-get install -f
sudo apt-get update
```
and see what that gives you.

If that doesn't work then try ```
sudo dpkg --configure -a
```

If that works,then install the drivers using synaptic.

Good Luck

---

### Post by Saja on 2008-10-01
Hey everybody,

it's still the same problem. I installed all drivers (csh, LPR --> mfc210clpr-1.0.2-1.i386.deb), cupswrapper --> cupswrapperMFC210c-1.0.2-3.i386.deb) but its not printing (by the way, the scanner is fine).

I tried to delete the drivers to install them again (because install one package on the other is also not working). But I can't remove the LPR driver. It says there is an error in the pre-removal script 127 (E: mfc210clpr: Unterprozess pre-removal script gab den Fehlerwert 127 zurück). 

How can I remove the damaged LPR driver? It's not working via the terminal, it's not working via synaptic...I don't know how to solve this.

Anyone else an idea? Would be nice!

Thanks a lot
Saja

---

