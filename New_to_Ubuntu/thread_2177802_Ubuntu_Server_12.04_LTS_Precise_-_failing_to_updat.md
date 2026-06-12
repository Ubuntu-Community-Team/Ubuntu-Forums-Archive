---
title: "Ubuntu Server 12.04 LTS Precise - failing to update"
date: 2013-09-30
forum: New to Ubuntu
---

### Post by kmTTCHn on 2013-09-30
Hi! I've read many threads regarding this or similar issues but did not get an answer.
I am a linux newbie.

First of all my goal is to install GUI on ubuntu server, but to be able to do that I need to update and/or get the right sources.
When I type sudo apt-get update I get "Failed to fetch http://..." and "Ign http://..." I've tried several sources by editing /etc/apt/sources.list file and always get the same result. 
I'm thinking that Ign means ignore and that the files in the archives are not yet the right version, that they are older or same as the server ones, since I've downloaded the server installation files yesterday. If true, then it makes perfect sense why it would not update. In that case I'd like to know how can I download and install the ubuntu-desktop directly.

What I've done so far:
- tried to update from several sources (austrian, slovenian, US)
- added nameserver 8.8.8.8 and nameserver 8.8.4.4 to resolv.conf
- checked if paths for the archives are correct and they seem ok
- checked if there are any proxy settings, that would block fetching from http but onestly did not find much. So I can't exclude the proxy yet!

hopefully you all can give me an answer.

---

### Post by theDaveTheRave on 2013-09-30
kmTTCHn,

I'm not sure about your error messages, but your assumptions seem sound to me. [this thread]("http://askubuntu.com/questions/294525/what-does-ign-mean-when-running-an-apt-get-update") seems to agree with you.

As for running a gui desktop on your server.

I'm guessing that you are not a complete linux new, and you have a prefered desktop, I propose that you follow the details on this [ubuntu wiki page]("https://help.ubuntu.com/community/ServerGUI") for installing a deskstop.

David

---

