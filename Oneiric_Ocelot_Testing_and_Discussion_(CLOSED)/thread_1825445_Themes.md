---
title: "Themes"
date: 2011-08-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by tad1073 on 2011-08-15
Where is the theme manager for gnome shell?

---

### Post by P-I H on 2011-08-15
It is called Tweak Advanced Settings.
If you install with Synaptic, search for "gnome-tweak-tool"
If you install with Software Center, search for "Tweak Advanced Settings".

---

### Post by cariboo on 2011-08-15
> **tad1073 said:**
> Where is the theme manager for gnome shell?

According to the gnome devs, you don't need to change your theme. :)

---

### Post by SushiR on 2011-08-15
> **cariboo907 said:**
> According to the gnome devs, you don't need to change your theme. :)

According to the gnome devs you don't have to change anything, because the devs are always right and know better than you... ;-D

---

### Post by Harry33 on 2011-08-15
Well it is somewhat funny that the once very used tool (you know it used to be Appearance) to change themes etc. is called a tweaking tool. :guitar:

---

### Post by edujose on 2011-08-15
Be vary that when changing theme under Unity, windows' borders don't get the new appearance until you log out and then login again. Maybe they change inmediately under Gnome Shell (haven't tried in it).

Speaking of Gnome-tweak-tool, why did they put the picture of a robot head full of hardware? Is it to scare normal users away? :)

---

### Post by tad1073 on 2011-08-16
got it....some themes widow borders do not activate even though they are installed.

---

### Post by VinDSL on 2011-08-16
> **cariboo907 said:**
> According to the gnome devs, you don't need to change your theme. :)
I agree.  Users needn't change the theme!

What's wrong with the default, anyway?

Resistance is futile...  :D

---

### Post by VinDSL on 2011-08-16
> **edujose said:**
> Speaking of Gnome-tweak-tool, why did they put the picture of a robot head full of hardware?
Oh, is that still around?

That was from the re-education camp seminars, last winter.

You can change that, if you want.

I prefer the woodpecker with a cigar, from the LAU Jbeil meetings.

---

### Post by madjr on 2011-08-16
just like ubuntu decided not to follow the crazy path of gnome-shell, they will also need to add some tool to change the theme in the default install...

i wonder if they are working on it.

i know they are working on re-adding some screen saver functionality and lock screen, but changing themes can be just as important, specially for accessibility.

i personally cant live without my dark themes..

---

### Post by Harry33 on 2011-08-16
Not giving an opinion whether Unity or Gnome-shell is following a crazy path,
I find it just as important as to change the themes, to be able to modify or adjust the current theme.

---

### Post by madjr on 2011-08-16
> **Harry33 said:**
> Not giving an opinion whether Unity or Gnome-shell is following a crazy path,
I find it just as important as to change the themes, to be able to modify or adjust the current theme.

well it wasnt ubuntu's idea to get rid of the theme tool...

seems the current gnome3 devs dont want people to change their themes.

hopefully we'll see a fix for this in oneiric

---

### Post by edujose on 2011-08-16
> **madjr said:**
> well it wasnt ubuntu's idea to get rid of the theme tool...

seems the current gnome3 devs dont want people to change their themes.

hopefully we'll see a fix for this in oneiric

Hope so. It would be great if Gnome Shell devs do it, but I'm not very optimistic about that.

So more work for Unity devs.

---

### Post by jbicha on 2011-08-16
I vote for gnome-tweak-tool but somebody needs to write the theme panels for Unity.

Also at the moment, gnome-tweak-tool has a hard dependency on gnome-shell. It will have to be able to dynamically check whether things like gnome-shell or Unity are installed before making a failed attempt to read their gsettings.

---

### Post by jbicha on 2011-08-16
gnome-tweak-tool or any configuration panel won't be included by default in Oneiric though as it's too late for that. There's very little room on the CD and Design may not like a tweak tool that's too powerful/confusing on the main CD. And there isn't any tool that's ready yet anyway.

---

### Post by edujose on 2011-08-17
Thanks jbicha for your analysis and thoughts.

Yes, it's feature freeze so no time to refurbish gnome-tweak-tool to not bring Gnome Shell with it. Better for 12.04.

I would just include a point in release notes of oneiric about please installing Gnome-tweak-tool to change themes easily (it didn't fit on the live CD for space reasons).

<humor>
Anyway this theme-changing thingy is just for nuts with nothing better to do, so who cares? Have a life! :p :p
</humor>

---

### Post by madjr on 2011-08-17
> **edujose said:**
> Thanks jbicha for your analysis and thoughts.

Yes, it's feature freeze so no time to refurbish gnome-tweak-tool to not bring Gnome Shell with it. Better for 12.04.

I would just include a point in release notes of oneiric about please installing Gnome-tweak-tool to change themes easily (it didn't fit on the live CD for space reasons).

<humor>
Anyway this theme-changing thingy is just for nuts with nothing better to do, so who cares? Have a life! :p :p
</humor>

probably what the gnome3 devs thought...

Linus am with u!!

---

### Post by vulfgar on 2011-08-20
To be able to change theme is an **essential** feature. We are many who doesn,t have perfect vision, It's f.e. almost impossible to see which icons are showing in dash because the background is to transparent and it was even worst befor I managed to get rid of the blur, that made my eyes ache.  I don't understand why it's not possible to change the transparancy in ccsm för dash background, when you can change it for panels.

If anyone has a trick to change that, editing conf-files or something like that, I'll be happy if you'd share that.

---

### Post by cariboo on 2011-08-21
Gnome-tweak-tool allows you to select several accessibility themes. Check out the screenshot.

---

### Post by jbicha on 2011-08-21
You can also set the accessibility theme from System Settings>Universal Access. Click the contrast drop-down.

---

### Post by t.rei on 2011-08-21
That screenshot confuses me - I never ever had the ambiance window border working in gnome-shell, I think.

hey, I just got it working - after looking at .xsession errors I found that the <shadow> and the <padding> tags where the culprit.

So I made a copy of Ambiance and removed those lines.

---

### Post by vulfgar on 2011-08-21
> **cariboo907 said:**
> Gnome-tweak-tool allows you to select several accessibility themes. Check out the screenshot.

Nice of you,:) but thats not the problem. Themes doesn't change the style in dash. Most of all I would like to get rid of the transparancy or at least make it less transparant. It's also irritating that dash change colors by itself sometimes. A very bright red or blue color doesn't improve usability and that together with the transparancy makes it completely useless. Only way to start program is to have a terminal open at all times and give commands, but thats hardly user-friendly.

---

### Post by mc4man on 2011-08-21
> **vulfgar said:**
> Nice of you,:) but thats not the problem. Themes doesn't change the style in dash. Most of all I would like to get rid of the transparancy or at least make it less transparant. It's also irritating that dash change colors by itself sometimes. A very bright red or blue color doesn't improve usability and that together with the transparancy makes it completely useless. Only way to start program is to have a terminal open at all times and give commands, but thats hardly user-friendly.
There should be some change at some point to the dash blur/trans deal, here I disable the blur so I can use a transparent panel.
When you do that you see that the dash is actually completely transparent.
For the moment have taken to opening dash over a dark window, in my case a cobalt blue gedit
Atm the dash/lens have so many issues that not too useable anyway

---

### Post by tajreed on 2011-08-21
and users/groups in Unity. May need groups to make sure the user is checked as a user of vbox. I hope they're not gone for good.

---

### Post by jerrylamos on 2011-08-21
> **tajreed said:**
> and users/groups in Unity. May need groups to make sure the user is checked as a user of vbox. I hope they're not gone for good.

ubuntu still "advertises" customizing ubuntu for yourself, and does have ubuntu, lubuntu, xubuntu, kubuntu, ...

Either the "appearance" settings are gone for ever or they are broken.  No word I've seen in any of the developer announcements.

I do "Clearlooks" when available, but not in Oneiric as it sits.

I bounce back and forth between Oneiric and Narwhal.  So far I don't see any advantage to Oneiric.  I run it just to report bugs.

Jerry

---

### Post by RJ12 on 2011-08-21
Because of the Background of Gnome 3... I fear that they have been removed. Ubuntu Developers might make an Applet to change it though... this is what I hope. Otherwise... we have lost a lot of customization!

---

### Post by vulfgar on 2011-08-21
> **mc4man said:**
> ...
Atm the dash/lens have so many issues that not too useable anyway

I guess yo'r right, I suppose I've got to be patient, but it's not easy... :p

---

### Post by wedderburn on 2011-08-21
you can edit themes using the dconf-editor, look under org.gnome.desktop.interface for the settings.

---

### Post by cariboo on 2011-08-21
Merged two similar threads.

---

### Post by arpanaut on 2011-08-21
So, where does this leave an Ubuntu user who for whatever reason refuses to or does not want to install genome-shell?

For example, I try to test development releases for the most part "as is" other than codecs and prop. drivers to get an out of the box feel for what is coming. CCSM being one exception because I can't stand the default sizes of icons in the launcher(wish I could do the same in dash) but I think this is a bug too. Why should it be necessary to install extra packages to configure minor appearance properties?

I see this as a major OOB deficiency with the development of Oneric. 
Why should I be required to install gnome-shell and all it's dependencies, just to change themes and appearance.  At this point I have no desire or intention of running gnome-shell so why have it installed?

Just seems like a serious lack of usability in the default installation.

---

### Post by cariboo on 2011-08-21
@arpnaut

Create a bug report and ask that the gnome-shell dependencies

@tajreed

Click the power button and select System Settings, then click the Users under system, click the unlock icon should allow you to change permissions.

---

### Post by wedderburn on 2011-08-22
> **arpanaut said:**
> So, where does this leave an Ubuntu user who for whatever reason refuses to or does not want to install genome-shell?

For example, I try to test development releases for the most part "as is" other than codecs and prop. drivers to get an out of the box feel for what is coming. CCSM being one exception because I can't stand the default sizes of icons in the launcher(wish I could do the same in dash) but I think this is a bug too. Why should it be necessary to install extra packages to configure minor appearance properties?

I see this as a major OOB deficiency with the development of Oneric. 
Why should I be required to install gnome-shell and all it's dependencies, just to change themes and appearance.  At this point I have no desire or intention of running gnome-shell so why have it installed?

Just seems like a serious lack of usability in the default installation.

Well thats the problem when a distro doesn't follow upstream, but you can grab dconf-editor its not the most newbie friendly but it does work and with the minimal dependencies.

---

### Post by tajreed on 2011-08-22
Caribou-as far as I can tell, there is no place in "User Accounts" to fiddle with group permissions or to add users to groups.

---

### Post by cariboo on 2011-08-22
> **tajreed said:**
> Caribou-as far as I can tell, there is no place in "User Accounts" to fiddle with group permissions or to add users to groups.

You're right, more gui configurations that the gnome devs have taken away. Fortunately you can still do it from the command line. :)

---

### Post by vulfgar on 2011-08-22
> **wedderburn said:**
> you can edit themes using the dconf-editor, look under org.gnome.desktop.interface for the settings.
Hmm, can't find a way to edit dash, though, And it's dash that needs tweaking.

---

### Post by edujose on 2011-08-22
Surely there will be some GUI options coming in for changing dash looks (maybe in CCSM). Don't know when, hope rather soon.

All in all, things are coming together slowly because of several factors:

1. The transition from GTK+ 2 to GTK+ 3 - New Gnome Shell uses new GTK+ 3 too. It affects all distros providing Gnome, including Ubuntu. Ubuntu, in turn, replaces Gnome Shell with Unity (ported from GTK+ 2 to GTK+3) but uses the rest of the Gnome environment: Gnome programs, config utilities and so on.

2. The new Gnome Shell - Its functionality is still catching up in relation to previous Gnome 2.x, with some things still unavailable. So things missing in Shell are also missing in Unity.

3. Unity is an evolving DE (Desktop Environment) - Functionality is being added or changed, looks and usability being improved, etc. All this together with the port to GTK+ 3. Gnome Shell is also evolving and adding functionality -well, removing and adding, uh, whatever- :)

Sooo, things will come. If not for Oneiric, for next version. Meanwhile we can file bugs for missing things (like config options for dash, or users and groups options).

Like cariboo said, there is also the command line, though no one wants to fiddle with dconf-editor or 'useradd' command (I sometimes do but it's not my ideal for day-to day use :) )

---

