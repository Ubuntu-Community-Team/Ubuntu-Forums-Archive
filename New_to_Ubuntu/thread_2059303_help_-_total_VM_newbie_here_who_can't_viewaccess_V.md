---
title: "help - total VM newbie here who can't view/access VM anymore"
date: 2012-09-17
forum: New to Ubuntu
---

### Post by just4kixx on 2012-09-17
hi all, I'm hoping someone can help me, because I really REALLY need to access my files.

This  is a friend's laptop, so I don't know it as well as I might otherwise. I  know it's running Ubuntu and Windows XP as a VM. Haven't had any  problems with it since it was loaned to me last year. He doesn't know  anything about this stuff either, so I've had to learn about snapshots,  etc. on my own.

The problem started this morning. I got a low  disk warning, so the first thing I did was try and delete snapshots. It  gave me an error [too many child files] and then the screen when grey  and said that windows was inaccessible. 

I tried a reboot, but  when that was done, the icon for the OSE was no longer in the side docky. The Firefox  that's on the dock that runs in Ubuntu also will not start, saying the  application didn't identify itself.

I also got the following warning:

NS_ERROR_Failure 0x80004005
Start tag expect, '<' not found

Location: /home/robert/virtualBox VMS/ Windows XP/Windows XP.Vbox/ line 1 [0], column 1
I've  gone to the Disk Usage Analyzer and can see the files. I can also see  the VirtualBox VMs folder and open it. There's a folder named Logs and  another one - Snapshots. There are also three files: Windows XP.vbox     WindowsXP.box-prev  and Windows XP.vdi

There's a Windows XP link on the desktop, but when I tried clicking on it, it gave me the following error message: 

Failed to create the VirtualBox COM object
The application will now terminate.

Under Details: Callee RC: NS_ERROR_FACTORY_NOT _REGISTERED (0X800040154)

Is there anything at all I  can do to restore Windows - at least long enough to move some stuff and  bring the disk usage size down?

---

### Post by heyandy889 on 2012-09-17
Whoa. Sounds kind of ******. Just searching around, found a couple pages that might help.

[http://www.kace.com/support/resources/kb/article/Failed-to-create-VirtualBox-COM-object](http://www.kace.com/support/resources/kb/article/Failed-to-create-VirtualBox-COM-object)

[http://forums.freebsd.org/showthread.php?t=11893](http://forums.freebsd.org/showthread.php?t=11893)

Also, could you restore an old snapshot? Or possibly make a new, fresh virtual machine, and put the snapshot in there?

---

### Post by ty74 on 2012-09-17
You can access your window xp files from your ubuntu partion. Click on your home folder and it should show the partions of the hard drive on the right side. Just click on the windows one and dig your way through the file system to find your files.

As for your cleaning up some file space get bleachbit and use bleachbit root to delete your language packages. Look on this website how to delete language packages and other helpful tips [http://www.howtogeek.com/116971/7-tips-to-get-the-most-out-of-bleachbit-a-ccleaner-for-linux/](http://www.howtogeek.com/116971/7-tips-to-get-the-most-out-of-bleachbit-a-ccleaner-for-linux/).

---

### Post by just4kixx on 2012-09-17
First off, thank you both for the quick reply. Things got worse before they got better. After a reboot,Ubuntu threw me a new error abut the configuration defaults for the Gnome Power Management have not been installed correctly, but I figured my way around this with CTRL ALT F1 and sudo apt-get clean and sudo apt-get autoclean and once I ran sudo reboot I could at last get back in....

For accessing my window xp files, is this right? I found the folder on the left side of the window:

File System >Home > Robert >VirtualBox VMs. 

There's a Windows XP folder inside of this,  with a Logs folder, a Snapshots folder and three other files: Windows XP.vbox      Windows XP vbox-prev    Windows XP.vdi

I'm going to check out those links too.

---

### Post by cprofitt on 2012-09-17
One question:

1.  Was the low disk space warning on the host (Ubuntu) or the guest (Windows)?

Two suggestions:
You can make a new virtual machine and boot it to a LiveCD with the old Windows VDI disk mounted. That would allow you to looks at the Windows file system (there are other more complex methods, but this is likely the easiest)

If you have an external drive I would back-up the VDI immediately to ensure you have the original in case of any other issues.

---

### Post by just4kixx on 2012-09-17
The low disk warning was on the guest [windows]

could you possibly give me a step by step walkthru on how to do the whole new virtual machine / live CD thing? I wouldn't know where to start.

my external HD just died a few weeks ago.  : (

Also - and this is comparatively minor, but now that I've gotten back into ubuntu, I can't get my firefox to connect to the web, even though my connection is there.

---

### Post by cprofitt on 2012-09-17
Here are the steps to making a new virtual machine:

[http://www.thegeekstuff.com/2012/02/virtualbox-install-create-vm/](http://www.thegeekstuff.com/2012/02/virtualbox-install-create-vm/)

You will need to alter a few things:
1.  When it comes to making your boot hard disk just select the existing windows .vdi

After that try to start Windows and see if it works. If it does then we can proceed from there to increase the disk size.

The instructions to increase HD size are here:
[http://www.virtualbox.org/manual/ch08.html#vboxmanage-modifyvdi](http://www.virtualbox.org/manual/ch08.html#vboxmanage-modifyvdi)


If it does not work, then we can look at using the liveCD to rescue files.

---

### Post by just4kixx on 2012-09-17
I figured out how to start a new virtual machine, before I came back here.  And I didn't understand that 2nd link at all - newbie, remember? : )

where/how do I type in the modifyhd command?

Is there anyway I can load my old vdi files int this new machine so I can get access to those files?

---

### Post by cprofitt on 2012-09-17
If you have created a new virtual machine -- did you install an OS? Did you make a new hard drive or attach your old one?

---

### Post by just4kixx on 2012-09-18
I don't think it matters cprofitt, since it greyed out on me with a "paused" symbol. The original drive says inaccessible, so I guess that's a step up.

And I think I made a mistake and the low disk messaqge was from Ubuntu.. I was in Windows when it popped up.

I managed to increase my free space to 1.3 gig this morning before I left for work. 

Tried to start Windows and got the following:
Failed to create the VirtualBox COM object
Start tag expected, '<' not found
Location:'/home/robert/.VirtualBox/VirtualBox.xml, line 1(0), column 1.

/build/buildd/virtualbox-ose-4.0.4.-dfsg/src/vbox/main/src-server/VirtualBoxlmpl.cpp [518](nsresult VirtualBox::())

Details:
Result Cide: NS_ERROR FAILURE (0x80004005)
Componenet: VIrtualBox
InterfaceL
IVirtualBox {d2de270c-1d4b-4c9e-843f-bbb9b47269ff}

...now what this all means, I have no idea!!!!

---

### Post by just4kixx on 2012-09-19
I have freed up 400 gig but still can't access the VM.

As I said in my earlier post, when I click on the Windows XP link on my desktop, I get the following error message:

Failed to create the VirtualBox COM object
Start tag expected, '<' not found
Location:'/home/robert/.VirtualBox/VirtualBox.xml, line 1(0), column 1.

/build/buildd/virtualbox-ose-4.0.4.-dfsg/src/vbox/main/src-server/VirtualBoxlmpl.cpp [518](nsresult VirtualBox::())

Details:
Result Cide: NS_ERROR FAILURE (0x80004005)
Componenet: VIrtualBox
InterfaceL
IVirtualBox {d2de270c-1d4b-4c9e-843f-bbb9b47269ff}

Is there another way to access the VirtualBox so I can try and access Windows?

I can see the vdi files, but at this point I have no idea what to do. Help, please!

---

### Post by ty74 on 2012-09-19
For the windows files they are on the left side (my mistake) should be under devices. The folders may look strange but keep searching through the folders till you find your files. When your find the files drag them where you want them in the ubuntu folder.

---

### Post by just4kixx on 2012-09-19
I actually got back into WindowsXP. After googling for a bit, I went into the [hidden files] .VirtualBox and found that the xml file was empty. So I renamed the .xml-prev to the original name and was able to set up a new VM

BUT

none of the work I had on the desktop was there. I've only been able to load the WindowsXP.vdi files. Trying to load any of the other ones gives me this:

 Failed to open the hard disk /home/robert/VirtualBox VMs/Windows XP/Snapshots/{daef7a85-9327-489e-b057-830a84a31bd8}.vdi.
 Parent medium with UUID *{6c512f52-1390-4e36-9c6f-e31f9724fd99}* of the medium '/home/robert/VirtualBox VMs/Windows XP/Snapshots/{daef7a85-9327-489e-b057-830a84a31bd8}.vdi' is not found in the media registry ('/home/robert/.VirtualBox/VirtualBox.xml').
  
   Result Code: 
  NS_ERROR_FAILURE (0x80004005)
   Component: 
  Medium
   Interface: 
  IMedium {9edda847-1279-4b0a-9af7-9d66251ccc18}
   Callee: 
  IVirtualBox {d2de270c-1d4b-4c9e-843f-bbb9b47269ff}

details:

Result Code: 
  NS_ERROR_FAILURE (0x80004005)
   Component: 
  Medium
   Interface: 
  IMedium {9edda847-1279-4b0a-9af7-9d66251ccc18}
   Callee: 
  IVirtualBox {d2de270c-1d4b-4c9e-843f-bbb9b47269ff}

---

