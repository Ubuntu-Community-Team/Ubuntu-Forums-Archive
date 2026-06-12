---
title: "Have a major problem or so it seems...."
date: 2008-08-05
forum: New to Ubuntu
---

### Post by OZFive on 2008-08-05
I am running Hardy Heron off a Sony Vaio N325E laptop and cannot get it to boot up normally as it has sinece 8.04 came out.

Bios screen lags
takes a while for Grub to come up
The Ubuntu boot slider comes up after a longer than usual bit and then the slider does it's slide back and forth quite a few times (normally it does one and then it loads everything.)

Then I get this.....


Someone please tell me what is going on here?

---

### Post by jamesrfla on 2008-08-05
Take a look at this and you will get your answer. [http://ubuntuforums.org/showthread.php?t=875181](http://ubuntuforums.org/showthread.php?t=875181)

---

### Post by st33med on 2008-08-05
Ahh... jamersfla has a solution. Look at his post, not mine. I am just an uninteresting little blip in this system, move along...

---

### Post by OZFive on 2008-08-05
I am looking into it, but before I do anything i want to make sure I understand what I am doing.  What happened to spontaneously casue for this to be needed.  It was working fine for months with Hardy Heron installed.

---

### Post by OZFive on 2008-08-05
Also I am having trouble wiht the instructions on that link.  I am not as advanced as that other user.  Can someone please give a step by step through this? I do NOT want to screw this up!

---

### Post by st33med on 2008-08-05
Well, the first step is to mount your HDD from the LiveCD. Just pop in the LiveCD and do this in the terminal:
```
sudo mount /dev/sda
cd /media/disk
```

Then, do everything else as this quote says, but, replace the root directory ('/') with /media/disk (eg: instead of /home/ it would be /media/disk/home)
> What is is saying is that when you edit the boot paremeters from GRUB, it does it only for that boot. If you want to make the changes stick, you need to edit the grub configuration file - but you need to do it in the correct form to prevent the changes from being deleted when the configuration file is overwritten when new kernels are introduced and the file is regenerated.
First make a backup
Code:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup

Now open to edit:
Code:

gksudo gedit /boot/grub/menu.lst

If you just add the options to each kernel manually, the changes will be deleted when the file is autoupdated later. So rather than doing it like that, find the line that says something like
Code:

# defoptions=splash quiet

And change it to something like
Code:

# defoptions=splash irqpoll

or using whatever parameters are necessary on your system. Do the same for the altoptions line (for the recovery mode kernel):
Code:

# altoptions=(recovery mode) single

and change to something like
Code:

# altoptions=(recovery mode) single irqpoll

Save and close the file, now regenerate it with the new options:
Code:

sudo update-grub

Double check the file to see that the options have been added correctly, then you can reboot and the changes will automatically be added in GRUB.

---

### Post by jamesrfla on 2008-08-05
> **st33med said:**
> Well, the first step is to mount your HDD from the LiveCD. Just pop in the LiveCD and do this in the terminal:
```
sudo mount /dev/sda
cd /media/disk
```

Then, do everything else as this quote says, but, replace the root directory ('/') with /media/disk (eg: instead of /home/ it would be /media/disk/home)

Don't use irqpoll. Try another option like acpi=off.

---

### Post by OZFive on 2008-08-05
oh boy am I a bit nervous about all this folks.  I tried the first command in the terminal and I get nothing from it but sitting there blankly looking at me.

I really hate to be a bother about all this but you folks have been great about this so far and believe me I would love to return the favor someday.  But I am having a nightmare using a Terminal here and the instructions of putting the /media/disk/  where usually /home/ would go... I do not know where to put it in the terminal instructions.  Please some more help on this?

---

### Post by OZFive on 2008-08-05
Okay so I got this far and did this..... Is what I changed in the screen shot correct?

I then tried the "***sudo update-grub***" in the Terminal and got this....

[I][B]ubuntu@ubuntu:/media/disk$ sudo update-grub
Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###[/B][/I]

---

### Post by st33med on 2008-08-05
You got really far...
You can still get into tty very slowly, right? Go into your Ubuntu install and do that command from a tty (Ctrl-Alt-F[1-6]). BE PATIENT :)

---

### Post by OZFive on 2008-08-05
okay I see what you mean about tty, (I had no idea that was there, I learn something new every day it seems) You say to go into my Ubuntu Installand do the "sudo update-grub" from there.  What do you mean for me to do exactly?

And I would have not gotten this far if not for you and the others that have helped thus far.

---

### Post by OZFive on 2008-08-06
Here is another question... I know some people put their home folder in a seperate partition from thier system install.  

Could I possibly do something like that?  Use GParted to create a seperate partiotion for my home folder, move it there, protecting it and then reisntalling 8.04 in the troublesome area? Starting over again fresh?

---

### Post by OZFive on 2008-08-06
A new day!

Help?

---

### Post by mjwhitfield on 2008-08-06
> **OZFive said:**
> Here is another question... I know some people put their home folder in a seperate partition from thier system install.  

Could I possibly do something like that?  Use GParted to create a seperate partiotion for my home folder, move it there, protecting it and then reisntalling 8.04 in the troublesome area? Starting over again fresh?

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Ask if you get stuck :)

---

### Post by OZFive on 2008-08-06
Cool!  I thank you for the instructions and am going to try it after I go to tthe store and get myself a 16gb USB Flash drive to back up my home folder first.  Is there anythin else I need to back up before I bite the bullet and reinstall to make the process a bit more smoth getting things back to the pre-trouble times?

---

### Post by Elfy on 2008-08-06
If you have edited any files - xorg or such then make a copy of those as well and you should be able to copy them back. It might also be worth - if you have enough room on the stick to copy your apt cache if you have bandwidth problems.

But if you haven't done anything else you should be okj with your /home backed up.

You could check your bash history in a text editor just to see if there is anything that jumps out at you - it's a hidden file in your /home

.bash_history

---

### Post by PmDematagoda on 2008-08-06
OZFive:- From the picture you posted, it seems that your hard drive either is about to fail or is sprouting bad sectors, I think you may need to replace your hard drive as well in addition to a reinstall.

---

### Post by OZFive on 2008-08-06
> **PmDematagoda said:**
> OZFive:- From the picture you posted, it seems that your hard drive either is about to fail or is sprouting bad sectors, I think you may need to replace your hard drive as well in addition to a reinstall.

It is still a new laptop ( I know that does not men anything in the long run ) I can still use the Live CD and access my HD which I am grateful for.  Iwill have to look out for it and make daily backups I suppose. 

I do not understand what yo mean though when a hard drive is sprouting bad sectors....

---

