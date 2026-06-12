---
title: "Ubuntu to xubuntu or lubuntu?"
date: 2012-06-26
forum: New to Ubuntu
---

### Post by seal308 on 2012-06-26
Hello,
I love linux so far. 
I've been using ubuntu.
However my computer is very laggy and slow.
Here are my specs: [http://dl.dropbox.com/u/48157044/hardware_info.html](http://dl.dropbox.com/u/48157044/hardware_info.html)
Basically I just want to know which OS would be best for my computer lubuntu or xubuntu?
I know lubuntu is lighter however I was wondering if xubuntu would also work well.
Basically i need something that is snappy and doesn't lag so bad.

Another concern i have is apps.
The apps i use all the time are dropbox, synergy, firefox, document viewer, a music player
And if possible some sort of video player like VLC but that's not a necessity.

I am by no means a power user. I download apps off the ubuntu app store. I do not know how to install apps using terminal.

Any help is much appreciated.

Thanks

---

### Post by wildmanne39 on 2012-06-26
Hi, lubuntu is my recommendation but you can also logout and login to classic no effects and see how much that improves performance without installing another operating system.
Thanks

---

### Post by seal308 on 2012-06-26
I'm sorry, how do i this? (get onto classic)
Thanks

---

### Post by wildmanne39 on 2012-06-26
Hi, I am assuming you are using 12.04, logout then click on the picture of the little foot, then on classic no effects and enter paqssword.

If 11.04 or 11.10 I believe once you logout you click on your username then a drop menu will appear.
Thanks

---

### Post by kansasnoob on 2012-06-26
> **seal308 said:**
> I'm sorry, how do i this? (get onto classic)
Thanks

I've been making some notes here:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

Regarding other DE's look at the Playing Around section here:

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by seal308 on 2012-06-26
So what i did was logged out.
Clicked on that little icon on login. 
Clicked on Unity 2d.

My computer does seem a little faster.
However if I want to install lubuntu what do i do?
I was reading this article: [http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-how-to-install-the-lubuntu-desktop](http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-how-to-install-the-lubuntu-desktop)

It shows how to get the lubuntu desktop.
However wouldn't installing the desktop just add on to ubuntu therefore making it more slow.
How would I make it into a lubuntu OS that's fast.

Thanks

---

### Post by Paqman on 2012-06-26
> **seal308 said:**
> 
However wouldn't installing the desktop just add on to ubuntu therefore making it more slow.


No, because you can only run one desktop environment at a time. You'd log out of Unity, pick LXDE from the wee list just like you did for Unity 2D and log back in.

Linux systems are very modular, you can swap bits around a fair bit to get the system how you want it.

---

### Post by seal308 on 2012-06-26
Therefore are you saying I could have as many desktop environments as I want and the computer would not get slower? Because of the whole "swapping" effect?

---

### Post by wildmanne39 on 2012-06-26
Hi, I personally would just put lubuntu on after doing a reformat so you have a lean mean machine.
Thanks

---

### Post by seal308 on 2012-06-26
Hello, I would I reformat the computer for just lubuntu. And what is the difference between this method and the lubuntu desktop.
Thanks

---

### Post by wildmanne39 on 2012-06-26
Hi, you would have just lubuntu and not ubuntu and all of its desktops.
Thanks

---

### Post by Paqman on 2012-06-26
> **seal308 said:**
> And what is the difference between this method and the lubuntu desktop.


Nothing really, except that you'd still have all the Unity/Gnome packages on your system if you started with Ubuntu and installed lubuntu-desktop. But that's easily fixed with a [single command]("http://www.psychocats.net/ubuntu/purelubuntu").

Under the skin Ubuntu/Xubuntu/Kubuntu/Lubuntu are all pretty much the same, they just differ on what desktop packages are plonked on top.

---

### Post by zombifier25 on 2012-06-26
You can just install LXDE, nothing more. Install lxde-core package, and you'll get only LXDE and not the apps that come with it.

---

### Post by mike555 on 2012-06-26
I second installing lxde-core to try lxde , but I would recommend Xubuntu clean install , I use it on my Acer with specks like yours and it runs good.

---

### Post by seal308 on 2012-06-26
Sorry missed typed in last post.
Hello, **how** would I reformat the computer for just lubuntu. And what is the difference between this method and the lubuntu desktop method.
Thanks

---

### Post by seal308 on 2012-06-26
Thanks mike.
I think i might try xubuntu after looking at it.
So is it like this:
install xubuntu by typing sudo apt-get install xubuntu-desktop
Try it out.
When ready to convert. 
sudo apt-get remove ubuntu-desktop

So is that installing the core?
or is this something different?

---

### Post by sibin xavier on 2012-06-26
> **seal308 said:**
> Hello,
I love linux so far. 
I've been using ubuntu.
However my computer is very laggy and slow.
Here are my specs: [http://dl.dropbox.com/u/48157044/hardware_info.html](http://dl.dropbox.com/u/48157044/hardware_info.html)
Basically I just want to know which OS would be best for my computer lubuntu or xubuntu?
I know lubuntu is lighter however I was wondering if xubuntu would also work well.
Basically i need something that is snappy and doesn't lag so bad.

Another concern i have is apps.
The apps i use all the time are dropbox, synergy, firefox, document viewer, a music player
And if possible some sort of video player like VLC but that's not a necessity.

I am by no means a power user. I download apps off the ubuntu app store. I do not know how to install apps using terminal.

Any help is much appreciated.

Thanks
Lubuntu ,PuppyLinux,Zorin OS lite

[http://www.lubuntu.net/](http://www.lubuntu.net/)
[http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)
[http://zorin-os.com/free.html](http://zorin-os.com/free.html)

I prefer Lubuntu and zorin OS ,Both uses LXDE interface..

---

### Post by zombifier25 on 2012-06-26
> **seal308 said:**
> When ready to convert. 
sudo apt-get remove ubuntu-desktop

So is that installing the core?
or is this something different?

ubuntu-desktop is merely a meta package. Installing it will pull in all the Ubuntu packages (like xubuntu-desktop for Xubuntu), but removing it will do nothing. If you want to remove Ubuntu's components you have to track down each and every softwares installed, which is hard, because your original system is Ubuntu.
I don't see why you must do this anyway. The only thing it will harm is your hard drive space.

The easier way would be to just remove Ubuntu altogether and install Xubuntu on top.

---

### Post by seal308 on 2012-06-26
So therefore
I must make a cd for xubuntu and install it like how i did for ubuntu?

---

### Post by seal308 on 2012-06-26
Is there a way i can do this without having to install the whole thing by a cd again?

---

### Post by mike555 on 2012-06-27
Sorry , but a clean install of Xubuntu is best........ backup your documents, etc. on an external drive or thumbdrive first then just format and in install Xubuntu from .iso.

 after that you might want to install LibreOffice and a few other programs ....... but avoid any KDE apps.

---

### Post by kansasnoob on 2012-06-28
> **Paqman said:**
> Nothing really, except that you'd still have all the Unity/Gnome packages on your system if you started with Ubuntu and installed lubuntu-desktop. But that's easily fixed with a [single command]("http://www.psychocats.net/ubuntu/purelubuntu").

Under the skin Ubuntu/Xubuntu/Kubuntu/Lubuntu are all pretty much the same, they just differ on what desktop packages are plonked on top.

+1!

I've personally tested those conversions in Precise :D

See [post #5]("http://ubuntuforums.org/showpost.php?p=12055061&postcount=5").

---

### Post by Dylansd on 2012-07-05
Hi All,

So been using Linux for almost 20 years. 
Redhat 5.0, gentoo, etc..
Ubuntu was good for 3 years, but then unity+compviz ruined it. 

Switched both my desktop and netbook to Lubuntu... and OMFG.

Legend, speed is mind blowing, ease of use awesome. 
All I can say is wow, probably the best linux experience I have ever had. Openbox on gentoo is a close second but the admin is killer.

LXDE + ubuntu = smile from ear to ear.

---

### Post by I2k4 on 2012-07-05
I'm dual booting lubuntu 10.10 on a little Acer netbook with the same Atom N270 specs as the orginal poster's.  For that machine, I rejected _all_ the Ubuntu/Mint spin offs from version 11.04 onward, as being too demanding and slow - Ubuntu left old and weak machines behind starting with version 11.  The cost of using 10.10 is end of support / updates for most repositories, but it does everything I want blindingly fast on a weak machine. 

The one downside of the Lubuntu LXDE interface is that it's a bit cruder and less newbie friendly than others, and I'm glad I tried out some Gnome versions first to get the feel of Linux.  

I strongly suggest using a 4GB _Persistent Live USB_ as a great way to check out the very different GUIs, package managers, and preinstalled software on different versions.  It will also test compatibility - for example Xubuntu when tried it simply would not find the Acer's hard drive and had some other kinks on that machine.  Persistent Live USBs allow you try out just about everything the OS routinely does and compares resource demands - of course performance then improves on a regular hard drive install.

The Ubuntu step by step below is bullet proof, except that the Pendrive installer can set space for "Persistence" which saves settings and updates / software installations between reboots:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Have fun.

---

### Post by amr-maro on 2012-09-18
> **seal308 said:**
> Is there a way i can do this without having to install the whole thing by a cd again?

Yes, you can put your Xubuntu or Lubuntu .iso image on a USB stick and install from it just like a CD. Have a look at this:
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu)
It works for all Ubuntu flavours.
Then boot your computer from the USB stick.

Good luck :)

---

