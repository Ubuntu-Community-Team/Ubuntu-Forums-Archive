---
title: "Microsoft Life Cam"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by Vendettaseve on 2008-10-19
Hey everyone



Any way to get a microsoft lifecam running on Ubuntu? Im just curious since I have one left over from my Windows days and will be giving it away shortly if theres no hope for it on my machine, Id just like to make sure Im not giving away something I could also use.


Iv checked around for drivers etc, cannot find any, is there a generic one for it? etc

Much appriciated

V

---

### Post by anaconda on 2008-10-19
atleast
Microsoft LifeCam VX-1000
"works" out of the box, but picture quality is MUCH worse than in windows..
and the colours arent that good either..in different programss it works differently..

in cheese
the colour is black/red
in camorama it is black/blue
and in skype it is black/brown (or yellow)  (almost wery good)

I haven't searched drivers for that yet, since it kind of "works" straight away..

---

### Post by Vendettaseve on 2008-10-19
I believe I have Lifecam 1.4, at least thats what the install CD says.

---

### Post by iPeppers on 2008-11-18
> **anaconda said:**
> atleast
Microsoft LifeCam VX-1000
"works" out of the box, but picture quality is MUCH worse than in windows..
and the colours arent that good either..in different programss it works differently..

in cheese
the colour is black/red
in camorama it is black/blue
and in skype it is black/brown (or yellow)  (almost wery good)

I haven't searched drivers for that yet, since it kind of "works" straight away..


Really?  Because I have a LifeCam VX-1000 plugged in right now, the light is green, and I know it works in Windows XP, because it's the only reason that I still have to duel boot into windows.... but it doesn't work in ubuntu 8.10 for me. 

lsusb gives me:
Bus 002 Device 009: ID 045e:00f7 Microsoft Corp. LifeCam VX-1000.

But Cheese, Camorama, aMSN, and Skype all tell me that they can't find a webcam.  What do I do?

---

### Post by jesterthejedi on 2008-12-24
Working after 6 months of waiting and searching forums. 

Do this:
Download driver:
[http://linuxtv.org/hg/~jfrancois/gspca/](http://linuxtv.org/hg/~jfrancois/gspca/)
grab the .bz2 file
extract and change directory
in terminal type "make" no quotes take about 5 mins
then type "sudo make install"
reboot

tested working on Intrepid With Cheese, Ekiga, Skype, GyachE, Xawtv

COLORS are fine! no more green/blue Hardy mess.
not working in Camorama, Camstream, errors in gqcam

installed xawtv, luvcview, and removed camserv.

I am so happy that I should pinch myself. I bought this webcam in June for my birthday and it was always a pain in the butt to solve. Success at last!

---

### Post by kseunder84 on 2009-06-15
I followed the directions step by step jesterthejedi put up, cheese detects my webcam but all that comes up is solid green, anyone know how I can fix this?

---

### Post by jesterthejedi on 2009-06-15
Check my other posts, you need to try the LD preload trick for cheese.

---

### Post by stanca on 2009-10-07
Now this one:
```
sudo apt-get install subversion build-essential linux-headers-$(uname -r) && wget http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2 && tar xf tip.tar.bz2 && cd gspca-* && make && sudo make install && sudo depmod -ae $(uname -r)
``` ;):P

---

### Post by raxie on 2010-08-01
Help!! I'm new to this game but keen to learn. I have the LifeCam 1.4 and tried to download
the jfrancois/gspca/archive/tip.tar.bz2 as suggested and get the following terminal response:-

--2010-08-01 17:38:29-- [http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2]("http://linuxtv.org/hg/%7Ejfrancois/gspca/archive/tip.tar.bz2")
Resolving linuxtv.org... 130.149.80.248
Connecting to linuxtv.org|130.149.80.248|:80... connected
HTTP request sent, awaiting response... 404 Not Found
2010-08-01 17:38:30 ERROR 404: Not Found

Does this mean that the file(?) has been removed? If so can anyone supply it to me please.

Thanks Raxie

---

### Post by no2498 on 2010-08-01
raxie
look in sound & video for cheese webcam booth

try the cam in cheese

---

### Post by raxie on 2010-08-02
Thank you. A great help.

---

### Post by raxie on 2010-08-03
I'm trying to get the webcam lifeCam 1.4 working with Skype and failing miserably. I tried following the instructions off another board which required me to go System>Preferences>Main Menu>Skype>properties and change the Command. It didn't work, but like an idiot, I didn't record the previous command. Can somebody please tell me what it should be? I am trying but its difficult for a pensioner like me to get his head around. Great when all is working well-bit like going to the dentists for a checkup.[IMG]file:///home/john/Desktop/Screenshot-Launcher%20Properties.png[/IMG]

---

### Post by no2498 on 2010-08-05
sounds like you need to get rid of skype but do not just uninstall it
make a new post asking for how to get rid of all of its folders
tell them you changed something in its folders or what ever it was

---

