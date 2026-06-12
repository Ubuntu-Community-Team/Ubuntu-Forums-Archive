---
title: "new user"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by amireli7 on 2008-06-28
I bought a new computer and installed ubuntu for the first time. Windows was never installed. I tried it, but because I couldn't get office to work and openoffice didn't do the trick for me I decided, reluctantly, to go back to windows. I put a windows XP install disk in the DVD drive, set bios to boot from CD but nonetheless my computer starts ubuntu.

Any suggestions?

---

### Post by masterjonny on 2008-06-28
Do you have multiple CD drives? 

Even though your computer is set to boot from a disc by default it will look in your primary one.

---

### Post by amireli7 on 2008-06-28
I only have one DVD/CD.

---

### Post by Canis familiaris on 2008-06-28
Try pressing F8 at boot time and choose CD medium as boot medium.
BTW What problems did you face in Ubuntu? We could help you solve those problems.

---

### Post by antmenj on 2008-06-28
Did you save changes in the bios?

Did the DVD drive even try to boot?

BTW what was the issue with openoffice?

---

### Post by Canis familiaris on 2008-06-28
You nessecarily do not need to remove Ubuntu to run Windows. You could dual boot or run Windows in Virtualbox/VMWare and do [this]("http://amitech.50webs.com/ultimate.html")

---

### Post by amireli7 on 2008-06-28
When I brought word documents from work to work on at home and I'd open it with openoffice it didn't quite come out right. I had to learn how to do everything, like making tables, making forms etc. from the beginning. I learned that I could install office with a program called wine but figuring out how to do it was too complicated for me. My kids would bring disks to play with, and couldn't. Figuring out how to use an ipod took a while etc. Google Earth was really slow. It just seemed like too much work for a home user such as myself with an average computer background. This is the first time I posted on a forum btw and am pretty impressed how quickly my post was answered. If you have any suggestions before I format my hard disk and install windows I'm open to suggestions.

---

### Post by amireli7 on 2008-06-28
> **antmenj said:**
> Did you save changes in the bios? 
Did the DVD drive even try to boot? I don't know.
BTW what was the issue with openoffice?

I saved the changes, and I don't think the DVD even tried to boot, but I don't know.

---

### Post by Canis familiaris on 2008-06-28
> **amireli7 said:**
> I saved the changes, and I don't think the DVD even tried to boot, but I don't know.

Did you try pressing F8 or whatever key combination at startup for selecting boot disks? What is your motherboard.

---

### Post by amireli7 on 2008-06-28
I just tried pressing F8 but didn't work.
my motherboard is  GA-MA69GM-S2H (?)

I know ubuntu can be installed on a computer that already has windows, but can I install windows on a computer that already has ubuntu?

---

### Post by hyper_ch on 2008-06-28
well, in a year M$ plans to support ODF in M$O... so you might want to change to an open document format anyway...

---

### Post by Canis familiaris on 2008-06-28
> **amireli7 said:**
> I just tried pressing F8 but didn't work.
my motherboard is  GA-MA69GM-S2H (?)

I know ubuntu can be installed on a computer that already has windows, but can I install windows on a computer that already has ubuntu?

Does Ubuntu boot CD work?

---

### Post by amireli7 on 2008-06-28
> **Anurag_panda said:**
> Does Ubuntu boot CD work?

I don't understand the question.

---

### Post by Canis familiaris on 2008-06-28
> **amireli7 said:**
> I don't understand the question.

Put the Ubuntu Live Cd now when you are booting, Does the following menu come which asks you to Install Ubuntu.
[IMG]http://i168.photobucket.com/albums/u178/anurag_panda/ubuntuboot.gif[/IMG]

---

### Post by bubba_169 on 2008-06-28
> **amireli7 said:**
> I don't understand the question.

Can you boot from the Ubuntu cd? If so then the problem might be with the Windows cd itself...

---

### Post by amireli7 on 2008-06-28
I rebooted with the ubuntu CD and my computer recognuzed it. I didn't get the exact window but I got a language menu. Anyway, it booted form the CD, I think. en I put in a different windows XP disk and it still did not boot from that disk.
When my computer starts up I get a line which says something like : boot from cd/dvd:
after which I tried pushing y, enter, F8 - just about anything imaginable and then it sys something like - to boot from CD press any key which I do and then it says something like starting GRUB 1.5
The screens flash by quickly as the computer starts.

---

### Post by antmenj on 2008-06-28
So if you boot ubuntu then put in the windows cd can it read files on it?

OR have you ever installed from that exact windows cd before?

---

### Post by Canis familiaris on 2008-06-28
> **amireli7 said:**
> I rebooted with the ubuntu CD and my computer recognuzed it. I didn't get the exact window but I got a language menu. Anyway, it booted form the CD, I think. en I put in a different windows XP disk and it still did not boot from that disk.
When my computer starts up I get a line which says something like : boot from cd/dvd:
after which I tried pushing y, enter, F8 - just about anything imaginable and then it sys something like - to boot from CD press any key which I do and then it says something like starting GRUB 1.5
The screens flash by quickly as the computer starts.

That means your PC is booting CD at boot. 
Also this means your Windows install CD is at fault. The other CD mught be the copy of the first CD, so I guess it will not work.
Get another Windows CD from somewhere else.

---

### Post by amireli7 on 2008-06-28
The 2 CDs are completely different, neither one worked. But I seem to have solved the problem by switching my new keyboard with an older keyboard. For some reason after I switched keyboards I was able to get into the boot menu with F12 which I wasn't able to do with the new keyboard. Thanks for all the help.

---

### Post by Canis familiaris on 2008-06-28
But it still wont work because both CDs are kaput.

---

### Post by robertchahine on 2008-06-28
> **amireli7 said:**
>  I couldn't get office to work and openoffice didn't do the trick for me I decided, reluctantly, to go back to windows.



Have you tryed installing office on [virtualbox]("http://virtualbox.org")? Because it works like a charm

---

### Post by amireli7 on 2008-06-28
> **Anurag_panda said:**
> But it still wont work because both CDs are kaput.

It seems to be working. I'm formatting my (other) computer right now.

I don't know why my computer was not booting according to the order listed on the bios, or why I was not able to access the boot order menu with the new keyboard, but right now it seems to working.

---

### Post by amireli7 on 2008-06-28
> **robertchahine said:**
> Have you tryed installing office on [virtualbox]("http://virtualbox.org")? Because it works like a charm

I never heard of virtualbox. Why does a home user need two operating systems on one computer?

---

### Post by Canis familiaris on 2008-06-28
> **amireli7 said:**
> I never heard of virtualbox. Why does a home user need two operating systems on one computer?
To get the best of both Linux and Windows. See [this]("http://amitech.50webs.com/ultimate.html") screenshot

---

### Post by amireli7 on 2008-06-28
> **Anurag_panda said:**
> To get the best of both Linux and Windows. See [this]("http://amitech.50webs.com/ultimate.html") screenshot

I understand that linux is free and less vulnerable to viruses, but if I have both OSs then those two advantages are irrelevant. What other advantages would ubuntu have for a regular user? BTW, I didn't see the screen shot, though in a previous comment you linked to a picture with both OSs (is that what you meant?) which I admit is a cool picture.

---

### Post by Canis familiaris on 2008-06-28
> **amireli7 said:**
> I understand that linux is free and less vulnerable to viruses, but if I have both OSs then those two advantages are irrelevant. What other advantages would ubuntu have for a regular user? BTW, I didn't see the screen shot, though in a previous comment you linked to a picture with both OSs (is that what you meant?) which I admit is a cool picture.
It is the same picture.

Advantages of Linux:
(1) It is free and open source. (doesn't matter to you because you already have Windows)
(2) Free of viruses, spyware, amd other malware
(3) It is faster than Windows which has office, ant-virus, anti-spyware, etc.
(4) Easier management of software via Synaptic.
(5) With Virtualbox you can run both Windows and Ubuntu simultaneously and if you have a reasonably powerful PC than the Windows Virtual Machine will load in seconds inside VIrtualbox and you can run your favourite MS Office, etc.

What is your PC configuration? Could you post the RAM, processor, graphics card, etc.? We could help you set up Windows in Virtualbox. It'll take some effort for initial setup but It would be worth the effort though.
With this setup you could run internet in Ubuntu and could also protect your Windows from Virii/Spyware.

---

### Post by amireli7 on 2008-06-28
I have 2 computers. The newer, which I am installing windows right now has:
Processor: AM2 Atalon 4600+X2 
Memory: 1024MB DDR2 800MHZ
motherboard: gigabyte GA-MA69GM-S2H
Hard dirve: 160GB 7200 RPM SATA2 
DVD: LG Super Multi 20x DVD

The older one:
Pentium[R] D CPU 2.80 GHz
1.93 GB RAM

---

### Post by Canis familiaris on 2008-06-28
> **amireli7 said:**
> I have 2 computers. The newer, which I am installing windows right now has:
Processor: AM2 Atalon 4600+X2 
Memory: 1024MB DDR2 800MHZ
motherboard: gigabyte GA-MA69GM-S2H
Hard dirve: 160GB 7200 RPM SATA2 
DVD: LG Super Multi 20x DVD

The older one:
Pentium[R] D CPU 2.80 GHz
1.93 GB RAM

Pretty good configurations! I assume you do not use BOTH of them for gaming,
And are you willing to that little time and effort for getting your PC as per that screenshot?
I would suggest you use the Pentium D PC for this because it has more RAM.

BTW WHat is your graphics card?

---

### Post by amireli7 on 2008-06-28
I finished installing windows so switching keyboards did the tick. This new keyboard I have has all sorts of features for windows so that I thought there might be a problem with ubuntu.

I don't do any "gaming" if by that you mean games which require high performance computer or graphics.

I don't know what graphics card I have. I think it's built into the motherboard but I don't know.

By installing ubuntu and virtual machine is their any danger of losing data, accidentally formating prt of the hard disk? etc.

---

### Post by Canis familiaris on 2008-06-28
> **amireli7 said:**
> 
By installing ubuntu and virtual machine is their any danger of losing data, accidentally formating prt of the hard disk? etc.
It is very unlikely with an Ubuntu installation and only happens when user becomes careless.
The likelyhood of losing data by Installing Windows in Virtualbox in Linux is as much as Installing MS Office in Windows. So I reckon it is safe.
BTW Did you remove Ubuntu while installing Windows?

---

### Post by Canis familiaris on 2008-06-28
Oh so your graphics in the AMD machine is (integrated) ATi Radeon X1250, thats same as mine. So we know where we are headed.
Could you tell me the name of the motherboard of Pentium D PC so that I could find its graphics card too.

---

### Post by amireli7 on 2008-06-28
I formatted the entre hard disk, so ubuntu is gone for now.

---

### Post by Canis familiaris on 2008-06-28
> **amireli7 said:**
> I formatted the entre hard disk, so ubuntu is gone for now.
You can easily install Ubuntu along with Windows for dual boot.
Since this is a fresh Windows install, you do not even need to defragment it. So go ahead and install Ubuntu.
(1) Insert the live CD to install Ubuntu.
(2) Select the option to run Ubuntu in Live CD mode.
(3) When you get to the live environment, go to System->Administration->Partition Editor
(4)In Partition editor you'll see all your current partitions. I presume since you formatted the entire hard disk so there would be only one partition which would be C: in Windows.
(5) Resize the Windows partition. Keep it sufficiently large so that you could install all your programs. I think 32GB would be sufficient.
(6) Apply the changes.
(7) Now you would have (YOUR HARD DISK SPACE TOTAL SPACE) - (SPACE ALLOTTED TO WINDOWS) as unallocated.
eg. if it is 160 GB partition and you kept Windows having 32 GB, you would have 128GB as unallocated now.
(8) Create a new Primary partition of 16 GB and select its file system as ReiserFS (you could choose ext3 here too but I suggest ReiserFS for system partition)
(9) Create another partition of about 256MB more than your RAM. I suppose it would be 1.25 GB for your AMD PC, 2.2GB for your Intel PC) and format it as SWAP.
(10) Select the rest of space and set the remaining partition as Extended Partition which you could use to create logical drives for more partitions.
(11) Create a logical drive of sufficient size that it could hold all your documents in Ubuntu, and virtual Windows XP installation. I suggest it to be from 32 to 64GB.
(12) Format the rest of extended partition as NTFS logical drive. This partition could be used for sharing files b/w Windows and Ubuntu.

Then install Ubuntu and in the install select the 
partition in (8) mount point as /
partition in (11) mount point as /home
partition in (9) would be automatically used as SWAP.

BTW if you do not game and plan to run Windows in Virtualbox and do not experience hardware problems in Ubuntu, you do not need Windows as the dual boot option at all. You could wipe out Windows. The Windows in Virtualbox would be as powerful as Windows physically in your hard disk.

And besides if you do not manage to set up tyour PC as per that screenshot and do not want Ubuntu you could always pop in that Windows CD and install Windows again.

---

### Post by amireli7 on 2008-06-28
> **Anurag_panda said:**
> Oh so your graphics in the AMD machine is (integrated) ATi Radeon X1250, thats same as mine. So we know where we are headed.
Could you tell me the name of the motherboard of Pentium D PC so that I could find its graphics card too.

P5VD2-MX  (?) That's what it says when I turn on the computer.

---

### Post by Canis familiaris on 2008-06-28
> **amireli7 said:**
> P5VD2-MX  (?) That's what it says when I turn on the computer.

Ah! VIA chipset! 
Use that AMD machine for this. I do not much about VIA.

---

### Post by amireli7 on 2008-06-28
> **Anurag_panda said:**
> You can easily install Ubuntu along with Windows for dual boot.
Since this is a fresh Windows install, you do not even need to defragment it. So go ahead and install Ubuntu.
(1) Insert the live CD to install Ubuntu.
(2) Select the option to run Ubuntu in Live CD mode.
(3) When you get to the live environment, go to System->Administration->Partition Editor
(4)In Partition editor you'll see all your current partitions. I presume since you formatted the entire hard disk so there would be only one partition which would be C: in Windows.
(5) Resize the Windows partition. Keep it sufficiently large so that you could install all your programs. I think 32GB would be sufficient.
(6) Apply the changes.
(7) Now you would have (YOUR HARD DISK SPACE TOTAL SPACE) - (SPACE ALLOTTED TO WINDOWS) as unallocated.
eg. if it is 160 GB partition and you kept Windows having 32 GB, you would have 128GB as unallocated now.
(8) Create a new Primary partition of 16 GB and select its file system as ReiserFS (you could choose ext3 here too but I suggest ReiserFS for system partition)
(9) Create another partition of about 256MB more than your RAM. I suppose it would be 1.25 GB for your AMD PC, 2.2GB for your Intel PC) and format it as SWAP.
(10) Select the rest of space and set the remaining partition as Extended Partition which you could use to create logical drives for more partitions.
(11) Create a logical drive of sufficient size that it could hold all your documents in Ubuntu, and virtual Windows XP installation. I suggest it to be from 32 to 64GB.
(12) Format the rest of extended partition as NTFS logical drive. This partition could be used for sharing files b/w Windows and Ubuntu.

Then install Ubuntu and in the install select the 
partition in (8) mount point as /
partition in (11) mount point as /home
partition in (9) would be automatically used as SWAP.

BTW if you do not game and plan to run Windows in Virtualbox and do not experience hardware problems in Ubuntu, you do not need Windows as the dual boot option at all. You could wipe out Windows. The Windows in Virtualbox would be as powerful as Windows physically in your hard disk.

And besides if you do not manage to set up tyour PC as per that screenshot and do not want Ubuntu you could always pop in that Windows CD and install Windows again.

I did steps 1 throuh 10 but I couldn't figure out how to do 11.

---

### Post by Canis familiaris on 2008-06-28
> **amireli7 said:**
> I did steps 1 throuh 10 but I couldn't figure out how to do 11.

I hope you have created an extended partition as per #10.
Now let me expain:
A hard disk has a limitation of 4 primary partitions. Now 4 partitions is far too less. So generally you can create 3 primary partitions and 1 extended partition. In the extended partition you can create unlimited no. of partitions a.k.a. logical drives.
So right click on the extended partition (grey portion), select new partition and create the partition as I stated in the previous post.

See how you learn great stuff in Linux/Ubuntu.
I hope you enjoy it. :)

---

