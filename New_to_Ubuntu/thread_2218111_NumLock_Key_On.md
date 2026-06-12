---
title: "NumLock Key On"
date: 2014-04-19
forum: New to Ubuntu
---

### Post by tb75252 on 2014-04-19
I am using Ubuntu 14.04 LTS, 64-bit.

How do I get the NumLock key to be automatically turned on after booting up but **_before_** the login screen?  There is an option in the BIOS for such thing but it does not seem to have any influence in Ubuntu...

---

### Post by naxiz on 2014-04-19
Hey,

I found [this]("https://help.ubuntu.com/community/NumLock") help page.

These steps will probably do the trick:

```
sudo apt-get install numlockx
sudo sed -i 's|^exit 0.*$|# Numlock enable\n[ -x /usr/bin/numlockx ] \&\& numlockx on\n\nexit 0|' /etc/rc.local
```

---

### Post by tb75252 on 2014-04-19
> **naxiz said:**
> Hey,

I found [this]("https://help.ubuntu.com/community/NumLock") help page.

These steps will probably do the trick:

```
sudo apt-get install numlockx
sudo sed -i 's|^exit 0.*$|# Numlock enable\n[ -x /usr/bin/numlockx ] \&\& numlockx on\n\nexit 0|' /etc/rc.local
```
Unfortunately numlockx does not seem to achieve my goal...

To further clarify my initial post:  I would like to have the NumLock key automatically turned on right after the GRUB2 selection and before the Ubuntu login screen.

---

### Post by migs73 on 2014-04-19
I take it you want this as your login password has numbers in it.

I think this might be what you are looking for;
[https://answers.launchpad.net/lightdm/+question/173666]("https://answers.launchpad.net/lightdm/+question/173666")

---

### Post by tb75252 on 2014-04-19
> **migs73 said:**
> I take it you want this as your login password has numbers in it.

Yes, that's exactly it!> 
I think this might be what you are looking for;
[https://answers.launchpad.net/lightdm/+question/173666](https://answers.launchpad.net/lightdm/+question/173666)
I tried the following commands:
```
sudo gedit /etc/lightdm/lightdm.conf
greeter-setup-script=/usr/bin/numlockx on
``` ...but that did not get along with the NVIDIA driver that I have installed.  Basically, after selecting Ubuntu from the GRUB menu it was giving me a blank screen.  Had to boot up with the Live DVD, mount the Ubuntu root directory, chroot into it and delete the:
```
greeter-setup-script=/usr/bin/numlockx on
``` command.

---

### Post by migs73 on 2014-04-22
Did you still have numlockx installed when you got this issue?

---

### Post by tb75252 on 2014-04-22
> **migs73 said:**
> Did you still have numlockx installed when you got this issue?
Yes, since the command references numlockx I reasoned that it would not be a good idea to uninstall it.

---

### Post by migs73 on 2014-04-22
Lol!
Just checking! Might have been an easy fix.

:)

---

### Post by grumblebum2 on 2014-04-22
This is constantly changing.
In 14.04 this works for me.
```
gksudo gedit /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
```
...and add at the end this line...
```
greeter-setup-script=/usr/bin/numlockx on
```

 **/usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf** should now look like...
```
[SeatDefaults]
greeter-session=unity-greeter
**greeter-setup-script=/usr/bin/numlockx on**
```

You should probably delete the **/etc/lightdm/lightdm.conf** file you created before.
You may need to restart.

---

### Post by tb75252 on 2014-04-23
> **grumblebum2 said:**
> This is constantly changing.
In 14.04 this works for me.
```
gksudo gedit /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
```
...and add at the end this line...
```
greeter-setup-script=/usr/bin/numlockx on
```

 **/usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf** should now look like...
```
[SeatDefaults]
greeter-session=unity-greeter
**greeter-setup-script=/usr/bin/numlockx on**
```

You should probably delete the **/etc/lightdm/lightdm.conf** file you created before.
You may need to restart.
It worked!  Thank you very much everybody for the help.  I really appreciate it.

---

### Post by ksor on 2014-05-05
> **tb75252 said:**
> Unfortunately numlockx does not seem to achieve my goal...

To further clarify my initial post:  I would like to have the NumLock key automatically turned on right after the GRUB2 selection and before the Ubuntu login screen.

For me it's the same problem in Lubuntu 14.04 which I just installed, and I've tried all the methods described here [https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock) - NONE of them works in my Lubuntu 14.04 - so I'm very frustrated !

Any idea what is going wrong in Lubuntu compared with Ubuntu ?

---

### Post by LifeEnemy on 2014-05-26
I have 14.04 and don't need to have the numlock on before the start screen. Where can I find the keyboard layout settings in the linked help article? They don't seem to exist for me.

---

### Post by rom117 on 2014-12-18
> **grumblebum2 said:**
> This is constantly changing.
In 14.04 this works for me.
```
gksudo gedit /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
```
...and add at the end this line...
```
greeter-setup-script=/usr/bin/numlockx on
```

 **/usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf** should now look like...
```
[SeatDefaults]
greeter-session=unity-greeter
**greeter-setup-script=/usr/bin/numlockx on**
```

You should probably delete the **/etc/lightdm/lightdm.conf** file you created before.
You may need to restart.


This worked for me but I used the file **60-lightdm-gtk-greeter.conf**, 50-unity-greeter.conf does not exist**.**

(I am using LUbuntu 14.04.1 LTS)

---

### Post by Llyffant on 2015-02-20
I'm a total newb, running the 14.04, and have previously solved this problem, but after a recent update, it reverted back to numlock being disabled on startup - so frustrating - why don't Canonical know people want to keep their settings when there's an update?!

And I couldn't remember what I did a few months ago, so was back to square one.
```
gksudo gedit /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
```
didn't work for me, even after installing gksudo or whatever it is
```
sudo gedit /etc/lightdm/lightdm.conf
```
just returned an error and a blank file, but 
```
sudo gedit /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
```
(note the missing gk at the start) finally opened the file I need, and enabled me to paste in:

greeter-setup-script=/usr/bin/numlockx on

If anyone in the know feels like offering a technical explanation to what I've found, I'd be interested. Thanks!

---

