---
title: "Howto Smartlink modem on dapper"
date: 2006-05-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Matchless on 2006-05-12
Hi,
   Hope this how to helps, as the smartlink modem files on the dapper repos seems to be for breezy and do not work properly on dapper. I have given a shortened howto as it is intended to be read with the dialupmodemhowto on the wiki.
_**Howto get Smartlink winmodem working in dapper**_

1.Read the ubuntu wiki dialupmodemhowto, the steps below only compliment the wiki and you should have all the preliminaries done as described for the Smartlink modem, but you can omit installing gcc-3.4 as this is not required for dapper.
2.Download sl-modem-daemon2.9.9d+e-pre2-5.deb and sl-modem_2.9.9d+e-pre2.orig.tar.gz from the debian website [http://packages.debian.org/unstable/misc/sl-modem-daemon](http://packages.debian.org/unstable/misc/sl-modem-daemon).
3.Copy the sl-modem-daemon file to your local repository and update your Packages.gz file, this will allow you to install with Synaptic etc. or use your favourite .deb installation method.The presently available daemon on the ubuntu repos does not work after a reboot on dapper
4.Copy the sl-modem_2.9.9+e-pre2.orig.tar.gz file to your Desktop and right click on it and select “Extract here” and a folder wth the same name will be created with the extracted files on your desktop.
5.Now rename the folder to an easier name such as “slmodem”
6.Open a terminal and cd in to the slmodem folder
7.Type make
8.Type sudo make install
9.Type sudo modprobe slamr
10.Type dmesg | grep slamr
11.Now install sl-modem daemon with Synaptic
12.Use Kppp to query the modem, if this works you are there!
13.Edit /etc/default/sl-modem-daemon to change the line SLMODEMD_COUNTRY= USA to i.e SOUTHAFRICA or your country
14.Type sudo /etc/init.d/sl-modem-daemon restart to restart the daemon.
15.If you do a “Query modem” in Kppp you will see that your country has changed.
16.It seems as if the Smartlink modems with Netodragon chip MDV92XP does not work, but the ND92XPA chip works.

---

