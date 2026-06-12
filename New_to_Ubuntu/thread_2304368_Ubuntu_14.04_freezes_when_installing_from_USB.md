---
title: "Ubuntu 14.04 freezes when installing from USB"
date: 2015-11-26
forum: New to Ubuntu
---

### Post by Michael_Priest on 2015-11-26
I'm trying to install Ubuntu on my laptop but every time i go to install it, Ubuntu freezes when i install. I've downloaded the .iso and used Universal USB installer so i can install via my USB. I restart my laptop, then select to boot from the USB, I then get the selection screen and selct Install Ubuntu, this is where it freezes, with the Ubuntu logo. 

My machine:

[TABLE="class: tab_box, width: 100%, align: center"]
[TR]
[TD="class: tdb, align: right"]**Processor (CPU)**[/TD]
[TD="class: td, colspan: 2, align: left"]Intel® Core™i5 Dual Core Mobile Processor i5-4210M (2.60GHz) 3MB[/TD]
[/TR]
[TR]
[TD="class: tdb, align: right"]**Memory (RAM)**[/TD]
[TD="class: td, colspan: 2, align: left"]8GB KINGSTON SODIMM DDR3 1600MHz (1 x 8GB)[/TD]
[/TR]
[TR]
[TD="class: tdb, align: right"]**Graphics Card**[/TD]
[TD="class: td, colspan: 2, align: left"]NVIDIA® GeForce® GTX 850M - 2.0GB DDR3 Video RAM - DirectX® 11[/TD]
[/TR]
[TR]
[TD="class: tdb, align: right"]**2[SUP]nd[/SUP] Graphics Card**[/TD]
[TD="class: td, colspan: 2, align: left"]NONE[/TD]
[/TR]
[TR]
[TD="class: tdb, align: right"]**Memory - Hard Disk**[/TD]
[TD="class: td, colspan: 2, align: left"]750GB WD SCORPIO BLACK WD7500BPKX, SATA 6 Gb/s, 16MB CACHE (7200 rpm)[/TD]
[/TR]
[/TABLE]

Thanks in advance

---

### Post by mastablasta on 2015-11-26
does the ubuntu run in live session? if so you can go to live session and then click install icon. see if that works. 

also you probably have Nvidia Optimus graphics technology which is officially not supported for linux. so you need to look into that to make the graphics work well on your laptop.

---

### Post by Michael_Priest on 2015-11-26
No it doesn't, it still freezes when I try to run it.

---

### Post by mastablasta on 2015-11-26
well that is odd. now it would be a good time to check for the downloaded ISO integrity if you haven't yet done that: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

if it still doesn't work, then the only way is to use OBI (one button installer) or a similar program. however install should work out of the box.

when you run it from live session does only installer freeze or the whole desktop?

---

### Post by Michael_Priest on 2015-11-26
I've checked the ISO integrity and the hashes are the same.

It's the whole desktop that freezes, i can take a video if that would help

---

### Post by ajgreeny on 2015-11-26
Have you tried using the nomodeset boot option from pressing F6?

That can sometimes solve temporarily the problem of booting machines with nvidia graphics, but I do not know about the optimus situation, I'm afraid, which may mean this is another problem.

---

### Post by Michael_Priest on 2015-11-26
Do I need to press F6 whilst the machine is booting?

---

### Post by Geoffrey_Arndt on 2015-11-26
Have you tried entering your BIOS/Firmware to see if there is an option to turn off the nvidia graphics (and thus use Intel Integrated Graphics)?   If this is available as an option, the Live system may properly boot up, and the install should work.   

Additionally, what kind of prep have you done to the PC for installing Ubuntu?   Are you familiar with UEFI and what to check for, what to enable/disable?   Have you partitioned the drive for a second OS and/or formatted the space with ext4?

Finally, see this link for info on a user with the same graphics card as you, as to how he handled the Optimus conundrum.   This is worth a read . . . . if you're serious about running Linux on that machine.

[http://thelinuxrain.com/articles/the-state-of-nvidia-optimus-on-linux](http://thelinuxrain.com/articles/the-state-of-nvidia-optimus-on-linux)

Final-Finally . . . . .  unless you're a gamer, _**the best way by far **_ to run two OS's is to get a Win 7 or Win 10 iso, and run it in a Virtual Machine (Oracle's Virtual Box for example) . . . using hardware found at these vendors:

[http://linuxpreloaded.com/](http://linuxpreloaded.com/)

---

### Post by Michael_Priest on 2015-11-27
Thanks for the help, as I wasn't getting anywhere with installing it onto my machine, I took you're advice and have installed it upon a Oracle virtual machine. I'm pleased to say that has worked :)

---

### Post by Geoffrey_Arndt on 2015-11-27
Great . . . good to know it's working on your VM.   

 Later, as you get to experience Ubuntu, Unity DE, and all the good design elements of modern Linux desktops, you'll be much better prepared to research getting Linux friendly hardware versus trying to fit the square peg into the round hole.   That's something most folks have run into, including me.

Now, all my PC's are purchased online from firms like System76, Zareason, etc. . . . . takes maybe 10 minutes to fully setup . . . . so simple even a cave-man can do it.  :lolflag:

---

### Post by sudodus on 2015-11-27
Welcome to the cave!

It is a good start to buy a computer with linux. After getting some experience, we usually find that our caveman brain is not too bad after all, and we can install linux into more stubborn computers :-D

---

