---
title: "HOWTO:  Quickly Open a Terminal From Nautilus"
date: 2005-04-13
forum: Outdated Tutorials &amp; Tips
---

### Post by bobmitch on 2005-04-13
This has probably been covered before, but I couldn`t see it anywhere...

Anyway, this is a quick method of dropping to a terminal from nautilus, which automatically changes directory to wherever you were browsing with nautilus. (For any local location - won`t work with ftp or other esoteric locations).

Big thanks to the guys in the Drag and Drop To Run As Root HOWTO [thread](http://www.ubuntuforums.org/showthread.php?t=24008&highlight=open+root)  for showing me how this could be achieved.

[CENTER]**HOWTO:  Quickly Open a Terminal From Nautilus**[/CENTER] 

[list]
[*]Open a Terminal
[*]Type:
```
cd ~/.gnome2/nautilus-scripts
```
[*]Type:
```
gedit Open\ Terminal\ Here
```
[*]Paste the following code into the file:
```
#!/bin/sh
# From Chris Picton
# Replaces a Script by Martin Enlund
# Modified to work with spaces in path by Christophe Combelles

# This script either opens in the current directory, 
# or in the selected directory

base="`echo $NAUTILUS_SCRIPT_CURRENT_URI | cut -d'/' -f3- | sed 's/%20/ /g'`"
if [ -z "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" ]; then
     dir="$base"
else 
     while [ ! -z "$1" -a ! -d "$base/$1" ]; do shift; done
     dir="$base/$1"
fi

gnome-terminal --working-directory="$dir"
```
[*]Save the gedit file, and quit.
[*]Back in the terminal type:
```
chmod +x Open\ Terminal\ Here
```
[/list] 

et voila.... 

In any nautilus window, you can right click, and from the **scripts** sub-context-menu, click on **Open Terminal Here** to open a terminal at the currently viewed directory.

[EDIT]  You can now highlight a folder and perform the operation to open a terminal at the location highlighted.

Hope somebody besides me finds this useful - the lack of this option has driven me batty since my foray into linux. :)

---

### Post by jonny on 2005-04-13
Works perfectly.  You just got rid of the last advantage KDE has over Gnome.

---

### Post by frühstück on 2005-04-13
good idea

---

### Post by luca_linux on 2005-04-13
[QUOTE=jonny]Works perfectly.  You just got rid of the last advantage KDE has over Gnome.[/QUOTE]
 Yeah, Gnome rulez!

---

### Post by Spudgun on 2005-04-13
Good stuff  :grin:

---

### Post by shakin on 2005-04-13
Great how-to. I didn't realize how useful this was until I tried it and now I can't live without it!

Do you know if there is a manual to see what variables are available? For instance, there is $NAUTILUS_SCRIPT_CURRENT_URI and $NAUTILUS_SCRIPT_SELECTED_URIS. Any more? I bet a lot of useful scripts can be made. In fact, I'm going to make a couple right now and do how tos if they work well.

---

### Post by bobmitch on 2005-04-13
[QUOTE=shakin]Great how-to. I didn't realize how useful this was until I tried it and now I can't live without it!

Do you know if there is a manual to see what variables are available? For instance, there is $NAUTILUS_SCRIPT_CURRENT_URI and $NAUTILUS_SCRIPT_SELECTED_URIS. Any more? I bet a lot of useful scripts can be made. In fact, I'm going to make a couple right now and do how tos if they work well.[/QUOTE]

The quick answer to your question is "Yes".

The long answer is taken from the "About Scripts" dialog:

> When executed from a local folder, scripts will be passed the selected file names. When executed from a remote folder (e.g. a folder showing web or ftp content), scripts will be passed no parameters.

In all cases, the following environment variables will be set by Nautilus, which the scripts may use:

NAUTILUS_SCRIPT_SELECTED_FILE_PATHS: newline-delimited paths for selected files (only if local)

NAUTILUS_SCRIPT_SELECTED_URIS: newline-delimited URIs for selected files

NAUTILUS_SCRIPT_CURRENT_URI: URI for current location

NAUTILUS_SCRIPT_WINDOW_GEOMETRY: position and size of current window 

There's tons of useful things which can be done with this - the terminal launcher is the only one I could think of that was bothering me enough to make me implement something though. :D

I look forward to seeing anything you come up with. :)

---

### Post by shakin on 2005-04-13
[QUOTE=shakin]Great how-to. I didn't realize how useful this was until I tried it and now I can't live without it!

Do you know if there is a manual to see what variables are available? For instance, there is $NAUTILUS_SCRIPT_CURRENT_URI and $NAUTILUS_SCRIPT_SELECTED_URIS. Any more? I bet a lot of useful scripts can be made. In fact, I'm going to make a couple right now and do how tos if they work well.[/QUOTE]

To answer my own question, here are the available variables:


NAUTILUS_SCRIPT_SELECTED_FILE_PATHS:
    newline-delimited paths for selected files (only if local)
NAUTILUS_SCRIPT_SELECTED_URIS:
    newline-delimited URIs for selected files
NAUTILUS_SCRIPT_CURRENT_URI:
    current location
NAUTILUS_SCRIPT_WINDOW_GEOMETRY
    position and size of current window 

You can also use the gdialog application if your script needs user input.

--

dupe post. I spent too long browsing other scripts :)

---

### Post by bobmitch on 2005-04-13
After some browsing, I came across a [perl version](http://g-scripts.sourceforge.net/nautilus-scripts/Execute/Open%20Terminal%20Here) of my script.  Lol.

---

### Post by Remix_88 on 2005-04-13
Take a look at G-Scripts :-)

[http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)

---

### Post by bobmitch on 2005-04-13
[QUOTE=Remix_88]Take a look at G-Scripts :-)

[http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)[/QUOTE]


Just been there, found a better bash script to use and updated my howto. :D

Nothing like re-inventing the wheel, eh? :D

---

### Post by XDevHald on 2005-04-13
To make myself look like a n00b, I can't find my gnome2 folder, looked for 15 mins and still can't find it, I even have my Show Hidden Files selected.

---

### Post by shakin on 2005-04-13
[QUOTE=Remix_88]Take a look at G-Scripts :-)

[http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)[/QUOTE]

Yeah, when I found that I realized most of my ideas for scripts were already there. I'm still planning on making two file transfer scripts -- one for ftp and one for scp -- that ask for server and remote directory name using gdialog. Right now I'm having a bit of difficulty getting gdialog to do what I want.

---

### Post by Nis on 2005-04-13
[QUOTE=Doc]To make myself look like a n00b, I can't find my gnome2 folder, looked for 15 mins and still can't find it, I even have my Show Hidden Files selected.[/QUOTE]
 Should be in ~/.gnome2

If you want to quickly get to the nautilus-scripts directory click on your desktop, press 'Ctrl+L', and put '~/.gnome2/nautilus-scripts/' into the dialog.

---

### Post by bobmitch on 2005-04-13
[QUOTE=shakin]Yeah, when I found that I realized most of my ideas for scripts were already there. I'm still planning on making two file transfer scripts -- one for ftp and one for scp -- that ask for server and remote directory name using gdialog. Right now I'm having a bit of difficulty getting gdialog to do what I want.[/QUOTE]

You might have more joy with **zenity** than gdialog?

---

### Post by Nis on 2005-04-13
[QUOTE=bobmitch]You might have more joy with **zenity** than gdialog?[/QUOTE]
 zenity rocks.  Much easier than gdialog.  You can now even do notification icons with zenity.

---

### Post by minio on 2005-04-13
There is an other way. You can install python-nautilus (not sure in which repository it is) and then copy open-terminal.py from /usr/share/doc/python-nautilus/examples/ to /usr/lib/nautilus/extensions-1.0/python/ . Restart nautilus and you will get Open terminal entry in right click menu.

---

### Post by XDevHald on 2005-04-13
VERY impressive! and thank you for the help there Nis, much appreciated :grin:

---

### Post by Gandalf on 2005-04-13
nice tick...... thanks

---

### Post by thepoch on 2005-04-17
[QUOTE=bobmitch]After some browsing, I came across a [perl version](http://g-scripts.sourceforge.net/nautilus-scripts/Execute/Open%20Terminal%20Here) of my script.  Lol.[/QUOTE]

Hehe, you found the one I modified. I would have written it as a bash script, but since I found that, I just fixed that (adding the 'opening on desktop' feature). I guess my 'fix' might no longer be needed in latter gnomes (never bothered hacking it again), but it still works for me since 2003.

 :)

---

### Post by Sionide on 2005-05-24
Well done, very very useful... I've always thought about the need for this.

---

### Post by bored2k on 2005-06-01
Very useful. Thanks:D.

---

### Post by Basotang on 2007-07-28
Hi,

I just followed that:
> There is an other way. You can install python-nautilus (not sure in which repository it is) and then copy open-terminal.py from /usr/share/doc/python-nautilus/examples/ to /usr/lib/nautilus/extensions-1.0/python/ . Restart nautilus and you will get Open terminal entry in right click menu.

I now have a Open Terminal entry in the right click menu but nothing happens. Any idea why?

Thanks a lot in advance!

Seb.

---

### Post by Basotang on 2007-07-29
Replying to my own message, login out and in again made the Open Terminal work.

Seb.

---

### Post by Samhain13 on 2007-07-29
Hello. I have been lurking in these forums but have not posted much.
I guess now I can just say **"Thanks"** for this handy script, which I need.
Cheers! :)

---

### Post by jpyanowski on 2007-07-29
I want to add my thanks for this how-to. It makes using the terminal with nautilus so much easier. :)

---

### Post by mcduck on 2007-07-30
What's the difference between this solution and the entry you get if you install 'nautilus-open-terminal' from repositories?

That one adds 'Open Terminal' to desktop right-click menu and 'Open Terminal Here' to Nautilus right-click menu..

Just run this, log out & back (or 'killall nautilus')
```
sudo apt-get install nautilus-open-terminal
```

---

### Post by Tuan Tran on 2007-07-30
i must be retarded but where is the sub context menu :S tried right clicking everywhere lol...

---

### Post by Tuan Tran on 2007-07-30
sry about that. i clt+alt+ backspace and logged back in and it worked. lol thx guys ! this is really handy for installing things. (unzip by the manager. browse it. open in terminal. ./configure and so on....)

---

