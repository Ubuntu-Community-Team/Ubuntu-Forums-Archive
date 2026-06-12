---
title: "My windows Xp not open from the Grub (ubuntu 13.10)"
date: 2014-03-13
forum: New to Ubuntu
---

### Post by tigre2 on 2014-03-13
Hello Everybody.. 
I am one person that I am trying to switch from XP to ubuntu..I am trying Dual Boot Windows XP & Ubuntu 13.10 in my Computer (HP desktop 2.5 Ram memory and 2 terabites of Hard disk)..I wish to have XP while i am learning to use ubuntu
I have installed ubuntu 13.10 over my windows xp pack 2. I have followed the tutorials, guides and everything to do it. I did the process of partition of the hard drive and everything..
Well, my Ubuntu 13.10 is already installed and I can open it through my password but when I am trying to start windows through the grub the Black screen appears and cursor is blinking. My Computer is not doing Nothing.. I wait 3-4 hours to see if probably to start windows is slowly but Nothing happening..Just Black screen and cursor blinking
What could be the problem?
How I can assure that my installation was good?
 
Is my first time with Linux..
Thanks in advance
;)

---

### Post by oldfred on 2014-03-13
When you said over XP?
The installer give choices to replace or use entire hard drive or side by side. 
I prefer Something else as then I have total control of partitions and sizes, but that does require some knowledge of partitions and planning on how you want hard drive organized.

First try this in terminal in your Ubuntu install (not live installer), and if it does not add Windows run BootInfo report
sudo update-grub

You can install this in your Ubuntu install or into  your live installer.
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by nunecas123 on 2014-03-13
Have you tried running Boot-Repair to fix GRUB?
[http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)

Boot it from a USB or CD and choose recommended repair.

---

### Post by tigre2 on 2014-03-13
thanks for your fast answer..
Yes . I forgot to mention on my thread that I have used the third option " Something else"  during my  installation. I have organized "on manual" the partitions of my hard disk..
Ok. I will follow your recomendations..
thanks;)

---

### Post by tigre2 on 2014-03-13
I have tried all recomendations mentioned and Nothing..
I have run Boot repair through my CD Live (ubuntu 13.10). 
On create a Bootinfo summary I got this Information:
URL [http://paste.ubuntu.com/7087937/](http://paste.ubuntu.com/7087937/)
In case you still experience boot problems URL: [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
No changes has been performed on your computer

I did run again the Boot repair and I select "recommended repair"
I got this information: Boot successfully repaired
URL: [http://paste.ubuntu.com/7087990/](http://paste.ubuntu.com/7087990/)
in case still experience problems boot problem
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
you can now reebot (OK)

I push Ok I take out my live CD and Restart my computer. 
I have moved my cursor to:
microsoft windows xp professional (on/dev/sda1)
and enter To try to open my windows and Nothing. Just black screen and cursor blinking..
Ubuntu 13.10 starts very well my problem is my windows XP 
What is my Next Option??
I need to send an email to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]??
thanks

---

### Post by coffeecat on 2014-03-14
Not a Chat thread.

*Thread moved to **Absolute Beginners Section**.*

---

### Post by Vladlenin5000 on 2014-03-14
I think the problem here has to do with a corrupted partition, the NTFS one. When exactly have you noticed the Windows XP wasn't booting? I suppose that you tested it right after shrinking its partition... Has it started the chkdsk? It should have started it, take some time to check and correct the now smaller partition for logical error emergent from the shrinking process and then boot as usual. IF NOT THEN you should have booted with the Windows XP CD and proceeded to do a system repair (please refer to Microsoft support)... Only install the second OS after you're 100% sure the original one boots normally.

Assuming (guessing) you skipped some of the aforementioned steps, what *might* work now is booting from the XP CD and do the system repair. The side effect: It'll delete GRUB. In order to finally have the dual boot system as it should you should then boot with the Ubuntu CD, select the option to boot from the hard drive - it'll boot your already installed Ubuntu (hopefully) - and then just do ```
sudo update-grub
``` to restore GRUB.

---

### Post by oldfred on 2014-03-14
Boot-Repair cannot fix most Windows issues, you need the Windows XP disk for that.
Follow Vladlenin5000 suggestions, you may need to run chkdsk more than once to fix everything.

Is this a new larger hard drive on an older system? Sometimes BIOS settings can make a difference. When I installed my new SSD, I changed to AHCI so I could implement trim, but then XP does not work. You have to have BIOS in large or LBA for XP to still work.

---

