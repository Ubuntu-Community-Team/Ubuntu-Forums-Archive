---
title: "Where to begin once you've booted."
date: 2012-07-08
forum: New to Ubuntu
---

### Post by Venn2021 on 2012-07-08
Hello. I'll start by saying this is my first experience with Ubuntu or Linux of any kind. I have a **Compaq Notebook** running **Windows 7**. 

Recently my hard drive went kaput. My main concern is retrieving (if possible) my files. Especially my music. I was directed to Ubuntu as a means to access my HDD, so I booted up a USB flash drive and popped it in the malfunctioning machine.

So, my question is, where do I go from here? There are several options on the first blue screen, but the most promising looked like "Boot From 1st Hard Drive", or something. I did this, and watched a myriad of code scroll down, finally ending with a line that says, "**BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu4) built-in shell (ash)**". After that is a line offering to show built-in commands.

I have no idea what any of this means. All I want to do is be able to access my files (again, if possible), and extract them onto a flash drive so I know they're safe before I try re-installing my OS or anything.

Does anyone have the patience to point me in the right direction? Any help is appreciated, thank you very much.

---

### Post by carl4926 on 2012-07-08
It's hard to tell just what you have done. Sorry.
If you have created a bootable USB Ubuntu live cd on a USB flash drive, you can boot from that and arrive at a live desktop. That is a working live Ubuntu session, that you can try without installing.
But from there you can access windows with the file manager. It will be seen at the top of the left hand corner of the file manager Eg; 120GB File system or whatever size windows is.
Click it and you should be good. If this were a proper Ubuntu installation you would need to enter a password to access windows.

---

### Post by raja.genupula on 2012-07-08
see in the image , you have to select the 1st option . that will takes you to  LIVE mode and you can get your data back .

---

### Post by NikTh on 2012-07-08
You must specify what did you with .iso image ? where did you burn it ? CD/DVD or Usb ? 
The option "Boot from fist hard drive" does nothing ,really .  It just boot from your Kaputten HDD. 
You must find an option like "Default" or "Try Ubuntu without installing" and boot from there. 

Then you follow these simple steps.. ( i assume that you have Ubuntu 12.04) 

1) Click on Dash (up-left Ubuntu icon) 
2) write **nautilus** or** files** and click first icon from left to open it..
3) At left window you will see devices list . Click one (it will listed like 100GB filesystem or whatever)
4) Begin to backup (copy-paste) your important files.

---

### Post by Venn2021 on 2012-07-08
NikTh, thanks, I got to the desktop. As I said before, I've never used Ubuntu, and I just wasn't giving it enough time to load the program.

Well I've been searching high and low for anything resembling my files. They're not in the Ubuntu default media folders, and I can't seem to find them in any of the folders listed in the "File System" folder. 

If my files are intact, do you have any idea where they would be? I'll keep searching and edit this post if I find them.

Thank you very much.

---

### Post by drs305 on 2012-07-08
Boot the Ubuntu LiveCD, "Try Ubuntu". 

If your Windows partition doesn't mount automatically, you will need to mount your Windows partition - probably sda1 or sda2. To mount it, run this command from a terminal (ALT-F2):
```

sudo mount /dev/sda1 /mnt
gksu nautilus /mnt
```

With the second command, explore what's on /mnt. If it's not your Windows partition:
```

sudo umount /mnt
sudo mount /dev/sda2 /mnt
```
Once you find your files, you can copy them to another partition or external. Let us know if you need help with that part of things.

---

### Post by kansasnoob on 2012-07-08
> **Venn2021 said:**
> NikTh, thanks, I got to the desktop. As I said before, I've never used Ubuntu, and I just wasn't giving it enough time to load the program.

Well I've been searching high and low for anything resembling my files. They're not in the Ubuntu default media folders, and I can't seem to find them in any of the folders listed in the "File System" folder. 

If my files are intact, do you have any idea where they would be? I'll keep searching and edit this post if I find them.

Thank you very much.

I might be able to help you but I first need to clarify something. In your OP you said "**There are several options on the first blue screen**".

Having said "blue screen" makes me think you may be using an Ubuntu derivative rather than Ubuntu itself so please open the terminal and post the output of these two commands:

```
echo $DESKTOP_SESSION
```

```
lsb_release -a
```

---

### Post by mastablasta on 2012-07-08
> **Venn2021 said:**
> 

If my files are intact, do you have any idea where they would be?.

windows partition will be marked as "filesystem" or somehting similar usualyl with the size next to it.

---

### Post by Venn2021 on 2012-07-08
drs305, those commands you posted worked like a cinch. I'll tell you it's good as hell to see all my files are still in there. I'm in the process of dragging them out little by little via flashdrive (actually my phone, it's got more storage).

The file transfer seems to be taking forever, though. I'm only copying from the filesystem to a usb flash drive. I mean it's taking over an hour to copy 700mb worth of pictures. If that's normal, then I have no problem sticking it out. I'm just wondering if there's something I can do to expedite the process.

Once again, thanks everyone for the help, really.

---

### Post by drs305 on 2012-07-08
It depends a lot on the flash drive, but I'd just let it copy as long as it doesn't stop completely. I've had flash drives take that long.

---

### Post by Kopkins on 2012-07-08
> **Venn2021 said:**
> drs305, those commands you posted worked like a cinch. I'll tell you it's good as hell to see all my files are still in there. I'm in the process of dragging them out little by little via flashdrive (actually my phone, it's got more storage).

The file transfer seems to be taking forever, though. I'm only copying from the filesystem to a usb flash drive.  I mean it's taking over an hour to copy 700mb worth of pictures. If that's normal, then I have no problem sticking it out. I'm just wondering if there's something I can do to expedite the process.

Once again, thanks everyone for the help, really.
[COLOR=Black]
  
Whichever you're using, your phone/flashdrive could have a low write speed, causing your slow transfer speed. Also, you said your hard drive went kaput. You are transferring data off of your kaput hard drive. Could be low read speed of your that drive. 

If you wanted you could use the disk utility to check if your hard drive has a low read speed, but I would just keep transferring the files if it's working.

Kopkins

[/COLOR]

---

