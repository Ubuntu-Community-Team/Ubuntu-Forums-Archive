---
title: "info please"
date: 2011-08-20
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ronacc on 2011-08-20
What is the name of that indicator (top right corner ) that provides the logout , suspend , etc options . I need to know what to call it so that I can file a bug against it .

---

### Post by Basher101 on 2011-08-20
wow thats a good question...they should add mouseovers like in windows for stuff like this so we musnt always ask...i have no idea what its called, but i would guess system menu? or ...i dunno how its called, would like to know myself what that is^^

---

### Post by ronacc on 2011-08-20
they used to before all this unity / gnome3 crap started removing all choice from the users .

---

### Post by mc4man on 2011-08-20
indicator-session

---

### Post by SoFl W on 2011-08-20
Can you right click on it and then select "about", that will tell you the name.

Attached is what my about looks like.

---

### Post by Basher101 on 2011-08-20
well, my first ubuntu i was using was 10.10...did not have any particular usage for it and dumped it...later windows kept screwing up, so i downloaded 11.04 and started actually using it, and the feeling of it after i googled for a few hours and fiddled around with it, customizing backgrounds themes mouse pointers icons ect....i was simply blown away. I also made a fresh install of windows. It took me 5 hours total of custimizing it to be like before...also the updates ate up alot of the time...after a fresh install of ubuntu (on a usb stick for my friend) it took me 30 minutes installing and customizing it how he wanted it. Also for DE i like unity alot, gnome 2.3 was kinda cramped with the system menu, i mean half of your screen was just the system drop down menu...still i think its just a matter of taste. Everyone his/her own

---

### Post by Basher101 on 2011-08-20
*facepalms* d'uh...in the upper panel on the top are just indicator applets, i should have guessed earlier that its the for the sessions as it gives logout,change user,ect. options

---

### Post by jerrylamos on 2011-08-20
> **ronacc said:**
> What is the name of that indicator (top right corner ) that provides the logout , suspend , etc options . I need to know what to call it so that I can file a bug against it .

There's an indicator up there all right, but it:

Doesn't Do Anything.

Used to be, since the one on the main panel didn't have any purpose, I could do a logout and there was an indicator at the top right of that I could use.

That one doesn't do anything either.

So I launch a terminal and do sudo reboot or sudo halt.

Last couple of nights all sudo halt did was put up an Ubuntu screen and turn the hard drive off.  Did not halt.

So I did the ultimate manual power off button.  That's not broken yet.

Jerry

---

### Post by ronacc on 2011-08-20
try ```
sudo shutdown now 
``` . that should power you off , halt just brings the system down .and thas what I am gong to bug about the indicator-session ( thanks mac4man ) no shutdown/reboot option only that utterly worthless logout option .I have given them enough time to put back those options , now its time to bitch .

---

### Post by buzzmandt on 2011-08-20
> **ronacc said:**
> try ```
sudo shutdown now 
``` . that should power you off , halt just brings the system down .and thas what I am gong to bug about the indicator-session ( thanks mac4man ) no shutdown/reboot option only that utterly worthless logout option .I have given them enough time to put back those options , now its time to bitch .
give'em helsinki


> they used to before all this unity / gnome3 crap started removing all choice from the users .
removing all choice from the users=gnome

---

### Post by Harry33 on 2011-08-20
> **ronacc said:**
> try ```
sudo shutdown now 
``` . that should power you off , halt just brings the system down .and thas what I am gong to bug about the indicator-session ( thanks mac4man ) no shutdown/reboot option only that utterly worthless logout option .I have given them enough time to put back those options , now its time to bitch .

In gnome-shell you see only the logout option, but pressing alt (when the menu is open) will make the power-off option visible.

---

### Post by mc4man on 2011-08-20
> **ronacc said:**
> try ```
sudo shutdown now 
``` . what I am gong to bug about the indicator-session  -  no shutdown/reboot option only that utterly worthless logout option .I have given them enough time to put back those options , now its time to bitch .
The indicator is only for unity*, and presently does have everything but a restart option which is inc. on the shutdown box
Gs uses as Harry described, nothing for ubuntu to do, (change) there

---

### Post by ronacc on 2011-08-20
since I only use gnome-shell I guess I need to bitch at gnome . 

@ harry33  I don't think I should have to press anything to get an option that has always been normal , I think that a majority of linux users are like myself and run a single user personal system and therefore  rarely or never have need to logout , however we do have need very often to either shutdown or (less often) reboot . Personaly I NEVER logout , suspend or hibernate , my box is either on or OFF as in not consuming ANY power .

---

### Post by ranch hand on 2011-08-20
There is an extension to get you the shutdown option.  This gives you a box with the option to also restart.

Seems to work pretty well.

Gnome seems interested in just doing the broad brush strokes and leaving the details to the community.

---

### Post by ronacc on 2011-08-20
where is this extension available ? This is my busy season so I haven't had much time lately to keep up with things .

---

### Post by ranch hand on 2011-08-20
> **ronacc said:**
> where is this extension available ? This is my busy season so I haven't had much time lately to keep up with things .
Extensions are getting out of hand and a little difficult to find.  Here is one list;
[http://www.fpmurphy.com/gnome-shell-extensions/](http://www.fpmurphy.com/gnome-shell-extensions/)

All I have installed are the 6 included in this package which includes the shut down deal;
[http://intgat.tigress.co.uk/rmy/extensions/index.html](http://intgat.tigress.co.uk/rmy/extensions/index.html)

I just extracted the buggers and put them in both the recommended files.  They did not all work if just in one of them.  The package has been upgraded to 0.2.5 since I downloaded it at 0.2.3 so that may no longer be true.

Probably should download it again and see if it makes a difference.  May do that later.

---

### Post by ronacc on 2011-08-20
Thanks  RH I found your links in another thread ( gnome shell bug ) and following one of them compiled the git extensions , got the "alternative-status-menu" one working and figured out how to edit the .JS to get rid of everything but system settings  and power off . I tried the user-theme one but it fails on build so I need to find the problem there , I'll take a look at the others you link to also .

---

### Post by ronacc on 2011-08-20
installed the gnome-shell-frippery extensions , some of them anyway kept the previous shutdown menu that I had edited and I had to remove the bottom panel one as it was putting the bottom panel on the top and covering up the top panel , something must have changed since they were built .

---

### Post by jerrylamos on 2011-08-20
> **mc4man said:**
> The indicator is only for unity*, and presently does have everything but a restart option which is inc. on the shutdown box
Gs uses as Harry described, nothing for ubuntu to do, (change) there

I beg to differ.  On three of my test pc's, tower, 2 notebooks, the indicator at the top right of the screen on Oneiric Unity-3D i386 updated to 20 August:

Doesn't do anything at all!.

It used to.  It's busted.

Back to the command line....

Jerry

p.s.: at least it doesn't hang xorg like the Ubuntu Start button does when I type in:
sys
I entered launchpad bug #830319 for that one.

---

### Post by mc4man on 2011-08-20
> **jerrylamos said:**
> I beg to differ.  On three of my test pc's, tower, 2 notebooks, the indicator at the top right of the screen on Oneiric Unity-3D i386 updated to 20 August:

Doesn't do anything at all!.

It used to.  It's busted.

Back to the command line....

Jerry

p.s.: at least it doesn't hang xorg like the Ubuntu Start button does when I type in:
sys
I entered launchpad bug #830319 for that one.

Don't know about that - it's worked in all my installs for quite some time now, do a fresh one each weekend after each week's upgrades
Right now on a new 08/20 just installed, the indicator-session works just fine

---

### Post by cariboo on 2011-08-20
@jerrylamos

All three of my installs, my netbook from the tool-chain upload, my moldy-oldy install from July and the fresh install from Aug 18 all have the shutdowen option in the session-indicator. The only strange thing I see is the icon on the July and fresh installs.

---

### Post by mc4man on 2011-08-21
The session icon should have changed with an upgrade(s) the other day, forget which (ubuntu-mono was one, there was another
screen is what I had then after the upgrades and also have in fresh install today
(had a bug on the computer icon where it was marked invalid saying new icons were on the way ..

---

### Post by cariboo on 2011-08-21
I've had the proper icon on my netbook for a couple of days, I've done updates twice today, on my older install, but haven't rebooted yet. I haven't updated the fresh install yet, and probably won't until tomorrow.

---

