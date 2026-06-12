---
title: "Ubuntu 12.04 Canon MP560 Printer not found"
date: 2014-05-03
forum: New to Ubuntu
---

### Post by Charlie_Jones on 2014-05-03
I am an absolute beginner with Linux.  Leaving Windows XP, I installed Ubuntu 12.04 LTS using WUBI.  All went well and my Canon printer, MP560 was identified and worked flawlessly.  Two days ago I started getting "unable to locate printer" error.  I can turn the printer off and then back on and it prints, but this is only for the print job in queue.  The next time I attempt printing, I get the unable to locate printer message.

Knowing nothing about Ubuntu, I seek assistance in rectifying this problem.

Many thanks for any assistance.

---

### Post by pdc on 2014-05-03
Hi Charlie; welcome to Ubuntu; we hope you enjoy it; in many cities are the world, there are LUGs (Linux User Groups) and if one meets nearby to you, it is an opportunity to take a laptop along to learn more

______________________________________________________________________________________________

I wonder whether you have the 32bit version of ubuntu installed; in the way you sometimes have to check your tyre pressure in the car, or check the oil level, in ubuntu it can be helpful to lift the bonnet occasionally;

in the search function called DASH ......... have you found it.............if you type (or copy and paste) ..............> [COLOR="#FF0000"]uname -m[/COLOR]

let us know what it says

.....the reason I ask is Canon make drivers; and perhaps the Canon driver might help the situation; if you subscribe to a thread; (click the options a few below this when you reply (advanced reply) .................it helps keep in touch)

---

### Post by Charlie_Jones on 2014-05-05
Thank you very much for responding.

When I copied and pasted uname -m in the search box of Dash, it returned "sorry, there is nothing that matches your search."

However, I went to System Settings/Details and found "OS type: 64 bit".

It dumfounds me that the printer worked flawlessly for a period of time then suddenly began experiencing the problem described.

I shall sincerely appreciate your further guidance.

---

### Post by Vladlenin5000 on 2014-05-05
The first problem you have is not having a proper installation - WUBI has been abandoned and for very good reasons - although I'm not sure if it has to do with your problem. If I were to guess I would say yes, it has a lot to do with the issue you're experiencing because what WUBI did was install Ubuntu inside Windows. Really not better than a virtual machine and potentially worse in what concerns peripherals.

The command you were given is to be typed (or copy-pasted) in a terminal, not the dash. You can either search terminal in dash and open it or just do CTRL+ALT+T.

---

### Post by pdc on 2014-05-05
my apologies Charlie: VladLenin is absolutely right: I was aiming to head you towards a terminal; ..............means well.................tries hard.......................

I suspect Vlad is also very right about your install; a clean install of ubuntu would sound a lot better

---

### Post by JeQhdMD on 2014-05-05
Additionally, the latest release of Ubuntu is 14.04 (Trusty Tahr) , another LTS (Long Term Support) version.  So, it makes sense to obtain that version, as it will be supported till April of 2019.   Wubi is indeed a dead duck.

---

### Post by Charlie_Jones on 2014-05-05
Gosh folks......thanks for you input!  Y'all are awesome!

I ran the uname -m command in terminal and here is result:  X86_64

I guess I got the wrong version because this old Dell is definitely a 32 bit machine.  Could 64bit on 32bit machine be the problem with printing?

If I could understand the installation instructions better, I would attempt a clean install.  Alas, I am such a greenhorn with Linux and reluctant to undertake this.  Of course I could make an image backup of my system and then hack away and if I mess it up too badly, simply restore from the image backup.  Does a tutorial for us greenhorns exist to guide the installation?

Again, many thanks to all responders.  I am most grateful.

---

### Post by pdc on 2014-05-06
well Charlie to put a version of ubuntu onto your computer: 

you need to put what is called a liveCD of Ubuntu into a CD drive on your computer;
make sure your boot is set so that it looks to boot from the CD drive first;
boot the liveCD; and either go for install there and then with the first screen; (or use the try ubuntu button to load ubuntu; and click on the install button once your have a try-desktop)

I only give that summary to give you an overview; you may be pleasantly surprised how easy it is to do: many cities around the world have LUG: linux users groups: google and see if one is in your city: they might well help you

---

### Post by Charlie_Jones on 2014-05-06
PDC, thanks again.

I found a Linux user group in Mobile and have written for details.

In the meantime, I decided to install the recommended Ubuntu 14.04 LTS on my 64 bit Windows 7 machine.  I have an empty 60 gb partition on the drive and wished to install Ubuntu there.  I downloaded the 14.04 lts iso and burned the cd.  I viewed the program by selecting "try Ubuntu" and afterwards decided to install.  Here is where the problem occurs........I get message "this computer has no detected operating systems. What would you like to do?"

Now I am uncertain and reluctant to proceed further.  

Any guidance shall be greatly appreciated.

---

### Post by pdc on 2014-05-06
Charlie: well done on getting the liveCD burnt; and booted from it? and you got to the ubuntu desktop on the liveCD? well done

if you are going to leave Windows; and you are clear of that; then you will be wanting to get rid of it ?? ........ erase it??? ........... 

for those situations, I am sure some would ask you if you can boot from the Ubuntu liveCD...............so you got the desktop with the option of install..and some might in their own hearts think..well, why not just click on the "install" button and go ahead;

it is only you will be doing that; and so need to decide;

looks like the guys (and gals) of the SAL [http://www.salug.org/](http://www.salug.org/) are meeting this Saturday: you can always rock up then; someone will be delighted to help you out

---

