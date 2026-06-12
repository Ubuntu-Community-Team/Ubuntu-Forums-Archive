---
title: "New User/Questions"
date: 2012-02-20
forum: New to Ubuntu
---

### Post by Sagimore on 2012-02-20
I just updated my machine to 11.10 last night, I was hoping it would fix an issue im having with Calibre. Calibre is not working with my nook tablet. There is no "Send to Device" option.

Im not sure this is the correct location to ask, but how can I tell if im running the correct version of calibre inside Ubunto. And if im not how to update. Im not even sure the program is stable with this OS.

If anyone has link to understanding all the lingo and how the OS is updated, where things are stored etc please post the link in reply. All the different version names are confusing the hell out of me. Vine, oneeiricocelot, GNOME etc. Very noobish here, but are a lot of the names simply for add ons for launchers etc?

---

### Post by oldos2er on 2012-02-20
Calibre works fine for me in 11.10, but I'm using it with a Kindle, not a Nook. If you plug your Nook in, Ubuntu should automount it. If that's not happening, maybe try a different USB port? 

You can upgrade to the latest version of Calibre by running this command in a terminal (to open a terminal, use Ctrl-Alt-t): 
```
sudo python -c "import sys; py3 = sys.version_info[0] > 2; u = __import__('urllib.request' if py3 else 'urllib', fromlist=1); exec(u.urlopen('http://status.calibre-ebook.com/linux_installer').read()); main()"
```

It will install to /opt/calibre if you accept the defaults. More info here:
 [http://calibre-ebook.com/download_linux](http://calibre-ebook.com/download_linux)

Not sure what "Vine" is, did you mean Wine?

GNOME is a desktop environment, one of many. [http://en.wikipedia.org/wiki/GNOME](http://en.wikipedia.org/wiki/GNOME)

Oneiric Ocelot is the name given to Ubuntu 11.10. Every Ubuntu version has an 
animal name in the form of Adjective Noun. Don't ask me why.

---

### Post by Lisiano on 2012-02-20
@oldos2er "Vine" might refer to Vino or Vinagre. Although apt-cache also says there is a "vinetto - A forensics tool to examine Thumbs.db files", doubt that would be it though.


@Sagimore
Generally Ubuntu will prompt you whenever there is an update. You can issue a manual update if you wish. There are multiple ways, first I'll explain the GUI (Graphical User Interface) way, since it's easier.
To update using GUI tools, open Dash (Or Dashboard) by pressing the Super key (Also called Windows key by people who came from Windows) or pressing the Ubuntu logo on the top left corner, then searching for Update Manager, another way is to press Alt+F2 and type ```
update-manager
``` then enter. From there you first do a Check to see what updates are available then Update.

The CLI (Command Line Interface) way is a both easier and harder, easier since if you can remember the command name, you can do it faster and harder since you need to first become used to a terminal. To start, open up a terminal in Dash the same way we opened Update Manager, or in Alt+F2 and typing ```
gnome-terminal
``` or simply pressing Ctrl+Alt+T. Then typing this to "Check" for updates ```
sudo apt-get update
```sudo - Perform action as root/superuser/administrator
apt-get - For now, our package manager
update - command to apt-get to update the update list.
It will ask for a password, it's your user password, when you type it it won't be visible, don't be alarmed, it's still being typed in, just press enter when you typed it.
You will see a lot of text fly by and soon get back to a line that looks like this```
username@pcname:~$
```username - your username
pcname - your PC's name

After that, you just type this and the system will show you what updates are available
```
sudo apt-get upgrade
```
If you like what you see, just press Enter and it will update, if you don't, type N and press Enter or hit Ctrl+C.

Now for the lingo you asked:
Vine - I don't know what you mean by it, if Wine then it's some software that let's you run Windows programs, if Vino then it's a VNC server, if Vinagre the it's a VNC client.
Oneiric Ocelot - It's Ubuntu 11.10 codename, 11 is the year and 10 is the month of release
GNOME - This is a desktop environment.

---

### Post by Sagimore on 2012-02-20
Thanks guys, yes I meant wine..Ive been playing in for a few hours now, and love it.

And yes the calibre update worked, Calibre now sees the device. Thanks a ton:P

---

