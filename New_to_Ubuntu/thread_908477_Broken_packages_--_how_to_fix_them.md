---
title: "Broken packages -- how to fix them?"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by Halsnalle on 2008-09-02
When I try to upgrade Ubuntu, I get a message that I've got broken packages, but I can't seem to fix them in Synaptic. I just get the following error message:

> E: /var/cache/apt/archives/openoffice.org-core_1%3a2.4.1-1ubuntu2_i386.deb: misslyckades i buffer_write(handtag) (10, ret=-1)

The broken packages all seem to be related to OpenOffice (the package I can't update nor repair is openoffice.org-core).

Any suggestions?

---

### Post by bumanie on 2008-09-02
Try > sudo dpkg --configure -ain terminal

---

### Post by Halsnalle on 2008-09-02
Thanks! dpkg says that a dependency problem prevents configuration of openoffice.org. So I guess I should change my version of openoffice.org-core according to the following. But how do I do *that*?

> dpkg: beroendeproblem förhindrar konfigurering av openoffice.org:
 openoffice.org beror på openoffice.org-core (= 1:2.4.1-1ubuntu2), men:
  Versionen av openoffice.org-core på systemet är 1:2.4.1-1ubuntu1.
dpkg: fel vid hantering av openoffice.org (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av openoffice.org-evolution:
 openoffice.org-evolution beror på openoffice.org-core (= 1:2.4.1-1ubuntu2), men:
  Versionen av openoffice.org-core på systemet är 1:2.4.1-1ubuntu1.
dpkg: fel vid hantering av openoffice.org-evolution (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av openoffice.org-gnome:
 openoffice.org-gnome beror på openoffice.org-core (= 1:2.4.1-1ubuntu2), men:
  Versionen av openoffice.org-core på systemet är 1:2.4.1-1ubuntu1.
dpkg: fel vid hantering av openoffice.org-gnome (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av openoffice.org-impress:
 openoffice.org-impress beror på openoffice.org-core (= 1:2.4.1-1ubuntu2), men:
  Versionen av openoffice.org-core på systemet är 1:2.4.1-1ubuntu1.
dpkg: fel vid hantering av openoffice.org-impress (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av openoffice.org-officebean:
 openoffice.org-officebean beror på openoffice.org-core (= 1:2.4.1-1ubuntu2), men:
  Versionen av openoffice.org-core på systemet är 1:2.4.1-1ubuntu1.
dpkg: fel vid hantering av openoffice.org-officebean (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av openoffice.org-base:
 openoffice.org-base beror på openoffice.org-core (= 1:2.4.1-1ubuntu2), men:
  Versionen av openoffice.org-core på systemet är 1:2.4.1-1ubuntu1.
dpkg: fel vid hantering av openoffice.org-base (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av openoffice.org-math:
 openoffice.org-math beror på openoffice.org-core (= 1:2.4.1-1ubuntu2), men:
  Versionen av openoffice.org-core på systemet är 1:2.4.1-1ubuntu1.
dpkg: fel vid hantering av openoffice.org-math (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av openoffice.org-draw:
 openoffice.org-draw beror på openoffice.org-core (= 1:2.4.1-1ubuntu2), men:
  Versionen av openoffice.org-core på systemet är 1:2.4.1-1ubuntu1.
dpkg: fel vid hantering av openoffice.org-draw (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av openoffice.org-gtk:
 openoffice.org-gtk beror på openoffice.org-core (= 1:2.4.1-1ubuntu2), men:
  Versionen av openoffice.org-core på systemet är 1:2.4.1-1ubuntu1.
dpkg: fel vid hantering av openoffice.org-gtk (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av openoffice.org-calc:
 openoffice.org-calc beror på openoffice.org-core (= 1:2.4.1-1ubuntu2), men:
  Versionen av openoffice.org-core på systemet är 1:2.4.1-1ubuntu1.
dpkg: fel vid hantering av openoffice.org-calc (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av openoffice.org-filter-binfilter:
 openoffice.org-filter-binfilter beror på openoffice.org-core (= 1:2.4.1-1ubuntu2), men:
  Versionen av openoffice.org-core på systemet är 1:2.4.1-1ubuntu1.
dpkg: fel vid hantering av openoffice.org-filter-binfilter (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av openoffice.org-writer:
 openoffice.org-writer beror på openoffice.org-core (= 1:2.4.1-1ubuntu2), men:
  Versionen av openoffice.org-core på systemet är 1:2.4.1-1ubuntu1.
dpkg: fel vid hantering av openoffice.org-writer (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av python-uno:
 python-uno beror på openoffice.org-core (= 1:2.4.1-1ubuntu2), men:
  Versionen av openoffice.org-core på systemet är 1:2.4.1-1ubuntu1.
dpkg: fel vid hantering av python-uno (--configure):
 beroendeproblem - lämnar okonfigurerad
Fel uppstod vid hantering:
 openoffice.org
 openoffice.org-evolution
 openoffice.org-gnome
 openoffice.org-impress
 openoffice.org-officebean
 openoffice.org-base
 openoffice.org-math
 openoffice.org-draw
 openoffice.org-gtk
 openoffice.org-calc
 openoffice.org-filter-binfilter
 openoffice.org-writer
 python-uno


---

### Post by Kevbert on 2008-09-02
To repair package, try
```
sudo apt-get install -f
```

---

### Post by bumanie on 2008-09-02
Do you have all your /etc/apt/sources.list up to date and enabled? Check by going to System --> Administration --> Software Sources and check the first 4 boxes. Then go to third party software and check the boxes there. Then in terminal > sudo apt-get updateand see if you get some downloads made available. Open office core is usually updated via the ubuntu fixes/updates, which is why I wonder whether your sources.list may not be up to date or possibly enabled.

---

### Post by Halsnalle on 2008-09-02
Okay, have checked all boxes suggested. When I close Software Sources, I get the warning about broken packages again.

"Sudo apt-get update" does not seem to find any new available updates to download. 

@Kevbert: I get the following output. It seems to choke upon unpacking the replacing openoffice.org-core, complaining that the unit is full (?) and that a subprocess paste is killed by signal (broken pipe), etc.

> Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
Korrigerar beroenden.... Färdig
Följande paket har installerats automatiskt och är inte längre nödvändiga:
  xserver-xorg-video-amd libdns32
Använd "apt-get autoremove" för att ta bort dem.
Följande ytterligare paket kommer att installeras:
  openoffice.org-core
Följande paket kommer att uppgraderas:
  openoffice.org-core
1 uppgraderade, 0 nyinstallerade, 0 att ta bort och 0 ej uppgraderade.
13 ej helt installerade eller borttagna.
Behöver hämta 0B/26,8MB arkiv.
Efter denna åtgärd kommer 81,9kB diskutrymme att frigöras.
Vill du fortsätta [J/n]? J
(Läser databasen ... 146817 filer och kataloger installerade.)
Förbereder att ersätta openoffice.org-core 1:2.4.1-1ubuntu1 (med .../openoffice.org-core_1%3a2.4.1-1ubuntu2_i386.deb) ...
Packar upp ersättande openoffice.org-core ...
dpkg: fel vid hantering av /var/cache/apt/archives/openoffice.org-core_1%3a2.4.1-1ubuntu2_i386.deb (--unpack):
 misslyckades i buffer_write(handtag) (10, ret=-1): bakändan dpkg-deb under "./usr/lib/openoffice/program/libsvx680li.so": Enheten är full
dpkg-deb: underprocess paste dödad av signal (Brutet rör)
Fel uppstod vid hantering:
 /var/cache/apt/archives/openoffice.org-core_1%3a2.4.1-1ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by bumanie on 2008-09-02
Kevbert's code is for a forced install of the OO core, as that has not worked - not sure what to suggest next - as it would have been my next suggestion. May be you should put in a bug report to launchpad and see if they have a fix or work-around. Had a qucik look at launchpad and there doesn't seem to be a similar problem having been logged. For interest provide output of > df -h /> df -h /homeWant to check how much room your / and /home partition has.

---

### Post by Halsnalle on 2008-09-02
> **bumanie said:**
> Want to check how much room your / and /home partition has.

Okay, turns out the problem was that I'd run out of space:

> Filsystem            Storlek Anvnt Tillg Anv% Monterat på
/dev/sda3             5,1G  5,1G     0 100% /
johan@johan-laptop:~$ df -h /home
Filsystem            Storlek Anvnt Tillg Anv% Monterat på
/dev/sda3             5,1G  5,1G     0 100% /


So, a simple "sudo apt-get clean" freed enough space to get the "sudo apt-get install -f" to work, and now I've successfully replaced the borken openoffice.org-core package.

For a newbie, though, it was not precisely obvious (obviously) from warning messages etc that the problem was simply a lack of space... I guess I should expand my Ubuntu partition (I'm slowly migrating from Mac OS X).

Thanks for the help, both of you!

---

### Post by Kevbert on 2008-09-03
This problem with lack of space on hard drives seems to be cropping up more and more often.  It might be worth raising a bug report on launchpad as the symptoms and error messages don't immediately make it obvious that you've run out of resources.

---

