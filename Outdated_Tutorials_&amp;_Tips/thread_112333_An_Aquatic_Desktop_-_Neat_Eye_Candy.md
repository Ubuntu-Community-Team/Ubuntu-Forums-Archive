---
title: "An Aquatic Desktop - Neat Eye Candy"
date: 2006-01-04
forum: Outdated Tutorials &amp; Tips
---

### Post by poofyhairguy on 2006-01-04
I have sat on this into for too long. Its time to tell the tale about some pretty neat eye candy. 

I will let the author explain it:

" xdesktopwaves is a cellular automata setting the background of your X Windows desktop under water. Windows and mouse are like ships on the sea. Each movement of these ends up in moving water waves. You can even have rain and/or storm stirring up the water."

Sounds cool huh? Here is some screenshots:

[http://ubuntuforums.org/gallery/showimage.php?i=1681&original=1&c=2](http://ubuntuforums.org/gallery/showimage.php?i=1681&original=1&c=2)

[http://ubuntuforums.org/gallery/showimage.php?i=1682&original=1&c=2](http://ubuntuforums.org/gallery/showimage.php?i=1682&original=1&c=2)

[http://ubuntuforums.org/gallery/showimage.php?i=1683&original=1&c=2](http://ubuntuforums.org/gallery/showimage.php?i=1683&original=1&c=2)


Bonus is that its REALLY stable for me. Downside is that is uses CPU power (you determine how much though).

If you want to try it, pull out the terminal and type in:

```
sudo apt-get install xdesktopwaves
```

Now lets try it out. Put this command in the terminal:

```
xdesktopwaves
```

There is the effect. Press control and C to stop it. Now to make it better. First I like to improve the quality. This command is an example of how to do that.

```
xdesktopwaves -quality 8
```

That is my favorite level of quality. It might make it too slow for you. So replace the "8" with any number from one to nine, with one being the lowest. Keep experimenting with the numbers until you hit the balance of performance and looks for your machine. Its your CPU power at work, so choose wisely. 

Next we will play with the color. Here is an example command:

```
xdesktopwaves -colortheme 3
```

Now change the "9" to any number one through nine. Each is very different. Fun to try out. One looks like toxic waste, another like blood. I like 3 the best, but 1 is the most blue. 7 and 9 are cool too.

Now for the fun stuff. To add rain use this example command:

```
xdesktopwaves -rain 2
```

Cool huh? Again you can change "2" to any number one through nine but I find after "3" it gets too busy for my own tastes. 

Now is the worst effect- the storm. It adds wind as an element. To try use this example command:

```
xdesktopwaves -storm 2
```

Again replace the "2" with any number one through nine if you wish. I never use this one because I find it makes my desktop too busy.

Now if you REALLY like this trick and you are willing to give up your desktop for it (it does not get deleted, it is just hidden) then try this command:

```
xdesktopwaves -opaque
```

Its a safe command, so everyone should try it once.

Now figure out what commands you like and try stacking them. Here is an example and good default:

```
xdesktopwaves -quality 7 -opaque -rain 1 -colortheme 7
```

Order does not matter, just put a space in between each. Try it.

Here is the command I use:

```
xdesktopwaves -quality 8 -rain 1 -colortheme 3
```

Now  armed with your favorite setup (or mine) lets make a launcher on your desktop;

Put this command in the terminal:

gedit toggle_xdesktopwaves.bash 

Fill the empty file by copying and pasting this:
```

#!/bin/bash
a=`ps -aef | grep -i xdesktopwaves | awk ' {if ($8 == "xdesktopwaves"){printf "2"}} '`
if  [[ $a = "" ]]
then
	**yourcommand** 
else
	kill -9 `ps -aef | grep -i xdesk | awk ' {if ($8 == "xdesktopwaves"){printf $2}} '`
fi
```

The part I bolded is where to put your  custom command. Here is the one I use
```

#!/bin/bash
a=`ps -aef | grep -i xdesktopwaves | awk ' {if ($8 == "xdesktopwaves"){printf "2"}} '`
if  [[ $a = "" ]]
then
	xdesktopwaves -quality 8 -rain 1 -colortheme 3 
else
	kill -9 `ps -aef | grep -i xdesk | awk ' {if ($8 == "xdesktopwaves"){printf $2}} '`
fi

```

Now lets move the file:

> sudo cp toggle_xdesktopwaves.bash /usr/bin/toggle_xdesktopwaves.bash

And make it work:

> sudo chmod 755 /usr/bin/toggle_xdesktopwaves.bash

Now right click on your desktop or panel. Choose the " Create (custom) launcher." 

For name put "xdesktopwaves" In the "command" blank put:

```
/usr/bin/toggle_xdesktopwaves.bash
```

Pick whatever icon you want, I attached the real one to this thread. To use it first download it to you home folder. Then untar it with this command:

```
tar -zxvf xdesktopwaves.xpm.tar.gz
```

Then move it to the right place with this command

```
sudo mv xdesktopwaves.xpm /usr/share/pixmaps/xdesktopwaves.xpm
```

And then select the icon.

There you go. You now have a on off button for these neat effect. I hope you enjoy, and spread the love to your friends and family.

---

### Post by frodon on 2006-01-04
I love this trick, thanks poofy ;)

---

### Post by lizardking on 2006-01-04
some screen?

---

### Post by Havoc on 2006-01-04
I love it, but it doesn't work without Nautilus drawing the desktop, meaning, no Water with E17...I'm sad. :(

---

### Post by ricka on 2006-01-04
wow nice stuff :cool: 
thanks poofyhairguy

---

### Post by poofyhairguy on 2006-01-04
[QUOTE=lizardking]some screen?[/QUOTE]

Added some to first post.

---

### Post by poofyhairguy on 2006-01-04
[QUOTE=Havoc]I love it, but it doesn't work without Nautilus drawing the desktop, meaning, no Water with E17...I'm sad. :([/QUOTE]


Hmmm...thanks for telling me. I will make this a Gnome guide then.

---

### Post by poofyhairguy on 2006-01-04
[QUOTE=ricka]wow nice stuff :cool: 
thanks poofyhairguy[/QUOTE]

No problem.

---

### Post by Mr_J_ on 2006-01-04
I'm pretty sure i followed everything you said. but i still get permission denied on using the launcher.
I should change the location of the .bash file to my home folder?

Anyway... I love the effects!

---

### Post by mcduck on 2006-01-04
That's a nice one. Thanks. 

Have you tried xpenguins too? It's also available in repositories. 

I also tried xsnow, but that doesn't seem to work, I suppose it doesn't like nautilus. It's a bit sad as some snow would have looked great on my January desktop ;)

---

### Post by ricka on 2006-01-04
hm strange that at -quality 9 it uses 100% cpu and at -quality 8 max 40% :\

---

### Post by fog on 2006-01-04
[QUOTE=Mr_J_]I'm pretty sure i followed everything you said. but i still get permission denied on using the launcher.
I should change the location of the .bash file to my home folder?

Anyway... I love the effects![/QUOTE]
Make it executable ;) 
I'm playing with mouse over half an hour....
Very nice **poofyhairguy** ;-)

---

### Post by Mr_J_ on 2006-01-04
That worked! Making it executable with "sudo chmod 755 /usr/bin/toggle_xdesktopwaves.bash" worked perfect!
Still keeps itself slow on moving windows, but who cares.

I'm trying all the eye candy I can until something busts.

---

### Post by poofyhairguy on 2006-01-04
[QUOTE=fog]Make it executable ;) 
I'm playing with mouse over half an hour....
Very nice **poofyhairguy** ;-)[/QUOTE]


Thanks, I added that.

---

### Post by snowjunkie on 2006-01-04
[QUOTE=Havoc]I love it, but it doesn't work without Nautilus drawing the desktop, meaning, no Water with E17...I'm sad. :([/QUOTE]

I assume it won't work in KDE then?

---

### Post by Lord Illidan on 2006-01-04
[quote=snowjunkie]I assume it won't work in KDE then?[/quote]

Works fine in Kubuntu - KDE here!!
Thanks poofyhairguy

---

### Post by kevcart3 on 2006-01-04
Works in XFCE too. It's very cool. :cool:

---

### Post by Gandalf on 2006-01-04
Very cool effects Thx poofyhairguy :D
xpenguins is also cool, xfishtank didnt work for me :(

---

### Post by poofyhairguy on 2006-01-04
[QUOTE=Gandalf]xfishtank didnt work for me :([/QUOTE]


Me neither. Anyone get xsnow to work?

---

### Post by fog on 2006-01-04
xfishtank or xsnow running in root window.
In gnome, nautilus shows the desktop. Go:
Applications-->System Tools-->Configuration Editor:
apps-->nautilus-->preferences and uncheck: show desktop.
Open the terminal and write: **xsnow** or **sudo xfishtank**.
Enjoy :) 
The screenshots are from Dapper, but it's the same for Breezy:

[http://www.ubuntuforums.org/gallery/showimage.php?i=1689&original=1&c=2](http://www.ubuntuforums.org/gallery/showimage.php?i=1689&original=1&c=2)
[http://www.ubuntuforums.org/gallery/showimage.php?i=1688&original=1&c=2](http://www.ubuntuforums.org/gallery/showimage.php?i=1688&original=1&c=2)

(sorry for my bad english)

---

### Post by daedalusman on 2006-01-05
Damn, this is some really cool stuff, more ways for me to impress my windows using buddies :D , thanks poofyhairguy another of your great guides.

---

### Post by Tab on 2006-01-05
[QUOTE=Havoc]I love it, but it doesn't work without Nautilus drawing the desktop, meaning, no Water with E17...I'm sad. :([/QUOTE]
E17 handles things a lot different from most DEs, and uses its own Evas canvases for drawing the background, etc. It's not surprising that this works for Gnome, KDE, XFCE, but not E17. Then again, an E17 module for this effect would probably be pretty trivial to write.

---

### Post by foxy123 on 2006-01-05
strange:
```
$ xdesktopwaves
bash: xdesktopwaves: command not found

```

although I've got it in Synaptic marked installed...

EDIT: for some wierd reason /usr/games was not in my path...

---

### Post by i3dmaster on 2006-01-05
Thanks man! This eye candy is sweet!

---

### Post by jannol on 2006-01-05
really cool, poof, you're keeping busy :D :D :D

---

### Post by Iandefor on 2006-01-05
Whew! For  minute there, I was afraid you'd gone and done a howto on making GNOME look like Aqua.

---

### Post by poofyhairguy on 2006-01-05
[QUOTE=Iandefor]Whew! For  minute there, I was afraid you'd gone and done a howto on making GNOME look like Aqua.[/QUOTE]

Not this guy. I just say no to fake Aqua themes.

---

### Post by poofyhairguy on 2006-01-05
[QUOTE=jannol]really cool, poof, you're keeping busy :D :D :D[/QUOTE]

Its a busy time of year for this stuff!

---

### Post by poofyhairguy on 2006-01-05
[QUOTE=i3dmaster]Thanks man! This eye candy is sweet![/QUOTE]

No problem.

---

### Post by Iandefor on 2006-01-05
[quote=poofyhairguy]Not this guy. I just say no to fake Aqua themes.[/quote] Good man. I can't stand Aqua.

---

### Post by xtacocorex on 2006-01-05
This is amazingly cool.

Now if I could only make it my screensaver...

---

### Post by rjwood on 2006-01-05
Another bookmark from poofyhairguy---I am going to have to give you your own catagory.

Thanks a lot---great stuff!!!!!!! Our desktops would be so bland without you;)

---

### Post by poofyhairguy on 2006-01-05
[QUOTE=rjwood]Another bookmark from poofyhairguy---I am going to have to give you your own catagory.

Thanks a lot---great stuff!!!!!!! Our desktops would be so bland without you;)[/QUOTE]

Thanks. I'm glad I am eating CPU cycles all over the place.

---

### Post by Gray. on 2006-01-06
This is really nice. Playing with the mouse has never been so fun. lol

---

### Post by Lord Illidan on 2006-01-06
It does slow down my desktop a bit, though. Is it because I am using KDE or is the same for everyone. Does it use open gl?

---

### Post by benplaut on 2006-01-06
that is so frikkin cool!

it's a bit hard to read conky, though... and takes up alot of cpu. 

conclusion: good for showing off :P

---

### Post by poofyhairguy on 2006-01-06
[QUOTE=Lord Illidan]It does slow down my desktop a bit, though. Is it because I am using KDE or is the same for everyone. Does it use open gl?[/QUOTE]

No, I think it just uses the CPU. Hence the slowness.

---

### Post by poofyhairguy on 2006-01-06
[QUOTE=benplaut]
conclusion: good for showing off :P[/QUOTE]

Exactly.

---

### Post by ubuntu_demon on 2006-01-07
great stuff!

---

### Post by mstlyevil on 2006-01-07
Awesome Poofy. Thanx for the how to on this.

---

### Post by poofyhairguy on 2006-01-07
[QUOTE=mstlyevil]Awesome Poofy. Thanx for the how to on this.[/QUOTE]

No problem. We each do our part, right?

---

### Post by ardchoille on 2006-01-07
This is awesome! Thanks poofyhairguy :)

---

### Post by gabhla on 2006-01-08
Oh, this great stuff...thanks.

---

### Post by mstlyevil on 2006-01-08
I noticed that the hit on my RAM was minimal but the CPU is running between 50-60% with my settings as follows.

Quality-8
color-2
Rain-3

I actually think this is pretty good considering the high quality setting. I just love my AMD Athlon64 3200. My old Athlon 2500 would have pegged out even overclocked at a 3200.

---

### Post by poofyhairguy on 2006-01-08
[QUOTE=mstlyevil]I noticed that the hit on my RAM was minimal but the CPU is running between 50-60% with my settings as follows.

Quality-8
color-2
Rain-3

I actually think this is pretty good considering the high quality setting. I just love my AMD Athlon64 3200. My old Athlon 2500 would have pegged out even overclocked at a 3200.[/QUOTE]

Quality 9 seems to be what kills it. At quality 9 one of my cores (not a multicore app) is completely pegged!

---

### Post by ubuntu_demon on 2006-01-08
This are my settings :

xdesktopwaves -quality 8 -rain 1 -opaque -storm 1

But maybe it's more beatiful with some blue / water wallpaper (without the opaque). Does anyone have found a nice one ?

---

### Post by AMCDeathKnight on 2006-01-09
worked fine and great for me thanks alot

---

### Post by poofyhairguy on 2006-01-09
One thing I noticed: gdesklets don't play the best with this. Well...some do.

Just warning yall.

---

### Post by leech on 2006-01-11
Either xdesktopwaves is really old, or Enlightenment DR13 had something very similar.  Because I recall playing around with something like this back when I first started using linux.  Actually I think it was originally called xripple.

Anyhow, it's still really cool :D

Speaking of Enlightenment DR13, it's too bad Metacity stinks, otherwise we could have some good eye-candy like that.  It kind of sucked on lower resolution screens, but now that I'm running 1600x1200, it would be damn sweet!

Couldn't find a real screenshot, but here's a wannabe clone of DR13's theme for Window blinds.

[http://pcdesktops.emuunlim.com/wb21-25.shtml](http://pcdesktops.emuunlim.com/wb21-25.shtml)  Just scroll down to E13

Leech

---

### Post by Redeyes_Gambit on 2006-01-12
Woa, this is sweet! My first candyhack. Thanks poofyhairguy! Who knows maybe I'll try adding a GRUB a graphical background next. Courage must be built a little at a time lol.

Oh, a note to those of us with wimpus minimus CPUs, this thing still runs, and runs great on lower quality settings. I have a 350 mghz cpu with 392 ram, and a TNT2 agp 2x card with 32 megs of ram on it (and the standard Ubuntu driver. Not the official Nvidia driver.) At quality lev 4 it runs great (at pegged cpu lol, but no lag). Just figured I'd let anyone who's reading this thread but is concerned about not having enough power know that. After all, even those of us who have older hardware deserve eyecandy too. :D

---

### Post by stalefries on 2006-01-13
I have a 500 mhz CPU, 256 ram, and it runs fine at normal settings, except when moving windows. It takes about half a sec to do it then. Otherwise, great!

---

### Post by stalefries on 2006-01-28
Also, instead of putting that whole complicated line starting with 'kill', it'd be easier and simpler to do "xdesktopwaves -end".

---

### Post by Gilson on 2006-01-28
Very nice, thanks ;) .

---

### Post by cosimo on 2006-02-09
Hello,
 I LIKE IT!!
 Also, after you make the initial on/off button, you can add 
more xdesktopwaves commands into the applications menu editor, as if adding a  new application, using any xdesktopwaves command combinations , turning them on in the menu and turning them off with the original button, since only one incident of xdesktopwaves can run at a time. 
Very cool!
 Thanks
 Coz

---

### Post by tlaloczint on 2006-02-09
wow!! I bow to you this is so sweet my windows budies are all jealous!
wohooooo! \\:D/ \\:D/ \\:D/ \\:D/ \\:D/

---

### Post by JustRandomName on 2006-02-17
How do you get this working with conky?

Or maybe the question should be: How do you get conky to work with this?

---

### Post by quadomatic on 2006-02-19
hmmm, i do sudo apt-get install xdesktopwaves, but then when i type xdesktopwaves in the terminal, it says

bash: xdesktopwaves command not found. wats goin on?

---

### Post by jannol on 2006-02-19
apt might have failed installing try reinsta&#314;l it

---

### Post by majikstreet on 2006-02-19
this is nice.. I was suprised that I could do it with my integrated graphics..

sudo apt-get install xpenguins
then do that too.. funny !
sudo apt-get install xfishtank
I did that but for some reason it didn't install lol, I'm going to try it again.

---

### Post by poofyhairguy on 2006-02-20
[QUOTE=majikstreet]this is nice.. I was suprised that I could do it with my integrated graphics..
[/QUOTE]

Its all on the CPU I think.

---

### Post by majikstreet on 2006-02-20
ahh.. well shows what I know :D

---

### Post by ChaosEsper on 2006-02-21
Hey guys, this is really my first linux OS, so bear with possible idiot comments, lol.  I typed in the first command: sudo apt-get install xdesktopwaves , and I get this response: 
Reading package lists... Done
Building dependency tree... Done
E: couldn't find package xdesktopwaves

so, did I do something wrong, or what?

---

### Post by poofyhairguy on 2006-02-21
[QUOTE=ChaosEsper]Hey guys, this is really my first linux OS, so bear with possible idiot comments, lol.  I typed in the first command: sudo apt-get install xdesktopwaves , and I get this response: 
Reading package lists... Done
Building dependency tree... Done
E: couldn't find package xdesktopwaves

so, did I do something wrong, or what?[/QUOTE]

You have to enable the Universe. I always just assume that people do that in my guides.

---

### Post by egon spengler on 2006-02-22
ChaosEsper, [read this.](https://wiki.ubuntu.com/AddingRepositoriesHowto) It doesn't really explain what repositories are, just how to enable them, if you want to know what they are (and you probably should) google will explain it all

---

### Post by alfonz on 2006-02-22
[QUOTE=fog]Make it executable ;) 
I'm playing with mouse over half an hour....
Very nice **poofyhairguy** ;-)[/QUOTE]

haha, its adictive isn't it?


Thanks Poofyhairguy, Cheers!!!

---

### Post by WheelDweller on 2006-02-27
Ya know what would really set this off?  It would even legitimize it as something more than mere eyecandy, too...

If you could somehow link weather service information (like the gnome-applet or other favorite source) to have it come on when it's scheduled to rain.

Kinda like being in Nethack, and having the game recognize actual moon phases.  It just adds something for me, ya know?

---

### Post by white_tiger_daniel on 2006-03-08
umm just 1 prob- it comes up with nothing when I type xdesktopwaves at my terminal and I'm running gnome whick might have been the problem :-k

---

### Post by casper26 on 2006-03-12
Nice Post! Thanks!  =)

---

### Post by blackjack6.21.91 on 2006-07-05
awesome!!
there are more options.  just do
> man xdesktopwaves
awesome!!

---

### Post by seshomaru samma on 2006-07-07
hI
I've followed the instructions on the first post carefully and everything seems to be running smooth but I want to ask one question:
if i want to stop the aquatic effect what can i do (except log-out)
i tried ctrl-c but it doesn't work.
thanks

---

### Post by Lunar_Lamp on 2006-07-07
If you started it from inside a terminal, you need to select the terminal window and hit 'ctrl+c' in the terminal window.  Ctrl+c is a standard shortcut to kill an application running from within a terminal window.

---

### Post by seshomaru samma on 2006-07-07
Thanks
I started it from an icon
I now discovered that clicking again on the icon stops it so ...problem solved...

---

### Post by jannol on 2006-07-07
Are you sure cause I don't think there is such function in xdesktopwaves builtin so if it really does work as you say, either I am wrong or you have some toggle script that launches xdesktopwaves or nothing makes sence until you understand it LOL :-P

If you do find out that it doesn't work as you say, you could use a toggle script that does the job.

---

### Post by IrishGangsta on 2006-07-09
hey there, I just did this neat little trick and it was awesome!!
Only mine is blood red, but this is great, i been looking for an animated desktop and this isnt too bad. One day i hope to create and animate my own background but hey, this is awesome!

good looks

---

### Post by avender on 2006-07-09
I'm sorry, but the screen shots are not loading...

---

### Post by Metroid48 on 2006-08-03
Okay, this is SO cool! Works like a charm, but I would suggest these options:

xdesktopwaves -t -i -si 4 -vs 2 -rain 2 -colortheme 3 -quality 6 -storm 3

It's a little CPU intensive, but you just need to change quality for that. The -t adds transparency and gets rid of desktop icons while running. I found them to look glitchy. -i forces idle mode to actually work. -si changes sky intensite (0 - 10, 10 means light reflection from virtual 'sun' is stronger) and -vs changes the viscosity (1-5).

Anyway, great guide! I also love xpenguins, but that's REALLY glitchy. I can't get xFishtank or Xearth to work. But still, this is so cool.

-Metroid48

PS- Thanks for bringing my CPU to 100% strain and making me spend hours on eyecandy foolin'!:D Love all these eyecandy threads!

---

### Post by Darrious on 2006-08-03
I typed sudo apt-get install xdesktopwaves and it came up with this.

```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xpenguins

```

Shouldn't it be there?

---

### Post by _simon_ on 2006-08-03
As the screenshots in the first post no longer work, can someone upload some more please?

---

### Post by aroswald1977 on 2006-08-04
Yeah, it is a neat little FSA, thanks for the button script.
Colorscheme 2 works great with my green theme, and my roomate is saying OMG! WTF! where did you get that?

---

### Post by argie on 2006-08-05
This works great. It's really nice.

However I'm using one of those terminals in the background that look real snazzy from [HOWTO: Terminal as the desktop background.](http://ubuntuforums.org/showthread.php?t=202249&highlight=devilspie).
Is there a way to make xdesktopwaves run "on top" of this window? Currently, the ripples just go around it. 

Thanks again, this is just beautiful.

---

### Post by Darrious on 2006-08-07
It's the greatest. Better then anything I've ever seen.

---

### Post by kvonb on 2006-08-13
Screenshot for _simon_

The screenshot doesn't really do it much justice, it looks a LOT better on the screen for some reason!

EDIT: you have to make sure you zoom in on that screenshot otherwise it looks terrible!

---

### Post by AbGilley89 on 2006-08-13
Is this any way we could get some more screenshots? The orig ones don't work anymore.

---

### Post by gruffy-06 on 2006-08-13
A pretty maniac. Far better than other configs, incl. mine! :-D

---

### Post by muz1 on 2006-08-13
It needs some work to smooth it out but as a concept, it is awesome.
This is where it is at people.
Cheers
muz

---

### Post by Rashid584 on 2006-09-23
> rashid@rashid-desktop:~$ sudo apt-get install xdesktopwaves
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xdesktopwaves
rashid@rashid-desktop:~$

:S

-Rashid

---

### Post by grucho on 2006-10-16
hey everyone...i still have a lot of problems with tthis plug-in...when i write sudo apt-get... the terminal is asking me for a passwor...i just insert my  sistem password and after nothing is happening...when i try to write xdesktopwaves the console is saying that  command not found...what i can do?!??! plz!

---

### Post by hikaricore on 2006-10-16
you need to have the dapper/universe repositories enabled to install xdesktopwaves

add the line:
```
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse main restricted
```

to your sources.list

```
sudo gedit /etc/apt/sources.list
```

and that should do the trick...as well as giving you access to nearly every extra package known to man lol

---

### Post by grucho on 2006-10-18
thanks man! but i still have a big problem! sorry but im a nubs with linux...where should i write this line...because if i try to write it in the console is not working...where i must write it? im getting crazy!!! ](*,) ](*,)

---

### Post by chakkid on 2006-10-18
Totally awesome! From what i see:). I'm going to try it out when i go home.

---

### Post by dannyboy79 on 2006-10-18
you're links of the screenshots don't show you screenshots. they show you some kind of weird ubuntu forum home page that's all white and not any screenshots. sounds cool but i'd like to see it first. thanks for the info none-the-less

---

### Post by sYs^ on 2006-10-20
The correct links are these:

[http://ubuntuforums.org/gallery/showphoto.php?photo=1681&limit=recent](http://ubuntuforums.org/gallery/showphoto.php?photo=1681&limit=recent)
[http://ubuntuforums.org/gallery/showphoto.php?photo=1682&limit=recent](http://ubuntuforums.org/gallery/showphoto.php?photo=1682&limit=recent)
[http://ubuntuforums.org/gallery/showphoto.php?photo=1683&limit=recent](http://ubuntuforums.org/gallery/showphoto.php?photo=1683&limit=recent)

It wasn't a big deal to figure out what's wrong. :p

---

### Post by grucho on 2006-10-21
thanks everyone but i still have 2 problems...how can i use it with the 3d desktop? is possible? the water effect with a radeon 9600pro is working? because on my pc is not working!

---

### Post by BigWillyT on 2006-10-27
Thanks a ton for this very cool guide that adds yet one more really cool visual to an already awesome desktop!

---

### Post by d3v1ant_0n3 on 2006-11-09
Just given this a whirl on top of Beryl, and it looks great- I can't use the 'water' plugin with beryl due to a lack of Pixel Shaders on my graphics.

Unfortunately, due to the CPU overhead, it's not really suitable for fulltime use.

However, it WOULD make a nice screensaver replacement (GL screensavers go wonky on me with beryl) Is there any way to adjust the script for this so when it's run, it serves the same purpose as locking the desktop? I.e. click the icon to run it, cue the pretty water and locking, and upon mouse movement/keyboard input, you get a password entry box, enter password, turn off effect?

---

### Post by shearn89 on 2007-01-10
Wow! awesome - cheers for the info...

---

### Post by Kevf on 2007-02-12
Installed the package, but the command:

xdesktopwaves

doesn't respond at all :confused:

---

### Post by sefkaz on 2007-02-12
is it compatible with beryl ??

-ron-

---

### Post by ltk5 on 2007-02-12
have tried xpenguins.. love them, they're so cute. I still have to try the aquatic desktop. Thanks for the tut :D

---

### Post by phoqueyoo on 2007-02-12
This is a fairly old program. Does anyone think they can modify the code to make it truly transparent?

Thanks.

---

### Post by Rabbit_Alex on 2007-02-13
Programs like this (and new games) are what make me want to build a new computer and replace this two year old laptop.

Has anyone tried using this on a top-of-the-line PC with all the settings at maximum?
:popcorn:

---

### Post by kobewan on 2007-02-13
> **Kevf said:**
> Installed the package, but the command:

xdesktopwaves

doesn't respond at all :confused:

Yeah, I **thought** that was happening on my computer as well.

Actually, this program has no effect unless the desktop is actually visible. Run the the command, and then minimize all your windows.

---

