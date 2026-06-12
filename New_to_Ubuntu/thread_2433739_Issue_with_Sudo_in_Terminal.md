---
title: "Issue with Sudo in Terminal"
date: 2019-12-24
forum: New to Ubuntu
---

### Post by mike6658 on 2019-12-24
I have just installed Ubuntu 18.04.3 LTS and appear to have an issue with the Sudo command in the Terminal and would be grateful for some help and advice.

Whilst I am quite new to Linux, I have used the Terminal with my Raspberry pi so have a bit of knowledge (always dangerous, I know!) . 

I was following a Chris Titus Tech YouTube suggestion for an initial set up, which I copied and pasted, when the issue first arose. Basically the very first part is a Sodo apt update, the Terminal accepted this, and then the Terminal asked for my password - as I expected as this also happened in the YouTube video. 

However although the cursor is there  I cannot type anything in.

I have checked a few things. The Terminal is working okay, the prompt is correct with the $.  I am able to open the Terminal and get it to give me the date by typing in 'date' and then enter, also 'cal' works giving month with date highlighted. I then tried 'sudo apt update' but the same issue occurs that I cannot type in anything, the cursor just sits after the $. I tried copying and pasting but this also did not work.

I have tried to find a thread on this issue, but could not find one.  Thanks in advance for any help.

---

### Post by guiverc on 2019-12-24
This is only a quick thought - ensure the terminal is your active window (ie. click on it using the mouse).

I'm not on 18.04, but my cursor looks the same if the window is active or a background window, so at least once my password wrongly went into my IRC window :(

---

### Post by yetimon_64 on 2019-12-24
> **mike6658 said:**
> ...However although the cursor is there  I cannot type anything in....

When entering a sudo password you will NOT be shown any feedback, the terminal is working correctly this is a Linux security measure.

Keep entering the password till complete and press "Enter" on the keyboard. If nothing goes wrong with the command and password the prompt will return to normal; this means the command worked properly.

Note that the sudo password is not needed on a raspberry pi, that is a custom setting the pi uses particularly if on a pi4 unit. With my use of raspberry pi 4 installs the file /etc/sudoers.d/010_pi-nopasswd (name may be partly  incorrect here, the real file is named alike this) gets altered/disabled to return the raspbian installation to a more secure installation like Ubuntu uses.

**Edit**: there is an alteration you can do to the file /etc/sudoers that can alter the situation so the terminal outputs asterisks when the password is input. Let us know if you want feedback with passwords in the terminal. 

Have another go knowing the above, good luck. Regards, yeti.

---

### Post by Holger_Gehrke on 2019-12-24
Are you sure it's not working exactly as designed ? 'sudo' intentionally does** not show anything** when you type the password. It's a security measure against people looking at your screen being able to see the length of your password because knowing that would make guessing it (or running a brute force attack against it) easier.

Holger

Edit: yetied by a ninja -- uhm, no; the other way around ...

---

### Post by mike6658 on 2019-12-25
Thanks, you were absolutely correct and issue now sorted.  The password is not shown, clearly a good idea, I have been that used to dots coming up I immediately jumped to the wrong conclusion of what was going on!!!!

What an idiot I am.

---

### Post by CelticWarrior on 2019-12-25
> **mike6658 said:**
> Thanks, you were absolutely correct and issue now sorted.  The password is not shown, clearly a good idea, I have been that used to dots coming up I immediately jumped to the wrong conclusion of what was going on!!!!

What an idiot I am.

You are NOT an idiot, definitely :D
The problem is you have been miseducated by less secure OSes, that's all. Due to that your expectations - seeing some kind of feedback when entering the password - are perfectly legit.

---

### Post by bunny9000 on 2019-12-25
> **mike6658 said:**
> Thanks, you were absolutely correct and issue now sorted.  The password is not shown, clearly a good idea, I have been that used to dots coming up I immediately jumped to the wrong conclusion of what was going on!!!!

What an idiot I am.

First time I ever used the terminal many years ago I did the same. I think it's a general newbie trap.

Rule no 1 - Never assume anything :D

---

### Post by yetimon_64 on 2019-12-25
> **mike6658 said:**
> ...What an idiot I am.
Not idiotic at all, that terminal feature catches very nearly every new user their first time in terminal.

> **bunny9000 said:**
> First time I ever used the terminal many years ago I did the same. I think it's a general newbie trap....:D

Yes it is. Near 12 years ago in Gutsy Gibbon 7.10 I got hit my first time in terminal. Did a quick google search and discovered the security feature.

I like the password feedback myself, I use very long passwords up to 22 characters, so I turn on asterisks for password input. 

My password feedback in terminal looks like ...
```
yetiman:~ $  sudo blah
[sudo] password for yetiman: **********************
```

Regards, yeti.

---

