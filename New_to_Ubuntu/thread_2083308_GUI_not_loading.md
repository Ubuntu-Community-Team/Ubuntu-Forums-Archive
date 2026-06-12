---
title: "GUI not loading"
date: 2012-11-12
forum: New to Ubuntu
---

### Post by pras8421 on 2012-11-12
Hi, . . 
 
A small problem occurred today in my ubuntu 12.04 which is installed inside windows 7 using wubi.

I have installed kde in it and everything including even the login screen has been changed.
Today I thought of upgrading to 12.10.
As it was runmand.
It asked me somening outta memory I wanted to uninstall kde and did run a long comthing in the middle that kde daemon is default and do you want to remove it(something like, I don't remember exactly)
I selected yes.

This is how the actual problem started. 

If I now select ubuntu normal boot at the startup, a dialogue box appears saying your computer is running in low graphics mode, press okay to manually configure. The kde startup wheel appears before the dialog box. So I can assure that kde is not completely uninstalled.

If I press okay another dialogue box appears with the following four options 
   run in low-graphics mode for just one session
   reconfigure graphics 
   troubleshoot the error
   exit to console login

Unfortunately, I can't select any of these options using either up-down keys and I don't even get the mouse pointer.

If I reboot pressing and holding the power button just a '-' will come after sometime, later it checks the battery status and haults:( 

In the next reboot the same dialog box. 
Next reboot "-"
I get these two in kinda alternative way.

My question is how do I get back to GUI?

I opened recovery mode, did all possible things: cleaning up, repairing the broken packages etc. Nothing worked out:(
  
Pleeeease help me out . . .

---

### Post by pras8421 on 2012-11-12
Or anybody please tell me how to copy the contents of the home folder to a flash memory in recovery mode. . .

---

### Post by slickymaster on 2012-11-12
Why don't you try with a LiveCD. That way you'll have access to all the partitions.

One other thing, you say you have ubuntu 12.04 installed inside windows 7?! Do you mean in dual-boot, along side with windows seven or dou you have it in a virtual machine?

---

### Post by newb85 on 2012-11-12
Wubi, a.k.a, the Windows installer, is a form of virtual machine, and there won't be a separate Ubuntu partition to browse using the Live CD.

Once you're in recovery mode, you'll need to determine what the flash drive is named (so that you have a destination).

```
ls /media
```

Then you should be able to copy your home directory to the flash drive.  You'll probably want to make sure to include hidden files and preserve permissions and timestamps.

Also, it might be a good idea to do put them into an archive, like

```
tar -cpf /media/*flashdrivename*/backup.tar /home/*username*
```

(If your home folder is too large for your flash drive, it might work to create a compressed archive.  More on that in the manpage for tar.)

Edit: also, I'd recommend when you reinstall that you use the Live CD to install alongside Windows instead of using Wubi.

---

### Post by bcbc on 2012-11-12
You can view files from windows using this: [http://ext2read.blogspot.ca/](http://ext2read.blogspot.ca/)

Install and point it at the \ubuntu\disks\root.disk file.

It might be possible to recover what you have, but you'll need a live CD/USB to troubleshoot. Let me know if you want to try and I'll give you some ideas. (It sounds like you might have just run out of space while upgrading - which is a known issue)

---

### Post by pras8421 on 2012-11-14
Thanks, I reinstalled 12.04 losing the data before going through your suggestion :-( 

Then upgraded it to 12.10 ;-)

Today morning when I am kinda playing in comp.-conf.-settings-manager, unity got stuck and when I rebooted I had the same problem but on the further reboot the things were normal except unity; where in I'm not getting the dashhome :)

I removed unity by the following command

  "sudo apt-get remove unity unity-2d unity-2d-panel unity-2d-spread unity-asset-pool unity-services unity-lens-files     unity-lens-music unity-lens-applications gir1.2-unity-5.0 unity-common indicator-sound indicator-power indicator-appmenu   libindicator7 indicator-application indicator-datetime indicator-messages libnux-2.0-0 nux-tools libunity-misc4 unity-  2d-commonicator-appmenu libindicator7 indicator-application indicator-datetime indicator-"

and reinstalled using 
  "sudo apt-get install ubuntu-desktop"

but the dashhome is not appearing.

This is not really a problem as I have cinnamon and gnome desktops.
However the beautiful 3d effects are not possible in these desktop environments as I know.

Any suggestions to recover the dash-home please??

---

