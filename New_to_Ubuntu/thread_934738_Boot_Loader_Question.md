---
title: "Boot Loader Question"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by tjkoch on 2008-09-30
Hey all, 

Ok I setup my bootloader to use Windows as Default if no choice is picked, but I was wondering if there was a way to completely avoid the bootloader screen and automatically go to Windows every time, and if I want to boot Linux I would press a key at a certain time?  I'm just doing this to make things a bit easier on my wife she gets confused by this stuff.

If that's not possible is it possible to have your bootloader on a usb stick instead of on one of your hd's and when you want to load linux you just put your stick in? This will make my Windows boot ups much quicker and wont confuse my wife either. I think the USB idea would be better.

---

### Post by WWSmith36 on 2008-09-30
You have to edit your /boot/grub/menu.lst file

From the terminal type

```
gksudo gedit /boot/grub/menu.lst
```

Find the line that says
#hiddenmenu

and uncomment it by changing it to
hiddenmenu

Save and exit.  Now you will have to hit ESC key to get into grub boot menu
Hope this helps

---

### Post by tjkoch on 2008-10-01
Thanks for the info. Is the bootloader on a usb stick a valid idea or does it make no sense since this will also cut down boot times?

---

### Post by lisati on 2008-10-01
> **tjkoch said:**
> Thanks for the info. Is the bootloader on a usb stick a valid idea or does it make no sense since this will also cut down boot times?

While you're looking at the menu.lst file, look for an entry "timeout". You can change it to any value you want - a smaller value will result in a marginally quicker boot time, but be careful of making it '0' as this can make it difficult to select a different OS on boot up

---

### Post by gotanothergrot on 2008-10-01
This is useful to me also however , how would i get vista to boot by default instead of ubuntu, as my 9 year old has an account with the former OS.

many thanks

---

### Post by tarps87 on 2008-10-01
Open up the menu.lst file:
```
sudo gedit /boot/grub/menu.lst
```
Then you'll need to find where vista/longhorn is listed move this section under the heading default os and move the Ubuntu section to under the heading other os's. I'm not am my Ubuntu machine so I can show you an example but is you post you menu.lst file I can show you what bits you will need to change

---

### Post by Dacker on 2008-10-01
i've question about this issue,...  

i know that when you install windows on linux the boot loader will not be there, i've tried to deal with the issue under the dos and used partition magic and fdisk to active this and unactive that but the problem comes worse and the boot master RBM has gone........  right now i fixed on but my question roaming around how can i install windows on linux ??????  

note:
  not because that i would like to install windows:-& but just to know how ??

---

### Post by tarps87 on 2008-10-01
Have a look at:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
there is also another good link in a thread somewhere but it can't find it at the moment

---

### Post by caljohnsmith on 2008-10-01
> **tjkoch said:**
> 
If that's not possible is it possible to have your bootloader on a usb stick instead of on one of your hd's and when you want to load linux you just put your stick in? This will make my Windows boot ups much quicker and wont confuse my wife either. I think the USB idea would be better.
In case you want to pursue the idea of putting your boot loader on a USB stick, it is definitely possible to do that. That way you could reinstall the Windows boot loader on your HDD and Windows will always boot on start up unless you have your USB stick connected, and then you would boot to the USB stick instead (assuming your BIOS supports booting USB devices). If you want to pursue this, please post the output of:
```
sudo fdisk -l
```
While you have your USB stick connected.

---

### Post by tjkoch on 2008-10-01
Caljohnsmith: 

I typed that command with my usb stick installed but I'm getting this error:

sudo: fdisk: command not found

Any idea why I don't have fdisk?

---

### Post by drs305 on 2008-10-01
The simplest way to do what you want is to use a boot editor called StartUp-Manager. You can use the gui app to set Windows as the default OS, set the menu display time, or even let it boot automatically without ever seeing the menu (timeout=0). As mentioned, this would prevent you from seeing other options, but it sounds like that may be what you want. If that is how you decide to do it, you regain access to the menu by hitting ESC during the early stage of the boot and the options will appear. (Personally I'd leave it at 1 second).

Visit this tutorial link for information on how to install and use StartUp-Manager:
[StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by caljohnsmith on 2008-10-01
Are you running that command from a terminal (applications > accessories > terminal) while you are in Ubuntu?

---

### Post by tjkoch on 2008-10-01
Caljohnsmith: Yes, I tried it as root also and it didn't work.

---

### Post by kansasnoob on 2008-10-01
> **drs305 said:**
> The simplest way to do what you want is to use a boot editor called StartUp-Manager. You can use the gui app to set Windows as the default OS, set the menu display time, or even let it boot automatically without ever seeing the menu (timeout=0). As mentioned, this would prevent you from seeing other options, but it sounds like that may be what you want. If that is how you decide to do it, you regain access to the menu by hitting ESC during the early stage of the boot and the options will appear. (Personally I'd leave it at 1 second).

Visit this tutorial link for information on how to install and use StartUp-Manager:
[StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

+1 ....... so simple:

[ATTACH]86996[/ATTACH]

Select default OS, untick Show bootloader menu, reduce the timeout to say 3 seconds .............. then just watch closely when it's booting up if you want to get into grub and hit esc.

---

