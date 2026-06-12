---
title: "HOWTO: Tango(kinda) userlist icons for XChat"
date: 2006-08-15
forum: Outdated Tutorials &amp; Tips
---

### Post by xen on 2006-08-15
This is a quick tutorial for those that are bored with the standard userlist icons in XChat. Unfortunately I cannot remember the origin of these icons that I have modified for the purposes of this tutorial, I can however tell you that they came from a Tango (unofficial) icon theme for Gaim. I do not think that these icons are official, but they fit in nicely.

End result:
[IMG]http://img130.imageshack.us/img130/5860/screenshot1mm4.png[/IMG]

Simply extract these icons attatched to the directory (you will need to create it):
```
/usr/share/xchat/
```

NOTE: If you want to use your own icons, you must use the same name as I have for these images.

Cheers, xen.

---

### Post by crackseller on 2006-08-17
Well done, Xen :)

---

### Post by LacteuS on 2006-08-17
Very nice. Thanks for the tip :)

---

### Post by anodizer on 2006-08-17
Is there any way to have an icon for a user without op/voice/whatever?
When does "Red" and "Purple" icons appear?

---

### Post by Dylan103 on 2006-08-17
Very very nice, what theme is that btw? I like it, but not the background from what I can see, reminds me of windows.. lol.

---

### Post by Horizon on 2006-08-17
> **Dylan103 said:**
> Very very nice, what theme is that btw? I like it, but not the background from what I can see, reminds me of windows.. lol.
Looks like Rezlooks Gilouche to me. Nice icons btw, I never even thought of Xchat icons =D>

---

### Post by zenwhen on 2006-08-17
These are super nice. Anything is nicer than the default ones, but these are great.

---

### Post by Tomosaur on 2006-08-17
Nice one, I hated the stupid dot things.

---

### Post by starscalling on 2006-08-18
sigh
just one more thing on a long list of em that doesnt work for me ~_~

---

### Post by Horizon on 2006-08-18
> **starscalling said:**
> sigh
just one more thing on a long list of em that doesnt work for me ~_~
What do you mean it doesn't work? All you have to do is "mkdir /usr/share/xchat" and copy them all into there. Maybe this doesn't work on gnome-xchat? I don't know since I uninstalled that after I started it and thought "wtf is this?! I want my xchat".

---

### Post by h1web on 2006-08-19
lol its nice xen.

---

### Post by xen on 2006-08-20
Yeah for those that wanted to know, the GTK theme is Rezlooks-Gilouche. The wallpaper is kind of Windows-ish, they are dual-monitor wallpaper's by -kol. (You can catch his entire series at deviantART).

Cheers!

(I am aware this mod is not suited to everyone, because these icons are fairly big, you can either resize them or just not use them, but no point complaining eh?!)

---

### Post by hype on 2006-08-20
Just a noob question: How did you manage to put the channels list at bottom of Xchat window?

Nice set of icons tho.

---

### Post by its_me_gb on 2006-08-21
View > Layout > Tabs

---

### Post by bestial on 2006-09-05
Nice work! And I didn't have any troubles for it to work in gnome.

---

### Post by Uncle Spellbinder on 2006-09-06
Created */usr/share/xchat/*, added the icons.  Nothing. I rebooted, still nothing. Ideas?

---

### Post by apakatt on 2006-09-27
I made a quick "port" for Konversation. I have attached the Konversation-theme here. Im not 100% sure if I got the colors right for the different user-types but according to the screenshot I belive its about right.

---

### Post by henriquemaia on 2006-09-27
Thanks a lot. Worked like a charm!

@Uncle Spellbinder: I just restarted xchat and there they were. What xchat version are you running?

---

### Post by xopher on 2006-11-23
Bless you!

lol, I sound like a nun.

No really, they're great! Thank you!

---

### Post by Eazy© on 2006-11-23
> **Uncle Spellbinder said:**
> Created */usr/share/xchat/*, added the icons.  Nothing. I rebooted, still nothing. Ideas?

This didn't work for me either. What I did was: downloaded the [source]("http://xchat.org/files/source/2.6/xchat-2.6.8.tar.bz2"), unzipped it, and overwrote  the original icons in "xchat-2.6.8/src/pixmaps" with the new once. Then I compiled with:
```
./configure
make
sudo checkinstall 
```
(you need the checkinstall package if want to make a deb-package)

I do got a problem of my own that I don't have been able to solved yet. I cant get spelling support to work with English language. Swedish works (I'm Swedish). In Dapper I had spelling support to work for both English and Swedish at the same time. In Edgy this seems to be impossible. It doesn't matter what compile option I do eg. 
```
./configure --enable-spell=static
./configure --enable-spell=libsexy
./configure --enable-spell=gtkspell
```

I have tried to install all spelling package available like aspell, ispell, dev-packages etc. I'm guessing it has to do with locales or something, because it dosen't generate a "LC_MESSAGES/xchat.mo" for English language (don't know if it should?...I'm a noob) If anyone has an idea of whats wrong, I wold be most grateful.

---

### Post by JayTee on 2006-11-29
I tried this and only the new Op icon shows up. The regular chat room members and members set as away don't have any icons.
[Edit] 11/30/06
I had one of the ops in one of my usual IRC haunts give me voice and that gives me the yellow icon so it's working I guess. Anyone know what the purple, red and hop icons do?

---

### Post by ryu kun on 2006-12-06
> **anodizer said:**
> Is there any way to have an icon for a user without op/voice/whatever?
When does "Red" and "Purple" icons appear?

"Userlist icons: Call the files op.png, hop.png, voice.png, red.png and purple.png. Red and Purple are used for Channel Owner and Founder. They will be loaded at the next startup."

from [official XChat FAQ]("http://www.xchat.org/faq/#q27").

---

### Post by L3oN on 2006-12-07
It don't work fine for me...

This is the result:
[[IMG]http://img143.imageshack.us/img143/2642/schermataxchatl3onazzurve5.th.png[/IMG]](http://img143.imageshack.us/my.php?image=schermataxchatl3onazzurve5.png)

Any icon not appear!

---

### Post by atlas95 on 2006-12-07
Is this work for xchat-gnome?

---

### Post by ryu kun on 2006-12-07
> **L3oN said:**
> It don't work fine for me...

This is the result:
[[IMG]http://img143.imageshack.us/img143/2642/schermataxchatl3onazzurve5.th.png[/IMG]](http://img143.imageshack.us/my.php?image=schermataxchatl3onazzurve5.png)

Any icon not appear!

It works fine for you. Normal users don't get any icons in user lists, it's normal.

---

### Post by L3oN on 2006-12-07
Ah ok sorry...

There is noway to get Normal user an icon?

---

### Post by klhrevolutionist on 2007-04-25
Ok, I have compiled xchat into it's own directory /usr/local/Xchat

So where would I put these pixmaps ?? Thanks

---

### Post by xopher on 2007-09-10
Hi! I've been using these icons for a long time now, but when I upgraded xchat to 2.8.4, they won't show anymore.

Any ideas?

---

### Post by Whoopie on 2007-09-10
Hi,

please follow [https://bugs.launchpad.net/ubuntu/+source/xchat/+bug/137712](https://bugs.launchpad.net/ubuntu/+source/xchat/+bug/137712)

A new backport is already requested.

Best regards,
Whoopie

---

### Post by xopher on 2007-09-15
Thank you :)

---

