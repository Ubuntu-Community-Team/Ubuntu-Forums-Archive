---
title: "Werid Sound problem, and Deleting files problem."
date: 2008-05-22
forum: New to Ubuntu
---

### Post by Pap3r on 2008-05-22
I have two problems recently.  I've been putting off posting them for quite a while now, as I was hoping to find a solution on my own.  Here's my more pressing matter, followed by a less important, but much more puzzling one.

So here's the deal.  My sound is screwy.  Why, you ask?  Well, It seems as though my programs conflict with each other...  I use Alsa, and my media players that I have tested have all had similar results...  They work :P  (Rythmbox/XMMS/Amarok).  I have also tested sound in games, native and non native, and have found it to work.  Sound in Firefox works as well, which is also nice.

Everything is fine and dandy...  Everything works... when it is used alone.

Here's what I mean.  When using Rythmbox or any other audio player, sound in other programs running simultaneously, i.e. browsing the net while listening to music, does not work on one or the other.  It depends on the order I open the program.  This goes for games too.  I'll open Rythmbox, turn on a tune, and start browsing, but the instant I get to a video or song online, no sound is heard.  If I open firefox or the game first, and begin using it, I receive sound from Firefox/game, but *not* from Rythmbox.

If I close Rythmbox, then reopen firefox/game I receive sound, but not in rythmbox...  But If I try to duplicate this in reverse, close firefox and then open rythmbox again, I don't get sound from the latter, only firefox.

I can regain sound in rythmbox/games by restarting x, but the process repeats itself after.  Why is this happening?  I'd like to just be able to pause my music to listen to a video, not restart x to get everything back to normal.

Here's my second issue:  I can't empty my trash...  I have DirectX files in my trash bin, and I am unable to delete them.  I have been unsuccessful in locating the trash's actual location, so I can't rm -r it.  It will delete all other files in the trash, besides the DirectX ones.  I get a permission denied claim, but since I can't find them manually, I can't sudo them.  Any help?

---

### Post by Master Grah on 2008-05-22
Well, for the second problem, you could try moving the file back to the desktop, or whatever, changing the file permissions, and then redeleting it. As for the sound, I have nothing.

---

### Post by iaculallad on 2008-05-22
For the sound problem, try doing this:

System->Preferences->Sounds

and switch ALL from Automatic to ALSA

---

### Post by Pap3r on 2008-05-22
I can't move the files form the trash, it only copies them, and I can't change the permissions of the files in the trash...

Sound works now, thanks very much :)

---

### Post by iaculallad on 2008-05-22
cd ~/.Trash

(cd ~/.Trash is your GNOME user directory for Trash actually) then issue the command

sudo rm -rf *.*

but be very careful because that will delete all files in your Trash.

---

### Post by Pap3r on 2008-05-22
I couldn't cd to .trash, nor was it even in home with a ls -a

I couldn't find it an any other locations either.

---

### Post by iaculallad on 2008-05-22
> **Pap3r said:**
> I couldn't cd to .trash, nor was it even in home with a ls -a

I couldn't find it an any other locations either.

Copy the exact words (cd ~/.Trash) and paste it on your terminal:

**cd ~/.Trash**

then issue the command

**sudo rm -rf *.***

but be very careful because that will delete all files in your Trash.

---

### Post by Pap3r on 2008-05-22
```
pap3r|joe-desktop~| cd ~/.Trash
bash: cd: /home/joe/.Trash: No such file or directory
pap3r|joe-desktop~|

```

I told you :/

---

### Post by iaculallad on 2008-05-22
> **Pap3r said:**
> ```
pap3r|joe-desktop~| cd ~/.Trash
bash: cd: /home/joe/.Trash: No such file or directory
pap3r|joe-desktop~|

```

I told you :/

Are you using the GNOME or the KDE as your desktop?

---

### Post by Pap3r on 2008-05-22
Gnome

---

### Post by iaculallad on 2008-05-22
> **Pap3r said:**
> Gnome

Try this:
[B]
sudo rm -rf ~/.local/share/Trash[/B]

or **cd ~/.local/share/Trash**

then issue the command **sudo rm -rf *.*** inside the Trash directory

sudo rm -rf ~/.local/share/Trash

that should do it.

~/.local/share/Trash is you Trash directory

---

### Post by Pap3r on 2008-05-22
Awesome, that got it, thanks! :)  I've been referring to this [http://www.linuxconfig.org/images/7/79/Dirtree.jpg](http://www.linuxconfig.org/images/7/79/Dirtree.jpg) until I can memorize the hierarchy :P

---

### Post by iaculallad on 2008-05-22
> **Pap3r said:**
> Awesome, that got it, thanks! :)  I've been referring to this [http://www.linuxconfig.org/images/7/79/Dirtree.jpg](http://www.linuxconfig.org/images/7/79/Dirtree.jpg) until I can memorize the hierarchy :P

You're Welcome. Goodluck and Go Ubuntu

---

