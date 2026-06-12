---
title: "First install - text hard to read"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by Sharptongue on 2008-11-13
I have read a number of discussions warning that running any Linux distro will not be as straightforward as installing Windows, and my first ever Linux installation - Ubuntu 8.04 - has proven to be so.

The procedure seems to have worked, except that all the text, from the beginning of the installation, appears as pixellated multicolours. It is like a squarish version of those blot pictures used to grade colourblindness.

I am 100% unimpressed.

So, before I give up on Ubuntu and try another Linux flavour, does any one want to try and convince me that it is worth trying again ?

Please bear in mind that I am still on dialup, so downloading any other version over the net is not an option. I obtained the CD ISO image from a CD on a recent issue of APC magazine.

---

### Post by philinux on 2008-11-13
Being on dial up is going to be a pain when it comes to installing drivers, other apps you may need and security updates.

The graphics card driver would be the one that could cure your display problems. What are you system specs.

---

### Post by Axos on 2008-11-13
Yup, that's what it looked like on my old laptop until I installed the proprietary video device driver using System -> Administration -> Hardware Drivers (which will download and install the driver).

On my newer laptop the video looked great right out of the box though installing the proprietary driver enabled 3D support.

---

### Post by Sharptongue on 2008-11-16
Be patient with me, as I'm new to this.

> **Axos said:**
> Yup, that's what it looked like on my old laptop until I installed the proprietary video device driver using System -> Administration -> Hardware Drivers (which will download and install the driver).

System -> Admin -> H Drivers
from inside Ubuntu, right ?

So you're saying that, unless I can start an internet connection, it won't work ?
This is not good news, as I have no idea how to configure a dialup connection. And, though this is a more minor issue, I would also need to install the internal modem - an irritation, though it can be done.

And having all the text in pixellated squares makes doing anything unusual inside Ubuntu a real pain.

In short, is there a way I can find out what driver I need, then download it separately (i.e. not from within Ubuntu), then add it to the Ubuntu install ?

---

### Post by Peter09 on 2008-11-16
Yes,
Can you post the output of the terminal command to confirm the driver that you are using.
```
lshw -C display
```

You/or some one here should be able to find the package of that driver on the internet. You then download it on another machine and transfer it via a usb stick to your machine where you can install it.

---

### Post by Sharptongue on 2008-11-17
> **Peter09 said:**
> Yes,
Can you post the output of the terminal command to confirm the driver that you are using.
```
lshw -C display
```


Terminal Command ?
I tried this in DOS and it doesn't work.
Do you mean to execute the command from some indeterminate location inside the ubuntu install (which is barely readable) ?

> **Peter09 said:**
> 
You/or some one here should be able to find the package of that driver on the internet. You then download it on another machine and transfer it via a usb stick to your machine where you can install it.

Okay, I await someone here to find this for me :|

Are there recorded instances of newbies installing Ubuntu on new PCs with no such annoyances ?

---

### Post by mjwhitfield on 2008-11-17
> **Sharptongue said:**
> Are there recorded instances of newbies installing Ubuntu on new PCs with no such annoyances ?yes, my 80 year old Gran.

Any modern O/S is going to be a pain to install if you're unable to download anything.

Why have you moved away from Windows?

---

### Post by The Cog on 2008-11-17
> Are there recorded instances of newbies installing Ubuntu on new PCs with no such annoyances ?
Sarcasm like that is more likely to annoy people and prevent them from trying to help that it is likely to encourage them to help.

Typing Ctrl-Alt-F1 will get you a text prompt that should be readable. Log in and try the command there. Use Ctrl-Alt-F7 to get back to the GUI afterwards.

P.S.
The GUI terminal is under the menus Applications->Accessories->Terminal if you can read that.

---

### Post by Sharptongue on 2008-11-17
> **The Cog said:**
> Sarcasm like that is more likely to annoy people and prevent them from trying to help that it is likely to encourage them to help.


What sarcasm ?
I'm genuinely puzzled.
Various flavours of Linux have been getting much greater exposure, at least in computer mags and in some IT classes, over the past 12 months or so. A lot of glowing reviews have been written by evangelists, keen to recruit new converts to their favoured flavour. But none of them mention the apparently forseeable installation issues, such as this one.

To find critical views, other than the extreme "avoid at all costs and stick with Windows no matter what", one has to do targetted web searches.

> **The Cog said:**
> 
Typing Ctrl-Alt-F1 will get you a text prompt that should be readable. Log in and try the command there. Use Ctrl-Alt-F7 to get back to the GUI afterwards.

P.S.
The GUI terminal is under the menus Applications->Accessories->Terminal if you can read that.

Cheers. I'll try it.

---

### Post by Sharptongue on 2008-11-22
The Cog : "Typing Ctrl-Alt-F1 will get you a text prompt that should be readable. Log in and try the command there. Use Ctrl-Alt-F7 to get back to the GUI afterwards.

P.S.
The GUI terminal is under the menus Applications->Accessories->Terminal if you can read that."

Okay, tried it, and found a display *similar* to this one :

display UNCLAIMED
description: VGA compatible controller
product: 86c968 [Vision 968 VRAM] rev 0
vendor: S3 Inc
physical id: 10
width: 32bits
clock: 33MHz
capabilities: vga controller
configuration: latency=0

.... which lead me to this thread ...
[http://ubuntuforums.org/archive/index.php/t-907042.html](http://ubuntuforums.org/archive/index.php/t-907042.html)

... and the feel of the discussion there seems to hold the answer, which is that Ubunutu probably won't run well enough on my old machine, and I would be better to try a more minimal flavour. Looks like my excursion into Ubunutu is at an end, at least until I get a more powerful PC for Linux experimentation.

Any comments ?

---

### Post by chrisod on 2008-11-22
It's kind of hard to comment on the suitability of your machine without knowing the specifications of the machine. Can you post them?

---

### Post by Sharptongue on 2008-11-23
> **chrisod said:**
> It's kind of hard to comment on the suitability of your machine without knowing the specifications of the machine. Can you post them?

Okay.
Now confirmed, the display from :
lshw -C display

is -

display UNCLAIMED
description: VGA compatible controller
product: 86c968 [Vision 968 VRAM] rev 0
vendor: S3 Inc
physical id: b
width: 32bits
clock: 33MHz
bus info: pci@0000:00:0b:0
version: 00
capabilities: vga controller
configuration: latency=0

(Note that I have typed this from notes. I have not yet found a way to save any info from the Ubuntu machine)

and it is running on
Intel Celeron 533 MHz
192 Mb RAM

Do you need any more info ?

Also, following up from this thread [http://ubuntuforums.org/archive/index.php/t-907042.html](http://ubuntuforums.org/archive/index.php/t-907042.html)
.... If Ubuntu 8.04 is too demanding for my old PC, would it help to try an older version of Ubuntu, or simply better to try a lighter flavour ?

---

### Post by chrisod on 2008-11-23
Ununtu needs 256K RAM minimum to run, 384K to install from the Live CD. You are going to need a distribution tuned for older machines, something like Puppy Linux or Damn Small Linux. I'm not sure about Xbuntu with that box, maybe somebody else can weigh in on that.

---

### Post by Sharptongue on 2008-11-24
> **chrisod said:**
> Ununtu needs 256K RAM minimum to run, 384K to install from the Live CD. You are going to need a distribution tuned for older machines, something like Puppy Linux or Damn Small Linux. I'm not sure about Xbuntu with that box, maybe somebody else can weigh in on that.

384 K ? Do you mean slowish broadband ?

The only flavour that runs out of the box so far is Knoppix 5.0.1

Does this mean that I could expext similar problems with these others I have burnt -
Centos 5.1
Mandriva (3 cds)
Mint 4.0
gOS

---

### Post by CatKiller on 2008-11-24
> **Sharptongue said:**
> and it is running on
Intel Celeron 533 MHz
192 Mb RAM

I've run Xubuntu on a machine with similar specifications. It's... alright. Not blazingly fast, but certainly usable.

The live cd of the full Ubuntu will struggle - if it runs at all - although it might be possible to install it using the Alternate cd for a text-mode installation. Once it's installed, I shouldn't imagine that it will be that fast.

There are Linux distributions that are directed towards older computers. Puppy and DSL are the usual recommendations, although there are others. The really minimal ones are generally less user-friendly, since all of the helpers and graphical tools and such take up more resources.

If you can squeeze any more RAM into that machine, then it would probably help enormously. I don't know how well supported the S3 graphics are these days.

Dial-up Internet access can be a bit of a pain if you're using a WinModem rather than a real modem. You might find it easiest, if your machine has the capabilities, to borrow a network connection till you've got it set up (and to find out how to set it up) and then use your dial-up connection when it's all up and running.

---

### Post by CatKiller on 2008-11-24
> **Sharptongue said:**
> (Note that I have typed this from notes. I have not yet found a way to save any info from the Ubuntu machine)

You can redirect output from a command with **>**. So with that particular command, you could run

```
lshw -C display > display.txt
``` which would put the output to a text file in your Home directory. Getting that text file to another computer is left as an exercise for the reader, since I don't know what sort of thing you have available.

---

### Post by chrisod on 2008-11-24
I meant MB as in memory when I typed K as in bandwidth above. My point holds though. You need to focus on the Linux distros that are tuned for older machines. Even you get Ubuntu (or Debian, Centos, or Fedora) running it's not going to run well on 192 MB of RAM).  I don't think Mandriva will run on your box either. gOS and Mint I'm not sure about. If I were you I would check the web and confirm the minimum system requirements before I spent anymore time trying to install operating systems.

---

### Post by halitech on 2008-11-24
I can speak from experience that Debian with XFCE4 will run fine on that machine (check my specs) although installing is usually done easiest over the net. And I agree with CatKiller, borrowing a highspeed connection might be easiest until you get things configured at least.

---

### Post by Sharptongue on 2008-11-26
Thanks for the input, guys.

I'm having a go at Zenwalk 4.8, which is supposed to run on min 128 Meg, but haven't been able to get it to start yet. Have posted similar query on Zenwalk forum.

What got me onto this track in the first place was a highly skilled Unix/Linux lecturer whose classes I briefly attended earlier this year (long story). This chap made a theatrical gesture of bragging about an old PC which he'd built as a personal firewall using either Linux or Unix (he didn't quite specify). The PC was a 486, and was still running and doing a better job than a current Windows server firewall.

While I'm not expecting to go this far back into PC history, it is the light end I'm looking at. So upgrading the RAM is not an option, at least for the PC I'm currently using as a Linux sandbox.

If Puppy / DSL prove not too user-friendly, as some web sources warn, then my fallback position is to plug on with Knoppix.

---

### Post by chrisod on 2008-11-26
An old 486 is fine as a firewall because he doesn't have a graphical user interface installed. No desktop, no web browser, just a command line. Ubuntu would probably be fine that way too, but you'd probably have to roll your own version of Ubuntu minus everything related to X server and the GUI, unless somebody has already done that.

---

### Post by CatKiller on 2008-11-26
> **chrisod said:**
> Ubuntu would probably be fine that way too, but you'd probably have to roll your own version of Ubuntu minus everything related to X server and the GUI, unless somebody has already done that.

That would probably be **ubuntu-minimal**. No GUI, just a handful of command-line tools. You can then install a light window manager on top.

There's also Fluxbuntu, which is this approach but with FluxBox installed as a window manager.

I haven't tried either, so I can't really say how applicable they'd be to the OP.

As I mentioned earlier, not having the overhead of helper applications and the like can give a much steeper learning curve. It's not insurmountable, though.

---

