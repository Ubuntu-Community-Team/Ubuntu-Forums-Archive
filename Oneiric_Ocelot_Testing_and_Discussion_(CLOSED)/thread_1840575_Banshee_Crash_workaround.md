---
title: "Banshee Crash workaround"
date: 2011-09-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by cor2y on 2011-09-07
So for the past two weeks i have been unable to launch banshee without it crashing.
Turns out a bug from the 10.10 days has reared its ugly head again, if you have the ubuntuone music store extension installed (like i did since i have purchased music via that store to try it out with ubuntuone storage) banshee will continuously crash, you have to remove the addon for banshee to not crash.

Now can someone tell me where i can properly fill this bug? Is it under banshee or ubuntuone?

---

### Post by DogMatix on 2011-09-07
I would have thought banshee.

But, then again...

---

### Post by CaptainMark on 2011-09-08
yeah i had this in the early 11.10 days, what a pain

---

### Post by effenberg0x0 on 2011-09-08
cor2y => You nailed it. I removed the Ubuntu One plugin and it got rock solid again.

Thanks,
Effenberg

---

### Post by VinDSL on 2011-09-08
Heh!  I must have missed that one.

Banshee has been working pretty good for me lately.

Just saying...

---

### Post by VinDSL on 2011-09-08
> **cor2y said:**
> Now can someone tell me where i can properly fill this bug?
[http://banshee.fm/contribute/file-bugs/](http://banshee.fm/contribute/file-bugs/)
[https://bugs.launchpad.net/ubuntu/+source/banshee](https://bugs.launchpad.net/ubuntu/+source/banshee)

Banshee had (like) 800-900 bugs, last I knew.

Make sure to check for dupes...

---

### Post by thonuz on 2011-09-08
I can't seem to use Banshee anymore at all. Songs or albums will not play when I click the play button or from the menu. If I move to tracks to queue then press play it seems to work. 
I don't think its user friendly. I dont like play queues and playlists.The most frustrating thing is trying to kill a random song its playing and have to shut the desktop.
Maybe this is a unity feature but why cant I shut Banshee off easily?

---

### Post by VinDSL on 2011-09-08
> **thonuz said:**
> Maybe this is a unity feature but why cant I shut Banshee off easily?
Truthfully, I've never found a player that works 100%.  Banshee is no better or worse than others, IMO.

Banshee responds rather slowly to commands, on my machine.  That's its biggest problem.

I've found that pre-loading Banshee into memory at boot makes for a better experience.

Here's the shell script that I use:

```

#!/bin/bash
sleep 30
banshee --hide --redirect-log

```

Might want to give it a whirl...  ;)

---

### Post by effenberg0x0 on 2011-09-08
I'm using Clementine for the last couple days with no problem yet. I like that it also integrates with the desktop volume control, like Banshee. The interface and library organization / music search kills Banshee in my opinion. 

Regards,
Effenberg

---

### Post by sgage on 2011-09-08
I've tried 'em all, and still prefer Rhythmbox. It's nice and simple (like me), and rock solid.

Banshee is way too unstable and outright buggy for my liking. 

We sure do have a lot of choices, which is nice.

---

### Post by chromatica86 on 2011-09-08
Man am I glad I read this. Worked perfectly.
Banshee is now working very nicely.

---

### Post by CaptainMark on 2011-09-08
ive always used banshee, i agree its seriously buggy, always has been but its got a lot more features than rhythmbox has

---

### Post by cor2y on 2011-09-08
Thanks for heads up guys, i thought maybe i was the only one experiencing this bug. ;)

Also has anyone else noticed that the "Listen To Music"  Lense in Unity has been replace with Totem  and the totem icon?

---

### Post by chromatica86 on 2011-09-08
But now there's a new problem.
If my ipod is mounted banshee will open and then close right away. Without the ipod mounted it works great.

---

### Post by mc4man on 2011-09-08
> **cor2y said:**
> 
Also has anyone else noticed that the "Listen To Music"  Lense in Unity has been replace with Totem  and the totem icon?
It was previously (a ways back) due to a misnaming issue & unity using gconf defaults
Now whatever you have selected in System Settings > System Info > Default Applications > Music should be what is displayed in the dash lens
(the actual music lens itself will only use banshee no matter what is the default and being shown in the main dash lens

---

### Post by cor2y on 2011-09-08
> **mc4man said:**
> It was previously (a ways back) due to a misnaming issue & unity using gconf defaults
Now whatever you have selected in System Settings > System Info > Default Applications > Music should be what is displayed in the dash lens
(the actual music lens itself will only use banshee no matter what is the default and being shown in the main dash lens

Thanks for the info, according to my Setup i have totem for music and banshee for video by default, no idea how that happened.

>  			 			 			 		   		 		 		But now there's a new problem.
If my ipod is mounted banshee will open and then close right away. Without the ipod mounted it works great.

Maybe that Ipod extension  is acting up again, i remember a couple of releases ago if it was enabled it too would crash banshee, try disabling that plugin from the extension menu under preferences, then restart and see if that helps with it not crashing when ipod is mounted.

---

### Post by effenberg0x0 on 2011-09-08
> **chromatica86 said:**
> But now there's a new problem.
If my ipod is mounted banshee will open and then close right away. Without the ipod mounted it works great.

Banshee **hates **proprietary hardware.

:-)

Regards,
Effenberg

---

### Post by mc4man on 2011-09-08
> **chromatica86 said:**
> But now there's a new problem.
If my ipod is mounted banshee will open and then close right away. Without the ipod mounted it works great.
Got an ipod that's been hanging around here for several yr.'s, what model don't know. (black, 1GB
Anyway it works fine in banshee, ( as does ubuntuone.

1st. thing I'd try is to setup a new user, login to it & try your ipod there. If it works then the issue is local to your main user.
If not then maybe your install is slightly borked, (not uncommon), or there is an issue with whatever model of ipod  you have

---

### Post by chromatica86 on 2011-09-08
> **mc4man said:**
> Got an ipod that's been hanging around here for several yr.'s, what model don't know. (black, 1GB
Anyway it works fine in banshee, ( as does ubuntuone.

1st. thing I'd try is to setup a new user, login to it & try your ipod there. If it works then the issue is local to your main user.
If not then maybe your install is slightly borked, (not uncommon), or there is an issue with whatever model of ipod  you have
I've got a 3rd gen 32gb touch.
It works in rhythmbox but I like banshee more so I'd like it to work.

---

