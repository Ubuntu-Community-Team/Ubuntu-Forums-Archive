---
title: "Gnome Classic &amp; Gnome Classic - no effects gone?"
date: 2011-07-31
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by walt.smith1960 on 2011-07-31
I've been using updated 11.10 on a semi-regular basis.  I've been using Gnome Classic or Gnome Classic - no effects.  The latter provided an experience much like Gnome 2 and I was thinking that would be a nice alternative on low powered machines.  I updated today and those options are gone. Gnome-panel was removed and cannot be installed -- it appears to conflict with Unity 2D.  Only Ubuntu, Ubuntu 2D and Gnome (3) are shown on the startup screen.  Are Gnome classic and its sibling gone, or am I not seeing them because I have adequate graphics capability to use Ubuntu or Gnome 3?  If they're gone, I hope it's temporary.

On the plus side it appears that Gnome 3 shell is finally getting some love.  It seems to be functional now.  I may uninstall Unity 2D just to see what happens.

Edit:  It's back!!-see below

---

### Post by ELD on 2011-07-31
They are gone, the only thing like it now is Gnome 3's fall back mode.

---

### Post by kansasnoob on 2011-07-31
> **ELD said:**
> They are gone, the only thing like it now is Gnome 3's fall back mode.

Doesn't the package "gnome-session-fallback" work anymore?

BTW I gave up on it after gnome-panel version 3 showed up, just made me want to cry.

---

### Post by walt.smith1960 on 2011-07-31
It's back!!  Going to Synaptic and enabling "gnome-session-fallback" did it.  Gnome-panel by itself would not install.  I have lost the "desktop" icon in the lower left of the screen, there's probably a way to get that back.  it will be nice if this option remains available for the Unity & Gnome 3 haters that want to stay with mainstream Ubuntu.  There is a delay drawing screens (bars, icons etc.) when switching between D.E.s  It seems like waiting a few seconds then issuing the "3 fingered salute"(ctrol-alt-delete) helps. Simply leaving it alone for a minute or two may work too.

---

### Post by hugmenot on 2011-08-02
But you don't have any indicators now, right?

indicator-applet needs to get ported to gnome-panel3 and gtk3. ASAP I hope.

---

### Post by jbicha on 2011-08-02
gnome-panel is vanilla upstream (in other words, we aren't patching gnome-panel like we used to). As far as I know, getting indicators working with it is not a priority.

Gnome Shell does not need "indicators" (application and system status menus as I prefer to call them) since they already have a status area in the top bar that works well with the keyboard. Application status menus show up in the messaging tray.

---

### Post by hugmenot on 2011-08-03
I’m not talking about Gnome Shell. I talking about gnome-panel.

I’m sure there are quite a few people who are still most comfortable with their accustomed classic gnome-panel setup and they are not ready yet to switch to a new paradigm, be it Unity or Gnome Shell.

Without indicators gnome-panel is mostly unusable because of all the patching that goes on in other important packages, like NetworkManager applet. It’s not possible to run nm-applet in the notification area anymore, this was patched out to make nm-applet exclusive to indicators. The same holds with sound-indicator and gnome-power-manager.

As far as I can tell the only porting effort needed to make libindicator and indicator-applets gnome-panel 3 compatible is a few API changes. 

If this isn’t achieved having gnome-panel in the archive at all is pointless. And forcing people to adopt Unity is not a good approach I think. 

Why did they do all that effort to put indicators on the gnome-panel only to leave that stuff working for one or two releases?

---

### Post by jbicha on 2011-08-03
Networking, sound, and power all still work in Gnome Fallback in Oneiric. It's definitely not as nice as the indicators or the Gnome Shell implementation.

It's not a vast conspiracy to force people to adopt Unity. Personally I've been using Gnome Shell this month because it works well in Ubuntu & does what I want. However, there are only a limited number of people working on Ubuntu's software but I don't know any of these people who actually use Gnome Fallback as their primary desktop. And there are a lot of other important issues and getting other new software ready, which has meant that as far as I know no one has bothered trying to get indicators working in Fallback. Gnome never accepted the Ubuntu patches and it's a lot of work to maintain invasive patches like these.

Xubuntu looks a fair amount like Gnome 2 so you might look to use them if you want the latest Ubuntu foundation but without Unity or Gnome Shell.

---

### Post by hugmenot on 2011-08-03
I forgot to mention the appmenu, which I foun the biggest improvement in the last cycle an it’s lost now.

I don’t have nm-applet nor a sound icon here.

---

### Post by cariboo on 2011-08-03
I've got gnome-session-fallback running here with all the normal icons in the system tray, although network-manager doesn't have the proper icon, see the screenshot. Alt-right-click works too.

---

### Post by cariboo on 2011-08-03
@hugmenot

Your last two post didn't belong here, I moved them to the Cafe.

---

### Post by hugmenot on 2011-08-03
```
In general, we're not trying to drop it but it's not a priority.  In
Oneiric the gnome-panel API changes slightly and the indicator-applet
needs to be migrated.  I hope to get to fixing it, but I'm not 100% sure
if I will.

                --Ted
```
I hope they get to it.

Yanking people out of their comfortable environs is not the way to go. Gnome 3 and it&#8217;s apps aside from Gnome Shell have some nice improvements. Unity as well (indicators, appmenu and so on). But the paradigm shift is a hard sell for many.

Since, as Ted says it&#8217;s doable, I see no reason to abruptly deprecate gnome-panel.

---

### Post by yaddoshi on 2011-08-04
I decided to give Alpha a try, and all seemed well until I installed proprietary ATI drivers, resulting in booting to a black screen until I went into recovery mode and uninstalled them.  I had previously been playing with Gnome 3 Shell in 11.04 using the developers PPA and had trouble with using proprietary drivers there also.  I like to play games like WoW in LINUX so this is a bit of an issue for me.  It's good to know there are currently packages available to switch back to Ubuntu Classic (no effects) because that's really necessary in order for the games to run correctly.  At this time I'm not planning on upgrading from 11.04 until the proprietary drivers boot issue is resolved, however.

---

### Post by dino99 on 2011-08-04
cant get several workspaces now when logged as gnome-classic, even via dconf :(

---

### Post by walt.smith1960 on 2011-08-04
> **dino99 said:**
> cant get several workspaces now when logged as gnome-classic, even via dconf :(

I wonder why? I set mine for 3 workspaces and just tried them -- they work fine. 2 instances of Firefox and one of Libre Office writer.  Just right click on the single workspace and select 'preferences' 1 row 3 workspaces. I don't remember if I'm logged on as Gnome Classic or Gnome Classic -no effects though.

---

