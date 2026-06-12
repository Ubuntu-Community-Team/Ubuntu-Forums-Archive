---
title: "New to Ubuntu, Need help with drivers."
date: 2008-08-27
forum: New to Ubuntu
---

### Post by inimitablesikh on 2008-08-27
Hey, I just installed Ubuntu 8.04 the 32 bit version, I think, I didn't choose the 64 bit version so I am assuming it was 32 bit, from the official site this is the one I downloaded and burned to a CD... Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)....I have a core 2 duo but I am sure it will work fine. These are the drivers I need IDT High Definition audio codec and the Belkin N1 Wireless Desktop card driver.

All help is appreciated. Thank you. 

Also, I want to install my gfx card driver can u tell me how? this is the one i downloaded [http://www.nvidia.com/object/linux_display..._173.14.12.html](http://www.nvidia.com/object/linux_display..._173.14.12.html)

---

### Post by patrickballeux on 2008-08-27
Why are you looking for the drivers?  Your hardware is not auto detected on the live CD?

Normally, when starting a live CD, the hardware is detected.  Only the graphics cards can have a better support once Ubuntu is installed because you have access to more drivers.


For your wireless card, you can use the NDiswrapper driver that will use the Windows driver to enable you wireless card.  (But if there is a native driver, use it first...)

You NVidia card will be detected without problem.

For your sound card, I think that the updates (after the installation) will support your card.  On my Dell 1521, the CD version was not able to load the sound card, but by updating to the latest, everything was working as expected. 

Good luck!

---

### Post by EnGorDiaz on 2008-08-27
ok here are some tips my friend


if you want new themes 
go here [www.gnome-look.org](www.gnome-look.org)

goto system>preferences>appearance click install and the file must be tar.gz. also most of the themes are metacity and click customize in the theme to pick borders for your windows stuff like that

please remember with themes and to search up on google if you have trouble or on these forums 

do i need an antivirus?

yes because securtiy first my friend and also look at this thread 

[http://ubuntuforums.org/announcement.php?f=329](http://ubuntuforums.org/announcement.php?f=329)
[http://ubuntuforums.org/showthread.php?t=229128&highlight=install+avast](http://ubuntuforums.org/showthread.php?t=229128&highlight=install+avast)

they say there are no viruses for linux but you never know

also dont run this command for gods sake -.- "sudo startx"


running windows games and programs

[http://www.winehq.org/](http://www.winehq.org/) install wine first then search in google for wine doors


one tip give linux time you will adjust to it over time you might even switch back to windows but you will come back trust me


also remember this website bookmark it [www.getdeb.net](www.getdeb.net) trust me all your app's are there

remember ubuntu uses .deb not rpm or any other package except look at this page

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

ummm i guess you can travel on from here

---

### Post by inimitablesikh on 2008-08-27
EDIT: Everything is working but where can I get the windows fonts from and all also how do i install this theme [http://www.gnome-look.org/content/show.php/Overglossed+Emerald?content=74873]("http://www.gnome-look.org/content/show.php/Overglossed+Emerald?content=74873")

---

### Post by inimitablesikh on 2008-08-28
Can anyone help?

---

### Post by tuxxy on 2008-08-28
TO isntall that theme you must down emerald theme manager and then drag the downloaded tar.gz into this.

---

### Post by philinux on 2008-08-28
System>admin>Synaptic Package Manager.

Search for ubuntu restricted extras and install.

Or

Accessories Terminal

sudo apt-get install ubuntu-restricted-extras

will get you ms fonts codecs and other stuff you need.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

also click the medibuntu link below for other useful stuff.

---

### Post by inimitablesikh on 2008-08-28
Okay thanks. Also, I really want to know how do you install tar.gz files...i downloaded a program its tar.gz and i don't know how to install. How do I?

---

### Post by hyper_ch on 2008-08-28
install anything on ubuntu: [http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html) (currently down)

and for microsoft fonts install the msttcorefont pacakge.

---

### Post by inimitablesikh on 2008-08-28
SO can you tell me how to install tar.gz files?

---

### Post by inimitablesikh on 2008-08-28
this is what I am trying to install [http://www.kryogenix.org/code/jackfield/]("http://www.kryogenix.org/code/jackfield/")

---

### Post by inimitablesikh on 2008-08-29
Okay I installed it but in general how do you install tar.qz files they don't work for me!

---

