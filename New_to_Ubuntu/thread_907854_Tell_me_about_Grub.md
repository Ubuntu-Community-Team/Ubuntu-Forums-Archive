---
title: "Tell me about Grub"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by jfbays on 2008-09-01
This is truly an "Absolute Beginner" question: 

As far as I can tell, Grub is what loads the OS.  Is this correct?  Tell me more.  Also, I have come across a few posts where someone wants to remove Grub.  Why?  What are the advantages and dis-advantages of Grub?

---

### Post by jemate18 on 2008-09-01
> **jfbays said:**
> This is truly an "Absolute Beginner" question: 

As far as I can tell, Grub is what loads the OS.  Is this correct?  Tell me more.  Also, I have come across a few posts where someone wants to remove Grub.  Why?  What are the advantages and dis-advantages of Grub?

Is this what you're looking for? This might help
> [http://tldp.org/HOWTO/Multiboot-with-GRUB.html](http://tldp.org/HOWTO/Multiboot-with-GRUB.html)

---

### Post by jemate18 on 2008-09-01
Also this. The official GRUB site
> [http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)

---

### Post by OutOfReach on 2008-09-01
You are correct, GRUB is a boot loader. People generally want to remove it because they have uninstalled Ubuntu or any other Linux distro and want their computer to boot to Windows automatically.

---

### Post by jfbays on 2008-09-01
Thanks fellows.  At this point, I have a dedicated Ubuntu machine.  And I find that I'm on it 95% of the time.  So I do not need any dual-boot capability.  Yet, Grub still boots my computer.  Is this normal?  Or is there a point -- when Ubuntu is the only OS -- that one no longer needs Grub?

---

### Post by doorknob60 on 2008-09-01
No, you need GRUB (or LILO, but GRUB does about the same thing) to load Ubuntu, it's just that when you use Windows only you don't need it.

---

### Post by dRock1286 on 2008-09-01
It also helps when new kernels are released.  For example..I was running virtualbox that didn't work with a new kernel version so, from the GRUB menu, I could choose the older kernel to run so I could run VBox until it was updated.  So, it does serve it's purpose sometimes.

---

### Post by OutOfReach on 2008-09-01
> **jfbays said:**
> Thanks fellows.  At this point, I have a dedicated Ubuntu machine.  And I find that I'm on it 95% of the time.  So I do not need any dual-boot capability.  Yet, Grub still boots my computer.  Is this normal?  Or is there a point -- when Ubuntu is the only OS -- that one no longer needs Grub?

Yes you will still need GRUB, without it you wouldn't be able to boot into Ubuntu. :)

---

### Post by jfbays on 2008-09-02
Grub menu?  Where the heck is that? Seriously...

---

### Post by dRock1286 on 2008-09-02
The menu is what is loaded.  Sometimes you have to hit a button to see it...I don't know, I think mine pops up automagically...  :S  sorry

---

### Post by egalvan on 2008-09-02
> **jfbays said:**
> Thanks fellows.  At this point, I have a dedicated Ubuntu machine.  And I find that I'm on it 95% of the time.  So I do not need any dual-boot capability.  Yet, Grub still boots my computer.  Is this normal?  Or is there a point -- when Ubuntu is the only OS -- that one no longer needs Grub?

As others have said, Linux uses grub to load.

Now if you only use Linux, and want the grub menu to be hidden,
then you can edit **/boot/grub/menu.lst** and un-comment the "hiddenmenu".
Remove # mark to the line that says "hiddenmenu" with only ONE hashmark

in a terminal type

```
gksudo gedit /boot/grub/menu.lst
```

then find the following lines (about 22 lines down)

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR="Red"]# hiddenmenu[/COLOR]
```

change to

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR="Red"] hiddenmenu[/COLOR]
```


and grub will be "silent".

---

### Post by xeth_delta on 2008-09-02
[EDIT] Posted late. For a better explanation see the post just above.
> **jfbays said:**
> Thanks fellows.  At this point, I have a dedicated Ubuntu machine.  And I find that I'm on it 95% of the time.  So I do not need any dual-boot capability.  Yet, Grub still boots my computer.  Is this normal?  Or is there a point -- when Ubuntu is the only OS -- that one no longer needs Grub?

As has been mentioned grub is a boot loader, hence, regardless of how many operating systems you have on your machine, one (grub or whichever other boot loader) is needed. The same is valid also for Microsoft products, only that, it will not show any menu when there's only one OS installed (or so used to be some time ago, I don't know if that's the case with their newer OSs).

Regarding the menu, you can choose whether it should appear on screen automatically. In any case, you should be able to make it visible at boot time by pressing ESC when presented with the option.

---

### Post by egalvan on 2008-09-02
> **jfbays said:**
> Grub menu?  Where the heck is that? Seriously...

When you boot your computer, grub loads and then, depending on its settings, will display a "menu" of boot options.

Grub can be set to display this menu, or not.

When you install linux to a machine that already has another (known) operating system, grub will add it to the menu, and display the menu on boot.

When you install linux to a machine with no other known OS's, then grub will "hide" the menu, since there is only one option.
although, technically, there are other boot options, such as "repair", 
"memtest", other kernels, etc


these settings can be changed. see my prev post

Also the colors, blinking, etc...

---

### Post by jfbays on 2008-09-02
Oh yeah, I've seen that.  Thanks everyone.  Bye for now.

---

### Post by Marcke on 2008-09-02
> **OutOfReach said:**
> You are correct, GRUB is a boot loader. People generally want to remove it because they have uninstalled Ubuntu or any other Linux distro and want their computer to boot to Windows automatically.

How do I do this?

I have my Ubuntu still installed, but want Windows to boot automatically.

---

### Post by kansasnoob on 2008-09-02
> **Marcke said:**
> How do I do this?

I have my Ubuntu still installed, but want Windows to boot automatically.

Assuming that both Ubuntu and Windows are currently bootable and you only want to change which OS boots by default I'd install startupmanager which is in synaptic:

```
sudo apt-get install startupmanager
```

It'll then show up in System > Administration > Startup Manager

[ATTACH]83766[/ATTACH]

You see where it says Default Operating System you can click on the toggle to the right and select which OS or Kernel to boot by default. You can also select how many kernels to display, change timeout value, etc.

---

### Post by Marcke on 2008-09-02
> **kansasnoob said:**
> I'd install startupmanager which is in synaptic:

Thank you for the tip.

I suppose I need an internet connection to use synaptic? If so, 

I haven't been able to make my wireless work yet though. I have a TKIP/AES protection, MAC-filtering and disabled the SSID broadcast on my wireless modem. Where can I install the wireless and add this data?

Thanks for your help.

---

