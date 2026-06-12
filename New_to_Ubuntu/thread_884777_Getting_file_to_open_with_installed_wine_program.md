---
title: "Getting file to open with installed wine program"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by VitaminBB on 2008-08-09
After using transmission I realized I missed utorrent so I installed it using wine, even figured out how to create a link for it in the applications menu, done and done.

Now when I go to download a torrent file it asks me what I want to open it with, now I have been saving the torrent to the desktop then dragging it into the utorrent window, it works but how do I get the "open with" to chose utorrent?

I dug around the computer and I cant even find the utorrent folder created in wine, how would I get firefox to point to that program to open the torrent file with automatically? or is this a limitation of using linux with wine?

---

### Post by pytheas22 on 2008-08-09
I don't have an answer to your question, but as an alternative to utorrent, you may want to look at [Deluge]("http://deluge-torrent.org/").  It's pretty much a clone of utorrent and as far as I can tell offers all of the same functionality (much of it provided via plugins, some of which are not enabled by default, so turn them on once you install it), including detailed control over torrents.  I used to like utorrent when I was on Windows and was never satisfied with the Linux alternatives until I found Deluge, which keeps me very happy.

Also, Deluge is completely free; utorrent doesn't release the source, I think.

---

### Post by VitaminBB on 2008-08-09
Thanks for the tip, ill have to download it and try it out ...

Anyone out there know how to get a file to "open with" a wine application?

---

### Post by speedzor on 2008-08-09
Just choose 'open as', and you'll have an option 'wine windows application', or something similar.
Click that, and you'll probably open utorrent when you've done this with a .torrent file.

At least it works for me like this when using bittorrent.

---

### Post by VitaminBB on 2008-08-09
It only has a couple things to select from, I have to click "other" but when I dig into my directory I cant find utorrent or the wine directory anywhere, im assuming i dont have permission to see it but how do i get this figured out?

---

### Post by Separ on 2008-08-09
the wine folder is a hidden directory. It is located as ~/.wine which can be seen in nautilus by hitting ctrl+h.

To open with a wine app, right click the thing you want to open, choose open with, at the bottom click the arrow so you can enter a custom command and type "wine ~/.wine/drive_c/Program\ Files/Wineapp/app.exe" without quotes and replacing Wineapp and app.exe with the program you want it to open with. (At least that's what I assume that you would have to do)

---

### Post by VitaminBB on 2008-08-09
You the man, thanks alot :)

---

### Post by Hozza on 2008-12-03
cheers, worked perfectly!

I was trying to get KGB files to open with the KGB archiver windows exe that i installed with wine.

I also got the icon for KGB files to change to the KGB archive popper icon file woooooo XD

---

### Post by kchristensen516 on 2009-07-09
You could always write a simple script to open the file

```
wine /home/username/.wine/drive_c/"Program Files"/"utorrent"/utorrent.exe
```

or whatever the correct path is. Save it as utorrent.sh, and make sure it's executable:

```
chmod +x ./utorrent.sh
```

Hope this helps.

-Kevin

---

### Post by youarefunny on 2010-02-02
> **Separ said:**
> the wine folder is a hidden directory. It is located as ~/.wine which can be seen in nautilus by hitting ctrl+h.

To open with a wine app, right click the thing you want to open, choose open with, at the bottom click the arrow so you can enter a custom command and type "wine ~/.wine/drive_c/Program\ Files/Wineapp/app.exe" without quotes and replacing Wineapp and app.exe with the program you want it to open with. (At least that's what I assume that you would have to do)

This isn't working for me.

HELP

I use MS word because i find it loads WAY faster and it would help if I could open directly.

Ubuntu 9.10

---

### Post by pytheas22 on 2010-02-02
> **youarefunny said:**
> This isn't working for me.

HELP

I use MS word because i find it loads WAY faster and it would help if I could open directly.

Ubuntu 9.10

Which custom command did you enter?

---

### Post by youarefunny on 2010-02-14
On the Wine website ([winehq.org]("http://winehq.org")) there is a section for this.  You create a script for every program and chose open with and you select the script.  This works perfectly.

This is also found at the Ubuntu Wiki page for Wine
[https://help.ubuntu.com/community/Wine#Creating%20file%20associations]("https://help.ubuntu.com/community/Wine#Creating%20file%20associations")

I have attached the 2 scripts that I use.  If you quickly look at them you will quickly figure out the file path change that you have to make.  Then just choose open with and navigate to where ever you saved the script.

Enjoy

---

