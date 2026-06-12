---
title: "alpha2 problems"
date: 2011-07-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-07-08
I installed alpha2 earlier and have now fully updated.
The wireless applet has disappeared from the top panel.
If I try to adjust the slider for sound level from the sound applet the slider can only go to fully on or fully off then the desktop crashes and logs me out.

This is an almost unchanged installation with no proprietary drivers installed.

Are these problems being seen by others in aplha2?

---

### Post by Harry33 on 2011-07-08
> **Quackers said:**
> I installed alpha2 earlier and have now fully updated.
The wireless applet has disappeared from the top panel.
If I try to adjust the slider for sound level from the sound applet the slider can only go to fully on or fully off then the desktop crashes and logs me out.

This is an almost unchanged installation with no proprietary drivers installed.

Are these problems being seen by others in aplha2?

OK Quackers,
I had a similar problem with the network applet (wireless applet) with my 32-bit (Intel graphics) setup. But after upgrading libappindicator3-1 and libindicator3-6 the issue was gone. I do not use any PPA's with that setup.

---

### Post by Quackers on 2011-07-08
Yes, pretty much vanilla here too :-)
Have you tried to adjust the sound level?
After the updates you mention my wireless indicator is still missing - I'm on 64 bit.

---

### Post by sgage on 2011-07-08
> **Quackers said:**
> Yes, pretty much vanilla here too :-)
Have you tried to adjust the sound level?
After the updates you mention my wireless indicator is still missing - I'm on 64 bit.

A lot of stuff with indicators seems to be a mess right now. Did you do a partial upgrade at any time? I use Synaptic, and it tells you exactly what it is going to do, and right now, it wants to remove all kinds of indicator stuff, along with Unity 2D. So I'll just wait.

Just have to wait until all the dependencies and whatnot get sorted - things get uploaded asynchronously. You can really get a feel for what's going on if you use Synaptic...

---

### Post by Harry33 on 2011-07-08
> **Quackers said:**
> Yes, pretty much vanilla here too :-)
Have you tried to adjust the sound level?
After the updates you mention my wireless indicator is still missing - I'm on 64 bit.

It is true that there are a lot of updates concerning different indicators right now.
Here are the most recent ones.

Anyways, the sound-level setting works well in my 64-bit setup (but gnome-shell with indicator-sound not installed).

> 
[ubuntu/oneiric] indicator-appmenu 0.2.91-0ubuntu1 (Accepted) Ken VanDine
[ubuntu/oneiric] indicator-messages 0.4.91-0ubuntu1 (Accepted) Ken VanDine
[ubuntu/oneiric] indicator-me 0.2.92-0ubuntu1 (Accepted) Ken VanDine
[ubuntu/oneiric] indicator-power 0.2-0ubuntu1 (Accepted) Ken VanDine
[ubuntu/oneiric] indicator-datetime 0.2.91-0ubuntu1 (Accepted) Ken VanDine
[ubuntu/oneiric] libappindicator 0.3.90-0ubuntu1 (Accepted) Sebastien Bacher
[ubuntu/oneiric] indicator-application 0.3.91-0ubuntu1 (Accepted) Sebastien Bacher
[ubuntu/oneiric] indicator-session 0.2.92-0ubuntu2 (Accepted) Sebastien Bacher
[ubuntu/oneiric] indicator-power 0.1-0ubuntu1 (Accepted) Ken VanDine


---

### Post by Quackers on 2011-07-08
It's a fresh alpha2 install - about 8 hours old :-)
I do use synaptic for updates.
It seems reasonable to me to want to remove some indicator stuff if it's going to replace them. Like removing Unity and replacing it with a new version. Happens all the time doesn't it?
If there are dependency problems synaptic should tell us about them first - and often does, it seems to me. Though not always, in my experience :-)

A desktop crash whilst adjusting the volume seems a bit odd though! If others are experiencing the same I can wait for updates to solve it. If it's something wrong with my system I need to be looking elsewhere.

I'll keep an eye on updates.


Thanks Harry33 I'll keep watching :-)

---

### Post by fjgaude on 2011-07-08
> **Quackers said:**
> Yes, pretty much vanilla here too :-)
Have you tried to adjust the sound level?
After the updates you mention my wireless indicator is still missing - I'm on 64 bit.

On my Alpha 2 x64 VMware install the sound works as it should, with the slider controlling the sound.

I've not tried it on my GRUB iso x64 install. Will sometime tomorrow when I get time.

###

I spoke too soon... I rebooted the VM and the sound icon is gone! So... we wait for fixes to come through.

---

### Post by Quackers on 2011-07-09
Thanks fjgaude, it seems so :-)

---

### Post by Quackers on 2011-07-09
I installed a couple of gtk2 packages (for sound and indicator) and now my wireless applet is back and works normally. The sound is still not fixed fully though. I can now adjust the sound without crashing lightdm by clicking on the icon and then on "sound settings". I can adjust the slider there and the volume changes - even though the output stays shown as 100%, when it isn't.
Adjusting the slider in the normal way produces no change at all - the slider does not move.

Also it seems that gdm is not installed by default in alpha2. Is that intentional?

---

### Post by cecilpierce on 2011-07-09
Same thing here with the volume, its only on one of three oo's. Seems like someone would figure this thing out, Ive tried and cant  :p

---

### Post by lucazade on 2011-07-09
> **cecilpierce said:**
> Same thing here with the volume, its only on one of three oo's. Seems like someone would figure this thing out, Ive tried and cant  :p

don't have problem with sound here but i've read there are some issue with sound applet in alpha2 [release notes]("https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview")

"Sound is muted in live session and first boot of fresh installation with many sound cards. (770349)"

---

### Post by Quackers on 2011-07-09
Sound isn't muted for me, it's just not adjustable in the normal way - I have to use sound settings in the drop-down from the applet.

Anyway it's all a moot (not mute :-) ) point now as on boot I have no keyboard or pointer movement :-)
It's getting worse all the time!
I think I'll give alpha2 a rest and return to Natty for the moment.

---

### Post by lorenzfx on 2011-07-09
> **Quackers said:**
> Sound isn't muted for me, it's just not adjustable in the normal way - I have to use sound settings in the drop-down from the applet.

Anyway it's all a moot (not mute :-) ) point now as on boot I have no keyboard or pointer movement :-)
It's getting worse all the time!
I think I'll give alpha2 a rest and return to Natty for the moment.

after restarting the session manager (rebooting, logging out and back in and so forth) I cannot user mouse or keyboard either, but after plugging them in and out they work again

---

### Post by Quackers on 2011-07-09
Yes thanks, that works with the usb mouse but I'm on a laptop - no good for keyboard :-(

And welcome to UF lorenzfx :-)

---

### Post by lorenzfx on 2011-07-09
so how do I report this bug? since I don't know which pid is causing this, it seems I cannot report it using apport...

---

### Post by Rasa1111 on 2011-07-09
> **Quackers said:**
> Sound isn't muted for me, it's just not adjustable in the normal way - I have to use sound settings in the drop-down from the applet.

Anyway it's all a moot (not mute :-) ) point now as on boot I have no keyboard or pointer movement :-)
It's getting worse all the time!
I think I'll give alpha2 a rest and return to Natty for the moment.


 I think you just saved me a good hour or two.
I'm going to remove this 11.10Alpha2 USB stick and forget about it for awhile I think. lol
I was just about ready to install it to.   Thanks.

---

### Post by Quackers on 2011-07-10
Rasa1111, in all honesty there seems to be only two of us with this problem, so far. It was fine before I ran the updates from the last 2 days or so (apart from the dodgy sound control). Still no keyboard/mouse now, but it boots :-)

---

### Post by teachop on 2011-07-10
> **Quackers said:**
> but it boots :-)
Not booting here... and sudo service lightdm restart ends with a black screen.

---

### Post by jerrylamos on 2011-07-10
Well, I've got Alpha 2 live booting & running on this Acer netbook, an Acer notebook, an older IBM Thinkpad, and a Compaq tower.

Having said that I'm chicken to try updates.  Let the dust settle a bit.

I'm running live with "persistent" which saves changes and even updates when I want, installs will wait a while.

Install on a USB hard drive a couple weeks ago with the then current Daily Build blew the master boot record and partition table on the main hard drive on my notebook.  Oops.  4 DVD's later the Windoze 7 struggled to life.  Why keep Windoze 7?  At some point I'll upgrade and a then used notebook is more use to someone with Windoze.....

Jerry

---

### Post by fjgaude on 2011-07-10
Yes, Jerry, I wait too... without a Ubuntu 2D I can't have a VM to play with and update many times a day. There's no driver for 3D in VMware Player...

My 3D GRUB ISO works but I'm not persistent, so... I wait for the next daily.

---

### Post by pulpo69 on 2011-07-10
if i get to lightDM login screen, mouse cursor is frozen and keyboard doesn't work. If i plug out the mouse and keyboard connectors and plugin again keyboard and mouse works. (both usb connected)

---

### Post by Quackers on 2011-07-10
Same here (but sometimes that login screen doesn't appear - even though it's set to not autologin!) for the usb mouse but it's a bit more involved for me to unplug a laptop keyboard. It's obviously some sort of detection problem at boot (possibly synaptics, in my case).

---

