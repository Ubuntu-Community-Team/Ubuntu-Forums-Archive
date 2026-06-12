---
title: "Help configure mouse acceleration on Ubuntu"
date: 2021-01-22
forum: New to Ubuntu
---

### Post by satoshi-yoda on 2021-01-22
Good day :3

I am a PC user for about 20 years and a programmer for about 10 years, but only worked on Win and on MacOS so far.
At the moment I am considering moving to Ubuntu, which I successfully installed on a new PC few months ago (latest 20.04 version with all updates if that matters).
At the moment all works fine, except one thing that really blocks me to fully move from Windows: it's the ability to tweak the mouse acceleration I'm used to.

I googled A LOT about this. Mostly internets says "Just disable mouse acceleration, it is a bad feature", "It is a stupid thing, disable it, please", "How to disable mouse acceleration?".
Many of topics about mouse acceleration (I would say 90%) concerned about disabling it. Yes, that obstructs me from googling my problem (-_-")
Because that's not my case =) I want exactly opposite: to ENABLE mouse acceleration, because I worked with it for many many years, and completely used to it.

Internets frequently says that mouse acceleration enabled by default on Ubuntu.
Maybe I am getting it wrong, or I mean something else by "mouse acceleration", but in my opinion it is NOT enabled on my config.
What do I want from my mouse: I want that when I move it quickly physically it travels faster on monitor, and otherwise.
For example: when I move it slowly from one corner of the screen to another, it takes about 20cm on the table to cross the screen, and when I do it fast &#8212; it only takes 10cm on the table, that is what I want. But at the moment it does not matter how I move my mouse, it always takes, let's say, 15cm to cross the screen.

On Windows there is 5 tools that I used for it:
[LIST=1]
[*]Default Windows checkbox in mouse settings &#8212; it does not allow any configuration, just on/off. It is bad, but it kinda worked for me. But when I moved to 4k monitor with 200% ui scale it became really bad, because it starts to "activate fast speed to early".
[*]github.com/TemporaryName/PointerSpeedSetter &#8212; tool for customize windows acceleration curve.
[*]Mouse drivers &#8212; I am using Razer Abyssus 2014 at the moment, their software allows acceleration to be set from "0" to "10". Not the best choice, because that software has some issues, and "0" to "10" suffers from lack of understanding how exactly does it calculate stuff.
[*]Beautiful Povohat's and KovaaK's free-to-use mouse acceleration drivers &#8212; Guys really did great job to popularize mouse acceleration and understanding how brilliant it is if you configure it properly. Their software allows user to build a custom curve (from several available templates), which tells what speed mouse will get at different physical velocity. It has some issues with anti-cheat software for some competitive shooter games lately, but it does not troubles me personally.
[*]mouseacceleration.com &#8212; payed tool similar to Povohat's, but can help design any bezier curve, not only some templated variants.
[*](not relevant to my problem, but helpful to mention it) &#8212; Some competitive games, like Quake Live or Diabotical contains their own methods for configure in-game mouse acceleration, and many pro-gamers use it. That ideas actually helped Povohat's to build some curve templates for his intercept driver.
[/LIST]

On MacOS I was happy with default config, does not change anything, it worked just fine. Maybe just some tweaks in mouse speed for different actual devices.

ANY of that methods would be fine for me, if they were available on Ubuntu... But:

What I tried to do on Ubuntu:
[LIST=1]
[*]I tried to configure acceleration with default UI and with some help of the dconf. As I understand from internets Ubuntu default acceleration works as a curve that contains 2 flat lines and a step between them: one mouse speed for slow movement, and another for fast movement. It would be fine for me, but it does not work! Does not matter how fast/slow I move my mouse &#8212; the speed is always the same (yes, I can change that speed in settings), maybe because my mouse has 1000Hz 3500DPI and I have 4k monitor using 200% ui scale, which causes threshold to trigger to early, I don't know... And I don't know on which part of the curve I am: on the slow one, or on the fast one. From general mathematical understanding that kind of curve can be defined with 3 float parameters: (low-speed, high-speed, threshold) or (speed, fast-speed-multiplier, threshold) or whatever, it does not matter until there is 3 parameters. But default UI offers only one parameter, which is I don't know what, but looks like fast-speed-multiplier. There is some linux configs that offers 2 parameters, like that wiki.archlinux.org/index.php/Mouse_acceleration I understand that is not Ubuntu, but I am talking about that, there is still 2, not full 3 parameters. But, yes, 2 is better that 1 (^_^")
[*]I tried to get Razer drivers for Ubuntu. I did not found proprietary drivers. There is openrazer + some GUI, but none of them offers mouse acceleration option, as I see, maybe I am wrong.
[*]I googled for some third-side tools similar to 2. 4. 5. variants from windows, but did not find any...
[*]I learned about ways to write my own scripts to do that, but it is a long way...
[/LIST]

So, my questions (prioritized) is:
[LIST]
[*]Can I configure default ubuntu mouse acceleration threshold that way, so I can actually see it? Perfectly a way to set 3 parameters, or at least 2? But not just one.
[*]Is there some third-side tools that I missed?
[*]Maybe there is some mouse manufacturers which provides drivers with mouse acceleration settings? I would gladly buy it.
[*]Any guides to custom script my way through it?
[/LIST]

Thanks for reading =)
Sorry for a lot of text, but that problem happens to be really keystone for me, so I tried to describe it thoroughly.

---

### Post by simon-webb on 2021-01-22
Hi. If the "adaptive" acceleration profile in gnome-tweaks doesn't give you something close enough to what you want, things could get tricky because GNOME seems to be overriding the other methods for controlling this stuff (I can't see anything on that Arch wiki page that's Arch-specific, but it's not working on GNOME because this desktop is overriding that stuff with its own settings). So, assuming you want to stay on GNOME, without hacking the default desktop fairly substantially you might be limited to the gsettings options that it makes available, which (from gsettings list-keys org.desktop.gnome.peripherals.mouse and gsettings range org.desktop.peripherals.mouse accel-profile and speed respectively) look to be just the acceleration profiles exposed by the gnome-tweaks tool, and the speed setting exposed by the control in the standard GNOME mouse settings dialog.

[Edit]I've just realised that you may not have seen gnome-tweaks as it's not in the default install. The magnifying glass in the top left corner of the Ubuntu Software GUI will enable you to search for and then install gnome-tweaks...otherwise it's just```
sudo apt install gnome-tweaks
gnome-tweaks
```in a terminal.

---

### Post by satoshi-yoda on 2021-02-20
Thanks for the help! :3

> **simon-webb said:**
> So, assuming you want to stay on GNOME, without hacking the default desktop fairly substantially you might be limited to...
Do I have other options besides Gnome, assuming I want to stay on Ubuntu?

> **simon-webb said:**
> I've just realised that you may not have seen gnome-tweaks as it's not in the default install.
Yes, I already tried gnome-tweaks earlier.
There are 3 available options for Acceleration Profile: Adaptive, Default, Flat. With first 2 mouse speed is **constant** and fast, with Flat it is **constant** and slow. So, no luck here =(

---

### Post by daniewicz on 2021-02-21
You could install kubuntu which uses KDE instead of Gnome.

---

### Post by CatKiller on 2021-02-21
> **satoshi-yoda said:**
> Do I have other options besides Gnome, assuming I want to stay on Ubuntu?

[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)

I would also recommend Kubuntu.

As well as the official flavours, there are community-made ones, and you can just install additional desktop environments even if there isn't a maintained flavour for it. It gets messy if you have too many at once, though, so don't just install them all.

---

### Post by DuckHook on 2021-02-21
> **satoshi-yoda said:**
> …Do I have other options besides Gnome, assuming I want to stay on Ubuntu?…
Please see the link in my sig: The Best 'buntu Flavour.

---

### Post by mastablasta on 2021-02-22
i have a Chinese "gaming" mouse (2 actually), local brand added on them so overall quite generic. it has that button where you can change the DPI resolution. similarly i have a medium size Kingston mouse. same with the little button on top. i use Kubuntu (KDE) on all desktops and mouse works just as you want it. this is quite annoying when you play CS:GO or other FPS games, because you never know how much you need to push the mouse to aim in proper spot. so i turn on RAW input in games and use the mouse acceleration feature on desktop. it gives better control over cursor and if i need slower movement i can quickly switch to it by lowering the laser DPI of the mouse.

---

