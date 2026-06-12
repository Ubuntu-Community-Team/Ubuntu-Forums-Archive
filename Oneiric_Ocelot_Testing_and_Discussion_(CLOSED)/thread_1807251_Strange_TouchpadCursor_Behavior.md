---
title: "Strange Touchpad/Cursor Behavior?"
date: 2011-07-18
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by moore.bryan on 2011-07-18
Every now and again, my cursor will lag in its response to my touchpad... I've checked all my mouse settings and sensitivity is as high as it can go, but I still have the problem. It seems the cursor is "losing" my touchpad. Any ideas where I can start debugging this?

---

### Post by Cybie257 on 2011-07-18
I would start out by giving details about your laptop(???). Some laptops have had issues and there is a bios/firmware upgrade available. 

Also, be sure that it's not too sensitive as it could pick up your other fingers and cause it to 'appear' to lag when all it's really doing is fighting two separate inputs. I tend to do that without noticing and have the same problem until I realize I was getting lazy with my hand and letting another finger too close to the pad..

-Cybie

---

### Post by christopher.wortman on 2011-07-18
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

### Post by moore.bryan on 2011-07-18
> **Cybie257 said:**
> I would start out by giving details about your laptop(???). Some laptops have had issues and there is a bios/firmware upgrade available.
No bios update for me... it's an Asus 1005HA, the one in my signature.

> **Cybie257]Also, be sure that it's not too sensitive as it could pick up your other fingers and cause it to 'appear' to lag when all it's really doing is fighting two separate inputs. I tend to do that without noticing and have the same problem until I realize I was getting lazy with my hand and letting another finger too close to the pad..

-Cybie[/QUOTE]
Thanks for this too, Cybie... I thought about this so paid attention for about 15/20-minutes and found it popped-up most commonly when I wasn't using the touchpad for a while, which made me wonder is utouch was "losing capture" on the touchpad.

[QUOTE=christopher.wortman said:**
> [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)
Thanks for this, as well... first place I went.

---

### Post by mc4man on 2011-07-18
This is due to an upstream change in gnome-settings-daemon
The previous for some time was to have a 0.5 sec 'lock' on touchpad after using the keyboard.
For the most part the 0.5 was unnoticeable.

Some people and their hardware have issue's with the 0.5 sec time, so it was upped to 2 sec's which is quite noticeable and personally can't stand. 
For myself have reverted gsd back in a rebuild - otherwise you could disable the lock in the mouse settings

Bug report 
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/801763](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/801763)

---

### Post by moore.bryan on 2011-07-18
> **mc4man said:**
> This is due to an upstream change in gnome-settings-daemon
The previous for some time was to have a 0.5 sec 'lock' on touchpad after using the keyboard.
For the most part the 0.5 was unnoticeable.

Some people and their hardware have issue's with the 0.5 sec time, so it was upped to 2 sec's which is quite noticeable and personally can't stand. 
For myself have reverted gsd back in a rebuild - otherwise you could disable the lock in the mouse settings

Bug report 
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/801763](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/801763)
That's **exactly** the problem! I read through the bug thread, but didn't really see a valid reason for the 2-seconds! That's a relatively insane amount of time.

I shall mark this as solved... thanks, mc4man!

---

### Post by mc4man on 2011-07-18
> but didn't really see a valid reason for the 2-seconds! That's a relatively insane amount of time.
At first I didn't either, but looking a bit past that report can see where _possibly_ it makes sense. I'd think those most affected by the 0.5 have large macbook style touchpads and can type fast. (the complete opposite of here.

Ultimately you have people that will be annoyed by the 2 sec., a lot who don't care either way and people affected by the 0.5
So it's likely affected will trump annoyed.

While I could probably just disable the lock and never be affected, the rebuild is quite easy and it's just a single edit, changing 2.0 to 0.5

---

### Post by moore.bryan on 2011-07-19
> **mc4man said:**
> So it's likely affected will trump annoyed.
Reluctantly, I agree.

[QUOTE=mc4man]
While I could probably just disable the lock and never be affected, the rebuild is quite easy and it's just a single edit, changing 2.0 to 0.5[/QUOTE]
Where'd you find the rebuild instructions?

---

### Post by mc4man on 2011-07-19
Pretty straightforward - 
You can get the build-deps a couple of ways, mk-build-deps allows you to easily remove the dev packages but for now will just use apt-get, myself am always (re)building something so don't care about carrying dev packages
Plus g-s-d will likely update several times over the course of O's dev

Create a build folder and cd to, something like this
```
mkdir gsd_build && cd gsd_build
```

Then
```
sudo apt-get build-dep gnome-settings-daemon
```
just in case not installed
```
sudo apt-get install fakeroot
```
```
apt-get source gnome-settings-daemon && \
cd gnome-settings-daemon-3.1.3
```

Leave the terminal open and browse to and open in text editor, for such a simple edit no need to do as a patch

gnome-settings-daemon-3.1.3/plugins/mouse/gsd-mouse-manager.c
Enable line numbers and scroll down to line 536, change back to 0.5 -  screen 1
Save

Your choice - if you build now it will build same package as is current, it will install as a re-install but will then be seen as upgradeable to the repo package. You can do this and be careful not to upgrade or you can up the new build slightly so only when g-s-d updates will you be notified.
For bug filing when g-s-d may be involved you'd want to leave at current package version, otherwise I'd up it

To up slightly - 
Open gnome-settings-daemon-3.1.3/debian/changelog
No need to create a proper new entry, just append the top line like this
gnome-settings-daemon (3.1.3-0ubuntu6[COLOR="Blue"]+nmu1[/COLOR]) oneiric; urgency=low
save
Back at the terminal
```
dpkg-buildpackage -rfakeroot -D -us -uc
```

When done just install the gnome-setting-daemon package as seen in screen 2, using gdebi is the easiest (not installed by default anymore

---

### Post by moore.bryan on 2011-07-19
Thanks for this... I'm trying it out with just disabling the disable touchpad choice and, apparently, I don't really ever have my palm swipe it while typing. Perhaps there will be a more elegant solution in the next few days; however, if I find my palms begin to get lazy, I'll recompile. 

Thanks, again, for these instructions!

---

### Post by mc4man on 2011-07-19
> Perhaps there will be a more elegant solution in the next few days
You could subscribe to the bug report and see where it goes, days no, weeks maybe..

---

### Post by moore.bryan on 2011-07-19
"Weeks," true... I'm always thinking devs work 24/7 and never need sleep. ;-)

---

