---
title: "FAILED INSTALL:  Please Help!!"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by jukingeo on 2008-05-24
[Hello All,

I been GRUBBED!!!

Yes, the thing I been trying to avoid happened.  Something went wrong with the Grub boot-loader on my installation of Ubuntu Version 8.04.

I have a two hard drive setup and I just installed a new 500gb SATA drive in which to put Ubuntu on.

This is how I partitioned my drive (sd2 is for Ubuntu, sd1 is my main Windows drive):

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x32c632c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9726    78124063+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cf364

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1837    14755671   83  Linux
/dev/sdb3            1838       13995    97659135   83  Linux
/dev/sdb4           13996       60800   375961162+   5  Extended
/dev/sdb5           54722       60800    48829567+   b  W95 FAT32
/dev/sdb6           13996       32231   146480607   83  Linux
/dev/sdb7           32232       54465   178594573+  83  Linux
/dev/sdb8           54466       54721     2056288+  82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 

I have set up my hard drive as above and I set up Grub on the sd2 drive.  I rebooted my machine and Grub came up with 3 selections for Ubuntu and one for my Windows boot up.

However, all is not well in never never land.

When I select any of the 3 choices for Ubuntu, I get this error message:

Error 17: Cannot Mount Selected Partition

When I try to select the Windows Boot, this is the error message I get:

Error 13:  Invalid or Unsupported EXE format.

I am writing this message to the forum because I was able to boot up the Live CD.  Needless to say, I cannot get into my new Ubuntu installation and worse, Windows isn't booting up either.

I am NOT very happy at this point considering that this was something I tried to avoid.  And I tried everything possible NOT to involve the primary hard drive (sda1 80gig), because that is where Windows is located.

I seriously doubt something went wrong with Windows, but I am putting the blame on the boot-loader.  
I would appreciate some help in correcting this mishap in that I would like to get both  Windows and Ubuntu back up and running from the hard drive.

Thank You,
Geo

---

### Post by dmacdonald111 on 2008-05-24
Have you tried fixing it with the 'fixmbr' command? You can use the livecd to boot to your command prompt and should be able to use it to get grub up and running again.

---

### Post by markbuntu on 2008-05-24
try switching the plugs for the drives on your motherboard. The bios will look for the first SATA drive which is sda which is your windows drive. 

Grub is on sdb and the windows boot loader on sda. If you only have one drive it does not matter which plug it is in but when you start adding drives it does. SATA drive order is determined by which plug they are in on the motherboard. No jumpers, nothing to do but change the plugs, quick and easy.

You do not have to do anything else but that. Grub will load and you can boot into either system. Windows will not notice any difference and will not even see the other drive.

HPFS/NTFS is the windows file system designator so the boot sector on sda is for windows.

---

### Post by jukingeo on 2008-05-24
> **dmacdonald111 said:**
> Have you tried fixing it with the 'fixmbr' command? You can use the livecd to boot to your command prompt and should be able to use it to get grub up and running again.

Hello,

This is my first Ubuntu install, I really don't know anything about the boot-loader.  So I don't know what to "fix" after I type in the fixmbr command.  And another question.  WHERE do I type in fixmbr?

I am going to need a complete walk through to fix the problem.

Thanx,

Geo

---

### Post by jukingeo on 2008-05-24
> **markbuntu said:**
> try switching the plugs for the drives on your motherboard. The bios will look for the first SATA drive which is sda which is your windows drive. 

Grub is on sdb and the windows boot loader on sda. If you only have one drive it does not matter which plug it is in but when you start adding drives it does. SATA drive order is determined by which plug they are in on the motherboard. No jumpers, nothing to do but change the plugs, quick and easy.

You do not have to do anything else but that. Grub will load and you can boot into either system. Windows will not notice any difference and will not even see the other drive.

HPFS/NTFS is the windows file system designator so the boot sector on sda is for windows.

I don't have a first SATA drive.  For some reason, Ubuntu thinks my first drive is a SATA...it isn't, it is an IDE drive.  Before I added the SATA drive I had two IDE drives.  I replaced my secondary IDE drive with the SATA drive.  Now for some reason I am getting an indication that my first hard drive is a SATA drive in lieu of the sda designation instead of hda.  But I do assure you my first drive isn't a SATA.

Any any regard, your suggestion may be good in getting my Windows back up, but my goal is to fix the problem.  If I can't fix the boot loader then is there a way to delete it and then repair it (reinstall it) afterwards?

Thanx,

Geo

---

### Post by ercferret18 on 2008-05-24
you would type fixmbr in the terminal (applications at the top, then accessories, then terminal)

---

### Post by meierfra. on 2008-05-24
Try this:


At the grub menu at boot-up select the ubuntu item, but do not press "enter", press "e" instead.  At the new screen which appears, press "e" again to edit the first line. The line should look like

root (hd0,3)

(of course the   numbers will be different)

Change the first number: If it is a "0" change it to "1", if it is a "1" change it to "0".

Press "enter" and then "esc" to get back to the grub menu.

You now should now  able to boot into ubuntu.

If this work you have to make the changes permanent by editing the file
"menu.lst". Open a terminal and type

```
gksudo gedit /boot/grub/menu.lst 
```

change the line

"#groot (hd0,3)" the same way you    just changed "root (hd0,3)"

Save the file.

In the terminal type

```
sudo update-grub
```


That's it.

For help with booting into Windows, post the bottom half of the file "menu.lst"

---

### Post by jukingeo on 2008-05-24
> **ercferret18 said:**
> you would type fixmbr in the terminal (applications at the top, then accessories, then terminal)

Ok, this is what I get:

ubuntu@ubuntu:~$ fixmbr
bash: fixmbr: command not found
ubuntu@ubuntu:~$ 

Command not found??

---

### Post by jukingeo on 2008-05-24
> **meierfra. said:**
> Try this:


At the grub menu at boot-up select the ubuntu item, but do not press "enter", press "e" instead.  At the new screen which appears, press "e" again to edit the first line. The line should look like

root (hd0,3)

(of course the   numbers will be different)

Change the first number: If it is a "0" change it to "1", if it is a "1" change it to "0".

Press "enter" and then "esc" to get back to the grub menu.

You now should now  able to boot into ubuntu.

If this work you have to make the changes permanent by editing the file
"menu.lst". Open a terminal and type

```
gksudo gedit /boot/grub/menu.lst 
```

change the line

"#groot (hd0,3)" the same way you    just changed "root (hd0,3)"

Save the file.

In the terminal type

```
sudo update-grub
```


That's it.

For help with booting into Windows, post the bottom half of the file "menu.lst"

If I go in the terminal this is what I get:

ubuntu@ubuntu:~$ sudo update-grub
Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###

ubuntu@ubuntu:~$ 

It says Grub isn't installed, and I know for a fact it is, because it does come up on boot. I just can't get into Windows nor Ubuntu

---

### Post by louieb on 2008-05-24
The mix of of ide and sata hard drives sometimes confuses GRUB install. 
Need to know which drive is 1st in the boot order. ide or sata. Any answer I could give will depend on on knowing that. 

When you got to the GRUB part of the install did you change the default location?  Need to know if the GRUB stage1 code was install in the MBR of the Windows drive.  

What happens if you change the boot order in BIOS.?

Good thread here on using two drives to dual boot. [Dualboot Two Hard Drives - Ubuntu Forums ]("http://ubuntuforums.org/showthread.php?t=179902")

Probally going to find the answer there. If you don't then you will need either a real Windows install disk or the Super Grub Disk. You can use either one to replace the MBR code of the windows drive with code that will load the windows boot loader. 
Which flavor of Windows are you using?

---

### Post by meierfra. on 2008-05-24
> ubuntu@ubuntu:~$ sudo update-grub

You need to do this once you successfully booted into ubuntu.Not from the liveCD

---

### Post by meierfra. on 2008-05-24
In other words: To this:

Reboot.
At the grub menu at boot-up select the ubuntu item, but do not press "enter", press "e" instead. At the new screen which appears, press "e" again to edit the first line. The line should look like

root (hd0,3)

(of course the numbers could  be different)

Change the first number: If it is a "0" change it to "1", if it is a "1" change it to "0".

Press "enter" and then "esc" to get back to the grub menu.

You now should now able to boot into ubuntu.
----------------------------------------------------------

Once you successfully booted into ubuntu, follow the rest of the instruction

---

### Post by jukingeo on 2008-05-24
> **meierfra. said:**
> Try this:


At the grub menu at boot-up select the ubuntu item, but do not press "enter", press "e" instead.  At the new screen which appears, press "e" again to edit the first line. The line should look like

root (hd0,3)

(of course the   numbers will be different)

Change the first number: If it is a "0" change it to "1", if it is a "1" change it to "0".

Press "enter" and then "esc" to get back to the grub menu.

You now should now  able to boot into ubuntu.

If this work you have to make the changes permanent by editing the file
"menu.lst". Open a terminal and type

```
gksudo gedit /boot/grub/menu.lst 
```

change the line

"#groot (hd0,3)" the same way you    just changed "root (hd0,3)"

Save the file.

In the terminal type

```
sudo update-grub
```


That's it.

For help with booting into Windows, post the bottom half of the file "menu.lst"

Hello,

OK, I tried this, and the first part worked!  However, the second part wouldn't allow me to change the "groot".  When I went to save it, it gave me an error message saying I don't have permission.  What gives with that?

Also, what do I do to fix the Windows boot up?  I can't get into Windows either?

Thanx,

Geo

---

### Post by meierfra. on 2008-05-24
> When I went to save it, it gave me an error message saying I don't have permission.

Did you open menu.lst via:

```
gksudo gedit /boot/grub/menu.lst
```

The "gksudo" will ask you for your password, giving  you permission to edit "menu.lst"



To boot into windows, you need to edit menu.lst one more time. But I need to see your current menu.lst before I can tell you exactly how to do it.

---

### Post by Raccoon1400 on 2008-05-24
> **jukingeo said:**
> Ok, this is what I get:

ubuntu@ubuntu:~$ fixmbr
bash: fixmbr: command not found
ubuntu@ubuntu:~$ 

Command not found??

Boot your windows CD, go into recovery mode, then type fixmbr.
If using vista, /fixboot/mbr

---

### Post by meierfra. on 2008-05-24
Don't do "fixmbr". You probably won't get into Ubuntu anymore if you do that. 
Getting Windows to boot should be easy once I see your menu.lst

---

### Post by jukingeo on 2008-05-24
> **meierfra. said:**
> Did you open menu.lst via:

```
gksudo gedit /boot/grub/menu.lst
```

The "gksudo" will ask you for your password, giving  you permission to edit "menu.lst"



To boot into windows, you need to edit menu.lst one more time. But I need to see your current menu.lst before I can tell you exactly how to do it.

Hello,

Ok, something must have gotten bunched up the last time. Perhaps it was because I was working with the Live CD, but once I got in via the first part of your suggestion, I rebooted, (via editing the command again) and then everything you said worked up to a point.  I was able to edit and save the "#groot" this time, however, there were three more lines that had the (1,0) in the boot line.  So I changed them to (0,0) and saved it again.  NOW it works! {Does the Cabbage Patch Dance}

I don't know why things got bunched up there and didn't work the first time.  I guess when in doubt....REBOOT!

Ok, that problem is fixed, now what about Windows?  I have the error code 13 on that one.

---

### Post by jukingeo on 2008-05-24
> **meierfra. said:**
> Don't do "fixmbr". You probably won't get into Ubuntu anymore if you do that. 
Getting Windows to boot should be easy once I see your menu.lst

One menu.lst coming right up!

(Note: It was the middle section under the "End Default Options" heading where I changed the additional hd (1,0) designations to hd (0,0).

## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b554ae58-fba0-4ae0-a405-0361be180aa3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b554ae58-fba0-4ae0-a405-0361be180aa3 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault

---

### Post by meierfra. on 2008-05-25
Change 

title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault

to

title Microsoft Windows XP Home Edition
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
savedefault

---

### Post by jukingeo on 2008-05-25
> **louieb said:**
> The mix of of ide and sata hard drives sometimes confuses GRUB install. 
Need to know which drive is 1st in the boot order. ide or sata. Any answer I could give will depend on on knowing that. 

When you got to the GRUB part of the install did you change the default location?  Need to know if the GRUB stage1 code was install in the MBR of the Windows drive.  

What happens if you change the boot order in BIOS.?

Good thread here on using two drives to dual boot. [Dualboot Two Hard Drives - Ubuntu Forums ]("http://ubuntuforums.org/showthread.php?t=179902")

Probally going to find the answer there. If you don't then you will need either a real Windows install disk or the Super Grub Disk. You can use either one to replace the MBR code of the windows drive with code that will load the windows boot loader. 
Which flavor of Windows are you using?

Hello LouieB

meierfra helped me out with getting the boot to work on Ubuntu.  Something initially happened when I used the Live CD, but when I did finally get in by editing the boot loader directly I was able to follow meierfra instructions and make the needed changes to get me finally into Ubuntu.  So as of now I am working off my Ubuntu installation.  However, I am still getting the error 13 for Windows and naturally can't boot to Windows.

As for my BIOS.  IDE is primary in the boot order.  If an IDE drive is hooked up in to IDE Primary, then SATA will not even appear on the Boot Order list. You CAN however boot from it in the boot menu.

As for the installation of Grub, the default looked like it was going to install itself on the Windows drive (1st hard drive).  I read that that is a no no and don't allow it to do such because it messes with the Windows boot up.  So Grub is installed on the Ubuntu drive.  So I tried to avoid a problem by listening to what I read, but yet a problem landed smack on my face.

I have Windows XP.

Geo

---

### Post by meierfra. on 2008-05-25
> However, I am still getting the error 13 for Windows and naturally can't boot to Windows.

I assume our last two post overlapped and you haven't tried  my most recent suggestion yet. Actually you also  should be able to boot straight into   XP by changing the boot order.

---

### Post by meierfra. on 2008-05-25
```
So Grub is installed on the Ubuntu drive.
```

For some reason I do not understand, the Ubuntu installer does follow your wish to install Grub onto the Ubuntu drive, but then writes "menu.lst" as if you would be booting from the Windows Drive.

---

### Post by jukingeo on 2008-05-25
> **meierfra. said:**
> I assume our last two post overlapped and you haven't tried  my most recent suggestion yet. Actually you also  should be able to boot straight into   XP by changing the boot order.

Yeah, we are overlapping.  We are both on-line at the same time, however I have to get out and then boot back in to test the settings.

Anyhoo.  HORRAY!!!  The last part what you wrote to fix windows worked!  I just followed what you wrote earlier to edit the hard drive comments and then replaced the last bit that you wrote on Windows this time into the menu.lst file...saved it and BAM!  I am dual booting.

Well, that didn't seem to be too bad.  


> **meierfra. said:**
> ```
So Grub is installed on the Ubuntu drive.
```

For some reason I do not understand, the Ubuntu installer does follow your wish to install Grub onto the Ubuntu drive, but then writes "menu.lst" as if you would be booting from the Windows Drive.

At least I believe that has happened.  The Ubuntu installer section on installing Grub is kind of vague.  But from the sound of it, it said it wanted to alter something (what was that MBR or other??) on the Windows drive and I was like "Oh, no you don't.  Nothing is touching the Windows drive".  So I thought that I was doing everything in my power to prevent this situation from happening.  In the end I couldn't get into Windows OR Ubuntu.  If it wasn't for the live CD I would have been able to log on to this forum to explain what happened.

Could explain what happened?  It seems like you knew exactly what was going on and homed right into the problem.  

Well, anyway, thanx a bunch!  You are definitely a Grub Guru!

Now...there are two other minor issues.

1) I have noticed that my drive partitions now appear as folders in under the File Browser.  When I booted via the Live CD, I had nice little drive Icons.  Is there a way I can change the folder Icons for my drives back to those little drive icons?  Would that be something you know how to do (if it can be done)??

2) I have the dreaded Sound Blaster X-fi sound card.  That is the next thing I want to get working.  While initially this was not a supported sound card in Ubuntu, I heard there are beta files out and that you can get at least some kind of sound out of the card.  Not sure if you know anything about this either, but if you do I would appreciate some help getting that sound card working.

Thanx,

Geo

---

### Post by meierfra. on 2008-05-25
> Nothing is touching the Windows drive"

I think you reached that goal. Just for fun, change the boot order in the bios and see whether you boot directly into XP.

---

### Post by Maestro23 on 2008-05-25
Beta Drivers for Sound Blaster X-Fi: [http://connect.creativelabs.com/linux/default.aspx](http://connect.creativelabs.com/linux/default.aspx)
Good luck.

---

### Post by jukingeo on 2008-05-25
> **meierfra. said:**
> I think you reached that goal. Just for fun, change the boot order in the bios and see whether you boot directly into XP.

Change the boot order to what?  On my machine with the BIOS I have it does say that if there is a primary IDE drive in place, that will be the boot drive.  Based on that I don't think I can ajust the boot order to the SATA drive. I can however, push my F12 key and I will get a boot menu and from there I can select the SATA drive.  If I didn't have an IDE primary, then the boot drive would be the SATA0 position (I can hook up two SATA drives on board) and that will boot from the boot sequence.

I would like to know what it was that caused the problem considering the fix didn't seem to be too bad. That is for reason being that I do want to document this and put it away with all my Ubuntu Help files.  (I am creating a special "Help" folder to document any problems I have with their resolves).

Anyway, I have my email working with Evolution and it just so happens my printer is supported through Linux.  So the big problem that still remains is that I have no sound.  Neither my Alesis audio interface (device I use for pro recording work) nor my Sound Blaster X-Fi is working.

I think there is a fix for the X-fi in the works so I am going to check into that.

Thanx again.

Geo

Anyway, thanx again for your help.

---

### Post by jukingeo on 2008-05-25
> **Maestro23 said:**
> Beta Drivers for Sound Blaster X-Fi: [http://connect.creativelabs.com/linux/default.aspx](http://connect.creativelabs.com/linux/default.aspx)
Good luck.

Yes, I did hear about a fix.  I am going to look into it today because I would like to get SOME kind of sound working.  I am going to want to try some games and some of the Ubuntu audio programs

I am going to do the Upgrade to Ubuntu Studio as well.

I will update everyone how that works out.

Thanx,

Geo

---

### Post by meierfra. on 2008-05-25
```
I would like to know what it was that caused the problem
```

The setting  in menu.lst  depend on the boot order in the bios. For example (hd1,2) refers to the third partition on the second hard drive.  (Grub starts counting at 0)   But what the second hard drive is depends on the bios (the first one is always the drive your are booting from, but everything else can by random)  The problem is that the Ubuntu installer does not know how the drives are ordered and so just makes a guess. Of course it will get it wrong from while to while.

This much   I understand. But I do not understand why the installer does not realize that you asked for grub to be installed to drive which contains the ubuntu partition. In this case all (hd?,?) have to be (hd0,?) and there is not reason for the Ubuntu installer to get it wrong.

Whenever I install Ubuntu to my external drive, I have the same problem. So after ubuntu is installed, I do not reboot immediately. Instead I edit  "/boot/grub/menu.lst" by changing all the (hd?,?) related to ubuntu to (hd0,?).

---

### Post by jukingeo on 2008-05-25
> **meierfra. said:**
> ```
I would like to know what it was that caused the problem
```

The setting  in menu.lst  depend on the boot order in the bios. For example (hd1,2) refers to the third partition on the second hard drive.  (Grub starts counting at 0)   But what the second hard drive is depends on the bios (the first one is always the drive your are booting from, but everything else can by random)  The problem is that the Ubuntu installer does not know how the drives are ordered and so just makes a guess. Of course it will get it wrong from while to while.

This much   I understand. But I do not understand why the installer does not realize that you asked for grub to be installed to drive which contains the ubuntu partition. In this case all (hd?,?) have to be (hd0,?) and there is not reason for the Ubuntu installer to get it wrong.

Whenever I install Ubuntu to my external drive, I have the same problem. So after ubuntu is installed, I do not reboot immediately. Instead I edit  "/boot/grub/menu.lst" by changing all the (hd?,?) related to ubuntu to (hd0,?).

There was a question on the install that did ask if the boot partition was to be located on hd0.  I could have mis-interpreted that to mean it is going to install Grub on that partition.  So naturally I selected "1".  Now that I am reading this and taking into account past posts here, I think that I DID put grub on the correct drive, but because of the misleading question, I ended up telling it to boot from the wrong drive by using the "1" designation instead of keeping it at the default of "0".

More then likely I would have left it alone if it wasn't for what I been reading about the dangers of installing Grub on the main Windows boot drive.  I was told to avoid that at all costs.  So the question in the Grub install instructions was contradictory to that and led me to believe it was doing one thing when in fact it was doing something else.

Considering that it happens to you as well.  I think that it is the poor wording of that question.  I think it the devs should rework that question so it is clear that Grub will not be installed or affect the installation on the Windows drive, but rather it is designating a point of reference to booting the partitions.

So thus it wasn't an issue of where Grub was being loaded, but where it was pointing to access the boot partition on the hard drives.  Naturally I mis-interpreted the poorly worded instruction and told it to look on the (1) partition...which of course, is incorrect.

While I am still a bit unclear about everything, your explanation did shed some light on what happened.

I think that Grub developers should make that section of the install a bit clearer as to what is going on because it was downright confusing and I wouldn't be surprised that many more people made that same mistake.

Thanx again for your help.

...Oh! While I have you here, I am trying to install OSS from a .deb file, but the instructions say I must do so from the "Failsafe Terminal" boot up.  However, I don't know much about navigating and finding files in the Failsafe Terminal.  Thus far I did do as the OSS instructions asked and put the file on my desktop, but for some reason it can't find the file.

Thanx,

Geo

---

### Post by meierfra. on 2008-05-25
> Considering that it happens to you as well. I think that it is the poor wording of that question. 

No. The question asks where to install grub. You and I told the installer to put it on (hd1). And the installer does exactly that. But the installer  then writes the wrong numbers into menu.lst, despite the fact that it has all the information to do it correctly. The problem is a poorly written installation program and not a poorly worded question.

---

### Post by jukingeo on 2008-05-26
> **meierfra. said:**
> No. The question asks where to install grub. You and I told the installer to put it on (hd1). And the installer does exactly that. But the installer  then writes the wrong numbers into menu.lst, despite the fact that it has all the information to do it correctly. The problem is a poorly written installation program and not a poorly worded question.

Ok.  I just knew something wasn't right with the program.

Anyway, I do have another question about Grub.  What if I wanted to change the boot order AND also include the USB port on the boot list.  What would I have to do?

Thanx,

Geo

---

### Post by meierfra. on 2008-05-26
> What if I wanted to change the boot order AND also include the USB port on the boot list. 

If I understand you correctly, you want to add  "Ubuntu" to the Windows Boot Loader on your internal drive.

There are two ways:

1) You can use WinGrub: [http://users.bigpond.net.au/hermanzone/p9.html]("http://users.bigpond.net.au/hermanzone/p9.html")


2) Manually add Ubuntu to "boot.ini". This is a little bit tricky and I do not really recommend it. But if you want,  I can show you how to do it.

---

### Post by jukingeo on 2008-05-27
> **meierfra. said:**
> If I understand you correctly, you want to add  "Ubuntu" to the Windows Boot Loader on your internal drive.

There are two ways:

1) You can use WinGrub: [http://users.bigpond.net.au/hermanzone/p9.html]("http://users.bigpond.net.au/hermanzone/p9.html")


2) Manually add Ubuntu to "boot.ini". This is a little bit tricky and I do not really recommend it. But if you want,  I can show you how to do it.


Hello, 

Hmmm, I guess this is more complicated than I thought.

Ok these are my takes:

1) If it involves messing with the Windows drive, then this is a big "No", but if it is the easier of the two, it can't hurt to hear you out.

2) This way sounds better than #1, but I am curious so again, I will hear you out.

Thanx,

Geo

---

### Post by meierfra. on 2008-05-28
If you want to add ubuntu to the windows bootloader, you certainly have to mess with Windows in some way or another. 

Solution 1) is entirely done  done from Windows, you need to download a file, unzip it, execute an .exe file, edit boot.ini and configure WinGrub. The link I gave you has very detailed instruction.

Solution 2) is done entirely from Ubuntu.  The steps are like this
a)  Edit boot.ini
b)  Backup the boot sector of your Windows Partition.
c)  Install Grub to the Boot sector of the Windows Partition.
d)  Copy the Boot sector of the Windows Partion to a file on the Windows C: drive.
e)  Restore the Windows Boot sector with the Backup from Step b).

So Solution 2 only changes  one file on the Windows Partiton and adds another. But it temporarily erases the Windows Boot sector.
It also uses "dd" which,  if you used wrongly, can  erase a whole hard drive.  

But why do you want to add Ubuntu to the Windows Boot Loader? Isn't your current setup working just fine?

---

### Post by jukingeo on 2008-05-28
> **meierfra. said:**
> If you want to add ubuntu to the windows bootloader, you certainly have to mess with Windows in some way or another. 

Solution 1) is entirely done  done from Windows, you need to download a file, unzip it, execute an .exe file, edit boot.ini and configure WinGrub. The link I gave you has very detailed instruction.

Solution 2) is done entirely from Ubuntu.  The steps are like this
a)  Edit boot.ini
b)  Backup the boot sector of your Windows Partition.
c)  Install Grub to the Boot sector of the Windows Partition.
d)  Copy the Boot sector of the Windows Partion to a file on the Windows C: drive.
e)  Restore the Windows Boot sector with the Backup from Step b).

So Solution 2 only changes  one file on the Windows Partiton and adds another. But it temporarily erases the Windows Boot sector.
It also uses "dd" which,  if you used wrongly, can  erase a whole hard drive.  

But why do you want to add Ubuntu to the Windows Boot Loader? Isn't your current setup working just fine?

Whoa!  That seems to be a really lengthy and risky to change a simple function as the boot order.  I think there is a misunderstanding.  Let me clarify:

I just wanted to be able to change the boot order from the boot loader (Grub) screen.  Right now if I turn on my computer and walk away, it loads up Ubuntu on default.  What if I wanted it to boot to Windows first?

Also I heard that there is a way to set the boot loader to boot directly from the USB port.

I figured that would just require a few settings within Grub, right?

---

### Post by meierfra. on 2008-05-28
I knew I was misunderstanding your request.  

This one has a really easy solution:


```

sudo  apt-get install startupmanager
gksudo startupmanager
```

and change your default OS to Windows.


Or you can edit "menu.lst" manually:


Just move your windows item  between the lines


# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

and

### BEGIN AUTOMAGIC KERNELS LIST

---

### Post by meierfra. on 2008-05-28
> Also I heard that there is a way to set the boot loader to boot directly from the USB port.

You are already booting from the USB. Grub is installed on the MBR of the USB drive.

---

### Post by king EZi on 2008-05-29
you have to boot up your system with a windows cd and select recovery mode by pressing R (note: this is when you see a blue screen with that option available) then you will get a DOS prompt, there type: fixmbr and it will as you which operating system you want to fix, select your windows OS. Good luck! 

Then after that you may try to install ubuntu all over again.

---

### Post by jukingeo on 2008-05-29
> **meierfra. said:**
> I knew I was misunderstanding your request.  

This one has a really easy solution:


```

sudo  apt-get install startupmanager
gksudo startupmanager
```

and change your default OS to Windows.


Or you can edit "menu.lst" manually:


Just move your windows item  between the lines


# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST



### BEGIN AUTOMAGIC KERNELS LIST

Thanx,

I knew it had to be simpliar than what you said earlier.

---

### Post by jukingeo on 2008-05-29
> **king EZi said:**
> you have to boot up your system with a windows cd and select recovery mode by pressing R (note: this is when you see a blue screen with that option available) then you will get a DOS prompt, there type: fixmbr and it will as you which operating system you want to fix, select your windows OS. Good luck! 

Then after that you may try to install ubuntu all over again.

Thanx for the input, but Meierfra already walked me through a fix which was much simpler than this method.

---

### Post by jukingeo on 2008-05-29
> **meierfra. said:**
> You are already booting from the USB. Grub is installed on the MBR of the USB drive.

It is?  I don't have a flash drive installed though.  But I did want to put a version of Ubuntu on a flash drive so this way I could boot it up on another computer if I wanted to.

---

### Post by meierfra. on 2008-05-29
Sorry, I thought you current Ubuntu install was on an external USB  hard drive.

How big is you flash drive? If it is   4GB or more, I suggest a regular install.  (just make sure that in step 7 of the installation, you click on "advanced" and install Grub to the MBR of your flash drive)

If it is less than that you are probably better off with a persistent LIVE USB install:

[http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/]("http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/")

---

### Post by jukingeo on 2008-05-30
> **meierfra. said:**
> Sorry, I thought you current Ubuntu install was on an external USB  hard drive.

How big is you flash drive? If it is   4GB or more, I suggest a regular install.  (just make sure that in step 7 of the installation, you click on "advanced" and install Grub to the MBR of your flash drive)

If it is less than that you are probably better off with a persistent LIVE USB install:

[http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/]("http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/")


Yes it is a 4gb flash drive.

Mainly I want it for a Windows Laptop computer (my wife's), but if I want to boot up Ubuntu, all I have to do is stick the flash drive in the USB port and I am good to go and have a version of Ubuntu set up with my settings without disturbing too much on my wife's laptop.

It is really NOT a mandatory thing, but it is a cool project I would like to try out with the newly bought 4gig flash drive I got.

---

### Post by meierfra. on 2008-05-30
> Yes it is a 4gb flash drive.

O.K when you can install it the same way you installed ubuntu on your SATA drive.  You just need to pay attention where you install grub.
(Although you might have the exact same problem as you had  now. But you know how to fix it)

---

### Post by jukingeo on 2008-06-03
> **meierfra. said:**
> O.K when you can install it the same way you installed ubuntu on your SATA drive.  You just need to pay attention where you install grub.
(Although you might have the exact same problem as you had  now. But you know how to fix it)


OK, Thanx,

I will try it out later in the week and see what happens. Also I do still have to see if my wife's laptop can boot from the USB.  I am not sure if it does.

That leaves me with another question.  If I put Ubuntu and Grub on the flash drive, it shouldn't affect the current system settings, correct?  This way with the flash drive out, the computer should boot normally to Windows, right?

Geo

---

### Post by meierfra. on 2008-06-03
Yes, unless you accidentally install Ubuntu or Grub to the Windows drive.

---

### Post by jukingeo on 2008-06-04
> **meierfra. said:**
> Yes, unless you accidentally install Ubuntu or Grub to the Windows drive.

So what should I look out for to make sure that it doesn't do that?

Thanx

Geo

---

### Post by meierfra. on 2008-06-04
Just do everything in the same  way as you installed Ubuntu on the sata drive. The only thing tricky is to use "advanced" at Step 7. But you already know how to do that. So you should not have any problems.

---

### Post by jukingeo on 2008-06-06
> **meierfra. said:**
> Just do everything in the same  way as you installed Ubuntu on the sata drive. The only thing tricky is to use "advanced" at Step 7. But you already know how to do that. So you should not have any problems.

Ok, thanx for the info.

I decided to forgo this 'experiement' for now because I am having much larger problems getting my audio and video applications to run properly in Ubuntu.

But I did document everything for when I get back to this.

Thanx again for your help.

Geo

---

