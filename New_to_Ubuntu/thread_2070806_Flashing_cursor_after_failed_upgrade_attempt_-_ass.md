---
title: "Flashing cursor after failed upgrade attempt - assistance appreciated!"
date: 2012-10-13
forum: New to Ubuntu
---

### Post by SiddharthaWolf on 2012-10-13
Hi, I recently got a new laptop and had been using ubuntu 11.10 quite happily on it for around 2 months but had been having a recurring problem with poor sound quality when listening to music. I made an amateurish attempt at improving this with the help of responses to previous queries addressing sound issues in ubuntu. In the process I somehow got rid of the sound icon from the toolbar (apologies for windows lingo) at the top right corner. I thought this may as well be the right time to upgrade to Ubuntu 12.10, so I did but managed to interrupt the installation when it was on the third or fourth stage (unpacking things) by clicking on an icon while I was waiting (which I now realise is a big no-no).

Unfortunately, now my laptop only boots to the Ubuntu dots-loading screen then turns into a flashing cursor (although it is fine with Windows). I can't work out if its trying to automatically continue the upgrade installation, as the CPU light on my laptop seems to flash (although rather rhythmically). Memtest will not load, recovery mode halts on 'initial ramdisk' and changing the code to "nomodeset" doesn't help at all. When I try to access the terminal after booting to ubuntu, it initially wont let me, before deciding to alternate for about a tenth of a second between the terminal and the flashing cursor. After some more random mashing of keys the terminal settled on the following message after a number of "stopping XXX" "starting XXX" messages:

<<Rather than invoking init script through /etc/init.d/gdm, use the service( utility, e.g. service (8)

Since the script you are attempting to invoke has been converted to an upstart job, you may also use the start(8) utility>>

It then pauses on <<checking battery state>>

Has anyone got any idea what is causing the problem or what I should do to get it all working again? I'd be very grateful

---

