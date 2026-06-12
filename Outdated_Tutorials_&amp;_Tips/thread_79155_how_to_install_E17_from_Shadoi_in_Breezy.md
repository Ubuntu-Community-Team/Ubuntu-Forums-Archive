---
title: "how to install E17 from Shadoi in Breezy"
date: 2005-10-19
forum: Outdated Tutorials &amp; Tips
---

### Post by dlpfmVfH on 2005-10-19
I was looking for e17 (the new enlightenment:KS) for breezy, and came across Shadoi's blog...[his blog]("http://shadoi.soulmachine.net/")
He has a debian unstable repository and now a Ubuntu Breezy repository
which makes adding E17 easy...

Add this line to your /etc/apt/sources.list:
```
deb http://soulmachine.net/breezy unstable/
``` 
and this to your /etc/apt/preferences (if there isn't any create one)
```
Package: enlightenment
Pin: version 0.16.999*
Pin-Priority: 999

Package: enlightenment-data
Pin: version 0.16.999*
Pin-Priority: 999
``` 

then:
install the public.key from:
```
in the terminal/konsole type:
wget soulmachine.net/public.key && sudo apt-key add public.key
``` 

or download this key and install it through synaptic/repositories/authentication:
[http://soulmachine.net/public.key]("http://soulmachine.net/public.key")

sudo apt-get update (or run synaptic refresh)

sudo apt-get install enlightenment

or browse with synaptic and install any e17 app.

good luck and give feedback if I need to change anything...
this is my first how to...;) [COLOR=Black][B][U]
All credits must go to Shadoi (aka Blake Barnett) for making the repository!!! [/U][/B][/COLOR]

oh and for evidince I tried:
```
 http://surfnet.dl.sourceforge.net/sourceforge/evidence/evidence_0.9.8-20050305-hoaryGMW_i386.deb
``` 
and did :
```
 sudo dpkg -i evidence_0.9.8-20050305-hoaryGMW_i386.deb
``` 
and it works...but no breezy packaged build yet...
 :???:

For more information:

[http://www.get-e.org/]("http://www.get-e.org/")
[http://www.enlightenment.org/]("http://www.enlightenment.org/")
[http://www.edevelop.org/]("http://www.edevelop.org/")
[http://www.soulmachine.net/wiki/index.php?title=Enlightenment_on_Ubuntu_5.10_%28Breezy_Badger%29]("http://www.soulmachine.net/wiki/index.php?title=Enlightenment_on_Ubuntu_5.10_%28Breezy_Badger%29")

language support: currently :
english
chinese
danish
finnish
german
hungarian
russian
slovenian
 spanish
Dutch

-----------------------------------------------------------------
Tool for configuring E17 with a gui Erme (Enlightenment_Remote Made Easy):
You needGTK2::Perl
this is just a perl script that will give a window with options for keybinding, mouse, focus, etc. 

[http://www.c7obs.net/%7Eadi/projects/perl/]("http://www.c7obs.net/%7Eadi/projects/perl/")

-------------------------------------------------------------------
KNOWN PROBLEMS
-ANY_MOD don't function very well. it's from enlightenmet_remote.
-signal binding works only if ANY_MOD is ON
-there is a problem if you modify a binding and then delete it. erme will not
 delete the binding but update it. if you want to delete it use a simple delete.
 this is my fault. i will fix it pretty soon
-------------------------------------------------------------------

on building eap files:
[https://sourceforge.net/projects/e17genmenu/]("https://sourceforge.net/projects/e17genmenu/")

You need to build this yourself...
short how to build:
apt-get build-essentials...
apt-get checkinstall
apt-get e17 dev packages...don't know exactly wich ones..

untar genmenu, ./configure, make, sudo checkinstall..and follow directions..

goodluck

---

### Post by Juippisi on 2005-10-19
Looks good!

I've been using [http://omicron.homeip.net/projects/easy_e17/easy_e17.sh](http://omicron.homeip.net/projects/easy_e17/easy_e17.sh) script to install E17 on my Breezy, but later today I'll test this repo.

Thanks for pointing it out ;-).

---

### Post by zenrox on 2005-10-19
easy way to add the key to breezy 
```

wget soulmachine.net/public.key && sudo apt-key add public.key

```

---

### Post by i3dmaster on 2005-10-19
Cool! Thanks

---

### Post by dlpfmVfH on 2005-10-20
[QUOTE=zenrox]easy way to add the key to breezy 
```

wget soulmachine.net/public.key && sudo apt-key add public.key

```[/QUOTE]

thanks added it to the howto...

---

### Post by nrgtek on 2005-10-20
Great how-to, got it up and running now. Is there any guide for E17? I realize this is still a "beta" application, but I would like to see basics for adding applications to the launcher and such. Thanks!

---

### Post by TimmyJ on 2005-10-20
go to [www.get-e.org](www.get-e.org) they have a great site with a collection of themes, backgrounds, eaps, and an excellent user tutorial

---

### Post by rjwood on 2005-10-20
where does the public key get coded into??

---

### Post by dlpfmVfH on 2005-10-20
you can add it with synaptic, in the repository section,
authentication...

it is to show that these packages, are from shadoi (aka Blake barnett)

---

### Post by rjwood on 2005-10-20
[quote=aboe]you can add it with synaptic, in the repository section,
authentication...

it is to show that these packages, are from shadoi (aka Blake barnett)[/quote]

OK just trying to be careful...
I should open snyaptic go to repositories then to authentication and add:

[http://soulmachine.net/public.key](http://soulmachine.net/public.key)
wget soulmachine.net/public.key && sudo apt-key add public.key

those 2 lines---just like that???

---

### Post by Chareos on 2005-10-20
Just guessing if there's a way to install engage (in the most slick way as possible) on Kubuntu, keeping use kde at all...

---

### Post by dlpfmVfH on 2005-10-20
[quote=rjwood]OK just trying to be careful...
I should open snyaptic go to repositories then to authentication and add:

[http://soulmachine.net/public.key]("http://soulmachine.net/public.key")
wget soulmachine.net/public.key && sudo apt-key add public.key

those 2 lines---just like that???[/quote]

no there are two ways of doing this...
terminal or console:
the line wget soulmache.net/public.key bla bla, will do the trick

or 
download the public.key..and insert it in synaptic...

gonna try at improve the how to on this...a little bit..

---

### Post by rjwood on 2005-10-20
I appreciate the "how to" I think you worked hard on it. And it is kind of you to share your knowledge.

It was just a little unclear for me that's all.

GREAT JOB!!

---

### Post by dlpfmVfH on 2005-10-20
[quote=Chareos]Just guessing if there's a way to install engage (in the most slick way as possible) on Kubuntu, keeping use kde at all...[/quote]

what do you mean?
install entrance and keep kdm, or replace kdm with entrance and keep kubuntu??

---

### Post by Tab on 2005-10-20
[QUOTE=Chareos]Just guessing if there's a way to install engage (in the most slick way as possible) on Kubuntu, keeping use kde at all...[/QUOTE]
Engage is no longer being developed as a stand alone app, and instead is being developed as a module for E17.

---

### Post by sizzam on 2005-10-20
Can someone post a screenshot of what their E17 theme looks like when they maximize a window?   I can't find a single screenshot that shows that.   I'm just curious to see which toolbars get covered up and which stay on top of the windows, etc.

Thanks in advance.

---

### Post by rjwood on 2005-10-20
has anyone been able to get the weather module to work??

When I try to set the location, cpu monitor goes thru the roof and x freezes.

I tried after disableing all the other modules.  No luck

---

### Post by fukusayo on 2005-10-20
When I use Entrance Display manager, E17 loads up without a hitch. 
However, when I try loading KDE or gnome I get and Xsession error:

"Xsessions: unable to launch "gnome" xsession --- "gnome" not found; falling back to default session"

then it will load up the default which is gnome, but kde is still inaccessible. 

Any idea on how so correct this error?

---

### Post by bam on 2005-10-20
amazing, never installed it until today....bye bye gnome. Thanks!

---

### Post by dlpfmVfH on 2005-10-21
[quote=fukusayo]When I use Entrance Display manager, E17 loads up without a hitch. 
However, when I try loading KDE or gnome I get and Xsession error:

"Xsessions: unable to launch "gnome" xsession --- "gnome" not found; falling back to default session"

then it will load up the default which is gnome, but kde is still inaccessible. 

Any idea on how so correct this error?[/quote]

no I'm still having trouble configuring entrance myself....
and removed it. because gnome was in English, because entrance only speaks english...

---

### Post by dlpfmVfH on 2005-10-21
[quote=sizzam]Can someone post a screenshot of what their E17 theme looks like when they maximize a window?   I can't find a single screenshot that shows that.   I'm just curious to see which toolbars get covered up and which stay on top of the windows, etc.

Thanks in advance.[/quote]

if you maximize everything will get covered.
this is default behavior of a new window...

---

### Post by Chareos on 2005-10-21
[QUOTE=Tab]Engage is no longer being developed as a stand alone app, and instead is being developed as a module for E17.[/QUOTE]


So I've to choose kde or e17 to get engage ?

---

### Post by dlpfmVfH on 2005-10-21
just try to install engage only...maybe it will get some packages from enlightenment, but I just started engage in gnome and it works...
you have to fill your engage bar, with eaps...just look at the guide, in [www.get-e.org](www.get-e.org) for more information.

---

### Post by Sav on 2005-10-21
> Tool for configuring E17 with a gui Erme (Enlightenment_Remote Made Easy):
You needGTK2::Perl

[http://www.c7obs.net/%7Eadi/projects/perl/](http://www.c7obs.net/%7Eadi/projects/perl/)

Can you add more details about using this gui?

Plus, I am unable to compile e17genmenu.

the configure script gave me this error:

> checking for eet - version >= 0.9.10... no
*** The eet-config script installed by eet could not be found
*** If eet was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the EET_CONFIG environment variable to the
*** full path to eet-config.
checking for engrave-config... no
checking for engrave - version >= 0.1.0... no
*** The engrave-config script installed by engrave could not be found
*** If engrave was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the ENGRAVE_CONFIG environment variable to the
*** full path to engrave-config.
checking for enlightenment-config... no
checking for enlightenment - version >= 0.16.999... no
*** The enlightenment-config script installed by enlightenment could not be found
*** If enlightenment was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the ENLIGHTENMENT_CONFIG environment variable to the
*** full path to enlightenment-config.


If I try to launch make, it suddenly stops:

> In file included from main.c:37:
sort.h:8:17: error: Eet.h: No such file or directory
main.c: In function &#8216;_e17genmenu_init&#8217;:
main.c:103: warning: implicit declaration of function &#8216;eet_init&#8217;
main.c:114: warning: implicit declaration of function &#8216;eet_shutdown&#8217;
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/home/sav/D-loads/E17/e17genmenu-4.1.4/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sav/D-loads/E17/e17genmenu-4.1.4'
make: *** [all] Error 2


I think I'm missing something.

---

### Post by dlpfmVfH on 2005-10-21
to compile e17genmenu , you need the dev packages, from e17..
just install al the e17 devs it is not so big...

erme, is just a perl script that makes a gui to change some settings otherwise done with console...

---

### Post by shadoi on 2005-10-21
[QUOTE=sizzam]Can someone post a screenshot of what their E17 theme looks like when they maximize a window?   I can't find a single screenshot that shows that.   I'm just curious to see which toolbars get covered up and which stay on top of the windows, etc.

Thanks in advance.[/QUOTE]

Use this command to enable the smart maximize policy (this will likely be the default when e17 is released.):
enlightenment_remote -maximize-policy-set SMART

As far as packaging e17genmenu, erme, etc. goes, I'm not planning to package every E utility that pops up, only those that are produced by the enlightenment team.  Mainly because there are already quite a few packages to maintain within the  enlightenment project alone, I'm happy to add packages that get added the enlightenment CVS, but working in many different CVS trees/projects is not something I have time to do.  

With that said, I would very much encourage anyone who is making a app or utility for enlightenment to email the [email]enlightenment-devel@lists.sf.net[/email] mailing list with information about what you are creating and ask if it's appropriate to get it added to the project.

-Blake

---

### Post by justaguynpc on 2005-10-21
shadoi

In the age of super-boredom hype and mediocrity...
Tuesday, October 18, 2005
Oopsie
I sorta... let the eutils and emodules packages fall through the cracks for Debian unstable. They're uploaded now, sorry about that. :)

posted by shadoi at 9:04 AM 5 comments 

----------------> Does this mean I shouldn't amend my repositories?


justaguy

---

### Post by telmo on 2005-10-21
There are **NO** e17 enlightenment packages in that repository...! What can i do?

---

### Post by Zed on 2005-10-21
Did you follow the instructions re /etc/apt/preferences in the first post in this thread?

---

### Post by telmo on 2005-10-22
[QUOTE=Zed]Did you follow the instructions re /etc/apt/preferences in the first post in this thread?[/QUOTE]

ooops... forget it! I thought it was the earlier version... sorry.

By the way, how do i install the backgrounds? I downloaded and copied them, but i can't run them.

---

### Post by dlpfmVfH on 2005-10-22
open emblem in the terminal or in the configuration panel background selector, they must appear.

---

### Post by Sav on 2005-10-22
[QUOTE=aboe]to compile e17genmenu , you need the dev packages, from e17..
just install al the e17 devs it is not so big...

erme, is just a perl script that makes a gui to change some settings otherwise done with console...[/QUOTE]

Thanks it works.

Now, I can't get the program to run:

> Checking For /usr/share/applications...Exists
Checking For Files In /usr/share/applications

Found: accessibility-keyboard.desktop
Getting Eap Name
Parsing Desktop File /usr/share/applications/accessibility-keyboard.desktop
        Name: Keyboard
        Comment: Set your keyboard accessibility preferences
        Exec: gnome-accessibility-keyboard-properties
        Icon: gnome-settings-accessibility-keyboard
Processing File /usr/share/applications/accessibility-keyboard.desktop
        Got Window Class: (null)
        Trying To Find Icon gnome-settings-accessibility-keyboard
        Checking For gnome-settings-accessibility-keyboard.png
        Getting Icon Size Argument
        Getting Icon Theme Argument
        Using Icon /usr/share/icons/hicolor/48x48/apps/gnome-settings-accessibility-keyboard.png
        Writing Icon /usr/share/icons/hicolor/48x48/apps/gnome-settings-accessibility-keyboard.png
sh: edje_cc: command not found
        Writing app/info/name:Keyboard

ERROR: Cannot open file /home/sav/.e/e/applications/all/accessibility-keyboard.eap for WRITE


---

### Post by dlpfmVfH on 2005-10-22
do you have write persmission for that directory as a normal user??
sounds to me it doesn't...

---

### Post by Sav on 2005-10-22
[QUOTE=aboe]do you have write persmission for that directory as a normal user??
sounds to me it doesn't...[/QUOTE]

Yes, I have. It doesn't work using sudo, too.

---

### Post by dlpfmVfH on 2005-10-22
strange I will give you my config log so you can examine it

---

### Post by telmo on 2005-10-22
[QUOTE=aboe]open emblem in the terminal or in the configuration panel background selector, they must appear.[/QUOTE]

Thx..., i hadn't installed eutils... dumb me! :cool:

---

### Post by andrewsawyer on 2005-10-22
Thank you for the How-To, it has worked perfectly.

I'm now up and running in Enlightened Gnome and I love it.

I do however have a couple of questions - things I just can't get my head around.

There is a quick launch bar at the bottom, and it has 4 icons in it - Eterm, Firefox, IRC and GIMP.  How do I add/remove from this?  I have tried to drag from the Gnome Applications menu, but this crashed Enlightened.

Following from this, these programs are the only ones in the Favourite applications menu.  How can I add/remove?

This one will be simple I'm sure, but I can't find it anywhere - how do you change the background?!?!

That's it.  Thank you for the how-to.  My screen looks great now - now if only I could get this other stuff sorted!

---

### Post by dlpfmVfH on 2005-10-23
There is a quick launch bar at the bottom, and it has 4 icons in it - Eterm, Firefox, IRC and GIMP.  How do I add/remove from this?  I have tried to drag from the Gnome Applications menu, but this crashed Enlightened.

[COLOR=Red]this is the ibar-module... you can disable this with left-clicking on the desktop and search the module-part.[/COLOR]

Following from this, these programs are the only ones in the Favourite applications menu.  How can I add/remove?

[COLOR=Red]Left click on the desktop go to configuration panel, and menu editor...
or remove them in terminal : ~/.e/e/apps/favorite in there is a .order file...
with the names of the programs...clear the .order file..
[/COLOR]
This one will be simple I'm sure, but I can't find it anywhere - how do you change the background?!?!

[COLOR=Red]Did you install e_utils?? if so there is a program called emblem...
download some new backgrounds from get-e.org and copy them into
~/.e/e/backgrounds... they will show up in emblem...or read the guide..
in get-e.org for other formats.
[/COLOR] 
[COLOR=Red]hope you enjoy e17 as much as I do[/COLOR]

---

### Post by Peturrr on 2005-10-23
It looks like the repo is down. Can't connect to soulmachine.net.

---

### Post by dlpfmVfH on 2005-10-23
you're right, soulmachine.net is completly down, I'm trying to reach shadoi..
for more info...

maybe somebody, could share some room to make a mirror....

---

### Post by steffen on 2005-10-23
[QUOTE=andrewsawyer]Thank you for the How-To, it has worked perfectly.

I'm now up and running in Enlightened Gnome and I love it.

I do however have a couple of questions - things I just can't get my head around.

There is a quick launch bar at the bottom, and it has 4 icons in it - Eterm, Firefox, IRC and GIMP.  How do I add/remove from this?  I have tried to drag from the Gnome Applications menu, but this crashed Enlightened.

Following from this, these programs are the only ones in the Favourite applications menu.  How can I add/remove?

This one will be simple I'm sure, but I can't find it anywhere - how do you change the background?!?!

That's it.  Thank you for the how-to.  My screen looks great now - now if only I could get this other stuff sorted![/QUOTE]

How do you do this? I have to switch between Gnome and E17. Is it possible to integrate?

---

### Post by fukusayo on 2005-10-23
[QUOTE=aboe]no I'm still having trouble configuring entrance myself....
and removed it. because gnome was in English, because entrance only speaks english...[/QUOTE]
Looks like I will have to stick with gdm. It's too bad though, entrance looks great.

---

### Post by andrewsawyer on 2005-10-23
[QUOTE=steffen]How do you do this? I have to switch between Gnome and E17. Is it possible to integrate?[/QUOTE]

You can thank mendicant for posting this info on the forum in the first place. Makes it all possible.

Put this in regular terminal:

Quote:
sudo cp /usr/share/gnome/default.session ~/.gnome2/session

Then this:

Quote:
sudo gedit ~/.gnome2/session

Look for this line:

Quote:
1,RestartCommand=gnome-wm --sm-client-id default1

Change the like to look like this:

Quote:
1,RestartCommand=gnome-wm --default-wm enlightenment --sm-client-id default1

Save the file. Restart the X server (hit ctrl, alt, and backspace at the same time).

Then log back into Gnome. Enlightenment will start after a little while. Be very patient. The first time it took me a few minutes to log in., and my machine is pretty fast.

If it worked, you will be on your new desktop, using Enlightened Gnome.

This information was sourced from poofyhairguy's how-to.

---

### Post by anatole on 2005-10-24
thank you for this howto, i tried it and worked nice :)
one strange bug i found is that the iconify-fullscreen-close buttons work only with the deafult theme... anyone else experiencing this or am i the only person? :)
and, i couldn't find Entangle and Emblem. aren't they included in the packages, or is there some change about them i didn't notice? (i tried e17 once with hoary back then).

---

### Post by dlpfmVfH on 2005-10-24
apt-get install e_utils...it is in that package...

and yes not everything from E17 is packaged...if you want everything...
start getting all the e17 devs...and download the cvs..to build the rest

---

### Post by mjwood0 on 2005-10-25
Thanks for the great info! I now have a much better looking desktop!

But I can't seem to find this e_utils package anywhere...  is it in the repos?

Edit:

Nevermind.  It's eutils with no underscore...

Thanks again!  Much nicer than regular gnome!!!

---

### Post by anatole on 2005-10-25
[QUOTE=mjwood0]Thanks for the great info! I now have a much better looking desktop!

But I can't seem to find this e_utils package anywhere...  is it in the repos?[/QUOTE]

just found that out, its name is "eutils" :)

---

### Post by EnderTheThird on 2005-10-25
I tried installing using the easy_e17.sh script before, but didn't have any luck, so then I used the repo.  I'm up and running in e17 and it's absolutely beautiful!  The only problem is that my functionality is kinda screwed.  I can't edit the programs available in the main menu or in the bottom launcher.  When I go to the Configuration Panel, it's empty!  How can I edit my settings in here so I can access all of my needed applications without needing to run them using a terminal?

---

### Post by kperkins on 2005-10-25
can't install genmenu (ver. 4.1.4).
Get this error when doing make:
/usr/bin/ld: cannot find -lfl
Any ideas?

---

### Post by anatole on 2005-10-26
[QUOTE=EnderTheThird]I tried installing using the easy_e17.sh script before, but didn't have any luck, so then I used the repo.  I'm up and running in e17 and it's absolutely beautiful!  The only problem is that my functionality is kinda screwed.  I can't edit the programs available in the main menu or in the bottom launcher.  When I go to the Configuration Panel, it's empty!  How can I edit my settings in here so I can access all of my needed applications without needing to run them using a terminal?[/QUOTE]

install the eutils package, the configuration panel won't be empty anymore ;)

---

### Post by dlpfmVfH on 2005-10-26
[quote=kperkins]can't install genmenu (ver. 4.1.4).
Get this error when doing make:
/usr/bin/ld: cannot find -lfl
Any ideas?[/quote]

sorry can't help you out there...didn't write genmenu....

---

### Post by kperkins on 2005-10-26
I figured it out.  Had to install a some library that I don't remember now. and, also, libssl-dev

---

### Post by Sav on 2005-10-26
[QUOTE=aboe]strange I will give you my config log so you can examine it[/QUOTE]

Hi I still have problems running the utility.
If you could send me your conf files, maybe it can help.
Bye

---

### Post by dlpfmVfH on 2005-10-26
here it is...

removed, some unnecessary lines. to make it fit...for this forum

hope it helps

---

### Post by chien on 2005-10-26
> can't install genmenu (ver. 4.1.4).Get this error when doing make:/usr/bin/ld: cannot find -lflAny ideas?

Hey Kperkins , Im getting the same compiling error, can you tell me exactly what did you do to solve this ? what libraries did you install??

---

### Post by joflow on 2005-10-26
[QUOTE=anatole]install the eutils package, the configuration panel won't be empty anymore ;)[/QUOTE]

I got eutils up and running but I can't figure out how to add programs to the menu.

I can get into the configuration menu and start up the menu editor but none of the programs on my machine are listed.  I'm trying to add gAIM and Evolution to the ibar...none of these programs are listed...just programs that aren't installed on my machine (xmms, sylpheed, KDE terminal, etc) and programs like firefox, x-chat, etc.

---

### Post by joflow on 2005-10-26
[QUOTE=joflow]I got eutils up and running but I can't figure out how to add programs to the menu.

I can get into the configuration menu and start up the menu editor but none of the programs on my machine are listed.  I'm trying to add gAIM and Evolution to the ibar...none of these programs are listed...just programs that aren't installed on my machine (xmms, sylpheed, KDE terminal, etc) and programs like firefox, x-chat, etc.[/QUOTE]

I think I must be missing something.

The "create icon" doesn't creat a .eap file.  I click on save and nothing happens.

When I try the manual method...by editing icon.edc and running build.sh, it  doesn't create a .eap file.

Something must be wrong with my install or I'm missing some package or something.

---

### Post by joflow on 2005-10-26
Does it have anything to do with root access?  I just found out that I can't edit the icons of the pre-existing .eap files.

---

### Post by dlpfmVfH on 2005-10-27
[quote=joflow]I got eutils up and running but I can't figure out how to add programs to the menu.

I can get into the configuration menu and start up the menu editor but none of the programs on my machine are listed.  I'm trying to add gAIM and Evolution to the ibar...none of these programs are listed...just programs that aren't installed on my machine (xmms, sylpheed, KDE terminal, etc) and programs like firefox, x-chat, etc.[/quote]

This is done with the e17genmenu, it creates a menu listing of gnome and/or kde apps...that are currently listed in de gnome/kde menus.

Some people are having problems, compiling this,
So I suggest to get all dev files that come with this repo...
and try and compile it...

don't know exactly what depencies e17genmenu has, but if you look close at the configure output, you can figure this one out...

good luck

---

### Post by saidin on 2005-10-28
I was able to get genmenu to compile without to many problems.  I am having problems executing the program.  It comes up with not being able to open the following:
```

 ERROR: Cannot open file /home/saidin/.e/e/applications/all/accessibility-keyboard.eap for WRITE

```

Well, I cannot even find the file to chmod it....
Is this a file i need to create?

---

### Post by joflow on 2005-10-28
I need a C compiler.

---

### Post by joflow on 2005-10-28
[QUOTE=joflow]I need a C compiler.[/QUOTE]

I realized that I needed the build-essential package but when I try to install it from the repo it says I need libc6-dev

When I try to install libc6-dev I get the following:

The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.3.5-1ubuntu12) but 2.3.5-7 is to be installed
E: Broken packages

---

### Post by corefile on 2005-10-31
installed but when entrance starts up, my keyboard is unusable. Doesn't happend when using gdm. anyone seen this before?

---

### Post by Sav on 2005-10-31
[QUOTE=aboe]here it is...

removed, some unnecessary lines. to make it fit...for this forum

hope it helps[/QUOTE]

Thanks I'll try it

---

### Post by Sav on 2005-10-31
It isn't a problem about compiling, but there is a missing file: accessibility-keyboard.eap

There is a missing command, too. Here is a log:

> sh: edje_cc: command not found
        Writing app/info/name:Keyboard

ERROR: Cannot open file /home/sav/.e/e/applications/all/accessibility-keyboard.eap for WRITE

I install edje bin file and now e17genemu starts. After something like compiling it ends with this error:
> Regenerating Eapp Cache...
sh: enlightenment_eapp_cache_gen: command not found
Finished


---

### Post by dlpfmVfH on 2005-10-31
the file is indeed missing, but on my rig this isn't a problem...I got, the menu in my setup just working fine...

don't use the accessibilty-keyboard anyway...

---

### Post by krye on 2005-10-31
[QUOTE=chien]Hey Kperkins , Im getting the same compiling error, can you tell me exactly what did you do to solve this ? what libraries did you install??[/QUOTE]

I had the same error, figured out I needed the "flex" package... just do a 'sudo apt-get install flex', it worked for me.

---

### Post by corefile on 2005-11-01
Strange, I downloaded the latest version of of e17genmenu (4.15) and when I untar it and run ./configure or sh ./configure it says:

someuser@somecomputer:~/e17genmenu$ ./configure
bash: ./configure: No such file or directory

---

### Post by foxy123 on 2005-11-01
[QUOTE=corefile]Strange, I downloaded the latest version of of e17genmenu (4.15) and when I untar it and run ./configure or sh ./configure it says:

someuser@somecomputer:~/e17genmenu$ ./configure
bash: ./configure: No such file or directory[/QUOTE]
I guess you need to run

```
./autogen.sh
```

then you can do ./configure if you need some switches or just run make.

---

### Post by krye on 2005-11-02
Any chance of an update? The EAP editor isn't broken anymore on cvs, but i'm not sure I really want to compile from cvs (i'm scared :) )

---

### Post by dlpfmVfH on 2005-11-02
[quote=krye]Any chance of an update? The EAP editor isn't broken anymore on cvs, but i'm not sure I really want to compile from cvs (i'm scared :) )[/quote]

There is going to be an update soon, but Shadoi is working at a automatic script that will pull e17 from cvs and build updates...

He has done this before, but the scripts were crude, so it will take some time to smooth it out... be patient please...I'm waiting on the script too, too make nightly builds for sarge..

---

### Post by krye on 2005-11-02
Ok, thanks!! :D

---

### Post by kazuya on 2005-11-02
this is great. awesome guide.

---

### Post by yankcrime on 2005-11-03
I have been using e17 repositories via [http://ubuntu.nooms.de/](http://ubuntu.nooms.de/) in hoary, but this is incompatible with breezy (upgraded the beginning of this week).

I switched over to shadoi repositories but I have a persistent error with directfb.  The error [.xsesions-error] reports:

/usr/bin/enlightenment: error while loading shared libraries: libdirectfb-0.9.so.20: cannot open shared object file: No such file or directory

I had (note past tense) libdirectfb-0.9-22 and tried libdirectfb-0.9-24 to no avail.  the libdirectfb-0.9-20 is uninstallable.  In searching edevelop.org, I noticed Shadoi said directfb is unnecessary.  Especially building from cvs, I guess you can pass a `disable directfb` argument to the compiler to bypass its necessity.  Is there an equivalent to be done with the binary build?  Also, it seems evas provides the directfb package, but it doesn't seem to be available in my case.

I am using the legacy nvidia driver on an AMD using kernel 2.6.12.

Does anyone have any thoughts?

---

### Post by corefile on 2005-11-04
trying to install e17genmenu



someuser@somecomputer:~/e17genmenu$ ./autogen.sh 
Running aclocal...
aclocal: configure.in: 19: macro `AM_ENABLE_SHARED' not found in library
aclocal: configure.in: 20: macro `AM_PROG_LIBTOOL' not found in library
aclocal: configure.in: 87: macro `AM_PATH_GTK' not found in library

am I missing some packages?

EDIT:

Ok fixed that but now getting

noglobal.h:8:19: error: Ecore.h: No such file or directory
global.h:9:24: error: Ecore_File.h: No such file or directory
In file included from main.c:37:
sort.h:8:17: error: Eet.h: No such file or directory
In file included from main.c:37:
w stuck on make errors

EDIT #2

Figured it out

---

### Post by dlpfmVfH on 2005-11-04
I have directfb22 installed, all the files, and use a new build not from the repo anymore, because of the updates lately, and because I maintain the dutch translation...

the shadoi repo is a bit out-dated at the moment, hopefully it will be updated soon.

---

### Post by rjwood on 2005-11-04
help----I installed entrance and set it as default but now I can't log in. I can log as another user but not me. It acts like it is going to let me in and then displays the log-in screen again. I can't get at anything. Doesn't accept my password through the other log-ins. I Don't know what to do. 

I set e17 as the window manager just before all this happened but that worked fine. It was after I set entrance and a couple of other selections from synaptic. 

any idea's!!!:rolleyes::confused:

---

### Post by Lorge on 2005-11-04
[QUOTE=corefile]trying to install e17genmenu



someuser@somecomputer:~/e17genmenu$ ./autogen.sh 
Running aclocal...
aclocal: configure.in: 19: macro `AM_ENABLE_SHARED' not found in library
aclocal: configure.in: 20: macro `AM_PROG_LIBTOOL' not found in library
aclocal: configure.in: 87: macro `AM_PATH_GTK' not found in library

am I missing some packages?

EDIT:

Ok fixed that but now getting

noglobal.h:8:19: error: Ecore.h: No such file or directory
global.h:9:24: error: Ecore_File.h: No such file or directory
In file included from main.c:37:
sort.h:8:17: error: Eet.h: No such file or directory
In file included from main.c:37:
w stuck on make errors

EDIT #2

Figured it out[/QUOTE]

How did you fix it?
What packages did you install?

---

### Post by joflow on 2005-11-08
[QUOTE=Lorge]How did you fix it?
What packages did you install?[/QUOTE]

would like to know this as well as I'm going to be trying to compile e17genmenu tonight.

---

### Post by eric0919 on 2005-11-09
I tried following this how to and everything seemed to work, but there is no choice for enlightenment when I log in.  Is there a way I can fix this or did i mess up the install?

thanks Eric

---

### Post by dlpfmVfH on 2005-11-10
look in /usr/share/xsession if there is an enlightenment.desktop
if not to create one is very simple

sudo cp gnome.desktop enlightenment.desktop
sudo (editor eg. nano, vi, cream) enlightenment.desktop

and change exec=blah,blah/gnome to /usr/bin/enlightenment remove comments to gnome or replace gnome with enlightenment...

good luck

---

### Post by eric0919 on 2005-11-10
Thanks I got it.  now I just need to gifure out how to configure it.

---

### Post by ssam on 2005-11-10
are there powerpc builds?

---

### Post by dlpfmVfH on 2005-11-10
not in this repo...you could ask the maintainers from get-e.org...or locate the irc channel for enlightenment and ask..

---

### Post by N8K99 on 2005-11-12
Hey Great tutorial, thanx for the effort and the clarity. I used it to install e17 but didn't really like the way it felt on default and didn't really enjoy the themes I found on the InterWeb. I reverted to the e16 which can be found in the Ubuntu Universe, but the inclusion of Entrance really did make a difference. I hate the incredible crawling speed of Gnome on my machine (low memory low budget) so I am just running enlightenment as my environment.

---

### Post by nastya on 2005-11-13
[QUOTE=Lorge]How did you fix it?
What packages did you install?[/QUOTE]

I had the same errors as him when I first tried to run ./autogen.sh. After doing some searching in google, I installed the following packages:libevas0-dev libecore0-dev libeet0-dev libcurl3-dev libengrave0-dev libgnome-dev. After installing them, it compiled fine.

---

### Post by mustang on 2005-11-13
Sorry for the somewhat offtopic question but I'm not familar with how windows managers work on Ubuntu.

So if I install enlightenment, will another option pop in on the login screen? This won't in any way affect my current GNOME windows manager right? Thanks

---

### Post by anatole on 2005-11-13
[QUOTE=mustang]Sorry for the somewhat offtopic question but I'm not familar with how windows managers work on Ubuntu.

So if I install enlightenment, will another option pop in on the login screen? This won't in any way affect my current GNOME windows manager right? Thanks[/QUOTE]

that's correct. at the gdm you will have the option to choose enlightenment, or go on with good old gnome :)

on the other hand, anyone (mainly aboe :D ) : any news about an update? i cannot wait for the working eapp editor... i would made the switch but i'm too lazy for making the eap files from a terminal :)

---

### Post by dlpfmVfH on 2005-11-15
The repo update to the new cvs has had a few delays, mainly because the nightly builds code isn't finished. And Shadoi is very busy at the moment...

I will contact him soon and post the results...

---

### Post by N8K99 on 2005-11-17
[QUOTE=mustang]
So if I install enlightenment, will another option pop in on the login screen? This won't in any way affect my current GNOME windows manager right? Thanks[/QUOTE]

If you are bold and install Entrance from the repositories on Shadoi's blog like the HOWTO suggests, then you will have a new login page based upon the Enlightenment Package. I really like this login page much better than the 'human' one provided by Ubuntu. Part of the appeal of Linux-world for me is the complete configurations options that are available, so I removed gdm and nautilus in order to speed things up on my old system. Using the packages from Enlightenment (I don't like the e17 themes or feel right now so I stayed with the E16 that is in  Ubuntu's Universe) I have got a dsktop computer that is nearly a decade old running some pretty fancy programs like OOo 2.0 without very much hassle whatsoever. I am quite happy with the progress that I am making here!! :D

---

### Post by ch13f121 on 2005-11-17
How do use the perl script, and how do I get genmenu installed, I haven't got the e17 devs. I don't even know what they are, so how am I gonna install em? :p  can anyone give me the names of the dev packages?

EDIT: I've got everything except that perl script for erms, I still don't know what to do with that. BUT when I try to install genmenu, I get this when I ./autogen.sh
Running aclocal...
./autogen.sh: line 8: aclocal: command not found

How do I fix this, better yet can anyone explain WHY this is happening?

---

### Post by Strangerdave on 2005-11-18
Okay I tried this How To and I wasn't sure how to get enlightenment working (I am a newbie here) so I typed it into a terminal and got this:

```
DYNAMIC DETERMINED PREFIX: /usr
setlocale() :: No such file or directory
An error occured when trying to use the locale: en_CA:en
Details:
E17 INIT: XINERAMA CHOSEN: [0], 1280x1024+0+0
_______                     _______
|:::::| Enlightenment Error |:::::|
~~~~~~~                     ~~~~~~~
Cannot create manager object for screen 0

_______                     _______
|:::::| Enlightenment Error |:::::|
~~~~~~~                     ~~~~~~~
Enlightenment set up window management for all the screens on your system
failed. Perhaps another window manager is running?

E17: Begin shutdown procedure!

```

How do I get enlightenment to work?

-SD-

---

### Post by ch13f121 on 2005-11-18
[QUOTE=Strangerdave]Okay I tried this How To and I wasn't sure how to get enlightenment working (I am a newbie here) so I typed it into a terminal and got this:

```
DYNAMIC DETERMINED PREFIX: /usr
setlocale() :: No such file or directory
An error occured when trying to use the locale: en_CA:en
Details:
E17 INIT: XINERAMA CHOSEN: [0], 1280x1024+0+0
_______                     _______
|:::::| Enlightenment Error |:::::|
~~~~~~~                     ~~~~~~~
Cannot create manager object for screen 0

_______                     _______
|:::::| Enlightenment Error |:::::|
~~~~~~~                     ~~~~~~~
Enlightenment set up window management for all the screens on your system
failed. Perhaps another window manager is running?

E17: Begin shutdown procedure!

```

How do I get enlightenment to work?

-SD-[/QUOTE]

you didn't try to start it while you were in gnome/kubuntu did you?  if you did, then that's why. go back to your login screen after you install it, and click sessions.  from there you want to select enlightenment

---

### Post by Strangerdave on 2005-11-18
Ha Ha ha......um yes, that was what I was trying to do:confused: 

I did what you said and it seems to be working.  Thanks for the info.

-SD-

---

### Post by darkmatter on 2005-11-18
[QUOTE=Lorge]How did you fix it?
What packages did you install?[/QUOTE]

Other than the missing dev libraries for E (easily solved), the 'AM_<whatever>' errors are the result of not having the appropriate version of automake installed.

E17 and the libraries/apps built for it (including e17genmenu) require automake 1.7+ to compile/install.

---

### Post by Jonne on 2005-11-21
ok, i haven't managed to compile e17genmenu, so what am I missing?

I installed everything listed in this thread (I hope), but when I do 'sudo sh ./autogen.sh', i get this:
```
Running aclocal...
Running autoheader...
Running autoconf...
Running libtoolize...
cp: failed to preserve ownership for `ltmain.sh': Operation not permitted
libtoolize: cannot copy `/usr/share/libtool/ltmain.sh' to `ltmain.sh'
./autogen.sh: line 11: glibtoolize: command not found

```

edit1:
ok, i found it:
I unpacked the archive on my fat32 partition (I use it to move files between windows and Linux, and basicly as the my documents folder in my home directory, even though i haven't booted windows in weeks), which meant that i couldn't set permissions. (or it gave problems setting them).

When i moved everything on a regular partition, and set the permissions right, it seems to work. (I'm not done yet, so i might run into other errors)

edit2:
Now i'm stuck here: i did 'make', and i get the following error:
```
/usr/bin/ld: cannot find -ljpeg
```

---

### Post by Bagger on 2005-11-23
Does anybody have any idea when Shadoi might be updating his e17 repository? Or do we need to find another source for the latest e17 like eLive.

Yes I suppose I could build it from CVS and may have to but I rather like the way these apt's work as opposed to Suse which I have been using for years.

If anybody has any news on Shodoi I'm sure it would be apreciated by all.

Thanks

---

### Post by joflow on 2005-11-27
Shadoi made a post on the edevelop forum saying that his "package repository should be updated tonight or tomorrow".. that was on Nov. 1st.  Any word yet?

---

### Post by Qrawler on 2005-11-27
Can someone help me out with this e17 module
I have trouble compiling E17 Module eloquence-0.4.2
When I do the ./autogen.sh I get this output (wich seems good to me?)
[COLOR="RoyalBlue"]
Running aclocal...
Running autoheader...
Running autoconf...
Running libtoolize...
Running automake...
src/Makefile.am:16: comment following trailing backslash
src/Makefile.am:17: comment following trailing backslash
src/Makefile.am:18: comment following trailing backslash
src/Makefile.am:19: comment following trailing backslash[/COLOR]

after this Irun the ./configure command  (which seems good to me)

[COLOR="RoyalBlue"]checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... missing
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for strerror in -lcposix... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
jericho@nb0308:~/download/eloquence-0.4.3$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... missing
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for strerror in -lcposix... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
chechecking how to recognise dependent libraries... pass_all
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C++ preprocessor... g++ -E
checking for g77... g77
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether g77 accepts -g... yes
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for g77 option to produce PIC... -fPIC
checking if g77 PIC flag -fPIC works... yes
checking if g77 supports -c -o file.o... yes
checking whether the g77 linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
Package audacious was not found in the pkg-config search path.
Perhaps you should add the directory containing `audacious.pc'
to the PKG_CONFIG_PATH environment variable
No package 'audacious' found
Package audacious was not found in the pkg-config search path.
Perhaps you should add the directory containing `audacious.pc'
to the PKG_CONFIG_PATH environment variable
No package 'audacious' found
checking xmms/xmmsctrl.h usability... yes
checking xmms/xmmsctrl.h presence... yes
checking for xmms/xmmsctrl.h... yes
checking bmp/beepctrl.h usability... yes
checking bmp/beepctrl.h presence... yes
checking for bmp/beepctrl.h... yes
checking audacious/beepctrl.h usability... no
checking audacious/beepctrl.h presence... no
checking for audacious/beepctrl.h... no
checking libmpd-0.01/libmpd/libmpd.h usability... no
checking libmpd-0.01/libmpd/libmpd.h presence... no
checking for libmpd-0.01/libmpd/libmpd.h... no
checking for amarok... no
checking for mpd_ob_new_default in -lmpd-0.01... no
checking for mpd_ob_new_default in -lmpd-0.01... (cached) no
checking for ecore-config... /usr/bin/ecore-config
cking whether ln -s works... yes
checking for evas-config... /usr/bin/evas-config
checking for esmart-config... /usr/bin/esmart-config
checking for edje-config... /usr/bin/edje-config
checking for eet-config... /usr/bin/eet-config
checking for enlightenment-config... /usr/bin/enlightenment-config
configure: creating ./config.status
config.status: creating Makefile
config.status: creating data/Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing default-1 commands
config.status: executing default commands[/COLOR]

But when I give the Make Install command I'm getting this?
[COLOR="RoyalBlue"]
Making install in src
make[1]: Entering directory `/home/jericho/download/eloquence-0.4.3/src'
/bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.                          -I..                          -I/usr/local/include       @glib_cflags@                          -I/usr/include -I/usr/include/enlightenment -DUSE_E_CONFIG_H  -I/usr/include -I/usr/include/enlightenment -DUSE_E_CONFIG_H -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I/usr/include/xmms -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I/usr/X11R6/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0     -g -O2 -c e_mod_main.c
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I. -I.. -I/usr/local/include @glib_cflags@ -I/usr/include -I/usr/include/enlightenment -DUSE_E_CONFIG_H -I/usr/include -I/usr/include/enlightenment -DUSE_E_CONFIG_H -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I/usr/include/xmms -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I/usr/X11R6/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -g -O2 -Wp,-MD,.deps/e_mod_main.pp -c e_mod_main.c  -fPIC -DPIC -o .libs/e_mod_main.o
gcc: @glib_cflags@: No such file or directory
e_mod_main.c: In function 'callback_gui_menu':
e_mod_main.c:1060: warning: passing argument 8 of 'e_menu_activate_mouse' makes integer from pointer without a cast
make[1]: *** [e_mod_main.lo] Error 1
make[1]: Leaving directory `/home/jericho/download/eloquence-0.4.3/src'
make: *** [install-recursive] Error [/COLOR]

Anyone got a clue how I can solve this? Sorry for this large post, but I really want this kewl look'n module to run :???:

---

### Post by Bagger on 2005-11-27
"Anyone got a clue how I can solve this? Sorry for this large post,...."

I may be wrong about this but it seems I saw something in a post here at ubuntu that there is an issue with the gcc version. Once again I'm not sure but I seem to recall that ubuntu installs gcc 3.4 and you need 3.3... something like that anyway. I'd probably have more information for you if I'd had this problem but as yet have not had the time to booger up my linux box.

---

### Post by Bagger on 2005-11-27
[QUOTE=joflow]Shadoi made a post on the edevelop forum saying that his "package repository should be updated tonight or tomorrow".. that was on Nov. 1st.  Any word yet?[/QUOTE]

I've been checking his site at [http://shadoi.soulmachine.net/](http://shadoi.soulmachine.net/) pretty regular of late and have seen nothing indicating he has updated the repository.

I' may switch to the elive repository, it seems to be more current.

---

### Post by DownloadTHIS on 2005-11-27
When I try to run e17genmenu I get this error:

e17genmenu: error while loading shared libraries: libssl.so.5: cannot open shared object file: No such file or directory

I installed libssl and the dev package, but no luck. Also, if I can't get this to work, is there another way to add menu icons?

---

### Post by Bagger on 2005-11-27
[QUOTE=DownloadTHIS]When I try to run e17genmenu I get this error:

e17genmenu: error while loading shared libraries: libssl.so.5: cannot open shared object file: No such file or directory

I installed libssl and the dev package, but no luck. Also, if I can't get this to work, is there another way to add menu icons?[/QUOTE]

I've never had much luck with e17genmenu and I really do not want all of the items in the menu anyway. 
The way I do it is first to create my .edc file... something as follows 

images {
   image: "icon.png" COMP;
}
collections {
   group {
      name: "icon";
      max: 48 48;
      parts {
	 part {
	    name: "image";
	    mouse_events: 0;
	    description {
	       state: "default" 0.0;
	       aspect: 1.0 1.0;
	       image.normal: "icon.png";
	    }
	 }
      }
   }
}

save as icon.edc, then compile with the following build script

#!/bin/sh
# actually compile an edje file with all the gfx etc.
edje_cc $@ -id . -fd . icon.edc kcontrol.eap
# add eap properties to the file - they are ALL optional EXCEPT name$
# and exe is optional for directory .eap files
enlightenment_eapp \
kcontrol.eap \
-set-name "kcontrol" \
-set-generic "kcontrol" \
-set-comment "kcontrol" \
-set-exe "kcontrol" \
-set-win-name "kcontrol" \
-set-win-class "kcontrol"

cp kcontrol.eap $HOME/.e/e/applications/all/

then go to the menu editor under the configuration editor. 

Hope this helps

---

### Post by tafsen on 2005-11-28
I followed the guide, but I think E16 got installed instead :o

---

### Post by tomski on 2005-11-28
thanks for this how too  :-)

i did have this in hoary but this time round with breezy it rocks!!

i did add the following :
gcc++ 3.4
flex
build-essential 

and after i installed i logged in once then back to tty-2 with ctrl+alt+F4 logged in as a user then ran e17genmenu

and it worked thanks

---

### Post by penvzila on 2005-11-30
there is a repository listed here:

[http://kanotix.com/PNphpBB2-viewtopic-t-12856.html](http://kanotix.com/PNphpBB2-viewtopic-t-12856.html)

that has some stuff that isn't in this one.  and it works at the moment.

---

### Post by benplaut on 2005-11-30
this ?build? is buggy as hell... i get segfaults every few minutes.

I'm trying that kanotix one... might work :)

<<edit>>

'not going to be installed' on about 20 dependencies... nope

---

### Post by anatole on 2005-11-30
[QUOTE=benplaut]this ?build? is buggy as hell... i get segfaults every few minutes.
[/QUOTE]
 
it has quite many broken things because the state of the cvs which it was built from had these bugs too (due to the mass amount of 'new' stuff in that back then)... the cvs is in a state far more developed than this one, but it seems like we have to wait a bit longer to get an update..

[QUOTE=benplaut]
'not going to be installed' on about 20 dependencies... nope[/QUOTE]

i think i do not understand this part... have you tried it? and it does not work? if so, bad news... i would consider trying this one...

---

### Post by penvzila on 2005-11-30
I get the occasional segfault too.  This is not really intended for general use, remember, it's still in development.

---

### Post by Bagger on 2005-11-30
[QUOTE=penvzila]I get the occasional segfault too.  This is not really intended for general use, remember, it's still in development.[/QUOTE]

I've been running e17 for sometime as my primary wm without any problems. I have a few issues with KDE apps but generally I run both KDE and Gnome apps with very little problem. Personally I'm very pleased with E17 and always look forward to the next cvs update as it has almost always been more reliable then previous updates.

---

### Post by penvzila on 2005-11-30
My segfaults have all come from evidence and etkconfig.  Evidence stopped doing it a while ago, but I still can't start etkconfig without a segfault.

---

### Post by Jonne on 2005-12-01
I switched to the elive repositories, but I seem to have trouble upgrading (or switching to the cvs version of) 'entrance', 'evidence', and 'examine'.

They are held back, because I don't have efl-all. efl-all, in turn, depends on:
xlibmesa-dev
xlibmesa-gl-dev   or
libglu1-xorg-dev

Where can I get those, and which one of the 3 should I use?

I tried googling for a deb of libglu1-xorg-dev , but it won't install because of a conflict (I can't tell what it's conflicting with).

---

### Post by tomski on 2005-12-01
how do you guys get around the fact that when you use a gtk app ie nautilus the desktop goes black, similar also happens with xfce in the way that when i use nautilus the left and right click menu changes to the right click menu you get in a folder

---

### Post by dlpfmVfH on 2005-12-01
[QUOTE=tomski]how do you guys get around the fact that when you use a gtk app ie nautilus the desktop goes black, similar also happens with xfce in the way that when i use nautilus the left and right click menu changes to the right click menu you get in a folder[/QUOTE]

use nautilus --no-desktop instead of nautilus

that will start nautilus without taking over the screen.

hope it helps

---

### Post by benplaut on 2005-12-03
[QUOTE=anatole]it has quite many broken things because the state of the cvs which it was built from had these bugs too (due to the mass amount of 'new' stuff in that back then)... the cvs is in a state far more developed than this one, but it seems like we have to wait a bit longer to get an update..



i think i do not understand this part... have you tried it? and it does not work? if so, bad news... i would consider trying this one...[/QUOTE]

"Package 'blah blah blah' is not going to be installed"... on almost every single package... pretty much, it would break too many dependencies (gnome, X, everything...)

i'm trying CVS right now, i'll report back

---

### Post by tomski on 2005-12-04
[QUOTE=aboe]use nautilus --no-desktop instead of nautilus

that will start nautilus without taking over the screen.

hope it helps[/QUOTE]


thanks aboe i'll edit the link for it that i put in the menu

cheers

---

### Post by super on 2005-12-15
i 've got a couple e17 questions:

1. can anyone tell me how to get icons for the e17 submenus? ([like in this screenshot?)]("http://sourceforge.net/dbimage.php?id=25682") i think e17genmenu does it automatically, but how do i do it manually?

2. does anyone know where i can find an eclair theme that matches the e17 'winter' theme? (that's the theme being used in the screenshot above)

thanks!

---

### Post by Redindian on 2005-12-20
Hello, I have installed E17, it is working fine. I have downloaded and unpacked e17genmenu in my home folder, ran ./autogen.sh. Went well. Then ran make.....gave me some error related to ecore. I'm sure i have installed automake 1.7 and ecore. I also installed eutils, i do have an icon called eapp_edit in my engage menu but its not working. Any idea what i'm doing wrong here?

---

### Post by dlpfmVfH on 2005-12-20
maybe you forgot the dev packages...for ecore??

---

### Post by Internet on 2005-12-20
I followed the How-to but It installed E16 :confused: I don't understand. When I look in synaptic, E17 isn't listed, only E16.

---

### Post by Dr. Nick on 2005-12-21
[quote=Internet]I followed the How-to but It installed E16 :confused: I don't understand. When I look in synaptic, E17 isn't listed, only E16.[/quote] 
Make sure to update your repositories after adding the e17 one, Also check this part

add this to your /etc/apt/preferences (if there isn't any create one)
    ```
 Code:
     [LEFT]Package: enlightenment
Pin: version 0.16.999*
Pin-Priority: 999

Package: enlightenment-data
Pin: version 0.16.999*
Pin-Priority: 999[/LEFT]

```[LEFT][/LEFT]

---

### Post by tomski on 2006-01-02
what would be the best way to update to the latest e17 as shadoi's repo has not changed since 14-Oct-2005 with enlightenment at 0.16.999.018
but the latest enlightenment is at 0.16.999.022.
should i use elive or cvs & how would these changes affect what i already have

---

### Post by Fyrzen on 2006-01-02
The e17 package alone is incredibly stable, the only errors i've encountered were segfaults(according to e17), which I caused by mistyping the names of some backgrounds in an enlightenment-remote add-bg command. 

But there's one thing i don't get, i'm missing a lot of features, the get-e guide always says to go to the configuration panel to change some options, but i've got nothing there, it's empty. What am I missing here?

---

### Post by anatole on 2006-01-02
[QUOTE=Fyrzen]The e17 package alone is incredibly stable, the only errors i've encountered were segfaults(according to e17), which I caused by mistyping the names of some backgrounds in an enlightenment-remote add-bg command. 

But there's one thing i don't get, i'm missing a lot of features, the get-e guide always says to go to the configuration panel to change some options, but i've got nothing there, it's empty. What am I missing here?[/QUOTE]

the packages are old, and e17 itself is under heavy development, so there are a lot of features / modules /etc added to the cvs that this version is missing.

---

### Post by tomski on 2006-01-02
I come bearing fresh fruits straight from the Edevelop forums where i asked if the soulmachine repository will be updated and :

Submitted by shadoi on Tue, 2006-01-03 05:02.

I'm updating the repository today.

[here is the thread  (sorry for the cross site link)]("http://edevelop.org/node/2053#comment-4451")
so there we go 
hopefully it will be a smooth update

---

### Post by Tab on 2006-01-02
> Submitted by shadoi on Tue, 2006-01-03 05:02.

I'm updating the repository today.We'll see about that. He said the same thing [two months ago]("http://edevelop.org/node/1717#comment-3829")...

---

### Post by tomski on 2006-01-02
Oh well i guess its back to hoping then eh! unless he's true to his word this time round

---

### Post by Dr. Nick on 2006-01-02
The CSV install following the guide on the forums is painless. You can tell a difference in the e17 interface due to the development between the 2. The CVS installs to a different flder, but you may have to remove this version to avoid conflict

If you decide to go CVS then either have a fast computer, or alot of time.
I started to CVS my laptop and it took 12hrs and hadnt even gotten half way (366p2 with 128mb ram). So i cancled it and used the shadoi build.

But on my amd 64 3000 desktop with 1GB ram the shadio version wouldnt work since its 386 but the cvs install took less than 2hrs total.

I heard the people at elive are supposed to have a new live cd out soon, not sure the exact date.

---

### Post by drfalkor on 2006-01-30
nice howto, but - when I start e17 the screen is black, and its loading loading loading,, and then I see a white background and nothing more happends ;)

---

### Post by Rev. Nathan on 2006-01-30
This is great! It worked! Enlightenment is pretty snazzy. :D

Although, damn, this is very errorsome. Within the first 15 minutes it crashed -- twice. Is this... expected?

---

### Post by Jonne on 2006-01-31
yes it is.

Although you'll learn how to use it without crashing it. (If you do something, and it crashes, don't do the same thing again ;) ).

It's really like using Windows at this point. Except that the E17 people at least warn you the code is alpha quality ;).

---

### Post by foxy123 on 2006-01-31
[QUOTE=Rev. Nathan]This is great! It worked! Enlightenment is pretty snazzy. :D

Although, damn, this is very errorsome. Within the first 15 minutes it crashed -- twice. Is this... expected?[/QUOTE]
i use e17 from cvs and it does not crash much...

---

### Post by linuxun on 2006-02-02
I did the install based on the directions in soulmachines wiki.

All appeared okay with menus, dock etc., but I just noticed that under configuration I get the config window but it is not populated with the icon selections.  It's just blank.

Any ideas?

---

### Post by mrgnash on 2006-02-23
It ran once, complained about an IPC socket and now it just segfaults everytime - even after removal and reinstall :( Sigh.. and it looked so pretty too.

---

### Post by shr00m on 2006-02-23
i read the very first post about adding shadoi repository so i added the line to apt list and made the preference file and got the public key but once i opened synaptic it keeps giving me an error saying that the line i added to the apt list is wrong i added this line right at the end of the apt list

deb [http://soulmachine.net/breezy](http://soulmachine.net/breezy) unstable

have i done something wrong, any ideas how to fix it.

---

### Post by hvar on 2006-02-23
Anybody know how to solve this wee little problem?

hvar@ubuntu:~/Desktop/e17genmenu$ ./autogen.sh
Running aclocal...
./autogen.sh: line 8: aclocal: command not found

Many thanks!

---

### Post by Griff on 2006-02-24
[QUOTE=Jonne]
It's really like using Windows at this point. Except that the E17 people at least warn you the code is [COLOR="Lime"]**PRE**[/COLOR]alpha quality ;).[/QUOTE]
Fixed and Limed.  ;) 
Anyone having success with gnome w/ e17?  I got it up and running and it's not crashing, but workspace one is very gnome and 2, 3, and 4 are pure enlightenment.  How do I get workspace one like the other enlightenment workspaces?

---

### Post by Resurrection on 2006-03-15
I keep trying to get the key through either terminal or just direct download, but unfortunately I can't connect to [http://soulmachine.net/ ]("http://soulmachine.net/").  Any body know of another way to get the key?

Edit:  Nevermind.  Can connect now.

---

### Post by tomski on 2006-03-16
i would not bother with adding the shadoi repo as he is more interested in maintaining a debian repo & letting women get to him...!!!!!
(which you could allways try to add as a source but that may break some things)

there are a couple of other repos about try looking in the edevelop forum

---

### Post by Resurrection on 2006-03-17
Yeah I figured that out.  It doesn't work for me anyway, so I just went back to XFCE4 for now.  I was able to get E16 installed, but I didn't really like it for some reason.

---

