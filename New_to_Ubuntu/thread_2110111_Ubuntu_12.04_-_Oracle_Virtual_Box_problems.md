---
title: "Ubuntu 12.04 - Oracle Virtual Box problems"
date: 2013-01-29
forum: New to Ubuntu
---

### Post by Shallowmind on 2013-01-29
I am a newbie here.  I have only had a Linux system for a month or so now.  I got my computer from Zareason with Ubuntu 12.04 installed from the factory.  

I recently installed Oracle Virtual box version 4.1.12.  I had trouble at first getting it to recognize the CD/DVD drive to install a Window XP VM.  I was able to figure that out.  

However I cannot seem to get it to recognize the USB drive at all.  I have installed the extension pack.  I have put my name in the VBoxusers group and logged out and back in.  I keep getting this message:


[Screenshot from 2013-01-29 09:48:24.jpg]("http://ubuntuforums.org/attachment.php?attachmentid=230796&stc=1&d=1359471260")


If I open Virtual Box and the VM is "off" I can access the settings and toggle USB on and off.  If the VM is running I can access the settings but it will not allow me to toggle USB on and off.

What should I do?

---

### Post by haqking on 2013-01-29
> **Shallowmind said:**
> I am a newbie here.  I have only had a Linux system for a month or so now.  I got my computer from Zareason with Ubuntu 12.04 installed from the factory.  

I recently installed Oracle Virtual box version 4.1.12.  I had trouble at first getting it to recognize the CD/DVD drive to install a Window XP VM.  I was able to figure that out.  

However I cannot seem to get it to recognize the USB drive at all.  I have installed the extension pack.  I have put my name in the VBoxusers group and logged out and back in.  I keep getting this message:


[Screenshot from 2013-01-29 09:48:24.jpg]("http://ubuntuforums.org/attachment.php?attachmentid=230796&stc=1&d=1359471260")


If I open Virtual Box and the VM is "off" I can access the settings and toggle USB on and off.  If the VM is running I can access the settings but it will not allow me to toggle USB on and off.

What should I do?

make sure you are in the group with

```
groups
```

---

### Post by Shallowmind on 2013-01-29
Do you mean  to type "groups" into a terminal?  If so this is what I got:

shallowmind adm cdrom sudo dip plugdev lpadmin sambashare vboxusers

Thanks

---

### Post by haqking on 2013-01-29
> **Shallowmind said:**
> Do you mean  to type "groups" into a terminal?  If so this is what I got:

shallowmind adm cdrom sudo dip plugdev lpadmin sambashare vboxusers

Thanks
  mm seems ok apart from you are running version 4.1.12 and it is currently at 4.2.6

if i was you I would upgrade to latest version and see if it resolves your issue

---

### Post by Shallowmind on 2013-01-29
I will try that now and get back with the results.  

Again - thanks

---

### Post by Shallowmind on 2013-01-29
Ok I downloaded VB version 4.2.6 and this is what I got after opening it:

[ATTACH]230799[/ATTACH]

Please note the error message

What now?

---

### Post by howefield on 2013-01-29
Uninstall the old version first.

---

### Post by Shallowmind on 2013-01-29
Do I have to uninstall Windows XP out of Virtual Box first?  Or do I just uninstall Virtual Box and windows goes along with it?

Thanks for your help and quick replies.

---

### Post by howefield on 2013-01-29
No your VM will be safe, but I would copy it out elsewhere in any event as I like to keep copies of my VMs :)

---

### Post by Shallowmind on 2013-01-29
OK so I removed 4.1.12.  I installed 4.2.6 and it prompted me to update the extension pack, which I did.  And I verified that I was in the VBoxusers group.

Windows works fine in the new version.  But it still will not recognize the USB.  It indicates there is no device connected.   I also get the same warning as attached in the first post above.

And if I may:  How can I remove Virtual Box and the VM still be there?

Also Do I need to have antivirus and such on the VM?

Thanks

---

### Post by furything on 2013-01-29
I tend to use vmbox more from windows than ubuntu but found from 4.2 it seemed to work.

Asking 2 daft questions
1. Have you mounted the device in ubuntu first?
2. How are you trying to connect usb?
Like this  - on the bottom right hand corner of the virtual machine running windows xp click usb icon and select the usb device wishing to connect to. (you can also do it from devices menu at top)

In windows it mounts the device first you then select the device and it locks it from removal insatlls it as a vmbox device and passes it through to the vm

---

### Post by Shallowmind on 2013-01-29
I have tried both methods that you mention above.  Nothing seems to work.

---

### Post by furything on 2013-01-29
Try messaging Morbius1 he recently helped a guy with sharing host to vm folders but from his screen shot examples he does use vmbox from a linux host.

As said I usually use vm from windows but if I get a chance will experiment tonight when I get home with my kubuntu box. If you can get hold of Morbius1 I am pretty sure he can help you

Edit - You need to ensure that the usb has read write access to the vmusr account

---

### Post by Shallowmind on 2013-01-29
Ok sorry but I'm a bit confused.  Very new to all this.

I don't think or know if I have mounted the device in Ubuntu first?  The USB does work in Ubuntu if that is what you mean.

And for question 2.  All it does when I (right) click on  the USB icon is say :"No USB devices connected" .  It does nothing if I left click it.  Same for "devices" at the top of the page.

And no I would not consider the questions daft.

Thanks

---

### Post by furything on 2013-01-29
> I don't think or know if I have mounted the device in Ubuntu first?  The USB does work in Ubuntu if that is what you mean.IF you can open the usb device first in ubuntu and do not unmount /eject it then try connecting usb devices.


For the network share Morbius1 suggested this
 > sudo gpasswd -a your-user-name vboxsfTo get file sharing to work. I don't know if this is the same for a usb device

A hint may be to run ```
cat /etc/passwd
``` and see if there are any other vm groups

---

### Post by Morbius1 on 2013-01-29
USB Linux host to Windows guest has always been problematic. To be honest outside of a printer which it seems to handle without problems I don't even bother with it any more.

I do however have a fallback just in case:

On the VBox settings for this guest create a Shared Folder of your /media directory. If the USB device is just a storage device Linux will mount it to /media/LABEL and you should find it as a folder within your new "media drive" on your Windows guest.

There's only 2 problems with this approach:

* If you have a lot of internal partitions that you mount through nautilus they will mount to /media as well and you might not want Windows to have access to it there.

* If this is something other than a USB storage device - like a phone or something - where you expect to launch an application in Windows when connecting - that will not happen.

On the plus side though if you have a usb stick formatted in say ext4 Windows will have no problem reading and writing to it. ;)

---

### Post by furything on 2013-01-29
Morbius1 glad to see you here

You know I should have thought of that.

Had issues remoting into work and accessing the dvd from vm.
Did exactly as you suggested  - create a shared directory (Transient) back onto to the dvd and accessed it as a folder.

Duh should have thought of that and recommended your solution.

---

### Post by Shallowmind on 2013-01-29
> **Morbius1 said:**
> USB Linux host to Windows guest has always been problematic. To be honest outside of a printer which it seems to handle without problems I don't even bother with it any more.

I do however have a fallback just in case:

On the VBox settings for this guest create a Shared Folder of your /media directory. If the USB device is just a storage device Linux will mount it to /media/LABEL and you should find it as a folder within your new "media drive" on your Windows guest.

There's only 2 problems with this approach:

* If you have a lot of internal partitions that you mount through nautilus they will mount to /media as well and you might not want Windows to have access to it there.

* If this is something other than a USB storage device - like a phone or something - where you expect to launch an application in Windows when connecting - that will not happen.

On the plus side though if you have a usb stick formatted in say ext4 Windows will have no problem reading and writing to it. ;)


Thanks.  I am trying to get my Quickbooks info into QB via the USB.  Will it work for that?

---

### Post by Shallowmind on 2013-01-29
And now I get to ask a daft question?  How do I do what Morbius1  is indicating above?

---

### Post by Morbius1 on 2013-01-29
** Shut down your Windows guest

** Open VirtualBox > right click the Windows guest > Settings and you should see something like the attached. Don't forget to select Auto-mount.

** Then start your Win VM again.

"media" should show up as another drive in WinXP

[COLOR=Blue]**EDIT**[/COLOR]: I've got to shutdown for a bit so if you have issues with any of that after you bring up the WinXP VM it may be because you didn&#8217;t install the Guest Additions. On the top bar of the VM select Devices > Install Guest Additions. Windows will do the rest.

---

### Post by Shallowmind on 2013-01-29
Thank you very much.  That seemed to do the trick.  I just cannot seem to get the info off of the memory stick now!  Figures.

Thanks again for all your help

---

### Post by Morbius1 on 2013-01-29
You can't get it off the stick in the Windows VM? Or you can't even get to it from the Linux host?

---

### Post by Shallowmind on 2013-01-29
I cannot get it off the stick in Window VM.  I have had this trouble before even on a straight windows machine.  I am trying to open my old files with the Quickbooks wizard.  It will show me the stick but when I press "open" it does nothing.  

I have not even tried to do this on the Linux side.  It does show up on Ubuntu and it will show me the files.  But I have not tried to open them Linux.

---

### Post by Morbius1 on 2013-01-29
Did a quick google and there seems to be a whole support subsection on this issue: [http://support.quickbooks.intuit.com/support/pages/inproducthelp/Core/QB2K12/ContentPackage/Core/File_Portable/portfile_troubleshoot.html](http://support.quickbooks.intuit.com/support/pages/inproducthelp/Core/QB2K12/ContentPackage/Core/File_Portable/portfile_troubleshoot.html)
> **Are you using a removable storage device such as a CD or USB flash drive?** Try copying the portable file (.qbm) to your hard disk first, and then use the Open or Restore Company wizard to If you can see the files in the file manager in WinXP copy them to a folder there and point the wizard to that folder.

Or copy the files to a linux folder say your Documents folder, create another shared folder to the Documents folder, and see if the wizard can find them there.

---

### Post by Shallowmind on 2013-01-29
Thank you.  I will give it a shot and post the results here.

---

### Post by Shallowmind on 2013-01-29
Again thanks to everyone for your help

And Morbius1 that link helped me get my info back into Quickbooks.  Thanks a million.

---

### Post by Morbius1 on 2013-01-29
Whew !

Just so you know I upgraded the VBox application yesterday and when I launched it this morning it froze on me. I have 13 Virtual machines in this thing and I was not a happy camper. Took me 2 hours to figure out how to fix the $#@& thing so I think with your problem I just got lucky ;)

---

### Post by Shallowmind on 2013-01-29
WOW.  One VM is enough for me. 

How is it I can delete Virtual Box and the VM still stay on the computer?

Also should I run anti virus and other such things in the VM?

Thanks

---

### Post by howefield on 2013-01-30
> **Shallowmind said:**
> How is it I can delete Virtual Box and the VM still stay on the computer?

Can you imagine the uproar if it did ?

Eg, how about you install vlc, and then decide you don't want it, so uninstall but it takes all your music and film collection with it ?

It is only the application that you are uninstalling.

> Also should I run anti virus and other such things in the VM?

Your windows install will behave as it would on the bare metal, the fact that it is virtualised doesn't mean anything in terms of how you secure and look after it, so yes, anti virus, defragging, and everything else that you would do on a "real" windows install should also be done to a virtualised one.

---

### Post by mlentink on 2013-01-30
> **Shallowmind said:**
> 

Also should I run anti virus and other such things in the VM?

Thanks

Yes. Definitely yes. Your Windows VM may run on virtual hardware, but it is still a windows machine just like any other. So please take all protective measures you would on a real metal windows box.

---

