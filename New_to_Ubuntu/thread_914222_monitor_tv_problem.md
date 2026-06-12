---
title: "monitor tv problem"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by nyteprowler02 on 2008-09-08
okay...what I'm trying to do is hook my tv up as my monitor.  my lcd was destroyed by my kids and I can't afford another one, but I have a spare tv.  I have the "S video" cable hooked into my video card.  Everything comes up on the tv, then it says something to the effect of: master 08: No Device and below it: master 01: No Device.

and then the tv screen goes blank and i hear the ubuntu come on and so I "blindly" type in my username & password, and  everything boots...just with out the video...leaving me blind...lol...I'm on a borrowed monitor right now, so I kinda need some immediate help.  Sorry to be in a hurry. 

-red-

---

### Post by knix on 2008-09-08
bump
I don't have a tv, so I don't know.
It probably has to do with your output resolution being to high for the tv, or not selecting input on the tv.

---

### Post by nyteprowler02 on 2008-09-08
Could you explain yourself a little bit more?... I'm thinking its within the settings that ubuntu has for the video card.  Ubuntu is not picking up the tv.

---

### Post by knix on 2008-09-08
yes. your tv probably runs at a lower resloution than your monitor. Try hooking up a borrowed monitor, opening a terminal, and typing "xfailsafedialog" and hitting enter. pick some low resolution like 640x480 or 800x600, then hook up your tv again.
Ubuntu doesn't "see" your tv because it's on the tv out interface, not the vga adapter.

---

### Post by kjohansen on 2008-09-08
what kind of video card do you have?

---

### Post by knix on 2008-09-08
with ati, install atitvout; with nvidia install nvtv

---

### Post by nyteprowler02 on 2008-09-08
I have an ati...

---

### Post by nyteprowler02 on 2008-09-08
good grief I didn't know they made so many friggin models of hitachi...lol...and of course I can't find the model number... I clicked on configure....still searching for model number...

---

### Post by nyteprowler02 on 2008-09-08
okay, so i ran my terminal, typed in what you said.  it said that it was running in low resolution....hold on...

---

### Post by nyteprowler02 on 2008-09-08
okay, so back in the terminal I typed: "atitv whatever the command you said was... and it told me to type: sudo ap something install atitv whatever...so I did...it ran...now what?  Sorry I'm asking questions like a fool...I was raised on windows, and its taking me a little bit longer to grasp ubunto although i've had it for about a couple of months and been off windows for about 2 years...lol....

---

### Post by nyteprowler02 on 2008-09-08
so again typing xfailsafedialog in terminal the following screen comes up: ubuntu is running in low graphics mode
your screen and graphics card could not be detected correctly.  To use higher resolutions, visual effects, or multiple screens, you have to configure the display yourself.

then there's the configure button, shutdown, and continue...

---

### Post by t0p on 2008-09-08
Now that you've installed **atitv** (that's what the sudo apt-get install command did), I'd suggest you use the program.  To find out how to use atitv, type into the terminal:

```
man atitv
```

---

### Post by nyteprowler02 on 2008-09-08
it says "no manual entry for atitv"

---

### Post by t0p on 2008-09-08
> **nyteprowler02 said:**
> it says "no manual entry for atitv"

Oh dear.  Was *any* documentation installed?  Have a look in **/usr/share/doc/atitv**.

Alternatively, if you type

```
atitv --help
```

into the terminal, it might give you a list of options/commands.

---

### Post by nyteprowler02 on 2008-09-08
okay i took the alternative....it installed it and is patiently waiting for its next command.... now what....???

---

### Post by nyteprowler02 on 2008-09-08
I like that "oh dear..."...like: that ain't good...lol...hehehe... or: what have we done now?...lol...

---

### Post by Periswell on 2008-09-08
ubuntu should sort out its s-video problems instead of making us do all the work. i been trying to get a non black and white picture on the tv screen for 4 months now.

-josh

---

### Post by t0p on 2008-09-08
Sorry, but I'm not familiar with atitv.  If typing in **atitv --help** hasn't produced a list of commands and there's nothing useful in **/usr/share/doc/atitv**, the only thing I can suggest is using google to look for a manual online.

The only positive thing I can add is that atitv is *probably* the program that will enable you to connect to your tv.  *Probably*. :)

If you do find a solution, please come back and post it up here.  I'm interested in connecting my computer to my tv.

---

### Post by nyteprowler02 on 2008-09-08
4 months? black & white.... my HD has no hope....lol....

---

### Post by Periswell on 2008-09-08
well i gave up 1 month ago. my dads vista (touch wood) does it, and im sad to say this, perfectly. ive got and intel video card so i cant do the atitv thing.

-josh

---

### Post by nyteprowler02 on 2008-09-08
ummm...question...how do i get into my /user/share/doc/ativ ?

---

### Post by Periswell on 2008-09-08
should that be /usr/share/atitv/doc?

---

### Post by Periswell on 2008-09-08
no you are right, do you want it in terminal or graphic?

---

### Post by nyteprowler02 on 2008-09-08
okay, so I went and typed in "man atitv"... this is what came up:

atitv(1) gatos manual

name
atitv - simple text-mode program from the gatos package

synopsis
atitv

description
The program atitv is still under development.  It gives basic function&#8208;
       ality needed to record video and take snapshots.
FILE FORMATS
       Note, motion capture in atitv use a special ".yuv" file  format  unique
       to gatos.

       Snapshots  on  the  other hand save to ".ppm" files, which are viewable
       (and convertible) by most graphics programs.

OPTIONS
       -h --help
              Get help.

 Manual page atitv(1) line 1
...

and a blinking cursor at the bottom...

---

### Post by nyteprowler02 on 2008-09-08
terminal or graphic?  ummm...can you please explain...??

---

### Post by Periswell on 2008-09-08
well do you want to access the folder in your terminal or going through youre file system.

also the fact that it says
> The program atitv is still under development. It gives basic function&#8208;
ality needed to record video and take snapshots.

is not good.

-josh

---

### Post by nyteprowler02 on 2008-09-08
yeah i kinda figured that....It would probably be simpler to go through my file system... I really don't fool with terminal that much unless its stuff like this....

---

### Post by Periswell on 2008-09-08
yeah i try to avoid it as much as i can, it sends my head funny. as atitv says is an incomplete project its proberly not got a document sorted out.

---

### Post by nyteprowler02 on 2008-09-08
hmmmm...this is not good...lol...any suggestions?

---

### Post by knix on 2008-09-08
My bad. I guesss I thought atitv was something other than what it was.

xfailsafedialog: you click configure, then it gives you the option to change settings (change resolution).
then click test. then keep settings. then OK.
Its normally what ubuntu launches when you have problems with X. However, it's also one of the easiest buit-in ways to configure x.

---

### Post by nyteprowler02 on 2008-09-08
well at least you tried...and nothings broken...I'll just have to find a deal on a used computer monitor until I can find out how to get it working...if I do come across some useful info on it, I'll be sure to post it, to let people know how its done...lol....thanks

---

### Post by nyteprowler02 on 2008-09-08
lol...it told me: Sorry, this configuration video card driver
and monitor doesn't appear to work:

hmmm....it also kept saying text failed...

---

### Post by t0p on 2008-09-08
> **nyteprowler02 said:**
> okay, so I went and typed in "man atitv"... this is what came up:

atitv(1) gatos manual

name
atitv - simple text-mode program from the gatos package

synopsis
atitv

description
The program atitv is still under development.  It gives basic function&#8208;
       ality needed to record video and take snapshots.
FILE FORMATS
       Note, motion capture in atitv use a special ".yuv" file  format  unique
       to gatos.

       Snapshots  on  the  other hand save to ".ppm" files, which are viewable
       (and convertible) by most graphics programs.

OPTIONS
       -h --help
              Get help.

 Manual page atitv(1) line 1
...

and a blinking cursor at the bottom...

That's just the first screen of the manual.  Hit the space bar and it will scroll down to show you the 2nd screen... and so on...

---

### Post by nyteprowler02 on 2008-09-08
yeah, I just now seen that...lol...so now what?

---

