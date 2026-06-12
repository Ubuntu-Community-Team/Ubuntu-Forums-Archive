---
title: "Cant install ubuntu 10.10 on my ASUS (black screen"
date: 2011-10-09
forum: New to Ubuntu
---

### Post by sinless@ on 2011-10-09
Hi evr1, this is my first time on Ubuntu Forums..

My lap-top sys,specs:[B]ASUS Intel(R) Pentium(R) Dual CPU T3200 @ 2.00GHz
             :NVIDIA GeForce 9300M GS 512MB
Motherboard- PEGATRON CORPORATION X71SL
             :3BG ram[/B]
 
[B][U]I have previously installed ubuntu maverick on my acer aspire one, and on several other PC, but when it came to my asus it just wont install.. 
[/U][/B]
*(i have tried this from CD-boot and USB-boot I also have a 50Gb partition so it will be along side windows)*

SO i get the start screen and a list of options
[U]1 Try ubuntu without installing
2 install ubuntu
3 check disc for defects
4 Test memory
5 boot from first hard disc...[/U]

I choose the 2 option then normally i get a purple screen and the install begins..But instead i get **black screen with a white dash at the top**.. it stays like this and nothing..its just **dead** then it shuts down ( after 10 or 20 mins)...

( I know that other ASUS users hade almost the same problem when they updated from 10.04 to 10.10)

So if someone has the knowledge and is willing to help i'll appreciate it!!.Thanks... :D

---

### Post by LinuxFan999 on 2011-10-09
Does anything happen when you select "Try Ubuntu  without installing"?

---

### Post by SeijiSensei on 2011-10-09
When the installation menu appears, hit F6, choose nomodeset from the menu that appears and hit Enter.  Then hit Enter again to boot.  Does that help?

---

### Post by sinless@ on 2011-10-09
Thanks 4 the reply :) ..
 I hit enter on nomodeset but when i hit it again it doesn't do anything. JUst a little ''x'' is appearing and disappearing in front of the word.. :/

---

### Post by sinless@ on 2011-10-09
Ok I hit: F6--nomodeset--enter--Esc-- choose 2 option--- again the same... :confused: @#$%@@#$.. i dont understand why it does this... :/

But thanks for the help guys.. Any new suggestions??

---

### Post by ?#Yhf%*&amp; on 2011-10-09
Have you tried Ubuntu 11.04 instead of 10.10? 11.04 has some new drivers that might solve you problem.

---

### Post by sinless@ on 2011-10-09
Thanks 4 the reply..

''*Have you tried Ubuntu 11.04 instead of 10.10? 11.04 has some new drivers that might solve you problem.*''

Nope.. Coz i've been told that the newer releases from ubuntu arent always the best at the start, i prefer to go on with maverick and what i know of it works 100% or emm lets say 99% :neutral: or else i wouldn't be writing this thread hire :D ..

But i think its something with ASUS it self somthing with the hardware..Maybe im wrong..i dont know..

---

### Post by wildmanne39 on 2011-10-09
Hi, did you try the other options that are in the list with nomodeset one at a time to see if one of them would work? Here is a link to help.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thank you

---

### Post by mike555 on 2011-10-10
> **sinless@ said:**
> Ok I hit: F6--nomodeset--enter--Esc-- choose 2 option--- again the same... :confused: @#$%@@#$.. i dont understand why it does this... :/

But thanks for the help guys.. Any new suggestions??

   Hit f6 ,nomodeset , escape , then choose then enter

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-10
acpi=off is a MUST have for installing it on my compaq.  But I agree that you should try it with 11.04.  I haven't noticed any major bugs in either of my Laptops....  I don't use unity, though....

---

### Post by collisionystm on 2011-10-10
> **sinless@ said:**
> Thanks 4 the reply..

''*Have you tried Ubuntu 11.04 instead of 10.10? 11.04 has some new drivers that might solve you problem.*''

Nope.. Coz i've been told that the newer releases from ubuntu arent always the best at the start, i prefer to go on with maverick and what i know of it works 100% or emm lets say 99% :neutral: or else i wouldn't be writing this thread hire :D ..

But i think its something with ASUS it self somthing with the hardware..Maybe im wrong..i dont know..

Use 10.04. It is supported until 2015.

---

### Post by sinless@ on 2011-10-14
Thanks a lot guys for the help!!:).. And sorry 4 the late response
Think I'll try 11.4 or 10.4.. But i dont really know what the main difference is between them:confused:.. And still no luck with 10.10 on Asus :/ ....

---

### Post by nikhilesh on 2011-10-14
> **Corbin052198 said:**
> Have you tried Ubuntu 11.04 instead of 10.10? 11.04 has some new drivers that might solve you problem.


i tried installing 11.04 on my system, but it shows the same error; A BLACK SCREEN

HP PAVILLION DV6
ATI RADEON HD 6490M

---

### Post by WIGGMPk on 2011-10-14
Have you tried installing via the "alternative" image?



Last ditch effort you can try these flags, they worked well for me on earlier releases.

```
noapic irqpoll noirqdebug
```

---

### Post by Joelbruce on 2011-10-14
I think your Acer has an AMD processor and your Asus has an Intel, so you need a different install disk, maybe, possibly.

---

### Post by WIGGMPk on 2011-10-14
> **Joelbruce said:**
> I think your Acer has an AMD processor and your Asus has an Intel, so you need a different install disk, maybe, possibly.

The processor that was mentioned in the OP can run 64-bit code, so it really wouldn't matter if they used a 32-bit or 64-bit image.

---

### Post by wildmanne39 on 2011-10-14
Hi, did you try what I suggested in post 8?
Thank you

---

### Post by strawheart on 2011-12-11
Hello,

I hate to necro this thread, but I do have a similar machine and was able to install 11.10 with both acpi=off ***and*** nomodeset selected (simply having one or the other does not work). So I hope this helps anyone who searches for a solution in the future..

---

### Post by Georgy17 on 2013-03-10
I have the same Computer and the same problem ( 12.10 version ), anyone has a solution for this ? I tried the nomodeset already, still black screen.

---

### Post by oldos2er on 2013-03-10
Old thread closed, please start a new thread.

---

