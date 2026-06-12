---
title: "Mac Aluminum USB keyboard, some keys not right"
date: 2022-09-29
forum: New to Ubuntu
---

### Post by nowyoumadememad on 2022-09-29
OK, here goes: Purchased a used gamer PC and a new 4K monitor on the cheap to try out Ubuntu as my old iMac is going geriatric and is not particularly good for its purpose any longer. Mac's pricetags nowadays are ludicrous and Ubuntu so far looks great for my purposes. Switched over trackpad, magic mouse and keyboard without problems and Ubuntu so far works fine for my needs. Have a rickety wireless Logitech keyboard, but hate the feel of it so until now have managed to find shortcuts for the symbols on the mac keyboard. Many of those i do not care much about, but the @ is not to be found at its position on the mac keyboard. Also the | , § , < and > symbols have switched places together with a few others. Not so much a problem as an annoyance. Anyone out there who know an easy solution without to much hassle and hack?

---

### Post by MAFoElffen on 2022-09-29
Try this for reassigning those keyboard keys:
[https://ubuntuforums.org/showthread.php?t=2130994&p=12582051#post12582051](https://ubuntuforums.org/showthread.php?t=2130994&p=12582051#post12582051)
(Read the whole thread to understand.) 

Adjust for your keys that you want to reassign. Basic logic is in *~/.xmodmaprc file: *remove the key you want to use from the keymap, then add it as the key you want to use. Both those files (*~/.xmodmaprc and ~/.xsessionrc) *do not exist. but as the Linux Graphics Layer comes up, if ~/[I].xsessionrc does exist, it will load right after ~/.bashrc... 

You could also add that call to it at the end of ~/.bashrc... Because ~/.xsessionrc assumes that you are using xorg xserver. If you are using wayland, make sure you make that call from ~/.bashrc.[/I]

Yes, that answer was from 2013 for Ubuntu LTS 12.04, but it still works and is relevant. The 'xmodmap' utility still exists with 22.04 as 'usr/bin/xmodmap'.

To add to that, this will give you which keymap is the current kepmap assignment:
```

setxkbmap -query

```
This will dump that currently assigned keymap and tell you which keys are assigned to what and what the specific key names are:
```

sudo dumpkeys -l

```
for more details system-wide configuration:L
[https://help.ubuntu.com/community/Custom%20keyboard%20layout%20definitions](https://help.ubuntu.com/community/Custom%20keyboard%20layout%20definitions)
or do a Google Search on: "Linux keyboard map assignment"
which will also (on some links) get into custom remapping and assigning keyboard key macros and functions...

---

### Post by ne29914 on 2022-09-29
Without language, layout and locale information it's difficult to say anything. Keyboard layouts are different all over the world.

---

### Post by nowyoumadememad on 2022-09-30
Hi,
Now there's a challenge for a newbie at the age of 65. I'll potter around and find out a few bits and ends and then have a go at it, doesn't look to scary. Keep the query open until I build my courage up and dive into it :)

---

### Post by MAFoElffen on 2022-09-30
I'm not sure now. I played with that for about an hour and kept getting errors.

I could remap common keys, because I could identify the keyname of those keys... But for "<" and ">". I couldn't figure out a correct keyname... 

For example, for "<" I tried Less, less, Meta_less, and Shift_coma... All of those names errored, saying they were bad modifier names.

EDIT:
But then I found the GUI utility:
[https://linuxhint.com/input-remapper-linux/]("https://www.linuxuprising.com/2020/12/remap-keyboard-and-mouse-buttons-on.html")

---

### Post by nowyoumadememad on 2022-10-04
Tha remapper tool really did the trick (almost), but the mac keyboard became too daunting. Not only the keys I mentioned but also the F1 - F12, the Alt, Cmd both on the left and right and it all ended up in conflicts and frustration. Me? I gone ordered a new cabled silent keyboard, not too pricey , allegedly adapted to use with Linux OS. Thank you for all the kind help, but I chickened out this time. Not that I didn`t try though..... 
What I do now: I will end this post(if I can) before I bother more people with better things to do, but thank you all for the good, kind help :).

---

### Post by MAFoElffen on 2022-10-04
No problem or bother at all. Never be afraid to ask a question here. That is one reason why this Forum exits. To help people and as a Community of Users. There is so  much more here to explore and to be a part of...

One of the computers I have here is a MAC Pro running Ubuntu. My work-around for a right-click is to use a regular USB mouse. (LOL) I can't seem to do anything like that from the notebook's touchpad. The struggle is real sometimes. (LOL)

Your solution was to buy a keyboard that matches your hardware and use. If you go to the "Thread Tools" Link at the upper right of this page, you can mark this thread as "Solved."

---

