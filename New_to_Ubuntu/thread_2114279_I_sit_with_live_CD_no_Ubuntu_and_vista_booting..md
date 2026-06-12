---
title: "I sit with live CD no Ubuntu and vista booting."
date: 2013-02-09
forum: New to Ubuntu
---

### Post by oliver74 on 2013-02-09
Hello Forum,

i was installing Ubuntu with a happy smile. I was trying it for me and my wife haded vista, but when i burned the CD and installed Ubuntu, then Vista was gone. So i was reading in the forum's, how to install Grub and 1 click fix and emilia and so, but after that, all is gone now. So my wife is angry and i try to fix stuff, what is over mine mind now. Maybe someone can tell me how i get a dual boot vista & ubuntu , so i can still try it out. I run on a 32 bit system and istalled the 32 bit version with 2gb ram. is a desktop from hp 

 I was reading in a forum i shall make in the terminal:  

sudo fdick- lu and then  sudo parted - l ubuntu@ubuntu:~$ sudo fdisk -lu
ubuntu@ubuntu:~$ sudo parted-l
sudo: parted-l: command not found

No command found. i think i am in deep trouble, for god sack, please help me, so that my wife sees how awsome the forum and the people are,then i wanna so much still go to ubuntu and learn all ...

---

### Post by Megaptera on 2013-02-09
Try this & post the results to let members see if Vista is still there or not ...

Link and full instructions - [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by oliver74 on 2013-02-09
i downloaded it,but it says that:

ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$

---

### Post by oliver74 on 2013-02-09
thats all pure terror to sit and not to know whats up.

---

### Post by GameX2 on 2013-02-09
Try to install GParted; it'll scan your hard drive partitions.

Open a Terminal (CTRL-ALT-T) and type:
```
sudo apt-get install gparted
```Type your password.  Nothing will appear which is normal.  GParted will install.  Launch GParted from the Unity Dash (Windows Key).

Send us a screenshot of the GParted Windows.  We'll see if Vista is still there or not, along with your files.

EDIT: My mistake.  Sorry, type this in the Terminal:

```
sudo apt-get install gparted
```

---

### Post by oliver74 on 2013-02-09
ubuntu@ubuntu:~$ sudo apt-get gparted
E: Invalid operation gparted
ubuntu@ubuntu:~$  


it will not give me gparted

---

### Post by GameX2 on 2013-02-09
> **oliver74 said:**
> ubuntu@ubuntu:~$ sudo apt-get gparted
E: Invalid operation gparted
ubuntu@ubuntu:~$  


it will not give me gparted

Sorry for the mistake.

Open a Terminal (CTRL-ALT-T) and type:
 ```
sudo apt-get install gparted
```
Then open GParted (Windows Key, then type GParted).  Send a screenshot of the windows, just to verify.

---

### Post by Mark Phelps on 2013-02-09
> **oliver74 said:**
> Hello Forum,

i was installing Ubuntu with a happy smile. I was trying it for me and my wife haded vista, but when i burned the CD and installed Ubuntu, then Vista was gone. 
HOW did you know this? Because when you booted, it went directly into Ubuntu? If SO, that is how it is SUPPOSED to work -- and be corrected in 5 minutes running a simple command.  You should have come here then ...

> So i was reading in the forum's, how to install Grub and 1 click fix and emilia and so, but after that, all is gone now. 
OK ... so if you installed using Wubi, then my first comment doesn't apply and fixing that is a bit harder -- but even then, Vista would not be "gone".
> So my wife is angry and i try to fix stuff, what is over mine mind now. Maybe someone can tell me how i get a dual boot vista & ubuntu , so i can still try it out. ...
 I was reading in a forum i shall make in the terminal:  

sudo fdick- lu and then  sudo parted - l ubuntu@ubuntu:~$ sudo fdisk -lu
ubuntu@ubuntu:~$ sudo parted-l
sudo: parted-l: command not found

No command found. You should just enter the one command "sudo fdisk -lu" (lowercase L, not a one) and post the results back here.
> i think i am in deep trouble...

Well, maybe NOT. 

Since I'm not clear on this from your post ... what exactly is the situation with the PC right now? I presume you can boot into Ubuntu, right?

If that is true, we need to see the results of the fdisk command.  This lists out the partitions on your drive and will show us if the Windows partitions (containing Vista) are still there.

Once we confirm the Windows partitions are still there, you can do the command "sudo update-grub" -- and if it works OK, you will then have a new GRUB config file with an entry for Vista.

---

### Post by oliver74 on 2013-02-09
ok found it

 ubuntu@ubuntu:~$ sudo apt-get install gparted
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gparted is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu:~$ 

so i did that what you said and what you see?

---

### Post by oliver74 on 2013-02-09
ok mark phelps , i did and it says that there is a process running when i tryed to do what you said, because of gpad i think


root privileges are required for running gpad.

Since GParted is a powerful tool capable of destroying partition tables and vast amounts of data, only root may run it.

---

### Post by GameX2 on 2013-02-09
> **oliver74 said:**
> ok mark phelps , i did and it says that there is a process running when i tryed to do what you said, because of gpad i think


root privileges are required for running gpad.

Since GParted is a powerful tool capable of destroying partition tables and vast amounts of data, only root may run it.

Gparted is already installed.
Press the Windows key, then type "Gparted" in the dash.  Clicking on the application will ask you for your password.
GParted will then start, and we'll see how your partition table look like (and if Vista is still there).

Can you boot from Ubuntu on your PC, or only from the Live-CD?

---

### Post by oliver74 on 2013-02-09
so i did it and i cannot take a screen shot, do someone know a good screen shot how to take that

---

### Post by oliver74 on 2013-02-09
no problem i found in ubuntu a screenshot taker, let me see if i get it on here


Do someone know then what is up with my computer, when i take that screen shot?

---

### Post by oliver74 on 2013-02-09
ok mark phelps, this time it is running and i make the sudo 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   383340959   191670448+   7  HPFS/NTFS/exFAT
/dev/sda2       383342590   602757119   109707265    5  Extended
/dev/sda3       602758800   625137344    11189272+   7  HPFS/NTFS/exFAT
/dev/sda5       383342592   598829055   107743232   83  Linux
/dev/sda6       598831104   602757119     1963008   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

what was then the different between sudo -lu and gparted?

---

### Post by oliver74 on 2013-02-09
i can only start with cd

---

### Post by GameX2 on 2013-02-09
No worries, Windows Vista wasn't deleted, your files are apparently still there. ;)

What exactly happen when you start your computer without the CD?  Do you get an error message?
My advise from here would be to use the software "Boot-Repair", but please wait before trying anything, perhaps a more advanced user has better knowledge of how to solve the problem.

At least, Windows Vista wasn't wiped.
Please avoid double/triple posting by using the orange "Edit" button at the bottom of your forum message.

---

### Post by oliver74 on 2013-02-09
ok, when i restart the computer, nothing works. when ubuntu first started right, i was reading in threats, how to use grub and then i tried that, but it never let me go in the programm gurb, only 1 click fix. now when i started gurb, no 1 click fix or to go in the programm. so know i dont now more. is there something i can do that it runs right again. what do you need more to fix it and do you know someone to help me them?


Oh or can i remove Ubuntu and then i have vista back? Then i can re install it over wubi or uninex. I was only installing it over cd, because , when i install it over windows installer, i get the 64bit version.

---

### Post by GameX2 on 2013-02-09
> **oliver74 said:**
> ok, when i restart the computer, nothing works. when ubuntu first started right, i was reading in threats, how to use grub and then i tried that, but it never let me go in the programm gurb, only 1 click fix. now when i started gurb, no 1 click fix or to go in the programm. so know i dont now more. is there something i can do that it runs right again. what do you need more to fix it and do you know someone to help me them?


Oh or can i remove Ubuntu and then i have vista back? Then i can re install it over wubi or uninex. I was only installing it over cd, because , when i install it over windows installer, i get the 64bit version.

Do you have a Windows Vista installation/repair CD ?

---

### Post by oliver74 on 2013-02-09
was the gparted doing something? could it be that , because i installed gparted, that my computer will start ubuntu without the cd? and yes i have a vista recovery disk,but when i go on repair , it cannot repair it. so i have to reinstall all and then all photos and letters are gone. thats sad. is there no one who knows how to get the dual boot section, so i can deside what to run, vista or ubuntu ?

---

### Post by GameX2 on 2013-02-09
Do not reinstall anything, all the Vista data is still accessible!
I need additionnal details to help, otherwise I can't help much.
Not a single error message appear, when you start your PC without a CD-ROM?

I assume you tried to use a recovery media; do you have the installation disk of Vista instead?
Nothing is lost yet.

Installing Gparted couldn't damage your computer, booting Ubuntu from the Live-CD does not affect your current Ubuntu installation.

---

### Post by oliver74 on 2013-02-09
So, i started ubuntu without the cd:popcorn::D:KS. Thanks to gparted and the nice people from ubuntu forum:KS:D:popcorn:.

So now,can someone help me to get an dual boot, so i can start vista ( my wife ):KS and Ubuntu ( me ) :KS.

thanks to all of you

---

### Post by arpanaut on 2013-02-09
If you are booted into your installed Ubuntu OS open a terminal and input:
```
sudo update-grub
```

observe the output from that command and you should see an entry for windows.
If that is the case, then close the terminal and reboot, when you get to the grub menu hit the down arrow key until it is highlighted  on the Win entry and hit enter.
If all goes well that should boot your vista install.

---

### Post by LostFarmer on 2013-02-09
From your live cd linux, to install grub.  From a terminal:

```
mount  /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```  grub-install should indicate 'success', if it prints an error post it.

now you should be able to restart.

---

### Post by oliver74 on 2013-02-10
> **LostFarmer said:**
> From your live cd linux, to install grub.  From a terminal:

```
mount  /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```  grub-install should indicate 'success', if it prints an error post it.

now you should be able to restart.

do i not have gparted on my computer, so i dont need grub?

---

### Post by oliver74 on 2013-02-10
> **arpanaut said:**
> If you are booted into your installed Ubuntu OS open a terminal and input:
```
sudo update-grub
```observe the output from that command and you should see an entry for windows.
If that is the case, then close the terminal and reboot, when you get to the grub menu hit the down arrow key until it is highlighted  on the Win entry and hit enter.
If all goes well that should boot your vista install.

[LostFarmer]("http://ubuntuforums.org/member.php?u=1268688") is that the same lostfarmer tells me and do i have to have grub,because i have gparted?

---

### Post by GameX2 on 2013-02-10
> **oliver74 said:**
> do i not have gparted on my computer, so i dont need grub?

Gparted simply manage your partition, GRUB is your bootloader that you want to have installed, to make your dual-boot working.

Does the command from LostFarmer work?

EDIT:

Run this:

mount  /dev/sda5 /mnt sudo grub-install --boot-directory=/mnt/boot /dev/sda
Tell us what message you get after typing these commands.

---

### Post by oliver74 on 2013-02-10
ok i have that picture 

addy@addy-NC783AA-ABA-SR5703WM:~$ mount  /dev/sda5 /mnt
mount: only root can do that
addy@addy-NC783AA-ABA-SR5703WM:~$ sudo grub-install --boot-directory=/mnt/boot /dev/sda
[sudo] password for addy: 

the first sudo from farmer says: Only root can do that? Am i still on the right move?

and then i shall give in the password to do that, am i right when i do that?:confused:

---

### Post by oliver74 on 2013-02-10
Arpanaut says sudo update-grub and then i get this too

addy@addy-NC783AA-ABA-SR5703WM:~$ sudo update-grub
[sudo] password for addy: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-37-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-37-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda3
done
addy@addy-NC783AA-ABA-SR5703WM:~$

---

### Post by LostFarmer on 2013-02-10
> **addy@addy-**NC783AA-ABA-SR5703WM:~$ mount  /dev/sda5 /mnt
mount: only root can do that My error , did not think mount needed to be root.  For root permissions the use of 'sudo' give it to you.

  '**andy@andy-**' indicates you are booting into the installed hdd linux, not a live cd.  Update us if you are still having a problem and how you are booting.

---

### Post by oliver74 on 2013-02-10
Ok, so i have done that what [arpanaut]("http://ubuntuforums.org/member.php?u=45953") told me for 21 hours.

If you are booted into your installed Ubuntu OS open a terminal and input:
 	Code:
 	sudo update-grub 
observe the output from that command and you should see an entry for windows.
If that is the case, then close the terminal and reboot, when you get to  the grub menu hit the down arrow key until it is highlighted  on the  Win entry and hit enter.
If all goes well that should boot your vista install.

So i sit now in Windows Vista and i can only boot in Vista, when i tip the arrow down, then i get the message, 1440x900 signal out of ranch. then i hit enter and then i can make a vista recovery or i hit f8 for advance stuff. so i did the recovery test and still it shows up when i hit the arrow down. so f8 and boot vista in normal mood.

But when i do nothing and hit the arrow not down, then i boot in Ubuntu. How get i the dual boot,where i choose what i wanna run?

Shall i try that under Ubuntu

mount  /dev/sda5 /mnt sudo grub-install --boot-directory=/mnt/boot /dev/sda

---

### Post by Bucky Ball on 2013-02-10
The sudo update-grub command found all OSs and everything actually looks present and correct.

You are not getting a list with a selection of OSs at boot? Then hit the shift key just after the BIOS screen when you start the computer. That should take you to the grub menu list. If you're still having problems you can install Boot Repair and run that.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If you want to change the menu list at boot then you should try Grub Customizer. That will allow you to change whether the list appears at boot or not and for how long along with a lot of other things.

[http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183)

---

### Post by LostFarmer on 2013-02-10
> Shall i try that under Ubuntu

mount  /dev/sda5 /mnt sudo grub-install --boot-directory=/mnt/boot /dev/sda  NO, that command is only if you were booting with the live cd and grub was not booting the computer.

If I read your post correctly, it sound like you can boot into Vista or Ubuntu.  That is duel booting.

Maybe you are thinking about  **virtual machine** (**VM**) booting ? Where one OS is ran inside of a different OS, if so that is way different than duel  booting.  I do not know how.  basically it is booting into ubuntu and running Vista as a program, if I understand the process correct.

---

### Post by oliver74 on 2013-02-11
What Bucky Ball is saying i mean.

When i start the computer, i wanna have a list to choose, like that

picture i uploaded, without hitting the arrow down. So maybe i will look a sec into the link Bucky Ball was giving me. Or maybe someone fast can tell me:D:KS

---

### Post by oliver74 on 2013-02-11
> **Bucky Ball said:**
> The sudo update-grub command found all OSs and everything actually looks present and correct.

You are not getting a list with a selection of OSs at boot? Then hit the shift key just after the BIOS screen when you start the computer. That should take you to the grub menu list. If you're still having problems you can install Boot Repair and run that.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If you want to change the menu list at boot then you should try Grub Customizer. That will allow you to change whether the list appears at boot or not and for how long along with a lot of other things.

[http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183)




thats what it says   Boot successfully repaired.

Please write on a paper the following URL:
[http://paste.ubuntu.com/1636442/](http://paste.ubuntu.com/1636442/)

In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or to your favorite support forum.

You can now reboot your computer.

The boot files of [The OS now in use - Ubuntu 12.04.2 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

ok so i restarted the computer and it was going directly to Vista. So i restarted the computer again and again and always it goes to vista and when i hit the shift key, it will not go to grub or ubuntu. maybe i have to start with cd again. 

A Question, would it not be better to install Ubuntu with Wubi? then i would have a start menu in the beginning to choose Vista or Ubuntu , right? But i have a feeling i am so close to score to have it done. something i miss.

---

### Post by Bucky Ball on 2013-02-11
1. You have one a menu. You have Windows and Ubuntu in the screenshot. Hit Ubuntu. What happens? If you boot into Ubuntu then open a terminal (Applications>Accessories>Terminal or type in Dash) and:

sudo update-grub

Straightforward and the 'quick way' to get this done, if it works. 

2. Failing the above, back to the links in my last post. 

The only odd thing about your screenshot is you appear to be using the Windows bootloader and not grub. Forget Wubi. It is a different thing and I can't help with that anyhow (many can't). You are wanting a dual-boot and that option isn't one.

---

### Post by oliver74 on 2013-02-11
> **Bucky Ball said:**
> 1. You have one a menu. You have Windows and Ubuntu in the screenshot. Hit Ubuntu. What happens? If you boot into Ubuntu then open a terminal (Applications>Accessories>Terminal or type in Dash) and:

sudo update-grub

Straightforward and the 'quick way' to get this done, if it works. 

2. Failing the above, back to the links in my last post. 

The only odd thing about your screenshot is you appear to be using the Windows bootloader and not grub. Forget Wubi. It is a different thing and I can't help with that anyhow (many can't). You are wanting a dual-boot and that option isn't one.

The screenshot was an exsample for what i wanna have it. I do not have the Vista Ubuntu boot menu. 

My computer now, is direcly booting in Vista. I installed grub and make the 1 click repair. How can i go back in Ubuntu? only with cd i think or. ?

---

### Post by arpanaut on 2013-02-11
Okay, so with the "boot repair" (aka one click solution) you have set windows as the default boot option.
Now when you boot there should be a 10 second delay with the Ubuntu Grub screen visible, when you see that push the down arrow and select the first Ubuntu choice. That will get you to the installed Ubuntu OS.
The screenshot you show is what the options are at boot IF you have installed Grub4dos  as your boot loader, which you do not.

Before you do anything else tell us if when you boot that you get a screen that offers listed as to which OS to boot, also by using the arrow keys you can select Ubuntu and can you successfully boot into into Ubuntu?

If that is the case then you are all set, the default boot is windows which will please the wife and when you want Ubuntu then it is easy enough for you to get there. 

If you want the grub4dos option, then I don't know, please research, I think that by doing that you will complicate the entire process.  But that is one of the beauties of Linux there are many options, and you can do as you please, I think that grub4dos is installed from windows, but I don't know for sure as I use the default Ubuntu Grub.

Hope that Helps.

---

### Post by oliver74 on 2013-02-11
> **arpanaut said:**
> Okay, so with the "boot repair" (aka one click solution) you have set windows as the default boot option.
Now when you boot there should be a 10 second delay with the Ubuntu Grub screen visible, when you see that push the down arrow and select the first Ubuntu choice. That will get you to the installed Ubuntu OS.
The screenshot you show is what the options are at boot IF you have installed Grub4dos  as your boot loader, which you do not.

Before you do anything else tell us if when you boot that you get a screen that offers listed as to which OS to boot, also by using the arrow keys you can select Ubuntu and can you successfully boot into into Ubuntu?

If that is the case then you are all set, the default boot is windows which will please the wife and when you want Ubuntu then it is easy enough for you to get there. 

If you want the grub4dos option, then I don't know, please research, I think that by doing that you will complicate the entire process.  But that is one of the beauties of Linux there are many options, and you can do as you please, I think that grub4dos is installed from windows, but I don't know for sure as I use the default Ubuntu Grub.

Hope that Helps.

ok i will try in a sec, but can you tel me what that means. when i make the 1 click that came to read for me.

The boot files of [The OS now in use - Ubuntu 12.04.2 LTS] are far from  the start of the disk. Your BIOS may not detect them. You may want to  retry after creating a /boot partition (EXT4, >200MB, start of the  disk). This can be performed via tools such as gParted. Then select this  partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

the boot file are far from the start disk? can change that ??? 

AND

You may want to  retry after creating a /boot partition (EXT4, >200MB, start of the  disk). This can be performed via tools such as gParted.???

hmm

---

### Post by arpanaut on 2013-02-11
If you can boot into Ubuntu then no worries.
If you cannot, then that may be a possible solution.
with most modern systems that is not an issue

---

### Post by black3agl3 on 2013-02-11
Sorry for quoting this old post
[QUOTE=oliver74]
 So i sit now in Windows Vista and i can only boot in Vista, when i tip  the arrow down, then i get the message, 1440x900 signal out of ranch.  then i hit enter and then i can make a vista recovery or i hit f8 for  advance stuff. so i did the recovery test and still it shows up when i  hit the arrow down. so f8 and boot vista in normal mood.

But when i do nothing and hit the arrow not down, then i boot in Ubuntu.  How get i the dual boot,where i choose what i wanna run?
[/QUOTE]
Can you actually reach the welcome screen for windows vista?
Oh and is english your first language?

------
Just a thought... I seem to understand there is no problem with his computer. My guess is that oliver74 misunderstood dual-booting... Thinks he can boot into vista and from there switch to ubuntu and vice versa.

---

### Post by oliver74 on 2013-02-11
black3 , i am from germany, maybe thats why, i am not so good to english.

so i tried the arrow down and then i wait into i hear the harddrive stop, but still a black screen. I have to hit enter and then i come into a window.

1 ram disk settings
2 vista recovery

f8 for advance settings. when i press f8 then the 1 is repair and the last is, start window normal. but when i start windows normal, it start the recovery session and i have to break and start new.

When i do nothing when i start the pc, i go direct to win vista.
arrow down to ram disk and vista recovery

so i have no ubuntu to boot, only i start it with the cd again.

is the problem not better fix, when i uinstall Ubuntu and then with wubi installer install it?

---

### Post by black3agl3 on 2013-02-11
Do you see something like this when booting up?
[http://upload.wikimedia.org/wikipedia/commons/c/cf/GRUB_with_ubuntu_and_windows_vista.png](http://upload.wikimedia.org/wikipedia/commons/c/cf/GRUB_with_ubuntu_and_windows_vista.png)

---

### Post by oliver74 on 2013-02-12
thats what i miss. I do not have that. And over night i haded the computer off and restarted it and i get nothing more. It's stop booting up. No arrow down works more. I sit with the cd from ubuntu and g parted find nothing too

---

### Post by oliver74 on 2013-02-12
when i the first time started vista again, the computer ask me if i wanna run a disk check and i did it. know i make a sreen shoot from gparted,but he finds nothing more of my harddrive. Is that because the bootloader from windows is in charge?

Ok, i was thinking what i else did yesterday, i was running cc cleaner. but could that maybe have taken some files? I am not sure. I haded the vista recovery disk running and it said, he could not find Vista. It looks like, i have the same problem again, but its time gparted is not finding my harddrive.

can i uninstall gparted and reinstall it? Is there someone who can help me? I was just telling my wife, that everything is ok, now all starts from the beginning again.

---

### Post by oliver74 on 2013-02-12
i have a pic from my harddrive too.

---

### Post by LostFarmer on 2013-02-12
Went from bad to worse.

Is the computer a desktop or laptop ?
What brand/model?
Have you done ANY thing in the bios/cmos settings ?

Sounds like a bios/cmos setting or hdd/cable problem.
Do you know how to get into bios/cmos at startup and check if the hdd is detected ?
(normal a F key ,esc or del keys , press as soon as comp. is turned on)

If it is a desktop have you been inside doing anything ?  if yes, check the cables.

the problem is not linux or Ms windows at this time.

---

### Post by oliver74 on 2013-02-13
i used only cc cleaner, normal clean thats all.

i have a desktop hp 2 gb and a nvidia onboard card.

no the hdd is not detected, for some time i used system care 6 and i think it mess the computer bios up. 

i now when i down load the bios for the mainboard, that it would run again, i did it, but i dont know how it works,when windows is not working.

can i somehow get to vista and ssfe the data on it? or the product key, so i can reinstall it? i have from hp recovery on the drive, i shall press f 11, but that will not work.

thanks for helping.

---

### Post by black3agl3 on 2013-02-13
> **LostFarmer said:**
> 
the problem is not linux or Ms windows at this time.
And that brought it to something way out of my league...

> **oliver74 said:**
> i used only cc cleaner, normal clean thats all.

i have a desktop hp 2 gb and a nvidia onboard card.

no the hdd is not detected, for some time i used system care 6 and i think it mess the computer bios up. 

i now when i down load the bios for the mainboard, that it would run again, i did it, but i dont know how it works,when windows is not working.

can i somehow get to vista and ssfe the data on it? or the product key, so i can reinstall it? i have from hp recovery on the drive, i shall press f 11, but that will not work.

thanks for helping.
Try looking up information about your motherboard and forcefully resetting your bios... **Dont try anything yet though**... I dont want to be responsible for making things even worse

EDIT: just to know... do you have any important information on your computer that you did not back up?

---

### Post by Bucky Ball on 2013-02-13
> **LostFarmer said:**
> Went from bad to worse.



+1. Just do some research, reinstall and try to follow the advice being given. I realise English is probably not your first language, but ...

---

### Post by LostFarmer on 2013-02-13
Normal software should not mess up the bios. 
 Till the bios sees the hdd , no software can.

First entering bios, is the date/time wrong ?  If yes, likely the motherboard needs a new battery.  Bad battery will cause the hdd not to be detected.

Next thing will be enter bios and do a 'reset to default settings' , normally that will be found on the save/exit page.  After you reset bios  and save-exit,  re-enter bios and check to see if it now sees the hdd , also reset the date/time.

The very last thing to try is a bios update, due to the very possibility that can if not done correctly , destroy the motherboard.

Just a note for now, if you ever open up the computer case be sure not only is the computer is shut down but the power cable is removed from the wall outlet.

After removing power, open the case and see if it has a lost of dirt inside, dust balls.  If yes do a web search on how to clean , if done wrong can destroy motherboard.

Just asking for now.  Do you have some other desktop ?  some other hdd, any size ?

---

### Post by oliver74 on 2013-02-13
ok , i did take out the cable from the computer and put them back on. then i tried to start the computer, nothing work, only black screen.

then i started the ubuntu cd and i run gparted and he found the harddrive again.

So can i restart the computer now and it works? Or do i need to install grub again?

And what was that with a batterie on my mainboard? I never heard that i have an batterie on my mainboard and where should that be at and how could that be change, if it is the problem? 

then i run utility disk check and it says i have 5 bad errors and i took a screen shot.

could that be the trouble?

ok i restart the computer and i am back in windows vista. I still miss the dual boot windows where i can choose Vista or Ubuntu. Without pressing arrow down.

---

### Post by LostFarmer on 2013-02-13
> And what was that with a batterie on my mainboard?  It is a big watch battery about size of a $.25 cent and it is silver in color .  They do not cost very much. Do not know about Germany money.  If it is bad the first indication is normally the time/date will continually be wrong after setting.  You will need to check you computer manual.

 > utility disk check and it says i have 5 bad errors   at this time likely no problem, but would recheck it every so often.

> ok i restart the computer and i am back in windows vista. I still miss  the dual boot windows where i can choose Vista or Ubuntu. Without  pressing arrow down. 	 Do not completly understand what you are trying to say.Go to [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)  , do you get a display something like that ?

---

### Post by oliver74 on 2013-02-14
Do not completly understand what you are trying to say.Go to [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)  , do you get a display something like that ?[/QUOTE]

thats what i try to say, i do not get a display.

it only says signal out of order change settings 1440x900 .

and then vista starts .

---

### Post by kurok on 2013-02-14
It sounds like the resolution for the bootloader screen in set wrong. I dont know if this will work or not since i have never tried it, maybe someone that has more experince will chime in and say if its possible or not.  Boot from your live disc again and follow the instructions on this page to install grub custiomizer [http://www.noobslab.com/2012/11/install-grub-customizer-302-in-ubuntu.html]("http://www.noobslab.com/2012/11/install-grub-customizer-302-in-ubuntu.html") Find this tool buy typing in its name and change your resolution to something your  moniter can handle. I hope this helps and good luck.

---

### Post by oliver74 on 2013-02-14
Ok, so i do the arrow down again, when i boot and it brings me only to ramdisk and vista recovery,but i cannot boot into ubuntu. still the same.

can someone tell me how to delete ubuntu and then i will reinstall it clean with Wubi.

i will try the grub 2 costimize and see what happen.

---

### Post by LostFarmer on 2013-02-14
> can someone tell me how to delete ubuntu and then i will reinstall it clean with Wubi  from all I have read, that is not a good option.   

I do agree with 'kurok' on the problem so should be able to come up with a solution.

---

### Post by oliver74 on 2013-02-21
thx

---

### Post by kurok on 2013-02-21
cool glad to be of help

---

