---
title: "Ubuntu boots to text screen"
date: 2012-09-01
forum: New to Ubuntu
---

### Post by zeb123dee on 2012-09-01
Hi Im new here, I so want to like ubuntu, Ive been trying it off and on for a few years but had so many problems with things not working, but now really getting fed up with windows so giving a good go and deleted windows.

At first I couldnt even load the install disk as it didnt like my wireless card, so removed that from the machine.

I am using Ubuntu 12.04 and liking it so far, but after upgrading the graphics driver from NVIDIA my machine will only boot up to a text screen.

It was working ok but when I tried to use a dual screen set up the display program said my display was "laptop" and no option for dual screen, its not a laptop its a desktop with 23 inch DVI screen, so thought to upgrade the graphic card driver. I downloaded the graphics card driver from NVIDIA web site which when I followed the instructions and went to a text screen (ctrl+alt+F1) said to stop the "x server".  Did that with "sudo service lightdm stop", then ran the .exe ("sudo sh <filename>") file and went through all the prompts, now when I boot I cant get to Unity (ctrl+alt+F7) its just always just text.

Please help, I really want to like this, love how quick it starts and shuts down.

---

### Post by anewguy on 2012-09-01
Try adding nomodeset to the boot line - if that works we can make it permanent.

---

### Post by zeb123dee on 2012-09-01
sorry not sure I understand, I am very new at this.

My machine boots to a prompt
<machine name> login:
where I enter my name and password
then get  prompt
<myname>@<machinename>:~$
where I typed "nomodeset"
but it said "command not found"

guess Im doing something wrong

---

### Post by anewguy on 2012-09-01
No, it actually goes in the boot line - you have to edit the bootline. There is a how-to for that in the forums - just search on nomodeset.

---

### Post by zeb123dee on 2012-09-01
searched for nomodeset but just got lots of threads like mine, no help on how to do it.

think I stumbled on editing the boot as when I start it has an option "e" and was able to edit and put nomodeset at the end and then did ctrl&x

but it said unknown command nomodeset and the screen just went to a rainbow of colours.

Getting really fed up now with ubuntu, windows is starting to look a good option again

---

### Post by Ubun2to on 2012-09-01
Can you get to the GUI via this command?
```
sudo service lightdm restart
```

---

### Post by Gone fishing on 2012-09-01
I was wondering what would happen if you ran the startx command - you could then see the errors. However, I would suggest where you went wrong was to download the driver from the nvidia site rather than using the nvidia driver in the repositories just click aditional drivers and let it do its magic.

Probably the easiest fix would be to start in failsafe mode and then select continue normal boot which will probably bypass the troublesome driver or select failsafex. Once you are in graphical mode then use the additional drivers utility.

---

### Post by zeb123dee on 2012-09-01
Tried doing
sudo service lightdm restart
and it said that NVIDIA kernal had version x but this NVIDIA driver was y.

But as regards the original advice with nomodeset, found the following post and did that and display is now good across two monitors, but how do I change the grub file as per its second advice to make permanent as it says I dont own grub?????

*************************************************
Looking good. Let's get you logged into your system, and see what we have to do yet (if anything).
First things first: Boot to your installed system, just after the bios screen clears - hold down the shift key to enable ubuntu's boot options screen. The default kernel should be highlighted at this point. Press the "e" key to edit the boot parameters. Now, look for the line similar to this: /linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash $vt_handoff // : With the arrow key arrow down to this line, and arrow across to "quiet splash" after quiet splash ..insert "nomodeset" by typing nomodeset . ctl-x to continue booting. Do you boot to your login ?

If you boot to the login screen, go ahead and log into your system. Do you like what you see ? If you like your graphics as it is now .... all that is left to do is make the nomodset permanent by editing your /etc/default/grub file to reflect the above. Else, install alternate graphics drivers.

---

### Post by phibxr on 2012-09-01
> **zeb123dee said:**
> Tried doing
sudo service lightdm restart
and it said that NVIDIA kernal had version x but this NVIDIA driver was y.


Are you really running 12.04? Please paste the output of the following command:

```
$ lsb_release -d
```

---

### Post by zeb123dee on 2012-09-01
> **phibxr said:**
> Are you really running 12.04? Please paste the output of the following command:

```
$ lsb_release -d
```


zebedee@study:~$ lsb_release -d
Description:    Ubuntu 12.04 LTS
zebedee@study:~$

---

### Post by zeb123dee on 2012-09-01
ok, managed to edit /boot/grub/grub.cfg with "nomodeset"
and now boots ok with good graphics accros two screens
one other problem with booting I have caused.....but that can wait until tomorrow thanks for all the help

---

### Post by anewguy on 2012-09-02
I was out for a while so sorry I missed your reply needing more help with nomodeset.  Glad that at least worked for you, and good job looking it up and fixing it yourself!

---

### Post by zeb123dee on 2012-09-02
Thanks for your help.  Not easy trying to learn new things but this forum and google seem to do the trick.

---

### Post by JKyleOKC on 2012-09-02
> **zeb123dee said:**
> how do I change the grub file as per its second advice to make permanent as it says I dont own grub?????Type this into a terminal window:```
gksudo gedit /etc/default/grub
```It will ask for your login password, then open gedit with super-user privileges so that you can edit grub's defaults. Find the line that contains "quiet splash" and add "nomodeset" after "splash" then save the file and run "sudo update-grub" to rewrite your grub configuration.

Alternatively, you can install grub-customizer and use it directly in the GUI. It will do the same thing, but will hide the details from you and there will be less chance for something to go wrong.

---

### Post by anewguy on 2012-09-03
+1.  The reason for this is that the file you changed is a generated file.  Doing as JKyleOKC says is the correct way - you edit a configuration file, then run updage-grub - it will generate the the new file.  Hope you're doing fine JKyleOKC!

---

