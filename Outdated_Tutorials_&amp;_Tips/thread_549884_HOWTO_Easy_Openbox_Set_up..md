---
title: "HOWTO: Easy Openbox Set up."
date: 2007-09-13
forum: Outdated Tutorials &amp; Tips
---

### Post by shearn89 on 2007-09-13
In response to a post in the Screenshot thread, here is a quick howto on how to get Openbox up and running...
All commands in "code" tags should be run in a terminal. I have also added command-line instructions, for those who like to do things the CL way! These are prefixed with "Code:". Ignore it if you wish.

N.B - I myself had some problems with the autostart file working. This was fixed (for me) by reinstalling Openbox using the .deb from the website. In the meantime, if your autostart isn't working, i'd suggest trying the package in the Gutsy repos (if you're on gutsy), or the official deb. I'm fairly certain the gutsy repo version is the latest, as I Gutsy is no longer in beta testing.

**This howto has been fully tested on Feisty and Gutsy 32bit. I don't have any idea about 64bit, or Dapper.**
This howto should be safe, and poses no risk in terms of breaking your system, however, I obviously take no responsibility. If you do get stuck or something breaks, post a reply to this (preferably with some feedback about where/how you got stuck) or in the "Random Openbox Chatter" thread (community cafe). Someone should be able to help you out!

**1. Grab the latest .deb from here:** [http://icculus.org/openbox/releases/openbox_3.4.4-0ubuntu1_i386.deb](http://icculus.org/openbox/releases/openbox_3.4.4-0ubuntu1_i386.deb)
and run it. This can be done either by clicking on the link and opening the file, or with the following command (assuming it downloads to the home folder):
```

wget http://icculus.org/openbox/releases/openbox_3.4.4-0ubuntu1_i386.deb
dpkg -i openbox_3.4.4-0ubuntu1_1386.deb

```
If it downloaded to the Desktop folder (or any other), you will have to insert "cd <directory>" after the wget.

[B]
2. Get the configuration tool from here:[/B]
[http://icculus.org/openbox/obconf/obconf_2.0.2-0ubuntu1_i386.deb](http://icculus.org/openbox/obconf/obconf_2.0.2-0ubuntu1_i386.deb)
and run it.
```

wget http://icculus.org/openbox/obconf/obconf_2.0.2-0ubuntu1_i386.deb
dpkg -i obconf_2.0.2-0ubuntu1_i386.deb

```

[B]
3. Grab the other stuff that you might want:[/B]
```

sudo apt-get install thunar thunar-volman-plugin pypanel feh

```
and also this:
[http://david.chalkskeletons.com/scripts/wallmenu-0.3.py](http://david.chalkskeletons.com/scripts/wallmenu-0.3.py)
Move the wallmenu script to your home directory, and rename it ".wallmenu.py".
Then open it (you may need to press ctrl-h to view hidden files).
```

wget http://david.chalkskeletons.com/scripts/wallmenu-0.3.py
mv wallmenu-0.3.py .wallmenu.py
gedit .wallmenu.py

```
Change the following bits:
```

# --------------------------------------------------------------------------- #
#                             User configuration                              #
# --------------------------------------------------------------------------- #
# types of files accepted (list, seperated by a |)
filetypes = "jpg|png|gif**|jpeg**"
# directory where wallpapers are stored (must be long: no ~ symbol allowed)
directory = "/home/**<your username>/<your wallpaper directory>**"
# program to set wallpaper
program = "feh --bg-scale"

```
*Thunar* is the lightweight file manager we'll be using, the volman-plugin is a plugin for it that deals with mounting/unmounting volumes (similar to the nautilus equivalent).
*Feh* is the program we'll be using for setting the background - it is a command line image viewer (can do slideshows and things - see "feh --help" for more info).
*Pypanel* is the panel and system tray we'll be using. See [the sourceforge page]("http://pypanel.sourceforge.net/") for more info.
_There are a number of alternatives to these programs;_ You CAN use nautilus instead of thunar, although it is slower and you have to be careful not to let it draw the desktop, and I know others use konqueror. I use thunar mainly because konqueror (to my knowledge) depends on a lot of libraries not on a default Ubuntu install - if you installed *Kubuntu*, konqueror would be a good choice. If you have a hunt around the forums, or on google, you will come across huge numbers of other options - look for "file managers".
*Pypanel* is used here because it is a popular choice, and the default configuration file is quite nicely setup and easy to change. I personally use XFCE4-Panel (installable via apt-get), but you could also try Perlpanel or Visibility. Again, check the forums or google.
As **fuscia** says - > one of the intentions of openbox is to get out of people's way so that they can run whatever apps they wish, so it's important, i think, to make people aware of how wide their choices are.


**4. Copy the default configuration file** to your openbox config directory so you can change keybindings etc.
```

cp /etc/xdg/openbox/rc.xml ~/.config/openbox/

```
If you want to, you can set your most-used programs to be launched with keyboard shortcuts. This is all done in this file. Open it with gedit, and find the section with lots of entries saying <keybind>. These can be changed to launch whatever you like (I have mine set up so that Alt-f1 launches rxvt, alt-f2 launches firefox, alt-f3 launches thunar. When you're done, save the file. If you're doing this from inside openbox, you need to reconfigure it with the menu shortcut.

**5. Download the menu.tar.gz attachment from the bottom of this post**, and extract it into ~/.config/openbox/
```

wget http://www.mediamax.com/shearn89/Hosted/menu.tar.gz
mv menu.tar.gz ~/.config/openbox/
cd ~/.config/openbox/
tar -xvf menu.tar.gz

```
[B]
6. Download the autostart.sh attachment from the bottom of this post,[/B] and copy it to the same place.
Code:
```

wget http://www.mediamax.com/shearn89/Hosted/autostart.sh
mv autostart.sh ~/.config/openbox/

```
This autostart script loads most of the useful things (screensaver daemon, keyring, gnome settings to match themes). It **also** loads Gaim - if you don't want this, you need to open the autostart.sh and remove the line saying "gaim &".
For more info on Autostart scripts, have a look at [this page]("http://icculus.org/openbox/index.php/Help:Autostart")

**7. Finally, logout**, go to "Options -> Select Session -> Openbox" and log back in again. You should be all done! 

You may also want to install Nitrogen (a background chooser) so hunt round the forums, as I can't get it to work. In this howto we installed "feh" and what is called a "Pipe menu", which applies backgrounds for you.

Any questions/feedback/errors please tell me - i'll try and answer ASAP.

Other tools you may want to try:
Tint Task Manager (TTM) (ttm.googlecode.com)
XFCE4-panel (from the repos: "sudo apt-get install xfce4-panel")
Visibility (not sure where to find it).


*_NOTES:_*
This was tested on my laptop (640Mhz, 10GB HD, 512MB RAM), running Feisty 32bit install on i386 archictecture. Now also tested in Gutsy! yay!

*_Changelog:_*
29/10/07 - Fixed some typos, and added a short sentence on the rc.xml file. Added a disclaimer, and some info on what it's been tested on. Look out for urukrama's OB guide coming soon!
16/09/07 - Changed the terminal command for getting the attachments - now hosted offsite.
14/09/07 - Added link to Autostart page on OB site, and added info on the installed programs. Changed formatting for easier viewing. Added terminal code for downloading etc. Added comments on different programs.

---

### Post by ArtF10 on 2007-09-14
Sounds good.....When you say "Grab the latest .deb from here" and run it, is there a way to do this from the terminal rather than downloading and clicking because I've had problems with those type of instructions.  Even extracting something somewhere....can it all be done entirely from the terminal?  

That would really help.

---

### Post by shearn89 on 2007-09-14
Yes - I'll add it in to the Howto.

---

### Post by ArtF10 on 2007-09-14
many thanks.

---

### Post by K.Mandla on 2007-09-14
Can you wget an attachment from the forums? When I wget it, I get a file called "attachment ..." that looks like the HTML for the page. You might have to host it offsite and link to there. :(

Otherwise, nicely done. ;)

---

### Post by shearn89 on 2007-09-15
Ahh. I'll investigate today when I get back from work - can't do anything at the moment. For now, people will just have to click and save...

---

### Post by PrimoTurbo on 2007-09-24
How do I make feh save background choice when I log out?

---

### Post by PrimoTurbo on 2007-09-24
I tried adding eval `cat ~/.fehbg` & to /.xinitrc but it doesn't work, I use gdm to login and there is an option for ~/.fehbg & in autostart already

---

### Post by shearn89 on 2007-09-27
If you get the latest .deb from the OB site, you can just create an autostart.sh file, as shown here. The older versions of OB for some reason don't use the autostart.sh file. If ~/.fehbg is in autostart, it should work on OB3.4

---

### Post by Hugo Galvão on 2007-10-01
> **PrimoTurbo said:**
> I tried adding eval `cat ~/.fehbg` & to /.xinitrc but it doesn't work, I use gdm to login and there is an option for ~/.fehbg & in autostart already

You simply need to
```

ln -s ~/.xinitrc ~/.xsession

```
I think Ubuntu looks for .xsession instead of .xinitrc, so making that simple link will do the trick, and your .xinitrc script will work

---

### Post by PrimoTurbo on 2007-10-02
Problem was that my wallpapers had a space in the filename, I had to rename them all for it to work. Is there anyway to make wallpapers with a space in the filename to work?

---

### Post by Hugo Galvão on 2007-10-02
> **PrimoTurbo said:**
> Problem was that my wallpapers had a space in the filename, I had to rename them all for it to work. Is there anyway to make wallpapers with a space in the filename to work?

Yes, but you have to edit the ~/.fehbg file, what you need to do is put a backslash before any space in the path to the wallpaper

Example, if you have
```

feh --bg-scale /home/primoturbo/wallpapers/this wallpaper.png

```
You change it to
```

feh --bg-scale /home/primoturbo/wallpapers/this\ wallpaper.png

```
Or you just quote the path
```

feh --bg-scale '/home/primoturbo/wallpapers/this wallpaper.png'

```
But for some reason, ~/.fehbg will be "corrected", so the first time it will work, but the next time you login, the ~/.fehbg file will be as it was, with spaces as they were. The simple solution, is to just point feh to do it in your .xinitrc script, so, instead of having
```

eval `cat $HOME/.fehbg`

```
in you .xinitrc script, you change it to
```

feh --bg-scale /home/primoturbo/wallpapers/this\ wallpaper.png

```

---

### Post by shearn89 on 2007-10-03
Im surprised that the autostart.sh isn't working - with the latest version of OB its meant to look for "~/.config/openbox/autostart.sh" first. I'll do some investigating, and try and post my results here.

---

### Post by Orlando84 on 2010-06-28
Hi!
Nice tut, I've edited autostart.sh with my needs and there were some mistakes with wallpapers, but when I've edited them too it started to work nice, can even set wallpapers from menu.
Thanks a lot.
My laptop lives on 2Gb memory stick with Ubuntu, with Openbox. That's great!

---

