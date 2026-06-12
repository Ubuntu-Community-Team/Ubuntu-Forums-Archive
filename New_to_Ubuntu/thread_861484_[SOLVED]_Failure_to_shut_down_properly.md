---
title: "[SOLVED] Failure to shut down properly"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by Confused Computer User on 2008-07-16
I have a Pentium II 400MHz with 254MB RAM (two 128MB DDR1 133MHz sticks). I’ve worked on Windows for a long time and only recently started experimenting with Linux. I downloaded Ubuntu 8.04 and made bootable CD. This went well and I loaded the Live CD (no system alteration... I want to wait a while before installing). The system loaded a bi slowly but it ran smoothly. I opened Open Office writer and then when I went to close it, the operation stop responding. Despite this Ubuntu (8.04) force shut it and the system kept running (I was surprised but pleased). 
Now my problem comes when I shut down Ubuntu (8.04). The system closes and the Disc pops out. On the screen I see a message telling me to remove the disc and close the CD tray (if any) and then press ENTER. I did this and waited about ten minutes without anything happening. Finally I shut down the computer manually. I rebooted this time without the CD to make sure that nothing happened. Windows booted up and ran as before but the question still lingers: why didn’t Ubuntu (8.04) shut down properly?
:confused:

---

### Post by drubin on 2008-07-16
Try download the alternate cd. and install Xubunt(For lower end systems).

---

### Post by fatality_uk on 2008-07-16
If you type the following into a terminal and copy and paste the output of the first 25 lines of the file here please.

> gedit /etc/init.d/halt

---

### Post by Confused Computer User on 2008-07-16
Fatality UK, I would gladly type &#8220;gedit /etc/init.d/halt&#8221; into a terminal but I am not sure I want to but up Ubuntu again, especially since I have no clue what happened in the first place. I want to also add another 128MB RAM stick which would give me the 384 MB RAM that Ubuntu recommends. 
On another note, what is gedit /etc/init.d/halt suppose to display and how do I access the terminal in Ubuntu (I am an absolute beginner when it comes to Linux)
Thanks.

---

### Post by Confused Computer User on 2008-07-16
Sorry to ask this here but where do you get your avatar?

---

### Post by fatality_uk on 2008-07-16
> **Confused Computer User said:**
> Fatality UK, I would gladly type “gedit /etc/init.d/halt” into a terminal but I am not sure I want to but up Ubuntu again, especially since I have no clue what happened in the first place. I want to also add another 128MB RAM stick which would give me the 384 MB RAM that Ubuntu recommends. 
On another note, what is gedit /etc/init.d/halt suppose to display and how do I access the terminal in Ubuntu (I am an absolute beginner when it comes to Linux)
Thanks.

Ahh. Yes upgrade RAM :)

That's the shutdown script. An a similar Intel PIII PC I had, I had to change the following line to correctly shutdown.

When and if you do bring Ubuntu back up, go into the menu Applications->Accessories->Terminal to bring up the terminal. Alternatively, press alt+F2 and type ```
gnome-terminal
``` and that will bring it up also.

The avatar. Can't remember. I think it was [http://tux.crystalxp.net/](http://tux.crystalxp.net/)

---

### Post by Confused Computer User on 2008-07-16
Fatality UK, you say: “An a similar Intel PIII PC I had, I had to change the following line to correctly shutdown” . So am I to understand that I would have to bring up the terminal and type “gedit /etc/init.d/halt” in it. I am a bit confused because in the last part you say I had to change the following line but I don’t see what you mean by following line.
How much part does the ram play in this whole situation? (Keep in mind this was a live CD boot up... id did not install it) Will my 254MB RAM be able to cut it?
Thank you in advance (for the help and the site).

---

### Post by avtolle on 2008-07-16
I think the RAM is the problem. The Live CD needs 384 mb to install, using the graphical installer, and Ubuntu needs a minimum of 256 mb to run. I'd give the alternate installation iso burned to CD a try (text based installer, so if you are just wanting to check Ubuntu out, ignore this) to install; the system requirements for Ubuntu are 256 mb RAM, but it might run, albeit a bit slowly, with 256 (which, if I understand correctly, is reduced to 254 mb, likely due to the graphics chip sharing some RAM).

---

### Post by FreewheelinFrank on 2008-07-16
Blame Bill:

[http://antitrust.slated.org/www.iowaconsumercase.org/011607/3000/PX03020.pdf](http://antitrust.slated.org/www.iowaconsumercase.org/011607/3000/PX03020.pdf)

My laptop never shuts down fully.

---

### Post by dislocated on 2008-07-16
I have the same problem on an old PIII running xubuntu. I've never given it much thought, and it never gives me any real problems. When I shut down, I just let Linux shut down as far as it can, and then I push the button.

BTW, I *love* the email from Bill... So typical.

---

### Post by Confused Computer User on 2008-07-16
Dislocated, you mentioned that you have a similar problem with your Pentium III. Now is this with a full install or are you running the live CD like me. On that note did anyone else have similar problems?
FreewheelinFrank, you suggest to blame Bill.  Well I can’t really since my Win95 (on the same computer) shuts down properly and without a problem.
Avtolle, you are right, it is 356 (I can’t add). The video card I have is old (I’m willing to bet it has 4MB) and doesn’t share memory with the RAM.

---

### Post by FreewheelinFrank on 2008-07-17
> **Confused Computer User said:**
> Dislocated, you mentioned that you have a similar problem with your Pentium III. Now is this with a full install or are you running the live CD like me. On that note did anyone else have similar problems?
FreewheelinFrank, you suggest to blame Bill.  Well I can&#8217;t really since my Win95 (on the same computer) shuts down properly and without a problem.
Avtolle, you are right, it is 356 (I can&#8217;t add). The video card I have is old (I&#8217;m willing to bet it has 4MB) and doesn&#8217;t share memory with the RAM.

To be fair on Bill, the Pentium II 400MHz seems to date from about 1998, and the email was written in 1999. However, it does seem to be true that hardware is tailored to the Windows interpretation of standards, rather than the standards themselves, which is my understanding of why Windows works and Linux (sometimes) doesn't.

---

### Post by fatality_uk on 2008-07-17
Check out this page:
[https://help.ubuntu.com/community/EeePC/Fixes#Shutdown](https://help.ubuntu.com/community/EeePC/Fixes#Shutdown)

Although it's for an eeePC, it solved my PIII problem.
But DO add the RAM ;)

---

### Post by Confused Computer User on 2008-07-17
Ok, so fatality UK let me just make sure I got this right.
What I should try (could work or not) is to: go into the menu Applications->Accessories->Terminal. Once there I should paste: “gedit /etc/init.d/halt” into the terminal and hit the return/enter key. Once there I add “modprobe -r snd-hda-intel to my /etc/init.d/halt”. Now do I hit Return/enter or do I click on something else. Please comfirm.
Once I try this I’ll get back to the forum and post whatever I got (given time restrictions, 2 weeks…maybe a bit more) Thank you for the help so far.

---

### Post by t0p on 2008-07-17
Getting more RAM is always a good idea, but I would question how necessary it is.  I use a Pentium 4 with 256 MB RAM, and I have no problem at all running Ubuntu and Kubuntu.  I have also successfully run the Ubuntu and Kubuntu LiveCDs on this system - they were a little slow, but that's to be expected from a LiveCD anyway.

---

### Post by t0p on 2008-07-17
> **Confused Computer User said:**
> FreewheelinFrank, you suggest to blame Bill.  Well I can’t really since my Win95 (on the same computer) shuts down properly and without a problem.
.

I think you misunderstood what FreewheelinFrank meant.  It is Bill's fault your pc won't shut down after running Linux, because Bill entered into a conspiracy with computer manufacturers to ensure they wouldn't work properly with Linux...

---

### Post by Confused Computer User on 2008-07-18
Thank you t0p for your post. You confirmend what I was thinking about from the start but did not really discuss. I knew that the amount of ram was sufficient and that the live CD's were slow. But because I only have 400MHz in term of processing power I find myself a bit over the bare minimum which is 300Mhz for Ubuntu. The Live CD took a full 10 to boot which is understandeble given my choice to boot from the CD and my hardware which is low end performance. However once running the menus were responsive and scrolling was surprisingly fast. However opening Open Office writer took again a few minutes and shutting it down was a bit of a problem. However I hope that more Ram and a possible install will smooth this over. However can you (or any one)please confirm if I can do the following while in a Live CD
"Go into the menu Applications->Accessories->Terminal. Once there, paste: “gedit /etc/init.d/halt” into the terminal and hit the return/enter key. Once there I add “modprobe -r snd-hda-intel to my /etc/init.d/halt”. Now should I hit Return/enter or do I click on something else".

this a post that was meant for fatalityuk but I hope any one can confirm it.
Thanks.:)

---

### Post by Confused Computer User on 2008-07-19
Can some one please reply to my last post?
> However can you (or any one)please confirm if I can do the following while in a Live CD
"Go into the menu Applications->Accessories->Terminal. Once there, paste: “gedit /etc/init.d/halt” into the terminal and hit the return/enter key. Once there I add “modprobe -r snd-hda-intel to my /etc/init.d/halt”. Now should I hit Return/enter or do I click on something else".:confused:
Thank you

---

### Post by lswb on 2008-07-19
> **Confused Computer User said:**
> 
...However can you (or any one)please confirm if I can do the following while in a Live CD
"Go into the menu Applications->Accessories->Terminal. Once there, paste: “gedit /etc/init.d/halt” into the terminal and hit the return/enter key. Once there I add “modprobe -r snd-hda-intel to my /etc/init.d/halt”. Now should I hit Return/enter or do I click on something else".

this a post that was meant for fatalityuk but I hope any one can confirm it.
Thanks.:)

You can do this but it will not change anything permanently from the live CD. When the live CD runs. it sets up a /etc and some other directories and files on a ram disk. That way no real hard disk use is necessary for temporary files and other variable information that is normally stored in files rather than ram. It is also a reason why it takes more memory to run from a live CD than an installed distro.

I would not be too concerned about failing to shut down completely from the live CD. IIRC I had the same issue with an old 600E thinkpad with 288MB when running the live CD, bit after installation shutdowns are normal.

---

### Post by mkvnmtr on 2008-07-19
It seems your problem is from ram usage of open office. Other than that the disk worked fine? Remember the live disk loads into ram so you don't have as much to play with for apps. I think anything you do in terminal on the live disk will not be saved after you shut down. I think the other poster thought you had Ubuntu installed. Some people say the have installen form the live disk with 256 Mb but most recomend the alt. install.

---

### Post by Confused Computer User on 2008-07-20
That's exactly it. The system ran smooth but the Open Office writer was dead slow... I could bearly type two letters (not words). Do you belive that an install will help? If so by how much?
Concerning the Terminal I think that I made a mistake somewher when shuting down because I did a resart and that went perfectly well.

---

### Post by lswb on 2008-07-20
The open office programs really need a lot of memory to run acceptably. With ubuntu installed on a hd, there will be more memory available to run programs and also access time for a hd is much faster than for a cd. You will definitely see improvement, but whether it will be enough to make using OO practical on that hardware, I can't say.

---

### Post by Confused Computer User on 2008-07-20
Thank you all for the input. So the conclusion is this: I believe that the CD works well but that I did something wrong during the shut down. Either pressd the ke too soon or not soon enough.

---

