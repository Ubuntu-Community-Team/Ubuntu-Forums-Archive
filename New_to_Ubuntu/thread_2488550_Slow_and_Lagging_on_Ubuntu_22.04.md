---
title: "Slow and Lagging on Ubuntu 22.04"
date: 2023-07-08
forum: New to Ubuntu
---

### Post by thejazzdev on 2023-07-08
Good day guys. I recently started having issue with my Ubuntu 22.04 
It became very slow and Lagging that I have to post this help from my phone and not my PC is it's very annoying.


I have a 500Gb SSD which I'm not even using up to 100Gb and 20Gb RAM.


I have tried different options I was able to find online. 


I installed Stacer to clean all clean all junk file.
I also installed htop and run both htop and top in terminal but I'm not sure what I'm looking at there (screenshot attached)
I also install preload as I have seen online but no change.


Not sure what is wrong. I used to have 4 workspace open with all instance running Google Chrome and VSCode and one with virtual machine before with everything working fine. But now, I can barely use one workspace. I can even use only chrome. Btw, i don't think i'm even using half of this system capacity yet.


I recently just moved from windows to Linux. I have running more stuff on windows and my pc and i haven't experience anything like this before.

Here is a link to all relevant screenshots i took [https://imgur.com/a/0LWKVy7](https://imgur.com/a/0LWKVy7)

Please help :sob:

[IMG]https://imgur.com/a/0LWKVy7[/IMG]
[IMG]https://imgur.com/a/0LWKVy7[/IMG]

---

### Post by ajgreeny on 2023-07-08
The only thing I see is 37 separate entries for chrome in your **top** output which seems to be a very high number.

I never use chrome so can not tell you if this is normal when using it or if it means that you have too many tabs open, each using a separate process which shows in that **top** window.

---

### Post by thejazzdev on 2023-07-08
Just as i stated, i have about 4 workstatus and they all have chrome running in them. This is something i do on windows a lot and my pc doesn't lag. 

I have uninstall chrome, docker, docker-compose, postgres and goland. These are applications i recently installed but this pc i still laggin alot. Not sure what to do at this junction.

---

### Post by mart1nf on 2024-04-10
Hi, I am having a similar issue. For example, I can't keep pressed the erase button or delete constantly as the system doesn't perform the operation. I have to click it each time. 
Then all that is pdf reading through document viewer is very sluggish.
Also Zotero has become slow too and libre office writer is pretty unusuable if not in --safe-mode. There is something with the plugin for sure
Finallly, opening a terminal it takes several seconds to prompt the user@computer: ~$ and be able to do something.

Although I don't know if these are all related, they did seem to start at similar times back a couple of months ago. The system worked as a charm before... other things don't seem to be compromised. 

clamAV is installed and running and htop doesn't seem to throuw anything out of the normal. 

Regards

Martín

---

