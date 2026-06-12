---
title: "installation failure"
date: 2012-01-26
forum: New to Ubuntu
---

### Post by mastergkage on 2012-01-26
hello guys please help i'm desperate, i have installed oneric from a usb all went well but upon the installation it tried to find something from the cd but did not found it since i used a usb pendrive, after that it said installation success how can i fix this, without the cd, I also tell a friend that ubuntu is good and but now i cannot do that since the installation fail tnx a lot guys your swift response is appreciated.

---

### Post by Double.J on 2012-01-26
Hi there,

Sorry I was a little confused, you said it was successful and failed?

As for looking for something on the CD - if you used a USB, it would look on the USB :)

Were you trying to install to a USB HDD? This sometimes fails to install the bootloader porperly, but does install the OS. If this is the case, then boot up the live usb, click try not install, and follow [this guide]("https://help.ubuntu.com/community/Boot-Repair") to install boot-repair.

Hope it helps :)

---

### Post by critin on 2012-01-26
> **mastergkage said:**
> hello guys please help i'm desperate, i have installed oneric from a usb all went well but upon the installation it tried to find something from the cd but did not found it since i used a usb pendrive, after that it said installation success how can i fix this, without the cd, I also tell a friend that ubuntu is good and but now i cannot do that since the installation fail tnx a lot guys your swift response is appreciated.

The same files will be on the usb pendrive that are on a cd.  If the installation was declared successful, how is it broken?  Where is it failing for you?

---

### Post by mastergkage on 2012-01-27
sorry for the confusion, I installed 11.10 via usb all went well until it try to search something on the cd, but since im using a usb i ignore it then it said successfully installed. then restart after the restart it did not boot displaying only a blinking line. then i tried boot repair using the default recommended but still no luck, as of typing this i am using live usb to boot

---

### Post by mastergkage on 2012-01-27
before the restart here what i got "An attempt to configure apt to install additional packages from the cd failed" then it said installation complete then after restart its booting only black screen with blinking cursor

---

### Post by SuaSwe on 2012-01-27
Hi mastergkage!

This appears to be a bug, at least it used to be on 10.10. I've looked around a bit and the workaround used in 10.10 seems to also have been successful on 11.10 - see [this link]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/658865") for details. I would suggest following the steps outlined there. :)

---

### Post by mastergkage on 2012-01-27
Is there still any other way, too complicated for me., i have found something about configuring the grub to quite splash nomodeset

---

### Post by mastergkage on 2012-01-27
I am searching the forums and google for the past two days on how to solve my problem 

I have tried
1.Using boot recovery recommended and advace. still does not work.
2. I tried to set it in nomodeset quite splash still not booting from hardisk.
3. I tried to boot in recovery mode but after the loading of text i see kernel panic and it hang. 

Im getting frustrated and inspired at the same time that it challenges my ability and everyday im learning something new too bad the laptop is not mine i just convince this friend of mine to try linux and this what happened the laptop model is toshiba u500

---

### Post by SuaSwe on 2012-01-28
Hi mastergkage,

I haven't experienced this particular issue myself, but the simplest suggestion in that bug link I submitted above appears, if I'm reading it correctly, to be:

1. boot into a LiveCD environment and opt for Try Ubuntu
2. once in the live desktop environment, go to Terminal and type in
```

sudo rm /usr/lib/ubiquity/apt-setup/generators/40cdrom

```
3. click Install Ubuntu and run through the install as normal

It is a known bug which from the looks of it is due to be resolved in 12.04; in order to get round it you probably will need to follow instructions relevant to the bug.

---

### Post by mastergkage on 2012-01-28
> **SuaSwe said:**
> Hi mastergkage,

I haven't experienced this particular issue myself, but the simplest suggestion in that bug link I submitted above appears, if I'm reading it correctly, to be:

1. boot into a LiveCD environment and opt for Try Ubuntu
2. once in the live desktop environment, go to Terminal and type in
```

sudo rm /usr/lib/ubiquity/apt-setup/generators/40cdrom

```
3. click Install Ubuntu and run through the install as normal

It is a known bug which from the looks of it is due to be resolved in 12.04; in order to get round it you probably will need to follow instructions relevant to the bug.

WWWWOOOOOOOOOOOWWWWWWWWWWWWWWWW!!!!!!! This code is awesome after following what you said this solve my problem thats bugging me for two days ahaha I almost jump back inside the windows :P After this everything went well and customizing my desktop Special thanks to you!! 

And Thank you of course to the guy who patiently try to help me and gave their suggestion, now whenever I'm doing a personal computing at home I will be using ubuntu, only at work windows and also guess what for two days of tinkering with ubuntu at home trying to make this work one of my room mate ask me to install ubuntu on his computer my first convert :popcorn: Because of your help I can now proudly install ubuntu on his laptop 

More Power to the Ubuntu Community!!!

PROBLEM:SOLVE!!!

---

### Post by Kixtosh on 2012-01-28
Great stuff! 

Please mark your thread as SOLVED (only you can do it, since you started it). Click on **[COLOR=Red]Thread Tools [/COLOR]**[COLOR=Black]on the top right of the thread itself to find that option.[/COLOR]

---

### Post by varunendra on 2012-01-29
> **mastergkage said:**
> before the restart here what i got "An attempt to configure apt to **install additional packages** from the cd failed"
The recommended way to avoid the possibility of such issues is to **NOT check the box** that says "Install Additional Packages" during installation (the stage just before starting the actual installation).

Hope it adds some "more power" ;)

Now please do as *Kixtosh *asked above (and my sig suggests below).

---

### Post by mastergkage on 2012-01-30
So that's how you mark it as solved thanks guys

---

