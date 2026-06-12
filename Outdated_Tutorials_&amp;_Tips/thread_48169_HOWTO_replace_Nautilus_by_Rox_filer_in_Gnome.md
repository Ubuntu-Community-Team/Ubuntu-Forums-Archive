---
title: "HOWTO: replace Nautilus by Rox filer in Gnome"
date: 2005-07-11
forum: Outdated Tutorials &amp; Tips
---

### Post by Laurent Cazalet on 2005-07-11
I like Gnome, but I'm always annoyed by Nautilus. And when you use Gnome, Nautilus gets in your way all the time, while I prefer a lot the agile Rox filer.

Here's a way to combine the best of both.

This script aims to transparently use Rox filer instead of Nautilus.
This HOWTO also gives a method to mount Gnome-VFS drives onto the system so that they are available to non-Gnome programs (like Rox filer).

[SIZE=4]Objective:[/SIZE]

Rox filer (or another file manager) runs as a transparent replacement of Nautilus everytime the system calls /usr/bin/nautilus. This is a user-specific hack. It doens't affect other users of the system.

In particular in the following cases
- open folder from Places menu and panels
- open automatically mounted media (CDROM, usb drive etc...)
- open trashcan clicking from Gnome panel (if TRASHDIR is set)
- "open folder" when called from Search dialog box
- open network drives (if Fuse and another tools are installed, see advanced topic below)

Opens normally Nautilus if:
- the environment variable NAUTILUS_REPLACEMENT is not set
- Nautilus browser mode is requested (--browse flag) (independant from settings)
- click on computer, network servers entries in Places menu
- open network drives from Places menu (if fuse not configured)
- click on trash applet and env. var. TRASHDIR is not set
- Nautilus is configured to draw the desktop and you click on desktop icons (not a feature of the script, though :)

As a side note, 
- You can still have Nautilus draw the desktop 
- drag-and-drop to trash applet works okay from Rox.


[SIZE=3]But...[/SIZE]
- under Metacity (standard Gnome window manager), Rox filer often opens new windows beneath the active window. workarounds if it's to annoying: use xfwm4 or openbox window manager.
- (minor) Opening Home Folder from the Places menu works fine but gives visual notification timeout
- if Nautilus gets updated, the script will have to be reinstalled.

[SIZE=4]Installation[/SIZE]
Five easy steps

1: install rox filer
```
sudo apt-get install rox-filer
```
2: Set nautilus aside
```
sudo mv /usr/bin/nautilus /usr/bin/nautilus.bin
```
3: Save this script as /usr/bin/nautilus (you must be root)
```

#!/bin/bash
#replacement/wrapper for nautilus
# also mounts network drives using gnomevfs-mount (using fuse)
# doesn't check if already mounted

NAUTILUS=/usr/bin/nautilus.bin
DEBUG=0
# backup our args list
ARGS=$@
ARGSCOUNT=$#

# call nautilus, with all args received in input
function run_nautilus() {
    [ $DEBUG != 0 ] && echo "OUT: Running Nautilus" >> $HOME/nautilus_wrapper.log
    exec $NAUTILUS $ARGS
}

# calls the replacement, only arg must be an existing dir
function run_replacement() {
    [ $DEBUG != 0 ] && echo "OUT: Running $NAUTILUS_REPLACEMENT. Args: '$@'" >> $HOME/nautilus_wrapper.log
    exec $NAUTILUS_REPLACEMENT $@
}

# make a directory where to mount our network drive
function makemountdir() {
    # get the server part of the URI
    SERVER="`echo \"$1\" | sed -e 's/^(https\|http\|sftp\|ftp\|ssh)//' -e 's/:\/\///' -e 's/.*@//' -e 's/\/.*//'`"
    MOUNTDIR=$MOUNTROOT/$SERVER
    [ $DEBUG != 0 ] && echo "...: Mounting $1 on $MOUNTDIR" >> $HOME/nautilus_wrapper.log
    mkdir -p $MOUNTDIR
}

[ $DEBUG != 0 ] && echo "IN: $0 invoked with '$@'" >> $HOME/nautilus_wrapper.log

# if this user didn't configure a replacement, just give way to nautilus
if [ -z "$NAUTILUS_REPLACEMENT" ]; then
    run_nautilus
fi


# loop through all args to see if one of them requires
# that we run nautilus
while [ -n "$1" ]; do
    case "$1" in
        -c|--check) ;;  #ignore
        -g) shift ;;  #ignore, and ignore next one
        --geometry) ;;  #ignore
        --no-desktop) ;; #ignore
        --sm-disable) ;; #ignore
        -n|--no-default-window)
            # run nautilus if not asked for anything else
            #if this is the only argument, start nautilus
            # this happens when nautilus is asked to draw the desktop
            if [ $ARGSCOUNT == 1 ]; then
                run_nautilus
            fi;;
        --sm-client-id) run_nautilus;;
        -? | --help) run_nautilus;;
        --usage) run_nautilus;;
        --browser) run_nautilus;;
        -q|--quit) run_nautilus;;
        computer*) run_nautilus;;
        network*)  run_nautilus;;
        trash*)
            if [ -z "$TRASHDIR" ]; then
                run_nautilus
            else
                run_replacement "$TRASHDIR"
            fi;;
        file*)
            # turn the file:/// URI into a filesystem path,
            FILE="`echo \"$1\" | sed -e 's/^file:\/\///' -e 's/%20/\ /g'`"
            run_replacement "$FILE";;

        ftp* | sftp* | http* | smb* | ssh* )
            #if we can mount this network dir through
            # Fuse and gnomevfs-mount, do it
            if [ -e /usr/bin/gnomevfs-mount ] && [ -n "$MOUNTROOT" ]; then
                makemountdir "$1"
                /usr/bin/gnomevfs-mount "$1" "$MOUNTDIR"
                run_replacement "$MOUNTDIR"
            else
                run_nautilus
            fi;;
        *)
            # unknown arg. if it's a filesystem object, use replacement
            # otherwise give up and start nautilus
            if [ -e "$1" ]; then
                run_replacement "$1"
            else
                [ $DEBUG != 0 ] && gmessage "$0 $ARGS" &
                run_nautilus
            fi;;
        esac
        shift
done

#default: open home dir
run_replacement $HOME
exit 0

```
4: change ownership and make this script executable
```

sudo chown root.root /usr/bin/nautilus
sudo chmod a+x /usr/bin/nautilus

```
5: Add this to ~/.gnomerc
So that changes affect only users that want it.
```

NAUTILUS_REPLACEMENT=/usr/bin/rox
TRASHDIR=$HOME/.Trash
export TRASHDIR NAUTILUS_REPLACEMENT

```
[SIZE=4]Advanced topic[/SIZE]
Icing on the cake: Fully take advantage of Nautilus network drives (using gnome-vfs) with any non-Gnome programs like Rox filer.

Not a full how-to, but it should be straightforward.

- compile and install fuse kernel module and library ([http://fuse.sourceforge.net/](http://fuse.sourceforge.net/))
(haven't tested the ubuntu package)
- compile and install gnomevfs-mount from [http://gnomedesktop.org/node/1981/31756](http://gnomedesktop.org/node/1981/31756) 
  be sure to --enable-keyring when running ./configure
(ask me for a deb package if you need to) 
- add this to your ~/.gnomerc (create it if it doesn't exist)
```
MOUNTROOT=$HOME/mnt
export MOUNTROOT
```
Configure your network drives from the Gnome interface, as you would normally do.

Enjoy automounting of those drives to $HOME/mnt/<server>
Clicking on the net drive from the Places menu mounts the drive and opens
rox-filer at the correct location.

To unmount those drives, call 
```
gnomevfs-umount $HOME/mnt/<server>
```
(I added a link to this command to  the mountpoint send-to of Rox filer)

Usual disclaimer: I'm not responsible if you **** your system up.

---

### Post by sapo on 2005-07-11
whats the difference between rox and nautilus? where can i read more about it? i really dont know this app...

---

### Post by bored2k on 2005-07-11
[QUOTE=sapo]whats the difference between rox and nautilus? where can i read more about it? i really dont know this app...[/QUOTE]
 I know rox is faster than the speed of light, but, I'm also curious (i never used rox.. just a bit).

Why should I use it instead of the beloved nautilus ? Why is it so much better ?

---

### Post by cutOff on 2005-07-11
[QUOTE=bored2k]Why should I use it instead of the beloved nautilus ? Why is it so much better ?[/QUOTE]
Not a flame but I wonder the same thing.

---

### Post by Mr. Electric Wizard on 2005-07-11
The only thing I don't like about Nautilus is the fact that it opens a new "window" when you drill down through a directory.
It would be nice if you could keep this from happening and have only the "active" window open.
I hate when I drill down, the child directory is always really tiny, and I have to resize it...

---

### Post by Heliode on 2005-07-11
[QUOTE=Mr. Electric Wizard]The only thing I don't like about Nautilus is the fact that it opens a new "window" when you drill down through a directory.
It would be nice if you could keep this from happening and have only the "active" window open.
I hate when I drill down, the child directory is always really tiny, and I have to resize it...[/QUOTE]

Open nautilus -> Edit -> Preferences -> Behaviour -> Select 'Always open in browser'
et voila!

I might have some of the names wrong (since I run Ubuntu in Dutch) but you should be able to figure it out. Also, when you have that, you can set the left panel to 'tree' so you get something that looks like Explorer on Windows.

---

### Post by bored2k on 2005-07-11
[QUOTE=Heliode]Open nautilus -> Edit -> Preferences -> Behaviour -> Select 'Always open in browser'
et voila!

I might have some of the names wrong (since I run Ubuntu in Dutch) but you should be able to figure it out. Also, when you have that, you can set the left panel to 'tree' so you get something that looks like Explorer on Windows.[/QUOTE]
 Exactly. That's the "fix" for Spatial nautilus introduced in Gnome 2.6. 

Any other reason why I should use rox ?

---

### Post by tread on 2005-07-11
Also, are file extensions registered as well as in nautilus?

---

### Post by regeya on 2005-07-11
[QUOTE=bored2k]Exactly. That's the "fix" for Spatial nautilus introduced in Gnome 2.6. 

Any other reason why I should use rox ?[/QUOTE]

Well, I'm not considering the move, but ROX is fast as lightning.  It's not the prettiest thing, but it's fast as lightning.

I don't see the point of using ROX unless you want to commit to the full-meal deal:  ROX-Desktop, the Pinboard, App dirs, etc.  Otherwise it's just a second-rate Finder-ish filemanager, IMHO.

This might be a nice thing to do with xfce on a low-resources machine, maybe. *shrug*

---

### Post by Laurent Cazalet on 2005-07-12
Well...
This howto is not meant to be a Rox filer advocacy. Look at [http://rox.sourceforge.net/phpwiki/index.php/ROX-Filer](http://rox.sourceforge.net/phpwiki/index.php/ROX-Filer) for features.
It's meant to help people who like the fast, handy, flexible Rox filer to have the choice to use it instead of Nautilus. I just wanted to publish my script and give them the choice.

For the rest, it's all a matter of personal taste and perception. 
My subjective perception is: not only Rox filer is fast as hell and uses drag and drop extensively, but it also comes with a lot of handy features and is a full gtk2 application (integrating pretty nicely with gnome desktop), which make you forget the command line for ever. And Nautilus is awkard and takes way too long to open and work with, for an application that should be unobstrusive. 
On slow machines, you really feel the difference, and if Gnome in itself is usable and a slick integrated environment, Nautilus is a real hassle to work with.

The pros I find in Rox filer may be cons to you. It's just like if you asked "why should I use xfce instead of gnome?". Just try it, this is the freedom of choice.

---

### Post by Mr. Electric Wizard on 2005-07-12
[QUOTE=Heliode]Open nautilus -> Edit -> Preferences -> Behaviour -> Select 'Always open in browser'
et voila!

I might have some of the names wrong (since I run Ubuntu in Dutch) but you should be able to figure it out. Also, when you have that, you can set the left panel to 'tree' so you get something that looks like Explorer on Windows.[/QUOTE]


Great, Thanx! :smile: 
I was pretty sure there was a fix for this...

---

### Post by henriquemaia on 2005-07-12
Thanks for this script. I like rox filer :D

---

### Post by tread on 2005-07-13
Thanks for this! I like rox, its a little rough around the edges but the speed makes up for it! And I love the window placement .. I hated how the nautilus window kept jumping about .. never figured out a way to stop that.

---

### Post by craigevil on 2005-08-10
Rox is cool. There are other apps you can use with it. The best thing about it is the fact that is a single process
that uses about 1/4 of the ram that nautilus or konqueror use.

If you have a low resource system or just use a low resource window manager like IceWM or Xfce , Rox is fantastic. You can use it with pinboard to display desktop backgrounds and icons.

If you use the Zero Install method it doesn't install anywhere but in the ~/Apps directory

---

### Post by zielaj on 2005-08-16
Here a some features of rox which I find particularly useful (I haven't used Nautilus much, so maybe it has them as well, I don't know)

1. Rox has good support for both keyboard and mouse operations.  For example, by pressing "/" you open a "location bar" in which you can type the name of the directory you want to see with autocompletion.  Moreover, the directory view in the main window is updated as you type, which is very convenient.

2. Ability to "wink" a file.  When you "wink" /some/path/myfile, it shows you the directory  /some/path and makes myfile blink a couple of times to get your attention.  Very useful when going up in the directory tree (/some/path -> /some); the directory /some is shown and the subdirectory path blinks so that you know where you came from.  Also useful for searches, for example, beagle has an option "reveal in file manager" which shows you the directory in which a given file is located.  With the wink option, the position of the file is immediately obvious, you don't have to search for it, however, this is not implemented in beagle yet.

3. Marking recently modified files and directories using a bold typeface.  If you have a directory with many entries (eg ~/download) to which you have just added a new file, then this feature allows you to see where this new file is immediately

4. Autoscaling windows.  The size and **layout** of the window is automatically chosen depending on the number of files in a particular directory.  In other words, small directories are shown with big icons, whereas big ones are shown with small icons.

---

### Post by Laurent Cazalet on 2005-08-16
Another good point for Rox: Contextual menus according to file type.

In Nautilus, you've got the uniform "Scripts" menu entry, which will show you all the scripts you can use, regardless of the file you right-clicked on. I don't want  to see the "Burn Iso" and "Mount Iso" menu entries when I'm right-clicking on an MP3 file! 

In Rox filer, the user can very easily configure contextual actions for each mime-type.

---

### Post by papangul on 2005-08-28
I don't have a .gnomerc in my home directory, I have a .gtkrc-1.2-gnome2. What to do? The contents of .gtkrc-1.2-gnome2 is:
> include "/home/<myusername>/.gtkrc.mine"

---

### Post by darkmatter on 2005-08-28
Rox has always been my favorite. As an added bonus - no menu bar :grin:

---

### Post by foxy123 on 2005-08-28
just to let you know that rox-filer 2.3 is out. It builds well from source, though you need to install some dependencies...

---

### Post by Laurent Cazalet on 2005-08-28
[QUOTE=papangul]I don't have a .gnomerc in my home directory, I have a .gtkrc-1.2-gnome2. What to do? The contents of .gtkrc-1.2-gnome2 is:[/QUOTE]

They are different files
.gtkrc* are GTK configuration files, for GTK theme selection etc...
.gnomerc is a script executed everytime you login in Gnome.

If you don't find .gnomerc in your home directory, just create it. 
In a terminal, run "gedit $HOME/.gnomerc", edit for your needs, and save.

---

### Post by papangul on 2005-08-28
Thanks for the reply, I created the .gnomerc file in my home directory. The problem is, now rox-filer opens on clicking Trash on the taskbar and "Home Folder" and "Desktop" in the "Places" menu. Nautilus still opens when I click on "Computer" and "Audio Disk" in the "Places" menu and when I click anything on the desktop.

I have "Filesystem", "Home", "Computer", "Audio Disc" and other folders on my desktop. I want rox-filer to open when I click any of them.

---

### Post by Laurent Cazalet on 2005-08-28
[QUOTE=papangul]Thanks for the reply, I created the .gnomerc file in my home directory. The problem is, now rox-filer opens on clicking Trash on the taskbar and "Home Folder" and "Desktop" in the "Places" menu. Nautilus still opens when I click on "Computer" and "Audio Disk" in the "Places" menu and when I click anything on the desktop.

I have "Filesystem", "Home", "Computer", "Audio Disc" and other folders on my desktop. I want rox-filer to open when I click any of them.[/QUOTE]

If you read again the original post, you'll see:

> Opens normally Nautilus if:
...
- click on computer, network servers entries in Places menu
- open network drives from Places menu (if fuse not configured)
...
- Nautilus is configured to draw the desktop and you click on desktop icons (not a feature of the script, though)


Nothing we can do about desktop icons. Desktop icons are created by Nautilus and Nautilus is just calling itself in this case.
Computer and Network are not folders but virtual places. Rox only knows real folders. You can edit the script I posted to get another behavior (open /media when clicking on Computer, for example).

---

### Post by papangul on 2005-08-28
[QUOTE=Laurent Cazalet]If you read again the original post, you'll see:



Nothing we can do about desktop icons. Desktop icons are created by Nautilus and Nautilus is just calling itself in this case.
Computer and Network are not folders but virtual places. Rox only knows real folders. You can edit the script I posted to get another behavior (open /media when clicking on Computer, for example).[/QUOTE]
 If I use idesk or something similar, it might be posible( perhaps some memory will be freed also). I don't know how to repace nautilus with idesk for drawing the desktop. If I somehow manage to do that actually, would the panel at the top and taskbar at the bottom be still there?

---

### Post by Laurent Cazalet on 2005-08-28
[QUOTE=papangul]If I use idesk or something similar, it might be posible( perhaps some memory will be freed also). I don't know how to repace nautilus with idesk for drawing the desktop. If I somehow manage to do that actually, would the panel at the top and taskbar at the bottom be still there?[/QUOTE]
 Never used idesk, but the if the desktop is controlled by Nautilus, the panels are in charge of gnome-panel. So they should remain. 
However, you might want to try the rox pinboard instead.

---

### Post by Wolki on 2005-08-29
[QUOTE=papangul]If I use idesk or something similar, it might be posible( perhaps some memory will be freed also). I don't know how to repace nautilus with idesk for drawing the desktop. If I somehow manage to do that actually, would the panel at the top and taskbar at the bottom be still there?[/QUOTE]

Rox has it's own desktop drawing thing. Just start it with "rox -p default". This will not mess with panels (btw, both the thing on top and on the bottom are called panels, the taskbar is just a little applet that you can put where you want)

To have nautilus stop drawing the desktop you have to change a gconf entry. Forget what it is called, but it's not hard to find, should be somewhere in the /apps/nautilus section.

The Rox pinboard works a little different than many other desktops. It's not a folder but a document, so things you put there are basically just links. This is a pretty clean solution, but you'll have to get used to it.

Rox also has it's own panels, the don't seem to be compatible with Gnome though.

I'm currently quite happy with nautilus and having rox on demand, but I used the complete ROX desktop (Filer+pinboard+panels+session manager+other apps+window manager (sometimes)) for a long time; so if you have questions I might be able to help.

---

### Post by mweierophinney on 2005-09-27
[QUOTE=bored2k]I know rox is faster than the speed of light, but, I'm also curious (i never used rox.. just a bit).

Why should I use it instead of the beloved nautilus ? Why is it so much better ?[/QUOTE]

I've been using rox for years, and typically without gnome at all; ubuntu is my first re-visit to gnome in almost 3 years. 

I like nautilus, but there's two key things that drive me crazy: (1) no ability to spring open the 'Open with...' menu without the mouse, and (2) no ability to change they keybindings. ROX allows both of these (actually, the 'Open with' menu is called 'Send To...' in rox, and you can spring it open with a keybinding... which you can configure).

These two things in rox allow me to navigate through a series of windows using only the keyboard, and do things such as choosing what program to open a file in, opening a group of files using the same command, opening an xterm at the current directory, opening new windows, and using a shell-completion entry to navigate to other directories. It combines the best of both the shell and a GUI, to my thinking.

With the HOWTO in this thread, I now can have items appear on the desktop without my intervention -- making it that much cooler.

---

### Post by qscomputing on 2007-06-14
For those of you wanting to use this technique, this I what I tried and works for me:

The script works as-is, though I made a couple of changes to make it work even better:

```
# calls the replacement, only arg must be an existing dir
function run_replacement() {
    [ $DEBUG != 0 ] && echo "OUT: Running $NAUTILUS_REPLACEMENT. Args: '$@'" >> $HOME/nautilus_wrapper.log
    exec $NAUTILUS_REPLACEMENT **"$@"**
}
```

The quotes are added in the last line to workaround a bug which occurs when there are spaces in the directory we want to open - ROX will look at each word as a seperate path to open.

```
        -q|--quit) run_nautilus;;
	**computer:) run_replacement "/media/";;**
        computer*) run_nautilus;;
```

This goes in the case statement; the line added (bold) causes /media/ to be opened when you select Places->Computer.

I haven't tried using gnomevfs-mount yet. If you use the links posted earlier in this thread, you'll find that they're dead, but as of 2007-07-14 the source for gnomevfs-mount is available in the Internet Archive: [http://web.archive.org/web/20051102071704/http://primates.ximian.com/~sandino/gnomevfs-mount/](http://web.archive.org/web/20051102071704/http://primates.ximian.com/~sandino/gnomevfs-mount/)

Hope someone finds this useful, but remember that your mileage may vary,
  - QS.

---

### Post by gaiterin on 2007-07-09
Hi.
How can replace ONLY (the Nautilus by Rox) in the "Places" menu?
I don't like change in more sites of the system.
I don't like replacement Nautilus in all system. ONLY when I click from Places menu.
Thanks.
Marcos.

---

### Post by afrodeity on 2010-04-18
I see this is a rather old thread, but an extremely interesting topic. Always thought roxfiler was a lot faster and when included with zeroconf packaging system, a real winner. Any thoughts about doing this with latest editions, 2010 lucid and karmic...

---

### Post by Mark76 on 2010-07-13
How do I reverse the change?

---

### Post by hanzf on 2010-12-10
I know rox from Puppy Linux and what other file manager can  create links with drag&drop, work on single click, handle  different "open with" menus for every file type and auto-size its window  to fit the contents... who wants more?
So first thank you for this howto. Rox is now my default file manager.
> **Wolki said:**
> Rox has it's own desktop drawing thing. Just start it with "rox -p default".
 Here I get the following error message:
```
hans@Hans-sein-Rechner:~$ rox -p default
 hans@Hans-sein-Rechner:~$ The program 'rox' received an X Window System error.
 This probably reflects a bug in the program.
 The error was 'BadAtom (invalid Atom parameter)'.
   (Details: serial 524 error_code 5 request_code 20 minor_code 0)
   (Note to programmers: normally, X errors are reported asynchronously;
    that is, you will receive the error a while after causing it.
    To debug your program, run it with the --sync command line
    option to change this behavior. You can then get a meaningful
    backtrace from your debugger if you break on the gdk_x_error() function.)
```the program keeps on running but the desktop backround is still dead. Any idea what this could be, and how to fix it?
[/QUOTE]
> **Wolki said:**
> 
To have nautilus stop drawing the desktop you have to change a gconf  entry. Forget what it is called, but it's not hard to find, should be  somewhere in the /apps/nautilus section.
In "gconf-editor", it is "apps/nautilus/preferences/show_desktop".

---

### Post by hanzf on 2010-12-10
PS. I just found out this "X Window System Error" thing is a bug in rox 2.5. I updated to 2.10, from here:
[http://packages.ubuntu.com/de/maverick/rox-filer](http://packages.ubuntu.com/de/maverick/rox-filer)
now rox also makes the desktop. Still some fine tuning to do....

---

### Post by hanzf on 2010-12-10
last question for this time...
> **Wolki said:**
> ...but I used the complete ROX desktop (Filer+pinboard+panels+session manager+other apps+window manager (sometimes)) for a long time; so if you have questions I might be able to help.
Whenever I put in, say, a CD, or a USB flash drive, or any removable media, nautilus will still open on that media.
Instead, I would like a CD (or flash drive, or whatever...) icon to appear on the desktop when the media is put in, and clicking this icon would mount the media and open rox on it, and when the media is removed the icon would disappear.
I know this is possible because Puppy Linux (I had Version 4.2.1) does so. These icons also had a different context menu offering "unmount" and some other special options I don't remember ;)
How does that work?

---

### Post by LewRockwellFAN on 2011-01-07
Thanks for this. I found this thread by googling for ways to set Thunar as default. Now I'll have to have a look at Rox first.

@ those who ask "Why bother?", for me the main answer is that Nautilus has a horrible memory leak that slows my system to a crawl and crashes aps. Thunar is also much faster than Nautilus even when Nautilus isn't being naughty.

---

