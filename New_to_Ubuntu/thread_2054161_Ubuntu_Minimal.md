---
title: "Ubuntu Minimal"
date: 2012-09-06
forum: New to Ubuntu
---

### Post by 3dmatrix on 2012-09-06
I wish to try out Ubuntu Minimal install and then keep adding the required softwares to it.

(1) Before i remove my existing ubuntu, I wish to make a list of packages already installed. And a list of packages being displayed in the Application menu. How can i do it from the command line ?

(2) Is there any help / tutorial available with advises on this kind of installation ?

(3) I am not sure what are the applications that run in the background by default in a normal install and some of those applications might be important from security point of view. But as they might not be installed in a minimal install, so is there any suggestion related to this ?


.

---

### Post by bodhi.zazen on 2012-09-06
> **3dmatrix said:**
> I wish to try out Ubuntu Minimal install and then keep adding the required softwares to it.

(1) Before i remove my existing ubuntu, I wish to make a list of packages already installed. And a list of packages being displayed in the Application menu. How can i do it from the command line ?

Why remove your current installation ? Why not dual boot.

See also:

[http://askubuntu.com/questions/9135/best-way-to-backup-all-settings-list-of-installed-packages-tweaks-etc](http://askubuntu.com/questions/9135/best-way-to-backup-all-settings-list-of-installed-packages-tweaks-etc)

> (2) Is there any help / tutorial available with advises on this kind of installation ?

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

> (3) I am not sure what are the applications that run in the background by default in a normal install and some of those applications might be important from security point of view. But as they might not be installed in a minimal install, so is there any suggestion related to this ?
.

From a security vantage, use apparmor.

Just start with a minimal system and add only what you need.

---

### Post by sisco311 on 2012-09-06
Did you consider to try (dual boot/VM/chroot) another distro (like ArchLinux)? The Arch Wiki is very good. IMO, it's much easier to build Arch from the bottom to top... 

*[SIZE="1"]/me runs & hides in a corner[/SIZE]*

---

### Post by 3dmatrix on 2012-09-07
> **bodhi.zazen said:**
> Why remove your current installation ? Why not dual boot.

From a security vantage, use apparmor.

Just start with a minimal system and add only what you need.

I am removing my current installation because I am not getting help to solve problems that i am facing after upgrading to ubuntu 12.04 
[http://ubuntuforums.org/showthread.php?t=2052344](http://ubuntuforums.org/showthread.php?t=2052344)

I did not understand that 'apparmor' stuff that you mentioned.

I wish to add ONLY that i need but i do not know what important security applications come out of the box in a normal ubuntu installion and what are its config. Because if things do not work well the only reply i receive on this forum is - REINSTALL !!!

.

---

### Post by NikTh on 2012-09-07
> **sisco311 said:**
> Did you consider to try (dual boot/VM/chroot) another distro (like ArchLinux)? The Arch Wiki is very good. IMO,** it's much easier to build Arch from the bottom to top... **


No is not. Completely accidental now. I Just finished a 12.04 LTS minimal install. It is much easier. 

Not needed to configure entire system from scratch (Arch has not installed even "sudo").
Not needed to configure user groups , etc. 
Not needed to configure daemons etc. 
Of course you will say , Read Wiki , yes  , but it's not much easier as you mentioned. 

In Ubuntu minimal install 
Only apply commands to install what is necessary for you. (packages - programs - Desktop Environment) .

---

### Post by 3dmatrix on 2012-09-07
> **NikTh said:**
> No is not. Completely accidental now. I Just finished a 12.04 LTS minimal install. It is much easier. 

Not needed to configure entire system from scratch (Arch has not installed even "sudo").
Not needed to configure user groups , etc. 
Not needed to configure daemons etc. 
Of course you will say , Read Wiki , yes  , but it's not much easier as you mentioned. 

In Ubuntu minimal install 
Only apply commands to install what is necessary for you. (packages - programs - Desktop Environment) .

After the minimal install is done, what is the default desktop in it ? Do u have any snapshot of the very basic OS ? Or is it just cli ?

---

### Post by NikTh on 2012-09-07
> **3dmatrix said:**
> After the minimal install is done, what is the default desktop in it ? Do u have any snapshot of the very basic OS ? Or is it just cli ?

For me , just CLI , nothing else. 

Of course in base text installer , I didn't select any package to install . You will see this option as the installation moving on. A window will ask for packages you want to install, you can choose - select packages with Space key . I select NONE. I pressed Tab and Ok immediately.

Thanks

---

### Post by mastablasta on 2012-09-07
this is how minimal install looks like: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
 
you get a cli in the end and you can then install whatever desktop you want (if you actually wan't/need it)

---

### Post by 3dmatrix on 2012-09-07
I am not too comfortable with CLI so in that case what should be my first install ?
LXDE / GNOME etc and network manager and browser ? What else might be needed to start internet ?

---

### Post by NikTh on 2012-09-08
Hello , 

It depends on what you want. What you are looking for. Do you want to install Ubuntu with Unity ? I installed. 

When you reboot (after core installation) you will login in CLI . Then do an update 
```
sudo apt-get update ; sudo apt-get dist-upgrade
``` probably it will not update anything , but you don't miss something to try. 

Now what I installed. 

```
sudo apt-get install ubuntu-destkop --no-install-recommends 
#This parameter (--no-install-recommends) saved my by almost 500 packages
```If you don't give the above parameter, I don't see the point to install from minimal .iso. 
or 
if you want to do it just for experience. Ok. 

Proceed 
```
sudo apt-get install network-manager gnome-applets indicator-datetime ttf-ubuntu-font-family ubuntu-restricted-extras unity-lens-applications unity-lens-files firefox gparted synaptic dconf-tools gconf-editor smplayer
```Reboot. 

All above are my installation. You may want to add or remove packages . Its just an example. 

Thanks

**Tip**: If you face problems with internet - wireless.. then check out the file 
/etc/network/interfaces. Contents must be like this ```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

``` , if something is different , then change it and make the contents of the file exactly like above.

---

### Post by jerrrys on 2012-09-08
My starting point for a basic install (starting with a terminal only install):

sudo apt-get install lightdm gnome-session-fallback gnome-terminal synaptic

That will give you a very basic gnome desktop

---

### Post by 3dmatrix on 2012-09-08
> **jerrrys said:**
> My starting point for a basic install (starting with a terminal only install):

sudo apt-get install lightdm gnome-session-fallback gnome-terminal synaptic

That will give you a very basic gnome desktop

Any idea how does it looks like ! I was thinking of LSDX or XFCE
How are these two different from the basic Gnome ?

---

### Post by 3dmatrix on 2012-09-08
> **NikTh said:**
> Hello , 

It depends on what you want. What you are looking for. Do you want to install Ubuntu with Unity ? I installed. 

When you reboot (after core installation) you will login in CLI . Then do an update 
```
sudo apt-get update ; sudo apt-get dist-upgrade
``` probably it will not update anything , but you don't miss something to try. 

Now what I installed. 

```
sudo apt-get install ubuntu-destkop --no-install-recommends 
#This parameter (--no-install-recommends) saved my by almost 500 packages
```If you don't give the above parameter, I don't see the point to install from minimal .iso. 
or 
if you want to do it just for experience. Ok. 

Proceed 
```
sudo apt-get install network-manager gnome-applets indicator-datetime ttf-ubuntu-font-family ubuntu-restricted-extras unity-lens-applications unity-lens-files firefox gparted synaptic dconf-tools gconf-editor smplayer
```Reboot. 

All above are my installation. You may want to add or remove packages . Its just an example. 

Thanks

**Tip**: If you face problems with internet - wireless.. then check out the file 
/etc/network/interfaces. Contents must be like this ```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

``` , if something is different , then change it and make the contents of the file exactly like above.

Well those are wonderful suggestions but i am afraid if a newbee like me does not installs those dozens of "--no-install-recommends" then in case of a any package not working optimum it wud be difficult for me to locate the prob. What do you say ?

---

### Post by jerrrys on 2012-09-08
You can see the differences for yourself by adding the different desktops to your install and choose one at boot.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=add+xfce+to+ubuntu&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=add+xfce+to+ubuntu&as_qdr=all&sa=Google+Search&lang=en)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=add+lxde+to+ubuntu&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=add+lxde+to+ubuntu&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by NikTh on 2012-09-08
> **3dmatrix said:**
> Well those are wonderful suggestions but i am afraid if a newbee like me does not installs those dozens of "--no-install-recommends" then in case of a any package not working optimum it wud be difficult for me to locate the prob. What do you say ?

I say that you have right. 

When someone go through this process (of mini.iso) he/she must be ready to face problems (little problems usually , but Web is your friend). 

If you want to avoid all this mess , the proceed with normal CD/Usb installation. Desktop.iso. 

Thanks

---

### Post by jerrrys on 2012-09-08
> **NikTh said:**
> I say that you have right. 

When someone go through this process (of mini.iso) he/she must be ready to face problems (little problems usually , but Web is your friend). 

If you want to avoid all this mess , the proceed with normal CD/Usb installation. Desktop.iso. 

Thanks

Yes, that would be best to start and then learn about the packages offered.  Synaptic Package Manager would help you with that.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by 3dmatrix on 2012-09-15
> **jerrrys said:**
> Yes, that would be best to start and then learn about the packages offered.  Synaptic Package Manager would help you with that.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en)

Well having a lot of grub related problem since i upgraded to 12.04 and not able to track any good solution, anyway i found some time to install Minimal and got stuck half the way as minimal could not recognise my network as there was no dhcp available. I was behind a dsl modem connection. And so finally minimal did not get installed. Next i brought a router from my friend to install it and when i selected LXDE desktop it installed the entire LUBUNTU. Which i never wanted. So once again i formated the partition and installed minimal but did not install any package. Can anyone tell me what should be the command for a very basic install of OPENBOX or ENLIGHTENMENT desktop and some very important packages needed with it. Does Synaptic works on these two desktops ? Which of these two packages would work better ? And what is the relation between LXDE and Openbox ?

---

### Post by NikTh on 2012-09-15
Hi 

Lets take your questions one at time. 

> **3dmatrix said:**
> Can anyone tell me what should be the command**  for a very basic install** of OPENBOX or ENLIGHTENMENT desktop and some  very important packages needed with it. 

I based on bold . 
```
sudo apt-get install e17 --no-install-recommends
```When you want a very basic install of an Environment then always you must include this parameter. (--no-install-recommends). This parameter will prevent the installation of recommended packages (as you can understand)

For Openbox is not the same , cuz OpenBox is NOT a Destkop Environment. Is just a window manager , so no extra or recommended packages included. 
So for OpenBox ```
sudo apt-get install openbox
```Important packages are 
1. Synaptic 
```
sudo apt-get install synaptic
```2.Netwrok-Manager
```
sudo apt-get install network-manager
```3. Display manager. Multiple display managers are available. I will give you my choice 
```
sudo apt-get install lightdm
```4. Internet Browser. Available and known are Chromium and Firefox.Chromium suggested as lighter browser. 
```
sudo apt-get install chromium
```> **3dmatrix said:**
> Does Synaptic works on these two desktops ? 
Yes. 

> **3dmatrix said:**
> Which of these two packages would work better ?  And what is the relation between LXDE and Openbox ?
LXDE is built  upon OpenBox window manager. It is using it. 

I will suggest LXDE. You will install a very basic LXDE destkop with this command
```
sudo apt-get install lubuntu-desktop --no-install-recommends
```Look the difference now
> sudo apt-get install lubuntu-desktop = Installation of 326 new packages.
sudo apt-get install lubuntu-destkop --no-install-recommends = installation of 62 new packages. 

Thanks

---

### Post by Scott Harrison on 2012-09-15
> **mastablasta said:**
> this is how minimal install looks like: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
 
you get a cli in the end and you can then install whatever desktop you want (if you actually wan't/need it)
Thanks for the link, very useful!

---

### Post by 3dmatrix on 2012-09-15
Thanx !

LXDE is built upon OpenBox window manager. It is using it.
I will suggest LXDE. You will install a very basic LXDE destkop with this command
Code:  sudo apt-get install lubuntu-desktop --no-install-recommends

So if i install Lxde (minimal) then does openbox also gets loaded ?
If so then how is the interface of distros like CrunchBang different from Lubuntu ?
As far as i know, Crunch Bang used Open Box and Lubuntu uses LXDE.
Any example of a very often used application that cannot be used on Openbox / LXDE ?

What is this Light DM that you mentioned ?
.

---

### Post by black veils on 2012-09-15
> **3dmatrix said:**
> Thanx !

LXDE is built upon OpenBox window manager. It is using it.
I will suggest LXDE. You will install a very basic LXDE destkop with this command
Code:  sudo apt-get install lubuntu-desktop --no-install-recommends

So if i install Lxde (minimal) then does openbox also gets loaded ?
If so then how is the interface of distros like CrunchBang different from Lubuntu ?
As far as i know, Crunch Bang used Open Box and Lubuntu uses LXDE.
Any example of a very often used application that cannot be used on Openbox / LXDE ?

What is this Light DM that you mentioned ?
.

if I distro states it is using openbox, then that is probably all it has. but if it states lxde, that includes openbox. this is how the open source world works, mix and match, modify etc

lxde has openbox as part of the desktop environment, but openbox can be used alone.

---

### Post by NikTh on 2012-09-15
Hi ,
> **3dmatrix said:**
> 
So if i install Lxde (minimal) then does openbox also gets loaded ?
Yes. If you logout you can see an openbox session too. 

> **3dmatrix said:**
> If so then how is the interface of distros like CrunchBang different from Lubuntu ?
The specific disto not using LXDE Environment. It not using a environment at all. It has only this Window manager (openbox) and some tools.

> **3dmatrix said:**
> As far as i know, Crunch Bang used Open Box and Lubuntu uses LXDE.
Correct. You can use Openbox separately , but you cannot use LXDE without openbox. (They are married) 
> **3dmatrix said:**
> Any example of a very often used application that cannot be used on Openbox / LXDE ?
No . I don't remeber any app that cannot run in Lubuntu but run in Ubuntu. Maybe applications that are specific to the Desktop Environment , like "Unity Mail" cannot be merged correctly in LXDE (Lubuntu).

> **3dmatrix said:**
> What is this Light DM that you mentioned ?
.

LightDM is the default display manager of Ubuntu 12.04.(Lubuntu 12.04 too) You must have a Display manager to handle your login screen. 
Except if you don't want , you can skip this step and starting the Desktop with ```
startx
``` command. 

Why I recommended Lubuntu ? 

1st cuz I like it and I using  it. 

2nd Cuz of this : [https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu) , you can find almost everything in there. 

3rd .. is FAST , yes , it is light as feather and fast as Rocket ! 

Thanks

---

### Post by mörgæs on 2012-09-15
The easiest way of setting up a minimal Buntu:

[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

---

### Post by mips on 2012-09-15
Backup your /var/cache/apt folder

---

### Post by 3dmatrix on 2012-09-15
Ubuntu Minimal is such a wonderful distro. There is so much to learn when we install things one by one according to our requirement. I installed OpenBox and E17 but somehow find Openbox slightly better. But having some config problem. The menu is not updating and many changes are not remaining permanent. But over all i have a nice and small OS working very fast. What will be the difference a LXDE and Lubuntu desktop ?

---

### Post by NikTh on 2012-09-16
> **3dmatrix said:**
>  I installed OpenBox and E17 but somehow find Openbox slightly better. But having some config problem. The menu is not updating and many changes are not remaining permanent. Sometimes Openbox restarted required.   > **3dmatrix said:**
> But over all i have a nice and small OS working very fast. What will be the difference a LXDE and Lubuntu desktop ?

I don't know what applications E17 carries , but with LXDE you would have a basic desktop Environment , fast yes , light yes and with some basic applications to start over.

eg: PcManFm (file manager) , lxterminal , leafpad (editor) , I think abiword (instead of libreoffice).. etc. 

Now you have job to do.. until you full setup your O.S. 
If you like Openbox, yes is the lighter of all , cuz as told before is not even a Desktop Environment , is a window manager. 
Begin to read from here : [http://openbox.org/wiki/Main_Page](http://openbox.org/wiki/Main_Page)

Glad you eventually setup a minimal.iso. 

Enjoy the pleasure of building. 

Thanks

---

### Post by 3dmatrix on 2012-09-16
I also installed Lubuntu Desktop just to try out. It is good too. In Openbox i like the lack of any panels / buttons etc. Everything seems hidden but is always there. You just rt click and get the menu. But every thing is very basic. The menu is not updating. I can not copy / paste in the terminal and many such lil prob. Compared to that Lubuntu is more or less a basic but ready Desktop.

When i install any application should i use the --no-install-recommends switch ? Or it is only suitable for the Desktop install ?

Any good forum for Openbox in your mind ?

---

### Post by NikTh on 2012-09-16
> **3dmatrix said:**
> 
When i install any application should i use the --no-install-recommends switch ? Or it is only suitable for the Desktop install ? 

No. This is not suggested. Of course you can use this switch on applications , but maybe an application wants something (a package) from the recommended , to do the job you want. 
So use this switch with caution. 

> **3dmatrix said:**
> Any good forum for Openbox in your mind ?

A distro that is debian-based and uses openbox is CrunchBang Linux. 

The forums are here : [http://crunchbanglinux.org/](http://crunchbanglinux.org/)

Thanks

---

### Post by 3dmatrix on 2012-09-16
Thanx !

---

### Post by sisco311 on 2012-09-16
> **NikTh said:**
> No is not. Completely accidental now. I Just finished a 12.04 LTS minimal install. It is much easier. 

Not needed to configure entire system from scratch (Arch has not installed even "sudo").
Not needed to configure user groups , etc. 
Not needed to configure daemons etc. 
Of course you will say , Read Wiki , yes  , but it's not much easier as you mentioned. 

In Ubuntu minimal install 
Only apply commands to install what is necessary for you. (packages - programs - Desktop Environment) .

Well, we have to agree, that we disagree about what *minimal* means. :)

sudo is not a **must**; configuring users and groups is it, and, knowing how to configure (auto-stop/start) the daemons (and what daemons are) is also a **must** in _my opinion_, if one wants to build a minimal `Linux OS'.

[/demagogy end] :)


Playing/Lurking with other distros helped me a lot to understand (more) about kernels/shells/display managers/window controllers/desktop environments etc... That's the reason why I suggested to the OP to try Arch or any other distro.

Likely it's irrelevant, but for the record... I usually use debootstrap to install Ubuntu and I find it easy, probably  because I learned how to do this...

---

### Post by NikTh on 2012-09-17
> **sisco311 said:**
> Playing/Lurking with other distros helped me a lot to understand (more) about kernels/shells/display managers/window controllers/desktop environments etc... That's the reason why I suggested to the OP to try Arch or any other distro..
Hi , 
I don't disagree . . And if you run the latest .iso (Oh yes , Arch made a new .iso , this is News! Hah) you will see that it hasn't even an Installer now. Nothing. Not even this basic text installer usually had. A terminal (Console like) and scripts to build and install the basic system.

I only disagree with this > **sisco311 said:**
>  IMO, **it's much easier** to build Arch from the bottom to top...

:)

---

### Post by bodhi.zazen on 2012-09-17
Well, it is "easier" to build Arch because there are less dependencies, so it is easier to keep things minimal.

There is certainly a learning curve to installing and using Arch, but once you RTFM you are good to go.

---

### Post by mips on 2012-09-17
> **bodhi.zazen said:**
> Well, it is "easier" to build Arch because there are less dependencies, so it is easier to keep things minimal.

There is certainly a learning curve to installing and using Arch, but once you RTFM you are good to go.

+1 I've noticed my ubuntu minimal installs pulls in more 'stuff' if I could call it that.

The Beginners Guide (Official install Guide optional but handy) is a must, the wiki is great for all other topics.

---

### Post by XBMC old School on 2012-09-20
@NikTh, You da Man(?)!!!!!!!!!!!

The ubuntu install didn't seem that minimal from the list option. But your terminal install is saweet!!! 
----------------------------------------------------------------------------------------------------

@3dMatrix Virtual box is the way to go.      
([https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads))

I have a ubuntu 10.04 install and building a 12.04 from scratch. The VBox is 
nice for apprehensive noobs (like me) because;

1) you can google things while you build and mod
2) you get endless do overs due to machine cloning and snapshot saving in Vbox,
3) you can sample programs and desktop environments and then ultimately only
    load the one you want (keep it lean)
4) you can build at your leasure, no mad 2 am dash to get a working install.
5) In the end, after you have guess and tested, revised and polished  
    (hopefully recompiled the Kernel). You can remaster it into a custom 
    installation (remastersys in the vbox machine)

I'm actually doing it right now
--------------------------------------------------------------------------------------------------------------

Awesome thread

Hey, if anyone can give a quick rundown on the "manual Package Selection" option that would be cool

****The only thing better than removing Unity is it not being in there in the first place.****

---

