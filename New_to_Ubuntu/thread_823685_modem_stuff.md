---
title: "modem stuff"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by Kalawala on 2008-06-09
hello again i have given up on my last modem and have now bought a usr courier business modem and though i have already bought it (it hasnt arrived yet for me to try it) it is linux capable correct? and where would i find the drivers for it anyone have any suggestions or are there any people out there that have or used this modem to give me some likes dislikes or anything with this modem (its for dialup if that matters)and for ubuntu 7.04 and also dual booted fedora

---

### Post by editrix on 2008-06-10
> **Kalawala said:**
> hello again i have given up on my last modem and have now bought a usr courier business modem and though i have already bought it (it hasnt arrived yet for me to try it) it is linux capable correct? and where would i find the drivers for it anyone have any suggestions or are there any people out there that have or used this modem to give me some likes dislikes or anything with this modem (its for dialup if that matters)and for ubuntu 7.04 and also dual booted fedora

I haven't seen your previous posts but have you tried 
[http://www.linmodems.org/](http://www.linmodems.org/)

Then there's [http://wiki.linuxquestions.org/wiki/Set_up_modem](http://wiki.linuxquestions.org/wiki/Set_up_modem) and Ubuntu's own DialUp HowTo.

Some external modems are winmodems only--you should have checked before you bought.

I know nothing about usb modems so I can't help there.

One very good way to search for Linux info is Google Linux (in my sig).

---

### Post by alexandremrj on 2008-06-10
USB modems are a bit tricky but you can search for drivers.

In this thread there is a little howto of configuring an usb modem (Anydata CDMA USB modem) using gnome-ppp, although there are no drivers at all.
 [http://ubuntuforums.org/showthread.php?t=763122](http://ubuntuforums.org/showthread.php?t=763122)

---

### Post by Kalawala on 2008-06-10
um well its a external r2 232 serial cable connection not a usb modem which i have never worked with an external modem before but when i emailed the company they told me this 

"After reading your email we understand that you would like to confirm if the 3CP3453 supports Linux since you are unable to find the drivers for it. In this case we kindly inform you that there are no drivers for Linux, since beyond full support of the Windows Operating Systems, the Courier 56K Business Modem will function in any operating system that supports an RS-232 COM port, such as DOS, Linux, or UNIX. Standard COM port settings are: 
* Bits per second: 115,200
* Data bits: 8
* Parity: none
* Stop bits: 1
* Flow control: hardware 
Assign your terminal application to use the COM port to which you connect the modem's serial cable." um so im guessing that means it is but i dont exactly know what do to with that information

---

### Post by Kalawala on 2008-06-11
anyone have any ideas what to do with that info?

---

### Post by alexandremrj on 2008-06-12
This is a shot in the dark, never tried it but you could still use gnome-ppp

In device you press autodetect and see what comes up. In type you place ISDN modem. Perhaps this will,work, can't promise.

---

### Post by niteshifter on 2008-06-12
Hi,

I went to USR's web page for the USR 3CP3453 modem and .... I think you'll have no problems with it working. It's pretty much just a plain V.9x analog modem. You'll need to install gnome-ppp (which should also pull in a program named wvdial).

I'm pretty sure I've even installed this exact modem before on GNU/Linux, using wvdial - it looked familar. Just don't really remember it, which is a good thing as it's the bad experiences that stick. It's also been awhile, that modem been around for years.

---

### Post by eotakos on 2008-06-14
xm... i have a more simple question than the first one. actually i've never seen a dialup modem work under ubuntu and even if my laptop's modem is compatible i wouldn't know how to make it operate. under system->administration-> hardware drivers i have enabled a proprietary driver "software modem", but even so i don't seem to manage making it dial from the network settings gui.

any suggestions? at this point even if i searched under linmodems.org i wouldn't know what i'd be looking for - that's why i'm posting here. I think i have to understand how the ubuntu side-of-things work first...

thanks for your time... :-)

---

### Post by cariboo on 2008-06-14
Your modem should be real easy to set up. just find what serial port it is using and use Kppp to dial.

Make sure you serial ports are enabled in you bios, in most cases you will only have two choices so if one doesn't work the other should.

Here is a howto:

[http://baheyeldin.com/linux/how-to-setup-a-modem-with-linux.html](http://baheyeldin.com/linux/how-to-setup-a-modem-with-linux.html)

Jim

---

### Post by eotakos on 2008-06-15
thanks for the post - i seem to be heading the right way since my laptop modem appears to be pci (internal) and not winmodem -

cheers!!

---

### Post by Kalawala on 2008-06-22
alright i seem to be able to have my modem connect to the internet but it doesnt stay connected for longer than 9 - 10 minutes it just disconnects any clue whats happening all i did was install gnome-ppp and put in my settings after plugging in the modem is there more for me to do

---

