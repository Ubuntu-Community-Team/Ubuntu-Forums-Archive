---
title: "Evaluating risks with Asus X201E for installing dual boot"
date: 2013-10-26
forum: New to Ubuntu
---

### Post by guadaatenea on 2013-10-26
Hi! I've just bought an Asus x201e notebook. It came with Windows 8, which seems to work rather slow and quirky (at least for me) on this 2gb-RAM pretty little thing. I saw on the Asus page that this model is sold with Ubuntu somewhere ([http://www.asus.com/Notebooks_Ultrabooks/X201E/#specifications](http://www.asus.com/Notebooks_Ultrabooks/X201E/#specifications)), so I think it's safe to give the existence of all the necessary drivers for granted (is it?).
Anyway, I would like to use dual-boot on it, but I've seen there seem to be a bunch of possible not-so-easy-to-fix problems with it, and as I've already paid for that Windows licence when I bought the thing, I wouldn't like to lose it, or its Recovery partition. 
So, the questions are:
-exactly how much do I risk screwing the original software and Recovery partition up by installing Ubuntu alongside Windows 8?
- what can I do to prevent that from happening? (I saw something about adding a small extra partition between Win8 and Ubuntu, not sure how necessary that might be)
- any known issues about Ubuntu on Asus x201e I should know about beforehand? (on a search on the site I found something about a wifi issue, not sure if it was somebody's punctual bad-luck-Brian problem or a known issue)
- which version should I install? (remember: 2gb RAM and an I-guess-crappy Celeron ULV processor). I thought 12.4 32 bits, am I right? or should I go for a newer one? I want it fast and stable above all.

(I'm not completely new on Ubuntu, I've used 9.10 Karmic between 2009-2011, but I'm posting this on the Absolute Beginner section because it was a long time ago and back then, when I installed, I just killed a pirate nonfunctional copy of Windows instead of trying to make a dual-boot)

---

### Post by sandyd on 2013-10-26
see [http://support.asus.com/Troubleshooting/detail.aspx?SLanguage=en&p=3&m=X201E&s=483&hashedid=IVotBp2Edz4XzX1Q&os=&no=1775](http://support.asus.com/Troubleshooting/detail.aspx?SLanguage=en&p=3&m=X201E&s=483&hashedid=IVotBp2Edz4XzX1Q&os=&no=1775) for instructions on how to create a recovery dvd to backup and reinstall windows if necessary

---

### Post by guadaatenea on 2013-10-26
"nevermind the risks" you mean? eventually, maybe, but anyhow I'd feel better if I could get some tips to prevent things from going wrong. Besides, the warranty in my country might expire if I change the OS for good (that's part of the disquiet, and since I bought the notebook three days ago and I don't consider it fully tested, it IS something to mind).

Even if you consider my worries irrelevant, the questions stand: 

1- how do I keep Win8 (and especially the Recovery partition) alive? I've never installed dual-boot and given the number of problems posted here it doesn't sound fool-proof.
2- which Ubuntu version should work faster and more reliably on this computer?
3- are there any known issues I should know?

---

### Post by guadaatenea on 2013-10-26
> **sandyd said:**
> see [http://support.asus.com/Troubleshooting/detail.aspx?SLanguage=en&p=3&m=X201E&s=483&hashedid=IVotBp2Edz4XzX1Q&os=&no=1775](http://support.asus.com/Troubleshooting/detail.aspx?SLanguage=en&p=3&m=X201E&s=483&hashedid=IVotBp2Edz4XzX1Q&os=&no=1775) for instructions on how to create a recovery dvd to backup and reinstall windows if necessary
I saw that, and it seems to be a mistake on Asus's website. X201E is a small notebook, something between a netbook and a notebook. Like a netbook, it has no DVD/CD drive, so that wouldn't work.

---

### Post by sandyd on 2013-10-27
> **guadaatenea said:**
> "nevermind the risks" you mean? eventually, maybe, but anyhow I'd feel better if I could get some tips to prevent things from going wrong. Besides, the warranty in my country might expire if I change the OS for good (that's part of the disquiet, and since I bought the notebook three days ago and I don't consider it fully tested, it IS something to mind).

Even if you consider my worries irrelevant, the questions stand: 

1- how do I keep Win8 (and especially the Recovery partition) alive? I've never installed dual-boot and given the number of problems posted here it doesn't sound fool-proof.
2- which Ubuntu version should work faster and more reliably on this computer?
3- are there any known issues I should know?
I didnt consider your worries irrelavant, nor was I saying never mind the risks - my statement was about how you could do a backup of your recovery partition so that if you actually do mess up your recovery partition/windows, you have a method to reinstall.

> **guadaatenea said:**
> I saw that, and it seems to be a mistake on Asus's website. X201E is a small notebook, something between a netbook and a notebook. Like a netbook, it has no DVD/CD drive, so that wouldn't work.

in that case [http://windows.microsoft.com/en-us/windows-8/create-usb-recovery-drive](http://windows.microsoft.com/en-us/windows-8/create-usb-recovery-drive)

---

### Post by guadaatenea on 2013-10-27
> **sandyd said:**
> I didnt consider your worries irrelavant, nor was I saying never mind the risks - my statement was about how you could do a backup of your recovery partition so that if you actually do mess up your recovery partition/windows, you have a method to reinstall.

When I replied that, your answer read only three letters "nvm", probably by some kind of weird mistake (I swear). I googled, read "nvm" meant "nevermind" and felt a bit appalled. Then, after I posted that little extension (I thought I was getting a "you sound stupid" reply for trying to keep Windows, when I actually legally kinda need to do so), the complete text of your reply showed. I didn't know whether you had edited in reply or it was a mistake from the first place, so I left both my replies there just in case, that was it. 

Thanks a lot, I'll check and report the results later! :)

---

### Post by sandyd on 2013-10-27
> **guadaatenea said:**
> When I replied that, your answer read only three letters "nvm", probably by some kind of weird mistake (I swear). I googled, read "nvm" meant "nevermind" and felt a bit appalled. Then, after I posted that little extension (I thought I was getting a "you sound stupid" reply for trying to keep Windows, when I actually legally kinda need to do so), the complete text of your reply showed. I didn't know whether you had edited in reply or it was a mistake from the first place, so I left both my replies there just in case, that was it. 

Thanks a lot, I'll check and report the results later! :)

was a thread edit - accidentally pasted the wrong link in, so I replaced the text with nvm while I went to go find the correct link so that you wouldn't click on the other one (which belonged in another thread) - sorry about that!

---

### Post by mastablasta on 2013-10-27
removing or damaging the OS doesn't void warranty. i mean what if a viruse destroyed the OS?

that's why recoverz method is for. and usually with netbook one is promted to create a backup of the OS on first boot. in netbooks with windows you do it on a USB drive.

methods to dualboot are indeed nto fool proof. Microsoft made sure of that to mkae is as hard as possible to install anything else on a mashicne.

still it is duable as long as hardware is supported. to check that you can boot into live session. that won=t do any changes to your current install or mess with the disk. good luck!

---

### Post by guadaatenea on 2013-10-31
Well, I'm having trouble trying to make it boot from USB. Actually, I can't get it to show me BIOS. I've tried pressing F2 (which is the instruction on ASUS website), F12 and delete (instructions on Ubuntu site), it just launched Win8.
Thank you!

---

### Post by phaenze on 2013-10-31
I bought an Asus x301a last month with Windows 7 - it's very similar to the x201e. Before installing, check a few things:
1. Do you have a 32-bit or 64-bit version of Windows? Check this [link]("http://pcsupport.about.com/od/windows-8/a/windows-8-64-bit-32-bit.htm") for how to find out.
2. Is it set up with GPT or MBR? Run fdisk (sudo fdisk -l) in Ubuntu to check. It will give you a fairly clear error message if you have GPT - which for this is actually desirable.

I'm presuming that your system is set up with GPT and (U)EFI. This is a good thing.

Anyhow, the overview of the process is this:
[LIST=1]
[*]Boot to Windows 8 and make iso copies of the recovery disks. Copy these so an external hard drive (although I left mine on).
[*]If possible, decrease the size of the Windows 8 partition under Windows.
[*]If you can't do it under Windows, you can change the size under Ubuntu. But, you will have to boot into Windows 8 and have it check the partition on next boot. Then, reboot into Win8, make sure the disks are checked and fixed and then reboot in Win8 again. To be honest, I ended up having to run the recovery utility to restore Windows - which took forever.
[*] Download the 64-bit version of Ubuntu (I used 12.04.3 LTS) and make a bootable USB.
[*]When you reboot, hit the <ESC> key, this should bring up a boot menu. You should see the USB drive listed twice. Pick the (U)EFI option.
[*]Install as usual.
[*]You won't be able to boot into Windows, so install and run boot-repair under Ubuntu. On my system, it fixed everything.
[/LIST]
At the end of the process I have a bootable Win8 installation, 64-bit Ubuntu and I later added a 32-bit Ubuntu.

Caveats:
[LIST=1]
[*]If the laptop is using secure boot, you will need to read up on possible issues with Ubuntu, UEFI and secure boot.
[*]If the system is set up with MBR (msdos under gparted), you may have problems with finding a free partition. MBR can only have 4 partitions - one of which can be an extended partition with logical partitions.
[*]You must use 64-bit Ubuntu for EFI. You can install 32-bit later (although there won't be a need to do so).
[/LIST]

I did the install in one evening. Everything works just fine. Well, except for Windows which runs just like it's supposed to. :)

Have fun.

Peace,
Paul :cool:

---

### Post by guadaatenea on 2013-11-03
Thanks a lot!, I'm still having a little trouble here, I have a 8gb usb disk to use, and my external 1Tb HD. But Win 8 doesn't offer me to make a partition recovery disk, it asks me for a 16gb empty usb (and I need the info on the external HD, of course I still have more than half of it but I need the c. 400gb of work information it contains). I might buy a 16gb pendrive tomorrow if there's no other option, but since phaenze said something about iso files... that might fix it for the moment.

---

### Post by Mark Phelps on 2013-11-03
> removing or damaging the OS doesn't void warranty. i mean what if a viruse destroyed the OS?


The seller gets to set the warranty terms, not the buyer... specifically, ASUS states in their warranty terms that > The warranty will not apply to or be valid under conditions including but not limited to the following: ... > i) There is damage from third party software or from virus(es);

This permits ASUS to disallow warranty coverage if another OS is installed and/or the existing OS suffers from damage by a virus.

It's generally a bad idea to tell folks that the warranty will still apply ... since manufacturers are very good at including exclusions that cover everything that can happen.

---

### Post by Mark Phelps on 2013-11-03
> But Win 8 doesn't offer me to make a partition recovery disk

Win8 is asking for enough space to make an image of itself, probably in compressed form -- which is why it takes more than 4GB.

---

### Post by guadaatenea on 2013-11-04
Yep, I know, I saw on the conditions that damaging Windows 8 would be enough excuse to void warranty. I bought a 16gb pendrive, nevermind, it's an extra money I didn't plan to spend but it might come in handy later anyway.

---

### Post by guadaatenea on 2013-11-04
*moved to new post, I guess it's another kind of problem now*

---

