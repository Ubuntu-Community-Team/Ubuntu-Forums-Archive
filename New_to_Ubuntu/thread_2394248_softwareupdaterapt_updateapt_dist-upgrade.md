---
title: "softwareupdater/apt update/apt dist-upgrade?"
date: 2018-06-14
forum: New to Ubuntu
---

### Post by bodhin2 on 2018-06-14
I updated all 3 laptops with the usual apt-get update, and then apt-get dist-upgrade.  i accidentally clicked on the software updater just now thinking it was another app and updated needed?   so - is the apt-get update updating ubuntu as such and the dist-upgrade upgrades ubuntu with various patches and fixes and then is the software updater just updating the various apps as such?  dumb question i realize but i always figured and was told by people who know that the first should do everything and no need to run software updates?  correct calrification would help me understand this a bit more.  Thank you.

---

### Post by Frogs Hair on 2018-06-14
The man page may help. run the following.  ```
man apt-get
```

---

### Post by bodhin2 on 2018-06-14
thanks so much - yet again.

---

### Post by Frogs Hair on 2018-06-14
There are man pages for many operations some are easier to understand than others. Example: ```
man dpkg
```

---

### Post by bodhin2 on 2018-06-14
Thanks Frogs Hair!

---

### Post by deadflowr on 2018-06-14
Fwiw software updater (also known as update-manager) is just a graphical frontend for apt-get.
Software updater runs both the apt-get update command (that's what it does when you first open it and that scrolling bar is zipping back and forth
And then when see updates and click install  it runs as apt-get dist-upgrade.

Software updater has an interesting security feature where it can allow updates for software that is already installed on the system.
[https://wiki.ubuntu.com/SecurityTeam/FAQ#Update_Manager_doesn.27t_prompt_for_security_updates]("https://wiki.ubuntu.com/SecurityTeam/FAQ#Update_Manager_doesn.27t_prompt_for_security_updates")

Software Updater also has one particular ability that other apt methods do not have (Or at least I have not heard  of any other apt methods that do)
And that is a setting called phased updates.
[https://wiki.ubuntu.com/PhasedUpdates]("https://wiki.ubuntu.com/PhasedUpdates")

Hope it makes sense.
Or adds something useful...

---

### Post by bodhin2 on 2018-06-15
wow!  OK!  so is it ok to still use the apt get upfate and dist upgrade commands in terminal or stick with the update manager?  it seems like the last one is safest?

in another distro using update manager had issues and i was told to do the update and upgrade via terminal....  so coming to ubuntu after many years i am trying to understand the best way that will work the best too.  thanks you.

---

### Post by mrdc76 on 2018-06-15
Software Updater is what you are expected to use *normally*. You can just wait it to run automatically or run it manually if you want to be sure that you have the latest software.

---

### Post by bodhin2 on 2018-06-15
thanks so any issues with doing it with the update and upgrade via terminal.

sorry - basic for you people but when you get used to another distro and their workarounds etc.....   then starting again here.  i just want to know the correct things to do.  i am not a command line dude but i am not opposed to using it for minor stuff if i understand and do it correctly.

:-)

---

### Post by mrdc76 on 2018-06-15
There are no issues with upgrading from terminal vs. Software Updater. They do pretty much the same thing. Beginners (in general) just should not be taught unnecessary complex routines.

---

### Post by bodhin2 on 2018-06-15
ok thanks. that is fine and i do not mind doing it via terminal.  the commands are memorized by now.

:-)

a point of clarification i guess.  i run the commands every 2-3-4 days as such.  sometimes i see security updates/releases posted on a linux news site and i run the commands.  sometimes i just run them every few days as a routine.  I ran them on 3 laptops yesterday morning early before i went out to work.  they downloaded and applied stuff.   came back in later wanted to check ubuntu software but hit software update instead and another one ran which i thought was weird for 2 in 1 day.  all 3 laptops had the same software updates too.   So -----   i had to ask.  it was probably a fluke that the second update happened; but that made me wonder if an aspect was not updated doing the command line method.  Hope this clarifies my cause and hence question...

---

### Post by deadflowr on 2018-06-15
> **bodhin2 said:**
> ok thanks. that is fine and i do not mind doing it via terminal.  the commands are memorized by now.

:-)

Terminal command histories can be accessed by scrolling back with the up/down arrow keys.
So you might only need to enter a command once, then scroll back to it whenever you need to run it again.

That said, on Desktop installs the preferred way is always use the graphical application.
It's why they are there, right?

---

### Post by bodhin2 on 2018-06-15
That's what i thought until in anther distro they said the preferred was was terminal.  also there was a gui glitch when it comes to y/n un upgrade for example.  not possible and it would freeze or never complete.  that is why the dumb questions here in ubuntu.

---

### Post by oldos2er on 2018-06-15
To expand a bit on what deadflowr said, ```
history
``` will show you a numbered list of commands you've run. If there's one you want to use again, use ```
!123
``` where 123 is the command you want to repeat. Bash is a pretty nice, useful thing.

---

### Post by bodhin2 on 2018-06-15
Thanks for everyone's help and knowledge!

---

### Post by Frogs Hair on 2018-06-15
I've been collecting commands in a gedit/text document since I started with Ubuntu  which comes in handy.

---

### Post by bodhin2 on 2018-06-15
i had a file of stuff that was needed t fix another distro,  i started a new one for ubuntu but have not collected all of the info due to my work schedule. small homestead farm and way too much for an old crippled one man band to do.  but will try to do some catch up on slower rain days before it just gets too crazy and i can't find all of the stuff i nned to collect.
e

---

