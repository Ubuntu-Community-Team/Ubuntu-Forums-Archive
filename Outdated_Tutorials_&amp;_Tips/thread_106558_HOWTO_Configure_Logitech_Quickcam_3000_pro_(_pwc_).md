---
title: "HOWTO: Configure Logitech Quickcam 3000 pro ( pwc )"
date: 2005-12-20
forum: Outdated Tutorials &amp; Tips
---

### Post by Pekkalainen on 2005-12-20
Hello!

It is time for my first howto and it will teach you how to configure your Logitech Quickcam 3000 pro webcam or quite possibly any webcam using the Philips pwc module. No one on this forum was able to help me so I had to figure it out for myself, and now I share my success with you in an as beginner-friendly way as possible. After all, I am a beginner myself :)

First of all, according to the info I dug up, the pwc module that comes with Ubuntu by default is old. Get a newer one here: [http://www.saillard.org/linux/pwc/](http://www.saillard.org/linux/pwc/)

You find installation instructions here: [http://www.saillard.org/linux/pwc/INSTALL.en](http://www.saillard.org/linux/pwc/INSTALL.en)
Follow the "Kernel 2.6 + module" instructions

Now you have your new pwc module installed and life is good... or is it? When I fired up my cam the image was extremely dark, the only thing I could see was my 60 watt ceiling light and it was gray. So if you are having the same problem as me, here is the solution:

To configure your cam download this nifty little program called setpwc: [http://www.lennartsson.se/debian/setpwc_0.9-1_i386.deb](http://www.lennartsson.se/debian/setpwc_0.9-1_i386.deb) ;)

(for further info about it see [http://www.vanheusden.com/setpwc/](http://www.vanheusden.com/setpwc/) )

Fire up a terminal and install the deb by typing:

sudo dpkg -i setpwc_0.9-1_i386.deb

When it is installed type:
setpwc -h
to get instructions on how to use it. 

In a perfect world this would be it. Unfortunatly I still had minor problems with brightness and a few other settings. I found the solution here:

[http://www.vanheusden.com/dov4l/](http://www.vanheusden.com/dov4l/)

Download the .tgz file and unpack it with the command:

tar xvf dov4l-0.8.tgz

Im not exactly sure about the "xvf" option, maybe it was "xvjf" or plain "xv", you have to experiment for now until someone can correct me on usage of the tar command. I will correct this step later if the one I wrote was wrong. Sorry for my poor memory ;)

Anywho... when the .tgz is unpacked you have a folder called dov4l-0.8. Browse to it by typing:

cd dov4l-0.8

Then type:

make

and then:

sudo make install

Now the program should be installed. Find out how it works by typing:

dov4l -h

Now you have 2 programs to configure your pwc based cam with. Fiddle around with them and hopefully you will have better image quality than any Windows user out there, I sure have ;)

I configured it by messing with either setpwc or dov4l and then trying it out in Kopete. One command, and then seeing what it did by opening a program, it can be a lengthy process but you get there sooner or later :cool:

That concludes my first howto, if you have any questions och suggestions just drop them here. Sorry for my poor english, I am swedish and I have only used english for about 16 years ;)

---

### Post by mirkov on 2006-01-21
I followed the guide and now have working driver and not-so-nice picture.
Could You please post Your setpwc and dov4l lines (parameters that work for your setup)?
thx

---

### Post by bradmo on 2006-06-19
Thanks a lot for this how-to.  It worked like a charm!

---

### Post by mip on 2006-06-27
Does this apply to Dapper?

How can I find out what version of the pwc module I have installed?

---

### Post by pumpkin_escobar on 2006-10-21
worked like a charm for me using kubuntu dapper 2.6.15-27-686!

used the 10.0.12-rc1 version of the driver

used 'setpwc_1.1-1_i386.deb'

much better image quality than in windows

first i restored the factory settings for the cam:

setpwc -x

then the biggest change was the framerate... it was stuck at 10 in windows and once i changed it to 30 using setpwc it was like a had a brand new cam:

setpwc -f 30

i also found that setting the whitebalance to 'outdoor' worked best in my lighting... go figure:

setpwc -w outdoor

thx much for the howto!

---

### Post by komputes on 2009-10-08
I tried pumpkin_escobar's commands/settings but I was not able to get the last two to work:

komputes@karmic:~$ setpwc -x                                
setpwc v1.2, (C) 2003-2006 by [email]folkert@vanheusden.com[/email]                      
komputes@karmic:~$ setpwc -f 30                             
setpwc v1.2, (C) 2003-2006 by [email]folkert@vanheusden.com[/email]                      
Error while doing ioctl VIDIOCSWIN: Invalid argument                      
komputes@karmic:~$ setpwc -w outdoor                        
setpwc v1.2, (C) 2003-2006 by [email]folkert@vanheusden.com[/email]                      
Error while doing ioctl VIDIOCPWCGAWB: Connection timed out

Are there any efforts to make a graphical application to modify these settings?

---

