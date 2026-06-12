---
title: "HOWTO: Have All Your Windows Fonts in Ubuntu."
date: 2005-12-21
forum: Outdated Tutorials &amp; Tips
---

### Post by Rev. Nathan on 2005-12-21
Well, I had a giant tutorial going, but my computer crashed. So instead of making a giant tutorial explaining everything step-by-step, breaking down each action and command, I'm just going to post the bare minimum. Maybe later I'll edit it (or someone else), but until then, following this tutorial blindly should also work.

This is a tutorial teaching you how to retrieve all your fonts from your Windows partition, and having them in Ubuntu. It's pretty simple and quick, and you'll have all your favorite fonts! Hurray for Wingdings! :D

First, you need to **mount your Windows partition** (skip these steps you are already mounted). You should know if you've mounted this or not; if you can access your files from your Windows partition by clicking an icon on your desktop, you are in business. If not, open up Terminal and type in the following:

> sudo mkdir /media/windows

This action will ask for a password, type it in. Once done, a new folder called 'windows' will be located at Places --> Computer --> Filesystem --> media.

> sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
All this gibberish means that your windows partition is now mounted in /media/windows.

Next, we [B]move our fonts from windows to ubuntu.
[SIZE="3"]
Start here if your windows partition is already mounted![/SIZE][/B]

Because people may have already mounted windows and placed it under a different name, we are going to copy and paste the fonts from windows in Ubuntu, rather than just grab them from windows directly.

So, go to Places --> windows (below 'Computer') --> WINDOWS --> Fonts

And your fonts are right there! Press Ctrl+A to select them all, and then Ctrl+C to copy them.

Now, go to your desktop, right click and make a new folder called 'fonts'. Open the folder, and press Ctrl+V to paste the fonts in there.

Open up Terminal (if you closed it), and type in

> cd Desktop/fonts

This will change the working directory to the directory you just made. Next,

> sudo cp *.ttf *.TTF /usr/share/fonts/truetype/msttcorefonts/

This copies the folder's fonts to ubuntu's font list.

Your done! Go to System --> Preferences --> Font and check 'em!

You may now delete the fonts folder you made on your desktop; no longer needed.

Bonus: You may also need to rebuild your font cache, I do not know if this is needed.

> sudo fc-cache -f -v
Resources:
[Tahoma Font in Ubuntu](http://ubuntuforums.org/showthread.php?t=82318)
[www.ubuntuguide.org](www.ubuntuguide.org)
The ubuntu wiki

---

### Post by onesojourner on 2006-01-10
this is great. for some reason it had never crossed my mind that I could use my windows fonts. I actually don't have a folder called msttcorefonts so I copied them to  usr/share/fonts/truetype. worked fine that way.

---

### Post by galgoz on 2006-01-11
when I type 

 sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

I get the error 

mount: special device /dev/hda1 does not exist

any tips?

---

### Post by meborc on 2006-01-11
**sudo fdisk -l**

then check if hda1 is the drive your windows ntfs partition is situated... if not, then change the code to hda2 or whatever

EDIT: ... but i don't know about the legal issues concerning copying ms fonts like this... :rolleyes:

---

### Post by Chris Tucker on 2006-01-11
it depends on your partition order, replace hda1 with your windows partition (try the app cfdisk to find out whats where)

---

### Post by galgoz on 2006-01-11
Found out the issue, it was sda1 as it is a sata drive.

---

### Post by audax321 on 2006-01-12
Also, if you don't want to install the fonts system-wide, you can install them for a specific user by changing:

```
 sudo cp *.ttf *.TTF /usr/share/fonts/truetype/msttcorefonts/
```

to

```
 
mkdir /home/<USERNAME>/.fonts
cp *.ttf *.TTF /home/<USERNAME>/.fonts

```

Then just rebuilt the font-cache as mentioned above. :)

---

### Post by souled on 2006-01-12
Thanks for this howto! Does Ubuntu support the fonts with the .fon extension also?

---

### Post by onesojourner on 2006-01-12
[QUOTE=souled]Thanks for this howto! Does Ubuntu support the fonts with the .fon extension also?[/QUOTE]

I would like to know that too.

---

### Post by mathieujohnson on 2006-01-14
would this trick work for downloadable fonts?
Its been more than 6 months that I don't have a windows install so no fonts to get but getting some fonts from the net is a possible solution.
would it work in the same way?

---

### Post by DimaIL on 2006-01-14
nice! thanks!
I have a question: Why do i need to open a terminal for just copy some fonts? Why i can't do this with copy-paste?

Thanks again!
Dima.

---

### Post by kosmic on 2006-01-14
You can do copy paste if you run Nautilus as Root

---

### Post by hubbadub on 2006-01-18
Wow, awesome tutorial, thanks!

---

### Post by Ruskie on 2006-01-18
[QUOTE=mathieujohnson]would this trick work for downloadable fonts?
Its been more than 6 months that I don't have a windows install so no fonts to get but getting some fonts from the net is a possible solution.
would it work in the same way?[/QUOTE]

Sure, the point is: copy any font you want to use into that directory and rebuild the cache. :)

---

### Post by DimaIL on 2006-01-18
[QUOTE=kosmic]You can do copy paste if you run Nautilus as Root[/QUOTE]
And How can i do it?

Thanks
Dima

---

### Post by Rev. Nathan on 2006-01-19
[QUOTE=DimaIL]And How can i do it?

Thanks
Dima[/QUOTE]
You can go to Applications --> System Tools --> Log In As Diffrent User, and do it from there. However, Automatix (see sticky at the top of this forum) comes with a script when you are right click any folder you are in and make it the root user browsing that folder, which is faster. As chose to just give the tutorial in the terminal as to not make someone so lost.

---

### Post by Rev. Nathan on 2006-01-19
[QUOTE=mathieujohnson]would this trick work for downloadable fonts?
Its been more than 6 months that I don't have a windows install so no fonts to get but getting some fonts from the net is a possible solution.
would it work in the same way?[/QUOTE]
Yes, I would safely assume that any .tff (whether capitalized or not) would work in Ubuntu. Also, gnome-look.org has a file called 6,760 fonts, if you just want to splurge.

[Link](http://www.gnome-look.org/content/show.php?content=9883)

A comment advises that it slows down the KDE start up, however... if you are using Kubuntu.

---

### Post by Rev. Nathan on 2006-01-19
[QUOTE=souled]Thanks for this howto! Does Ubuntu support the fonts with the .fon extension also?[/QUOTE]
I don't think it would hurt just to throw a .fon into the folder to see if it works. If it crashes you fonts or X or something, you can switch to another terminal (alt+F2, for example, the GUI is located on Alt+F7) and type:

sudo nano /usr/share/fonts/truetype/msttcorefonts/fontfilename.fon

Or whereever in the font folder you installed it, and whatever the name of the .fon file is. Also, I found this while looking for you answer on Google: [Link](http://ubuntuforums.org/showthread.php?t=7135). It appears that someone made a nifty script that converts .fon to .bdf fonts? Which are compatible with Ubuntu? Maybe you want to try this one, first.

I'm sorry, I'm actually a newbie myself. I just made this tutorial from logic I had acertained from reading and re-reading font guides, and using common-logic as to how I could just get something from Windows onto Linux. You could use the same logic to, say, get all you wallpapers onto Linux. Or your documents.

---

### Post by jmcwb on 2006-01-19
I didn't bother to copy the fonts from the WINDOWS/fonts directory to the desktop.  All that I did was:

(in a sudo -s terminal)
cd /<mountpoint>/WINDOWS/fonts
mkdir /usr/share/fonts/truetype/msttcorefonts/
cp *.ttf *.TTF /usr/share/fonts/truetype/msttcorefonts/

---

### Post by encho on 2006-01-19
Nice, but I could make two points here.
1. First of all, I think it would be more convenient if you were using symlink (if your win partition is auto mounted of course), this way you'll avoid duplicating fonts, but rather using one and same folder for win and ubuntu. When adding new font in ie linux, they will appear in windows as well and vice versa.
2. Rather than using global folder for fonts, it would be more convenient to use your home folder (localy installed fonts at .fonts, also could be symlinked to win folder or any additional lin users). Why? If you are upgrading your system from time to time (like myself :) ) you may want to keep your settings and home folder in separate partition. When reinstalling from scratch, u will still have your fonts & settings.
Hope this helps.

---

### Post by H.E. Pennypacker on 2006-09-20
I copied over Micrsoft Sans Serif, but it has a problem with spaces.  Whenever typing a space, some rectangle shows up.  It can't handle spaces.

I'll use another font, but anyone know how to solve this problem?

By the way, I am not looking for alternatives. I only want Microsoft Sans Serif.

---

