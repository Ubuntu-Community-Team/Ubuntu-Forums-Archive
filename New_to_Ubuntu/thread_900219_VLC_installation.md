---
title: "VLC installation"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by bamdad on 2008-08-25
hi guys i guess you all know the program called VLC. i really want to switch from windows since its almost killing me every day so im trying to shift my essential softwares. i have downloaded a vlc-0.8.1.tar.gz file (which is supposed to be the package as far as i've learned). i extracted it and there i found the INSTALL text which was giving the instructions for the installation. but in the text its been said that i cant install the software by typing "make install" but i tried doing this a couple times and got errors saying that no such command exists. i also tried using the synaptec but i could achieve anything again. i would be happy if you guys could help me. i've searched ubuntus help and this forum but couldnt find anything useful.

 thnx

*oh i forgot to add that i cant get online with my ubuntu yet. since my ADSL modem doesnt work. so i cant use the online features

---

### Post by aloshbennett on 2008-08-25
I think vlc is available under standard repositories.
If thats the case, you can install using
> sudo apt-get install vlc

---

### Post by BTMark on 2008-08-25
bamdad,

To install VLC, it should be as simple as opening up a terminal (Applications>Accesories>Terminal) and typing ```
sudo apt-get install vlc
```Another good resource for beginners is [_here_]("http://lifehacker.com/software/ubuntu/how-to-install-anything-in-ubuntu-231105.php"). Almost anything can be installed by Synaptic (System>Administration>Synaptic Package Manager), so downloading archives from vendors is usually just a waste of time!

---

### Post by Sycron on 2008-08-25
> **bamdad said:**
> hi guys i guess you all know the program called VLC. i really want to switch from windows since its almost killing me every day so im trying to shift my essential softwares. i have downloaded a vlc-0.8.1.tar.gz file (which is supposed to be the package as far as i've learned). i extracted it and there i found the INSTALL text which was giving the instructions for the installation. but in the text its been said that i cant install the software by typing "make install" but i tried doing this a couple times and got errors saying that no such command exists. i also tried using the synaptec but i could achieve anything again. i would be happy if you guys could help me. i've searched ubuntus help and this forum but couldnt find anything useful.

 thnx

*oh i forgot to add that i cant get online with my ubuntu yet. since my ADSL modem doesnt work. so i can use the online features

Yes, you can install vlc by doing what aloshbennett told you.

---

### Post by Bachstelze on 2008-08-25
The archive you downloaded contains the source code for VLC, which you will need to compile. This is not what you want, see [this](https://help.ubuntu.com/8.04/add-applications/C/index.html) for an introduction at how to install software in Ubuntu.

---

### Post by Crafty Kisses on 2008-08-25
This link may help you > [www.psychocats.net](www.psychocats.net)

Also look at my sig for the "Install Anything" option.

Both great tutorials.

---

### Post by BTMark on 2008-08-25
> **Codename said:**
> Look at my sig.


Not to get off-topic, but the "Install Anything" link is broken in your sig.

---

### Post by Crafty Kisses on 2008-08-25
> **BTMark said:**
> Not to get off-topic, but the "Install Anything" link is broken in your sig.

Yeah, MonkeyBlog has been down today. 

That's one of best tutorials to install stuff on Ubuntu.

---

### Post by bamdad on 2008-08-25
wow guys thnx alot for the fast replies. but the problem is that i cant download anything. im having the same problem installing the firmware for my conextant modem. so all i have is the .tar.gz file. in the psychocats tutorial they guy says that i can come to ubuntu forums for help on .tar.gz files :| now this is wierd

---

### Post by Sycron on 2008-08-25
> **bamdad said:**
> wow guys thnx alot for the fast replies. but the problem is that i cant download anything. im having the same problem installing the firmware for my conextant modem. so all i have is the .tar.gz file. in the psychocats tutorial they guy says that i can come to ubuntu forums for help on .tar.gz files :| now this is wierd

Open up a terminal, go to tar.gz directory and then run:
```
tar -xf *.tar.gz
./configure
make
sudo make install
```

* (in **tar -xf *.tar.gz**)  is your name of the archive

---

### Post by bamdad on 2008-08-25
thnx sycron. i tried the code but it didnt work, it said that no such file or directory as ./configure exists. and then it added that there's no rule for make to the target file or sth. i also tried downloading a vlc.deb file from ubuntus package archive but once i double clicked on the file it said that the dependancie is not met so i wasnt able to install it

---

### Post by Sycron on 2008-08-25
> **bamdad said:**
> thnx sycron. i tried the code but it didnt work, it said that no such file or directory as ./configure exists. and then it added that there's no rule for make to the target file or sth. i also tried downloading a vlc.deb file from ubuntus package archive but once i double clicked on the file it said that the dependancie is not met so i wasnt able to install it

That was about modem drivers, not vlc.

---

### Post by bamdad on 2008-08-25
ow ... right

im still working on the modem, it requires some packages which need gdebi to be installed. im downloading the required files right now. hoping this works

---

