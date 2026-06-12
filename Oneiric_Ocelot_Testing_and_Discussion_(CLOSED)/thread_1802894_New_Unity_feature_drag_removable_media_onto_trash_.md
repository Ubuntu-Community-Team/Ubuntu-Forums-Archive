---
title: "New Unity feature: drag removable media onto trash to unmount"
date: 2011-07-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2011-07-12
New feature by Andrea Azzarone: you can now drag removable media onto the trash can in the launcher to unmount them.

[http://vimeo.com/26335499](http://vimeo.com/26335499)

Right now this only works with launcher icons, not desktop icons.

Like it?

---

### Post by cgroza on 2011-07-12
Pretty neat. But I would like to try it before posting my opinion.

---

### Post by mc4man on 2011-07-12
If it unmounts the media then that would be a useful it not often used function.
If it ejects than it's not really adding anything other than for the few users who would expect such a feature.

Kinda interesting if actually unmounting that it was accepted considering unmount was removed for devices that can be ejected from unity's r. click menu. (or maybe it was ok to do so in an obscure way rather than directly

Edit: would have preferred they left unmount in the r. click..

---

### Post by CaptainMark on 2011-07-12
its not working for me, i can drag but dropping them into trash does nothing, ive tried usb flash and usb hdd's nothing

also in the video the user only drags one usb drive but both get unmounted???

---

### Post by MacUntu on 2011-07-12
Sorry, I should have noted that this is not yet in Oneiric but compiled from source.

> **mc4man said:**
> If it unmounts the media then that would be a useful it not often used function.
If it ejects than it's not really adding anything other than for the few users who would expect such a feature.

It unmounts AND ejects.

---

### Post by CaptainMark on 2011-07-12
aah makes more sense, i did check the video link for info but theres nothing there about it

---

### Post by mc4man on 2011-07-12
> **CaptainMark said:**
> aah makes more sense, i did check the video link for info but theres nothing there about it
You should probably see it in the next unity release - 
[https://code.launchpad.net/~unity-team/unity/trunk](https://code.launchpad.net/~unity-team/unity/trunk)

orig. bug on if interested
[https://bugs.launchpad.net/unity/+bug/764905](https://bugs.launchpad.net/unity/+bug/764905)

---

### Post by sgage on 2011-07-12
I'd be happy if clicking on the trash icon in the launcher opened the trash folder!

---

### Post by cgroza on 2011-07-12
> **sgage said:**
> I'd be happy if clicking on the trash icon in the launcher opened the trash folder!
Works fine here.

---

### Post by MacUntu on 2011-07-12
It does?

---

### Post by sgage on 2011-07-12
> **cgroza said:**
> Works fine here.

Hmmm... hasn't worked here in a couple of weeks. I can right click on it, and empty the trash, but simply clicking on it does nothing at all. 

Any idea as to what I might try to fix it?

---

### Post by berthiggins on 2011-07-12
It does not open for me either
I had not actually noticed :-)

---

### Post by sgage on 2011-07-12
> **berthiggins said:**
> It does not open for me either
I had not actually noticed :-)

What? How could you not notice? This is absolutely and totally a show-stopper bug!  :KS

---

### Post by mc4man on 2011-07-12
> **sgage said:**
> I'd be happy if clicking on the trash icon in the launcher opened the trash folder!

There is an obscure bug that can affect a few things, opening the trash in nautilus from the unity launcher is one - though typically it would open the trash with something other then nautilus

Could you post this file?
```
gedit ~/.local/share/applications/mimeapps.list
```

---

### Post by sgage on 2011-07-12
> **mc4man said:**
> There is an obscure bug that can affect a few things, opening the trash in nautilus from the unity launcher is one - though typically it would open the trash with something other then nautilus

Could you post this file?
```
gedit ~/.local/share/applications/mimeapps.list
```

Here it is:

```
[Added Associations]
x-scheme-handler/http=firefox.desktop;
x-scheme-handler/mailto=thunderbird.desktop;
text/calendar=gedit.desktop;
audio/x-vorbis+ogg=banshee.desktop;totem.desktop;
video/x-ogm+ogg=banshee.desktop;totem.desktop;
image/jpeg=eog.desktop;
application/x-wine-extension-ini=gedit.desktop;

[Default Applications]
audio/x-vorbis+ogg=banshee.desktop
video/x-ogm+ogg=totem.desktop
image/jpeg=eog.desktop
application/x-wine-extension-ini=gedit.desktop
```

Don't see anything about trash there...

---

### Post by mc4man on 2011-07-12
> **sgage said:**
> Here it is:
Don't see anything about trash there...
You wouldn't. You don't have 1 line that can cause some issues, though not directly to opening trash in nautilus from the launcher
> [Default Applications]

inode/directory=nautilus-folder-handler.desktop


(this is due to /etc/gnome/defaults.list still setting nautilus-folder-handler.desktop as the default. it affects other things.
bug here - 
[https://bugs.launchpad.net/ubuntu/+source/desktop-file-utils/+bug/797000](https://bugs.launchpad.net/ubuntu/+source/desktop-file-utils/+bug/797000)

The issue with trash is related to xdg-open, I've fixed it here about a week ago though likely not a valid fix anymore.
I'm doing a new install in a few - I'll see what happens

It's possible you'd see something like this in .xsession.errors, but not assured
/usr/bin/xdg-open: 563: gnome-open: not found

---

### Post by ronacc on 2011-07-12
Lets see now , how do I unmount this cd ? Oh yeah drag it to the trash ! Thats really intuitive and discoverable . I guess the devs really have all trooped off to lala land .

---

### Post by ezsit on 2011-07-12
Well, the Mac has had this feature since the early 1990's, if not earlier. I'd say this feature implementation is a waste of time for all but the Mac affectionados.

---

### Post by mc4man on 2011-07-12
> **sgage said:**
> Hmmm... hasn't worked here in a couple of weeks. I can right click on it, and empty the trash, but simply clicking on it does nothing at all. 

Any idea as to what I might try to fix it?
> Originally Posted by mc4man
I'm doing a new install in a few - I'll see what happens
For the moment you can still fix like this - 

```
sudo apt-get install libgnome2-0
```

If at some point you choose to open a dir. with anything other than nautilus than it will stop working unless you remove the line mentioned previously.
The other affects of opening a dir. with something other than nautilus can be negated by squaring up etc/gnome/defaults.list first though that will be of no help as far as trash folder from launcher

---

### Post by CaptainMark on 2011-07-13
i think id rather right click and unmount anyway, drag is a pain because of that small delay you have to depress the left mouse button for a second or so because i always move the mouse away too early and the launcher stays put

---

### Post by MacUntu on 2011-07-13
> **ronacc said:**
> Lets see now, how do I unmount this cd? Oh yeah drag it to the trash!

You don't need to use that functionality? As long as they just add features instead of change things, I'm okay with it.

And no, I don't think that feature makes any sense. A trash can is a trash can; you put things in it that you don't need anymore. Yet, millions of Mac OS X users don't seem to have a problem with it.

> **ronacc said:**
> I guess the devs really have all trooped off to lala land .

Yet you are still there. ;)

---

### Post by ronacc on 2011-07-13
point 1 I never use the trash can , one of the first things I do is add a "real" delete to nautilus .

point 2 who said I was sane ?

---

### Post by Peter09 on 2011-07-13
Yeah - I never could quite figure the trash can - if I drag to the trash can then I should expect it to be deleted (give me a couple of days grace is good). In Linux the trash seems to be just another folder in reality - to store things in.
 
the number of times I have had beginners run out of disk space because the trash is full ......

---

### Post by kahping on 2011-07-13
> **ronacc said:**
> Lets see now , how do I unmount this cd ? Oh yeah drag it to the trash ! Thats really intuitive and discoverable . I guess the devs really have all trooped off to lala land .

I'd have to agree. I'm more likely to think dragging a volume to thrash would just delete all its contents rather than unmount it :(

---

### Post by sgage on 2011-07-13
> **mc4man said:**
> For the moment you can still fix like this - 

```
sudo apt-get install libgnome2-0
```

If at some point you choose to open a dir. with anything other than nautilus than it will stop working unless you remove the line mentioned previously.
The other affects of opening a dir. with something other than nautilus can be negated by squaring up etc/gnome/defaults.list first though that will be of no help as far as trash folder from launcher

Not quite sure what you mean here, but installing the libgnome2 package has it working for now (opening trash from launcher icon). Thanks!

---

### Post by cariboo on 2011-07-13
Instead of using the trash can to eject an external drive like the Mac does, I rather have a way of removing the trash icon, as I'm with ronacc, I never use it, and enable delete as one of the first things on a new install.

---

### Post by mc4man on 2011-07-13
> **sgage said:**
> Not quite sure what you mean here, but installing the libgnome2 package has it working for now (opening trash from launcher icon). Thanks!

If you were to happen to right click on a folder > open with other application and do so, (like opening a folder with a music player), you'll then lose opening trash with nautilus. 

Based on the mimeapps.list you posted that doesn't appear likely to happen, if it does you can fix by removing the line in mimeapps.list I noted.
(for the trash deal it's actually both inode/directory= lines

---

### Post by meeples on 2011-07-14
> **kahping said:**
> I'd have to agree. I'm more likely to think dragging a volume to thrash would just delete all its contents rather than unmount it :(

Yeah i would say the same.

For the people who say this is how Mac OSX does it, when you start dragging a volume, the trash can changes to an eject button so you know your ejecting it rather than deleting its contents.

I would and other people would be scared to use this functionality in ubuntu unless it was made more clear what will happen to the volume.

---

