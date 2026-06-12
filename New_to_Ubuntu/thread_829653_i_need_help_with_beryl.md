---
title: "i need help with beryl"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by ktotheherm on 2008-06-15
i really am pretty confused. i am usally good at computer stuff but i just started this so i need some help installing beryl and i barely know anything about ubuntu. thx so much for all the help

---

### Post by akiratheoni on 2008-06-15
If you have 7.10 or 8.04, Compiz-Fusion is already pre-installed. Make sure your video card drivers are installed and updated (there are guides for particular cards, search it up) and then go to System -> Preferences -> Visual Effects.

Beryl is outdated though, it merged back with Compiz-Fusion.

---

### Post by dnns123 on 2008-06-15
If thats 8.04, I its called Compiz Fusion
Install CCSM from the add/remove if you want to tinker with it

---

### Post by quinnten83 on 2008-06-15
> **dnns123 said:**
> If thats 8.04, I its called Compiz Fusion
Install CCSM from the add/remove if you want to tinker with it

and the compiz fusion icon, which makes it even more manageable.

---

### Post by MattBD on 2008-06-15
And don't forget Emerald, that's worth having as well. But compizconfig-settings-manager is absolutely essential to get the most out of it.

---

### Post by steveneddy on 2008-06-15
Beryl is dead.

Compiz rocks and is pre-installed on your PC.

[Look here]("http://ubuntuforums.org/showthread.php?t=799070") for help.

[Read this]("http://www.compiz-fusion.org/") also. 

If you have an nVidia video card or ATI vid card, you may already be set.

Go to

**[COLOR="Blue"]System --> Preferences --> Appearance[/COLOR]**

and select the **Visual Effects** tab.

Click the **Extras** box, and if you are actually able to run Compiz, your whole world will change.

If it works, try moving a window around. Does it seem like jello?

Hold down the Ctrl+Alt keys while pressing on the left mouse button, now move the mouse.

Whoa! Check it out!

---

### Post by ktotheherm on 2008-06-15
ok i went to that link and downloaded the check program now how do i run the check? srry about my stupidity

---

### Post by st33med on 2008-06-15
You shouldn't need the check. Read the users post above you.

---

### Post by ktotheherm on 2008-06-15
i went to appearance and it wouldnt work so i am trying to see y it didnt work

---

### Post by steveneddy on 2008-06-15
> **ktotheherm said:**
> ok i went to that link and downloaded the check program now how do i run the check? srry about my stupidity

According to the thread, the link to the instructions and more about Compiz-Check are```
http://forlong.blogage.de/article/pages/Compiz-Check
```.

From the web page that I linked above:

> 
Get it here and follow the instructions how to use it: [http://forlong.blogage.de/article/pages/Compiz-Check](http://forlong.blogage.de/article/pages/Compiz-Check)


I guess you missed that part.

It's only a small script to see if your system is up to the task of running Compiz.

Tell us more about your system.

Processor

Video Card

System Memory

---

### Post by RomeReactor on 2008-06-15
Hi. Which version of Ubuntu are you running? Can you tell us more about your system--which video card it has, processor, amount of memory? If you're unsure about those, please write or paste the following in a terminal (Applications->Accessories->Terminal):
```
sudo lshw -C display
```
and press ENTER, then paste the output here. Afterwards run this:
```
glxinfo | grep rendering
```
and post the output of that as well.

---

### Post by ktotheherm on 2008-06-15
first of all i want to thank all of you for helping me.
processor: amd athlon x2 4400 oced at 2.4 
Video Card: MSI RX2400pro
RAM: 3gb dual channel

---

### Post by RomeReactor on 2008-06-15
I don't have experience with ATI cards, but try going to 'System->Administration->Restricted Drivers Manager' (in 7.10) or 'System->Administration->Hardware Drivers' (in 8.04) and enable the drivers for your card there. Then go to 'System->Preferences->Appearance' and on the Visual Effects' tab check 'Normal'.

Also post the output of running the following in the terminal (Applications->Accessories->Terminal):
```
cat /etc/X11/xorg.conf | grep Driver
```
and:
```
glxinfo | grep rendering
```

---

### Post by ktotheherm on 2008-06-15
Driver		"kbd"
	Driver		"mouse"
	Driver		"fglrx"
direct rendering: Yes

---

### Post by RomeReactor on 2008-06-15
According to the output, the fglrx driver is being used, which as far as I know is the correct one. 'Direct Rendering: Yes' means you have hardware acceleration enabled, so you *should* be able to run the effects. I don't know if this is still the case, but in previous versions you needed to install **xgl** to be able to run the desktop effects.

As others have commented in the first page, Beryl is discontinued; it has been merged with the original Compiz and is now called Compiz Fusion, which comes pre-installed in Ubuntu 7.10 and 8.04. To enable it, try the steps in my previous post.

---

### Post by ktotheherm on 2008-06-15
thank you i got the extra to work but i dont know how to download and run the desktop managers so i can customize it

---

### Post by ktotheherm on 2008-06-15
another question i am trying to download flash player and i dont know which one to download. it gives me three options .tar.gz, .rpm, YUM

---

### Post by RomeReactor on 2008-06-15
You can install **compizconfig-settings-manager**; you can find it in Synaptic (System->Administration->Synaptic) or to install it from the terminal:
```
sudo aptitude install compizconfig-settings-manager
```
Once it's installed, you can find it in 'System->Preferences->Advanced Desktop Effects Settings'.

As for Flash, you don't need to install it manually; go to a page that requires Flash--such as Youtube--and Firefox will offer to install it for you. After it's installed, close Firefox and open it again, and Flash should work then. Just make sure you choose Flash and not Gnash, if Firefox offers you that choice. Also. make sure Gnash isn't installed on your system, as it conflicts with Flash:
```
sudo aptitude purge gnash gnash-common mozilla-plugin-gnash
```

---

### Post by JoshuaRL on 2008-06-15
> **ktotheherm said:**
> another question i am trying to download flash player and i dont know which one to download. it gives me three options .tar.gz, .rpm, YUM

Okay, first go into System->Administration->Software sources.  Make sure everything except the install CD and source code is enabled, and then put this command into the terminal:
```

sudo apt-get install ubuntu-restricted-extras

```

And please, **please,** what version of Ubuntu are you using?

---

### Post by ktotheherm on 2008-06-15
thx i got it working but i only have two sides to my cube not 4 how do i fix that

and i am using the latest version

---

### Post by JoshuaRL on 2008-06-15
You'll need to change the amount of virtual desktops you have.  4 is a cube, 5 is a pentagon, and n-desktops is an n-gon.

---

### Post by ktotheherm on 2008-06-15
yes and you do that how

---

### Post by RomeReactor on 2008-06-15
In 'Advanced Desktop Effects Settings' go to 'General Options' and on the 'Desktop Size' tab increase the 'Horizontal Virtual Size' to 4. Press the 'Back' arrow and, still in Advance Desktop Effects Settings, scroll down to the Desktop section, uncheck 'Desktop Wall' and check 'Desktop Cube' and 'Rotate Cube'.

---

