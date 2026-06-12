---
title: "Invoking diagnostics reports..."
date: 2021-03-25
forum: New to Ubuntu
---

### Post by Innernet on 2021-03-25
Good day to all.

What commands on the terminal yield detailed diagnostics of misbehaviors that can be interpreted hopefully by a plain user or by experts on the forum ?  Commands that would explore a vast variety of problems causing slowing and crashing in the last minutes of operation ?.

Continued slow performance has been suggested as insufficient RAM in other forum responses.  But come on, six minutes to boot, 2 minutes to load a browser ?  Am ready to crush my compfuser and buy a new one; but want to make sure it is a hardware problem.  [Compaq CQ57]  Tried Lubuntu + Opera.  Good for a few initial weeks, now degenerated to equally horrible performance.
10+ years ago, humble machines were very agile and fast with Ubuntu.  Now with newer versions the hard drive decides to do some gargling, fan to speed up and everything goes turtle speed. HOW to produce  a report of WHAT causes the drive to do whatever it is doing ?

The ideal report would show 'hard drive has being processing an indexing task the last 5 minutes'  Or 'A video is being downloaded in the background'  Or 'the CPU is too busy with some crap'  Or 'updates are being downloaded in the background' 
Noticed mostly after starting a session, slowing near freezing coincides with some downloading of something that ends several (~10?) minutes later with an active 'Software updates'  message " Updates are ready to install , do you want to install it now ?" _ I have settings to NEVER check for updates, never install automatically anything._  Well, it not only disobeys the setting but slows everything.  Seems it downloads the updates and assumes they will be installed by the user saving time as they are already downloaded.
That is very wrong.  I do not want checking for updates, much less assuming they will be installed.   Am an ultralight user. Can imagine it would be hell to do multitasking...

Can some expert confirm this ignoring of settings is happening ?  How to REALLY stop the software obsession to take control of a machine ?  I want my machine doing what I want, no automatic things.

---

### Post by ActionParsnip on 2021-03-25
reading the logs in /var/log is a good starting point

---

### Post by ActionParsnip on 2021-03-25
The system doesn't download anything without authorization by the user. The only thing downloaded in the background is the package lists to show that updates are available. Nothing more. This is the equivalent of running:
```

sudo apt update

```
This only checks for available packages, no software is updated with the above command

---

### Post by poorguy on 2021-03-25
Open terminal and copy and paste this command press enter and enter password if asked then close terminal and restart the computer.

```
 sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop  
```

Have a look at the **start up apps **and see what can be disabled on start up that isn't needed.

Can't say how much of a difference it may make or may not make however if you have 5 minute start up times then every little bit helps.


As for slow browser opening to many browser extensions will sometimes create that problem from my experience. I use **Ublock Origin **and **DuckDuckGo Privacy Essentials** and nothing else and my browser busts open PDQ.


Post some specs and lets see what's inside of that Compaq CQ57 before you crush it.


Lubuntu Manual.
[https://manual.lubuntu.me/stable/](https://manual.lubuntu.me/stable/)


Managing software and sources.
[https://manual.lubuntu.me/stable/4/4.3/software_sources.html](https://manual.lubuntu.me/stable/4/4.3/software_sources.html)

---

### Post by grahammechanical on 2021-03-25
> that can be interpreted hopefully by a plain user

Most unlikely! If you want to investigate CPU and RAM usage as well as internet download and upload rates then Ubuntu comes with System Monitor. Easy to understand because it is a visual representation. And then there is Psensor. Again it is quite easy to understand.

[https://wpitchoune.net/psensor/](https://wpitchoune.net/psensor/)

And then is top and htop. Not so easy to understand these utilities. But like the others they gives real time output.

[https://www.geeksforgeeks.org/top-command-in-linux-with-examples/](https://www.geeksforgeeks.org/top-command-in-linux-with-examples/)

[https://www.geeksforgeeks.org/htop-command-in-linux-with-examples/](https://www.geeksforgeeks.org/htop-command-in-linux-with-examples/)

I know we can set Ubuntu to never check for updates but I am not sure if that applies to security updates. I think that it would be most stupid to allow uses to disable checks for security updates.

If we have a slow internet connection the check for updates can slow the operating system down. I know that from experience. I have broadband through the telephone line and if there is interference on the line then upload speed drops significantly.

Regards

---

### Post by Impavidus on 2021-03-26
The best you'll get is something like: "Process X is consuming 30% of CPU capacity," or "Process Y is using 40% of memory," or "Process Z is downloading at 3300 kB/s on port 12345." The tool you use to get that kind of information doesn't know what processes X, Y and Z are actually doing. That follows from the modular nature of the UNIX world. Hopefully the processes have some sensible names, but even then it isn't straightforward.

Processes can start and stop child processes whenever they like, just as they can open and close windows whenever they like. A program that on first sight appears to have one task, may actually run several child processes for subtasks, whereas in other cases there may be on first sight several programs running, which actually are just a single process that has opened multiple windows. Processes may request and get more memory than is available, which is no problem as long as they don't actually use it; memory is sometimes shared among multiple processes and a lot of memory is used to cache disk access, which is used memory, but still available.

The tools **top** or **htop** may help. **free** can tell about memory usage.

Regarding those upgrades... If you set it to never check for upgrades, you have to do so manually. I would keep it on automatic. If upgrades are available, you will be notified (or they will be installed automatically, depending on your settings), both after an automatic and after a manual check for upgrades. After you checked for upgrades, the pop-up to install them will continue to appear until you have installed them, even if you never check for upgrades again. For security upgrades you can choose between notification only, automatic download or automatic installation. It seems you want notification only. For snap packages, upgrades are automatically downloaded and installed. I don't like snaps, so I don't have any. And yes, you can completely remove the update manager and always check and install upgrades yourself from command line, but you'll probably forget, so that's a bad idea.

FYI, I've got a decent, although somewhat older laptop and have it set to check for upgrades daily and notify me of upgrades immediately, both for security upgrades and others. But I've got a decent fibre-to-the-premises connection, so I'm not concerned by download speeds.

---

### Post by DuckHook on 2021-03-26
As others have noted, your expectations are not realistic. Or, at a minimum, they conflict.

[LIST]
[*]The reason that we have computers at all is to get them to automatically do things for us. Taking but one example: if we had to perform every step of the boot process manually, few would ever get to the point of using their computers.
[*]The issue then, is: how much is too much? Contrary to your wishes, the majority of complaints that we get from newbies on our forums is: "Linux/Ubuntu doesn't automate enough stuff for me. I want it to be brainless." Since everyone has a different idea of what is too much or not enough, the devs have no choice but to play god on this one. Therefore, if you want to run a prepackaged distro, you will have to live with whatever the devs decide, which usually means ever increasing automation as they try to take advantage of new hardware.
[*]Fortunately, Linux is so customizable that it has almost infinite versatility. If you start with a command line install, then add only what you minimally need, the resulting configuration can approach the speed you recall from yesteryear.
[*]The drawback is that such a highly customized install will be unique. It requires skill to maintain and constant attention to stay on guard against not only malware, but cruft and obsolescence. If you run into issues, then forums like ours will be of limited help since you've basically gone most of the way to spinning up your own distro.
[*]If you want such a personalized install, you may be interested in the link in my sig: The Best 'buntu Flavour.
[*]When following any of the instructions in that link, take note my prior observations: installing any of the DEs will likely bog down your machine to a teeth&#8209;gnashing crawl. You would need to go the server+window manager-only route. Something like the fvwm option might work for you.
[*]It bears noting that your experiment with Lubuntu + Opera is not as light as you believe. Lubuntu is no longer as light as it once was after moving to Qt, and Opera is a seriously obese browser. If you want a light browser, you will need something like Dillo, Epiphany, Midori or even Links2. These are so light (and undepowered) that you will likely hate them.
[*]I turn off auto updates too, but it is for the opposite reasons that you do. I am so concerned about security that I want the opportunity to parse every single update before they get installed. The fact that they ultimately ***do*** get installed is a foregone conclusion. Perhaps I'm mistaken, but from reading your post, it seems that you want to stop updating altogether.
[*]Last but not least, perhaps any of the Ubuntu flavours is the wrong solution for you. There are lighter weight distros that are still well maintained and are built specifically for old and underpowered HW. You may wish to try out Bodhi, Slitaz, BunsenLabs, or that old dog, Puppy (please forgive the pun).
[/LIST]

---

