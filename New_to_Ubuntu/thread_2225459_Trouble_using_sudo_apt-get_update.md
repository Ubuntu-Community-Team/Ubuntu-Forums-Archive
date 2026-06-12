---
title: "Trouble using sudo apt-get update"
date: 2014-05-21
forum: New to Ubuntu
---

### Post by Bob_Jones on 2014-05-21
I just downloaded opendlp in a VM.  It's running Ubuntu 11.04.  I'm trying to run apt-get update, and I'm receiving an unable to connect message.  I understand that this version is no longer supported, but I tried using the old-releases.ubuntu.com as well.  I'm also not opposed to upgrading the version, but that failed as well.  I am able to ping google and yahoo, so DNS and networking seem to be working.  I've also tried a few different things I've found from searching Google including the following:  

Set a proxy in bashrc and enabled anonymous authentication in the proxy for the the virtual machine's IP.
http_proxy=http://yourproxyaddress:proxyport  
export http_proxy

Edited the /etc/apt/sources.list and replaced releases with old-releases.ubuntu.com/ubuntu/

Edited resolv.conf and added DNS

I tried updating using sudo apt-get install update-manager-core and sudo do-release-upgrade with no success (including changing /etc/update-manager/release-upgrades back-and-forth from lts to normal).

I have tried to get this going for several  hours, and I'm out of ideas.  Any help would be appreciated.

---

### Post by LastDino on 2014-05-21
Wow! I don't know the technical answer for this but just a question, when and **if** you do manage to do this, do you think it will work? I mean you're jumping, what? 6-7 releases in between?

From what I know, you need to do release by release update and I would be happy to spend 30 min on fresh install instead of whole day on the former. (Assuming: I can actually do it)

---

### Post by Bob_Jones on 2014-05-21
The documentation for opendlp is lacking, and I figured it would be easier for a novice like myself to just get the VM working instead of doing a fresh install, and trying to get all the components working.  I'm really not opposed to any suggestions, but I felt like I would be going down a rabbit hole trying to figure out how to configure all the pieces of that application on my own.

EDIT:  I also just noticed that I fat-fingered the version.  It's 11.04 not 10.04 (not that it changes much, but still)

---

### Post by Bashing-om on 2014-05-21
Bob_Jones; HI !

I too have no direct support for your problem, other than advising that as you are working with End-Of-Life releases the means to upgrade are related in this tutorial:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
Path being 11.04-> 11.10 ->12.04 -> 14.04
Will be much faster and less chance of errors to do a clean install of a current supported release ( 12.04, 14.04 ) as LastDino advises.

Make a clean install of the current release as your base, and go from there. (??)

Whatever path you choose, we are here to help.

---

### Post by llamabr on 2014-05-21
Is there some reason not to do a backup of personal data, and do a fresh install?

---

### Post by squakie on 2014-05-21
Perhaps we should ask the hardware specs - CPU, memory, graphics adapter, etc., - to be sure it will support 14.04 or for that matter even 12.04 or 12.10?

---

