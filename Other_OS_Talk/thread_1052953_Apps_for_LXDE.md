---
title: "Apps for LXDE"
date: 2009-01-28
forum: Other OS Talk
---

### Post by piousp on 2009-01-28
Hi folks!
Short story: i installed eeebuntu on my eeepc. Since i dont like gnome i installed LXDE on it.
So, everything works superfine under LXDE, but i'm missing a couple of apps:

1) A CPU frecuency changer, you know, changing between "Powersafe" and "Performance". On my laptop, i use KDE so kpowersafe its pretty good for me. LXDE has a battery monitor, but i cant find any cpu frecuecy changer or whatever that is called.

2) A wi-fi/network manager. Again, gnome's one doesnt cut it for me.

3) Any other cool app just for fun :)

Thanks in advance

---

### Post by meborc on 2009-01-28
2) [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by smartboyathome on 2009-01-28
I don't know if Ubuntu has it, but CPUFreq works great for me on arch. :)

---

### Post by cmay on 2009-01-28
did you see the eeepc applet in synaptic. i did not try it yet. (i use open box and lxde on my eee too :) )

---

### Post by piousp on 2009-01-28
Woah, thanks for the replies!! I'm gonna check everything as soon as i get home!!! Thanks!! :KS

---

### Post by piousp on 2009-01-28
> **smartboyathome said:**
> I don't know if Ubuntu has it, but CPUFreq works great for me on arch. :)

Duh, i typed exactly that on synaptic and there you go, like 5 different apps for cpu scaling. NICE!

---

### Post by smartboyathome on 2009-01-29
Another suggestion: Mirage for image viewing. It is light yet does everything an image viewer should do. :)

---

### Post by Paul Miller on 2009-01-29
Since lxde is the Lightweight X Desktop Environment, you can probably find apps that work well with it by searching for "light foo" or "lightweight foo", where foo represents the type of app you're after.  Maybe add "-gnome -kde" to your search string while you're at it. :-)

Incidentally, I'd like to highly recommend feh as an image viewer.  I think it's the best Linux image viewer since xv!

---

### Post by smartboyathome on 2009-01-29
> **Paul Miller said:**
> Since lxde is the Lightweight X Desktop Environment, you can probably find apps that work well with it by searching for "light foo" or "lightweight foo", where foo represents the type of app you're after.  Maybe add "-gnome -kde" to your search string while you're at it. :-)

Incidentally, I'd like to highly recommend feh as an image viewer.  I think it's the best Linux image viewer since xv!

I only recommend feh as a background switcher on E17 or other WMs which can't set root window backgrounds. Otherwise, I find it lacking in the image viewer department (it doesn't allow you to view multiple pictures without exiting and opening the new one up like in Mirage).

---

### Post by doorknob60 on 2009-01-29
Gpicview (which comes with Lxde) is great, so I recommned keeping it. Probably just as good (maybe better) than the Gnome and KDE default ones.

---

### Post by handy on 2009-01-29
I've just installed LXDE on Arch.

I am having trouble with the panel & also the only icon on the desktop that works is /home the other icons don't appear, but they do have their names showing, clicking on them brings up an error that the command failed?

The first time I started lxde it had a fast flickering colour change that was the size of the panel across the bottom of the screen.

I had a look at the wiki & set up the lxde panel config files in /home & got a panel, which I've put over on the right side vertical as is my preference these days.

It doesn't flicker any more but it does disappear for a while at times, & on starting the lxde it can choose to not show up for some minutes?  I'm learning to be patient with it. ;)

When I right click on the panel I get the following error:

[I]The folder contents could not be displayed

Error stating file '/home/handy/# /usr/share/lxpanel/images': No such file or directory[/I]

Though I can close the pop-up & still use the add / remove panel items dialogue.


What I do like about lxde at this early stage is its speed, it is making Xfce seem slow.  I also prefer PCMan to Thunar, though I don't use Thunar as I much prefer Worker.  Image Viewer is fast, it just needs to be able to set the images to fill the screen in preferences & it would be my viewer of choice.

You know it just occurred to me, that if I want more speed, I could go back to Openbox & use the Xfce panel which suits me down to the ground.  Though I wonder how much the Xfce panel will slow Openbox down?

---

### Post by piousp on 2009-01-29
Openbox with xfce panel??? Guess i'm gonna try it out!
Mirage is what i've been using for a while, so i had it before lxde.
I can swear i saw Wicd yesterday on synaptic, but now i just cant find it again, damn :o
PcMan is really good for my taste, and blackbox makes me happy. Now that i think about, some months ago, i saw a kinda big post about tiled wm, so maybe i'm ready to try em out.

Any way, back to topic: any GOOD lw music player? Right now i'm using one that its called "Aqualung" which i feel lighter than others, but any suggestions would be appreciated!

Also, should i keep GDM for the login screen? Can i get something lighter there too? I know i could just dump GDM and use console login and then start x, but nah, i dont feel like doing it ;)

By the way handy, that Zeitgeist page looks pretty interesting.

Thanks so far!

---

### Post by meborc on 2009-01-29
for login...

the fastest (quickest) is XDM, but it looks really ugly

i would use SLiM - [http://slim.berlios.de/](http://slim.berlios.de/)

it is small, fast AND good looking ;)

---

### Post by ugm6hr on 2009-01-29
> **meborc said:**
> i would use SLiM - [http://slim.berlios.de/](http://slim.berlios.de/)

it is small, fast AND good looking ;)

I like slim too.

Check the link below re: LXDE for more details.

---

### Post by handy on 2009-01-29
In Arch, I just use runlevel 5 & no login manager in inittab, & then edit .xinitrc to call whatever DE/WM, so that when I boot the machine I log in my user at the prompt & the DE/WM I've set to start in .xinitrc starts.

My .bashrc is as follows:

[I]. $HOME/.bashrc
if [[ -z "$DISPLAY" ]] && [[ $(tty) = /dev/vc/1 ]]; then
	exec xinit -- :0 
	logout
fi[/I]


When I log out I have to change out of vc/1, then login & issue whatever command - halt, reboot or whatever or login to vc/1 as root & do the same.

By issuing the following command you can use halt & reboot without being su:

*chmod +s /sbin/halt*

---

### Post by cardinals_fan on 2009-01-29
> **doorknob60 said:**
> Gpicview (which comes with Lxde) is great, so I recommned keeping it. Probably just as good (maybe better) than the Gnome and KDE default ones.
GQView has far more sophisticated tagging abilities and is still very light.

---

### Post by handy on 2009-01-29
> **cardinals_fan said:**
> GQView has far more sophisticated tagging abilities and is still very light.

I don't remember stumbling across GQView in the past.  I love it, thanks for bringing it to my attention, I just deleted Mirage & Gwenview with all of KDEMod, that had to be there whilst I was checking out Gwenview.

For my use, GQView looks like it will be hard to beat, it is quick & highly featured. :-)

---

### Post by cardinals_fan on 2009-01-29
> **handy said:**
> I don't remember stumbling across GQView in the past.  I love it, thanks for bringing it to my attention, I just deleted Mirage & Gwenview with all of KDEMod, that had to be there whilst I was checking out Gwenview.

For my use, GQView looks like it will be hard to beat, it is quick & highly featured. :-)
I use it myself for organizing and viewing just about everything.

---

### Post by handy on 2009-01-30
> **piousp said:**
> 
Openbox with xfce panel??? Guess i'm gonna try it out! 

I did it today, & I'm really happy with it. It is really quite a bit faster than Xfce, though my desktop looks identical (with no windows open anyway) even though it is Arch/Openbox that my xfce-panel is now sitting on top of.

You can see in the screenshot how the colours of the window title bar & the Openbox Menu don't really quite harmonise with the colour of the text in the Firefox menu & tabs.  That's because of the modified theme I'm using, it doesn't quite all work with Openbox for some reason?

I guess I'll eventually be driven to edit the gtkrc file. ;-|

> **piousp said:**
> 
By the way handy, that Zeitgeist page looks pretty interesting.


I wish the vast majority of the world's population thought so, we could turn things around pretty quickly under those circumstances.


***[Edit:]** Added 2nd screenshot showing the (now edited gtkrc) new colour of the fonts; it is a pragmatic theme not a theme of beauty. 8)*

***[Edit:2]** Added 3rd screenshot showing the customised menu layout which now has everything I require added to it & it feels just like /home now, only younger & nippier. :-D*

---

### Post by piousp on 2009-01-30
Nice nice nice! This is getting really fun. Anyways, back to custu... err, I mean, back to work :p
Thanks everyone!

@ugm6hr
I'm checking the site right now! Haven't tried wicd, i intent to do it today.

@handy
Thanks for your script! Although I don't really get it, that just means i gotta do some research now ;)

@cardinals_fan
Downloading GQView

---

### Post by jay576 on 2009-01-30
Anyone know how well it will run on 64mb of ram?

---

### Post by piousp on 2009-01-30
Mmm, my guess is that i would run fine if you have a good cpu, but who does have a good cpu with only 64mb of ram anyways? :p

Maybe you should made a ubuntu base install and then get lxde on it.

---

### Post by snowpine on 2009-01-30
> **jay576 said:**
> Anyone know how well it will run on 64mb of ram?

Nothing runs well with only 64mb. ;)

Seriously, it depends on what you use as the base system. I wouldn't even attempt Ubuntu+LXDE with only 64mb of ram. But SliTaz uses LXDE too, and it has a 'loram' flavor that is supposed to run with 64mb. There may be others, too, but I don't want to speak without experience.

---

### Post by jay576 on 2009-01-30
I'll try a Debian Lenny install with it on that machine soon.  It successfully installed Xfce on etch but was just extremely slow as you would expect.  I don't plan on actually using said computer for anything.

---

### Post by ugm6hr on 2009-01-30
> **jay576 said:**
> Anyone know how well it will run on 64mb of ram?

For less than 64MB, I recommend only DSL.

I gather DeliLinux runs reasonably well too.

Puppy Linux will run, and reasonably well, but it still feels too slow in the modern era to be a usable computer.  LXDE will be similar on any base, I suspect.

---

### Post by piousp on 2009-01-30
> **meborc said:**
> 2) [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

PERFECT!!! wicd is sooooo nice!!! Thanks!!
Just 1 question, can i set up a proxy there?

---

### Post by handy on 2009-01-30
> **jay576 said:**
> Anyone know how well it will run on 64mb of ram?

LowArch might work too?

*_[http://ubuntuforums.org/showthread.php?t=1028174](http://ubuntuforums.org/showthread.php?t=1028174)_*

---

### Post by meborc on 2009-01-31
> **snowpine said:**
> Nothing runs well with only 64mb. ;)

Seriously, it depends on what you use as the base system. I wouldn't even attempt Ubuntu+LXDE with only 64mb of ram. But SliTaz uses LXDE too, and it has a 'loram' flavor that is supposed to run with 64mb. There may be others, too, but I don't want to speak without experience.

emmmm. i care to argue with that first sentence...

i just got a hold on 64 M ram, 333 MHz pentium II, gateway solo 2500

it has windows 98 on it and it just files... i mean, the menus open instantaneously... MATLAB - 2 sec to open (it is old matlab, but so what)... PDF files - 1 second to open

this small baby is perfect :)

the problem is, i can probably only run [INX]("http://inx.maincontent.net/") on it :(

---

### Post by smartboyathome on 2009-01-31
> **meborc said:**
> emmmm. i care to argue with that first sentence...

i just got a hold on 64 M ram, 333 MHz pentium II, gateway solo 2500

it has windows 98 on it and it just files... i mean, the menus open instantaneously... MATLAB - 2 sec to open (it is old matlab, but so what)... PDF files - 1 second to open

this small baby is perfect :)

the problem is, i can probably only run [INX]("http://inx.maincontent.net/") on it :(

Hey, that is a newer version of my old laptop (Gateway Solo 2150), and it has more RAM and CPU power than yours! :P

Since it has that much RAM, though, I can run Puppy on it and it works just file (fully installed, that is, it doesn't work well in frugal/livecd mode).

---

### Post by glotz on 2009-01-31
> **meborc said:**
> i would use SLiM - [http://slim.berlios.de/](http://slim.berlios.de/)Can you shutdown the computer right from within session with it, just like with GDM or do you must exit to the greeter?

> **cardinals_fan said:**
> GQView has far more sophisticated tagging abilities and is still very light.+1 GQView kicks butt!

---

### Post by handy on 2009-01-31
> **piousp said:**
> 
@handy
Thanks for your script! Although I don't really get it, that just means i gotta do some research now ;) 

Here is a link where you will find out about starting up your DE/WM without a login manager, it is worth reading all the way through imho:

*_[http://bbs.archlinux.org/viewtopic.php?id=57677&p=1](http://bbs.archlinux.org/viewtopic.php?id=57677&p=1)_*

> **piousp said:**
> 
@cardinals_fan
Downloading GQView

I'm sure you are loving it, I think GQView is brilliant!

---

### Post by piousp on 2009-02-02
> **handy said:**
> Here is a link where you will find out about starting up your DE/WM without a login manager, it is worth reading all the way through imho:

*_[http://bbs.archlinux.org/viewtopic.php?id=57677&p=1](http://bbs.archlinux.org/viewtopic.php?id=57677&p=1)_*



I'm sure you are loving it, I think GQView is brilliant!

Nice!!! (Back to the forum spree... err, work i mean ;) )
GQView is brilliant indeed! You can add 1 more follower to GQView!

Thanks again handy!

---

