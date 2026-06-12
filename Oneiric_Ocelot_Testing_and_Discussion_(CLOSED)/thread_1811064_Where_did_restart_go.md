---
title: "Where did restart go?"
date: 2011-07-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sparker256 on 2011-07-24
The drop down menu in the upper right corner got reworked recently but the restart selection is missing. Anyone know how to get it back or is this a bug? If I select the logout selection and go to that screen there is a restart selection in that upper right corner of that drop down menu.

Speaking of drop down menus is there a way to take a screen shot of them?

Thanks Bill

---

### Post by mc4man on 2011-07-24
It's gone for the moment - a bug report suggests it will be returned, either directly or in the login screen - at least here it's not in login either

Edit: just got back in login - kept forgetting to go back to the default lightdm greeter 

[https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/815077](https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/815077)

---

### Post by sparker256 on 2011-07-24
> **mc4man said:**
> It's gone for the moment - a bug report suggests it will be returned, either directly or in the login screen - at least here it's not in login either

Edit: just got back in login - kept forgetting to go back to the default lightdm greeter 

[https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/815077](https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/815077)
Thanks added me to.

Bill

---

### Post by Starks on 2011-07-25
Tap the power button.

It'll bring up a menu.

---

### Post by mc4man on 2011-07-25
nm - a alt log out window w./ restart option was 'stuck'

---

### Post by scradock on 2011-07-29
> **Starks said:**
> Tap the power button.

It'll bring up a menu.
Did you notice - this one is gone now. Tapping the power button gives instant shut-down, even though the Power control thingy says "Ask me". Happened a day or two ago for me, using Unity-3d. Using Gnome-shell in Oneiric still gives the choice, btw.

This is particularly annoying because it means I can't switch from Oneiric to one of the installs on my mega-external drive. Once the machine powers off the external HD isn't mounted soon enough for boot - it's only accessible after a warm boot once an install on my internal HD has mounted the external HD.

---

### Post by scradock on 2011-07-29
> **mc4man said:**
> nm - a alt log out window w./ restart option was 'stuck'
Excuse me - what does that mean? I'm mystified!

---

### Post by P-I H on 2011-07-30
On my installation I log out and then click the "power button" in the upper right corner of the screen.

---

### Post by scradock on 2011-07-30
> **P-I H said:**
> On my installation I log out and then click the "power button" in the upper right corner of the screen.

Yes, that one still works - for now...

---

### Post by dog-soldier on 2011-07-30
i tried 11.10 on my Fujitsu lifebook t4210 from a thumb drive and when i tried to log out it wouldnt. i logged out and clicked on the power button in the upper right and when i would click on restart it would go back to the login screen.i tried 5 or 6 times and the same every time.

other than that every thing seemed to work even my pen.

---

### Post by caryb on 2011-07-31
In Kubuntu (probably unrelated issue) I have to sudo reboot in a terminal to restart the computer as of todays updates.


Cary

---

### Post by ELD on 2011-08-01
Restart is on the login screen (light dm) but not in the power button indicator in Ubuntu itself, why on why was it ever removed?!

---

### Post by kansasnoob on 2011-08-02
I reported this while iso-testing so hopefully it'll get bumped up from medium :)

---

### Post by cariboo on 2011-08-02
There was a post on the Ayatana mailing list about, the restart option being missing, it seems Mr. Shuttleworth agrees that it should be back in the menu.

---

### Post by ELD on 2011-08-02
Who's bright idea was it to remove that in the first place?

---

### Post by ratcheer on 2011-08-02
So, is it just a bug that they intend to fix in a few weeks, or was it an intentional change? I don't know how others are working around it, but I am using "sudo init 6". It is somewhat of a pain, because I always have to enter my password for sudo.

Tim

---

### Post by cecilpierce on 2011-08-02
I do a little less pain with Ctrl+Alt+F1 to get to tty1 then Ctrl+Alt+Delete and it reboots, still a PAIN :(

---

### Post by cariboo on 2011-08-02
I think it was by design, as it does show up when a restart is needed after and update. I think someone forgot that we do reboot on  occasion.

---

### Post by ratcheer on 2011-08-02
> **cariboo907 said:**
> I think it was by design, as it does show up when a restart is needed after and update. I think someone forgot that we do reboot on  occasion.

Thank you. I restart more often than I shutdown, especially on an Alpha release where there are scores of package updates most days.

Tim

---

### Post by kansasnoob on 2011-08-02
Oops I forgot the bug #:

[https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/815077](https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/815077)

---

### Post by mc4man on 2011-08-02
> **ratcheer said:**
> So, is it just a bug that they intend to fix in a few weeks, or was it an intentional change? I don't know how others are working around it, but I am using "sudo init 6". It is somewhat of a pain, because I always have to enter my password for sudo.

TimHere just a simple quicklist entry that runs reboot, (l.click, r.click), though could also be a single click desktop launcher
The need for a password on sudo is easily removed as in natty

---

### Post by meborc on 2011-08-12
restart is back. still not in the menu, but in the shutdown confirmation window... wonder if it will find it's way back to the menu list ;)

---

### Post by mc4man on 2011-08-12
Nm again, 2nd time this thread - do see in the shutdown now

---

### Post by sgage on 2011-08-12
I like having it in the menu, and I like the way the icon used to turn red when a restart was required after an update. I hope they bring that back.

---

### Post by jasonrisenburg on 2011-08-12
well like many "new" platforms it will have its "growing pains" we just need to out last the unity hick ups and learn to modify and use out ppas efficiently, if we so choose to change unity. there may be a ppa out there for it. I have found them for just about everything else I wanted.

---

### Post by lucazade on 2011-08-12
> **sgage said:**
> I like having it in the menu, and I like the way the icon used to turn red when a restart was required after an update. I hope they bring that back.

me too, i prefer old version.

---

### Post by ELD on 2011-08-12
I am with you guys, seems a step backwards to me :/

---

### Post by arpanaut on 2011-08-12
> **sgage said:**
> I like having it in the menu, and I like the way the icon used to turn red when a restart was required after an update. I hope they bring that back.

Ditto

---

### Post by cariboo on 2011-08-12
At least the design people didn't totally get their way and remove restart completely. The original plan was for us to log out first, before being able to restart. Also, it seems to me that this is the Gnome way, even in a pure Gnome 2.X environment, you had to click shutdown in order to get a menu with the restart option.

---

### Post by ELD on 2011-08-13
> **cariboo907 said:**
> At least the design people didn't totally get their way and remove restart completely. The original plan was for us to log out first, before being able to restart. Also, it seems to me that this is the Gnome way, even in a pure Gnome 2.X environment, you had to click shutdown in order to get a menu with the restart option.

It's so stupid who are these design morons?! They should be fired, i want restart back as a normal fricken option!

---

### Post by VinDSL on 2011-08-13
> **ELD said:**
> It's so stupid who are these design morons?! They should be fired, i want restart back as a normal fricken option!
Heh!

Me thinks that's what they call a non-negotiable objection.  :D

I dunno...

I have mixed feelings about it.

Personally, I just punch alt-ctrl-del, logout, and restart from the login screen.

---

### Post by t1497f35 on 2011-08-13
> **ELD said:**
> It's so stupid who are these design morons?! They should be fired, i want restart back as a normal fricken option!
I totally agree with you, it's a lot more time consuming to restart if I have to log out first, after all restarting for many people is a fairly common thing especially since a lot of people are dual/tripple booting. Those "morons", might not really be morons but they _do_ need a reality check.

Canonical should tell them and anyone who's working for it - if you're sacrificing usability and common sense in favor of design - you need to rethink your design. We can't afford a failure like in Gnome3 which even Torvalds hates.

---

### Post by mc4man on 2011-08-13
The way it currently is takes all of about 1/4 sec. to move cursor and use the restart box, - no big deal

---

### Post by rubenverweij on 2011-08-13
Restart is offered as an option in the dialog that pops up when you choose 'Shutdown'. So no need to first logout any more!

---

### Post by lucazade on 2011-08-13
> **mc4man said:**
> The way it currently is takes all of about 1/4 sec. to move cursor and use the restart box, - no big deal

true..  i hope the indicator will become blue as well if reboot is required after updates.

---

### Post by mc4man on 2011-08-13
> **lucazade said:**
> true..  i hope the indicator will become blue as well if reboot is required after updates.

Haven't seen that in quite some time, though I think I'm getting the OSD notify a bit more consistently now
(hard to say, I really don't like the default 10 sec display time so have moved it to 2.5 sec., may miss it once & a while..

---

### Post by meborc on 2011-08-13
> **VinDSL said:**
> 

Personally, I just punch alt-ctrl-del, logout, and restart from the login screen.

i just do sudo reboot in the nearest terminal


but still... i do not understand what is the thinking behind removing restart as one of the options in the list? are people not using it? what happens if kernel updates come through and you need a restart? 

damn design people, they can come up with truly amazing stuff (new software center for example) and then again they can come up with something totally unintuitive :D

---

### Post by ELD on 2011-08-13
I still think it is one of the most stupid decisions ever, why remove the option and put it on shutdown? People look at Shutdown as what it is, who the hell is it hurting to have a "Restart" option right there where everyone expects it to be.

---

### Post by jerrylamos on 2011-08-13
> **ELD said:**
> I still think it is one of the most stupid decisions ever, why remove the option and put it on shutdown? People look at Shutdown as what it is, who the hell is it hurting to have a "Restart" option right there where everyone expects it to be.

Yeh, I'm one who types in sudo reboot on a terminal to make sure I get a reboot and not a shutdown.

On Narwhal and many previous Ubuntu I do Ctrl-Alt-Del then Enter when I want to shutdown.  After closing all running applications of course.

Might be a way to do that if I spend much time on Oneiric.  I just tried the 12 August build which ran about a minute before hanging up solid no cursor movement no keyboard response.  Manual Power Off worked.

Jerry

---

### Post by ELD on 2011-08-14
I guess i can get used to the option being on ctrl alt delete, then again i have been thinking about this.

While yes it is very stupid to remove the restart option directly, but when you click it a confirmation window comes up anyway. 

So when you click shutdown, then restart, it's exactly the same amount of time since you are doing two things both times.

Still it's just idiotic to remove an option like that, i didn't see this discussed ANYWHERE, only the discussion to put it back in. While yes Ubuntu isn't a community as much as we like to think it is they do make decisions against us (sometimes for the better), i think this needed to be talked about more.

---

### Post by randomizer101 on 2011-08-14
You'd think that they'd have learned from the fallout of GNOME's decision to do the exact same thing. We can argue all day about which looks nicer and which makes more logical sense, but at the end of the day if commonly used functionality is not discoverable you've made a bad design decision.

---

### Post by lucazade on 2011-08-14
Ubuntu is trying, with the exception of Unity, to be more upstream possible, in order to reduce the number of patches, that are difficult to maintain.
So the issues with the reboot option seem related to this. 

We should ask gnome devs about the hidden restart option in g-shell, the same way about window decoration buttons removed, the half nautilus3 toolbar, the missing control panel for  fonts and themes, the 'wonderful' adwaita theme, the incomplete/incoherent fallback session, the undeveloped epiphany, the sad programs like rhythmbox and evolution.. and go on..
(I'm happy for other components of course!)

---

### Post by VinDSL on 2011-08-14
> **lucazade said:**
> We should ask gnome devs about [...] the sad programs like rhythmbox and evolution.. and go on...
Talking about doing away with things...

I can't believe Rhythmbox did away with rhythmbox-client!?!?!

That was the one feature that set it apart from the other players.

Last nail in the coffin for Rhythmbox, IMO.  I'll never use it again. :P

---

### Post by lucazade on 2011-08-14
> **VinDSL said:**
> Talking about doing away with things...

I can't believe Rhythmbox did away with rhythmbox-client!?!?!

That was the one feature that set it apart from the other players.

Last nail in the coffin for Rhythmbox, IMO.  I'll never use it again. :P

I didn't know rhythmbox-client.. yes, it should have been a handy feature. :/

---

