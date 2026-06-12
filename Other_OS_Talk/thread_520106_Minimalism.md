---
title: "Minimalism"
date: 2007-08-07
forum: Other OS Talk
---

### Post by fistfullofroses on 2007-08-07
I myself am very much a minimalist, and I am hopefully going to be creating a very minimalistic distro, simply because I think there should be one. Not sure 'bout the base yet, as I am still gather my ideas. My thoughts for it are either Debian/Ubuntu, Gobo, or Slack. 

Anyway, what all console programs do you use?
What window manager do you use?
What graphical programs do you use?

---

### Post by LaRoza on 2007-08-07
> **fistfullofroses said:**
> I myself am very much a minimalist, and I am hopefully going to be creating a very minimalistic distro, simply because I think there should be one. Not sure 'bout the base yet, as I am still gather my ideas. My thoughts for it are either Debian/Ubuntu, Gobo, or Slack. 

Anyway, what all console programs do you use?
What window manager do you use?
What graphical programs do you use?

If you want mininimalist OS's, try these:

0. Slax - Frodo edition
1. Puppy onebone
2. Minix
3. [http://www.newsforge.com/os/02/10/27/1259241.shtml?tid=23](http://www.newsforge.com/os/02/10/27/1259241.shtml?tid=23)

---

### Post by stmiller on 2007-08-07
Steve Reich? 

I think blackbox is a good simple WM.

---

### Post by kerry_s on 2007-08-07
right now i'm using jwm, but i tend to bounce around all the light WM's from time to time.

current setup is debian base install+jwm
mc=file manager editor
iceweasel=web browser, i have enough juice i don't need to go less than the best.
conky=to monitor the usual stuff
vlc=all around player
xpdf=seems like i come across alot of pdf's, so if i have to this is light & fast
xzgv or gqview=got to view pics

---

### Post by fwojciec on 2007-08-07
More food for thought:

[[img]http://img339.imageshack.us/img339/3714/screenaugust07aa5.th.png[/img]](http://img339.imageshack.us/my.php?image=screenaugust07aa5.png)

Distro: Arch Linux (easy to keep it uber-minimal if you want to)
WM: Openbox
Conky (top right corner), Pypanel (top left), and Tint (bottom left)
Filemanager: mostly MC, but also Thunar if I need graphics
Terminal: rxvt-unicode (+ screen, usually)
Firefox, OpenOffice

---

### Post by fistfullofroses on 2007-08-07
I like your setup quite a bit. I used jwm for a while myself. Right now I am using GoboLinux with evilwm.

---

### Post by pelle.k on 2007-08-08
Arch linux = good minimalist alternative.

---

### Post by K.Mandla on 2007-08-08
+1 for Arch.

I use rtorrent, rxvt-unicode, elinks, htop, mc, cplay and alsamixer for console applications. For movies I run mplayer against the framebuffer. If I could find a good console CD burner and a good console id3 tag editor, I'd never use X at all.

Openbox is my window manager when I do use X. The newest version (3.4.4) is lightning fast and looks great. lxpanel is good for a panel; some people need it, I use it now and again.

---

### Post by jseiser on 2007-08-08
ubuntu server install, locale purge deborphan etc.
keep everything nice and trimmed.
Evilwm +xbindkeys/gmrun = full space desktop, fast, no menu needed.


"gmrun"
 Alt +F2

"urxvt -e mc"
 Alt +F3

"gksu synaptic"
 Alt +F4

"links2 -g -mode 1280x1024x32K"
 Alt +F5

"firefox"
 Alt +F6

"urxvt -e  cplay"
 Alt +F7

"urxvt -e  rtorrent"
 Alt +F8

that is my whole desktop.  I use nano most times so i just ctrl/alt/enter and type nano /what/file/here and im ready to type.  I have leafpad installed but i do not use it enough to bind it to a key, so i just alt/F2 and type leafpad and if i need a fill word processor i have one.  If i could figure out screen, i would just use screen and tell x to get lost. :)

for those interested here is my xinitrc.

numlockx &                  

# Merge X resources from ~/.Xdefaults
[ -f $HOME/.Xdefaults ] && xrdb $HOME/.Xdefaults 

feh --bg-scale /home/justin/wall.png
xsetroot -cursor_name left_ptr 
conky &
xbindkeys & 
evilwm -term urxvt -snap 10 -fg black -bg black  

the good thing about doing it this way, is when i want to change backgrounds i just save the image as wall.png and restart x, no editing of xinitrc to update the background.

---

### Post by kerry_s on 2007-08-08
hmm, sounds interesting, is it ugly or just good enough. can you post a pic? how is it on decorations?
it's pretty small synaptics says its 94.2kb, jwm is 213kb, but has the standard stuff.

here's mine still work in progress, i'm trying to keep it simple.

---

### Post by pelle.k on 2007-08-08
> the good thing about doing it this way, is when i want to change backgrounds i just save the image as wall.png and restart x, no editing of xinitrc to update the background.

Sorry for the OT guys, but;
There's no need to edit .xinitrc if you use
```
eval $(cat ~/.fehbg)
```

---

### Post by init1 on 2007-08-08
> **fistfullofroses said:**
> I myself am very much a minimalist, and I am hopefully going to be creating a very minimalistic distro, simply because I think there should be one. Not sure 'bout the base yet, as I am still gather my ideas. My thoughts for it are either Debian/Ubuntu, Gobo, or Slack. 

Anyway, what all console programs do you use?
What window manager do you use?
What graphical programs do you use?
Console programs? 
apt-get
syslinux
ls
cd
fdisk
robotfindskitten
links2 -g (does that count?)
mv 
rm
make
nano
e3 (e3pi mainly) 
joe (jpico mainly)
Lots others that I have forgoten

WMs?
Evilwm
Dwm
Lwm
9wm
Rat Poisen
Small stuff like that

GUIs?
Firefox
XMMS
Gparted
Not much else

I was thinking of making a minimal distro based on TTY Linux. It's a nice base: 5MB. I'll need to figure out how to add sound and better internet support. 
[http://www.minimalinux.org/ttylinux/showpage.php?pid=1](http://www.minimalinux.org/ttylinux/showpage.php?pid=1)

---

### Post by jseiser on 2007-08-09
i would love a minimal distro, ive been wanting to base one of debian but i do not have the knowledge, i have a thread going in other os about doing just this.  Im stuck with xubuntu on my laptop, because the server install just wont work right :( i would really love to get all this **** off the laptop ubt xubuntu was better than vista ...

---

### Post by jseiser on 2007-08-09
> **kerry_s said:**
> hmm, sounds interesting, is it ugly or just good enough. can you post a pic? how is it on decorations?
it's pretty small synaptics says its 94.2kb, jwm is 213kb, but has the standard stuff.
.

if thats in reference to the evilwm, there isnt anything to screen shot really, its would just show my background and conky, change windows with Alt/Tab, you can move windows with mouse1, resize with mouse2, send them down with mouse 3.  You can also move windows with ctr/alt/hjkl to move left, up,down,right respectively.  ctrl alt x fullscreens the window, ctrl/alt/= will verticly maximise the window which is how i normally run things.  Say cplay/firefox split screened so i can surf and see my playlist.  or, leafpad and firefox split so i can follow a tutorial etc.  It is all about allowing oneself to use your whole display without any clutter.

---

### Post by kerry_s on 2007-08-09
> **jseiser said:**
> if thats in reference to the evilwm, there isnt anything to screen shot really, its would just show my background and conky, change windows with Alt/Tab, you can move windows with mouse1, resize with mouse2, send them down with mouse 3.  You can also move windows with ctr/alt/hjkl to move left, up,down,right respectively.  ctrl alt x fullscreens the window, ctrl/alt/= will verticly maximise the window which is how i normally run things.  Say cplay/firefox split screened so i can surf and see my playlist.  or, leafpad and firefox split so i can follow a tutorial etc.  It is all about allowing oneself to use your whole display without any clutter.

ohh, okay i think i tried that 1 then. if i remeber right it was to keyboard oriented for me. i like to kick back in my chair & put my feet up & just click away with the mouse sometimes. i might try it again anyway.
have you tried it with rox pinboard to add desk top icons?

okay tried it again, don't like evilwm, it's just to evil. :)

---

### Post by jseiser on 2007-08-09
never tried with icons, also, did you set up a xbindkeys?  It really makes it awesome, no need to open the console, just hit your bound key and bam, there is your program :)

---

### Post by kerry_s on 2007-08-09
> **jseiser said:**
> never tried with icons, also, did you set up a xbindkeys?  It really makes it awesome, no need to open the console, just hit your bound key and bam, there is your program :)

didn't bother to, like i said, i like to put my feet up on the desk and click with the mouse, not be  right up on it to press the keyboard shortcuts, that's just way to constraining. but if i needed the size i would put up with it. :)

---

### Post by Epilonsama on 2007-08-09
Why dont you try E17, is light on your resource and doesnt look like windows 95 :)

---

### Post by init1 on 2007-08-09
> **jseiser said:**
> i would love a minimal distro, ive been wanting to base one of debian but i do not have the knowledge, i have a thread going in other os about doing just this.  Im stuck with xubuntu on my laptop, because the server install just wont work right :( i would really love to get all this **** off the laptop ubt xubuntu was better than vista ...
GRML Small is rather nice. I think it has an installer script. I think it is less than 100MB. 
[http://grml.org/](http://grml.org/)

---

### Post by init1 on 2007-08-09
> **kerry_s said:**
> ohh, okay i think i tried that 1 then. if i remeber right it was to keyboard oriented for me. i like to kick back in my chair & put my feet up & just click away with the mouse sometimes. i might try it again anyway.
have you tried it with rox pinboard to add desk top icons?

okay tried it again, don't like evilwm, it's just to evil. :)
evilwm is nice :evil:

---

### Post by kerry_s on 2007-08-10
> **init1 said:**
> evilwm is nice :evil:

it's okay, i just can't get use to it. i added idesk for some icons & and a rotating background, put my conky up. i have a bad memory so trying to remember the keys is really throwing me off.
to each his own, you enjoy, i played with it all day, back to jwm for me. :)

---

### Post by fistfullofroses on 2007-08-10
Yeah, I've messed around with GRML before. It came with an issue of Linux Format. I don't really remeber which one. I have a few laying around the room here, and I know there are a ton in the desk here. Hadn't thought about GRML in a long while. I might give it a spin again.

---

### Post by fistfullofroses on 2007-08-10
Does everyone but me have robotfindskitten installed or something? I here about it all the time.

---

### Post by init1 on 2007-08-11
> **fistfullofroses said:**
> Does everyone but me have robotfindskitten installed or something? I here about it all the time.
```

sudo apt-get install robotfindskitten
robotfindskitten

```
I first found it on LNX-BBC. They have so many versions. DOS, Amiga, Debian, PSP, GBA, Flash, Java, Javascript. 
[http://robotfindskitten.org/](http://robotfindskitten.org/)
[http://www.lnx-bbc.com/](http://www.lnx-bbc.com/)

---

### Post by kyrhash on 2007-08-11
flux box, enough said

---

### Post by RAV TUX on 2007-08-11
> **fistfullofroses said:**
> I myself am very much a minimalist, and I am hopefully going to be creating a very minimalistic distro, simply because I think there should be one. Not sure 'bout the base yet, as I am still gather my ideas. My thoughts for it are either Debian/Ubuntu, Gobo, or Slack. 

Anyway, what all console programs do you use?
What window manager do you use?
What graphical programs do you use?

Wolvix Cub is nice and minimal (Slackware based)

You may want to consider an rPath base using rBuilder if you want an outstanding development environment.

---

### Post by vinboy on 2007-08-21
Yes we need a minimalist Ubuntu.
What I mean is a Ubuntu core, with Gnome, but exclude Firefox, Evolution and many many other applications.
that would be sweet.

---

### Post by kerry_s on 2007-08-21
> **vinboy said:**
> Yes we need a minimalist Ubuntu.
What I mean is a Ubuntu core, with Gnome, but exclude Firefox, Evolution and many many other applications.
that would be sweet.

with gnome & you think it's going to be minimal. no mater how you go about it gnome has alot of crap. Firefox is still usefull even on the slow and if you use a older version it's even better.

558mb minimal :)

---

### Post by bonzodog on 2007-08-22
I have Zenwalk Core installed, added X, then Openbox, SLiM for a login manager, firefox, gtk engines, and a few other X apps as I went along.

It really is minimal, as when you finish the core install, you end up with about 200MB of installed stuff.

K.Mandla: try using Bashburn for burning CD's, and learn cdrecord -- it is amazingly powerful given the right options at the cli. I use Growisofs for command line DVD burning.

---

### Post by urukrama on 2007-08-23
> **bonzodog said:**
> SLiM for a login manager

What are the advantages of slim over gdm? I generally install gnome-core as well, so gnome-dependencies are not that big of an issue for me.

---

### Post by fistfullofroses on 2007-08-23
SLiM is lighter weight, easier to skin, and generally much much faster to load. With a minimalist approach it is the way to go.

---

