---
title: "Too big System-Fonts because of Nvidia Driver"
date: 2016-09-10
forum: New to Ubuntu
---

### Post by tobias33 on 2016-09-10
Hi,

as a newbee I struggle quite a bit to get Lubuntu running on my rather old IBM ThinkPad (2007) with Nvidia Graphic Chip. The main problem: When I use the Nvidia Driver for my Graphics Card, the Fonts throughout the system get way too big. In Ubuntu Mate I solved the problem with changing the Font-DPI to 96 in the system preferences. Unfortunately, in Lubuntu, which I have to use because Mate was too much of a resource hog on my old Hardware, there is no such Option in the System Preferences.

Solutions via [Terminal]("http://www.techytalk.info/lubuntu-change-fonts-dpi-when-using-proprietary-nvidia-driver/") are a bit too complicated for me, I guess, as I can't get things running that way. Any idea how I could solve the big-font-issue?


Thanks in advance 

By the way: I don't find any possibilty in the System Preferences to choose a different soundcard.

---

### Post by oldrocker99 on 2016-09-10
It's not that complicated, really. Open a terminal and type```
sudo nvidia-xconfig --no-use-edid-dpi

```

Then type```
cd /etc/X11/
sudo nano xorg.conf
```

Look under "Monitor" and find this line:```
Option "DPI" "96 x 96"

```

Change the line to "48x48" and log out. When you log back in again, the fonts should be at a more reasonable size. Repeat with a smaller size if necessary.

Good luck!

---

### Post by tobias33 on 2016-09-10
Thanks for the reply. Unfortunately "[COLOR=#000000][FONT=&quot]Option "DPI" "96 x 96"" isn't there ([I made a screenshot]("https://www.dropbox.com/s/3pnj4v7635viivc/2016-09-10-234103_1680x1050_scrot.png?dl=0")). Anyway, I don't even know how to edit the file. The key-index at the bottom doesn't help because I don't know how to apply the commands. [/FONT][/COLOR]

---

### Post by howefield on 2016-09-11
> **tobias33 said:**
> Thanks for the reply. Unfortunately "Option "DPI" "96 x 96"" isn't there I made a screenshot. Anyway, I don't even know how to edit the file. The key-index at the bottom doesn't help because I don't know how to apply the commands.

With nano cursor down to the relevant section and add on a new line in the monitor section the line oldrocker99 has suggested. Ctrl + O keys to save the file, press enter and then Ctrl + X keys to close out of it.

Might be easier to use the leafpad text editor..

```
sudo -H leafpad /etc/X11/xorg.conf
```

to edit the file in a "GUI"

---

