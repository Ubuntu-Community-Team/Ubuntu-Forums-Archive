---
title: "HOWTO: Setup Icewm with Rox-Filer"
date: 2006-05-06
forum: Outdated Tutorials &amp; Tips
---

### Post by Peter76 on 2006-05-06
I've been using Icewm with Rox now for a while on an older machine and thought it a good idea to share my gathered knowledge till now, seeing not a lot of info on Icewm here.....

I'll assumme you did a server install and know your way around the command line.
Also have a look here: [https://wiki.ubuntu.com/Installation/LowMemorySystems](https://wiki.ubuntu.com/Installation/LowMemorySystems)

For this configuration, you need the following packages:

gdm ( or any other dm )
x-window-system-core
icewm
icewm-themes
rox-filer
menu
xfce4-terminal ( This is a Dapper package; use xterminal in Breezy )
Any other programs you like

Ok, so you have installed this and are ready for your first login. Now in GDM, set your session to icewm and make it the default. Otherwise it will start up with gnome and this doesn't work properly ( have never tried to get it to work though, so no info here. ) Well, type your log and pass and enter... There you are at a simple looking icewm session.

Now we are going to tweak this a bit so it looks nicer, we have a desktop with icons, and you know how to edit the icewm configuration files.
So first open a terminal, if you installed one, there should be a treminal icon in the taskbar and in your start( icewm )menu

```
mkdir ~/.icewm
```
```
cp /etc/X11/icewm/* ~/.icewm/
```

Now, with your favorite editor ( I use Mousepad here... ) create a file "startup" in the ~/.icewm directory and put the following line in it:

rox --pinboard=yourusername &

Save it and make it executable:

```
chmod +x ~/.icewm/startup
```

Now logout and log back in, in the Icewm menu -> Logout. Now you come back into Icewm with Rox filer having taken over the desktop and a nice icon sitting there for your home directory. If you right click, you now get the Rox menu, have a look around here, especially the options, this is pretty straight forward.
If you want more things on your desktop, just drag them there from a Rox window. One thing I like to have around is an icon for my cdrom, as this doesn't automatically appears as in gnome: from a rox window, go into the /media directory and drag the cdrom dir to the desktop. Now if you insert a cd and open this icon, it gets mounted automatically....

Setting the standard application for a certain file is also a matter of drag and drop: right click on the file you want to set the standard app for and -> Set run action.
Now in a Rox window go to ( most of the time ) /usr/bin/ and from there drag the application you want to use to the Set run action window. That's it!

There's no trash by default in Rox; you delete files PERMANENTLY by right clicking on them and -> delete. If you want to have a nice trash on your desktop, download a tarsh from here: [http://www.hayber.us/rox/misc/Rubbish-001.tgz](http://www.hayber.us/rox/misc/Rubbish-001.tgz)
Extract the file:

```
tar xzvf Rubbish-001.tgz
```

Drag the icon to your desktop and Voila, you now have a trash. Drag stuff to it to put it there. Be warned though: the delete option from the Rox menu still deletes things PERMANENTLY!!!

Two more little nifty Rox tricks: in a Rox window, hit '/' and you can type the location you want to go to, hit 'esc' to get out. Hit 'shift+!' to get a command line, hit 'esc' to get out again

Ok, this far about Rox, now we'll get into configuring Icewm. As you prabably figured out, the configuration files for Icewm are now in ~/icewm.

To add an application to your Icewm menu, there is are two ways. The easy way is to use the 'program's' menu in the Icewm menu. This menu is managed by the menu package. Every time you install a new application,run ```
update-menus
``` from the terminal and this menu will get updated with your new app.
The other way is by editing the ~/.icewm/menu file. Open it with your favorite editor and have a look at it; it's pretty self-explanatory. You can leave it as it is and add things to your needs, or delete everything in there and start all over again  as I did. What it comes down to is this:

If you want a menu, add:
```
menu "NameOfMenu" folder { 
}
```
And DON'T forget the closing bracket:-). If you want a submenu, add the same code between the brackets of the menu.
The syntax for adding a program to a menu is like this:

```
prog "NameOfProg" pathtoiconofprog commandtoexecute
```

You don't have to use the " " in the name of the program if it's a single word, but with them you can use spaces in the name. 
The path to the icon for the program is nine out of ten times /usr/share/pixmaps/nameofprogram.png. If this doesn't work, try .xpm instead of .png. If that doesn't work, you have to do a bit of searching around.....
So, if for example, we want to create an 'Internet' menu, with a 'Browser' submenu, with 'Firefox' in there, you need the following:

```
menu "Internet" folder {
    menu "Browser" folder {
    prog "Firefox" /usr/share/pixmaps/firefox.png firefox
    }
}
```

In the same way you can add programs to your toolbar, only then you have to edit ~/.icewm/toolbar ( DUH ).
Have a look at the other files in~/.icewm as well, especially the preferences. They shouldn't be too much trouble now. Don't change the programs file though, as it is maintained by the menu package.

Also don't forget to have a look int the themes menu in the Icewm menu ( Icewm->themes) I personally like the SilverXP a lot; looks very slick.

Hope I helped some people out with this HOWTO; any comments are very welcome!!! Many thanks to the Ubuntu developers for making this happen and to the Ubuntu community for being so alive and kicking!

---

### Post by Googler on 2006-05-15
easier way:
```
sudo apt-get install icewm rox icewm-themes
```
;)

i don't like to install icewm-themes "ugly themes" , instead download your prefered theme and extract it 
and .....
```
mkdir ~/.icewm/themes
```
copy your extracted theme folder to ~/.icewm/themes

and load it from the menu

---

### Post by jon_benge on 2006-05-26
Peter, this is an awesome tutorial so thanks :D 

If anyone is looking for some iceWM eyecandy, download [THIS SKIN]("http://themes.freshmeat.net/projects/icebuntu/") and install it following Googler's advice.

Next, open up a terminal and type:

```
sudo apt-get install gtk-theme-switch gtk2-engines-ubuntulooks
```

Then

```
update-menus
```

Click the iceWM menu > Programs > Apps > Tools > GTK+ 2.0 Theme Switch.

Click the drop down box and select 'Human', then click 'Apply'.

EDIT: Thought i'd post some screenshots :)

---

### Post by jon_benge on 2006-05-26
> **Peter]There's no trash by default in Rox said:**
> http://www.hayber.us/rox/misc/Rubbish-001.tgz[/url]
Extract the file:

You can also add that wastebasket to the 'right click file menu'.

Simply right click a file and choose 'Customise Menu'. A new ROX window will open and a message will appear. Simply drag the wastebin icon from the desktop into this new Window. A menu will appear and you need to choose 'Relative Link'.

From now, whenever you right click that file type, you will see 'Rubbish' in the menu. The downside is that you have to repeat this proceedure for everything single file type! ](*,)

---

### Post by Peter76 on 2006-05-28
Hi John, thanks for your suggestions, especially the one about the wastebasket, I was looking for something like that...
I've been quite busy with work lately, but when I have some time, I'll look if there's an easy way to set the procedure for all files... There is a file for ROX about MIME types, think there might ly a clue...

---

### Post by dmizer on 2006-05-29
[QUOTE=jon_benge]Peter, this is an awesome tutorial so thanks :D 

```
sudo apt-get install gtk-theme-switch gtk2-engines-ubuntulooks
```[/QUOTE]
um ... i can't find gtk2-engines-ubuntulooks in my repository anywhere.  i find that extremely odd.

but i concur, even though i don't have an appealing theme up yet, i do appreciate the tutorial.  i didn't expect to get icons without taking a bigger hit on my resources.

---

### Post by jon_benge on 2006-05-29
I got the 'gtk2-engines-ubuntulooks' package from the Dapper repositories. 
I can't remember whether it's in the main/restrictive or universal repositories.

It may be available in the Breezy repositories too, but under a different name. Try searching for it with:

```
sudo apt-cache search ubuntulooks
```

or

```
sudo apt-cache search gtk2 engines
```

---

### Post by dmizer on 2006-05-29
yeah ... i tried searching for gtk2, gtk2-engines, gtk2 looks, ubuntulooks ... i really can't find it.  all i found is clearlooks.

i'll keep looking and see if i can find it, but it looks like it might be a dapper only package.

never the less, i am extremely happy with the way this turned out.  thanks for the how to.

---

### Post by jon_benge on 2006-05-30
Clearlooks is a good theme, much better then the standard GTK themes.

---

### Post by dmizer on 2006-06-07
how do i put mounted drives on the desktop as a folder?  i don't need auto mount, but i'd like to place a folder for my network drives on the desktop for easy access.

edit:
okay, i'm an idiot.  i just went back and read the first post.  i just drag the mounted folder to the desktop and shezam ... folder on desktop.  lol

how about this ... is there a way to make that folder appear automatically every time i mount the drive?

---

### Post by Peter76 on 2006-06-08
> how about this ... is there a way to make that folder appear automatically every time i mount the drive?

Hi dmizer, I have heard about a program called ivman which should do that. Have not looked into that yet. Also wondering what Xubuntu uses. If you or somebody else comes up with something, please let me know.

Cheers, Peter

---

### Post by dmizer on 2006-09-17
this method is no longer working for me.  i can't get rox filer to take over the icewm desktop.

---

### Post by Peter76 on 2006-09-18
Hey Dmizer, what happened??? Is this under Edgy? Please explain...

---

### Post by dmizer on 2006-09-19
nope ... not under edgy.  please file this one under "typo"

in copying and creating the necessary files, i neglected to include the all important "~"

i have it up and working as it should now.  thanks.

edit:
i swear to god, i'm not usually this bad.

---

### Post by Peter76 on 2006-09-19
:-)

---

### Post by BLTicklemonster on 2006-11-25
Thank you. I have been using icewm off and on for a while now, but haven't been able to get any functionality out of it (like I want), but now I have some more control over things with rox-filer. I even have a wall paper now! 
thanks a lot!

---

### Post by BLTicklemonster on 2006-11-26
How does one add something to the toolbar that needs to run in terminal?

prog "Vmware" /home/my/images/image.png what_do_I_put_here?

---

### Post by Peter76 on 2006-11-27
Hi BLTicklemonster, nice you good use my how-to.
To get something to run in a terminal:

prog "Vmware" image.png xfce4-terminal -H -x vmware

if you use another terminal, have a look at the manpage wich options to supply; for xterm it would be -hold and -e ( you can use -e with xfce4-terminal as well though ) 
The -H/-hold option leaves the window open after the program finishes; can be handy if something goes wrong and you want to see the output... Otherwise omit it.
Good luck

---

### Post by BLTicklemonster on 2006-11-27
Excellent! Now I have the gnome-terminal button I wanted, but ... well, 

> man gnome-terminal (1) - is a terminal emulation application.
NAME

gnome-terminal - is a terminal emulation application.
SYNOPSIS

gnome-terminal [-e, --command=STRING] [-x, --execute ] [--window-with-profile=PROFILENAME] [--tab-with-profile=PROFILENAME] [--window-with-profile-internal-id=PROFILEID] [--tab-with-profile-internal-id=PROFILEID] [--role=ROLE] [--show-menubar] [--hide-menubar] [--geometry=GEOMETRY] [--disable-factory] [-t, --title=TITLE] [--working-directory=DIRNAME] [--usage] [-?, --help] 

That is one thing that bothers me about looking up information. It's written like .. well, for people who don't need information. I mean really, if you understand all that, shouldn't you be able to just figure this stuff out in your sleep?

I have found that

```
prog    "WindowsXPPro" /home/bill/images/xp.png gnome-terminal -e -x sudo vmware
```

generates a real neat bug report. But I can't open vmware with a bug report... 

So if you could shed some light on what all that cryptic stuff is up there, that would be nice, otherwise, if you could share with me, oh great and wonderful Peter76 (happy 30th birthday, by the way. I'm guessing the 76 is your birthday...), the I would be most grateful.

---

### Post by Peter76 on 2006-11-28
Hi BLTicklemonster, yes manpages are something in an arcane language that you have to get used to.... I still don't get them till I'v read 'em about ten times... Patience and Google is the thing here.
Anyway, in your command you should only use either -x or -e. In your case -x ( read the man here ) :-)
Gnome terminal doesn't support the -H option. Have a lokk at xfce4-terminal, it is much lighter than Gnome-terminal. Hope this solves your problem, otherwise, post again. And thanks for the congratulations, you're right there :-)

---

### Post by jdackle on 2007-07-27
Great thread! Helped a lot!
I was actually trying to setup openbox with rox but then got advised to try icewm. And that was a good advice!

This thread and all that contributed really heped me get started in an easy way! Thanks! :)

---

