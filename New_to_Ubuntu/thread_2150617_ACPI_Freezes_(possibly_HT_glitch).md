---
title: "ACPI Freezes (possibly HT glitch?)"
date: 2013-06-01
forum: New to Ubuntu
---

### Post by LucenNox on 2013-06-01
Hi!

I finally was able to get ubuntu 12.04 installed after disabling acpi on my lenovo 3000 j desktop. 

Now I'm trying to re-enable as much of it as possible, so that shutting down and multiple cores work properly, but it keeps freezing. Specifically, it freezes shortly after I log in, usually when I start opening programs, I've yet to have it freeze before.

These are the boot parameters I've tried so far:

acpi=off noapic nolapic : This is mostly functional, but it hangs on a full shutdown (restarts no problem), and only shows one core. To the best of my knowledge, the no(l)apic isn't neccessary with everything disabled, but should cause conflict, they're remnants on when I installed.

acpi=ht :crashes shortly after I log in

pci=noacpi pnpacpi=off noapic nolapic : also crashes

ht=off: saw one post somewhere where the person had had ht=on, so I gave it a try, although I'm not sure if it's actually a valid parameter. Regardless, this froze on a black screen immediately after logging in. 


It seems to me most likely that the problem is hyperthreading, since I still had an issue with just that and nothing else. The problem is, this is an AMD cpu (3800+), and most places seem to be saying that ubuntu won't enable it unless the cpu is already compatible, and I can't find any parameters that explicitly disable hyperthreading to test it out(except maybe that last one above).

Unfortunately, it always freezes long before I am able to get a terminal window open, so there's no time to find a command to tell me whether or not it's disabled. 

It's not absolutely critical to get this working, as I'm prepping the computer to be a server for miscellaneous things in college, but it's would still be nice to get the max usage out of it, so any help is appreciated. 

Thank you!


EDIT: Solved! ...kindof
I finally was able to get past that roadblock, the problem was ondemand.

> Here's the trick: Ubuntu acts like every machine is a laptop and  loads a large number of things that would perhaps work fine on a laptop  but which crash a desktop machine.  The service you want to get rid of  is "ondemand".  This service attempts to speed up and slow down your  CPUs in order to save energy, crucial on a laptop but not supported  (apparently) on our desktop boxes.  (After the install, your machine  will seem like it's working for usually less than 1 minute, then it will  lock up.  The lockup occurs because the ondemand tries to vary the CPU  speed and it crashes everything.)
The "easiest" way to get rid of  ondemand is to go into the recovery console, drop down to the command  line, then load something called rcconf  (sudo apt-get rcconf).  rcconf  has a display of the services that will be loaded when the machine is  run normally.  Find ondemand in the list, remove the asterisk next to  its name so it won't be started (move the cursor over the asterisk and  press the SPACE bar).  Then hit TAB to get to the <OK> button and  hit ENTER.  You may see some funky error message, but ignore it.
When you are back at the command line, shutdown -r now.
When  the machine reboots, it probably will go back into recovery console.   When this happens, just hit ENTER to start regular Ubuntu.  Everything  should be fine after that.



So now I can boot successfully without acpi=off. That said, it still only shows one core, and has issues fully shutting down, but progress is progress, so I have a few more things to try before having to resort to another new thread.

---

