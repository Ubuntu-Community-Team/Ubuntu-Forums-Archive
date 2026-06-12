---
title: "NEWBY Questions"
date: 2012-02-14
forum: New to Ubuntu
---

### Post by Larrytoo on 2012-02-14
Oh great Penguin,
 
  I come to you seeking knowledge and help with UMBUTU 10.xx on a Gateway 503GR running a pent-4-530 processor with the intel 915 chipset.  The machine has a 500GB SATA drive (Formatted, no system), 1GB dual channel RAM, dual layer DVD+-/RW, and several USB ports.
 
 This is my first use of LINUX though about 20 years ago I was a user of UNIX.
 
While attempting to load from a thumbdrive (stick) to a freshly formatted HD with no system, I get to the "Who Are You" page with all fields entered and either a green check or green comment on each except for "user Name".  The prompt at them bottom says "Ready when You are" but it will not allow me to go "Forward" ie., that tile will not highlight.
 
Where do I look for my problem?       :confused:
 
Oh, this machine is not on the internet (no signal in my area) which leads to my next question:  Can I download drivers to my stick on an internet machine and then load them on the Linux system?
 
Where would I go for drivers after I get the basic load to work?
 
Larry

---

### Post by openation1 on 2012-02-14
well at the bottom you can see the bar filling up with applications right? at the top there is a box. click on the box and tell the system the city where you live. that will help setup the time too. click forward once you are done. it will take you to another page and do the same. follow it until it is done.

---

### Post by Larrytoo on 2012-02-14
Well, I think I did that. Since I'm in the same timezone as NewYork, I just left it there though the time seemed odd (it was 9:47 here yet the example showed 4:47 mebbyso because I'm not on internet). clicked "forward" and filled in next screen. etc., untill reaching the Who Are You screen that asks for machine name, user name, password, etc. I entered all and got a green check next to each entry but no check on username even though I entered one, passwd was "good" and I indicated automatic log and no encription. The prompt at the bottom of the screen which had be saying "loading files" changed to "Ready when You are" BUT, only the "BACK" tile iluminated and I could not, by use of arrows or the mouse, get the forward button to work. That is where the system is now (back home as I'm at an office machine now).
 
Larry

---

### Post by josephmills on 2012-02-14
Is your username starting with a capital letter ? if so change that. what about when you set up the HOST name was that in caps? If so change it. so no cops at the start of uname and no caps at the start of HOST name try again(it is the way that /etc/shadow and /etc/group sees things just like in older unix systems )
Hope that this helps

---

### Post by Larrytoo on 2012-02-14
Thanks,  I'll check those things.  Sure brings back some old memories!
 
Larry

---

### Post by gordintoronto on 2012-02-14
> **Larrytoo said:**
> Oh, this machine is not on the internet (no signal in my area) which leads to my next question:  Can I download drivers to my stick on an internet machine and then load them on the Linux system?
 
Where would I go for drivers after I get the basic load to work?
 
Larry

Most of what you know about drivers no longer applies. However, it's one area where it's a lot easier if you have an Internet connection.

Most drivers come along with the kernel. Let's talk about four kinds of drivers: video adapter, WiFi adapter, printer and webcam.

For the first two, people normally run a program called "Additional Drivers," which will tell them if there are video or WiFi drivers to install. I have no experience with an i915 video adapter; it might only work as a generic VGA.

WiFi is a special case: many adapters are supported "out of the box," no need to install a driver. Others have a driver two clicks away in Additional Drivers (assuming an Ethernet connection to the Internet,) some need the Windows driver under something called NDISWrapper, and some will never work.

When I install any recent version of Linux, I turn on my network printer and run a program called "printers," and click on "add." A couple of clicks later, it scurries off to the Internet and installs the appropriate driver, and the printer works. Barring that approach, you go to the manufacturer's web site and collect the Linux driver, along with other required software. PITA.

In my experience, webcams either work or they don't. My specialty is cheap webcams purchased in China, and they have all worked for me "out of the box," except with Ubuntu 10.10, which required an unusual incantation.

Oddly, some of the nastiest driver issues are with hardware which was on the drawing board last week. Even something as simple as an Ethernet adapter might not be supported until it has been around for a few months, and all you can do is wait for it. (Or plug in an older Ethernet adapter in the short term; they're cheap.)

Do you have any other devices which might require a driver?

---

### Post by sadaruwan12 on 2012-02-14
Your user name have to be all simple and you have to re-enter your pass word twise after that you'll be able to continue. There's a issue when you fnish the last step thats why it's not letting you to continue.


This [Guide]("http://techhamlet.com/2010/05/how-to-install-ubuntu-10-04/") will help your get more knwoledge on the subject

---

### Post by mastablasta on 2012-02-15
> **gordintoronto said:**
> 
For the first two, people normally run a program called "Additional Drivers," which will tell them if there are video or WiFi drivers to install. I have no experience with an i915 video adapter; it might only work as a generic VGA.


they wrok though for better 3D performance the upgraded version might be needed.

---

### Post by wildmanne39 on 2012-02-15
Hi, > intel 915 chipsetis supported in the kernel you do not need to download a driver for that but since yours is so old it may not be supported in 11.04 and above any more, if you post the output of:
```
lspci | grep VGA
```
from the usb stick if you can not get it to install we might can tell you more.

I recommend running the live version of ubuntu first anyway to make sure your computer will run ubuntu.

What version of ubuntu are you trying to install?
Thanks

---

### Post by Larrytoo on 2012-02-17
Thanks,
 
   That was the problem, I was using upper case in my username.
 
Larry

---

### Post by Larrytoo on 2012-02-17
Ah,
 
  So what you are telling me is that when I plug in my HP Laserjet 2P+ or my HP Photosmart 2710, they should work,  GREAT!
 
  Now I need to solder a USB connector to my WiFi decoder ("I trapped" it in a closing door) to fix it, load the desktop system in the back of my truck, and find a hotspot to get the updates and possibly drivers.
 
  Another question, Is there a translator application that would allow me to run Windows software under Ubuntu?  Things like "Flight Simulator" or TurboTax?
 
Larry

---

### Post by Larrytoo on 2012-02-17
I was loading ver 10.10 so about 14 months old.  What would be the newest ver that would support my chipset?
 
Larry

---

### Post by Larrytoo on 2012-02-17
The games seem to work so I would guess the chipset is supported.  So do the applications I've tried.
 
Larry

---

### Post by gordintoronto on 2012-02-17
> **Larrytoo said:**
> Ah,
 
  So what you are telling me is that when I plug in my HP Laserjet 2P+ or my HP Photosmart 2710, they should work,  GREAT!
 
  Now I need to solder a USB connector to my WiFi decoder ("I trapped" it in a closing door) to fix it, load the desktop system in the back of my truck, and find a hotspot to get the updates and possibly drivers.
 
  Another question, Is there a translator application that would allow me to run Windows software under Ubuntu?  Things like "Flight Simulator" or TurboTax?
 
Larry

If you take the computer somewhere to get drivers, take your printers too.

There is something called WINE, which lets you run some Windows programs. There is a web site which will tell you what to expect. Off the top of my head, I think Flight Simulator is unlikely, but there's a good chance TurboTax will work. Don't ask about it here, use Google to find out for sure.

---

### Post by njrob on 2012-02-17
Hi, I'm trying to get an OpenGL support driver for my ATI Mobility Radeon X600 graphics card in Ubuntu 11.10

I need the OpenGL support for a game I'm trying to run in Wine 1.3.37 called DDO (Dungeons & Dragons Online).  Wine itself runs DDO's surrogate launcher known as pylotro.

I was told on the Wine forum on a thread about DDO to look for additional help specific to a relevant driver providing the OpenGL support that I need.  Any assistance or direction to a relevant thread/forum would be much appreciated.

---

