---
title: "[SOLVED] How to change an icon using script"
date: 2007-11-26
forum: Programming Talk
---

### Post by mdpalow on 2007-11-26
Hi everyone,

I changed a file's icon using gnome (properties) and wondered how you would do that in a terminal or shell script.

Can't find anything on it...

Can anyone help?

Thanks..

---

### Post by mdpalow on 2007-11-26
anyone?

bump.

---

### Post by macaholic on 2007-11-26
> **macaholic said:**
> The easiest way is to just right-click on the launcher and go to properties and change it by clicking on the icon. Now this only changes it for that particular launcher. The harder, but more thorough way (will change all instances of that icon), is to go to a launcher, click on the icon again, note the location of the icon. For example the loaction of the firefox icon is /usr/share/pixmaps/firefox.png.
Now, all you do is put the new icon you want on your desktop. name it so that it is the same as the icon you are replacing, and do
```
sudo cp ~/Desktop/<icon_name>/path/to/file
```
For firefox it would look something like this:
```
sudo cp ~/Desktop/firefox.png /usr/share/pixmaps/firefox.png
```
for evolution it would look something like
```
sudo cp ~/Desktop/evoltion.png /usr/share/icons/hicolor/scalable/apps/evolution.svg 
```
Things to note:
This will change if you have a different icon theme set other then GNOME, also depending on the name of the icon you are trying to replace it with, the file extension will change. Generally [svgs]("http://en.wikipedia.org/wiki/Svg") are the best choice for icons, but hi-res pngs work well also.
That was me telling someone else how to solve a similar issue. Hope that helped :)

---

### Post by mdpalow on 2007-11-26
thanks for the detailed answer.

The problem is that I want to change the icon of a sh script that is sitting on my Dektop and I don't want to change the icon for all text files, but just this one.

I realize it can be done by going to properties, but I need to do this in a script or from the terminal.

Do you know how to do that as well by any chance?

Thanks in advance...

---

### Post by PaulFr on 2007-11-27
AFAIK, the icon is picked up from the value of the **Icon=** entry in the <application_name>.desktop file in the Desktop directory.

Changing this via your script to an icon name (if the icon is part of the system icons) or a path to an icon file should change the icon displayed appropriately.

---

### Post by mdpalow on 2007-11-27
Hi Paul,

After reading your reply, I think I might have poorly stated what I want to do in my title.

I have a script sitting on my desktop. It has a folder in my /home/$USER directory where I have some help files. I have a script that uncompresses these files and puts everything where it should be. I'd like to add to this install script a little snippet that would also change the icon of the main script.

I know I can go into properties and change it there, but I need to know how to change it in a script, so when someone runs the installer, it puts everything in place and then changes the icon based on an icon file that is on the system already.

Do you know how this is done...?

Thanks and sorry for the confusion..

---

### Post by geirha on 2007-11-27
Obviously, a script can't contain an icon, so there's metadata involved. Nautilus creates metadata xml-files for each directory in ~/.nautilus/metafiles. You'll find the one for the desktop as ```
file:%2F%2F%2Fhome%2F**username**%2FDesktop.xml
``` (Having / characters in filenames is possible, but complicates things, so %2F is used instead)

In that xml-file you should find an entry for your script like: ```
<file name="test.sh" timestamp="1196172522" icon_position="220,22" custom_icon="file:///usr/share/pixmaps/baobab.xpm"/>
```

I would recommend you use launcher instead as it's easier to manipulate with a shell-script.

---

### Post by mdpalow on 2007-11-28
Hi geirha,

Thanks for the post. I didn't get a message you had replied or I would have responded sooner.

This is what I was looking for. However, you've got me thinking now about Launchers since you say they are easier to work with. Today, I was actually looking for the Launcher info on one I made, but no luck. Can you tell me - if I make a launcher, where is the file located that get updated with the new launcher info?

Thanks very much for your prior post, I'm gonna work with that until I hear something back from you or someone else about the launcher stuff..

Good night

Edit: I see why it's harder to work with in the .xml file as it is given a timestamp, which isn't a huge problem, but if/when you move the file (.sh),  it loses its icon. I'd like to see what you/anyone says about Launchers. Finally, I feel like I'm getting closer to resolving this. :) thanks...

---

### Post by geirha on 2007-11-28
Well, let's say the script is saved as ~/test.sh, rightclick the desktop and choose create launcher,

Type: Application
Name: test
Command: ~/test.sh
Change the icon to something

now, if you look in ~/Desktop, there should be a file test.desktop that looks something like:
```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=test
Type=Application
Terminal=false
Exec=~/test.sh
Icon=/usr/share/pixmaps/nohost.png
```

---

### Post by mdpalow on 2007-11-28
geirha

Thank you very much for this. Great answer. This is EXACTLY what I was looking for to do what I want.

---

