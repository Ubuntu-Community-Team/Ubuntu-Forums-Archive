---
title: "Newbie here with an issue with the Appearance preferences (100% CPU)"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by TameRacingDriver on 2008-05-10
Hi all,

Newbie to this forum and Linux and am having a slight issue with it, and was hoping someone could help me. First though I'd like to introduce myself. The name is Paul, I'm from the UK and work as an IT techie in MS Windows XP environment.

To give a bit of background, I first tried Linux in the form of Kubuntu about 2 years ago but ran in to quite a few problems that could not be fixed so I ended up going back to windows.

Lately, I have been frustrated by the poor performance of windows, my laptop is an AMD Turion based machine with 1 Gb of RAM, and it would seem that even Windows XP does not always run that well on it, despite my efforts to tune it up. I'm an IT techie so I generally know how to get the best out of Windows. I tried Windows Vista on it too and that was really slow. To be honest, I find Windows quite a boring OS and not all that stable at times. It does the job, but you could hardly call it an enjoyable experience at all.

Someone mentioned Ubuntu to me and said that its performance had made wonders for his similarly specced laptop, so I decided to give Ubuntu a try.

So on went 8.04, and to be honest, I was stunned at the ease of which everything just worked straight out of the box. It found my wireless card (a big problem last time I tried linux) and told me it needed a firmware update. It upgraded my gfx card driver automatically and performed upgrades to the OS. I turned on the special effects to see what they were like, and it has to be said they put Vista to shame. Not only that, but the OS reported that it believed my battery was broken - nothing like that ever appeared in Windows, and I just put the poor lifespan of the battery down to it being crap!

I still think its got some way to go before its a complete, polished OS that anyone can use very easily... I run a Squeezebox on my rig, and setting this up was WAY more complicated than in Windows, but I got working eventually.

The problems seemed to start when trying to install different themes.

I eventually got one installed, but I didnt like it. I found a theme I liked on deviantart but could I hell figure out how to install it. The first one was a file that simply installed simply from the Appearance prefs. Never mind.

Then I went and tried to change some colours on the Human theme, and thats when my trouble seemed to start.

The machine locked up. I could move the mouse, but nothing else would respond, and the only thing I could do was power the machine off by holding down the power button.

When it booted back up, I put my password in and was greeted to a blank desktop, with a white box in the top left, when I hovered the cursor over it, the cursor changed to a text cursor.

Long story short, to fix this problem, i renamed some folders by going into "BASH", and I attempted to rename .gnome, .gnome2, .gconf, .gconfd, and .metacity. Not all of these folders were found but at least 3 of them were, and they were renamed.

I rebooted the system and logged in, and I then had my desktop back, thank god.

I also installed a package called "Art Manager" but that did not seem to do anything when I attempted to load it so I removed it.

Now I have noticed that if I open the Appearance preferences, its not long before my fans start speeding up, which led me to believe something was not quite right. Sure enough, I looked in the System Monitor and discovered that it had maxed one of the cores of my CPU to 100%. Also, when I closed it, the process did not end. The only way to do it was to kill it with the system monitor.

Now what I cannot ascertain is whether this was a problem before I knackered my desktop up. I suspect it may have been as I dont think it should have locked up like it did.

Not only that, but once I killed the process, soon after my screen starts to flash (usually the bottom half of the screen flashes black once every 30 seconds or so). That is obviously extremely irritating and as far as I can tell the only way to fix it is to reboot and DONT open the Appearance prefs.

Now, I have done my best to search just in case this had been done to death, and indeed, there are a few mentions of it dotted around, but the only 'solution' I've been presented with thus far is to remove the gtk-qt-engine package from the Synaptic Package Manager, however, that is not actually installed, so thats not it.

It is the one thing for me that is spoiling what I so far, after a few hours, consider to be what is otherwise an EXTREMELY nice operating system. I would appreciate it if anyone had any ideas, and sure enough if there is any more information that I can give you, then please do speak up, and I will happily provide it.

Thanks all :)

---

### Post by TameRacingDriver on 2008-05-10
bump

---

### Post by TameRacingDriver on 2008-05-10
OK guys I reckon I've managed to fix it.

Found a hidden file called .gtkrc-2.0 located in my Home\User folder, moved that out and it seems to have solved the issue.

Never mind, its only took me 3 or 4 hours to fix!

:guitar:

---

