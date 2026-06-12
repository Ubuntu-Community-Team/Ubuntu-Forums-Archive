---
title: "CLIX for UBUNTU 7.04 - bling bling!!!"
date: 2007-07-03
forum: Programming Talk
---

### Post by xavier_r on 2007-07-03
This is experimental software...

I love using the command line...
So using the power of "screen" and php/ncurses i made a simple interface for launching and managing some commonly used apps from the command line...

Try and tel me how do you like it... :D
If you dont like the command line, still give it a try
I'm sure you'll start liking it...

I made the following combination:
     File Manager -> vfu (i like it) if u want mc just change the source code in check.php and clix.php
     Music Player -> orpheus 
     Spreadsheet -> slsc
     Browser -> links2
     Email -> elmo
     Chat -> centericq (great software, yahoo, irc, etc. all supported in text-mode)
     ASCII Art program -> cadubi
     Calendar App -> calcurse
     Address Book -> abook
     Screensaver -> cmatrix (awesome!!!)
     System  Statistics -> saidar

This is sort of a very static version right now... But later I planto add customized installation and customized menu... ;)

So Enjoy, and give me your feedback!!! :D

---

### Post by bobbocanfly on 2007-07-03
Lol! That looks very cool. Im sure i have seen something like it before (some guy did a post on "A Day Without X" and had all of his different Curses apps running in different windows, all written in curses). 

Next step turning it into a tiny linux distro for power users ;)

---

### Post by xavier_r on 2007-07-03
Thanks lol...
Did you try it ? Did it run smoothly?

---

### Post by raja on 2007-07-03
Hi,
I installed it and tried it. As I see it is a script to install and combine different curses based applications. I think it is a very exciting idea - though not being used to them, I found using them frustrating. 
But it definitely is a good alternative environment to work in and I will try to get used to them again. As far as the installation and things, it was smooth. May be good if the user can select the applications to install.

---

### Post by xavier_r on 2007-07-04
> **raja said:**
> May be good if the user can select the applications to install.

Yea I am developing that
-> Custom menu
-> Choice of application

curses based applications are frustating for new users , but once you get used to the strokes, its even faster than GUI

---

### Post by Nythain on 2007-07-04
oh i cant live without my curses apps... this bit of software appears interesting enough... i would try it out, but i dont like some of the software it uses (im an mpd/ncmpc and mc man myself) and i already have all the apps i need running on my desktop.

if you could find a way to incorporate lftp, rtorrent, and aptitude without any options (opens it up in interactive mode) would be even better, just some ideas

---

### Post by xavier_r on 2007-07-05
> **Nythain said:**
> just some ideas

Thanks dude
yea... I'm trying to come up with that...

---

### Post by xavier_r on 2007-07-06
Just a notice...
I have started this project on SourceForge... to further enhance CLIX and to make it usable by normal users...

The name has been changed... because Clix was already there...
Its now called **ScreenFace**...
[B]
Screen[/B] for GNU Screen
**Face** for Interface

If you are interested you can contribute to the project...
I am learning sourceforge at the moment... 
So instead you can mail me at [email]flac.ubuntu@gmail.com[/email]

You can still visit the sourceforge page at:
[https://sourceforge.net/projects/screenface](https://sourceforge.net/projects/screenface)

[IMG]https://sourceforge.net/dbimage.php?id=131023[/IMG]

---

### Post by xavier_r on 2007-07-14
ScreenFace for UBUNTU is now downloadable from sourceforge...
Get the latest version from there...
[https://sourceforge.net/projects/screenface](https://sourceforge.net/projects/screenface)

---

### Post by Note360 on 2007-07-14
Cool. Sorry about criticizing you earlier.

Oh and how about Clibuntu as a name

---

### Post by xavier_r on 2007-07-16
> **Note360 said:**
> Cool. Sorry about criticizing you earlier.

Oh and how about Clibuntu as a name

Did u try the latest version out?

I like the Criticism, np... :guitar:
And Clibuntu is a nice name...
But ScreenFace is more likely to work on any linux...
maybe Clibuntu could be the name for "Command Line Ubuntu" --- a separate distro...

Hey Note360, you interested in developing this?
My goal is to a get a creally cool and workable interface so that people get to know and love the command line...
I need to get more users to respond to this software... to actually make a software based on user demands...

---

### Post by Note360 on 2007-07-16
> **xavier_r said:**
> Did u try the latest version out?

I like the Criticism, np... :guitar:
And Clibuntu is a nice name...
But ScreenFace is more likely to work on any linux...
maybe Clibuntu could be the name for "Command Line Ubuntu" --- a separate distro...

Hey Note360, you interested in developing this?
My goal is to a get a creally cool and workable interface so that people get to know and love the command line...
I need to get more users to respond to this software... to actually make a software based on user demands...

I wouldnt mind developing actually, however my PHP isn't the best I havent really gone out of website design in which I mostly write th CSS HTML and implement php libraries and my friend does the heavy PHP work. I can try.

---

### Post by Note360 on 2007-07-16
oh btw I fixed install.php. It wasnt working for me at first it wouldnt do the apt-get all I had to do was add a -y to the command

sudo apt-get -y install applications

Works like a charm

---

### Post by Note360 on 2007-07-16
I know triple posts suck, but I made a new and improved install script (in bash though). It asks you for what applications you want the aptitude install actually works. I do not have an all default command yet in it. I will upload it soon.

EDIT: Added the install.sh

[http://zephyrwood.org/ScreenFace/install.sh](http://zephyrwood.org/ScreenFace/install.sh)

Features:
- Easy Wizard-Like (not really) customized install
- install.sh default or install.sh -d installs the defaults
- If you hit enter on an entry it will pass over it and set it to the default
- Added Text Editor with nano as the default

---

### Post by xavier_r on 2007-07-16
Great,,,
I understand bash scripts properly, but often make syntaz errors while writing, so  I chose php :)
But i would prefer bash than php for installation...
Great to have someone working for ScreenFace...

I have read many blogs and seen that people who adore command line, always talk of GNU Screen...
I think this software might have some potential...
So better make it mature and complete it...

Some update:
Right now i have chosen elinks as the default browser, because 
* it gives users the option to choose applications to open remote files...
So if, suppose i needed to view a image... I would open it from elinsk, enter zgv as the image file handler, and we coul dview imaes in text-mode browsing...

Currently working on that...
And there are plans remain to make rpm, deb, packages of ScreenFace... so that ScreenFace runs on every Linux...

---

### Post by Note360 on 2007-07-16
> **xavier_r said:**
> Great,,,
I understand bash scripts properly, but often make syntaz errors while writing, so  I chose php :)
But i would prefer bash than php for installation...
Great to have someone working for ScreenFace...

I have read many blogs and seen that people who adore command line, always talk of GNU Screen...
I think this software might have some potential...
So better make it mature and complete it...

Some update:
Right now i have chosen elinks as the default browser, because 
* it gives users the option to choose applications to open remote files...
So if, suppose i needed to view a image... I would open it from elinsk, enter zgv as the image file handler, and we coul dview imaes in text-mode browsing...

Currently working on that...
And there are plans remain to make rpm, deb, packages of ScreenFace... so that ScreenFace runs on every Linux...

Sounds cool. I will continue to better the installation script and I hope it becomes the preferred method of installation purely for the easy configuration (or at least I think it is easy).

I like lynx as a web browser purely because it is straight forward. However I think I will try to use elinks. (At the moment I am using Swiftweasel though). Also, I am going to try Elmo but I used to use mutt. I believe Elmo is no longer being maintained. For music player I prefer cplay and for File Manager I actually prefer the shell, but I have been experimenting with mc and vfu. Raggle is great. 

Also I set nano to the default editor because, it is simple, generic and no flame wars are usually involved (if I chose vim flame war, emacs flame war, any emacs offspring flame war).

Everything else is great except the Calendar doesn't work for me. (which isn't your fault)

Also maybe we should include irssi as a default IRC client?

Finally, I will throw my irc client into freenode.net #screenface

---

### Post by Motoxrdude on 2007-07-16
DO you want me to add a gui to this? Maybe we could make it so you choose whether you want to use in text mode or with a gui. let me know.

---

### Post by Note360 on 2007-07-16
> **Motoxrdude said:**
> DO you want me to add a gui to this? Maybe we could make it so you choose whether you want to use in text mode or with a gui. let me know.

I am not really part of this project but I thought the whole idea was for this to be a text mode thing. I could be wrong. Cool thing about this is that the code is quick and managable.

---

### Post by Note360 on 2007-07-16
I added one more feature (simple). I changed the help menu from vi to less. Why was it vi in the first place?

less is a file reader with out writing abilities it is kinda like more and resembles what is used in the man pages. I believe it is default in installation.

---

### Post by xavier_r on 2007-07-17
> **Note360 said:**
> Sounds cool. I will continue to better the installation script and I hope it becomes the preferred method of installation purely for the easy configuration (or at least I think it is easy).

I like lynx as a web browser purely because it is straight forward. However I think I will try to use elinks. (At the moment I am using Swiftweasel though). Also, I am going to try Elmo but I used to use mutt. I believe Elmo is no longer being maintained. For music player I prefer cplay and for File Manager I actually prefer the shell, but I have been experimenting with mc and vfu. Raggle is great. 

Also maybe we should include irssi as a default IRC client?

Finally, I will throw my irc client into freenode.net #screenface

[B]
I think, each individual person needs to have his own customized thing...[/B]
Like you prefer mutt and I elmo...
So what we can do is, create a set of utility applications running on command line, and give their description while installing, so that the newbie user gets to know what he is installing...

> Everything else is great except the Calendar doesn't work for me. (which isn't your fault)
Haha, the calendar didnt work for me either...
Actually, what happens is to add apptmts. we have to do Ctrl-A, and Screen uses Ctrl-A as a control operator... So we also need to include only those apps which dont conflict with Screen...


OK, irc.freenode.net #screenface... 

Some info about software I intend to use(besides what you already know):
File Manager  -> clex
Musicp Player -> cmus or orpheus (i like orpheus, for its ismple interface)
Programming IDE -> Motor
IRC -> rhapsody or BitchX

And I am trying to enable Framebuffer with Mplayer to enable watching videos... But crap it doesnt work...!!!!
See if you can make it work...
Then I will do an automated install for that...

And if you can get yourself an account at sourceforge?
Its easier to maintain it that way...

---

### Post by Motoxrdude on 2007-07-17
> **Note360 said:**
> I am not really part of this project but I thought the whole idea was for this to be a text mode thing. I could be wrong. Cool thing about this is that the code is quick and managable.

LMAO, yeah that crossed my mind about 5 minutes **after** i made the post ;)

---

### Post by xavier_r on 2007-07-17
> **Motoxrdude said:**
> DO you want me to add a gui to this? Maybe we could make it so you choose whether you want to use in text mode or with a gui. let me know.

How would you add GUI?
Are you talking of a similar GUI menu?

Any mockup ScreenSHots?

---

### Post by Motoxrdude on 2007-07-17
> **xavier_r said:**
> How would you add GUI?
Are you talking of a similar GUI menu?

Any mockup ScreenSHots?

Here is an example. I can add another column to make it more like the text version. Anyways, here you go.

EDIT: The "check.php"'s integration pretty much sucks. Anyways, i converted the check.php to bash so it integrates a lot better. Ill be adding a simple gui later for us with guis, but still like using text-based apps.

---

### Post by xavier_r on 2007-07-17
Dude, looks good :)
But its just a simple menu like thing...

Besides as for project goals...
Did you look at the project main site:
[https://sourceforge.net/projects/screenface](https://sourceforge.net/projects/screenface)[I]
 A console based interface build with PHP/Ncurses and based on the power of GNU Screen. Designed to be appealing as well as functional for the end-user. Aim is to provide an appealing interface for launching and running command line apps.[/I]

Its GNU Screen we are trying to exploit...
So this project will be command line...
Unless ofcourse we go ahead and make a separate window manager...
But thats a different story...

Also, curently check.php has been replaced by install.sh

---

### Post by Motoxrdude on 2007-07-17
> **xavier_r said:**
> Dude, looks good :)
But its just a simple menu like thing...

Besides as for project goals...
Did you look at the project main site:
[https://sourceforge.net/projects/screenface](https://sourceforge.net/projects/screenface)[I]
 A console based interface build with PHP/Ncurses and based on the power of GNU Screen. Designed to be appealing as well as functional for the end-user. Aim is to provide an appealing interface for launching and running command line apps.[/I]

Its GNU Screen we are trying to exploit...
So this project will be command line...
Unless ofcourse we go ahead and make a separate window manager...
But thats a different story...

Also, curently check.php has been replaced by install.sh

Maybe we could just split off and make a GUI application like this. One window, able to launch firefox, music player, etc. and have tabs between them. That's what i am thinking of doing this summer. Wanna join the bandwagon of one? ;)

---

### Post by Note360 on 2007-07-17
> **Motoxrdude said:**
> Maybe we could just split off and make a GUI application like this. One window, able to launch firefox, music player, etc. and have tabs between them. That's what i am thinking of doing this summer. Wanna join the bandwagon of one? ;)


I would but I want to see where this ScreenFace project goes first. I've been using it lately as a mainstay thing (for one day). I have to say its great but somethings annoy me.

1. The inability to edit
2. The inability to sort
3. The randomly placed blinking cursour
4. The time doesnt auto update
and some other things.

My only problem is I am having trouble actually using php. Also should we use SourceForge's cvs (why didnt we go to launchpad or google code?). Also my sourceforge is cwoodall. Also I think ultimately we should move this over to a faster compiled language like C. As of the moment you need to install php5-cli to run this and that isn't default on ubuntu (should I add that to the apt-get line?)

Edit: The Calendar works ^A isnt needed just hitting a has the same effect

---

### Post by xavier_r on 2007-07-17
> **Note360 said:**
> 
My only problem is I am having trouble actually using php.


For PHP in web i have had experience... But in CLI i am also new...
I chose, php/ncurses... because its a script... and a curses based app...
But still i had to learn ncurses, i am new to it...
But i chose it since it is easily customizable...

I dont know about other languages that can be used for Ncurses as a script...
I've heard Ruby maybe... but i dont know for sure...
Choose a language thats scripted...

Here's a basic php/ncurses tutorial... I find it mroe easier than C/curses.h...
[http://devzone.zend.com/article/1083-Using-Ncurses-in-PHP](http://devzone.zend.com/article/1083-Using-Ncurses-in-PHP)

> 
1. The inability to edit
2. The inability to sort
3. The randomly placed blinking cursour
4. The time doesnt auto update

Dont worry;) if we get our major things done...
We'll have minor things to sort out later...
Either way... we wont have as many bugs as Windows :lol:

> 
Also should we use SourceForge's cvs (why didnt we go to launchpad or google code?). Also my sourceforge is cwoodall.
Google Code, and Launchpad... affirmative with that...
To be true, right now i am more focused  on actually getting all user requirements sorted out... and program bugs fixed... Sourceforge is just a place to have a common download and website... Not CVS...
I dont want to open up many more... just work on ScreenFace for now...
If u can do open up there...

> Also I think ultimately we should move this over to a faster compiled language like C. As of the moment you need to install php5-cli to run this and that isn't default on ubuntu (should I add that to the apt-get line?)

Yea... sure...for apt-get...
For C i disagree... i find it much harder...
Even though I am quite experienced with it more than PHP...
I'm gonna check out Ruby, Python, etc... languages...
I'll see which language...

> 
Edit: The Calendar works ^A isnt needed just hitting a has the same effect
It didnt lol!!!

---

### Post by xavier_r on 2007-07-17
JUST TRY THIS OUT

create this file: /usr/share/xsessions/xterm.desktop
[B]
[Desktop Entry]
Encoding=UTF-8
Name=xterm
Comment=ScreenFaceWM
Exec=xterm -e "/usr/bin/ScreenFace"
Icon=
Type=Application[/B]

Login into xterm session through gdm...
Viewing movies is much easier now... No framebuffer required...

This is just some fun experiment... where ScreenFace is a window manager like ratpoison... only much easier :)

---

### Post by Note360 on 2007-07-17
lol cool. ill figure it out (how to make the files and do it all auto magically. Then set it up on install as a windows manager. Also now I am working on an addon that when you type ? during installation when it asks you what app to use it lists a few applications and my bad descriptions of them.

---

### Post by Note360 on 2007-07-17
it jsut says. XServer cannot launch xterm

---

### Post by xavier_r on 2007-07-17
> **Note360 said:**
> it jsut says. XServer cannot launch xterm
is xterm installed? did u create the file with root access? it worked fine on mine,,,

**3. The randomly placed blinking cursor** is now gone...
Plus, added, aptitude as software manager...
and terminal is now bash...
Check attachment...

---

### Post by Note360 on 2007-07-17
heh. cool. Ill jsut move over my installation upgrades I guess. lol. also didu change the help view from vi to less?

---

### Post by xavier_r on 2007-07-17
> **Note360 said:**
> also didu change the help view from vi to less?
hehe i forgot to attach that...
But its done... in v1.1

---

### Post by Note360 on 2007-07-17
get on the irc. irc.freenode.net #screenface

---

### Post by Note360 on 2007-07-17
Updated the installation script with.

* ? brings up a list of suggested applications
* Changed a few defaults to the ones xavier_r wants

---

### Post by Note360 on 2007-07-17
[http://www.zephyrwood.org/ScreenFace/install.sh](http://www.zephyrwood.org/ScreenFace/install.sh)

---

### Post by xavier_r on 2007-07-18
Bugs:
If I press ? on first time... it displays a list of options...
on 2nd time is ? is pressed, it accepts ? as an app...
and it does "sudo apt-get install ? ? ? ? ...."
that shouldnt happen...

Put a while statement or something instead of "if" to make sure that doesnt happen...

---

### Post by xavier_r on 2007-07-18
Modified install.sh. The following have been corrected...
Some typo errors...
Some formatting stuff for visual appeal...
Removed bash from file manage list... because our script is a bash script, and one already needs bash to install it...

and replaced "?"... with a more clear syntax...

---

### Post by xavier_r on 2007-07-18
New apps:

pytone - text based juke software...
dav - simple editor
jered - editor originally made by IBM as E

---

### Post by Note360 on 2007-07-18
Ha sorry. I was going to fix all that stuff but I was busy so I juat tried to push it out. Well idk if you need me any more. I am going to fix the script up a bit more now. Sorry about any typos. I am going to make it easier by setting the defaults as variables (why didn't I think of that before). Basically I am just going to make it more scalable than it currently is.

---

### Post by xavier_r on 2007-07-18
Hey np

I tried ScreenFace today acting to be a newbie... on a purely cli...
STEPS:
I installed UBUNTU 7.04 and chose "install a command line"
After installation I logged in, and did
$ sudo apt-get install elinks

i downloaded ScreenFace-1.1.tar.gz through elinks... (i had added php5-cli to install.sh)
I installed it...
and it worked
perfectly...!!!

great day... eh??? :lol:

---

### Post by Note360 on 2007-07-18
Cool.

I made some more enhancements to install.sh, but mostly from the developer side. Aswell as adding the new apps.

---

### Post by Note360 on 2007-07-18
Check out this name I came up wiht


cFace - Cface For Alien Centaur Engineers

woot. cface really meaning command line interface

---

### Post by xavier_r on 2007-07-18
Hehe,
CFace is a nice name... for a unix command...
But keep in mind.... GNU Screen is the base environment...
This program wont be anything without that...

---

### Post by xavier_r on 2007-07-18
**The time bug is solved now... **:guitar:
Check out the latest version... it looks beautiful...
Install it using...
$ bash install.sh

---

### Post by xavier_r on 2007-07-18
Latest versions of ScreenFace will be available here...
[http://screenface.66ghz.com](http://screenface.66ghz.com)
So that packages are easily accesible from text browsers...

---

### Post by xavier_r on 2007-07-21
**ScreenFace 1.2 released**
New Features:
* Run Command, so no need of opening up a terminal, when running programs
  Especially programs which need an argument to run, which screenface cannot handle, like for example, jered
* Removed seconds from time format, so old terminal screens can handle the interface without flickering
  As displaying seconds means to refresh the screen each time
* Plus various Programming bugs removed

Check out here...
[http://screenface.66ghz.com](http://screenface.66ghz.com)

---

### Post by Note360 on 2007-07-21
haha cool. Sorry I stopped helping out I had some stuff to do. Just tell me if their are any tasks u want me to do

---

### Post by xavier_r on 2007-07-21
> **Note360 said:**
> haha cool. Sorry I stopped helping out I had some stuff to do. Just tell me if their are any tasks u want me to do

How r u buddy ? :lolflag:
Did u like the changes?
Seen the latest version?

This guy named, Jared emailed me, and he wants to make this interface as a default for his CLI distro...
He is building a CLI-only distro... So we can make ScreenFace a real f*cking piece of software now...
He also wants to help us build this... I am still awaiting his email.. I'll tel you as soon as I get it...
We can collaborate with each other...

And also I have something for you to do...
Make a list of all command line apps, from synaptic(universe multiverse enabled)...
then that way we can have a list of software, which we will know we can use...
That means everything starting from nethack to cdw..., there are so many i dont even know...
Make a list and categorize them into categories like games, system, internet, editors, etc.

This list will help us, and our intended users a lot... and give us an idea about what can be included int CLI right now... But, before doing that task, first decide (because its gonna be a big task), do we really need such a list?  What do you think?

---

### Post by Note360 on 2007-07-21
that is alot of work, but ill try i guess. However, thats alot of work.

---

### Post by xavier_r on 2007-07-22
> **Note360 said:**
> that is alot of work, but ill try i guess. However, thats alot of work.

Good, take your time... Theres noe need to hurry on it...

---

### Post by xavier_r on 2007-07-22
**ScreenFace-1.3 released**, with new added feautures
Get it from here

[http://screenface.66ghz.com/](http://screenface.66ghz.com/)
Warning: THIS SOFTWARE IS STILL APLHA

---

### Post by Note360 on 2007-07-22
wow, likin the new layout. that is great.

---

### Post by xavier_r on 2007-07-23
Hey Note360, Jared, gave this... try it out...

Add the following to the bottom of your** /etc/screenrc** file for some
cool customization of screen. This lets screen have tabs at the bottom of
each window open.

See, the magic... :)
```

#Display tab will have a number, a name plus time and date
hardstatus alwayslastline
hardstatus string '%{= mK}%-Lw%{= KW}%50>%n%f* %t%{= mK}%+Lw%< %{=kG}%-=%D %d %M %Y %c:%s%{-}'
```

---

### Post by xavier_r on 2007-07-27
Hey Note360...
How r u?

See, here's somethig new..[B]
This is a view of images in web-browsers running in text-only mode...[/B]
Just do...
$ sudo apt-get install w3m fbida
and run w3m...

And lol its amazing...

---

