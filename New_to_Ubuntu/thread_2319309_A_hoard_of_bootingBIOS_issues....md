---
title: "A hoard of booting/BIOS issues..."
date: 2016-04-02
forum: New to Ubuntu
---

### Post by Bobby_Pendragon on 2016-04-02
Here's the thing. And I'll preface it by saying I'm very much in over my head - that's why I'm seeking help. A while ago, my Lenovo U410 laptop was having issues with the BIOS and wouldn't boot Windows 8.1. I didn't know how to fix it and wanted *something* to work on my PC, so I installed Ubuntu onto it's own partition. Later, Windows started booting normally again, so I continued using that and left Ubuntu in the background (the PC would automatically boot to Windows). I later installed Windows 10. 

Then, the same Windows booting issues that initially started everything started again and I was left with the Ubunutu I had installed to boot into. I wanted to get back on Windows, where all my files where, so I (quite irrationally) tried to remove Ubuntu completely by deleting a 32gb partition I'd apparently made for it. Yeah, I know that's not how it works now. Now, I couldn't get into Windows or Ubuntu, only the grub menu.

So, I tried installing Ubuntu again, by installing the newest version over the partition I'd deleted. Now Ubuntu works again. I'm still trying to access my Windows OS and all the files associated with it, which I'm *hoping* are on the disk somewhere. But I can't even boot into grub anymore, for some reason. I've tried to boot into Boot Repair Disc and a recovery drive I've made for Windows, neither seemed to work.

At this point, I just want to get access to Windows and my files. This laptop's had a lot of issues from day 1, I'm trying to get what I need and switch.

---

### Post by Bucky Ball on 2016-04-02
Welcome. Can you boot from the live installer (USB or DVD) and Try Ubuntu? If so, just move the files to safety from there. You could have done that whilst Ubuntu was booting at any time. Simply mount the drive the files are on and move. Ubuntu can access Windows patitions without issue. Win does not understand Linux partitions, though.

---

### Post by Bobby_Pendragon on 2016-04-02
Hey, thanks for your response! I think I could do that. But how do I go about retrieving the windows files from a different partition?

EDIT: When I try to boot from a USB, it goes straight into Ubuntu (15.10). If I can get the Windows files though there, though, that works too.

---

### Post by Bucky Ball on 2016-04-02
Try Ubuntu> when at the desktop open a file manager, click on the Windows partition. That's it.

---

### Post by Bobby_Pendragon on 2016-04-02
It doesn't appear to be readily visible. And I've looked online and others say you need to mount the drive. The only disk that appears to be available to Ubuntu is that of ubuntu itself.

---

### Post by Bucky Ball on 2016-04-03
Open Gparted from the desktop of a live session (boot from install media and get to a desktop, not install). Look for the Windows partition. It will be NTFS and will be named '/dev/sd**' something in the left column. 

Once you know what it is:
```

sudo mkdir /mnt/Win
sudo mount /dev/sd** /mnt/Win
```

Replace '/sd**' with whatever your partition is. Your Windows partition should be mounted. 

There is a [wealth of info]("https://duckduckgo.com/?q=mount+windows+drive+ubuntu&t=h") out there.

---

### Post by oldfred on 2016-04-03
Post this:
sudo parted -l

And if you left Windows fast startup on, Linux will not mount it normally to prevent damage to the hibernation. You may be able to force mount in read only mode.
       Fast Startup off (always on hibernation)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

---

