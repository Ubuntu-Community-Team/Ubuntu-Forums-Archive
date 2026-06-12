---
title: "How Can I Recover Data from an Exernal Hrd Drive that won't Mount?"
date: 2013-04-26
forum: New to Ubuntu
---

### Post by ChannelZ28 on 2013-04-26
first off, yes i tried searching. yes i read a bunch of posts. yes i know about testdisk and photorec, yes i know how to use them, no i couldnt get them to work. most of the posts were from a bunch of years ago, im hoping there is something newer.

i have a 500gb external drive that seems to have failed. it wont mount. i get various error messages when i try. i opened the disk utility in ubuntu and it recognizes the drive, shows it has a ntfs partition, but wont mount or format it. it always says the drive is busy. where it shows the volume, the little spiral in the corner goes on spinning indefinitely.

when i try to open photorec, it says "disc identification please wait..." and just stays there. 

i have used getdataback in the past, but i dont have access to a windows computer and to be honest, the data on the disc isnt really worth paying to recover. i want it back, but i dont need it back.

any other suggestions? i am not very computer savvy, i like very detailed instructions if you have any. thanks!

---

### Post by oldfred on 2013-04-26
Often Windows just needs chkdsk, but you have to run that from Windows.

If you have a NTFS data partition you need Windows or a Windows repairCD or flash to run chkdsk. I have used a Windows 7 repair flash drive on my XP partition and it did a better job or at least reported it found more stuff to fix.

Generally you should only have the same version as your Windows but if just for chkdsk it does not matter.
       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[URL="http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html"]http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html

[/URL] Always run chkdsk and run again until there are no errors, that may be all that is required
chkdsk c: /b
/b includes /r
[http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx)

[URL="http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html"]
[/URL]

---

