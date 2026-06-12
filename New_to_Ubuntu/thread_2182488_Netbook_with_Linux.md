---
title: "Netbook with Linux?"
date: 2013-10-21
forum: New to Ubuntu
---

### Post by Citta on 2013-10-21
[FONT=SimSun]Hi, [/FONT][FONT=SimSun]
[/FONT][FONT=SimSun]
[/FONT][FONT=SimSun]After severe crashes of Win7Starter I want try to install Linux-what would be the best distro? Best does mean software, etc, are starting and closing quickly and the OS should be reliable and stable. [/FONT][FONT=SimSun]
[/FONT][FONT=SimSun]The netbook is a VAIO VPCW21C7E, 4 years old. As a dual boot is Ubuntu 13.04 installed, it is quite lame and slower than Win. Processor is Atom. [/FONT][FONT=SimSun]
[/FONT][FONT=SimSun]I want run videos with the VLC Player, which is the best, at least under Win. Much better than WinMediaplayer. I-tunes will probably not available in Linux, I use it for podcatching  and it is very useful most of the time. I read a lot offline HTML, pdf and so on. [/FONT][FONT=SimSun]
[/FONT][FONT=SimSun]Mainly used as a machine for learning, e. g. CS101, so Python 2.7 will be installed. [/FONT][FONT=SimSun]
[/FONT][FONT=SimSun]
[/FONT][FONT=SimSun]What would you suggest for this purposes?[/FONT][FONT=SimSun]
[/FONT][FONT=SimSun]Thanks a lot for your advices and hints[/FONT][FONT=SimSun]
Citta
[/FONT][FONT=Times New Roman][/FONT]

---

### Post by Lars Noodén on 2013-10-21
Python and perl are pre-installed on just about any distro you can choose.  

If you want a smaller and faster GUI then you can go with Lubuntu which uses LXDE instead of Unity.  If you want even faster, skip the desktop environment and install just a window manager.  Openbox is popular.  There are also Enlightenment and FVWM-crystal.

---

### Post by Citta on 2013-10-21
Hello, 

Did I understood rightly that every distro is suitable for a weak netbook? What is a window manager, where can I see it? How to install it with Lubuntu and why is it faster? Is it usable for an unexperienced user like me?
Thanks
Citta

---

### Post by Lars Noodén on 2013-10-21
Some distros are targeted for weaker hardware.  [Lubuntu](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall) does that in the Ubuntu family.  There would also be Puppy Linux to look at.  LXDE requires less CPU and RAM than the other Ubuntu distros like Kubuntu and Xubuntu.  But it is still a full desktop environment and you might get by with just a window manager.  

The window manager is a component of the GUI and controls the appearance and behavior of the windows.  It can be used as part of a larger, heavier desktop environment or stand alone.  If you are looking to save system resources, then use a window manager stand alone and skip adding the full desktop environment.   Your applications like Firefox and LibreOffice are still going to be using the same amount of resources they always have, so distros like Lubuntu have pre-installed lighter weight alternatives.  However, with any distro you can add or remove what you want, when you want.

They are all suitable for beginners, but picking applications a la carte might be new and unfamiliar.  However, it is not hard.

---

### Post by Citta on 2013-10-22
Thanks, at first glance I assumed a window manager is something like a terminal...could you tell where I can find a document concerning this window manager, please? Perhaps I have to control the installation accordingly and later it might too difficult to change the installation and generally I would like to read something before spoiling the OS.

---

### Post by fantab on 2013-10-22
First try regular **Lubuntu**. If it does not work then you can work with a Window manager like Openbox.
[Crunchbang]("http://crunchbang.org/") is a debian based distro, like Ubuntu and uses Openbox. Try it from DVD/USB for some time to get the hang of Openbox. Remember it is Debian not Ubuntu.

---

### Post by Lars Noodén on 2013-10-22
I'm not sure of a place with concise definitions of the GUI components.  There are X11, the window manager and the desktop environment.  

For the window managers, you can get an idea by looking at them:  

[http://www.oroborus.org/](http://www.oroborus.org/)
[http://fluxbox.org/](http://fluxbox.org/)
[http://openbox.org/](http://openbox.org/)
[http://www.enlightenment.org/](http://www.enlightenment.org/)

They cover things like mouse focus, window borders and decoration, title bars, widgets (close, maximize) and their position and appearance, resize, and virtual desktops.  Some things are available as addons or in the default.  

All the window managers are available in Ubuntu, so it is possible to get a stripped down installation (see [core install](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Full_install.2C_minimal_install_or_core_install.3F)) without having to switch distros.  Lubuntu would be a good place to start because even though it provides a full desktop environment in LXDE, it is a light weight one.  If that slows you down too much then you can try one of the window managers without the full desktop environment.

---

### Post by Citta on 2013-10-22
"Remember it is Debian not Ubuntu".What are the consequences, if it is Debian, definition of Debian? I "know" Ubuntu, as mentioned, not 13.04, it is 12.04.....

---

### Post by Lars Noodén on 2013-10-22
Debian is another distro.  Ubuntu is a subset of Debian but with changes, mostly to the Desktop Environments Unity, KDE, XFCE and LXDE.  Debian has all of those except Unity but they are not pre-configured to look as nice.  Ubuntu has made them look as nice as they can out of the box.  With Debian, all that is possible, but you are expected to make the changes yourself.  I'm not sure you will gain any size advantage by trying Debian instead of one of the Ubuntus.  I'd repeat my recommendation of looking at using just a window manager.

---

### Post by Citta on 2013-10-22
Thanks for the clarification, now I have a lot to read, enhancing my education about Linux!:)

---

### Post by mastablasta on 2013-10-22
you need to use .deb packages for debian not for ubuntu. and also debian works in a slightly different way. but chrunchbang is quite nicely modified debian in a more user friendly way.

however there is really no need to switch. as suggested lubutnu and then install windows manager and switch to another widnows manager if you need to (if lubuntu is sitll too slow). the also have KDE for netbooks (netbook plasma). KDE can take a lot of resources or not. depends how you set it up.

a simple windows manager is also IceWM - looks kind of like windows 98. it is showcased well in AntiX (debian/mepis based distro). super light on resources yet with familiar user interface.

a comparison chart of windows managers: [http://en.wikipedia.org/wiki/Comparison_of_X_window_managers](http://en.wikipedia.org/wiki/Comparison_of_X_window_managers)
a bit of comparison of desktop environments: [http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments](http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments)

there are plenty of comparisons available online. for example: [http://www.renewablepcs.com/about-linux/kde-gnome-or-xfce](http://www.renewablepcs.com/about-linux/kde-gnome-or-xfce)

---

### Post by Citta on 2013-10-22
Thanks a lot for your reviews...will become a Linuxguru soon!:KS

---

### Post by fantab on 2013-10-22
> **fantab said:**
> First try regular **Lubuntu**. If it does not work then you can work with a Window manager like Openbox.
[Crunchbang]("http://crunchbang.org/") is a debian based distro, like Ubuntu and uses Openbox. Try it from DVD/USB for some time to get the hang of Openbox. Remember it is Debian not Ubuntu.

I suggested Crunchbang to OP to see and get the feel of Openbox... 
Enlightenment is another Windows Manager, you can checkout [Bodhi Linux]("http://www.bodhilinux.com/"), which is based on Ubuntu LTS.

---

### Post by beernarrd on 2013-11-11
> **fantab said:**
> I suggested Crunchbang to OP to see and get the feel of Openbox... 
Enlightenment is another Windows Manager, you can checkout [Bodhi Linux]("http://www.bodhilinux.com/"), which is based on Ubuntu LTS.

Bodhi runs smoothly and fine on my P4Centrino latitude ...

---

### Post by david98 on 2013-11-11
Try reading a linux bible they have been very helpful for me in the past and the majority is all transferable across linux distro's if you get a hard copy you get a multiboot disk with various distro's on it. The book's can be quite pricey but here in the uk you can pick them up in the library if they don't have them the will order them in for you for a small fee.

---

### Post by Citta on 2013-11-13
Hi, 

Just installed Lubuntu alongside Win7Starter. Starting the netbook the bootloader with Win7 at the end of the is displayed-enter-nothing else than a blackscreen. After several minutes the Vaio-logo appears, the bootloader and so on...Lubuntu runs quickly, faster than Win. 
Nevertheless I need to access Win, because my work is there located and much more. 

What to do??
Thanks for your advice!

Citta
Ps: Just another try started Win...but I do not know what will happen the next time, also I do not know why it booted now....

---

### Post by Citta on 2013-11-13
Thanks for the hint...could you refer certain books? I assume "linux bible" is no specific title.

---

### Post by Citta on 2013-11-13
Hi, 

Meanwhile the problem of not booting Win seems to be solved...it boots! After several rebootings!

---

### Post by thesleash on 2013-11-15
personally, i would install the latest long term release

---

### Post by FiremanEd on 2013-11-15
I have an Acer Aspire one D255E in which I bumped up the RAM to 2Gb and it runs Xubuntu 13.10 flawlessly.  I am not sure what you have as a netbook, but all the advice given are top notch choices.

---

