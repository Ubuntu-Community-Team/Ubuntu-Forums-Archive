---
title: "gtk window theme suddenly looks ugly ubuntu 12.04 gnome."
date: 2012-09-13
forum: New to Ubuntu
---

### Post by thebestofall007 on 2012-09-13
Hello folks. I have been having an annoying problem with my theme suddenly looking ugly, even with the default theme that came pre packaged when i installed my system. 

what happens is that the gtk theme turns all gray, sorta windows 95-ish and ugly and i lose my icons. not only that, when playing banshee, i lose the functionality of my media hotkeys (but the app doesn't crash, though), and my notification daemon that shows the song title/artist shows as a window as shown in one of the screenshots here:
 [img]http://i.imgur.com/hrMIC.png[/img] 

and the messed up windows and icons here:
 [img]http://i.imgur.com/TjhAT.png[/img]. 


i tried to fix this problem using instructions from this link: [http://askubuntu.com/questions/141328/default-themes-are-gone-windows-look-ugly](http://askubuntu.com/questions/141328/default-themes-are-gone-windows-look-ugly) with a no-go. So what i am forced to do is press alt+f2 then type killall nautilus in the box, type alt+f2 again and type nautilus to open nautilus again and restore my theme, and restart banshee. this works but is temporary.

Does anyone else have this issue and know how to solve it ONCE AND FOR ALL?

---

### Post by thebestofall007 on 2012-09-14
bump.

---

### Post by Frogs Hair on 2012-09-14
Try the following terminal command to restart Nautilus. ```
nautilus -q
```

---

### Post by thebestofall007 on 2012-09-14
> **Frogs Hair said:**
> Try the following terminal command to restart Nautilus. ```
nautilus -q
```

It fixes the problem temporarily like the killall nautilus and nautilus commands do, but it still comes back eventually.

Do you know of anyone who has filed any bug reports on this in launchpad?

---

### Post by Frogs Hair on 2012-09-15
This problem was related the the Gnome settings daemon on an earlier release but this is the first time I have seen it as a persistent problem on 12.04

---

### Post by thebestofall007 on 2012-09-15
> **Frogs Hair said:**
> This problem was related the the Gnome settings daemon on an earlier release but this is the first time I have seen it as a persistent problem on 12.04

The funny thing is that I never had this issue when I was using 11.10 Oneiric.

---

### Post by thebestofall007 on 2012-09-19
Anyone else had this problem?

---

### Post by thebestofall007 on 2012-10-22
UPDATE

I installed the light-themes packages again, BUT removed all themes so that only ambiance and radiance are present. 

The issue is still there, but it instead reverts back to this (IT LOOKS A HECK OF A LOT BETTER THAN THE WIN 95-ish THEME) this time around:

[IMG]http://imgur.com/69JSi.png[/IMG]


Another thing I found out: I get the above ugliness when I CLICK ON A FOLDER icon on the desktop, for example, but when I either initiate nautilus by typing it into the terminal or open a folder as root/administrator, my custom theme (ambiance with a dark side panel and green instead of orange colors, and gilouche icon theme) comes through and works as planned:

[IMG]http://imgur.com/kNWhk.png[/IMG]

My custom theme ONLY works if I type nautilus in the terminal or open a folder as root whenever the problem surfaces. It seems to be behaving like a problem with nautilus (maybe problems with permissions somewhere?).

Isn't this strange or what?

Any ideas?

---

### Post by Derek Karpinski on 2012-10-23
This was discussed once on askubuntu.com.

Try this.  It has worked for me before.  I think things get loaded out of order, and this will straighten it out.

Close all windows and prepare for a reboot.

```
cd /var/lib/ureadahead
sudo rm *pack*
sudo reboot now
```

let your computer reset, and at the login screen, log in as soon as it lets you.  Then sit for about 30 sec to 1 min to let ureadahead do its thing.

Seems odd this works, but it has solved the ugly theme for me more than once.  Like was mentioned before somewhere, things get loaded too early and it messes up the theme.  YMMV

---

### Post by thebestofall007 on 2012-10-23
> **Derek Karpinski said:**
> This was discussed once on askubuntu.com.

Try this.  It has worked for me before.  I think things get loaded out of order, and this will straighten it out.

Close all windows and prepare for a reboot.

```
cd /var/lib/ureadahead
sudo rm *pack*
sudo reboot now
```

let your computer reset, and at the login screen, log in as soon as it lets you.  Then sit for about 30 sec to 1 min to let ureadahead do its thing.

Seems odd this works, but it has solved the ugly theme for me more than once.  Like was mentioned before somewhere, things get loaded too early and it messes up the theme.  YMMV

That worked for a little while, but it still reverted back. I found another workaround when it reverts though: I typed "killall nemo" to kill nemo, then pressed ctrl alt f2 to bring up the command prompt, then typed "nemo -n" to start it again. it's a quick fix, though.

---

### Post by thebestofall007 on 2012-10-23
I just got through removing nemo (as i hate unity and am using cinnamon instead) and the system seems to be settling down some. the deletion of the ureadahead pack file helped too (thanks), as i did that after removing nemo. 

I got a clue that that nemo might have been causing the grief through this link:

 [http://cinnamon.linuxmint.com/?p=198]("http://cinnamon.linuxmint.com/?p=198"). 

I noticed that the sidebar looks a little different than the traditional nautilus sidebar (as i mentioned that when i invoked nautilus thru terminal, it worked as planned, but when clicking on an icon, it had the grief). 

it turns out that nemo is the default graphical file manager of cinnamon instead of nautilus (why they get the bright idea of using two different file managers is beyond me...) and nemo was crashing, thus causing the issues.


i'll see how this goes...

wish me luck.

---

### Post by thebestofall007 on 2012-10-23
> **thebestofall007 said:**
> I just got through removing nemo (as i hate unity and am using cinnamon instead) and the system seems to be settling down some. the deletion of the ureadahead pack file helped too (thanks), as i did that after removing nemo. 

I got a clue that that nemo might have been causing the grief through this link:

 [http://cinnamon.linuxmint.com/?p=198]("http://cinnamon.linuxmint.com/?p=198"). 

I noticed that the sidebar looks a little different than the traditional nautilus sidebar (as i mentioned that when i invoked nautilus thru terminal, it worked as planned, but when clicking on an icon, it had the grief). 

it turns out that nemo is the default graphical file manager of cinnamon instead of nautilus (why they get the bright idea of using two different file managers is beyond me...) and nemo was crashing, thus causing the issues.


i'll see how this goes...

wish me luck.

Bad news, it's still doing it.:(

the icon theme seems to fall back to humanity.

---

### Post by mag1strate on 2012-10-23
Since you started with unity  and you are now moving through different DE's you are having a bit of problems. This is due to the fact that all three you are using are sort of interdependent on one another. Removing one will cause others to fail requirements for another. Your best bet is to use either Mint (since it is now specific to cinnamon) or a variant flavor of ubuntu. From using Fedora, I see this happen alot when others try to move to KDE or anything else.

---

### Post by thebestofall007 on 2012-10-24
> **mag1strate said:**
> Since you started with unity  and you are now moving through different DE's you are having a bit of problems. This is due to the fact that all three you are using are sort of interdependent on one another. Removing one will cause others to fail requirements for another. Your best bet is to use either Mint (since it is now specific to cinnamon) or a variant flavor of ubuntu. From using Fedora, I see this happen alot when others try to move to KDE or anything else.

i finally fixed it.

Right now I am using mint, but it came with nemo as the graphical file manager alongside nautilus. i ditched nemo and just stuck with nautilus. so far soooo good :).


next, i followed the advice from this page: 

[http://askubuntu.com/questions/21305/desktop-forgets-theme]("http://askubuntu.com/questions/21305/desktop-forgets-theme") 

where i write a script that fixes some "race" condition between two instances of the gnome-settings-daemon or something like that. it turns out that nautilus wasn't to blame, but the gnome-settings-daemon was crashing and messing up nautilus.

next, i tried dereck karpinski's solution posted earlier that removes the *pack* file from /usr/share/readahead and rebooting the machine. that made the theme load more smoothly, and made sure everything loaded in the proper order.

i've been on for about 4 hours with no issues yet, and once again it's so far, so good here. 

THANKS ALL FOR HELPING ME, and I hope anything here helps others.

---

