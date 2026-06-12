---
title: "nVidia 5200 FX installation"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by 10Digits on 2008-04-24
Hi there
 I downloaded the nVidia geforce 5200 FX driver from the nVidia website for my i386 (32-bit?) computer.

But somehow I cannot install it on my computer ,
whenever i run {.run) driver thru the terminal it ends up saying that it has to be installed as root?

typing   sudo -i doesn't help..

What should I do? help!!

---

### Post by hermes0710 on 2008-04-24
Hi there. First of all you shouldn't install the driver manually. From the top menu select System - > Administration - > Restricted drivers manager, enter your password as requested and in the window that appears there must be an entry saying NVidia bla bla. Check the checkbox to enable it and restart. That would be all. Keep me posted

---

### Post by 10Digits on 2008-04-24
But will it work without an Internet connection??

Anyways really fast reply!! thnx!!

---

### Post by pedro_orange on 2008-04-24
> **10Digits said:**
> 
typing   sudo -i doesn't help..


Is that '-i' a typo? Or are you actually using that?

From the sudo manual:
> 
-i

    The -i (simulate initial login) option runs the shell specified in the passwd(5) entry of the user that the command is being run as. The command name argument given to the shell begins with a `-' to tell the shell to run as a login shell. sudo attempts to change to that user's home directory before running the shell. It also initializes the environment, leaving TERM unchanged, setting HOME, SHELL, USER, LOGNAME, and PATH, and unsetting all other environment variables. Note that because the shell to use is determined before the sudoers file is parsed, a runas_default setting in sudoers will specify the user to run the shell as but will not affect which shell is actually run.


I also agree with the previous poster. Restricted Drivers Manager is the best tool to use to install your nVidia driver.

---

### Post by pedro_orange on 2008-04-24
> **10Digits said:**
> But will it work without an Internet connection??

Anyways really fast reply!! thnx!!

Restricted Drivers does require the Internet; since it automatically downloads/installs the correct driver for you.

---

### Post by 10Digits on 2008-04-24
YES I am using sudo -i

But I don't know if Restricted Drivers Manager will work or not
without an internet connection??

Thanx pedro!!

---

### Post by hermes0710 on 2008-04-24
No, the restricted manager won't work without the internet connection... Unfortunately it's a complex thing to manually install the nvidia driver since it's going to mess up the ubuntu configuration. Even editing the /etc/X11/xorg.conf to reflect the manually installed driver is not enough. Is it impossible to establish an internet connection?

---

### Post by dmiller40 on 2008-04-24
I use the s-video out on my 5200, and to get it to work correctly i used envy to install the driver. Then i could also adjust the overscan.

dm

---

### Post by pedro_orange on 2008-04-24
So you did it using Envy?
Cause Envy uses the Internet too, to download your driver.

Communication Breakdown!!:KS

---

### Post by 10Digits on 2008-04-24
Yes impossible to say the least...

It is the same reason why i cannot install Envy,Easyubuntu,gDesklets,Exaile among others.

Without an internet connection...ubuntu has become a bitter experience..maybe I should use SuSe ???? They have a wide range of softwares to start with>>>>:confused:

---

### Post by Glugglug on 2008-04-24
I'm trying to do the same and the message comes up nvidia installer must be run as root but I don't know how to log in as root and before anyone says I should be using the restricted driver manager it doesn't work it just has a red dot against it and says not in use . The box is ticked enabled  and yes I have restarted the computer more than once.

---

### Post by 10Digits on 2008-04-24
I can feel your pain.....:(

---

### Post by hermes0710 on 2008-04-24
> **Glugglug said:**
> I'm trying to do the same and the message comes up nvidia installer must be run as root but I don't know how to log in as root and before anyone says I should be using the restricted driver manager it doesn't work it just has a red dot against it and says not in use . The box is ticked enabled  and yes I have restarted the computer more than once.


The fact that it is ticked but not in use means that you messed up the drivers... You should open a terminal, go to the folder that you downloaded the nvidia driver and execute ```
sudo sh ./NVidia-whatever-the-driver-name-is --uninstall
```

Then restart and launch again the restricted drivers manager in order to proceed with the installation of the driver following the ubuntu way.

---

### Post by amphet on 2008-04-24
I have a nvidia 5500 FX and its working ok, check your xorg.conf and make sure the driver section looks like this

```

Section "Device"
	Driver		"nvidia"

```

you can find xorg.conf in /etc/X11

---

### Post by hermes0710 on 2008-04-24
> **amphet said:**
> I have a nvidia 5500 FX and its working ok, check your xorg.conf and make sure the driver section looks like this

```

Section "Device"
	Driver		"nvidia"

```

you can find xorg.conf in /etc/X11

I think that this is going to work only if nvidia-glx-new is installed. Otherwise the "nvidia" driver is not present, only the "nv" one.

---

### Post by Glugglug on 2008-04-24
I agree that I could of messed up the drivers but the not in use message was there before I did anything. Still don't know how to log in as root done a search for it but nothing useful comes up so cant even change the xorg.config .

---

### Post by dmiller40 on 2008-04-24
The root login is disabled to begin with. You can edit it 2 ways

```
sudo gedit /etc/X11/xorg.conf
```

Or you can enable the root user.
Go to System -> Admin -> Login Window
 then check Allow local system admin login
Go to System -> Admin -> Users & Groups
 and change the root password.

You should be able to logout then login with
user: root
Pass: whatever you set.

Getting started is difficult to use the terminal, and loging in as root made it easier for me.

dm

---

### Post by 10Digits on 2008-04-29
Logged in just now to find your reply dmiller40
maybe I can manually install my graphics card driver after all..
just maybe..
I will keep you guys posted.

Thanx.

---

### Post by 10Digits on 2008-05-09
Hehe , Guess I am too lazy ...
Hey dMiller40

Your advice worked like a charm

Here's what i did , First I logged in as the root account and then through the terminal stopped the X server.

Then I pressed Ctrl + Alt + F1 to log in as root again ...

Then I cd'ed:rolleyes: to Desktop where the .run file is...

Then I ran sh NVIDIA-Linux-x86-169.12-pkg1.run
The setup ran smoothly and it even wanted me to configure the card at startup but my display is stuck at an ugly 800 X 600 res.
I can't seem to enable the driver though.
Any help would be more than welcome, Remember The answer should be on how to do it without an internet connection.

Thanx a lot

---

### Post by pedro_orange on 2008-05-09
Hmm so you manually installed it. Well done! Nearly there!

I guess what you can do to reconfigure screen resolution (among other things) is to do a:

```
sudo dkpg-reconfigure xserver-xorg
```

You'll get asked things like what mouse and keyboard (just hit defaults) you're using. 
You'll also get asked what resolutions your monitor can handle. (Refer to your manual) Choose them and they should be accessible from the Screen Resolution tool within GNOME.

---

### Post by 10Digits on 2008-05-09
Thanx pedro I feel we are nearly thee If this works It will be gr8...

I will try it out and inform every one about it.


Oh yeah I t  also brings up a message about nvidia-glx-new not being enabled ... what about thi:confused:s...

---

### Post by pedro_orange on 2008-05-09
If the driver is installed; you should be able to enable it through System > Administration > Restricted Drivers Manager

Or you can check /etc/x11/xorg.conf and see which driver your card is using there.

Btw; you can view/edit that file using:

```
sudo nano -w /etc/x11/xorg.conf
```

---

### Post by 10Digits on 2008-05-12
I've installed the Drivers anew configured the x server before logging in and done as wrote me to do....

The good news is while i am in root I can find the nVidia control center which is good I think!
But is tells me to run nvidia-xconfig or something like that.

We have almost done it ...

The bad news is that my PC configuration doesnot support the desktop effects somehow.:(

Whatever , though I think we have almost wrapped tyhis problem up what do you think Pedro??

---

