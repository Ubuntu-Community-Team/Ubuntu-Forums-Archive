---
title: "Dual boot grub problem. No menu, only command prompt after #set timeout. + xp home"
date: 2013-03-02
forum: New to Ubuntu
---

### Post by Syex on 2013-03-02
Hi, I'm new to Ubuntu and I am having a frustrating problem with dual boot.  I installed 12.10 on an old AMD, ATI system, sata hard disk with Windows xp home already on the other partition.  When I boot the computer, it goes straight to Ubuntu.  I looked into how to get the Grub menu and found a setting called 'set timeout' which according to advice from other posts I had to comment out to get the menu.  Now all that happens is the 'Grub>' command prompt appears.  I don't know how to progress. ](*,)

All I want is when the computer boots up to present me with a list of the two operating systems so I can select which one to boot into!  Before I changed the grub text I tried the 'Shift' button, however, that didn't work.  All that happened was 'grub loading' appeared in the top left for a second or two then vanished and booted straight into Ubuntu.  Is there a command one can type at the Grub> prompt which will allow the pc to boot up so I can at least change that 'timeout' setting back?

By the way, I have, and will continue to search for answers on this forum and other sources. 
I resorted to posting this question which unfortunately adds to an ever increasing list of similar questions because I'm still not finding a solution.  :confused:

I installed Ubuntu because sometimes I like a challenge, however this is ridiculous!  I think I've bitten off more than I can chew! Lol!

Syex

---

### Post by oldfred on 2013-03-02
Undo whatever you did and run this:

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

Sometimes this will bypass grub and just boot an otherwise working install.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)
[URL="https://help.ubuntu.com/community/UbuntuSecureRemix"]
[/URL]

---

### Post by Syex on 2013-03-02
Hi OldFred. Thanks for the quick reply!  Those pages look useful. I will attempt to do what you asked, give me a week at least. ;)  
One question before I can proceed is: How do I undo whatever I did when all I get is the Grub> prompt on boot?

Kind Regards

Syex

---

### Post by Grinage on 2013-03-02
If you have a live CD or DVD in some cases you can use the try ~buntu option and use that to undo the changes you made, I'm guessing to /etc/default/grub .  Hopefully you created a back up of the original or used comments to keep the machine from reading a particular line. For future reference if you're going to change a critical config file create a copy of it and call it *filename.old  *or *filename.bak* so if you need to undo your changes you can do it quickly and somewhat painlessly.  Or if you're a tweaker and you like to make changes to files often you can repeat the command line in the file you want to change and use a # at the beginning of the line. Doing so allows you to comment out unwanted commands and easily restore them if they don't do what you want.

Example:

GRUB_COLOR_HIGHLIGHT=blue/light-gray
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_DEFAULT=saved
GRUB_GFXMODE=640x480
GRUB_SAVEDEFAULT=true
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX="quiet"
#GRUB_CMDLINE_LINUX="nolpic"
#GRUB_CMDLINE_LINUX="acpi=off"

The # symbol tells your system to ignore everything after it on that line.  In this case I used different instructions to handle off ACPI commands that were causing fans not to function on my laptop and causing it to overheat.

In the future if you make changes to grub make sure you run ```
sudo update-grub
``` to make sure grub rebuilds correctly it will display what it's doing in your console for you to read.

---

### Post by Syex on 2013-03-03
Hi Grinage, last night I re-installed Ubuntu, probably an extreme move. Later I found this page and followed instructions: [http://askubuntu.com/questions/263296/dual-boot-and-grub](http://askubuntu.com/questions/263296/dual-boot-and-grub)  basically running sudo update-grub  This didn't work, I still got the message 'grub loading' for a second whilst holding shift then it booted into Ubuntu. 

I also updated to grub 2, however, I can't find the page with the details of how I did this.  I will try to find this info later if required. I ran boot-repair.
Here is the boot repair link as oldfred requested: [URL="http://paste.ubuntu.com/5581796/"]http://paste.ubuntu.com/5581796/


[/URL]

---

### Post by Syex on 2013-03-03
Some of the things that concern me on the report are: 

Unknown BootLoader on sda2 /sda3
cat: write error: Broken pipe 
Warning: extended partition does not start at a cylinder boundary. DOS and Linux will interpret the contents differently.

I'm thinking of running the tool again and selecting the Recommended-Repair, However, I'll wait for advice. :cool:

---

### Post by oldfred on 2013-03-03
When you move partitions about, data is not erased from old location. If that happens to be the PBR or partition boot record, script sees data in PBR but is not able to identify what boot loader it is (because it is not). You can ignore that issue unless it is a Windows NTFS partition as those have to have Windows boot signatures.

Not sure about the cat error, may be script issue.

Hard drives have not used cylinders since hard drives went over 8GB. Again you can ignore.
What is now important with new 4K drives and SSDs is that drives are on sector boundries that match drive. New partition tools start at sector 2048 and set partitions start points that are divisible by 8 which works for just about everything.

---

### Post by Syex on 2013-03-03
> **oldfred said:**
> When you move partitions about, data is not erased from old location. Is there any way I can tidy that up?  I'm going to go ahead and run boot-repair any time soon. (However, I'll keep my eyes open for a 'No not yet' type response lol!) 8-[

@oldfred, is there anything in that report that identifies the grub problem I have, because I don't fully understand it to be honest.  Thanks for your assistance.

Syex

---

### Post by oldfred on 2013-03-03
What grub problem are you having? I thought Boot-Repair fixed it?

While you can use dd to write 0s to any place on drive, it is very dangerous as any typo may erase the wrong thing. I rarely use dd and do not normally suggest it. The data is just there as is all data on a drive unless you totally erase entire drive. It will not cause any issues as it is not used by grub.

---

### Post by Syex on 2013-04-04
Hi, nothing worked so I gave up on the idea.:confused:  I've now installed Ubuntu 12.10 on a virtual machine, however now I'm getting an error message on Ubuntu's virtual boot stating: 'piix4 host smbus controller not enabled'.  I may yet post a new topic about this if I can't find an answer myself.

Syex

---

### Post by AndyOpie150 on 2013-04-04
I had a similar problem with my Windows grub after a hung install of Lubuntu. I could access my Windows OS thru my Ubuntu and Xubuntu distro's but was not recognized by grub. Tried the Boot-Repair Disk CD to no avail.

oldfred mentioned something about chkdsk command, but that it can only be run from a Windows OS.
Then I found this:
[ Hirens Boot CD]("http://&quot;http://www.hirensbootcd.org/'") It has a virtual Windows XP and Windows 7 OS which alowed me to run the chkdsk command. It replaced the missing files and now at least the partition was recognized.

I then ran this CD:
[ Boot-Repair Disk]("http://&quot;http://sourceforge.net/p/boot-repair-cd/home/Home/'") which fixed the grub menu to include my now recognizable Windows partition. When selected it booted right up to my Windows OS.

---

