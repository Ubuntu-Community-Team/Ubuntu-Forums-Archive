---
title: "[SOLVED] How do i download stuff?"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by psychobilly freakout on 2008-10-02
I want to download programs like, itunes, java etc.How do i do that with ubuntu because everytime i try it says it cannot download.

---

### Post by freebullets on 2008-10-02
first off, windows programs will not work with linux, so say bye bye to itunes, games, etc.

To download a file from a website use
```
wget http://example.com/file.exe
```
or just download it with firefox

---

### Post by perlluver on 2008-10-02
> **psychobilly freakout said:**
> I want to download programs like, itunes, java etc.How do i do that with ubuntu because everytime i try it says it cannot download.

As for java, and flash, you can just run this in a terminal: ```
sudo apt-get install ubuntu-restricted-extras
``` or you can browse System>Administration>Synaptic and look for ubuntu-restricted-extras.

---

### Post by bigdee973 on 2008-10-02
> **psychobilly freakout said:**
> I want to download programs like, itunes, java etc.How do i do that with ubuntu because everytime i try it says it cannot download.

your not gonna be able to install .exe files because thats a Microsoft Windows binary format.  the way you install things in Ubuntu is by going to Applications>Add/remove and where it says "show:" click "supported applications" and choose "all applications" and type in either the word of the program you want OR type in a keyword such as torrent downloader,  dvd burning software or java... unfortunately itunes does not run on linux BUT there are alternatives you could use SongBird or banshee to upload music to BUT it wont upload pictures or videos AND it works for only older generation ipods...ipods such as itouch the last 2 new nanos and iphone wont work with those programs...but older ipods such as the first ipod or ipod videos will work... the other way to install stuff is with .deb files...they are like the .exe files for ubuntu.  if you want to download limewire go to [www.limewire.com](www.limewire.com) and click linux and you will have a .deb to install... OR there is also COMPILING FROM SOURCE where u could install through commandline for instance google earth...if you download it for linux its a .bin file...you will have to use TERMINAL to install it..you would cd aka change directory to the location of the .bin file and give executable permissions to that file such as... chmod +x GoogleEarthLinux.bin and then doing ./GoogleEarthLinux.bin to install..then you will have a GUI to install...or if its in the resporitories in ubuntu you could use terminal to install by typing in sudo apt-get install azureus for example or sudo apt-get install gimp for example... or if there is the source you could install by sudo make sudo install...there are easy ways and there are hard ways... these days its easy cuz linux is popular and you will mostly find it in add/remove or on the site in .deb format or as a script like .bin for example... BUT each website will most likely tell you how to install or when you download the program it will come with a readme.txt file to tell you what to do its a small lump but not so hard to understand i was a retard once who didnt know nothing but then i got use to it... but use google to find a program you want and they will teach you how to do things...its sometimes confusing but make google or the forums your best friend for specific programs or tasks

---

### Post by psychobilly freakout on 2008-10-02
Also , how do i need to download like msn ?

---

### Post by perlluver on 2008-10-02
> **psychobilly freakout said:**
> Also , how do i need to download like msn ?

For that you can use Pidgin, or AMSN, or Emesence, all in add/remove programs.

---

### Post by SuperSonic4 on 2008-10-02
Live messenger just won't work on Linux :(

However there are good msn clones. emesene and amsn are the closest in look but pidgin does stuff like aim too. KMess is good if you have a kde desktop (never tried it in gnome)

```
sudo apt-get install emesene
```
```
sudo apt-get install amsn
```
```
sudo apt-get install kmess
```

Also look on the manufacturer's website for more up to date version particularly for emesene and amsn.

---

### Post by SuperSonic4 on 2008-10-02
I'd still avoid limewire on account of security but that's a whole different topic :p

The best bet to install programs is through Add/Remove programs although some prefer the terminal

---

### Post by Joeb454 on 2008-10-02
Removed various posts in the hope of preventing this thread descending into a flamewar. If you want to discuss that topic, head over to recurring discussions :)

---

### Post by psychobilly freakout on 2008-10-02
This is what im basically getting when i want to install any messenger programs 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kmess: Depends: kdelibs4c2a (>= 4:3.5.8-1) but it is not going to be installed
         Depends: libaudio2 but it is not going to be installed
         Depends: libqt3-mt (>= 3:3.3.8-b) but it is not going to be installed
  sun-java6-jre: Depends: sun-java6-bin (= 6-06-0ubuntu1) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-06-0ubuntu1) but it is not installable
  sun-java6-plugin: Depends: sun-java6-bin (= 6-06-0ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

What am i suppose to do? I try typing the apt get but i get nothing.

---

### Post by perlluver on 2008-10-02
> **psychobilly freakout said:**
> This is what im basically getting when i want to install any messenger programs 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kmess: Depends: kdelibs4c2a (>= 4:3.5.8-1) but it is not going to be installed
         Depends: libaudio2 but it is not going to be installed
         Depends: libqt3-mt (>= 3:3.3.8-b) but it is not going to be installed
  sun-java6-jre: Depends: sun-java6-bin (= 6-06-0ubuntu1) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-06-0ubuntu1) but it is not installable
  sun-java6-plugin: Depends: sun-java6-bin (= 6-06-0ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

What am i suppose to do? I try typing the apt get but i get nothing.

Run this in a terminal: ```
sudo apt-get -f install
```

---

### Post by SuperSonic4 on 2008-10-02
```
sudo apt-get install -f 
```

As far as I know that will overrule your dependency issues. I'm surprised you'd picked kmess though, it's generally regarded as a KDE app with associated dependencies.

You could always give synaptic a try since I believe that solves dependencies before installing. I think it's in System -> Administration but it's been ages since I used gnome lol

---

### Post by psychobilly freakout on 2008-10-02
Alright so now that everything is all cleared up *cough* when i try to download any of the programs i get this :

jeremy@jeremy-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
jeremy@jeremy-desktop:~$ 
jeremy@jeremy-desktop:~$ sudo apt-get install emesene
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
jeremy@jeremy-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
jeremy@jeremy-desktop:~$ 

What exactly does requested operation requires superuser privilege mean?

Thanks for the help!

---

### Post by Joeb454 on 2008-10-02
Run ```
sudo dpkg --configure -a
``` :) That should fix it

---

### Post by perlluver on 2008-10-02
> **psychobilly freakout said:**
> Alright so now that everything is all cleared up *cough* when i try to download any of the programs i get this :

jeremy@jeremy-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
jeremy@jeremy-desktop:~$ 
jeremy@jeremy-desktop:~$ sudo apt-get install emesene
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
jeremy@jeremy-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
jeremy@jeremy-desktop:~$ 

What exactly does requested operation requires superuser privilege mean?

Thanks for the help!

```
sudo dpkg --configure -a
``` sudo is superuser.

---

### Post by psychobilly freakout on 2008-10-02
Sorry, so many problems!! When i enter the code i get an error like this :

dpkg: error processing sun-java6-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-06-0ubuntu1); however:
  Package sun-java6-bin is not installed.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-jre
 sun-java6-plugin

---

### Post by perlluver on 2008-10-02
> **psychobilly freakout said:**
> Sorry, so many problems!! When i enter the code i get an error like this :

dpkg: error processing sun-java6-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-06-0ubuntu1); however:
  Package sun-java6-bin is not installed.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-jre
 sun-java6-plugin

Sounds like you didn't accept the license for it.

---

### Post by psychobilly freakout on 2008-10-02
> **perlluver said:**
> Sounds like you didn't accept the license for it.

What license?

---

### Post by perlluver on 2008-10-02
> **psychobilly freakout said:**
> What license?

It should have popped up a lot of text while it was installing, and you had to answer OK, or I Accept.  You have to tab to them, and click, OK, and I Accept.

```
sudo apt-get install sun-java6-bin
``` and try to install it again.

---

### Post by SuperSonic4 on 2008-10-02
It comes up in the terminal with a license, it's a blue background and you use tab to pick, it's quite distinctive so I suspect you didn't find it.

Did you try looking in synaptic?

---

### Post by psychobilly freakout on 2008-10-02
OK! Finally it's downloading! now how do i get it to put it on my desktop this is what its saying :

Setting up tcl (8.4.16-1) ...

Setting up tcl8.5 (8.5.0-2ubuntu1) ...

Setting up libsnack2 (2.2.10-dfsg1-5) ...
Setting up tcltls (1.5.0.dfsg-6) ...

Setting up tk8.5 (8.5.0-3) ...

Setting up amsn (0.97+final-0ubuntu5) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

And stops from there.

---

### Post by perlluver on 2008-10-02
> **psychobilly freakout said:**
> OK! Finally it's downloading! now how do i get it to put it on my desktop this is what its saying :

Setting up tcl (8.4.16-1) ...

Setting up tcl8.5 (8.5.0-2ubuntu1) ...

Setting up libsnack2 (2.2.10-dfsg1-5) ...
Setting up tcltls (1.5.0.dfsg-6) ...

Setting up tk8.5 (8.5.0-3) ...

Setting up amsn (0.97+final-0ubuntu5) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

And stops from there.

That is good, it means it installed ok.

---

### Post by SuperSonic4 on 2008-10-02
That means it completely successfully. To jump the gun (that version of aMSN probably won't work because of M$ changing the server)

```
sudo apt-get remove amsn
``` (but don't do autoremove)

Get the latest version of aMSN here: [http://www.amsn-project.net/linux-downloads.php](http://www.amsn-project.net/linux-downloads.php) (click the second one, for tcl/tk 8.5). When that downloads (say to the desktop) type in the terminal

```
cd ~/Desktop
```
```
chmod +x amsn-0.97.2-1.tcl85.x86.package
```
```
./amsn-0.97.2-1.tcl85.x86.package
```

first code removes the repo version of amsn but not its dependencies
second code takes you to the desktop
third makes the package file executable
fourth executes it.

---

### Post by psychobilly freakout on 2008-10-02
> **SuperSonic4 said:**
> That means it completely successfully

How do i obtain the program though? It is not on my desktop?

---

### Post by perlluver on 2008-10-02
> **psychobilly freakout said:**
> How do i obtain the program though? It is not on my desktop?

Look under applications, internet and elsewhere, nothing downloads to the Desktop, except through firefox, everything else goes to the Applcations menu.

---

### Post by Joeb454 on 2008-10-02
Check the menu at the top of your screen:

Applications &#8594; Internet :)

---

### Post by psychobilly freakout on 2008-10-02
Thanks guys for your help!!

I really appreciate it!!

---

### Post by perlluver on 2008-10-02
> **psychobilly freakout said:**
> Thanks guys for your help!!

I really appreciate it!!

No problem, please mark as solved.

---

### Post by Joeb454 on 2008-10-02
> **perlluver said:**
> No problem, please mark as solved.

You can do this from Thread Tools at the top of this page :)

---

