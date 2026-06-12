---
title: "Cannot shut down or restart ubuntu 17.10"
date: 2017-11-15
forum: New to Ubuntu
---

### Post by nickychap on 2017-11-15
Only 2 months experience with ubuntu (ie fairly ignorant as yet) & when I try to shut down or restart ubuntu 17.10 it sticks on the page with the row of 5 lights turning white then red in sequence under the ubuntu title (the splash screen?) - my only option is to hold down the power button until it switches off.
Advice please!

---

### Post by pissedoffdude on 2017-11-17
Hi,

There could possibly be something up with your hw's compatibility on 17.10's kernel.  Did it used to work just fine on a previous Ubuntu release, and was this an upgrade?  I'd suggest getting us the syslog to see if we can narrow this down.  Can you take note of the time you shut it down, then share that timefrime as well as /var/log/syslog and /var/log/syslog.1?  I'd also suggest running a:
```
sudo dmidecode > dmidedode.txt
```

so that your hardware information is outputted to a text file that we can take a look at it.  I forget if this is included in a default install, so if the above command fails, you can install dmidecode:
```
sudo apt install dmidecode
```

---

### Post by A.O._Stanley on 2017-11-17
I also am unable to shut down normally and have to shut down manually.

But I can restart after manual shut down.

Fresh install of 17.10 on new Dell laptop running an AMD processor.

---

### Post by pissedoffdude on 2017-11-17
> **A.O._Stanley said:**
> I also am unable to shut down normally and have to shut down manually.

But I can restart after manual shut down.

Fresh install of 17.10 on new Dell laptop running an AMD processor.

^^
Let's get your info as well.  Could be related to the OP's.  Can you try the commands from the post I mentioned for more information?  Also, does
```
sudo shutdown -h now
```

successfully shut your computer down, or does it hang?

---

### Post by A.O._Stanley on 2017-11-17
shutdown command does not work, but thanks.

The dmidecode stuff gets no results. Also, you have a spelling error. Regardless, either way it's spelled gets no results.

When I shut down and get to the Ubuntu screen with dots, if I hit esc I get to a screen that shows 'stopped' processes. At the bottom it shows that it is trying to stop three additional processes but they don't want to stop. One, I think is WPA, next is Network manager, and there is one more. These do not stop so I'm guessing this is what is preventing the computer from shutting down.

---

### Post by pissedoffdude on 2017-11-17
Sorry about the spelling error.  Did the dmidecode work?  Let's get the output of it.  I was hoping that if we get your HW, this can be something we can solve by installing the right drivers.  The dmidecode will be super useful for this.  If this is anti-working, we can look into other means.

---

### Post by A.O._Stanley on 2017-11-17
The dmidecode commands don't do anything.

The shutdown command didn't do anything.

When it's hanging, I hit esc and a screen appears that shows all the processes that have been stopped or are in the process of stopping. At the very end of the list I get:

A stop job is running for...

And the following three items cycle through, WPA supplicant, Raise network interfaces, Network manager.

They repeat every few seconds.

Don't know if any of that means anything

---

### Post by pissedoffdude on 2017-11-17
No worries.  The dmidecode commands were to get some information.  What is the information with them? (they assume you have an internet connection).  We probably can't get a straight up command that fixes everything (i hope so we can) but we need to see what's up with  your system which is why I suggested the previous commands.  If they still fail, can you get me the output of
```
cat /etc/lsb-release
```

---

### Post by A.O._Stanley on 2017-11-17
Since this was a fresh install on a new machine and I was having other issues, as well, I just installed 16.04 and I'm not having anymore issues. I will try to upgrade from 16.04 and see how it goes.

---

### Post by ajgreeny on 2017-11-17
This is good news.
If your reinstall really has solved this to your satisfaction please mark the thread as SOLVED from the Thread Tools menu at the top.

---

### Post by DuckHook on 2017-11-18
I am clearly sounding like a broken record by now, but if Xenial works for you and does everything that you want, then don't upgrade to Aardvark. It is simply not necessary.

Your shutdown problem sounds like the same issue from the following recent thread: [https://ubuntuforums.org/showthread.php?t=2377332&p=13710597#post13710597](https://ubuntuforums.org/showthread.php?t=2377332&p=13710597#post13710597)

There appears to be a problem with the latest kernel and either wpa-supplicant or network manager. If you are running Aardvark because you are helping either with the testing or the preparatory work for Beaver, then please add your experience to the launchpad report.

But if you are a general user who just wants to keep current, then please be aware that Ubuntu does not work like Windows and it is counter-productive to install non-LTS releases like Aardvark&#8213;which are good only for 9 months and are not as stable as LTS releases. Because Xenial (16.04) is an LTS, it is good until 2019 or 2021 depending on flavour. General users should stick with LTS releases and only upgrade to the next LTS (which will be Beaver 18.04). Leave those intervening releases to the guys who have no choice but to use them because of bleeding edge equipment, app requirements, etc. If your system is stable with Xenial, then stick with Xenial.

---

### Post by tranfuria on 2018-01-22
Im also having an issue similar to this, I cant suspend, shutdown, restart, or even close the lid on my laptop without the whole thing crashing. Same result from doing a `sudo shutdown -h now` command. Ive tried confiuring some of the files that are triggered by the different actions to use the pm-utils equivilant for each of the commands (pm-suspend for suspend, etc).

Most often i get a screen where the whole thing goes pixelated, with bars going across the screen. here is the imgur link for it: [https://imgur.com/0CUWRgu](https://imgur.com/0CUWRgu)
I've also attached the output of the dmidecode command.

Im running Ubuntu 17.10 on a 'new razer blade stealth 2017 model, with an intel i7-7500 (dualcore processor). I've tried ubuntu 16.04 and had the same issues.

Also i found that some 3rd party drivers were available online, from [https://openrazer.github.io/](https://openrazer.github.io/), i have these running and they work great for allowing me to control the lighting of the keyboard.


Also, not sure if its related to this or not, but i had to disable the capslock key on my keyboard because anytime i pressed it the same 'crash' would occur, with the screen going all pixelated and such.

Any help is much appreciated

---

### Post by zebullonpike on 2018-01-29
I have the same issue. I had 17.04 and it worked fine but 17.10 has a lot of unfriendly issues.

---

### Post by zebullonpike on 2018-01-29
I got the notice of an upgrade - so I upgrade 17.04 to 17.10 and it's worse than what I had before. If I reinstall something else then I will lose everything I have. It would be better if 17.10 is fixed and made better. Like a shutdown/restart function. Able to see what all apps are installed so I can un-install duplicates.

---

