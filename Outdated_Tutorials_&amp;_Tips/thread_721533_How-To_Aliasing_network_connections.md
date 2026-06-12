---
title: "How-To: Aliasing network connections"
date: 2008-03-11
forum: Outdated Tutorials &amp; Tips
---

### Post by lswest on 2008-03-11
Well, I'm sorry if this was posted anywhere, i didn't really see anything like it while i was looking around.

Okay, so my situation is this: every day (cept for weekends) i go to School, where i have to turn on my computer, load linux, and then wait for kwifimanager to load (nm-applet hardly ever works, so i replaced it).  However, a while ago kwifimanager didn't start, so i went ahead and did the terminal networking set-up (i like it more, if it wasn't so much stuff to type XD especially my home network key of 26 digits :P).  Anyways, so i came up with this solution, and dispensed with a need for any network manager (well, for my home and school networks, otherwise i can just use the terminal to connect to new networks)

what i did:

opened .bashrc with ```
sudo nano ~/.bashrc
```
then at the end of the page i added the line ```
alias [name of school]="sudo iwconfig essid [essid] key [key] && sudo dhclient wlan0"
``` so now all i have to do is enter either mis (name of my school) or "home" in the terminal, enter my password, and i connect to the network.  i find it a lot more efficient and "fun" :P to do than opening kwifimanager, and then inputting my password to get to the config panel, change what config to use, hitting activate and then ok.

also, on a side note:
i also added the line ```
alias ls="ls -l --color=always --classify"
``` to .bashrc so that when i type "ls" it lists it in the long format, colour coded and with classifications.  To make these system-wide aliases, add them to the file /etc/bashrc (requires reboot), or for the root user add these lines to /root/.bashrc

I know this isn't really important, but i find it more efficient, hey, maybe someone will find this useful :P  feel free to comment (this is my first how-to on this site, outside of quick how-to's in threads), so don't be TOO harsh :P

*IMPORTANT* those commands require the quotes to be there, so add the alias lines with quotes around the command

---

### Post by PinkFloyd102489 on 2008-03-11
If I ever get a laptop, this could come in handy. Thanks.

---

