---
title: "ubuntu live disc doesn't boot *with video*"
date: 2013-07-15
forum: New to Ubuntu
---

### Post by flyinghats on 2013-07-15
[FONT=tahoma]hello yes

i have a ubuntu 32 12.04 disc that works perfectly fine on a friend's computer - so it's not the disc

however fails to boot as can be seen here: [/FONT][http://www.youtube.com/watch?v=zQjEm_4GpG4](http://www.youtube.com/watch?v=zQjEm_4GpG4)[FONT=tahoma]
it fails at the 1:51 mark

i'm unsure what other infomation to provide. motherboard is on latest BIOS. i tried the 64 bit version and similar thing happens

_________________________________________

AMD Phenom 965
ASUS M5A78L-M LX V2[/FONT]
[FONT=tahoma]4 GB 1333 Mhz RM
AMD Radeon 6670[/FONT]

---

### Post by su:bhatta on 2013-07-15
OK, try this out and then inform....

On the first boot from the Ubuntu DVD you will find a **purple screen with a Man=keyboard** sign at the bottom of the screen:

1)At that screen you hit **Enter**...
it gives you a next screen where by default you will get a list of languages with English selected as default..

2)on that screen select English/or what you want---> hit enter... It will get you the Try Ubuntu/Install Ubuntu Screen

at the bottom of the screen you will see options underneath F1 F2 F3 etc.. ... **Hit F6** on that screen.. 
You will see a **pop up Box** at the bottom of the screen... use the arrow keys to go down to: "**NOMODESET**" hit enter... **a small Cross(X) **will appear beside 'nomodeset'

3)Press escape

Then choose Try/Install 
It should just boot up fine ....

BTW, All 'nomodeset' does is, it stops installing the video drivers at the beginning...
if you r using AMD, you may have to download proprietary drivers(Once installed) to get the right screen resolution n all....

---

### Post by flyinghats on 2013-07-15
thank you for the help - i had no idea the menu existed - before i was just doing the same thing

yes i tried your advice - again some erratic results. it says it will boot in low graphics mode then ends up at console

i wonder if the graphics card is the problem - i was thinking of taking the card out and trying with the motherboard graphics instead. or i could just wait half a year and try with a new version of ubuntu. i think i'll try the 64 bit version again too

here's the new video: [http://www.youtube.com/watch?v=LA96NjuxYCI](http://www.youtube.com/watch?v=LA96NjuxYCI)

edit: having discovered the enter mode at the beginning - i have found that this computer runs linux mint in compatibility mode - which is the ubuntu based operating system i wanted to work - and i think i will just have to find a graphics driver for it

---

### Post by su:bhatta on 2013-07-15
Worth giving the Motherboard graphics a try...Also, sometimes only 'nomodeset' will not do the trick & u may have to select a combination available from that F6 menu...

Also, you can try out the Ubuntu 13.04 Live Cd 
Dont install, try out a live session....
If you have to then try using the 'nomodeset' to try the live session & see how that works out....

In case you get something positive then you go forward & install.... I am sorry, i cannot help you with Mint....

---

### Post by su:bhatta on 2013-07-15
You should have a look at these pages for more details:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

[http://askubuntu.com/questions/152847/how-to-access-boot-options-12-04-live-usb](http://askubuntu.com/questions/152847/how-to-access-boot-options-12-04-live-usb)

Also, have a look around & search these forums & askubuntu.com .

---

### Post by zero2xiii on 2013-07-15
+1 for the help you have received so far.

Just a suggestion, once you reach the failsafe terminal (I assume) try running "startx" and see what errors you get, if possible please supply them. Also, the output of "dmesg" at this point will be helpful. You should have a fully functional system at this point, besides the graphics (no GUI). So you should be able to pipe any output to file and copy that file to somewhere you can access it, such a usb stick or the hard drive to attach here. If you are not sure how to do that, feel free to ask. I agree with "bhattabhishek" that it is a graphics driver issue, and also suggest giving the on board a try.

Good luck

---

