---
title: "Different Dual Boot Problem -W7 no such disk"
date: 2011-11-15
forum: New to Ubuntu
---

### Post by 02darkRS on 2011-11-15
I have Windows 7 Ultimate x64 & 11.04 x64 installed on a 60GB SSD. Home, Swap, tmp, var, Windows Users, Apps, Programs are all installed on different Partitions on a Seperate 1TB HDD. 
 
I was running 11.04 for a few weeks on dev/sda2 with minimal issues. I installed W7 about a month ago on dev/sda1. The system was set up for this from the start & I followed directions provided for installing 7 after Ubuntu. After install a fix to the mbr had me up & running. 
 
I am frequently running into a booting issue which I cannot nail down. My son & wife use Ubuntu to do homeschooling all day. When I get home & start my schooling (have to use windows for this) I log off any Ubuntu users who are on, then restart (i've also tried shutdown to see if that makes a difference). Many times this will result in different errors when Windows 7 attempts to boot: 
 
**Some are:**
**1. When I choose W7 from Grub I get no such disk. I then have to restart in a W7 recovery CD & load a System Image. **
**2. When I choose W7 from Grub I get an error saying windows needs to repair startup. This never works & I always end up reloading a system image. **
 
**This only happens when I restart from Ubuntu or when booting up from a shutdown where Ubuntu was the last OS used.** It does not however do this everytime & I cannot find any rhyme or reason as to when it occurs.
Should I run a bootscript & post it up or? what would help you all help me figure this out? I am repairing windows 5-10 times a week.

---

### Post by BillyBoa on 2011-11-15
Well, the suspicious for problem issues I see:

1. The Win7 installation over Ubuntu. Something went wrong on MBR.

2. Why you are using so many partitions for Ubuntu? Is there a special reason?

---

### Post by BillyBoa on 2011-11-15
> **02darkRS said:**
> I have Windows 7 Ultimate x64 & 11.04 x64 installed on a 60GB SSD. Home, Swap, tmp, var, Windows Users, Apps, Programs are all installed on different Partitions on a Seperate 1TB HDD. 

Well I have a solution to propose.

You uninstall Ubuntu from the Windows MBR to clear it from the problem.

Then you reinstall Ubuntu formatting only the partition /
to create a new boot system.

I don't know if someone has something better to propose.

---

### Post by 02darkRS on 2011-11-15
followed a tutorial that said to have swap,tmp,var off the ssd. 
 
i can boot back into Ubuntu just fine when this happens. It's the sda1 w/ W7 that seems to be getting trashed. Never have a problem with Grub itself. It always loads & always lists everything as usual. Just when I choose Windows7 I get these failures.

---

### Post by 02darkRS on 2011-11-15
> **BillyBoa said:**
> Well I have a solution to propose.
 
You uninstall Ubuntu from the Windows MBR to clear it from the problem.
 
Then you reinstall Ubuntu formatting only the partition /
to create a new boot system.
 
I don't know if someone has something better to propose.
 
 
If that's the answer I can do that but, was hoping not to. 
Never uninstalled an operating system. What do I do? Just format that partition from inside windows or boot into live cd & use gparted ? (the system was formatted with gparted from a live cd before any installations).
 
Any other options? (i appreciate & accept your advice but as you said someone else may have another idea?)
If it did it everytime I'd easilly accept that it was something during installation that went wrong. But this is not an every time occurrence.

---

### Post by oldfred on 2011-11-15
It almost always helps to post boot script. But it may be something in BIOS that script does not show.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by BillyBoa on 2011-11-15
You can check and repair your MBR from the Windows part with the program "EasyBCD" from Neosmart (free for personal use).

---

### Post by 02darkRS on 2011-11-15
Billy, 
It sounds like you're pretty confident it's a problem in the MBR? If so, I'll try the BCD tonight. 
 
OldFred, thanks, I will get that going as well & post back with the outcome. Will this record even when I boot into Windows?

---

### Post by oldfred on 2011-11-15
No the script uses Linux commands. It can run from a liveCD or most Linux installs. Someone posted from Puppy but Puppy seemed not to have all the commands so not much was found.

---

### Post by 02darkRS on 2011-11-15
> **oldfred said:**
> No the script uses Linux commands. It can run from a liveCD or most Linux installs. Someone posted from Puppy but Puppy seemed not to have all the commands so not much was found.
 
How will this help track Windows7 issue then? Ubuntu always boots just fine now. I used to get serious mounting errors all the time but those have somehow resolved.

---

### Post by oldfred on 2011-11-15
It just shows all the files needed to boot and many settings. It is just to verify things look ok.
It may be something in grub or it may be Windows. Or it may be how one system shuts down. Are you hibernating in one or the other? Does Windows always boot ok from a cold boot (power on) thru grub?

---

### Post by Mark Phelps on 2011-11-15
Another thought ... I know that YOU are using Win7, but are either of the others WRITING to a Windows partition from inside Ubuntu, either the Win7 OS, or another NTFS partition?

And, are you hibernating Win7 when you shut down?

Asking because sharing NTFS partitions in a PC that hibernates has been shown to be related to filesystem problems in Windows.

---

### Post by 02darkRS on 2011-11-15
Interesting you both mention hibernate..... i went through all the easy to find steps to turn off hibernate or any power down options in windows 7 after install. however sleep remained as a valid option on the shutdown menu & my son bricked the PC yesterday by accidentally clicking sleep. Wouldn't wake up for anything. I had to follow the same steps as mentioned above to get it back. BUT, he admitted to it & I am certain that this is not what has been happening because it's bricked on me many times during a restart from Ubuntu. So, as of last night I was able to find the way to remove sleep as an option. 
Thus, as of now:
Windows is set to never sleep or turn anything off and the options are removed from menus. 
Ubuntu is set to never sleep or turn anything off. (however, the options still remain in the menus to hibernate & sleep)

1.AS far as writing to the disks.... i guess it's possible my wife has been. She definitely does not understand the structure but..... I also do not think she's been dl'ing any files that she would have saved to the C:/. However, my data drive is frequently saved to from inside ubuntu. This is a separate NTFS partition on the 1TB HDD.

2.Back to the hibernate, I have another thread where I've asked about an issue with ureadahead & it appears to be a hibernate thing. I've recv'd no responses there. At some point they will log off. leave the PC. then when I come back & move the mouse it's a black screen with ureadahead 285 error & some other misc statements & a :>_ flashing prompt which takes no input. [http://ubuntuforums.org/showthread.php?t=1874270](http://ubuntuforums.org/showthread.php?t=1874270)

3.Windows always boots from a cold start through grub IF windows was the last OS used and as long as I haven't just played with something & screwed it up but that's unrelated :P

thanks for all the help!

---

### Post by oldfred on 2011-11-16
I know grub sets some flags if it has trouble booting and am not sure about shutdown that may cause problems. 

Does Ubuntu cleanly shutdown? Does grub/Ubuntu post any messages while booting that would cause grub to save a boot issue flag?

---

### Post by Mark Phelps on 2011-11-16
I brought up hibernation, because AFAIK, when Windows hibernates, it squirrels away copies of the partition tables of all the "drives" it had open.  Then, when it wakes up, it rewrites the partition tables from the saved copies.

This is what I think has been happening when folks do the following:
1) Use Win7 for a while -- with other partitions open.
2) Hibernate Win7
3) Boot into Ubuntu
4) Mount one of the Windows partitions
5) Write to or modify files on the mounted Windows partitions
6) Shutdown Ubuntu
7) Reboot into Win7

Upon waking up Win7, discover the changes they made in 5) are GONE!

So basically, if you have a true dual-boot setup (Windows and Linux) and you hibernate Windows and you have shared partitions between Windows and Linux -- that is asking for problems.

---

### Post by 02darkRS on 2011-11-16
Mark, this is definitely not what's happening with mine. If we leave windows & boot ubuntu it's either a full shutdown or a restart. We're not hibernating. 
 
OldFred,  when I get the no such disk error it is in the grub screen that this occurs. So, how can I check those logs? The other times however it will go all the way to the w7 boot screen then tell me I need to repair starttup (which always fails) & then I have to load a new system image.

---

### Post by oldfred on 2011-11-16
In system, administration, log file viewer, you can review log files. I am not in 11.10 now, but the locations of many of the programs have moved on how to get to them. Look at dmesg & messages.

If UUID is correct, it is saying system is booting before hard drive has come up to speed. I have seem some say with the new systems they had to add a boot parameter  for delay.

[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
boot_delay=

---

### Post by Mark Phelps on 2011-11-16
So, if I understand what you said:
1) Windows always starts OK as long as, when the PC was shutdown last, it was in Windows
2) If Ubuntu was last used, Windows fails -- and you have to load a new "system image".
3) You're not hibernating or sleeping Windows; instead, you're shutting it down completely every time it is used.
4) You're not hibernating Ubuntu; instead, you're shutting it down completely every time it is used.
5) While in Ubuntu, the only Windows partition that is modified is the Data partition; the OS partition is never modified.

Wish I could be more encouraging ... but this is turning out to be a real mystery ...

The only question I have at this point is -- HOW are you "loading the new system image" when Win7 won't boot?

---

### Post by 02darkRS on 2011-11-17
> **Mark Phelps said:**
> So, if I understand what you said:
1) Windows always starts OK as long as, when the PC was shutdown last, it was in Windows
2) If Ubuntu was last used, Windows fails -- and you have to load a new "system image".
3) You're not hibernating or sleeping Windows; instead, you're shutting it down completely every time it is used.
4) You're not hibernating Ubuntu; instead, you're shutting it down completely every time it is used.
5) While in Ubuntu, the only Windows partition that is modified is the Data partition; the OS partition is never modified.
 
Wish I could be more encouraging ... but this is turning out to be a real mystery ...
 
The only question I have at this point is -- HOW are you "loading the new system image" when Win7 won't boot?
 
All Correct with the exceptions: 
4 & 5 sometimes just a restart is performed & then the other OS is booted into from Grub. for instance, my sons school can all be done on Ubuntu. So, he's on Ubuntu all day. Then I come home to start mine. Restart the PC & load windows 7 at Grub. 3 of 5 days this results in the errors I am posting about.
 
Loading the new system image has to be done through my Windows 7 DVD. Boot PC into the DVD menu, choos repair using system image. My system images are on a special Partition on the HDD just for system backup.
 
OldFred, I am in 11.04 & the OS's are on a SSD. Rarely have issues booting Ubuntu. So, I doubt that fast boot is my problem . I will check the Grub logs though for the No disk error in Windows7 loads.

---

### Post by oldfred on 2011-11-17
There used to be a problem were DRM or anti-virus software in Windows would overwrite grub and cause boot issues. Perhaps something related in Windows is checking and seeing non-windows boot loader and creating issues?

---

### Post by 02darkRS on 2011-11-22
Strangely enough I have not had a single instance of this since I asked the family if they were writing files to C:\ or accidentally Hibernating, etc...... I've posted this to try to remove th feature options altogether. If I can do that & I do not have any failures for a week, I think we can say this is solved & it was accidental hibernates/suspends by clumsy PC users! 
 
[http://ubuntuforums.org/showthread.php?p=11480263#post11480263](http://ubuntuforums.org/showthread.php?p=11480263#post11480263)

---

### Post by 02darkRS on 2012-01-13
Well, the issue returned. I have since repaired windows about 3 times & completely fresh installed one time. That was 13 days ago & I already have corrupted files again. I finally ran across the right search term though & found that the issue is my OCZ SSD, the vertex +. There is a firmware update to supposedly fix it. Now if I could just find a good noob guide to updating SSD firmware. . . . . . 

The interesting this in all this is the SSD error trashed windows many times on reboot. Some I could never get back into windows without a repair install. Ubuntu however threw disk mounting errors but always loaded...... (might have failed once I can't fully recall but no where near Windows7 numbers)

Search purposes: Check Disk & Mounting Errors on OCZ Vertex + SSD are a known issue. You need a firmware update to 3.55 (as of this time)

I will mark solved if this indeed fixes the issue.

---

