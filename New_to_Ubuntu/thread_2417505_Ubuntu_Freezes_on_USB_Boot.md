---
title: "Ubuntu Freezes on USB Boot"
date: 2019-04-23
forum: New to Ubuntu
---

### Post by jody27 on 2019-04-23
Hi there everyone.

So I am new to Linux and have been having this issue for a while.
I am trying to get some simulations finished and windows keeps crashing so I need to get my Linux up an running.

So the Problem I am having is that when I say try, the logo comes up and dose its thing, I then see the mouse and sometimes I will see the Desktop for a second and then the screen will go black and my system locks up.
I know its locking up as pressing num lock and caps lock dose not allow the LEDs to turn on or off.


[B][I]Things I have Tried
[/I][/B]- I have changed to all different USB Ports on my system, even the ones at the top for the Keyboard and Mouse (I got the desktop to display for a Split second using those)

- I also Tried different Distros (Mint and Fedora) but I had the same issue.

- I tried the USB on my Laptop and it works Perfectly.

- I have also tried unplugging all drives and Peripherals to no Avail.

[B][I]System Specs
[/I][/B]Motherboard - MSI x399 Gaming Pro Carbon / AC
CPU - AMD Threadripper 2970wx
RAM - 128GB Corsair Vengeance LP
GPU - AMD R9 390 

Windows boots fine but I cannot get Linux to Boot so I can install it.
Any help would be Greatly Appreciated.

Thanks in advance.

---

### Post by oldrocker99 on 2019-04-24
It may be a problem with the .iso file. Download another .iso, and the download page will show how to use SHA256 to verify the download. Then, try it again. 

It is also possible that the USB is faulty. 

It is also possible that you simply copied the .iso to the USB instead of burning it. Here's how to burn an image in Windows:
[https://www.laptopmag.com/articles/mount-burn-iso-files-windows](https://www.laptopmag.com/articles/mount-burn-iso-files-windows).

Good luck!

---

### Post by jody27 on 2019-04-27
Hi there @oldrocker99

I thought so to, but the USB Works fine with my laptop and my other system.
I used Rufus to Burn it to the USB, I am not sure if there are others ?

I went into the Bios and made sure the Install from USB stuff was on as well.

---

### Post by jody27 on 2019-04-27
Hi there again.

So I did a recording of what happens and I also did a Disk check using Ubuntu and got the Results below.
I am not sure what is causing this.


Disk Check
[https://cdn.discordapp.com/attachments/288980729784827904/571685126581518336/IMG_20190427_150108.jpg](https://cdn.discordapp.com/attachments/288980729784827904/571685126581518336/IMG_20190427_150108.jpg)


The Issue I am having.
[https://cdn.discordapp.com/attachments/288980729784827904/571692709736218634/Ubuntu_Error.mp4](https://cdn.discordapp.com/attachments/288980729784827904/571692709736218634/Ubuntu_Error.mp4)

---

### Post by jody27 on 2019-05-05
Hi there everyone.
I found the Problem.

It was my GPU, the R9 390. I got an RX 570 and a GTX 1060 from a friend to try and both those cards worked.
I am not sure if its the way the Card performs or what but that was my issue.

---

### Post by Rubi1200 on 2019-05-05
Glad you got it sorted out.

Please mark this thread as Solved using the Thread Tools at the top of the first post so others looking for a solution can also find it.

Thanks.

---

