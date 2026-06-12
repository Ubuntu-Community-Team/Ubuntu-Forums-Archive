---
title: "Nvidia drivers, error message on restart"
date: 2015-02-18
forum: New to Ubuntu
---

### Post by will65 on 2015-02-18
Hi again guys,

I attempted to install Nvidia's 3.46.35 graphics drivers using ```
sudo apt-get install nvidia-346
```Clearly this was something I should have left until I understood Ubuntu's command lines better, because now I've got [this error message]("http://i.imgur.com/CkOm9Q6.png") popping up everytime I leave Ubuntu, and [also this one]("http://i.imgur.com/PmWaVO0.png") before Ubuntu loads up. Does anyone know what it means, and how to fix it? Apologies for the potato quality, the message flicks up for less than a second, and my stupid Samsung monitor feels the need to remind me of my resolution whenever I boot my computer up.

If I'm honest, the whole purpose of dual booting Ubuntu was really so that I could play the x64 version of Kerbal Space Program without getting CTDs every few minutes with mods installed. The Nouveau driver doesn't seem up to the task, and when I selected some of the additional drivers it left me with ugly aliasing, even with the graphics settings maxed. I can't see any Linux version of Nvidia's Catalyst Control Centre or GeForce Experience anywhere either.

Not gonna lie, I'm pretty disappointed that installing things seems to require a string of command lines. Doesn't anyone write installers for Linux, or is it just kinda assumed that if people go to the trouble of using a non-Windows OS they'll be willing to put up with time-consuming and complicated installations? As a new user who just wants to play some games, getting Ubuntu working properly is turning out to be very frustrating :(

---

### Post by steeldriver on 2015-02-18
Can you get to a CLI "virtual  terminal" by pressing Ctrl-Alt-F1 or Ctrl-Alt-F2 etc.? Can you boot into recovery mode?

FYI there already is a graphical installer for proprietary drivers - if you'd just gone to the dash and typed 'Additional Drivers' you'd have seen it, and it would have told you what proprietary driver version(s) had been tested on and were recommended for your system.

---

### Post by grahammechanical on 2015-02-18
> [COLOR=#000000]I can't see any Linux version of Nvidia's Catalyst Control Centre or GeForce Experience anywhere either.[/COLOR]

I think that Catalyst Control Centre is for AMD/ATI card video drivers. When we install an Nvidia Driver through Additional Drivers we also get an Nvidia X Server Settings utility as well. When I need to find it I just open the Dash and Type Nvidia.

I have never installed a proprietary video driver that I downloaded from the web site. I always use Additional Drivers. If we want to use what we think is the latest and greatest from Nvidia or AMD then we have no choice but to use the terminal because those drivers have not been tested by the Ubuntu developers and they are not in the Ubuntu repositories.

From my first install of Ubuntu more than 7 years ago installing a proprietary video driver has been as easy as one or two clicks in a GUI utility. But Ubuntu is also Linux and that means that we can always choose to do things the hard way.

Those error messages are nothing much to worry about. The ones that you see when shutting down are normal Linux messages that might normally be hidden by a splash screen. The one you see when loading does not stop Ubuntu from loading and working as normal. I run the development version of Ubuntu and I see that "broken pipe" message from time to time.

If you want to be mystified even more, then read this.

[http://unix.stackexchange.com/questions/84813/what-makes-a-unix-process-die-with-broken-pipe](http://unix.stackexchange.com/questions/84813/what-makes-a-unix-process-die-with-broken-pipe)

Ubuntu sits on top of Linux and it is normal for Linux to print messages to the screen. Some messages are "doing this" and "done that" type messages. Some are error messages. Usually they are hidden by a splash screen but as the loading of Linux/Ubuntu switches video modes when it activates a video driver  or when it logs Ubuntu on to Linux to load the desktop we sometimes get a glimpse of what Linux is working on.

Regards.

---

### Post by will65 on 2015-02-19
> **steeldriver said:**
> Can you get to a CLI "virtual  terminal" by pressing Ctrl-Alt-F1 or Ctrl-Alt-F2 etc.? Can you boot into recovery mode?

Yes, I've managed to get into the virtual terminal, but it won't let me login. It asks for a username (it's just 'Will') and then after pressing enter, it asks for my password. However, when I do that it just repeats the login request. It's quite infuriating.

> FYI there already is a graphical installer for proprietary drivers - if you'd just gone to the dash and typed 'Additional Drivers' you'd have seen it, and it would have told you what proprietary driver version(s) had been tested on and were recommended for your system.

I tried a few of them and they still left me with annoying aliasing (I did mention this in my first post). I wouldn't have attempted to install a newer driver otherwise, but I guess I've still got a lot to learn.

> **grahammechanical said:**
> When we install an Nvidia Driver through Additional Drivers we also get an Nvidia X Server Settings utility as well. When I need to find it I just open the Dash and Type Nvidia.

Tried that last night. The X Server Settings had practically no settings other than display resolution, and I couldn't see an advanced mode or anything similar.

> Those error messages are nothing much to worry about. The ones that you see when shutting down are normal Linux messages that might normally be hidden by a splash screen. The one you see when loading does not stop Ubuntu from loading and working as normal. I run the development version of Ubuntu and I see that "broken pipe" message from time to time.

Well at least that's something I guess. I'll just ignore them for now.

---

