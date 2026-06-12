---
title: "Some doubts as a new comer"
date: 2014-02-14
forum: New to Ubuntu
---

### Post by David_PS on 2014-02-14
Hi,

I am a newbie here. This will be my first (L)Ubuntu install. I have extensively used Fedora and openSUSE as well as PC-BSD and some hands on experience with CentOS and aLinux. So, I don't know about the repositories, install process etc with Ubuntu. Here are my questions.

1. I have a laptop with Celeron dual core (IVY) 1.6 GHz + 2GB RAM + 500GB HDD + touchscreen. Which desktop environment should I install to have a good usable system (KDE/Unity/Gnome/LXDE)?
2. Can anyone tell me a place where I can find step-by-step installation guide for UEFI/GPT based systems?
3. If I am installing Lubuntu, can I install tools like Libre office, Java, Audacity and games like Freeciv directly through repository? If so how?

I have searched a lot. But couldn't get satisfied with answers. Please help me out. If you feel this question is redundant, please forgive8-[

---

### Post by Vladlenin5000 on 2014-02-14
1. IMO, the specs are enough to run any but, as usual, lightweight is recommended and the general consensus will probably tend towards LXDE.
2. [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
3. Yes. Just search the apps in Lubuntu Software Center or install Synaptic or install them manually in the command line as usual.

---

### Post by David_PS on 2014-02-14
One more question, which is best? GPT or MBR? If GPT, can you give me a link for that? Will Lubuntu and Ubuntu installation process differ largely here?

---

### Post by Vladlenin5000 on 2014-02-14
The installation is similar in all aspects. The difference is only in the packages installed and resulting desktop environment. 
GPT is what you find in drives over 2TB instead of MBR.

---

### Post by G_Ajith_Kumar on 2014-02-14
Hi David, One can add the repositories to the Software Center directly and have all the required Programs loaded and set up from there. Here is an example of adding Lubuntu-desktop repository to the installed environment. One needs to replace the packages details in this command for each repository he needs to install. These may not be updated automatically and so one would need to update these packages with the update commands.

```
sudo apt-add-repository ppa:lubuntu-desktop/ppa
sudo apt-get update
sudo apt-get install lubuntu-software-center
```

The ppa repository details  are given in web page of each of the package.. one can google " how to install xxxxx package in Lubuntu" and get the details including the terminal commands.

More about configuring Lubuntu here: [https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides)

Good Luck. :)

---

### Post by ian-weisser on 2014-02-14
> **David_PS said:**
> 1. I have a laptop with Celeron dual core (IVY) 1.6 GHz + 2GB RAM + 500GB HDD + touchscreen. Which desktop environment should I install to have a good usable system (KDE/Unity/Gnome/LXDE)?
3. If I am installing Lubuntu, can I install tools like Libre office, Java, Audacity and games like Freeciv directly through repository? If so how?

The install .iso for each flavor of Ubuntu includes a Live media to try different desktop environments and to play with the package manager. The only way you can know your best experience is by trying them. They are *all* good, and your hardware should have no problem with any.

---

### Post by deadflowr on 2014-02-14
> 3. If I am installing Lubuntu, can I install tools like Libre office,  Java, Audacity and games like Freeciv directly through repository? If so  how?

I believe Lubuntu has it's own software center, which from where you can install all those and more.

---

### Post by walterorlin on 2014-02-17
Lubuntu also has synaptic package manager and you can use apt-get if you really wanted to.

---

### Post by David_PS on 2014-02-20
Thanks for all the encouraging replies and ideas. Here is my story:
1. Installed Ubuntu 12.04 LTS standard flavor with Unity 3D.
2. Fully UEFI and GPT based installation. I wiped everything and started like we do with a newly assembled desktop.
3. It was so painful to just wipe windows 8 out. Was beating around the bush for 40 minutess before I was able to boot and install Ubuntu.
4. Also installed LXDE through Software Center. Default install was just 1.5GB
5. Touchscreen, bluetooth, wi-fi, LAN, keyboard shorcuts everything works out of the box
6. Unity is much like Gnome and LXDE like KDE (I am from those two universes). So I like them both
7. Missing "su". I am used to it a lot. Also getting comfortable with apt-get instead of yum and zypper.
8. Battery performance is lesser. I have not used Win 8 in this laptop. But the specs said battery will last for 4 hours, while Ubuntu estimates it to 3 hours with full charge (with wi-fi, bluetooth turned off and brightness reduced)
9. Installed powertop. Seems working fine for now.
10. Tried both TLP and Jupiter. Both messed up with brightness control. So removed them.
11. Brightness control keys not working in LXDE and using 'xbacklight -dec' for the same
12. Using acpi_backlight=vendor. Other options like acpi_osi=Linux etc are again preventing brightness control key from working.
13. Idle RAM usage < 450 MB for Unity, < 200 MB for LXDE
14. Idle CPU 5-7% for unity 0-2% for LXDE
15. Idle CPU temp 35-50 C

Any suggestions on power optimization and battery improvements are welcome.

---

### Post by deadflowr on 2014-02-20
> Any suggestions on power optimization and battery improvements are welcome. 				

There is to be a ppa for a program called [jupiter]("https://launchpad.net/~webupd8team/+archive/jupiter")( It's somewhat of a dead project though)
(Or at least seems to be, since no updates have come for it in over a year)
There is this though
[http://www.webupd8.org/2014/01/install-laptop-mode-tools-164-with.html](http://www.webupd8.org/2014/01/install-laptop-mode-tools-164-with.html)

---

