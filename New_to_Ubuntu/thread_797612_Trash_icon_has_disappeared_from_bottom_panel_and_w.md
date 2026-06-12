---
title: "Trash icon has disappeared from bottom panel and won't come back"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by sunbird on 2008-05-17
At some point recently, my trash icon disappeared from my bottom panel. Trying to re-add it to the bottom panel (or to any panel for that matter), doesn't work either. Nothing happens. Ideas?

**Edit:** I tried deleting the panel and re-building it from scratch. All the other things (show desktop, switch workspace) add back fine, but the trash icon still won't show up. :(

---

### Post by Canis familiaris on 2008-05-17
Right click on a blank space notification bar/taskbar and choose Add to Panel...
And in Desktop & Windows choose Trash and click on Add.

To Add the icon to desktop:
    * Press Alt+F2 to get the &#8220;Run Application Dialog&#8221; and type gconf-editor
    * Open apps, then scroll down to nautilus and then choose desktop.
    * There is checkbox to trash, select it.

(EDIT): Misunderstood your post

---

### Post by FuturePilot on 2008-05-17
Bug
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/49594]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/49594")
It has to do with the Bonobo-activation-server not ending its processes on logout. So when you log back in, weird things happen. This is one of them.

---

### Post by Sonic Reducer on 2008-05-31
so, uh... how would you go about fixing it?

---

### Post by SunnyRabbiera on 2008-05-31
This is a hiccup I myself have encountered.
I would just forget about it and use the gconf-editor to make a trash can icon on the desktop.

---

### Post by FuturePilot on 2008-05-31
> **SunnyRabbiera said:**
> This is a hiccup I myself have encountered.
I would just forget about it and use the gconf-editor to make a trash can icon on the desktop.

That's what I did. There were a few things listed in the bug report as a workaround, but they are rather hack-ish.

---

### Post by crjackson on 2008-06-02
Having the trash icon issue myself. Also having issue of wireless not working after reboot.  I think it's related.  Problems come from the same batch of updates.

---

### Post by fakeollie on 2008-06-03
I'm also having the same exact problem: trash is gone, trying to add the trash icon back to the panel (any panel) simply doesn't work. While having the icon on the desktop is a decent workaround, count me in as one still waiting for a fix.

I might be wrong, but I believe this got broken after an update last week that updated both nautilus and gnome-panel (along with a lot of associated library packages). I have the "hardy-proposed" repositories enabled, so I expect a slight amount of breakage once every blue moon. Yet this being an error in a default and widely used feature (the trash icon applet) I'm surprised it doesn't seem to be that many people affected by it.

---

### Post by fakeollie on 2008-06-03
> **FuturePilot said:**
> Bug
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/49594](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/49594)
It has to do with the Bonobo-activation-server not ending its processes on logout. So when you log back in, weird things happen. This is one of them.

That my friend, hits it right in the head in my case. If I kill bonobo-activation-server (kill -9 "pid"), and restart gnome-panel (killall gnome-panel), voila, the trash icon is back!

This is obviously the bug to monitor.

---

### Post by crjackson on 2008-06-03
> **fakeollie said:**
> That my friend, hits it right in the head in my case. If I kill bonobo-activation-server (kill -9 "pid"), and restart gnome-panel (killall gnome-panel), voila, the trash icon is back!

This is obviously the bug to monitor.

I'm going to try this one too when I get home from work.  Could this same bug possible have killed my wireless connection somehow or is that coincidence?

---

### Post by ha-nocri on 2008-06-04
I have the same problem. I've enabled hardy-proposed repos, and trash icon disappeared.

I've tried to kill bonobo-activ.. and restart gnome-panel. The track icon is back, but if I restart X (Ctrl-Alt-Bcsp) trash icon is gone :(

---

### Post by Sonic Reducer on 2008-06-04
> **crjackson said:**
> I'm going to try this one too when I get home from work.  Could this same bug possible have killed my wireless connection somehow or is that coincidence?

wireless on my laptop is has been flaky too since that update. if it's not related to gvfs it's another "update/downgrade"

why hasn't this been fixed yet? i would think completely disabling the trash can (i can't even access it from the desktop, everything just gets permanently deleted), crippling nautilus (i can't access :///computer, can you), and quite likely screwing with the networking in some cases (this update did everything else, why not attribute this to it too?)

---

### Post by linuxisfree on 2008-06-06
> **sunbird said:**
> At some point recently, my trash icon disappeared from my bottom panel. Trying to re-add it to the bottom panel (or to any panel for that matter), doesn't work either. Nothing happens. Ideas?

**Edit:** I tried deleting the panel and re-building it from scratch. All the other things (show desktop, switch workspace) add back fine, but the trash icon still won't show up. :(

I'm having the same issues here, too. I hope they fix it soon. (I want my trash applet back!)

---

### Post by crjackson on 2008-06-07
> **linuxisfree said:**
> i'm Having The Same Issues Here, Too. I Hope They Fix It Soon. (i Want My Trash Applet Back!)

+1

---

### Post by Sonic Reducer on 2008-06-07
they don't even have to fix it, just rename the older version to a higher version number so update manager will "update" it back to how it was

---

### Post by linuxisfree on 2008-06-07
> **Sonic Reducer said:**
> they don't even have to fix it, just rename the older version to a higher version number so update manager will "update" it back to how it was

That... doesn't seem to be a bad idea, but would that really work?

---

### Post by Sonic Reducer on 2008-06-07
> **linuxisfree said:**
> That... doesn't seem to be a bad idea, but would that really work?

i don't see why it wouldn't, but i'm sure some maintainer will refuse to do it because there is a small security hole in the old version that someone could exploit if the moon was in the right phase and they stood on one foot while they hacked.

i heard it as a joke, but i'm really starting to agree with it. Hardy is ubuntu's vista. something as essential as the trashbin has been broken for two weeks without an update

---

### Post by BigSilly on 2008-06-07
> **Sonic Reducer said:**
> 
i heard it as a joke, but i'm really starting to agree with it. Hardy is ubuntu's vista. **something as essential as the trashbin has been broken for two weeks without an update**

[This is a thread from 18 months ago stating the same problem.]("http://ubuntuforums.org/showthread.php?t=282975&highlight=trash+icon+panel") They must be aware of it. I've got this issue too. One minute the trash icon is there on the bottom panel, the next it's gone, and trying to restore it again doesn't work. Technically it *is* there, it's just invisible! You can click the area it is supposed to be in and the trash will open, but the icon isn't there at all. I've tried several times deleting the panel and starting again, but to no avail. I even tried re-installing gnome-applets as advised here but that didn't work.

Starting to lose a little faith in Hardy. Loads of little things going funny like this of late for me.

---

### Post by rampageoberon on 2008-06-07
I had this problem. Think a reboot fixed it. It might be a windowsy solution but it worked. Hope that helps

---

### Post by crjackson on 2008-06-07
There are a few things that I'm not happy about in Hardy but more that I am.  I just put my trashcan on the desktop and use it from there.  I'm a little pissed that a recent update broke my wireless and I can't get it working consistently, but that's just the way it is.  I've ordered an Intel wireless card that's FULLY supported (after testing one of course) so that problem should be solved once and for all.

The Pulse Audio / Flash bug also annoys me, but it's not a deal breaker.  I had none of those issues with Gutsy, but I still like the performance of Hardy better in spite of the recent speed bumps.  It's an LTS version so I'm relatively sure those issues will be worked out in time (I pray).

Otherwise, I can't wait for Intrepid Ibex.

---

### Post by BigSilly on 2008-06-08
> **rampageoberon said:**
> I had this problem. Think a reboot fixed it. It might be a windowsy solution but it worked. Hope that helps

Yeah I'd already tried that but it didn't work.

I put the trash can on the desktop too, but I much prefer it on the panel. I can make do, but it seems so odd to me that there's even a discussion about such a silly thing. Why can't I have it on the panel?

I've yet to come across the deal breaker on Hardy - something that says "enough is enough". I'm still using it, and it's still pretty solid. But there are a lot of silly little niggly things like this that keep annoying me, that didn't occur in past Ubuntus. Things like no logoff sound, text onscreen when shutting down, fsck not checking all partitions at boot (even when changes have been made to fstab), among other things. And now little icons not doing as they're told. 

Like you say, Ubuntu gives more than it takes away, but it don't half feel a little scruffy of late. My apologies if this POV offends anyone. I certainly don't mean to do that.

---

### Post by fakeollie on 2008-06-13
For many people, this is a problem with bonobo-activation-server. I really wish they fixed this package, it screws up not only the panel applets, but also eog (Image Viewer) and it's very annoying. So, while there's no fix in sight for that package and library, here's another workaround.

Go to your home folder and create a file called .xprofile

```
gedit ~/.xprofile
```Inside that file, put this line:

```
killall -u $USER bonobo-activation-server
```Save it, close it and now you have to restart X, so the cleanest way is giving your whole system a reboot. When it's back, the trash and other missing applets will probably be back on your panel. If you had tried to add the trash before, it might happen that you'll see a lot of trash applets on your panel, just delete the others and reorganize your panels.

---

### Post by steve101101 on 2008-06-13
I had this problem and rebooting brought back the trash icon. Hope this helps.

---

### Post by crjackson on 2008-06-13
Actually I enabled proposed updates in my reop list.  I downloaded all the updates and now the problem is fixed on all my systems.

---

### Post by linuxisfree on 2008-06-14
> **crjackson said:**
> Actually I enabled proposed updates in my reop list.  I downloaded all the updates and now the problem is fixed on all my systems.

I did the same thing, and i just updated recently, and you're right... it WOULD fix it. My trash icon is back!:D

---

### Post by xtrender on 2008-06-15
hi.. here i have the same problem..

i dont know if it is related with the instalation of amarok..

aparently, the trash icon is there.. i cant click it but i can't see it.

any clues?

i'm newbie in linux..

---

### Post by Ivo Moelans on 2008-06-17
Last update (2008-06-17) has resolved the problem, at least on my system.

---

### Post by lemured on 2010-12-29
Hi.
I have the same problem, none of the suggestions I read here works.
With the trash bin also the side panel vanished, which is very annoying. Marking it as visible ['view'] doesn't work either, it tells me that it is visible w/ a friendly smile, but isn't. 
Anyone? Anything? ':(

---

### Post by lemured on 2010-12-31
Oups...

So my side pane has reappeared, but not by any action taken by me - any action at all. It just reappeared, as if a small legion of ubuntusymbol-shaped nano-robots have meanwhile been quietly working on the problem.
I hope they're still at it, as my trashbin still remains absent, and none of the suggestions worked.
If anyone has another idea that works, s/he deserves a ubuntu-shaped cherry-tart in case of succsess.

---

### Post by lemured on 2010-12-31
Okay, I'm a little spooked but glad:
apparently ubuntu came with a self-healing mechanism; again w/o doing anything [I mean: anything, not fiddled, nor fumbled, not tried anything subsequent to my former attempts, nor restarted]. My trash icon is back where it's supposed to be, as if back from a holiday and not expecting that I'd notice.
Just out of interest: if anyone could explain this to me, otherwise I'll treat any future problem with sitting back, relax and let my [the cheapest one can buy] netbook solve it internally w/ ubuntu nano-robots...

---

