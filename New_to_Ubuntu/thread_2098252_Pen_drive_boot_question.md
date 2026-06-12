---
title: "Pen drive boot question"
date: 2012-12-26
forum: New to Ubuntu
---

### Post by barebear on 2012-12-26
I built a boot USB stick with 32 bit Ubuntu 12.10 using the utility from pendrivelinux.com  because I wanted to do my online financial things in  a more secure environment than Windows. 

It works perfectly on  the desktop 32 bit XP SP 3 machine I built it on -- I can boot into  Ubuntu, do the internet things I need to do, shut down the computer,  pull out the boot USB, and then start again and be in my Windows  installation with no problem.

I have a laptop HP DV7-1133 with 64  bit Vista Home Premium, an AMD Turion dual core processor Mobile RM-70 2  GHz and ATI Radeon HD 3200 graphics. It was given to me so I'm not sure  of its exact age --I think approx. 5 yrs. 

When I try to boot the laptop from the 32 bit USB stick I get a black screen with one line of text that reads 
" SYSLINUX 4.06 EDD 2012-10-23 copyright 1994-2012 H. Peter Anvin et al "
Under that there is a flashing  -  ( cursor )which after 10 minutes is still flashing and nothing else has happened.

Do  note that I built a 64 bit Ubuntu 12.10 boot USB on the Vista rig  thinking that there might be a compatibility issue with my 32 bit stick.  Sadly, it also gives the identical aforementioned black screen with  text and cursor.

Given all of the preceding, I deduce that the problem most likely is with the laptop rather than the boot USB's I built. 

What,  if anything, can be done to enable my booting the laptop into Ubuntu  from my USB drive ? -- in case of a failure on my XP system I want to  have an alternative Linux environment in which to do financially  sensitive online things.

Please note that I am totally new to  Linux and if it weren't for the article in Maximum PC magazine a couple  of months ago I wouldn't have had the least clue as to how to accomplish  what little I've managed so far.

Thanks to all in advance for your help!

---

### Post by fdrake on 2012-12-26
> **barebear said:**
> 
I have a laptop HP DV7-1133 with 64  bit Vista Home Premium

i would get rid of it. get win xp or win 7 instead if you can. 


> 
When I try to boot the laptop from the 32 bit USB stick I get a black screen with one line of text that reads 
" SYSLINUX 4.06 EDD 2012-10-23 copyright 1994-2012 H. Peter Anvin et al "
Under that there is a flashing  -  ( cursor )which after 10 minutes is still flashing and nothing else has happened.

did you try to press the enter key? does it do anything?

why don't you try an older kernel with ubuntu 10.04
[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

---

### Post by barebear on 2012-12-26
For fdrake..

Hitting "Enter" was the first thing I did; nothing happened.

Like you, I despise Vista but don't have either the 64 bit XP or W 7 install discs and keys.

I am right that I shouldn't try to install 32 bit XP on the 64 bit machine ?

Thank you for your suggestion re 10.04 ---- I'll give it a go tomorrow  and post back with results-- you're in Boston and its 1230 AM Wed. here in Calif.

I read somewhere that Xubuntu is less resource intensive than Ubuntu. Is that correct ? If not, is there a version that is less resource intensive, and would it be understandable by a total Linux noob like me ?

---

### Post by fdrake on 2012-12-26
> **barebear said:**
> \\
I am right that I shouldn't try to install 32 bit XP on the 64 bit machine ?

32 bit works on 64 but not the way around.

> 
I read somewhere that Xubuntu is less resource intensive than Ubuntu. Is that correct ? it is less resource intensive but they have the same kernel. I would give it a shot too, just in case...

---

### Post by barebear on 2012-12-26
for fdrake....

Thank you again !

Now, what do you recommend trying first -- Ubuntu 10.04 or Xubuntu ? If Xubuntu, which version.

Where to go to get Xubuntu ?

A 32 bit XP install is a possibility if nothing else works, but I'd prefer to not have to invest that much time.

---

### Post by barebear on 2012-12-26
for fdrake...    I started with an Ubuntu 10.04 stick and freaked when I had no internet --the laptop connects through a wireless access point---I was being asked for Mac address, etc and was clueless as how to get that info.      I built an 11.04 stick and it worked with no internet issues other than having to enter my WPA2 key to connect through the WAP.      I then had to go online to find out how to update Firefox, managed to accomplish that, and consider the situation resolved since all I want Ubuntu for is safer online banking than in a Windows environment.      I find Ubuntu very complicated -- I had to go online to find out how to get to the terminal, and all the different commands are way over my head.      You can't just click on a download and install something. Sudo this, Sudo that...  grrr! lol.      Now if there were a simple to understand Ubuntu noob guide.....

---

### Post by fdrake on 2012-12-26
> **barebear said:**
> 
  I then had to go online to find out how to update Firefox, managed to accomplish 

Once you learn the method of solving an issues , you'll find out that the key is searching the net. Especcially the website of the software.

> 
that, and consider the situation resolved since all I want Ubuntu for is safer online banking than in a Windows environment. 

Ubuntu is secure but it is also up to the users to know what they are doing. Using usb-live-os for banking and purchases is a good idea.You can use it also to access emails and browse private data, when you are working with a system that you don not trust (or is public to anyone)

> 
I find Ubuntu very complicated 

You can ask in the forum if you cannot solve a proble by yourself.


> 
-- I had to go online to find out how to get to the terminal, and all the different commands are way over my head. 
Again you need to get used to it. Also havving a certain level of knowledge for everyday operations is suggested.


> 
 Now if there were a simple to understand Ubuntu noob guide.....
you can try these links 
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[https://help.ubuntu.com/11.10/ubuntu-help/index.html](https://help.ubuntu.com/11.10/ubuntu-help/index.html)

---

### Post by audiomick on 2012-12-26
Hi Barebear.
Regarding the Vista machine: I have a Vista laptop, and I can live with it for the windows stuff I need to use, which is not games and not that simple. That it just me, though.

If you don't need the windows on the machine, and can't get it to boot from USB, burn a CD / DVD of the Ubuntu .iso and boot from that. Get rid of the windows entirely and make a pure Ubuntu machine out of it. 

If the machine is running Vista, it should be able to deal with a current Ubuntu ok too. If you are worried about that, try running the live environment from the CD / DVD before you install. I don't think you should have a problem, though.

Just by the by, I would set up a dual boot on the desktop too, instead of dicking around with a USB stick. But that is just me...

---

### Post by barebear on 2012-12-26
for fdrake......

When I was commenting about updating Firefox I  meant in Ubuntu --I got the download w/ no problem  -- it was how to  install it that totally confused me. Just getting to the terminal was a  research job and I had to invest a lot of time to find the commands to actually be able to do the update -- a daunting experience to say the least.
> 
Using  usb-live-os for banking and purchases is a good idea. -- that's exactly  what I want Ubuntu for ---maybe, after looking through the links you  referred me to, I'll feel comfortable enough to try and do more.

I really do appreciate your time and help ! I'll post again after checking out the links.

for audiomick......

I think this Vista laptop wouldn't boot from the USB because of its hardware configuration -- it boots ok off the 11.04 stick that I made after being spooked by the internet connection issues I had with the 10.04 stick, but won't boot from a 12.10 stick.

I have no games on any of my systems. I want Ubuntu strictly for and per the quote above from fdrake

---

### Post by barebear on 2012-12-27
for fdrake....

I went to the links you were kind enough to provide and realize I have a horrific amount to learn -- I think I'm going to start with  [https://help.ubuntu.com/11.10/ubuntu-help/index.html ]("https://help.ubuntu.com/11.10/ubuntu-help/index.html")

If I'm going to ever really get comfortable w/ Ubuntu I've absolutely got to be able to install/uninstall software -- doing the FF upgrade from 3 to 16.1 left me overwhelmed --I'm no slouch at researching, but so much of what I found seemed to take for granted that I knew things which I had no clue about  (such as how to open the terminal -- I've learned Ctrl + Alt +T, but there are other ways too?)

The one thing I know for sure is that I'm going to stay with a boot USB for a very long time -- until I feel comfortable w/ Ubuntu there is no way I'm going to install it. For right now, as long as I have something more secure than Windows to do online financial and other sensitive things, I'm a happy camper.

One last ? for now --how many beans to a cup of Ubuntu ?

---

### Post by fdrake on 2012-12-27
> **barebear said:**
> for fdrake....

One last ? for now --how many beans to a cup of Ubuntu ?

you mean the cups in the forum?
I am not sure ....

---

### Post by audiomick on 2012-12-27
> **barebear said:**
> ... I think I'm going to start with  [https://help.ubuntu.com/11.10/ubuntu-help/index.html ]("https://help.ubuntu.com/11.10/ubuntu-help/index.html")


That is a good place to start.

> 
If I'm going to ever really get comfortable w/ Ubuntu I've absolutely got to be able to install/uninstall software ...

(such as how to open the terminal -- I've learned Ctrl + Alt +T, but there are other ways too?)...

The one thing I know for sure is that I'm going to stay with a boot USB for a very long time -- until I feel comfortable w/ Ubuntu there is no way I'm going to install it....

The best way to install software is to use the software centre. You wrote in one post "You can't just click on a download and install something". In fact, it is even easier than that: you just go to the software centre and look for your program. 
If the program isn't in the software centre, then you look for a .deb file in the internet. For windows you have to look for a .exe. No big differenence. But you will find that all out with time.

Terminal is easy. There is the key combination you mention. On 11.04 and earlier it is in the accessories menu. On the unity desktop, type "terminal" in the search box on the dash.

As far as getting comfortable with ubuntu goes, I really do recommend you install a dual boot on one of your machines, and use it. You learn a new OS quickest when you start doing your day to day stuff on it, and only go back to the familiar environment when you are really stumped on something that has to be finished really quickly. 

> 
One last ? for now --how many beans to a cup of Ubuntu ?

From here:
[http://ubuntuforums.org/announcement.php?f=48]("http://ubuntuforums.org/announcement.php?f=48")

> What's the deal with coffee cups/beans and the funny titles?

Beans are posts. The post/bean count can be turned off by the user if so desired.

There tends to be a close connection between geeks and coffee, so that's where the theme came from. Yes, we know not everyone likes coffee, but it's just a silly thing.

The images, their colors, and the changing icons don't have any special meaning. They simply change as time goes by. You will see (among other things) green coffee beans, roasted (brown) coffee beans, various sorts of coffee cups and mugs and so on. Like the titles, nothing specific is implied by the presence of specific images or titles (in almost all cases that is...staff, admins and banned users are some of the exceptions). These items are for fun, and are not serious. They are not a rank of any kind. They don't tell anyone how long you've been here nor how many posts you've made. The sayings and the images are a semi-random feature we have to provide a little kick. There is some structure to it, but only on the implementation side. We did this on purpose - because it was fun and whimsical.

There isn't a list of what you get, and when, because that's not the point. The reason for the secrecy was/is this: while we want to reward people who participate in these forums with titles and changing symbols we really don't want them to become some sort of gauge that people use to determine whether someone is speaking with more/less authority on a support topic. Other forums use the title/icon system that way and more power to them. However, there are people here with less than 20 posts who can code circles around much of the staff and are capable of giving amazing and useful responses to support questions...and there are some of us here with thousands of posts who might get lucky with a good and helpful reply on occasion. The fear is that people might use post count and titles/symbols as a means of judging the validity of a post's content rather than the content itself. We had a long discussion about this in the forums when they were first started and this subject has been revisited among the staff several times. Some forum members and staff wanted to eliminate the post count and title/icon system completely, some have gone the other way wanting a complete ranking system that is clear and gives honorific titles with great meaning to those with higher post counts (that particular group is in the extreme minority). The current system is a compromise that has been working pretty well for a while. With the compromise of meaningless titles/icons, post count can be hidden in UserCP. Anyway, this is why we don't publish how many posts are necessary for a change in title/icon...it's just a silly reward. The post numbers needed for title changes is something that is easy to modify so it gets modified on occasion, when the admins don't have better things occupying their time, merely to maintain the surprise factor. Bottom line: it just a trivial, whimsically amusing little thing. Don't read too much into it...it really isn't worth the slightest emotional involvement.


---

### Post by barebear on 2012-12-27
For audiomick/michael...

Thank you !

---

