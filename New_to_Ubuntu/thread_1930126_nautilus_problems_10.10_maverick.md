---
title: "nautilus problems 10.10 maverick"
date: 2012-02-23
forum: New to Ubuntu
---

### Post by okkie on 2012-02-23
collected 2800 photos overseas,downloaded on computer to make cd/dvd
1 computer cannot read blank dvd
2 home folder only gives f-spot,nothing else
3 did gksudo nautilus and got results as per attached screenshot
Please help me to rectify

---

### Post by jtarin on 2012-02-23
Try just the command **nautilus** w/out gksudo. If errors take a shot of terminal and post.
What are you using to burn the CD? I like GnomeBaker.

---

### Post by okkie on 2012-03-01
sorry I only come back now , my internet connection was interrupted.
Nautilus gives me exactly what I need but does not solve the problem.
\I go places home folder and F-Spot opens up.That is also the last program I used before the problem started.Is there not a code Ican use to rectify this and if you perhaps know what causes it and how can it be permanently rectified.These little things are also stopping me from upgrading as over the years I have never really had a properly working system.Thanks.
By the way I use K3B most of the time to stop BRASERO interfering all the time .

---

### Post by Krytarik on 2012-03-01
> **okkie said:**
> I go places home folder and F-Spot opens up.
Open the file "~/.local/share/applications/mimeapps.list", and make sure the entry for "inode/directory" looks like this:
```
inode/directory=nautilus-folder-handler.desktop;
```Here is a good explanation of what may have caused it, and how to prevent that in future:

[http://ubuntuforums.org/showthread.php?t=1675491](http://ubuntuforums.org/showthread.php?t=1675491)

Notice, however, that the concerning option, and possible cause of your issue, isn't included in the "Open With -> Other Application" dialog anymore, at least in Nautilus - on an updated system!

Regards.

---

### Post by okkie on 2012-03-01
~/.local/share/applications/mimeapps.list

I seem to have a permissions problem as well.Trying to open the above it says permission denied.

---

### Post by Krytarik on 2012-03-01
> **okkie said:**
> ~/.local/share/applications/mimeapps.list

I seem to have a permissions problem as well.Trying to open the above it says permission denied.
Don't *run* it as a command; it's a file! ;-) Open it with the text editor, or from Nautilus. It's in your home directory (indicated by the "~"), and hidden (indicated by the preceding "."); so in both the Open dialog and Nautilus, you need to press Ctrl+H to see the hidden files/directories. Additionally, also check "defaults.list" in the same directory, just to be sure, although it's completely empty on my Lucid 10.04.

---

### Post by okkie on 2012-03-02
Firstly,my lifelong friend with plenty computer experience and who got me involved in Ubuntu and was as kind as you, died 3 months ago leaving me in a way, half lost.I appreciate your time tremendously and ask you to please bear with me if I seem to be slow to understand but at 65 things are just not what they used to be.However;

I run nautilus in terminal and everything comes up as normal.Home folder is there but has no contents whatsoever.Must be another one of my miracles.

The file you told me to not run, but open,where do I find it and with what do I open it ?

thanks

---

### Post by Krytarik on 2012-03-02
Sorry for the late response; I slept a 'little bit' longer than expected. :P

> **okkie said:**
> The file you told me to not run, but open,where do I find it and with what do I open it ?
For the GUI text editor method, I'll just bold-mark the applying, basic stuff from my previous post:
> **Krytarik said:**
> **Open it with the text editor**, or from Nautilus. **It's in your home directory** (indicated by the "~"), **and hidden** (indicated by the preceding "."); **so in both the Open dialog** and Nautilus, **you need to press Ctrl+H to see the hidden files/directories**. Additionally, **also check "defaults.list" in the same directory**, just to be sure, although it's completely empty on my Lucid 10.04.

For the CLI clean-sweep method, just run both of these commands; this simply removes any entries for that MIME type from both the concerning files, thus reverting it to the default:
```
sed -i '/inode\/directory/d' ~/.local/share/applications/mimeapps.list
sed -i '/inode\/directory/d' ~/.local/share/applications/defaults.list
```

---

### Post by okkie on 2012-03-03
Thanks again.I just ran the two lines in terminal and places menu back to normal.






                     ** THIS THREAD IS CLOSED**

---

