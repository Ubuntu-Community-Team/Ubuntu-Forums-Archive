---
title: "Help! I don't know how to install linux on a laptop"
date: 2012-06-28
forum: New to Ubuntu
---

### Post by minecraftlogics on 2012-06-28
I have a laptop with windows vista, the os is corrupt. I installed ubuntu on a flash drive, i unzipped it on that drive and deleted the zip file (it is backed up) My laptop wont reganize it. What do i do? I am selecting boot from usb diskatte

---

### Post by oldfred on 2012-06-28
You cannot extract but have to install so it includes all the boot files.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by zealibib slaughter on 2012-06-28
you need to make the flash drive bootable using unetbootin. Download the exe run it and tell it where to find your ubuntu iso. It will do the rest. When it finishes reboot and select the flash drive from your boot menu.

---

### Post by minecraftlogics on 2012-06-28
My HP laptop has Vista on it but for several reasons I want Ubuntu as the only OS. The laptop BIOS will let me boot from a flash drive so I wanted to put Ubuntu on the flash drive and install from it. Is that possible.

---

### Post by robtygart on 2012-06-28
> **minecraftlogics said:**
> My HP laptop has Vista on it but for several reasons I want Ubuntu as the only OS. The laptop BIOS will let me boot from a flash drive so I wanted to put Ubuntu on the flash drive and install from it. Is that possible.

Yes it is, you need to follow the instructions above. Try UNetbootin [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

You can slect Ubuntu from the menu or you can use the one you already downloaded.



My HP laptop with Vista was the first computer that I put Linux on, I will not go back, it runs a lot smoother.

---

### Post by minecraftlogics on 2012-06-28
> **robtygart said:**
> Yes it is, you need to follow the instructions above. Try UNetbootin [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

You can slect Ubuntu from the menu or you can use the one you already downloaded.



My HP laptop with Vista was the first computer that I put Linux on, I will not go back, it runs a lot smoother.

Thanks, it is downloading right now.

---

### Post by minecraftlogics on 2012-06-28
> **robtygart said:**
> Yes it is, you need to follow the instructions above. Try UNetbootin [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

You can slect Ubuntu from the menu or you can use the one you already downloaded.



My HP laptop with Vista was the first computer that I put Linux on, I will not go back, it runs a lot smoother.

Is that program to prep the drive for booting, or to download and reboot the computer it downloaded on with linux?

---

### Post by robtygart on 2012-06-28
Everything to make it boot will be on Unetbootin.

If you want to use the operating system (ISO) you downloaded then choose "Diskimage" and browse for the ISO. On the bottom were it says Type: USB drive, and check to see if the dirve letter is the same as the one you wish to install on, click OK and Follow along with the program. When its finished it should tell you to restart. 

[IMG]http://sourceforge.net/apps/trac/unetbootin/raw-attachment/wiki/MiscWikiFiles/unetbootin-windows7.png[/IMG]

---

### Post by robtygart on 2012-06-29
> **minecraftlogics said:**
> Is that program to prep the drive for booting, or to download and reboot the computer it downloaded on with linux?

I read your post again, I understand now. 

This program will do everything. Put the operating system onto the USB and make it bootable. 

After using it all you need to do is reboot and it will load the OS so you can try it or install.

---

### Post by mastablasta on 2012-06-29
yes and the boot order in bios ofcourse has to be set to boot from USB first.

---

### Post by minecraftlogics on 2012-06-29
I got it, thanks. Now I have one more problem, how do I install java?

---

### Post by black veils on 2012-06-29
last time i knew, you install ```
ubuntu-restricted-extras
``` to inclusively get java

---

### Post by minecraftlogics on 2012-06-29
> **black veils said:**
> last time i knew, you install ```
ubuntu-restricted-extras
``` to inclusively get java

I don't understand

---

### Post by black veils on 2012-06-29
> **minecraftlogics said:**
> I don't understand

well i may be wrong anyway, things have changed. take a look at this thread [http://ubuntuforums.org/showthread.php?t=1977010](http://ubuntuforums.org/showthread.php?t=1977010)

it will help you understand the java situation.

as for not understanding what i posted, it was a reference to a package which can be installed through **Synaptic**, and maybe the **Software Centre**.

---

### Post by minecraftlogics on 2012-06-29
> **black veils said:**
> well i may be wrong anyway, things have changed. take a look at this thread [http://ubuntuforums.org/showthread.php?t=1977010](http://ubuntuforums.org/showthread.php?t=1977010)

it will help you understand the java situation.

as for not understanding what i posted, it was a reference to a package which can be installed through **Synaptic**, and maybe the **Software Centre**.

I don't need the jdk, i just need java to play minecraft

---

### Post by black veils on 2012-06-29
scroll down to "adding this ppa to your system"

[https://launchpad.net/~webupd8team/+archive/java]("https://launchpad.net/~webupd8team/+archive/java")

---

### Post by blackbird34 on 2012-06-29
...And btw, "ubuntu-restricted-extras" is a bunch of things (mp3 and flash support for example) that can't be included in the base Ubuntu install for legal reasons, Java may be among these.

---

### Post by robtygart on 2012-06-30
> **minecraftlogics said:**
> I don't need the jdk, i just need java to play minecraft

You can access software to install from the Ubuntu Software center, it is the orage paper-looking bag. Type "Ubuntu Restricted extras" or type "Java". I don't know about "OpenJDK Java" I haven't tried it.

---

