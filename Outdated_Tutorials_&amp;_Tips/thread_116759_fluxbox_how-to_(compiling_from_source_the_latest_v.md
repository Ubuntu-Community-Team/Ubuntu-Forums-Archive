---
title: "fluxbox how-to (compiling from source the latest version) plus tips &amp; tricks"
date: 2006-01-13
forum: Outdated Tutorials &amp; Tips
---

### Post by otake-tux on 2006-01-13
I'm a big fan of fluxbox. It is highly and easily customizable.  It's wicked fast and it's very pretty.  FLuxbox is in the ubuntu repositories but they are two versions behind and are missing a lot of handy features like fluxbox-generate_menu.  Also, the package in the repositories loads really slow wich should not be the case for a window manager that's supposed to be really fast. 

In this how-to I'm going to sum up all the info I have collected and add a few of my own customization tricks.  Most of what's here I found on other threads, but this info should be in one well organized place so here goes.

1: Download the source tar ball of the latest development version.  The stable version is too old and not supported anymore and the development version is the one the devs recommend.  They actually state 
"The latest stable release is v0.1.14. Development version of Fluxbox can be found here. Please note that 0.1.14 is actually fairly dated (and unmaintained) now, and the development series is quite stable. It is mainly waiting on translation and documentation work before it becomes stable. "

Get the source tarball [here]("http://fluxbox.sourceforge.net/version-0.9.php")

2: Get the tools to compile from source 
```
sudo apt-get install build-essential checkinstall xlibs-dev
```

3: Open your favorite terminal and  untar the file you downloaded. example :
```
tar xvzf fluxbox-0.9.14.tar.gz
```

4: cd into the directory created.

5: Type  ```
./configure --enable-kde --enable-gnome --disable-xmb
``` the disable xmb fixes the slow start up time in ubuntu.

6: Type make .

7: Type sudo checkinstall. This builds the package and puts it in /usr/local/bin

8: There are two ways to be able start fluxbox 

        a)  A .xsession file in your home directory. you may have it or not. if you dont create it.in the terminal type nano ~/.xsession and put this in there ```
exec /usr/local/bin/fluxbox
```

        b) Use you're start up file.  Type nano ~/.fluxbox/startup (if it does not exist, create it) and put this in there```
exec /usr/local/bin/fluxbox -log ~/.fluxbox/log
```

I encourage to use option b, since this is the one I use and I know it works well.

9:  Now to enter kde,gnome or any other window manager I use GDM. It comes standard in Ubuntu.  I know how to make an entry for fluxbox in GDM, I do not know how to do it in the others. To make an entry for fluxbox in GDM in a terminal type ```
cd /usr/share/xsessions
```
now type ls. There should be various files in there with names like gnome.desktop .  Type nano fluxbox.desktop. put this in there :
```
[Desktop Entry]
Encoding=UTF-8
Name=Fluxbox
Comment=This is fluxbox
Exec=/home/(username)/.fluxbox/startup

``` 
That is if in step 8 you chose option b. if you chose option a, on the Exec line          put Exec=/home/(username)/.xsession .       

10: Logout. Now when you go to GDM there will be a fluxbox entry in the session menu. Enter fluxbox.  If it works, you are done with the installation.  To access the menu just right click anywhere in the desktop.  I know that what you have now is pretty bare. But the rest is just customization.

**Customization Tips and Tricks**

Fluxbox is all about minimalism.  I like to use light apps to keep everything really fast so thats the type of tricks I know so here goes. 

1: To get  backround image, open a terminal and type sudo apt-get install feh
then locate the image you want to use as wallpaper. in my case my backrounds are in a directory called wallpapers in my home directory so to set a backround I type at the command line ```
fbsetbg wallpapers/wallpaperofmychoice.png
```

To not have to type all of that every time you want to set a new backround edit your start up file ```
nano ~/.fluxbox/startup
``` add the following line to that file :  ```
fbsetbg -l 
```  this command will always load the last image you set as backround so you only have to type fbsetbg image.png once.  

2: Apps you want to have upon start up are set at the ~/.fluxbox/startup file.  Here's my startup file as an example:
```
# fluxbox startup-script:
#
# Lines starting with a '#' are ignored.
fbsetbg -l
gkrellm &
gnome-volume-manager &
xscreensaver -nosplash &

``` 
first line sets my wallpaper, second starts grellm (a graphical system monitor), the fourth line you will want to have (gnome-volume-manager &) this will automount dvd's, USB  hdd's and loads of other stuff. I actually have a lot more stuff in my startup file but I'm keeping it simple to get you started.

I know many more tips and tricks and other users probably know more than I do.  I would like this thread to have all the nice things you can do  in fluxbox so plz if you know any customization tricks, post them.

This was my first how-to so point out any mistakes.  I will correct them.  Fluxbox is a great window manager.  I think the main reason its not so famous amongst the ubuntu community is because the package in the repositories is just worng.
my Fully customized desktop
[[IMG]http://ubuntuforums.org/gallery/files/5/4/3/1/2/desk_thumb.jpg[/IMG]]("http://ubuntuforums.org/gallery/files/5/4/3/1/2/desk_original.jpg")

edit- fixed the checkinstall typo.

---

### Post by eriqk on 2006-02-04
Very cool, thanks! The difference is impressive. I think it reduced the time it took to log in from nearly a minute to 10 seconds (this is a very slow machine).
Thanks again, very helpful.

Groet, Erik

---

### Post by kevcart3 on 2006-02-05
I know this isn't a big problem, but just to avoid confusion, you might want to change "sudo check install" to "sudo checkinstall" :p

Thanks for the guide though, I didn't actually realize I had such an old version of fluxbox installed :O

---

### Post by i3dmaster on 2006-02-05
Thanks for your HowTo!

---

### Post by Iandefor on 2006-02-06
[quote=otake-tux]I know many more tips and tricks and other users probably know more than I do. I would like this thread to have all the nice things you can do in fluxbox so plz if you know any customization tricks, post them.

This was my first how-to so point out any mistakes. I will correct them. Fluxbox is a great window manager. I think the main reason its not so famous amongst the ubuntu community is because the package in the repositories is just worng.
my Fully customized desktop
[IMG]http://ubuntuforums.org/gallery/showimage.php?i=1747&original=1&c=4[/IMG][/quote] I love fluxbox for it's speed (loads in about a second). I'd really like to stick with it, but here is a few question I've got:
How do I change the GTK themes?

---

### Post by ganatronic on 2006-02-06
Thank you. I've been meaning to try fluxbox for a while (I was waiting to reformat my laptop, but then after I reformatted I forgot about trying it ;).

I got it working, but I had a problem (I'm not an ubuntu master, which is probably why I hit a problem. so bear with me, please). My problem was based around steps 8 and 9. For step 8, I decided to first do option b. I had installed everything in a directory I created: /home/myname/fluxbox/ . So for step 8 I renamed the directory to /home/myname/.fluxbox.

Then I did as you suggested: nano ~/.fluxbox/startup 
and pasted in the line from b.

I added the fluxbox.desktop file.

Logged out, chose fluxbox, and then received an error telling me that /home/myname/.fluxbox/startup was not found, and so xsessions couldn't start. I'm guessing my mistake is a basic one, but I'm just not seeing it. I created the /home/myname/.fluxbox/startup file -- it is there -- so why's it saying it's not?

I got it to work by following option a. in step 8. I created a file called .xsession in the home directory. However, when logging in I received the same error (except this time saying it couldn't find /home/myname/.xsession -- and then it asked if I wanted to proceed with my default session (gnome), I said okay, and lo, it didn't send me to gnome, but sent me to fluxbox. Weird, but for now I'm happy.

Perhaps I'm not creating files in the correct manner. Or I'm creating them in the wrong location.

But man, fluxbox is so fast and simple. I love having zero clutter. All I need to do is customize little toolbar, and I'm good to go. Thanks!

---

### Post by no1wantdthisname on 2006-02-06
You have to 
```
chmod +x ~/.fluxbox/startup
```
to get it to work.

---

### Post by rado_london on 2006-02-06
That is brilliant. I thought that XFCE is fast but I changed my opinion.
Thanks a lot.

---

### Post by ganatronic on 2006-02-06
[QUOTE=no1wantdthisname]You have to 
```
chmod +x ~/.fluxbox/startup
```
to get it to work.[/QUOTE]

Thanks. That did it.
I tend to go through periods where I rarely use the terminal, and then I forget basic things.

---

### Post by evs on 2006-02-07
Excellent Howto.  I never realized the Breezy package was so outdated.  After reading your guide I decided to try something out.  Instead of compiling myself, I changed all the "breezy"s in my /etc/apt/sources.list to "dapper" and did ```
sudo apt-get update && sudo apt-get install fluxbox
```  The Dapper package is 0.9.14-1.  I don't know if it was compiled w/ xmb disabled like you suggested, but it's definitely faster than the Breezy package - it started up in 4 seconds on my AMD Sempron 3000, 512 MB ram.  If anyone else goes this route, just don't forget to change /etc/apt/sources.list back to breezy.

---

### Post by Rev. Nathan on 2006-02-07
Installed just great! Thanks. Although I'm not really digging Fluxbox. Too light? This will be great when I nab an old system.

---

### Post by mohapi on 2006-02-07
Very nice. And *very* fast. Given I can work out the quirks, this might be my desktop of choice from now on. Cheers!

---

### Post by yabbadabbadont on 2006-02-07
The Fluxbox homepage lists a source for a Debian package of 0.9.14-1.

On that page, the maintainer has provided a deb file specifically for Breezy.

[http://logicvortex.net/debian/fluxbox/]("http://logicvortex.net/debian/fluxbox/")

Much easier than building yourself.  (not as much fun though)

---

### Post by johannes on 2006-02-07
[QUOTE=Iandefor]How do I change the GTK themes?[/QUOTE]
Add "gnome-settings-daemon &" (without quotes) on startup. That will load the theme you set in Gnome.

---

Thanks for the how-to by the way. :)

---

### Post by yabbadabbadont on 2006-02-07
You could also install gtk-theme-switch.  Then run 'switch' to change your gtk 1 theme and 'switch2' to change your gtk 2 theme.

---

### Post by Installer36 on 2006-02-08
Just a quick note if you edit the  /etc/apt/sources.list and change to dapper I had to make sure it was dapper not Dapper..not sure if this was something I did wrong or just haow it worked for me...Thanks   Just checked it out and it worked by changing the apt/souces.list.....Almost to fast for me!

---

### Post by william_nbg on 2006-02-09
Mine is all set up, Works great!! Just playing around with everything a bit ...

has anyone here given 'fluxstyle' a try yet? It's the only thing I can't seem to get installed right.

---

### Post by kch_86 on 2006-02-09
I really like fluxbox, works great on my old dell latitude. But I have a couple of problems. 
1) I put the fbsetbg -l in my startup file but everytime I log in I get an error that says that there wasn't a previously stored background. But when I run the same command from xterm it replaces the background no problem.

2) Whenever I try to lower the transparency values for the title bar/window/slit nothing happens. I have ran these commands :  fluxbox -i and xdpyinfo | grep. And both of them say RENDER. And there isn't an option for the Menu transparency, there's alpha options for the slit and toolbar, but not one for the menu. So how can I change the transparency of the menu? I have the latest dev version f/m their site.

Any ideas? Help much appreciated.

---

### Post by yabbadabbadont on 2006-02-09
1) There should be a file in your ~/.fluxbox directory called lastbackground or lastwallpaper, something like that.  That is the file that is read by the fbsetbg -l command.  Also, the style you currently have selected can override that command, unless you put fbsetbg -l as the rootCommand option in your ~/.fluxbox/init file.

2) Look through the settings in your ~/.fluxbox/init file.  Just look for the pattern trans.  Make sure that the transparency related keys you find are all enabled and see if it helps.

---

### Post by kch_86 on 2006-02-09
I looked through the init file. I tried setting  - forcepseudotransparency and - decorateTransientWindow to true. I also tried setting the alpha channel for menu and windows to 150 and, but it didn't do anything.

---

### Post by yabbadabbadont on 2006-02-10
[QUOTE=kch_86]I looked through the init file. I tried setting  - forcepseudotransparency and - decorateTransientWindow to true. I also tried setting the alpha channel for menu and windows to 150 and, but it didn't do anything.[/QUOTE]

I would suggest installing fluxbox using the deb package found here [http://logicvortex.net/debian/fluxbox/](http://logicvortex.net/debian/fluxbox/)

There is a package of the latest version built specifically for Breezy there.  I just installed it and verified that the alpha options are all present.  You have to take the option to restart fluxbox from the menu to make any alpha changes take effect though.

The specific steps that I took were:
1) sudo -s -H
2) apt-get install menu   (dependency of the deb package that I pointed you to)
3) dpkg -i fluxbox_0.9.14-1_i386.deb
4) logout and login using failsafe xterm session
5) sudo update-menus
6) startfluxbox                (this will create a proper ~/.fluxbox directory structure)
7) ctrl-alt-backspace       (for some reason, fluxbox didn't startup all the way)
8) select the fluxbox session from GDM and login.

Everything worked properly from that point on.

---

### Post by kch_86 on 2006-02-13
alright, I followed your instructions exactly. When I ran startfluxbox, I got a bunch of errors. All the ones that I could see were like:  failed to set  session.somevalue. I don't know what's going on. My laptop has an old ati rage 128 graphics card, would this have anything to do with it?

---

### Post by yabbadabbadont on 2006-02-13
Your video card shoudn't have anything to do with it.  Fluxbox runs on top of X, and as long as you see the GDM login screen, it should work too.

The errors/warning messages are normal the first time a user runs fluxbox.  It just means that there isn't an init file in the .fluxbox directory yet.  (or an incomplete one)  It should create a default ~/.fluxbox/init file for you after it displays those messages.

As I said in my instructions, for some reason, fluxbox didn't start up all the way (I just got a black screen) and I had to kill X with ctrl-alt-backspace.  After that, selecting a fluxbox session from GDM worked fine.

When you originally built fluxbox from source, did you use checkinstall so that it was installed from the created deb package?  Either way, did you uninstall the old version before installing the package I suggested?  Since you had been using fluxbox before, did you remove or rename your ~/.fluxbox directory before following my instructions?  (I forgot to suggest that in the steps I listed, sorry)

These are just some things to try.  I switched back to Gentoo (again), so I'll have to get Breezy installed in vmware before I'll be able to try to troubleshoot this some more.

---

### Post by kch_86 on 2006-02-13
yeah i did ctrl-alt-backspace after I ran startfluxbox for the first time. I renamed my .fluxbox file before I installed with the .deb. I'll try and install again and use checkinstall to make sure it was installed from the deb package.

---

### Post by l0c0dantes on 2006-02-15
How do I set my screen resolution tho? right now im at the amazingly tiny 1600x1200 >_<

---

### Post by yabbadabbadont on 2006-02-16
You can use ctrl-alt-(numeric keypad)+ and ctrl-alt-(numeric keypad)- to change it temporarily or you can edit your /etc/X11/xorg.conf file.

```
Section "Screen"
        Identifier      "Screen0"
        Device          "Card0"
        Monitor         "Monitor0"
        DefaultDepth    24
        SubSection      "Display"
                Viewport        0 0
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection      "Display"
                Viewport        0 0
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection      "Display"
                Viewport        0 0
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection      "Display"
                Viewport        0 0
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```
Only include the screen resolutions that you want to allow.

---

### Post by topper_harley on 2006-02-16
How can I edit the startup file to make a certain application to start on a certain desktop?

For example, on startup, I would like to run Firefox on desktop 2 and Eterm on desktop 1 and 3.

Is it possible?

Thanks,
Andrea

---

### Post by yabbadabbadont on 2006-02-16
It is possible to do some of this by using the apps file in the ~/.fluxbox directory.  However, I'm not sure about having two Eterms on two different desktops automatically.  Read through this [http://fluxbox-wiki.org/index.php/Howto_edit_the_apps_file](http://fluxbox-wiki.org/index.php/Howto_edit_the_apps_file) for how to do this.

Actually, after reading through that link myself, I think you can do what you want.  You will have to include the -name option on the command line when you launch Eterm.  You will need to give each instance a different name so that the settings for that specific instance can be saved in the apps file.  The wiki article sort of gives an example of this using xterm, but Eterm supports the -name option too.

---

### Post by topper_harley on 2006-02-17
I think Eterm supports the -n option instead of -name, but should work the same.
I prefer Eterm because I can have completly transparent terminals with this command:
Eterm -O -x -f white --scrollbar 0 --buttonbar 0 

Thanks for your help!!!

---

### Post by topper_harley on 2006-02-17
The "-n" trick worked great!!!
I have a different terminal in each workspace! :)

Now I have another question:
I've ridden in the docs that fliuxbox doesn't have built-in session manager. Is it possible to use an external one? Maybe Gnome-session?

I can restart or halt my laptop using the command line but I don't know how to suspend to ram and suspend to disk without a session manager. Can anybody explain me how to?

Thanks...

---

### Post by l0c0dantes on 2006-02-17
Hello there! Well, I figgured out how to change my screen resolution (found the path for the gnome control center and put it on my menu) However, I now have another problem. I would like to have a graphical way to access my files, but whenever i run nautilus, it will replace the fluxbox wallpaper, Kill my right click menu, and kill my App bars. Is there a way I can Take care of that? Or, will I need to get much more familiar with my local terminal >_<

---

### Post by topper_harley on 2006-02-18
[QUOTE=l0c0dantes]Hello there! Well, I figgured out how to change my screen resolution (found the path for the gnome control center and put it on my menu) However, I now have another problem. I would like to have a graphical way to access my files, but whenever i run nautilus, it will replace the fluxbox wallpaper, Kill my right click menu, and kill my App bars. Is there a way I can Take care of that? Or, will I need to get much more familiar with my local terminal >_<[/QUOTE]
Try nautilus --no-desktop --browser
or install rox-filer

---

### Post by yabbadabbadont on 2006-02-18
PC Man FM (pcmanfm) is a very nice file manager.  I don't think it is in the repositories, but there are deb packages on it's sourceforge files page.

Homepage: [http://pcmanfm.sourceforge.net/](http://pcmanfm.sourceforge.net/)

Packages: [http://sourceforge.net/project/showfiles.php?group_id=156956](http://sourceforge.net/project/showfiles.php?group_id=156956)

---

### Post by topper_harley on 2006-02-18
> PC Man FM (pcmanfm) is a very nice file manager. I don't think it is in the repositories, but there are deb packages on it's sourceforge files page.

Homepage: [http://pcmanfm.sourceforge.net/](http://pcmanfm.sourceforge.net/)

Packages: [http://sourceforge.net/project/showf...roup_id=156956](http://sourceforge.net/project/showf...roup_id=156956)

That's a very nice file manager! ...and also works with tabs like firefox!!

Now the only thing I need is a session manager...

How do you shut down your computer with fluxbox? Just "sudo halt" or what?

---

### Post by yabbadabbadont on 2006-02-18
If you are using a graphical login manager, like GDM, then just exit fluxbox and then select shutdown from there.  If, like me, you login to the text console, exit fluxbox and sudo poweroff.

(actually, I'm running Gentoo nowdays, so I use su instead of sudo)

---

### Post by topper_harley on 2006-02-19
[QUOTE=yabbadabbadont]If you are using a graphical login manager, like GDM, then just exit fluxbox and then select shutdown from there.  If, like me, you login to the text console, exit fluxbox and sudo poweroff.

(actually, I'm running Gentoo nowdays, so I use su instead of sudo)[/QUOTE]

And how do you suspend to ram or hybernate?

---

### Post by yabbadabbadont on 2006-02-19
> And how do you suspend to ram or hybernate?
I don't.  However a simple search of these forums for "howto hibernate" returned many threads that look useful.  I hope that helps you find what you need.

---

### Post by Nategoofs on 2006-02-20
Hi,
   When i get to the point where im inside the cd /usr/share/xsessions directory, I can type nano fluxbox.desktop but when i put in 
[Desktop Entry]
Encoding=UTF-8
Name=Fluxbox
Comment=This is fluxbox
Exec=/home/(username)/.fluxbox/startup

and try and save it, it says "[ Error writing fluxbox.desktop: Permission denied ]".  What can i do to correct this?
Thanks

---

### Post by Spano on 2006-02-20
> I can type nano fluxbox.desktop

I think you need to type "sudo nano fluxbox.desktop" (minus the quotes)
As super user you'll have permission to change the contents of the file.

---

### Post by m666 on 2006-02-21
how to switch to other user in fluxbox, letting main session work in background?
(multiple sessions)?

---

### Post by Nategoofs on 2006-02-21
Thanks, but now it says it couldn't find /home/myname/.xsession -- and then it asked if I wanted to proceed with my default session (gnome) and i looked at the beginning of this thread and i tried the chmod +x ~/.fluxbox/startup command, but i dont know if i did it right.  Is there i certain directory i need to be in?  If not, what else can i do to correct this?

---

### Post by topper_harley on 2006-02-21
Will Fluxbox work better with the XGL that will come with Dapper?

Is it possible to try XGL with Breezy and Fluxbox?

---

### Post by topper_harley on 2006-02-22
Well...
That's me surfing in this site with fluxbox...


[http://i1.tinypic.com/oaoz2x.png](http://i1.tinypic.com/oaoz2x.png)

Thanks to everybody for your help!!!

---

### Post by dccool879 on 2006-02-23
[QUOTE=ganatronic]Thank you. I've been meaning to try fluxbox for a while (I was waiting to reformat my laptop, but then after I reformatted I forgot about trying it ;).

I got it working, but I had a problem (I'm not an ubuntu master, which is probably why I hit a problem. so bear with me, please). My problem was based around steps 8 and 9. For step 8, I decided to first do option b. I had installed everything in a directory I created: /home/myname/fluxbox/ . So for step 8 I renamed the directory to /home/myname/.fluxbox.

Then I did as you suggested: nano ~/.fluxbox/startup 
and pasted in the line from b.

I added the fluxbox.desktop file.

Logged out, chose fluxbox, and then received an error telling me that /home/myname/.fluxbox/startup was not found, and so xsessions couldn't start. I'm guessing my mistake is a basic one, but I'm just not seeing it. I created the /home/myname/.fluxbox/startup file -- it is there -- so why's it saying it's not?

I got it to work by following option a. in step 8. I created a file called .xsession in the home directory. However, when logging in I received the same error (except this time saying it couldn't find /home/myname/.xsession -- and then it asked if I wanted to proceed with my default session (gnome), I said okay, and lo, it didn't send me to gnome, but sent me to fluxbox. Weird, but for now I'm happy.

Perhaps I'm not creating files in the correct manner. Or I'm creating them in the wrong location.

But man, fluxbox is so fast and simple. I love having zero clutter. All I need to do is customize little toolbar, and I'm good to go. Thanks![/QUOTE]

i had the same problem as you, and i went back to the console and typed in chmod +x ~/.fluxbox/startup, yet im still getting the  cannot find startup. help??

---

### Post by darkfusion on 2006-02-24
I cant seem to get any terminal I use to be transparent . Gnome-terminal,aterm and eterm all wont . Any idea why ?

Edit:/// Fluxbox seems to be working now , Strange .

---

### Post by eriqk on 2006-02-24
[QUOTE=darkfusion]I cant seem to get any terminal I use to be transparent . Gnome-terminal,aterm and eterm all wont . Any idea why ?

Edit:/// Fluxbox seems to be working now , Strange .[/QUOTE]

You need to start aterm with the appropriate options. You'll find them with "aterm --help".

Unless, of course, this is what you've been doing. I that case, I have no idea.

Groet, Erik

---

### Post by otake-tux on 2006-02-24
I gotta tell you, these forums beave in very strange ways.  When I wrote this thread I submitted it and then went to check if its was posted.  I swear to GOD it would not appear in my thread history nor my post history.  If I had known it been posted I would have been more active.

That being said,  pretty soon I'm going to start writing a GUI app to get icons on the fluxbox deskstop.  This GUI will use idesk to put the icons on the desktop.  All the user will have to do is choose the icon and its command.  I'm still not decided as to which language to use for this.  I'm torn between python and java :-k .  It cant be C cause I don't have that much time. 

I promise to be more active in this thread and I thank all of you for your responses. :)

---

### Post by yabbadabbadont on 2006-02-24
[QUOTE=otake-tux]That being said,  pretty soon I'm going to start writing a GUI app to get icons on the fluxbox deskstop.  This GUI will use idesk to put the icons on the desktop.  All the user will have to do is choose the icon and its command.  I'm still not decided as to which language to use for this.  I'm torn between python and java :-k .  It cant be C cause I don't have that much time. [/QUOTE]

That sounds nice.  However, such a tool already exists and (I believe) is listed on the idesk homepage.  It is called idesktool.  It is a simple GUI wizard for adding, removing, and configuring desktop icons using idesk.  Of course, more choices are always nice, so I look forward to seeing what you produce.  Good luck on your project.

EDIT: See [here](http://www.jmurray.id.au/ideskconf.html) and [here](http://users.netwit.net.au/~pursang/idesk-extras.html) for both the tool and some other idesk goodies.

---

### Post by ganatronic on 2006-02-25
[QUOTE=dccool879]i had the same problem as you, and i went back to the console and typed in chmod +x ~/.fluxbox/startup, yet im still getting the  cannot find startup. help??[/QUOTE]

I'm not sure what to advise. Maybe try creating the startup folder with "sudo nautilus"? maybe that'll take it more seriously (you can tell I'm a pro, huh?). and then do the chmod. 

Is the "Exec=/home/(username)/.fluxbox/startup" in /usr/share/xsessions correct? Did you try both versions of step 8 (version A, and then version b)?

---

### Post by skorange on 2006-02-25
Hey all,

I've built the deb from source and am enjoying fluxbox.  My only issue is that when booting into fluxbox I seem to lose the config settings for my synaptics touchpad i made in the /etc/X11/xorg.conf file.  The touchpad works, but the driver seems to not be loaded as features like scroll bar sliding, etc don't function anymore (the settings work fine in kde)

any suggestions?

---

### Post by skorange on 2006-02-25
nevermind, figured it out.  my problem had nothing to do with fluxbox ;) which makes  sense.

---

### Post by m666 on 2006-02-25
[QUOTE=dccool879]i had the same problem as you, and i went back to the console and typed in chmod +x ~/.fluxbox/startup, yet im still getting the  cannot find startup. help??[/QUOTE]
[http://fluxbox-wiki.org/index.php/Howto_update_fluxbox#Using_Ubuntu](http://fluxbox-wiki.org/index.php/Howto_update_fluxbox#Using_Ubuntu)
It worked for me, 'startup' file was made automatically and fluxbox is starting up faster.

---

### Post by Kiwinote on 2006-02-25
When I do step 7 I get this error:
kiwinote@Kiwinote:~/Desktop/fluxbox-0.9.14$ sudo check install
Password:
sudo: check: command not found

Any ideas what's going wrong?

Thanks,
Kiwinote

---

### Post by xtacocorex on 2006-02-25
Kiwinote:
It should be checkinstall as one work.

Now for my question. I installed Fluxbox from the repos a couple of months ago and greatly enjoy it. One thing I found is that when I log in through KDM, it starts a whole bunch of non-needed KDE services. Is there any way to prevent this?

---

### Post by mrgnash on 2006-02-27
For some reason, none of the programs I list in my .fluxbox/startup file actually start up when I log into Fluxbox :( This problem has persisted from the old version of Flux I was using to the latest one I installed through following this guide. I can't work it out...

---

### Post by ToastedToad on 2006-02-27
[QUOTE=mrgnash]For some reason, none of the programs I list in my .fluxbox/startup file actually start up when I log into Fluxbox :( This problem has persisted from the old version of Flux I was using to the latest one I installed through following this guide. I can't work it out...[/QUOTE]


Can you post your /home/user/.fluxbox/startup?

Are you using the "&" after every entry?

Seems that since it has happened on two different flux installs, it would be a configuration error somewhere. Be it syntax or whatnot.

---

### Post by mrgnash on 2006-02-27
Sure thing:

```
# MrGnash's Fluxbox startup script

# Programs which need to run constantly, as opposed to a one time execution need "&" at the end of a command.

exec /usr/local/bin/fluxbox -log ~/.fluxbox/log
gnome-terminal &
opera &
gaim &
gnome-volume-manager &
```

---

### Post by Kiwinote on 2006-02-27
When I try step 8b I can edit the file, but then it wants File Name to write when I save it, what should this be?

Kiwinote

---

### Post by mrgnash on 2006-02-27
[QUOTE=Kiwinote]When I try step 8b I can edit the file, but then it wants File Name to write when I save it, what should this be?

Kiwinote[/QUOTE]

It should just be: startup

---

### Post by Kiwinote on 2006-02-27
When I start up fluxbox I get an error that implies that it can't find Fluxbox. I looked around and in usr/share/xsessions I can click on GNOME, but when I try to click on Fluxbox I get this error:
Couldn't display "/usr/share/xsessions/fluxbox.desktop".
The location is not a folder.

Any ideas what to do about this?

Kiwinote

---

### Post by Kiwinote on 2006-02-27
Finally, I'm in Fluxbox. :-D :-D :-D  
I didn't have the right permissions set for the startup file. :(  
Now I still need to resolve some other problems with permissions, but at least I'm in Fluxbox. Later on in the week I may install it on my own computer, this was for my brother who I have finally convinced to use linux, but he isn't impressed about the speed and wants it just as fast as win98!!! Got to try and speed up FF now.

Thanks for all the help,

Kiwinote

---

### Post by Kiwinote on 2006-02-27
//EDIT Double post

---

### Post by yabbadabbadont on 2006-02-27
[QUOTE=mrgnash]Sure thing:

```
# MrGnash's Fluxbox startup script

# Programs which need to run constantly, as opposed to a one time execution need "&" at the end of a command.

exec /usr/local/bin/fluxbox -log ~/.fluxbox/log
gnome-terminal &
opera &
gaim &
gnome-volume-manager &
```[/QUOTE]

The problem is that the programs you are trying to start will never run until you exit fluxbox.  As indicated by the comment in the file, you need to start your programs *before* the exec fluxbox line.  EDIT: Actually, the comment in your startup file is unclear about that.  Sorry.  END EDIT  If you use the exec command, processing of the script stops until the program that is "exec'd" exits.  If you need to start fluxbox first, so that it can draw the root window for example, then you need to change how it is started.  Here is my startup file as an example of how to do this.
```
# fluxbox startup-script:
#
# Lines starting with a '#' are ignored.

# This sets a black background

fbsetroot -solid black

# Turn off beeps:

xset -b

# Increase the keyboard repeat-rate:

xset r rate 250 30

# Start fluxbox in the background and save it's PID

/usr/bin/fluxbox &
fluxpid=$!

# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.

# Launch all registered desklets, but wait a little before starting
# so that fluxbox has time to draw the root window background

adesklets -d 3
gkrellm2 &
wmdrawer &

# Don't exit until the fluxbox process id exits

wait $fluxpid

```

---

### Post by mrgnash on 2006-02-27
That works perfectly now, thankyou :D

---

### Post by yabbadabbadont on 2006-02-27
You're welcome.  I'm glad it helped.

---

### Post by otake-tux on 2006-02-28
[QUOTE=yabbadabbadont]That sounds nice.  However, such a tool already exists and (I believe) is listed on the idesk homepage.  It is called idesktool.  It is a simple GUI wizard for adding, removing, and configuring desktop icons using idesk.  Of course, more choices are always nice, so I look forward to seeing what you produce.  Good luck on your project.

EDIT: See [here](http://www.jmurray.id.au/ideskconf.html) and [here](http://users.netwit.net.au/~pursang/idesk-extras.html) for both the tool and some other idesk goodies.[/QUOTE]


The reason I wanted to do this was for practice.  You know, as a hobby and a learning experience.  I didn't know about the idesk tools though.  You're post has slightly dismotivated me.  :(  Oh,well.  I might still do it.

---

### Post by ninocass on 2006-02-28
i cant seem to get the idesktool to work 

```

nino@laptop:/usr/bin$ idesktool
Xdialog found. So far so good..
idesk found - we're on a roll :)
Config. file  found - excellent!

```

thats all it says with no popups or anything

---

### Post by yabbadabbadont on 2006-02-28
[QUOTE=otake-tux]The reason I wanted to do this was for practice.  You know, as a hobby and a learning experience.  I didn't know about the idesk tools though.  You're post has slightly dismotivated me.  :(  Oh,well.  I might still do it.[/QUOTE]

Hey, don't let me stop you.  Like I said, more choices is better than fewer, and I *do* look forward to seeing what you produce.

---

### Post by yabbadabbadont on 2006-02-28
[QUOTE=ninocass]i cant seem to get the idesktool to work 

```

nino@laptop:/usr/bin$ idesktool
Xdialog found. So far so good..
idesk found - we're on a roll :)
Config. file  found - excellent!

```

thats all it says with no popups or anything[/QUOTE]

I've never had a problem with it, but I've only used it on Gentoo.  I'll have to install Breezy in VMware to see if I can reproduce your problem.  How did you install it?

---

### Post by gingermark on 2006-02-28
I use KDM and would prefer to continue to do so. I got up to part 8b. Does anyone know how to do part 9 in KDM? I have read through the whole thread, so apologies if I missed the answer.

EDIT: Part 9 also works for KDM.

---

### Post by maximegb on 2006-03-01
[http://ubuntuforums.org/gallery/files/5/4/3/1/2/desk_original.jpg](http://ubuntuforums.org/gallery/files/5/4/3/1/2/desk_original.jpg)

Are icons on your screenshot managed by idesk ?

---

### Post by Adrian_b on 2006-03-03
What do i do if the fonts of gnome-applications are WAY too small?(=> font size 28 is about size 12 in gnome)

---

### Post by yabbadabbadont on 2006-03-03
You could run gnome-settings-deamon in your ~/.fluxbox/startup file.  Or, if you are talking about gtk apps in general, you could install gtk-theme-switch and run switch (for gtk 1) or switch2 (for gtk 2) to set the theme and also the font used.

---

### Post by towsonu2003 on 2006-03-03
could you by any chance attach your startup thingy (all of it)? that would be a nice place to get started with what one (me) can do costumizing. thanks. nice howto (compiling now->hopefully this thing won't explode -knock on wood)

---

### Post by yabbadabbadont on 2006-03-03
If you mean the ~/.fluxbox/startup file, then here is mine:```
# fluxbox startup-script:
#
# Lines starting with a '#' are ignored.

# This sets a black background

fbsetroot -solid black

# Turn off beeps:

xset -b

# Increase the keyboard repeat-rate:

xset r rate 250 30

# Start fluxbox in the background and save it's PID

/usr/bin/fluxbox &
fluxpid=$!

# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.

# Launch all registered desklets, but wait a little before starting
# so that fluxbox has time to draw the root window background

adesklets -d 2
gkrellm2 &
idesk &

# Don't exit until the fluxbox process id exits

wait $fluxpid

```

If that isn't what you meant, please elaborate.

---

### Post by towsonu2003 on 2006-03-03
that was it, thanks! :)

---

### Post by towsonu2003 on 2006-03-05
just wanted to thank you for this fine howto. my 3rd ever'successful' compile :)

---

### Post by jinxjinx on 2006-03-06
when i boot up I get " fbsetbg: No previous wallpaper recorded for display :0 "
message. but when i type fbsetbg -l from the console it loads my background. what gives?
Thanks

btw fluxbox is awesome!

---

### Post by topper_harley on 2006-03-12
Where can I find an applet wich displays, on fluxbox toolbar or in a slit, the thumbnails of the other desktops like there is in gnome?

---

### Post by yabbadabbadont on 2006-03-12
That would be one of the pager applications.  Synaptic (with universe and multiverse enabled) shows bbpager and fbpager as two choices.  You will probably want fbpager as it was written for fluxbox.  There are others listed on fluxbox.org, but you would need to either build them from source or find a debian package.

Fluxter has a debian package on its homepage here [http://benedict.isomedia.com/homes/stevencooper/projects/fluxter.html](http://benedict.isomedia.com/homes/stevencooper/projects/fluxter.html)

---

### Post by topper_harley on 2006-03-13
Thank you, I've tried fbpager wich looks nice and is easy to costomize!

It also supports alpha transparency :)

---

### Post by jbennett on 2006-03-14
When I attempt to login to a fluxbox session, an error message pops up that says that the session failed to start because /home/justin/.fluxbox/startup cannot be found.  Here's what my ~/.fluxbox/startup file looks like:

```
exec /usr/local/bin/fluxbox -log ~/.fluxbox/log
```

And here's my /usr/share/xsessions/fluxbox.desktop

```

[Desktop Entry]
Encoding=UTF-8
Name=Fluxbox
Comment=This is fluxbox
Exec=/home/justin/.fluxbox/startup

```

Does anyone have any ideas about what might be causing this error?  I've checked and rechecked the location of everything and its all in the right place, as far as I can tell.

Thanks for any help.

---

### Post by sldonmtns on 2006-03-14
edit:fixed

---

### Post by yabbadabbadont on 2006-03-22
[QUOTE=jbennett]When I attempt to login to a fluxbox session, an error message pops up that says that the session failed to start because /home/justin/.fluxbox/startup cannot be found.  Here's what my ~/.fluxbox/startup file looks like:

```
exec /usr/local/bin/fluxbox -log ~/.fluxbox/log
```

And here's my /usr/share/xsessions/fluxbox.desktop

```

[Desktop Entry]
Encoding=UTF-8
Name=Fluxbox
Comment=This is fluxbox
Exec=/home/justin/.fluxbox/startup

```

Does anyone have any ideas about what might be causing this error?  I've checked and rechecked the location of everything and its all in the right place, as far as I can tell.

Thanks for any help.[/QUOTE]

You are making fluxbox call itself recursively...

I posted a proper ~/.fluxbox/startup file earlier in this thread (on the previous page or two) to use as a starting point.  You will need to change it to start the programs you want to run at fluxbox startup.  I also think your fluxbox.desktop file is wrong.  You don't call the startup file directly, it gets called by startfluxbox.  You should probably change the Exec= line to call startfluxbox instead.  Hopefully these two things will solve your issue.

EDIT: OK, I just went back and re-read the first post.  I'm surprised it works that way for anyone, but apparently it does.  (I sit corrected) :)  No other linux distribution I've used configures fluxbox that way though.  Try configuring it the way I suggested and see if it helps.  Personally, I don't use GDM when I have my system configured with fluxbox and instead login at the console.  I call startfluxbox in my .xinitrc and just run startx when I want to use it.  I'm running Gnome now because I want to play with compviz.

---

### Post by darkwarrior0404 on 2006-04-02
> 3: Open your favorite terminal and untar the file you downloaded. example :
Code:

tar xvzf fluxbox-0.9.14.tar.gz


4: cd into the directory created.

5: Type
Code:

./configure --enable-kde --enable-gnome --disable-xmb

the disable xmb fixes the slow start up time in ubuntu.

Okay, mine just goes all to crap and doesnt let me do anything lol... i cd'd into desktop where i created it, and typed in the code and it doesnt let me do anything? Help?

---

### Post by darkwarrior0404 on 2006-04-03
> 2: Get the tools to compile from source
Code:

sudo apt-get install build-essential checkinstall xlibs-dev


3: Open your favorite terminal and untar the file you downloaded. example :
Code:

tar xvzf fluxbox-0.9.14.tar.gz


4: cd into the directory created.

5: Type
Code:

./configure --enable-kde --enable-gnome --disable-xmb



I cant get past 2?? What directory do I need to be in ? ](*,)

---

### Post by Rikostan on 2006-04-03
Awesome.. thanks for this! I used Litestep for the last 5 years or so on my windows machines. It is a lot like fluxbox, but based on afterstep. I still find myself right clicking to access my menus on gnome. :) 

I also used fluxbox on a slower laptop I had Debian installed on and it was far faster than KDE and Gnome.

This will come in handy for my next ubuntu install which is going to be on an older Compaq m700 laptop.

---

### Post by jinxjinx on 2006-04-03
does anyone know if there's a way to use your mouse keys as key bindings in fluxbox/keys file?
Specifically I want my middle mouse button to close windows.
Thanks

---

### Post by johnraff on 2006-04-03
[QUOTE=darkwarrior0404]I cant get past 2?? What directory do I need to be in ? ](*,)[/QUOTE]I think when you untar that fluxbox gz file a new folder called "fluxbox-0.9.14" or something will be created to hold the files. That's the folder you want to move to.

---

### Post by boxingnun on 2006-04-04
I was about to abandon fluxbox because of the slow startup, then I found your how-to and I'm deleting all my other window managers. I've been working the bugs out, but I can't figure out how to get anti-aliased fonts. The option doesn't appear on the menus and I can't find any references to it in the init file. Thanks.

---

### Post by darkwarrior0404 on 2006-04-04
[QUOTE=johnraff]I think when you untar that fluxbox gz file a new folder called "fluxbox-0.9.14" or something will be created to hold the files. That's the folder you want to move to.[/QUOTE]


not a clue, i tried talking to a guy last night about it, and well were both stumped cause he tried talking me through the install and it kept just giving me errors, what steps do i need to follow straight through, im pretty lost :-k

---

### Post by jinxjinx on 2006-04-04
no one knows how to bind keys to the mouse?
Thanks!

---

### Post by yabbadabbadont on 2006-04-05
[QUOTE=boxingnun]I was about to abandon fluxbox because of the slow startup, then I found your how-to and I'm deleting all my other window managers. I've been working the bugs out, but I can't figure out how to get anti-aliased fonts. The option doesn't appear on the menus and I can't find any references to it in the init file. Thanks.[/QUOTE]

Add ```
session.screen0.antialias:      true
``` to your init file.

---

### Post by yabbadabbadont on 2006-04-05
[QUOTE=jinxjinx]no one knows how to bind keys to the mouse?
Thanks![/QUOTE]

As far as I know, you can't without hacking the source code yourself...  you can only define keys in the keys file.

Actually, middle-click is already handled specially.  If you middle-click the maximize button, the window will only maximize in the vertical direction.  Right-clicking that button will only maximize horizontally.

---

### Post by boxingnun on 2006-04-05
[QUOTE=yabbadabbadont]Add ```
session.screen0.antialias:      true
``` to your init file.[/QUOTE]

That was already in my init file, but I missed it somehow...sorry. Anyway, I changed the font in the style file from lucidasans to sans. Stupid problem with a simple fix...thanks for the help.

---

### Post by YuHoo on 2006-04-05
I compiled the latest cvs 0.9.15 and it went in without a hitch. But after several attempts I still can not figure out how to get the menu to have start functions beyond
```
Fluxbox default menu
-----------------------------
xterm
Restart
Exit
``` I don't know if there needs to be something else installed, or if I'm just missing something obvious. I do like the speed, but if all I get is a blueish theme and the terminal, well, I'll just do without the window manager.

---

### Post by eklypze on 2006-04-05
Everything seems to be going wrong for me today. I have tried to install this for a while now and it seems I am missing a bunch of dependancies. May anyone help me? This is the error I get from the first step.

[I]The following packages have unmet dependencies:
  checkinstall: Depends: installwatch (> 0.6) but it is not going to be installed
  libgcc1: Depends: gcc-4.0-base (= 4.0.3-1) but 4.0.1-4ubuntu9 is to be installed
  menu: Depends: libstdc++6 (>= 4.0.2-4) but 4.0.1-4ubuntu9 is to be installed
  xlibs-dev: Depends: libice-dev but it is not going to be installed
             Depends: libsm-dev but it is not going to be installed
             Depends: libx11-dev but it is not going to be installed
             Depends: libxext-dev but it is not going to be installed
             Depends: libxi-dev but it is not going to be installed
             Depends: libxmu-dev but it is not going to be installed
             Depends: libxmuu-dev but it is not going to be installed
             Depends: libxpm-dev but it is not going to be installed
             Depends: libxrandr-dev but it is not going to be installed
             Depends: libxt-dev but it is not going to be installed
             Depends: libxtrap-dev but it is not going to be installed
             Depends: libxtst-dev but it is not going to be installed
             Depends: libxv-dev but it is not going to be installed
             Depends: x-dev but it is not going to be installed
             Depends: xlibs-static-dev but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
[/I]

---

### Post by yabbadabbadont on 2006-04-06
[QUOTE=YuHoo]I compiled the latest cvs 0.9.15 and it went in without a hitch. But after several attempts I still can not figure out how to get the menu to have start functions beyond
```
Fluxbox default menu
-----------------------------
xterm
Restart
Exit
``` I don't know if there needs to be something else installed, or if I'm just missing something obvious. I do like the speed, but if all I get is a blueish theme and the terminal, well, I'll just do without the window manager.[/QUOTE]
You can either install menu (and maybe menu-xdg) then 'sudo update-menus' or, as your normal user (not sudo) run 'fluxbox-generate_menu -is -ds' in a terminal.  The second method will create a configuration file called menuconfig in your ~/.fluxbox directory that you can modify to control some of the behavior of fluxbox-generate_menu.  If nothing else, the second method will give you a properly formatted menu file which you can then modify yourself.

---

### Post by hcker2000 on 2006-04-06
Ahh fluxbox + ubuntu = the best os. Fluxbox is great. Has to be the best interface to x that there is. Only reason to keep kde or gnome around is incase you need help seting up some hardware as fluxbox dosnt have all the fancy smancy wizards (no big loss though).

---

### Post by errr on 2006-04-06
[QUOTE=eklypze]Everything seems to be going wrong for me today. I have tried to install this for a while now and it seems I am missing a bunch of dependancies. May anyone help me? This is the error I get from the first step.

[I]The following packages have unmet dependencies:
  checkinstall: Depends: installwatch (> 0.6) but it is not going to be installed
  libgcc1: Depends: gcc-4.0-base (= 4.0.3-1) but 4.0.1-4ubuntu9 is to be installed
  menu: Depends: libstdc++6 (>= 4.0.2-4) but 4.0.1-4ubuntu9 is to be installed
  xlibs-dev: Depends: libice-dev but it is not going to be installed
             Depends: libsm-dev but it is not going to be installed
             Depends: libx11-dev but it is not going to be installed
             Depends: libxext-dev but it is not going to be installed
             Depends: libxi-dev but it is not going to be installed
             Depends: libxmu-dev but it is not going to be installed
             Depends: libxmuu-dev but it is not going to be installed
             Depends: libxpm-dev but it is not going to be installed
             Depends: libxrandr-dev but it is not going to be installed
             Depends: libxt-dev but it is not going to be installed
             Depends: libxtrap-dev but it is not going to be installed
             Depends: libxtst-dev but it is not going to be installed
             Depends: libxv-dev but it is not going to be installed
             Depends: x-dev but it is not going to be installed
             Depends: xlibs-static-dev but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
[/I][/QUOTE]

There is offical packages for ubuntu breezy for fluxbox .9.14, compling it is pretty much a total waste..

[http://logicvortex.net/debian/fluxbox/](http://logicvortex.net/debian/fluxbox/)  
Make sure to get the package marked for breezy users. I spoke with dopey (the offical packager for Debian/Ubuntu fluxbox packages) in irc the other day and he said he would have .9.15 packages very soon. There is really no need to compile from source unless you just are bored or for some reason his package is missing xinerama or something..

If you have trouble use our wiki: [http://fluxbox-wiki.org/](http://fluxbox-wiki.org/)
In the howto section we have a [howto update using ubuntu]("http://fluxbox-wiki.org/index.php/Howto_update_fluxbox#Using_Ubuntu") guide. We also have many other great fluxbox specific howtos on this wiki. I personally think its the best fluxbox resource on the net.

---

### Post by thewayofzen on 2006-04-07
ive compiled flux from source before in the past just for the purpose of defeating that slow startup.. but i always found that once compiled it would never respect the bitmap font settings needed to display the artwiz fonts.  the deb package in the repos always allows them to work fine but the fluxbox as i installed fromt he latest source never would..
yes i know for a fact my fonts are installed properly.. or they wouldnt work in gnome .. or the repo flux.. just somehow they never work in the one i compile myself.

can anyone confirm if they are now working?

---

### Post by benplaut on 2006-04-07
can the original writer of the HOWTO change 0.9.14 to 0.9.15? everything else should work

---

### Post by Bjorg on 2006-04-07
[[IMG]http://ubuntuforums.org/gallery/files/5/4/3/1/2/desk_thumb.jpg[/IMG]]("http://ubuntuforums.org/gallery/files/5/4/3/1/2/desk_original.jpg")




What's the name of that panel right-up in that screen. I'm looking for that sensor/display.

Thanks.

---

### Post by etank on 2006-04-07
I think the package you are looking for is called gkrellm.

---

### Post by eklypze on 2006-04-07
[QUOTE=errr]There is offical packages for ubuntu breezy for fluxbox .9.14, compling it is pretty much a total waste..

[http://logicvortex.net/debian/fluxbox/](http://logicvortex.net/debian/fluxbox/)  
Make sure to get the package marked for breezy users. I spoke with dopey (the offical packager for Debian/Ubuntu fluxbox packages) in irc the other day and he said he would have .9.15 packages very soon. There is really no need to compile from source unless you just are bored or for some reason his package is missing xinerama or something..

If you have trouble use our wiki: [http://fluxbox-wiki.org/](http://fluxbox-wiki.org/)
In the howto section we have a [howto update using ubuntu]("http://fluxbox-wiki.org/index.php/Howto_update_fluxbox#Using_Ubuntu") guide. We also have many other great fluxbox specific howtos on this wiki. I personally think its the best fluxbox resource on the net.[/QUOTE]

Thank you for replying. I have tried out your suggestion to download the package and I get another error.

[i](Reading database ... 58950 files and directories currently installed.)
Preparing to replace fluxbox 0.9.14-1 (using fluxbox_0.9.14-1_i386.deb) ...
Unpacking replacement fluxbox ...
dpkg: dependency problems prevent configuration of fluxbox:
 fluxbox depends on menu (>= 2.1.19); however:
  Package menu is not configured yet.
 fluxbox depends on libgcc1 (>= 1:4.0.1); however:
  Package libgcc1 is not configured yet.
dpkg: error processing fluxbox (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fluxbox[/i]

---

### Post by yabbadabbadont on 2006-04-08
> **eklypze]Thank you for replying. I have tried out your suggestion to download the package and I get another error.

[i](Reading database ... 58950 files and directories currently installed.)
Preparing to replace fluxbox 0.9.14-1 (using fluxbox_0.9.14-1_i386.deb) ...
Unpacking replacement fluxbox ...
dpkg: dependency problems prevent configuration of fluxbox:
 fluxbox depends on menu (>= 2.1.19) said:**
> 

Use apt-get or synaptic to install menu and libgcc1 then it should go ahead and configure fluxbox.

---

### Post by eklypze on 2006-04-08
Apparently there is an issue of my menu and libgcc1 packages being broken. According to Synaptic both of those are installed, although they are broken. I have tried to uninstall them but if I uninstall those a whole bunch of essential programs that I have need to be uninstalled as well. I have no idea how to fix these broken packages now. :(

---

### Post by guillote_GNU on 2006-04-13
I'm a big fan too... it's good to see people using it and making howto's.
I just wanna add a couple of things.
In configure line perhaps you should use:

#./configure --prefix=/usr --disable-xbm

--prefix=/usr will put binaries in /usr/bin that is the deafault ubuntu directory, kde and gnome support are by default enabled in fluxbox.

And finally, in fluxbox.desktop file you should put the line:

exec /usr/bin/startfluxbox

that command uses automatically startup script for fluxbox and u dont need to edit .xsession file.
I hope it works and be helpful.

---

### Post by daedalusman on 2006-04-13
Great guide, I used the 0.9.14 deb file and now fluxbox is my default desktop, with conky is the best. Only uses about 90megs of ram at startup, just amazing. And so far I haven't ran into any major problems with it yet. Thanks.

---

### Post by geuis on 2006-04-13
response to eklypze

You have to get 'menu' from the universal repository. Do this:

sudo nano /etc/apt/source.list and uncomment the 2 lines about the universal repository. 

Save those changes, then do:
sudo apt-get update

Then:
sudo apt-get install menu

This should install the menu.

Then install Fluxbox. I downloaded the fluxbox_0-1.9.14-1_i386.deb package from [http://people.debian.org/~dopey/fluxbox/ubuntu-breezy/fluxbox_0.9.14-1_i386.deb](http://people.debian.org/~dopey/fluxbox/ubuntu-breezy/fluxbox_0.9.14-1_i386.deb)

sudo apt-get install -i fluxbox_0.9.14-1_i386.deb

It installed for me!

---

### Post by gymsmoke on 2006-04-15
checkinstall 1.5.3, Copyright 2001 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]: 

Is this a harbinger of errors to come??

If the deb package is available, how would it be installed differently from compiling the source? (I've seen a few references to it in the thread, but no offer of how to install it) ...

---

### Post by gymsmoke on 2006-04-15
removed the source install and went here...
[http://logicvortex.net/debian/fluxbox/](http://logicvortex.net/debian/fluxbox/)
got .9.14 ...

(THIS IS HOW TO INSTALL A .DEB PACKAGE INTO UBUNTU)
sudo dpkg -i flux... produces this:

Selecting previously deselected package fluxbox.
(Reading database ... 66489 files and directories currently installed.)
Unpacking fluxbox (from fluxbox_0.9.14-1_i386.deb) ...
Adding `diversion of /usr/bin/bsetroot to /usr/bin/bsetroot.blackbox by fluxbox'
Adding `diversion of /usr/share/man/man1/bsetroot.1.gz to /usr/share/man/man1/bsetroot.blackbox.1.gz by fluxbox'
dpkg: dependency problems prevent configuration of fluxbox:
 fluxbox depends on menu (>= 2.1.19); however:
  Package menu is not installed.
 fluxbox depends on libimlib2; however:
  Package libimlib2 is not installed.
dpkg: error processing fluxbox (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fluxbox

---

### Post by feanor_arcamenel on 2006-04-20
Hello, thanks for the tutorial, it helped much. but I get an error when I change my exec line in /usr/share/xsessions/fluxbox.desktop

It is originally like this: 
exec fluxbox

so when I change it to:
exec /home/username/.fluxbox/startup

It gives an error: Your session only lasted less than 10 seconds
and I have to logout automatically

why's that?

---

### Post by Cedfelix on 2006-04-24
[QUOTE=feanor_arcamenel]Hello, thanks for the tutorial, it helped much. but I get an error when I change my exec line in /usr/share/xsessions/fluxbox.desktop

It is originally like this: 
exec fluxbox

so when I change it to:
exec /home/username/.fluxbox/startup

It gives an error: Your session only lasted less than 10 seconds
and I have to logout automatically

why's that?[/QUOTE]
Try ths thread if it is an ICE authority problem.
[http://ubuntuforums.org/showthread.php?t=139628&highlight=ICE+authority](http://ubuntuforums.org/showthread.php?t=139628&highlight=ICE+authority)

---

### Post by yabbadabbadont on 2006-04-28
[QUOTE=feanor_arcamenel]Hello, thanks for the tutorial, it helped much. but I get an error when I change my exec line in /usr/share/xsessions/fluxbox.desktop

It is originally like this: 
exec fluxbox

so when I change it to:
exec /home/username/.fluxbox/startup

It gives an error: Your session only lasted less than 10 seconds
and I have to logout automatically

why's that?[/QUOTE]
As has been suggested earlier in this thread (much earlier I think), try:
exec /usr/bin/startfluxbox

This is how most distrobutions do it.

---

### Post by eklypze on 2006-05-01
[QUOTE=geuis]response to eklypze

You have to get 'menu' from the universal repository. Do this:

sudo nano /etc/apt/source.list and uncomment the 2 lines about the universal repository. 

Save those changes, then do:
sudo apt-get update

Then:
sudo apt-get install menu

This should install the menu.

Then install Fluxbox. I downloaded the fluxbox_0-1.9.14-1_i386.deb package from [http://people.debian.org/~dopey/fluxbox/ubuntu-breezy/fluxbox_0.9.14-1_i386.deb](http://people.debian.org/~dopey/fluxbox/ubuntu-breezy/fluxbox_0.9.14-1_i386.deb)

sudo apt-get install -i fluxbox_0.9.14-1_i386.deb

It installed for me![/QUOTE]

Thank you for your reply, and sorry for replying very late. I have tried those steps, and this is the error I received.

[I]eklypze@eklypze:~$ sudo apt-get install menu
Reading package lists... Done
Building dependency tree... Done
menu is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libgcc1: Depends: gcc-4.0-base (= 4.0.3-1) but 4.0.1-4ubuntu9 is to be installed
  menu: Depends: libstdc++6 (>= 4.0.2-4) but 4.0.1-4ubuntu9 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
[/I]

---

### Post by McAbre on 2006-05-09
I got my fluxbox from the repositories, and fixed the slow loading by adding 
"export LC_ALL=C" right before "startfluxbox" in the ~/.fluxbox/startup

Also, the fluxbox-generate_menu I found in /usr/share/doc/fluxbox
This is what I did:

1. cd /usr/share/doc/fluxbox
2. gzip -d fluxbox-generate_menu.gz
3. cp fluxbox-generate_menu /usr/bin
4. chmod a+x /usr/bin/fluxbox-generate_menu
5. cd /home/username
6. fluxbox-generate_menu

Then you have to edit the init file to change the menuFile path:

nano -w /home/username/.fluxbox/init
session.menuFile:       /home/username/.fluxbox/menu

You can find better explanations of these things here:
[https://wiki.ubuntu.com/Fluxbox]("https://wiki.ubuntu.com/Fluxbox")               

Hope it helps. =)

-M

---

### Post by JadedMaple on 2006-06-03
Alright, so I just installed Fluxbox from Synaptic except.. When I rightclick.. I have nothing in that Fluxbox menu..

How do I get my programs into there?

Ah, fixed er.


Anyway, how the heck do I take a screenshot?

---

### Post by yabbadabbadont on 2006-06-03
[QUOTE=JadedMaple]Anyway, how the heck do I take a screenshot?[/QUOTE]

If you just installed Fluxbox in addition to the standard ubuntu-desktop, then you can run gnome-screenshot.  Otherwise you will need to install a program like scrot or imagemagick.  If you install imagemagick, then use the "import" command to take screenshots (both full screen and single window).

---

### Post by K2712 on 2006-06-03
When I installed fluxbox, I set my wallpaper, added the 'fbsetbg -l' to my startup file, but when I logged in the wallpaper would only splash on the screen, and not stay set.  I had to place an '&' after the 'fbsetbg -l' line to get the wallpaper to stay set.

Just thought I would post this just incase someone else was having the same problem...

---

### Post by JadedMaple on 2006-06-03
Uh. How do I browse my file system? :O

I feel so stooopid.

---

### Post by K2712 on 2006-06-03
I use rox, it's fast, and lightweight:

```
sudo apt-get install rox-filer
```

Then you will need to update your right-click menu to show all installed apps.  This can be done using fluxconf:

```
sudo apt-get install fluxconf
```

Then use fluxmenu to add/remove apps(ROX) to your right-click menu:

```
flexmenu
```

---

### Post by dartakaum on 2006-06-04
anyone else can't get amsn icon on the desktopbar?

---

### Post by souled on 2006-06-17
Hmm... I'm getting the "...less than 10 seconds..." error for some reason. I tried to restart fluxbox, and I was kicked out to the gdm. Now I keep getting that error whenever I try to log in. I tried changing the ownership of ICEauthority, but that doesn't help. I tried the 'startfluxbox' idea and that doesn't work either. I can log into Gnome no problem... What's going on here?

---

### Post by fineghal on 2006-07-31
So I compiled and installed fluxbox. After installing rox-filer if I somehow wiped out my fluxmenu file, and trying to edit it via "fluxmenu" gives me gtk errors, specifically: 
Gtk-CRITICAL **: gtk_tree_store_append: assertion `VALID_ITER ( parent, tree_store)' failed

I'd rather not have to remove and reinstall flux, any ideas?

I tried uninstalling Rox, no go.

Note: The menu is completely wiped out. Even the defaults "xterm" don't work. Of course I have eterm installed. Restart and Shutdown still work oddly. My menu file is blank though. 

According to the init file I'm loading from ~/.fluxbox/menu
Is there another menu I set up somewhere?

Edit: A flux-generate_menu command fixes the problem of a wiped out menu, however the GUI menu editor fluxmenu still isn't working. When I'm back at my laptop I'll try removing and reinstalling fluxmenu. I have the feeling it may be a dependency problem.

---

### Post by ardchoille on 2006-08-22
Very nice tutorial, thank you very much :)

---

### Post by Dark Damo on 2006-08-22
I get this error when trying to get checkinstall:

```
damo@damo-desktop:~/Desktop/Fluxbox/fluxbox-1.0rc2$ sudo apt-get checkinstall
E: Invalid operation checkinstall

```

Can someone help me please?

---

### Post by Typhoon on 2006-08-22
> **Dark Damo said:**
> I get this error when trying to get checkinstall:

```
damo@damo-desktop:~/Desktop/Fluxbox/fluxbox-1.0rc2$ sudo apt-get checkinstall
E: Invalid operation checkinstall

```

Can someone help me please?

sudo apt-get install checkinstall

---

### Post by Dark Damo on 2006-08-22
```
damo@damo-desktop:~$ sudo apt-get install checkinstall
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package checkinstall

```

Cant find package :S Like the other 500 times i tried stuff.

Care to help some more?

Thanks

---

### Post by Dark Damo on 2006-08-22
```
damo@damo-desktop:~/Desktop/Fluxbox/fluxbox-1.0rc2$ sudo checkinstall

checkinstall 1.5.3, Copyright 2001 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Installing with "make install"...

========================= Installation results ===========================

Copying documentation directory...
/var/tmp/WGgPbkEnVrXcfqRVJAGZ/installscript.sh: line 13: 22295 Segmentation fault      mkdir -p "/usr/share/doc/fluxbox-1.0rc2"

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```

I got that when using check install.

---

### Post by wittyguysuku on 2006-09-26
> **otake-tux said:**
> I'm a big fan of fluxbox. It is highly and easily customizable.  It's wicked fast and it's very pretty.  FLuxbox is in the ubuntu repositories but they are two versions behind and are missing a lot of handy features like fluxbox-generate_menu.  Also, the package in the repositories loads really slow wich should not be the case for a window manager that's supposed to be really fast. 

In this how-to I'm going to sum up all the info I have collected and add a few of my own customization tricks.  Most of what's here I found on other threads, but this info should be in one well organized place so here goes.

1: Download the source tar ball of the latest development version.  The stable version is too old and not supported anymore and the development version is the one the devs recommend.  They actually state 
"The latest stable release is v0.1.14. Development version of Fluxbox can be found here. Please note that 0.1.14 is actually fairly dated (and unmaintained) now, and the development series is quite stable. It is mainly waiting on translation and documentation work before it becomes stable. "

Get the source tarball [here]("http://fluxbox.sourceforge.net/version-0.9.php")

2: Get the tools to compile from source 
```
sudo apt-get install build-essential checkinstall xlibs-dev
```

3: Open your favorite terminal and  untar the file you downloaded. example :
```
tar xvzf fluxbox-0.9.14.tar.gz
```

4: cd into the directory created.

5: Type  ```
./configure --enable-kde --enable-gnome --disable-xmb
``` the disable xmb fixes the slow start up time in ubuntu.

6: Type make .

7: Type sudo checkinstall. This builds the package and puts it in /usr/local/bin

8: There are two ways to be able start fluxbox 

        a)  A .xsession file in your home directory. you may have it or not. if you dont create it.in the terminal type nano ~/.xsession and put this in there ```
exec /usr/local/bin/fluxbox
```

        b) Use you're start up file.  Type nano ~/.fluxbox/startup (if it does not exist, create it) and put this in there```
exec /usr/local/bin/fluxbox -log ~/.fluxbox/log
```

I encourage to use option b, since this is the one I use and I know it works well.

9:  Now to enter kde,gnome or any other window manager I use GDM. It comes standard in Ubuntu.  I know how to make an entry for fluxbox in GDM, I do not know how to do it in the others. To make an entry for fluxbox in GDM in a terminal type ```
cd /usr/share/xsessions
```
now type ls. There should be various files in there with names like gnome.desktop .  Type nano fluxbox.desktop. put this in there :
```
[Desktop Entry]
Encoding=UTF-8
Name=Fluxbox
Comment=This is fluxbox
Exec=/home/(username)/.fluxbox/startup

``` 
That is if in step 8 you chose option b. if you chose option a, on the Exec line          put Exec=/home/(username)/.xsession .       

10: Logout. Now when you go to GDM there will be a fluxbox entry in the session menu. Enter fluxbox.  If it works, you are done with the installation.  To access the menu just right click anywhere in the desktop.  I know that what you have now is pretty bare. But the rest is just customization.

**Customization Tips and Tricks**

Fluxbox is all about minimalism.  I like to use light apps to keep everything really fast so thats the type of tricks I know so here goes. 

1: To get  backround image, open a terminal and type sudo apt-get install feh
then locate the image you want to use as wallpaper. in my case my backrounds are in a directory called wallpapers in my home directory so to set a backround I type at the command line ```
fbsetbg wallpapers/wallpaperofmychoice.png
```

To not have to type all of that every time you want to set a new backround edit your start up file ```
nano ~/.fluxbox/startup
``` add the following line to that file :  ```
fbsetbg -l 
```  this command will always load the last image you set as backround so you only have to type fbsetbg image.png once.  

2: Apps you want to have upon start up are set at the ~/.fluxbox/startup file.  Here's my startup file as an example:
```
# fluxbox startup-script:
#
# Lines starting with a '#' are ignored.
fbsetbg -l
gkrellm &
gnome-volume-manager &
xscreensaver -nosplash &

``` 
first line sets my wallpaper, second starts grellm (a graphical system monitor), the fourth line you will want to have (gnome-volume-manager &) this will automount dvd's, USB  hdd's and loads of other stuff. I actually have a lot more stuff in my startup file but I'm keeping it simple to get you started.

I know many more tips and tricks and other users probably know more than I do.  I would like this thread to have all the nice things you can do  in fluxbox so plz if you know any customization tricks, post them.

This was my first how-to so point out any mistakes.  I will correct them.  Fluxbox is a great window manager.  I think the main reason its not so famous amongst the ubuntu community is because the package in the repositories is just worng.
my Fully customized desktop
[[IMG]http://ubuntuforums.org/gallery/files/5/4/3/1/2/desk_thumb.jpg[/IMG]]("http://ubuntuforums.org/gallery/files/5/4/3/1/2/desk_original.jpg")

edit- fixed the checkinstall typo.


But if I'm neither root user nor sudoer, I cannot edit gnome.desktop isn't it? So in that case, how can I start my specific login session as fluxbox session, leaving other users to use gnome as they desire?

thanks!
Wg

---

### Post by wittyguysuku on 2006-09-26
> **wittyguysuku said:**
> But if I'm neither root user nor sudoer, I cannot edit gnome.desktop isn't it? So in that case, how can I start my specific login session as fluxbox session, leaving other users to use gnome as they desire?

thanks!
Wg

Eureka!
I found out! it's by editing > $HOME/.xprofile. wherein > exec startfluxbox should be placed.

---

### Post by DJiNN on 2006-09-27
> **Dark Damo said:**
> ```
damo@damo-desktop:~$ sudo apt-get install checkinstall
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package checkinstall

```Cant find package :S Like the other 500 times i tried stuff.

Care to help some more?

Thanks

Hey there, just seen your message. Did you get it sorted out? If not, try editing your apt sources list 

```
 sudo leafpad /etc/apt/sources.list 
```and "Uncomment" the other repos by removing the "#" in front of them. You'll see what i mean when you get the list up, it's well documented and explains what to do in there.  (Obviously change "Leafpad" in the above for whatever your chosen editor is (gedit, nano, mousepad etc)

Then try again and it'll probably have no problems. 

Hope that helps. Fluxbox is definitely worth the effort. :)

---

### Post by dhalgren on 2006-10-01
> **souled said:**
> Hmm... I'm getting the "...less than 10 seconds..." error for some reason. I tried to restart fluxbox, and I was kicked out to the gdm. Now I keep getting that error whenever I try to log in. I tried changing the ownership of ICEauthority, but that doesn't help. I tried the 'startfluxbox' idea and that doesn't work either. I can log into Gnome no problem... What's going on here?

I also had this problem, and my solution (I am a little lazy) was to uninstall, including config files, using synaptic, and then to reinstall with gdebi installer from the deb package created by checkinstall.

This got rid of the 10 second problem, but it did result in fluxbox being called "foo" on the gdm login screen. I cna live with that. :)

---

### Post by fasoulas on 2006-12-14
> 
8: There are two ways to be able start fluxbox 

        a)  A .xsession file in your home directory. you may have it or not. if you dont create it.in the terminal type nano ~/.xsession and put this in there ```
exec /usr/local/bin/fluxbox
```

        b) Use you're start up file.  Type nano ~/.fluxbox/startup (if it does not exist, create it) and put this in there```
exec /usr/local/bin/fluxbox -log ~/.fluxbox/log
```

I encourage to use option b, since this is the one I use and I know it works well.

9:  Now to enter kde,gnome or any other window manager I use GDM. It comes standard in Ubuntu.  I know how to make an entry for fluxbox in GDM, I do not know how to do it in the others. To make an entry for fluxbox in GDM in a terminal type ```
cd /usr/share/xsessions
```
now type ls. There should be various files in there with names like gnome.desktop .  Type nano fluxbox.desktop. put this in there :
```
[Desktop Entry]
Encoding=UTF-8
Name=Fluxbox
Comment=This is fluxbox
Exec=/home/(username)/.fluxbox/startup

``` 
That is if in step 8 you chose option b. if you chose option a, on the Exec line          put Exec=/home/(username)/.xsession . 

I tried this option
 
b) Use you're start up file.  Type nano ~/.fluxbox/startup (if it does not exist, create it) and put this in there```
exec /usr/local/bin/fluxbox -log ~/.fluxbox/log
```

i press ctrl = o to save the and it shows this 

**File Name to Write:**

what do i have to put hare????

pls help i want to try fluxbox

---

### Post by Muximori on 2006-12-14
Hi, I love fluxbox and am trying to get it working with my xubuntu install.

I choose it in the session manager and log in, and it works fine, except I can't do anything because the right click menu it completely empty and I don't know any keyboard shortcuts. How do I set up the menu?

---

### Post by kerry_s on 2006-12-14
> **Muximori said:**
> Hi, I love fluxbox and am trying to get it working with my xubuntu install.

I choose it in the session manager and log in, and it works fine, except I can't do anything because the right click menu it completely empty and I don't know any keyboard shortcuts. How do I set up the menu?

Log back in to xubuntu & in terminal-> sudo update-menus
Then log in to fluxbox.
or 
mousepad ~/.fluxbox/menu
change
 [include] (/etc/X11/fluxbox/fluxbox-menu)
to
 [include] (~/.fluxbox/fluxbox-menu)
 Then you can just use-> update-menus

```
[begin] (Fluxbox)

[exec] (Files) {emelfm} 

[exec] (Terminal) {xterm} 
 
[submenu] (Net)
 [exec] (Firefox) {firefox}
 [exec] (Gaim) {gaim}
 [exec] (Downloads) {xterm -T "Prozilla" -e dproz}
[end]

[submenu] (Sound)
 [exec] (Mplayer) {gmplayer}
 [exec] (Burner) {xfburn}
 [exec] (Wmix) {wmix}
 [exec] (Kill-Wmix) {killall wmix}
[end]

[submenu] (Admin)
 [exec] (Synaptic) {gksu synaptic}
 [exec] (Root-Files) {gksu emelfm}
 [exec] (Terminal-Root) {gksu xterm}
[end]

[submenu] (Settings)
  [restart] (Restart)
  [config] (Configuration)
   [submenu] (Styles)
      [stylesdir] (/usr/share/fluxbox/styles)
      [stylesdir] (~/.fluxbox/styles)
   [end]
 [submenu] (Backgrounds)
  [wallpapers] (/usr/share/fluxbox/backgrounds)
  [wallpapers] (~/.fluxbox/backgrounds)
 [end]
[end]

[separator]
[exec] (Run Program) {fbrun}
[exec] (Keyboard) {xvkbd -no-keypad}

[submenu] (ScreenShots)
 [exec] (Snap) {scrot %T.jpg}
 [exec] (Select) {scrot -s -b %T.jpg}
 [exec] (Wait 5) {scrot -d 5 %T.jpg}
[end]

[separator]
[submenu] (Debian-menu)
 [exec] (Update-menus) {update-menus}
 [include] (~/.fluxbox/fluxbox-menu)
[end]


[separator]
[exec] (Screen Off) {/home/user/.screen-off}
[exit] (Exit)
[exec] (Reboot) {sudo shutdown now -r -f}
[exec] (Shutdown) {sudo shutdown now -h}
[end]

```

---

### Post by Muximori on 2006-12-14
Thankyou very much!

---

### Post by adamJ5 on 2006-12-20
Sorry, but this didn't work for me. :( I followed your steps, but after I've logged out and logged back in it wasn't Fluxbox but Gnome that appeared. 

Is it a way to solve this?

---

### Post by Monoxide on 2006-12-20
I olny seen gnome after my install....which is the default.

---

### Post by zetsumei on 2006-12-20
i used the command 
 > xterm -help

and couldn't find the option for transparency...could someone tell me what option it is and how you show it on your desktop like some of those screenshots of people's desktops are...sorry for being noob, im learning

---

### Post by yabbadabbadont on 2006-12-20
> **zetsumei said:**
> i used the command 
 

and couldn't find the option for transparency...could someone tell me what option it is and how you show it on your desktop like some of those screenshots of people's desktops are...sorry for being noob, im learning

xterm doesn't, by itself, support pseudo-transparency.  They are probably using a different terminal program that does.  (Eterm, Aterm, rxvt, urxvt, mrxvt, gnome-terminal, Konqueror, ...)

---

### Post by BLTicklemonster on 2006-12-21
I love fluxbox, but I can't decide on what I want to use as a toolbar. Right now I have gdesklets added to startup, and I'm using Gnome Bar (from Toolbar/Misc) which is kind of okay, but I was using xfce4-panel before and I liked it better, but it's just not what I want. 

Any ideas out there? What do you all use?

---

### Post by yabbadabbadont on 2006-12-21
> **BLTicklemonster said:**
> I love fluxbox, but I can't decide on what I want to use as a toolbar. Right now I have gdesklets added to startup, and I'm using Gnome Bar (from Toolbar/Misc) which is kind of okay, but I was using xfce4-panel before and I liked it better, but it's just not what I want. 

Any ideas out there? What do you all use?

None at all.  I have a key-binding to the root menu so I have no need for a panel.  The default toolbar is enough for me.  As for available panels, I've seen people use the ones you have already mentioned as well as pypanel, perlpanel, fspanel, fbpanel, suxpanel, rox (more of a desktop than panel), gnome-panel, Kicker (from KDE), YAB (from Adesktlets), and Modubar (from Adesklets).  I'm sure there are others that I've forgotten.  ;)

---

### Post by BLTicklemonster on 2006-12-22
Thanks Yab, but I just sat and messed around and finally it sunk in how to get the menu where I could edit it to how I want it, sooooo, I can now put just what I want right where I want it. I see now how there's really no need for that bar after all :) !!!

---

### Post by BLTicklemonster on 2006-12-22
Okay, I settled down with gdesklets using the basic toolbar/launcher which is easily personalized. 

Now I have a question about my mouse... I have xmodmap working okay, but I need to get my dpi up to 800, how do I get locomo to run in fluxbox? My mouse is pathetic in online gaming, and I play a run and gun mod called Zark on our Unreal Tournament server.

---

### Post by yabbadabbadont on 2006-12-22
> **BLTicklemonster said:**
> Okay, I settled down with gdesklets using the basic toolbar/launcher which is easily personalized. 

Now I have a question about my mouse... I have xmodmap working okay, but I need to get my dpi up to 800, how do I get locomo to run in fluxbox? My mouse is pathetic in online gaming, and I play a run and gun mod called Zark on our Unreal Tournament server.

Usually, any programs you want to run automatically should be added to your ~/.fluxbox/startup file.  I'll post mine as an example (that differs from the default):
```
/home/bubba/.fluxbox $ cat startup 
#
# custom script that updates a file with all my wallpapers (50,000+ of them)
# notice that it is started in the background
#
wallpaper-list-create &

#
# restore my preferred nvidia driver settings
#
nvidia-settings --load-config-only

#
# Set the root window to solid black by default
#
fbsetroot -solid black

#
# Turn off annoying beeps
#
xset -b

#
# Set the keyboard repeat delay and rate
#
xset r rate 250 30

#
# I like having the numlock on by default
#
numlockx

#
# Start fluxbox in the background and save it's process id
# This gives it a chance to draw the initial desktop before
# other programs startup
#
fluxbox -log "/home/bubba/.fluxbox/log" &
fluxpid=$!

#
# Start gkrellm in the background and save it's process id
#
gkrellm2 &
gkpid=$!

#
# Start my custom wallpaper rotating program in the background
# and save it's process id.  (rotate wallpaper every 300 seconds)
#
wallpaper-set-rotate 300 &
wsrpid=$!

#
# Now wait until the fluxbox process id exits (i.e. until I exit fluxbox)
#
wait $fluxpid

#
# Send a kill signal to my wallpaper script and gkrellm
# so that they can shut down cleanly as X exits
#
kill $wsrpid
kill $gkpid
```

---

### Post by BLTicklemonster on 2006-12-23
Thanks yab, but the numlocks thing didn't work for me, and I wonder how one would pid gdesklets? How do you find out what to put on that line? That's a really neat trick. If I click to restart fluxbox, I lose gdesklets, and I suppose that pid line would stop that from happening?

I've been doing all this in feisty so far, and decided to try now in dapper, and just remembered that fluxbox never showed up (loaded from synaptic) no matter what I did, so I hope following this guide will fix that)

*edit: duh, installed numlockx :)

---

### Post by yabbadabbadont on 2006-12-23
> **BLTicklemonster said:**
> Thanks yab, but the numlocks thing didn't work for me, and I wonder how one would pid gdesklets? How do you find out what to put on that line? That's a really neat trick. If I click to restart fluxbox, I lose gdesklets, and I suppose that pid line would stop that from happening?

I've been doing all this in feisty so far, and decided to try now in dapper, and just remembered that fluxbox never showed up (loaded from synaptic) no matter what I did, so I hope following this guide will fix that)

*edit: duh, installed numlockx :)
I don't run gdesklets, so I'm not sure if what I show there would work for that.  Check the documentation for gdesklets to see what, if any, command line parameters it takes.  It could be that you can call it with some kind of kill or shutdown option.  Adesklets has such an option, so perhaps gdesklets does too.  Also, I'm not sure about the restart problem with gdesklets.  I don't see that behavior from the programs I start.  Perhaps it is a gdesklets thing?

---

### Post by BLTicklemonster on 2006-12-23
The gdesklets icon in the toolbar disappears, as well as the actual thing I use. I guess I'll keep looking. I was putting locomo -8 & in startup, it was supposed to be locomo & so I have that straight now. Thanks for your help.

---

### Post by deezay on 2006-12-25
i'm a newb so bear with me.. i've followed everything to spec on my xubuntu box, but when i try to log in with flux as my session i get the error that there is no '/usr/local/bin/fluxbox' file. and surely enough.. there is none. how would i remedy this? by the way.. merry christmas!

---

### Post by bodhi.zazen on 2007-01-12
sudo mkdir /usr/local
sudo mkdir /usr/local/bin
sudo ln -s /usr/bin/startfluxbox /usr/local/bin/startfluxbox

you may also want to do this with fluxbox:

sudo ln -s /usr/bin/fluxbox /usr/local/bin/fluxbox

Find startfluxbox: 

which fluxbox

The above assumes /usr/bin/fluxbox

---

### Post by polkajunior on 2007-01-19
i followed all the instructions but, i looks like i dont even have the .fluxbox diectory that was supposed to be installed and its not hidden there just wasnt one made. so far i
downloaded the source to deskop
uppacked it on desktop then followed the instructions..

but i dont have the .fluxbox directory?

---

### Post by yabbadabbadont on 2007-01-19
> **polkajunior said:**
> i followed all the instructions but, i looks like i dont even have the .fluxbox diectory that was supposed to be installed and its not hidden there just wasnt one made. so far i
downloaded the source to deskop
uppacked it on desktop then followed the instructions..

but i dont have the .fluxbox directory?
The ~/.fluxbox directory and initial config files are created by the startfluxbox script that is supposed to be used when starting (wait for it....  :D) fluxbox.  If you start fluxbox through your ~/.xinitrc then make sure that you call startfluxbox and not fluxbox.  If you start fluxbox through a fluxbox.desktop file in /usr/share/xsessions, make sure that the exec line is calling startfluxbox instead of fluxbox.  That is how upstream expects fluxbox to be started.  (and why they created the startfluxbox script in the first place.  ;))

---

### Post by polkajunior on 2007-01-19
man im sorry guys i made  a stupid mistake. i got it working. thanks!

---

### Post by MaXqUE on 2007-02-15
> **yabbadabbadont said:**
> You can use ctrl-alt-(numeric keypad)+ and ctrl-alt-(numeric keypad)- to change it temporarily or you can edit your /etc/X11/xorg.conf file.

```
Section "Screen"
        Identifier      "Screen0"
        Device          "Card0"
        Monitor         "Monitor0"
        DefaultDepth    24
        SubSection      "Display"
                Viewport        0 0
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection      "Display"
                Viewport        0 0
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection      "Display"
                Viewport        0 0
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection      "Display"
                Viewport        0 0
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```
Only include the screen resolutions that you want to allow.

Yes, I've done that before. But its a hard coded change. If you occasionally change you sceen resolution like i do, you'll want something less permanent. 

When Ubuntu was installed Gnome had a panel for that which didn't' alter X.org.conf. Those are no longer in our Fluxbox menus but the applets are still there.

you can type in a terminal:

```
/usr/bin/gnome-display-properties & 
```

you will get a utility which will change your screen resolution. Remember that Fluxbox fully supports Gnome. I will add this do one of my menus. 

Actually, I wonder why all of those things aren't in our System menus.

Cheers,
MaXqUE

---

### Post by yabbadabbadont on 2007-02-15
> **MaXqUE said:**
> Yes, I've done that before. But its a hard coded change. If you occasionally change you sceen resolution like i do, you'll want something less permanent. 

When Ubuntu was installed Gnome had a panel for that which didn't' alter X.org.conf. Those are no longer in our Fluxbox menus but the applets are still there.

you can type in a terminal:

```
/usr/bin/gnome-display-properties & 
```

you will get a utility which will change your screen resolution. Remember that Fluxbox fully supports Gnome. I will add this do one of my menus. 

Actually, I wonder why all of those things aren't in our System menus.

Cheers,
MaXqUE

Actually, you get gnome-display-properties if you have gnome installed.... I don't.  ;)

If you don't mind using the command line or just want to setup some shortcut keys in Fluxbox, read up on the xrandr utility.  It is generally installed with the base xorg install.  (man xrandr for details)

---

### Post by MaXqUE on 2007-02-15
> **otake-tux said:**
> The reason I wanted to do this was for practice.  You know, as a hobby and a learning experience.  I didn't know about the idesk tools though.  You're post has slightly dismotivated me.  :(  Oh,well.  I might still do it.

Well, just re-assemble yourself! :) 

Debian in general is notoriously slow in getting up to  date applications into the system. lots of times we have to do it ourselves and make noise so those higher up know we're interested in these things. Thanks to you, Fluxbox is one of the few things that *is* working right for me on  Ubuntu.

I dont' have AppleTalk yet, the Netatlk packages aren't signed so I cannot compile from source, The packages for it avaiilable to Ubuntu do not have the right encryption compiled so that passwords will be encrypted from a Mac to a Linux box :(


 I've learned a lot from what you wrote.... Below are some more things.. some of which I"ve tried, other I haven't.

Thanks again for this small HOW-TO. It would be nice to turn this into a regular place for Ubuntu users to exchange information on configuring Fluxbox.

In one distro I used they had a little applet called udate-menus which did just like updatedb except that it updated all the applications in the Fluxbox menus. This should happen during the install but it doesn't always. That was a life save sometimes.

We are also not tied to Nautilus as our fiile manager. Rox-Filer is a nifty file manager as well. iDesk OR (not both) can place icons on your desktop.

Cheers
MaXqUE

---

### Post by dracomordag on 2007-02-17
this guide somehow erased the "shut down" options from my login/options screen and from my logout button while im logged in

any idea how? how to fix?

---

### Post by MaXqUE on 2007-02-18
> **dracomordag said:**
> this guide somehow erased the "shut down" options from my login/options screen and from my logout button while im logged in

any idea how? how to fix?

That's WAY to complex for Fluxbox. Being completely minimalistic, Fluxbox doesn't provide those, you right-click on the desktop, select the "fluxbox" menu at the bottom, and choose "Exit" from the sub menu that appears. That takes you to your Ubuntu login screen again. In the lower left hand side of the login screen there is a menu which will allow you to choose your XWindow manager as well as things like shutdown, restart or choose an XSession on another machine. That confused me about Fluxbox at first as well, until I realised that putting those controls in Fluxbox would simply duplicate controls which were already in place elsewhere.

Now what does bother me is that running /usr/bin/gnome-control-center will let you configure your screen resolution, but the problem is that it isn't saved anywhere. I didn't have this problem when I originally installed Ubuntu and was running Gnome but I do when i am running Fluxbox.

I've had some really bad experiences editing Xorg.conf, so I will not touch that file. Like the other operating systems we've all used, the screen resolution can be changed and saved at anytime by a user with sufficient privileges. It should be the same way on Linux.

Having just one screen resolution may be OK for office environments, but it isn't for multimedia environments.

---

### Post by yabbadabbadont on 2007-02-18
> **MaXqUE said:**
> Now what does bother me is that running /usr/bin/gnome-control-center will let you configure your screen resolution, but the problem is that it isn't saved anywhere. I didn't have this problem when I originally installed Ubuntu and was running Gnome but I do when i am running Fluxbox.

I've had some really bad experiences editing Xorg.conf, so I will not touch that file. Like the other operating systems we've all used, the screen resolution can be changed and saved at anytime by a user with sufficient privileges. It should be the same way on Linux.

Having just one screen resolution may be OK for office environments, but it isn't for multimedia environments.

"man xrandr"

It isn't a nice pretty gui, but it will let you change your screen resolution.  (among other things)  Or you could just use the old standard X windows way...  ctrl-alt-+ and ctrl-alt--  (that is the plus and minus keys on the numeric keypad)  I think that only cycles through the resolutions defined in /etc/X11/xorg.conf though.

---

### Post by BLTicklemonster on 2007-02-19
MaX, have you tried running that as sudo?

---

### Post by dracomordag on 2007-02-19
> **MaXqUE said:**
> That's WAY to complex for Fluxbox. Being completely minimalistic, Fluxbox doesn't provide those, you right-click on the desktop, select the "fluxbox" menu at the bottom, and choose "Exit" from the sub menu that appears. That takes you to your Ubuntu login screen again. In the lower left hand side of the login screen there is a menu which will allow you to choose your XWindow manager as well as things like shutdown, restart or choose an XSession on another machine. That confused me about Fluxbox at first as well, until I realised that putting those controls in Fluxbox would simply duplicate controls which were already in place 

nah, i dont even use fluxbox. it took it away from my gnome sessions.

---

### Post by Graduate on 2007-03-01
How do I change icons nautilus and in the system in general? I had tux n tosh i think they're called in gnome and they went back to default. I already used "switch2" to change the gtk theme, but I'm lost in the icon part.

[COLOR="Red"]**edit**[/COLOR]
Ok, I figured out how to change the icons. I run gnome-theme-manager in the termial, pick the icons I want, and tada. However, when I restart, shut down and log back in, or just log out of fluxbox, the themes go back to default. Anyone know how to change this so the icons are permanent.

---

### Post by yabbadabbadont on 2007-03-01
> **Graduate said:**
> How do I change icons nautilus and in the system in general? I had tux n tosh i think they're called in gnome and they went back to default. I already used "switch2" to change the gtk theme, but I'm lost in the icon part.

[COLOR="Red"]**edit**[/COLOR]
Ok, I figured out how to change the icons. I run gnome-theme-manager in the termial, pick the icons I want, and tada. However, when I restart, shut down and log back in, or just log out of fluxbox, the themes go back to default. Anyone know how to change this so the icons are permanent.

Edit your .gtkrc-2.0 file and add
```
gtk-icon-theme-name="MyIconTheme"
```

---

### Post by Kingsley on 2007-03-01
This is lightning speed compared to KDE. I feel like Fluxbox lacks some functionality but maybe it just takes some getting used to.

---

### Post by Raavea on 2007-03-06
Hi guys.
 I've had fluxbox on my machine for a few days and still haven't really gotten the hang of modifing it to look.. Nice. 
 I won't give up FF, even though it's slow, and I have GNOME running under my Flux.. Thing is, all my gnome apps are horrendously ugly and do not read the GNOME theme. They load it if I execute gnome-theme-manager in the xterm, but I have to leave that terminal window open to keep the theme there. I have a similar issue with fbdesk.

 Thing is, I have both of these in my startup, and so far as I can see, it should all be working as intended;
```
exec /usr/local/bin/fluxbox -log ~/.fluxbox/log
# fluxbox startup-script:
#
# Lines beginning with hash are ignored. I'd eat them, myself..
fbdesk &
fbdesk -rc ~/.fluxbox/init &
gnome-theme-manager &
gkrellm &
gnome-volume-manager &
xscreensaver -nosplash &
```I only just added fbdesk& to the top, though fbdesk -rc was already there. So far as I can see, this should cause these programs to open on my logging into flux - right?

---

### Post by yabbadabbadont on 2007-03-06
> exec /usr/local/bin/fluxbox -log ~/.fluxbox/log
Must be the last line in the file.

---

### Post by Raavea on 2007-03-07
Thanks Yabba, I wasn't aware of that. :)

---

### Post by yabbadabbadont on 2007-03-07
> **Raavea said:**
> Thanks Yabba, I wasn't aware of that. :)

You're welcome.  Just for future reference, from the bash man page:```
       exec [-cl] [-a name] [command [arguments]]
              If command is specified, it replaces the shell.  No new process is created.  The arguments become the argu&#8208;
              ments to command.  If the -l option is supplied, the shell places a dash at the beginning of the zeroth arg
              passed to command.  This is what login(1) does.  The -c option causes command to be executed with an  empty
              environment.   If -a is supplied, the shell passes name as the zeroth argument to the executed command.  If
              command cannot be executed for some reason, a non-interactive shell exits, unless the shell option execfail
              is  enabled,  in which case it returns failure.  An interactive shell returns failure if the file cannot be
              executed.  If command is not specified, any redirections take effect in the current shell, and  the  return
              status is 0.  If there is a redirection error, the return status is 1.
```
Basically, when the exec command is executed, fluxbox is started and the script stops and waits until fluxbox exits.  So the commands you specified after the exec never get run until *after* you exit fluxbox.  If, for some reason, you want or need to launch fluxbox first, there is a way to do it.  Here is my startup file as an example:```
/home/bubba $ cat .fluxbox/startup 
wallpaper-list-create &

fbsetroot -solid black

xset -b -dpms s off r rate 250 30

numlockx

fluxbox -log "/home/bubba/.fluxbox/log" &
fluxpid=$!

wallpaper-set-rotate 300 &
wsrpid=$!

gkrellm &
gkrpid=$!

wait $fluxpid

kill $wsrpid
kill $gkrpid
```
Notice that I use the "wait" command to pause execution of the startup script until the fluxbox process id exits  (until I exit fluxbox).  I then send a kill signal to gkrellm and my own random wallpaper script.

---

### Post by Raavea on 2007-03-08
So, Yabba, in the startup script the $something is like the $something in PHP...?

Can I also ask if you can tell me how to get XFCE-4 to be the internal-bit for my fluxbox install, as opposed to GNOME? That'd speed things up, and XFCE has better compatability with Flux, right? 
I have a hunch that this bit;```
(...)
gnome-theme-manager &
gkrellm &
gnome-volume-manager &
(...)
```Is somehow important, and that I shouldn't just get rid of it. But I want to remove GNOME and related stuff as much as possible to try and speed this laptop up.

*(Really, what'd suit me best is a complete guide to getting an uber-sexy looking flux desktop, with transparency _-working-_ and lightweight apps... Other than my beloved Firefox and Thunderbird. Is Mousepad as good as Gedit? I reeeeally like Gedit..)*

---

### Post by Nikron on 2007-03-08
Used this guide to set up 1.0rc2 very easily, on a server install for a nice pretty desktop using VNC.  Thanks

---

### Post by yabbadabbadont on 2007-03-08
> **Raavea said:**
> So, Yabba, in the startup script the $something is like the $something in PHP...?

Can I also ask if you can tell me how to get XFCE-4 to be the internal-bit for my fluxbox install, as opposed to GNOME? That'd speed things up, and XFCE has better compatability with Flux, right? 
I have a hunch that this bit;```
(...)
gnome-theme-manager &
gkrellm &
gnome-volume-manager &
(...)
```Is somehow important, and that I shouldn't just get rid of it. But I want to remove GNOME and related stuff as much as possible to try and speed this laptop up.

*(Really, what'd suit me best is a complete guide to getting an uber-sexy looking flux desktop, with transparency _-working-_ and lightweight apps... Other than my beloved Firefox and Thunderbird. Is Mousepad as good as Gedit? I reeeeally like Gedit..)*
I'm not sure that I understand your question.  The Fluxbox startup script is a Bash shell script.  ("man bash" for details on bash scripting features)  

Fluxbox is a window manager.  It serves the same purpose as Metacity, Kwin, and xfwm.  It doesn't need or use anything from gnome, kde, xfce, ...  You can use some pieces of those desktop environments with fluxbox if you so choose, but they are not necessary.  (gnome-panel, kicker, xfce-panel, for example)  You don't need gnome-theme-manager if you properly configure your ~/.gtkrc and ~/.gtkrc-2.0 files.  gtk-theme-switch provides two tools to help you change your gtk1 and gtk2 themes.  (called switch, and switch2)  I assume that gnome-volume-manager handles automounting things for you.  I don't like or use automounting so I can't offer any suggestions for replacing it.  Sorry.

---

### Post by Raavea on 2007-03-09
> **yabbadabbadont said:**
> I'm not sure that I understand your question.  The Fluxbox startup script is a Bash shell script.  ("man bash" for details on bash scripting features)  
 If you meant my question regarding dollar signs, it's not important, but to briefly explain, in PHP you can store something in a variable, so I could make a variable called [FONT="Courier New"]$sheep[/FONT] and when I make the script execute, it will display or execute what I stored in [FONT="Courier New"]$sheep[/FONT] - be it to say Baa baa baa or open a popup with black sheep in it. I was just wondering if that is how the [FONT="Courier New"]wait $fluxpid[/FONT] command in your script works. 

> **yabbadabbadont said:**
> Fluxbox is a window manager.  It serves the same purpose as Metacity, Kwin, and xfwm.  It doesn't need or use anything from gnome, kde, xfce, ...  Aaah, I thought that the window manager handled the window edges, simply because I have installed Fluxbox, but it is using gnome for the internal theming, so to get rid of the ugly grey inner windows I need to open gnome-theme-manager, and thus it's still rather slow and so on and so on.

> **yabbadabbadont said:**
> You can use some pieces of those desktop environments with fluxbox if you so choose, but they are not necessary.  (gnome-panel, kicker, xfce-panel, for example)  You don't need gnome-theme-manager if you properly configure your ~/.gtkrc and ~/.gtkrc-2.0 files.How can I configure these to make Fluxbox do everything itself? I will of course be searching once I have posted this, but if you have any tried and tested links you oculd pass on, it would aid me greatly. :)

> **yabbadabbadont said:**
>  gtk-theme-switch provides two tools to help you change your gtk1 and gtk2 themes.  (called switch, and switch2) So GTK *is* needed..? Or...? Please note that I am in no way a well-versed linux user. Most of what I've accomplished is guesswork and picking people's brains.. I have dabbled with enlightened-gnome but never really enjoyed it as much as plain gnome. Pure enlgihtenment *(E16 then E17)* were awesome, but my hardware didn't like it. 

So what is needed, simply, what can I leave to Flux and what do I have to use other things for? *(I already know I need a file manager, a desktop manager if I want to use it like a GNOME desktop, and obviously sundry software like OO and a terminal.)*

> **yabbadabbadont said:**
> I assume that gnome-volume-manager handles automounting things for you.  I don't like or use automounting so I can't offer any suggestions for replacing it.  Sorry.Automounting is more of an issue than a bonus, but for some reason at the time I thought it was needed to get my hd0 to work. I know I don't, and have no idea why I thought that.. XD

Thanks for taking the time to try to help me, I really appreciate it. :)


**Nikron** - Congrats! :D


EDIT: Oooh, hey, I am sure I did this part;> 5: Type

./configure --enable-kde --enable-gnome --disable-xmb

the disable xmb fixes the slow start up time in ubuntu.But if my fluxbox is using gnome.. Then I didn't.. Right? :S?


EDIT THE SECOND: All sorted on the gnome front. :D

---

### Post by band-aid on 2007-04-02
Sorry to revive a 3 week old thread (if its not stickied) but I am having trouble following the instructions. When I do sudo checkinstall no ~/.fluxbox directory is created. I thought this was normal so I made it myself and created the startup script in it. Fluxbox starts fine but crashes upon trying to do anything. It listed a ton of files that it could not find. It was at this point that I realized that none of the files were created in the .fluxbox directory. Its like the install process did not do its job.

---

### Post by yabbadabbadont on 2007-04-02
> **band-aid said:**
> Sorry to revive a 3 week old thread (if its not stickied) but I am having trouble following the instructions. When I do sudo checkinstall no ~/.fluxbox directory is created. I thought this was normal so I made it myself and created the startup script in it. Fluxbox starts fine but crashes upon trying to do anything. It listed a ton of files that it could not find. It was at this point that I realized that none of the files were created in the .fluxbox directory. Its like the install process did not do its job.

The ~/.fluxbox directory is not created until the first time that startfluxbox is run.  You will save yourself a lot of pain if you just delete the ~/.fluxbox directory and let startfluxbox create it, and all its files, for you automagically.  :D

---

### Post by band-aid on 2007-04-02
That got it. Thanks a ton, I think I've found my new favorite window manager. It starts so bloody fast, its crazy.

---

### Post by Pugwash on 2007-04-04
Thanks for the guide, decided to upgrade to the latest version, I've been using the version in the repos for a while. Just a question, what exactly does this do :

```
./configure **--enable-kde --enable-gnome** --disable-xmb 
```
(the enable kde and gnome bit)

Also, how do I turn of the tabbed browsing feature, I'm too old fashioned for such things.

Cheers

---

### Post by yabbadabbadont on 2007-04-04
> **Pugwash said:**
> Thanks for the guide, decided to upgrade to the latest version, I've been using the version in the repos for a while. Just a question, what exactly does this do :

```
./configure **--enable-kde --enable-gnome** --disable-xmb 
```
(the enable kde and gnome bit)

Also, how do I turn of the tabbed browsing feature, I'm too old fashioned for such things.

Cheers

The two options just enable support for KDE and Gnome apps use of the system tray (I think).

You can either configure fluxbox to not use tabs at compile time or in your running fluxbox, go to the tab settings menu and enable the "tabs in titlebar" (or something like that).  Then you won't get external tabs.

---

### Post by Pugwash on 2007-04-05
> **yabbadabbadont said:**
> The two options just enable support for KDE and Gnome apps use of the system tray (I think).

Ah, i just did ./configure, I've not seen any probs with amarok minimising to the toolbar. But I'll reinstall it again, just in case.

> You can either configure fluxbox to not use tabs at compile time or in your running fluxbox, go to the tab settings menu and enable the "tabs in titlebar" (or something like that).  Then you won't get external tabs.[/QUOTE]

Where's the tabs setting menu? Could you modify the init file?

Cheers

---

### Post by yabbadabbadont on 2007-04-05
> **Pugwash said:**
> Ah, i just did ./configure, I've not seen any probs with amarok minimising to the toolbar. But I'll reinstall it again, just in case.
No need as the default is to include support for both kde and gnome when configure is run.

> **Pugwash said:**
> Where's the tabs setting menu? Could you modify the init file?

Cheers

Fluxbox menu->Configure->Tab options->Tabs in Titlebar

Or set this in your ~/.fluxbox/init file:
```
session.screen0.tabs.intitlebar:        true
```

---

### Post by Pugwash on 2007-04-07
> **yabbadabbadont said:**
> No need as the default is to include support for both kde and gnome when configure is run.



Fluxbox menu->Configure->Tab options->Tabs in Titlebar

Or set this in your ~/.fluxbox/init file:
```
session.screen0.tabs.intitlebar:        true
```

Cheers, that solved it. :)

Thanks

---

### Post by RedSquirrel on 2007-04-09
> **jinxjinx said:**
> no one knows how to bind keys to the mouse?
Thanks!


Just in case anyone was wondering about this feature, it is available in 1.0rc3. It is the first item on [this page]("http://fluxbox.sourceforge.net/version-0.9.php").

[Here]("http://fluxbox-wiki.org/index.php/Howto_edit_the_keys_file#Mouse_Events") is the relevant section from the Fluxbox wiki.

I haven't played around with this too much because I try to use my mouse (trackball, actually) as little as possible, but for you steady mouse users out there... ;)


Here is my keys file, with the top three lines that were added *automagically*:

```
!mouse actions added by fluxbox-update_configs
OnDesktop Mouse1 :hideMenus
OnDesktop Mouse2 :workspaceMenu
OnDesktop Mouse3 :rootMenu

Control Mod1 Left :PrevWorkspace
Control Mod1 Right :NextWorkspace
Mod1 Tab :MacroCmd {Deiconify LastWorkspace} {NextWindow 0}
Mod1 F1 :Workspace 1
Mod1 F2 :Workspace 2
Mod1 F3 :Workspace 3
Mod1 F4 :Workspace 4
Mod1 F5 :ExecCommand xfce4-terminal
Mod1 F6 :ExecCommand leafpad
Mod1 F7 :ExecCommand abiword 
Mod1 F8 :ExecCommand thunar
None XF86HomePage :ExecCommand firefox
None XF86Mail     :ExecCommand mozilla-thunderbird
None XF86Search   :ExecCommand 
None Print :Execute import -pause 10 -window root ~/misc/screenshots/screen-`date +%Y%m%d-%H%M%S
`.jpg
Mod1 Sys_Req :Execute import -frame ~/misc/screenshots/window-`date +%Y%m%d-%H%M%S`.jpg
Super_L :RootMenu
Super_R :RootMenu

```I'm using SVN version 4842.

Cheers.

---

### Post by bodhi.zazen on 2007-06-21
I know it's an old thread, but just to show (new users) what Fluxbox can do :

[[IMG]http://img46.imageshack.us/img46/2761/fluxiconsep5.th.png[/IMG]](http://img46.imageshack.us/my.php?image=fluxiconsep5.png)

That is how I like it, clean, little or no desktop icons, but I do like icons in the menu.

FYI : That is a custom script to generate a fluxbox menu with icons (don't expect fluxbox to look like that out of the box). If you would like a copy of the script, send me a PM.

---

### Post by yabbadabbadont on 2007-06-21
You can also get icons in your fluxbox menu by using the "-is -ds" options with fluxbox-generate_menu which is included when you install fluxbox.

Edit: @bodhi.zazen: That's a nice setup you've got there.

---

### Post by thirtyoughtsix on 2007-08-17
hi all..

i'm using fluxbox for about month now and i'm impressed.. 
 
i just compiled 1.0rc3 and everything worked fine..

...but i'm not able to change the fonts anymore. i'm using custom style themes which worked great in the version i installed via apt.. i tried the standard styles but it's all the same.. i just have one single (quite ugly) standard font.. i'm using feisty and tried to compile fluxbox with different options (--enable-this --enable-that) but no chance.. after installing the previous version from apt again it worked.. i tried to remove it entirely but that didn't solve the problem as well.. overlay and different notations of *font i think i tried everything..

any idea? i really would like to use the new version (they fixed that annoying bug when resizing windows with no width given) but this font is really and i mean really ugly.. 

another thing is i would like to maximize my windows on doubleclick (*i know i know but i'll never get used to anything else*)..
is there another way than changing the source code (as described here: [http://fluxbox-wiki.org/index.php/Howto_Make_dblclick_titlebar_maximize](http://fluxbox-wiki.org/index.php/Howto_Make_dblclick_titlebar_maximize))?

thanks

---

---

### Post by boob11 on 2007-08-21
Thanks a lot.

---

### Post by RedSquirrel on 2007-08-21
> **thirtyoughtsix said:**
> hi all..

i'm using fluxbox for about month now and i'm impressed.. 
 
i just compiled 1.0rc3 and everything worked fine..

...but i'm not able to change the fonts anymore. i'm using custom style themes which worked great in the version i installed via apt.. i tried the standard styles but it's all the same.. i just have one single (quite ugly) standard font.. i'm using feisty and tried to compile fluxbox with different options (--enable-this --enable-that) but no chance.. after installing the previous version from apt again it worked.. i tried to remove it entirely but that didn't solve the problem as well.. overlay and different notations of *font i think i tried everything..

any idea? i really would like to use the new version (they fixed that annoying bug when resizing windows with no width given) but this font is really and i mean really ugly.. 

Weird. I have not had this problem. I normally use custom styles, but as a test, I copied the "Operation" style from /usr/local/share/fluxbox/styles into ~/.fluxbox/styles and changed the window.font to 'dejavuserif 16'. As you can see from my screenshot, it worked. I am running Fluxbox SVN 5056.

Are you using the 1.0rc3 code from the main Fluxbox hompage? If so, maybe you could try the SVN code instead. I have never had any problems changing fonts on any of the SVN versions I have built (and I have built a large number of them! :)).

If I get some time later today, I will build the 1.0rc3 code from the main homepage and see if I can reproduce your issue. 




> **thirtyoughtsix said:**
>  another thing is i would like to maximize my windows on doubleclick (*i know i know but i'll never get used to anything else*)..
is there another way than changing the source code (as described here: [http://fluxbox-wiki.org/index.php/Howto_Make_dblclick_titlebar_maximize](http://fluxbox-wiki.org/index.php/Howto_Make_dblclick_titlebar_maximize))?


None that I'm aware of, but I don't maximize windows at all so this is not something I've delved into very deeply.


Update:

I built the plain 1.0rc3 from the tarball on the main homepage and I can change fonts (see second screenshot). 

Try using the fonts I used in my screenshots and see if they work. If you copy one of the system style files to your ~/.fluxbox/styles directory and still can't change fonts on that to something else, I'm not sure what to suggest. It sounds like something is being overridden somewhere. Perhaps your overlay file is causing the issue, but I'm not sure. If you don't use the overlay file for now (e.g., if you rename it) and just change the style files themselves, does that work?


Update (again):

I put this in my overlay file:

```
*font:  dejavuserif-18
```and for "Operation" system style, it only affects the toolbar. Interesting. This is just one of those things you have to play around with, I guess. :)






Screenshots...

1st one is on SVN 5056
2nd one is on plain 1.0rc3

---

### Post by TeaSwigger on 2007-09-06
Hello, first I'd like to thank the op, RedSquirrel and yabbadabbadont for the great info contributed to the forum re: fluxbox. It's been enormously helpful.

I have a non-critical question. Here's what I'm trying to do: run Fluxbox over Kubuntu. My second PC is as slow as a badly needed tax return (a 2003 budget dell w/ 256mb ram, but the Celeron processor is really, really lame). I've been learning Kubuntu on my first PC and really like the majority of KDE apps but the speed and simplicity of FB is a real plus on the sluggish box. So I'm trying to optimize a bit without too much trouble, being a 2nd PC.

In the first post there's mention of compiling with the opt "disable-xmb." As the fluxbox in the repos seems fairly up to date I'd installed it. The question is, would this option still be relevant and if so is there a way to incorporate it in the existing install? It takes ~15 sec to load fluxbox; don't know if that's long or not since it seems really light for that amount of delay.

---

### Post by yabbadabbadont on 2007-09-06
15 seconds may, or may not, be slow depending upon what is being run in your ~/.fluxbox/startup file.  (the speed of the hard drive can also be a factor)  As a test, you might try commenting out (put a # in front of) every line in that file **except** for the line containing "exec fluxbox".

---

### Post by TeaSwigger on 2007-09-06
> **yabbadabbadont said:**
> 15 seconds may, or may not, be slow depending upon what is being run in your ~/.fluxbox/startup file.  (the speed of the hard drive can also be a factor)  As a test, you might try commenting out (put a # in front of) every line in that file **except** for the line containing "exec fluxbox".

Absolutely nothing extra loading at startup, it's still a default config.

---

### Post by RedSquirrel on 2007-09-07
> **TeaSwigger said:**
> Absolutely nothing extra loading at startup, it's still a default config.
That's odd. I have never had any delays in Fluxbox starting up, even on an old computer. 15s seems kind of long to me, but I guess it depends on individual systems and perhaps (?) what else is running. Still, with your RAM, I'm surprised that it would take that long...

I don't think I would worry too much about the xmb issue. The first post in this thread hasn't been updated in a while and I don't think the issue has been present in recent Fluxbox packages (hasn't been a problem for me, anyway). 

By the way, which version of Fluxbox are you using?

What is the speed of that celery (err, celeron) processor?

---

### Post by TeaSwigger on 2007-09-07
lol Celery indeed, and wilted at that. My three years older PIII blows it away. Anywho it's a 1.6mhz Celeron, 256mb ram... hm will have to check on the graphics card, which could be the root of the matter since it also won't "do" usplashing if that's potentially relevant. I've had to use "nosplash" in grub, not worked around to that issue yet since it's a second pc and is working otherwise.

Thanks for the answer re: XMS, I'll relieve my mind of it. ;)

I'm running what's in the repos at the moment, 0.9.15.1+1.0rc2-1 according to their rather extensive reckoning. There's nothing added in the startup file. It does feel slow to load.  I've just popped fluxbox onto the PIII and it comes up in just a few seconds (taking a liking to fluxbox, in fact). I'm not concerned about the loading time per se, more that it might indicate something else perhaps worth looking into further.

If I may I have a question about a point early in the thread:

> **yabbadabbadont said:**
> You could also install gtk-theme-switch.  Then run 'switch' to change your gtk 1 theme and 'switch2' to change your gtk 2 theme.

That sounds like a great idea for a fluxbox-only install but would using this method potentially "mess up" the theming, font size and all that, if one were to use KDE some of the time?

---

### Post by RedSquirrel on 2007-09-08
> **TeaSwigger said:**
> I'm running what's in the repos at the moment, 0.9.15.1+1.0rc2-1 according to their rather extensive reckoning. 

OK. I just wondered if maybe you were using the development package from gutsy or something. I haven't had any issues with a slow startup using the 1.0rc2 version from the repositories.


> **TeaSwigger said:**
> There's nothing added in the startup file. It does feel slow to load.  I've just popped fluxbox onto the PIII and it comes up in just a few seconds (taking a liking to fluxbox, in fact). I'm not concerned about the loading time per se, more that it might indicate something else perhaps worth looking into further.

I'm not sure what the cause might be. My old ATI card is holding up pretty well. Someone else might have some ideas, though... ;)



> **TeaSwigger said:**
> If I may I have a question about a point early in the thread:

That sounds like a great idea for a fluxbox-only install but would using this method potentially "mess up" the theming, font size and all that, if one were to use KDE some of the time?

I don't think KDE applications would be affected since they use a different toolkit (Qt), not GTK. 

This post by yabbadabbadont (from a different thread) provides a nice way to be certain that the GTK settings apply when you run Fluxbox, but not any other WM/DE:

[http://ubuntuforums.org/showpost.php?p=3120123&postcount=114](http://ubuntuforums.org/showpost.php?p=3120123&postcount=114)

---

### Post by TeaSwigger on 2007-09-08
Thank you Red Squirrel and yabbadabbadont. 

Being as I'm building this on Kubuntu and not ubuntu, it's KDE controlling the gtk stuff instead of gnome - if I'm not mistaken - so how does this factor in, if it does? I've located a 'gtkrc' and 'gtkrc-2.0' file in ~/.kde/share/config. Do I ignore these and just go ahead and follow the suggestion in the link you gave? Just don't want to go mucking around too much without asking 'till I learn this stuff :)

EDIT: ah... hm think the idea is dawning on me lol... there's three separate types, gtk, gtk2 and Qt, and KDE's theming controls all 3 it looks like...? If the switch & switch2 method will let us control gtk & gtk2 in a fluxbox enviro, how may we control Qt apps, and do so without messin' up KDE? Or can we? 

Oh and is there a way I could use the teatime Gnome applet in fluxbox? Me & tea, tehe

---

### Post by RedSquirrel on 2007-09-10
> **TeaSwigger said:**
> I've located a 'gtkrc' and 'gtkrc-2.0' file in ~/.kde/share/config. Do I ignore these and just go ahead and follow the suggestion in the link you gave?

If you follow the method of the link above, it shouldn't cause any problems. It will only apply the settings when you login to Fluxbox. 

[EDIT: I believe that if you have the ~/.gtkrc* files in place, they will *override* the ones in ~/.kde/share/config when you run Fluxbox, but I can't be certain because I don't have KDE installed. In any case, it won't hurt anything. You can always just delete the ~/.gtkrc* files and everything will go back to the way it was (which is the point of yabbadabbadont's startup script modification ;)).]



> **TeaSwigger said:**
> how may we control Qt apps, and do so without messin' up KDE? Or can we? 

I haven't touched KDE in years so I'm not in a position to answer this. Sorry.



> **TeaSwigger said:**
> Oh and is there a way I could use the teatime Gnome applet in fluxbox? Me & tea, tehe

I've never used it (even though I like tea :)), so I'm not sure. One possibility is docker. It's in the repositories.

---

### Post by chocolatetoothpaste on 2007-09-21
So, here we are whipping a dead horse again.  I installed fluxbox, had it working great, but it wouldn't load my start up script.  No errors, it would just never load the startup.  it reloaded the theme I had chosen, but that was the extent of it.  So, the problem is, when I type in startx, it won't load fluxbox.  I have to manually type it in after starting x.  Can anyone think of why this may be?  I don't run a display manager, btw, just text based, so selecting a session is out.  Any thoughts?

EDIT:  I figured it out.  I didn't have any .xsession or .xinitrc script, since I installed my system command line only.  Also, I was having issues with fluxbox remembering my settings, so I had to do a chown to make all the files mine, cause they belonged to root.  All works well now, I hope everyone else is successful!

---

### Post by nest on 2007-09-26
people, i have installed fluxbox a few weeks ago and everything is working g8.

i just wanna do one thing that its tiring me up: put some transparency.

i've already put this commands on the xorg:

```
       Section "Extensions"
       Option "Composite" "Enable"
       Option "RENDER" "Enable"
       EndSection
```

then i put this in to xorg too (cuz i've a ati)
```

       Option        "backingstore" "true"
```

and this:

```
       Option        "AllowGLXWithComposite" "true"
```

then i run the xcompgmr and the pc turns incredible slowly :mad:. it should no happen (i've a amd2 1.9mhz with 1gb of ram and a ati xpress 1250 so...)

any ideas? :(

---

### Post by diazjavier on 2007-09-29
It works fine  with Edubuntu Feisty and Fluxbox 1.0rc3 in my AMD k6-2 475MHz with 432MB of RAM.
From Argentina, thank you very much!

---

### Post by rjmdomingo2003 on 2007-11-14
> **nest said:**
> people, i have installed fluxbox a few weeks ago and everything is working g8.

i just wanna do one thing that its tiring me up: put some transparency.

i've already put this commands on the xorg:

```
       Section "Extensions"
       Option "Composite" "Enable"
       Option "RENDER" "Enable"
       EndSection
```

then i put this in to xorg too (cuz i've a ati)
```

       Option        "backingstore" "true"
```

and this:

```
       Option        "AllowGLXWithComposite" "true"
```

then i run the xcompgmr and the pc turns incredible slowly :mad:. it should no happen (i've a amd2 1.9mhz with 1gb of ram and a ati xpress 1250 so...)

any ideas? :(
Try if this helps: [http://fluxbox-wiki.org/index.php/Transparency](http://fluxbox-wiki.org/index.php/Transparency)

---

### Post by NullHead on 2007-12-14
I just installed fluxbox and I don't have any application menus. 

Anyone know what the problem is?

---

### Post by yabbadabbadont on 2007-12-14
> **NullHead said:**
> I just installed fluxbox and I don't have any application menus. 

Anyone know what the problem is?

Known bug in Gutsy.  See the excellent menu tutorial by RedSquirrel for a solution:

[http://www.ubuntuforums.org/showthread.php?t=371144](http://www.ubuntuforums.org/showthread.php?t=371144)

---

### Post by jviscosi on 2007-12-15
The Fluxbox devs have changed from SVN to GIT as of December 13th:

> 
Changes for 1.0.1:
*07/12/13:
   * SVN IS DEAD. WE NOW USE GIT.
     - to get the latest development sources of fluxbox, run the following command and compile as usual:
       git clone git://git.fluxbox.org/fluxbox.git
       cd fluxbox
       ./autogen.sh && ./configure && make install
If you want to install the base package of git to be able to run this command, the package name is not actually "git" (which is a package of GNU tools), it's "git-core".

```

sudo apt-get install git-core

```<Insert [_GIT_]("http://www.urbandictionary.com/define.php?term=Git") joke here>

---

### Post by NullHead on 2007-12-15
> **yabbadabbadont said:**
> Known bug in Gutsy.  See the excellent menu tutorial by RedSquirrel for a solution:

[http://www.ubuntuforums.org/showthread.php?t=371144](http://www.ubuntuforums.org/showthread.php?t=371144)

Thanks! that is such a beautiful guide!!

---

### Post by RedSquirrel on 2007-12-15
> **jviscosi said:**
> The Fluxbox devs have changed from SVN to GIT...

Yep, I stumbled upon that during my Fluxbox build on Arch.

"We have switched to git..." :rolleyes: 



> **NullHead said:**
> Thanks! that is such a beautiful guide!!

Glad you liked it. :)

---

### Post by melzanis on 2008-05-25
Ok I couldn't get the version that you stated. and for some reason I can't get past option 5. I keep getting the same output:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/melzanis/Desktop/fluxbox-1.0.0/missing: Unknown `--run' option
Try `/home/melzanis/Desktop/fluxbox-1.0.0/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

I don't have a clue as to what I should do here... any help

ok so I found out what the first problem was, but now i'm getting another one about X windows:

checking for X... no
configure: error: Fluxbox requires the X Window System libraries and headers.

what can I do about this?

---

### Post by eduardosd on 2008-05-25
If you are running Gutsy or a newer release (i.e. Hardy), you have to install the package xlibs-static-dev instead of xlibs-dev. That would be:
```
sudo apt-get install xlibs-static-dev
```
That should do it. Run step 5 again and it should work.

---

### Post by melzanis on 2008-05-25
Ok good news and bad news... good news first, your command worked eduardosd. I finally got past that part. However, for the bad news that command sudo checkinstall can't be found. What might the proper command be?

ok I have it installed but when I logged out it was fast with an error that told me to login to failsafe to fix this error. When I was faced with what I believe is the GDM I found in the bottom left conner a place to select my session. I had also saw that I had a choice of 'fluxbox.desktop', so I selected that choice and was given the following error:

No Exec line in the session file: fluxbox.
Running GNOME failsafe session instead

I'm at a lose for words here, I really don't know that I did wrong. I followed the instructions, can someone please help !

---

### Post by melzanis on 2008-05-26
ok I have followed these instructions up to 8. and I'm at a lose for how to continue from that point on. Can someone please help

ok so I tried to get through section 8. and I logged out when finish, however when I logged back in under fluxbox and logged in I got a message saying it can't find fluxbox. some please help

ok I finally got it to work... just need to twick it now

Oh I thought I would ask this because I have been trying to get it to work but it just doesn't seem to want to.
I'm trying to get my key bindings to work so I can switch to the all four different workspaces. For some reason i'm not doing it right it think. 

i'm not sure where even need to change or add the code to make it do this can some one point me in the right direction please.

---

### Post by 2k! on 2008-05-29
ok i know this how-to is very dated but i know you guys can help me out. ok so i got to step two and this happened: 

tar xvzf fluxbox-1.0.0.tar.gz
tar: fluxbox-1.0.0tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

i am not a ubuntu cmd jedi so i'm lost. any help would be appreciated.

---

### Post by RedSquirrel on 2008-05-29
> **2k! said:**
> ok i know this how-to is very dated but i know you guys can help me out. ok so i got to step two and this happened: 

tar xvzf fluxbox-1.0.0.tar.gz
tar: fluxbox-1.0.0tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

i am not a ubuntu cmd jedi so i'm lost. any help would be appreciated.

Judging by the error message, it looks like you ran ' tar xvzf fluxbox-1.0.0tar.gz' when it should be  'tar xvzf fluxbox-1.0.0.tar.gz'.

If you're running Hardy Heron (Ubuntu 8.04), the fluxbox package from the repositories is up to date and works fine:

```
sudo apt-get install fluxbox
```(On Gutsty Gibbon, there are a few minor issues with the fluxbox package but it is still "usable".)

---

### Post by 2k! on 2008-05-30
hey thanks it worked, yes im using gutsy anything i should know about?

---

### Post by 2k! on 2008-05-30
ok so i just went into fluxbox and everything is blank. just a bottom bar and  when i right click a menu of options come up and one-five seem to be options. i dont know what went wrong.

---

### Post by RedSquirrel on 2008-05-30
> **2k! said:**
> hey thanks it worked, yes im using gutsy anything i should know about?

The menu does not show up when you first install it and even when you get it to show up, it may be missing some sections or entries (see solution below).

fluxbox on gutsy is missing support that allows you to have rounded window corners and the icons in the toolbar (bottom of screen) may look a little weird. I have instructions for compiling your own fluxbox if you find the issues bother you (see menu/customization tutorial link in my signature). 


> **2k! said:**
> ok so i just went into fluxbox and everything is blank. just a bottom bar and  when i right click a menu of options come up and one-five seem to be options. i dont know what went wrong.

See the menu tutorial link in my signature, specifically the sections:

[B]I installed Fluxbox from the repositories, but there is no menu when I right-click on the desktop. How do I fix this??
[/B]
and 

**The Fluxbox Menu on Gutsy Gibbon is missing some items. How can I fix this?**

---

### Post by 2k! on 2008-05-30
ok so i couldnt get it to work so i uninstalled everything that has to do with flux and im gonna update to hardy heron and im going to try it from your  tut from scratch im sure ill have more questions. thanks.

---

### Post by 2k! on 2008-05-30
ok so i upgraded to hardy and im going to try this again. any helpful tips to get me started would be great thanks.

---

### Post by RedSquirrel on 2008-05-30
> **2k! said:**
> ok so i upgraded to hardy and im going to try this again. any helpful tips to get me started would be great thanks.
As far as I know, the fluxbox package on Hardy should work pretty well without having to do too much to it. When I tried it last month, the right-click menu was available and everything seemed to work (more or less).

I have some links and information for fluxbox in my tutorial. One of the best places to look when you're starting to customize fluxbox is the wiki:

[http://fluxbox-wiki.org](http://fluxbox-wiki.org)

Have fun. :)

---

### Post by 2k! on 2008-05-30
ok i got it working now i just gotta set it up the way i want it. thanks alot.

---

### Post by melzanis on 2008-06-29
Okay so I'm back with a small problem.
     I updated my system using the command-line, I though hey I might as well restart because I using fluxbox, it doesn't tell if I need to restart. Once I restart and was booted back into the login screen, I entered my info. and I got this error I get saying it can't find the bin file ( you know the one that 'checkinstall' makes) So I've come across this 5 times now. Each time I've had to rebuild everything, however this time it's saying it faild to install the package. I'm at a lose for words on what to do here, can some one try to help me out here.

cheers

Never mind... I needed to run that 'checkinstall' command as root =P

---

### Post by mustimasti on 2008-07-07
hi guyz i m new to linux and i m trying to install fluxbox , can u tell me in which folder i should extract this fluxbox and i dont know how to edit the source file as checkinstall doesnot work can u explain in more dept like step by step, i dont know anything on ubuntu server nor on linux, if u want u can mail me on [email]mustafa.chittalwala@gmail.com[/email] please help me guyz

---

### Post by snowpine on 2008-07-07
> **mustimasti said:**
> hi guyz i m new to linux and i m trying to install fluxbox , can u tell me in which folder i should extract this fluxbox and i dont know how to edit the source file as checkinstall doesnot work can u explain in more dept like step by step, i dont know anything on ubuntu server nor on linux, if u want u can mail me on [email]mustafa.chittalwala@gmail.com[/email] please help me guyz

Hi Mustafa, if this thread is over your head :) you can try typing ```
sudo apt-get install fluxbox
``` at the command line, or go into the synaptic package manager and install the fluxbox package. This is assuming you're running Hardy Heron 8.04.

---

### Post by RedSquirrel on 2008-07-07
> **mustimasti said:**
> hi guyz i m new to linux and i m trying to install fluxbox , can u tell me in which folder i should extract this fluxbox and i dont know how to edit the source file as checkinstall doesnot work can u explain in more dept like step by step, i dont know anything on ubuntu server nor on linux, if u want u can mail me on [EMAIL="mustafa.chittalwala@gmail.com"]mustafa.chittalwala@gmail.com[/EMAIL] please help me guyz
As snowpine said, just install the fluxbox package. That's much easier.

```
sudo apt-get install fluxbox
```If you are running a version of Ubuntu older than Hardy Heron, make sure you run

```
sudo update-menus
```right after you install fluxbox. This will generate the default fluxbox menu.

---

### Post by mburg23 on 2008-08-24
im really really noob at x only got it today i want to install fluxbox ive trying everything you guys have said. ive downloaded fluxbox-1.0.0.tar.gz to desktop then unzipped it on the desktop by double clicking it. i get these msgs wen i try and do what u guys say




w4rlock@w4rlock-desktop:~$ tar xvzf fluxbox-1.0.0.tar.gz
tar: fluxbox-1.0.0.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
w4rlock@w4rlock-desktop:~$ sudo apt-get install fluxbox
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?



any suggestions

---

### Post by yabbadabbadont on 2008-08-24
> **mburg23 said:**
> any suggestions

The latest version of Fluxbox is available in the Ubuntu repositories.  At least it is in Hardy Heron (version 8.04).  Just use Synaptic to install it.

System->Administration->Synaptic Package Manager.

Edit: looks like you tried apt-get, but already had another package manager running somewhere.  (that's what the error means)  Completely log out.  Then log back in.  Now run Synaptic, search for fluxbox, and then select it.  Hit the Apply button to install it.  Now log out again.  On the Sessions menu at the login screen, there should now be a Fluxbox Session option.  If not, reboot and check again.

---

### Post by mburg23 on 2008-08-24
i figured it out i just had to do the updates then it worked so i have it installed but ...... wen i start up a fluxbox session i can only use the styles it already has and i want to use a different one that i downloaded ... so wat i did was downloaded the style. i had trouble finding the directory where my styles where. but eventually found it, it was in /usr/share/fluxbox/styles/ and i went to paste the style in i downloaded and it says i dont have permission to do that and im not sure how to change permission so i can paste and edit the themes. any suggestions on that? 


Could not save the file /usr/share/fluxbox/styles/bora_green/theme.cfg.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

---

### Post by yabbadabbadont on 2008-08-24
You just need to extract it to your user's style directory.  In your home directory, there is a hidden directory called ".fluxbox"  Note that it starts with a period.  In that directory is a styles directory.  You need to extract your style there, then it should show up in the menu for selection.

---

### Post by mburg23 on 2008-08-24
thanx heaps i think i get it now lucky you said that cause i wouldnt have thought to check for hidden files

---

### Post by mburg23 on 2008-08-24
kk this is a little off the compiling topic but installing dockapps in fluxbox. i know you have to type a command in startup to get them to work and i know there is already alot of dockapps installed without having to download them, you can view them by typing  "sudo apt-cache search dockapp"
in terminal. so what i was wondering was what you have to type in the start up script to get them to work. and or, say i downloaded a dockapp i.e "cputnik-0.1.0" where do i have to extract it to and what would i type in start up to get it to work. sorry i know this is noob stuff but its hard going form windows to X and getting it to work. 


i want somthing like 
[http://www.box-look.org/CONTENT/content-pre1/85565-1.jpg](http://www.box-look.org/CONTENT/content-pre1/85565-1.jpg)

---

### Post by RedSquirrel on 2008-08-24
The program on the left side of the screenshot you posted is called conky. It's in the repositories:

```
sudo apt-get install conky
```


Have a look at the following for information on configuring conky:

[http://conky.sourceforge.net](http://conky.sourceforge.net)
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by konza on 2008-09-03
Well, I am having trouble getting fluxbox into the start menu.  Distro:Hardy I've installed fluxbox every possible way. Synaptic,get-apt and no starting FB to be found.  Lastly I completely removed it via Synaptic and reinstalled it the same way.  Still nothing in the start menu.  Redsquirrel, following your help text elsewhere the following is as far as i can get.  It looks to me like everything that should be there is but still no fluxing luck.LOL    Am I missing something or what?
 
konza@konza-laptop:~$ dpkg -l fluxbox
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  fluxbox        1.0.0-3        Highly configurable and low resource X11 Win
konza@konza-laptop:~$ ls -l /usr/share/xsessions/
total 24
-rw-r--r-- 1 root root  235 2007-12-09 15:44 fluxbox.desktop
-rw-r--r-- 1 root root  235 2008-09-03 15:43 fluxbox.desktop~
-rw-r--r-- 1 root root 2948 2008-04-10 11:10 gnome.desktop
-rw-r--r-- 1 root root 9715 2008-07-17 14:14 ssh.desktop

---

### Post by snowpine on 2008-09-04
> **konza said:**
> Well, I am having trouble getting fluxbox into the start menu.  Distro:Hardy I've installed fluxbox every possible way. Synaptic,get-apt and no starting FB to be found.  Lastly I completely removed it via Synaptic and reinstalled it the same way.  Still nothing in the start menu.  Redsquirrel, following your help text elsewhere the following is as far as i can get.  It looks to me like everything that should be there is but still no fluxing luck.LOL    Am I missing something or what?
 
konza@konza-laptop:~$ dpkg -l fluxbox
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  fluxbox        1.0.0-3        Highly configurable and low resource X11 Win
konza@konza-laptop:~$ ls -l /usr/share/xsessions/
total 24
-rw-r--r-- 1 root root  235 2007-12-09 15:44 fluxbox.desktop
-rw-r--r-- 1 root root  235 2008-09-03 15:43 fluxbox.desktop~
-rw-r--r-- 1 root root 2948 2008-04-10 11:10 gnome.desktop
-rw-r--r-- 1 root root 9715 2008-07-17 14:14 ssh.desktop

By "start menu" do you mean the applications menu? If so, Fluxbox won't appear there. You need to log out, then from the GDM login screen, click on the Sessions menu and choose Fluxbox. Let us know if that works!

---

### Post by konza on 2008-09-05
Thanks snowpine and sorry for being vague. The menu i was referring to was :
System>Administration>Login Window. From the dropdown in Login Window Preferences chose Fluxbox(yes it is there)and checked it as the Default.  Did the ctrl,alt, backspace to restart things.  When i right click on the desktop it still only gives me the gnome options box,(Create folder-launcher-document, keep aligned and change desktop background) I also did a complete restart of the computer for the heck of it...to no avail.  If it is of any consequence i use Hardy as the only OS on a HP laptop.

---

### Post by snowpine on 2008-09-05
> **konza said:**
> Thanks snowpine and sorry for being vague. The menu i was referring to was :
System>Administration>Login Window. From the dropdown in Login Window Preferences chose Fluxbox(yes it is there)and checked it as the Default.  Did the ctrl,alt, backspace to restart things.  When i right click on the desktop it still only gives me the gnome options box,(Create folder-launcher-document, keep aligned and change desktop background) I also did a complete restart of the computer for the heck of it...to no avail.  If it is of any consequence i use Hardy as the only OS on a HP laptop.

I've never tried to switch to Fluxbox using the method you describe; try using the Sessions dropdown on your login (GDM) screen like I described in my previous post.

If you are indeed in Fluxbox but you get the Gnome options when you right click the background, it probably means you are running Nautilus file browser. To use Nautilus in Fluxbox, you must start it with the command:

```
nautilus --no-desktop
```

That will keep it from trying to manage your desktop (which is a big mess). I personally prefer to use the Thunar file manager with Fluxbox because it does not mess with the desktop like Nautilus.

Hope that helps!

ps if problems persist, maybe check your /.fluxbox/startup file to make sure you aren't running Nautilus at startup (or if you are, use --no-desktop like I said).

---

### Post by konza on 2008-09-05
Ata Kili ! (really magnificent) Snowpine, while pouring over your replies something caught my eye.  All along i have had "sessions" and :login window" stuck in my brain.  To get to the login window, well, i found that under 'Administration' and indeed from there one can choose what  you wish to use as a desktop. FROM the login screen...FROM finally registered to me.  Duhhh, the rest from there on out was fine.  Thanks again,  for helping and having patience with new person to Ubuntu.

---

### Post by haiyun211 on 2009-05-22
hi guys way new to ubuntu but I am stuck on the step of make it will not work for me and the command sudo checkinstall says no command exists.  Help please?

---

### Post by RedSquirrel on 2009-05-23
> **haiyun211 said:**
> hi guys way new to ubuntu but I am stuck on the step of make it will not work for me and the command sudo checkinstall says no command exists.  Help please?
Is there a reason you are compiling fluxbox from source? The **fluxbox** package in the repositories works well.

```
sudo apt-get install fluxbox
```

---

### Post by haiyun211 on 2009-05-23
because they said that that one in the repository is outdated.

---

### Post by RedSquirrel on 2009-05-23
> **haiyun211 said:**
> because they said that that one in the repository is outdated.

Who is "they"? Are you referring to the author of this tutorial? The first post hasn't been touched for over three years. :)

The fluxbox package on older Ubuntu releases had a few problems, but it's much better these days.

Which Ubuntu release are you running?

---

### Post by haiyun211 on 2009-05-23
9.04 and I did what you said and dont really know where to go from here?  I have only been using ubuntu for one day.

---

### Post by snowpine on 2009-05-23
> **haiyun211 said:**
> 9.04 and I did what you said and dont really know where to go from here?  I have only been using ubuntu for one day.

Relax and enjoy Ubuntu as it is meant to be enjoyed for at least a few days. :) You don't need to jump into the advanced stuff right away. (Especially trying to follow a outdated tutorial for an older release.)

---

### Post by haiyun211 on 2009-05-23
Well the main reason I switched to Ubuntu is so I can setup my layout the way I would like it to look and really make it my own thats why I have been so up on getting fluxbox going so I can start to customize my windows and have that transparent look to them.

---

### Post by snowpine on 2009-05-23
> **haiyun211 said:**
> Well the main reason I switched to Ubuntu is so I can setup my layout the way I would like it to look and really make it my own thats why I have been so up on getting fluxbox going so I can start to customize my windows and have that transparent look to them.

That is admirable, but check the dates on any tutorial you follow to make sure it applies to the version of Ubuntu you're using (April 2009 or newer).

---

### Post by haiyun211 on 2009-05-23
Thanks for the advice I installed it the way of "sudo apt-get install fluxbox" and have not found anything to take me from here.

---

### Post by snowpine on 2009-05-23
> **haiyun211 said:**
> Thanks for the advice I installed it the way of "sudo apt-get install fluxbox" and have not found anything to take me from here.

You have to log out, then from the login screen, choose Fluxbox under the Sessions menu.

Or, enjoy the Gnome desktop that is the Ubuntu default for at least a day or two. :)

---

### Post by haiyun211 on 2009-05-24
Thanks that worked great now I cant figure out how to connect to my wireless from flux box and so I switched back to gnome to do some research.  Do you know of any good detailed websites on how to get started on fluxbox or maybe if you would not mind helping me its up to you but thanks for your help so far.  I hate being a newb.

---

### Post by RedSquirrel on 2009-05-24
[http://fluxbox.org](http://fluxbox.org)
[http://fluxbox-wiki.org](http://fluxbox-wiki.org)

man pages for fluxbox and fluxstyle. In a terminal, run:

```
man fluxbox
```and
```
man fluxstyle
```Press 'q' when you are done reading the man pages.

I don't use wireless, so I can't help with that. However, there are most likely some posts about it which you could find by searching the forums. Good luck. :)

If you have more fluxbox-related questions, it might be a good idea to ask them in the [Desktop Environments forum]("http://ubuntuforums.org/forumdisplay.php?f=329"). More people will see your question there. ;)

---

### Post by haiyun211 on 2009-05-24
Thanks man that will help alot.

---

### Post by xdemo on 2010-03-02
First off, old post... but deserves a bump. Tutorial helped me out alot in trying to find out why the fluxbox package (in the karmic repo's) seems to take ages to load up (almost 40 seconds!), 

Just downloaded the 1.1.1 tarball and compiled wit[FONT=monospace]h the "--disable-xmb" param, [/FONT]sped it up to about 3 seconds from gdm!
[FONT=monospace]
[/FONT]> **haiyun211 said:**
> Thanks that worked great now I cant figure out how to connect to my wireless from flux box and so I switched back to gnome to do some research.  Do you know of any good detailed websites on how to get started on fluxbox or maybe if you would not mind helping me its up to you but thanks for your help so far.  I hate being a newb. 

You need to use "nm-applet --sm-disable &" in your ~/.fluxbox/startup to enable wireless, at least, it works for me.

@op thanks for tutorial.

---

### Post by Rodney9 on 2011-06-26
Fluxbox the fastest

---

