---
title: "Help Please - Installation &amp; Guide"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by xsentinelx on 2008-05-06
Well i am at it again! giving this another try & really want it to woRk .. (kindly excuse som of the noob questions :))

I created a separete partition (U - 10gb) & placed wubi inside .. ran the installation using the same partition as the instalaltion directory.

It created U:\ubuntu\install and had ubuntu-8.04-desktop-amd64.iso inside .. ran the installation & the next stop was ubuntu desktop after a while ;)

Since I had the iso backedup the second time i installed on a diff system (promoting ubuntu), I ran wubi.exe & it created the same folders. placed ubuntu-8.04-desktop-amd64.iso inside folder "install" & was able to install ubuntu without connecting to the internet & the need to download.

Now that i am downloading a 32bit version, would the same procedure work with wubi? would it run the installation on finding ubuntu-8.04-desktop-i386.iso inside the folder? :)

Secondly have a Intel DG31PR motherboard, is ubuntu compatible with tht? googling gave me mixed results, non labeled "IT IS" in my search results :(   ....anyone?

I am use to running apps like hostmgr, peergardian, blocklist man, to filter things which show up on my screen as well as for p2p, where if wanted to block a list of ips through iptable, is it possible? ( am sure it is but some easyway? :), can a list of ip's be imported into iptable to block? or any alternative apps which could be used?

The root user has no password on initial setup. how to set a pass for the root user?

How does hardening the kernel impact my sys? makes it slower, less compatible or xyz? 

The final one .. installing snort in IP mode escapes me ...(sad but true) & having it in IDS doesnt serve the purpose for me. WHT AM I TO DO?! :( errr. (pls dont say read read n read .. gets me more confsed everytime!!). any work around, alternatives or dummies guide to install/config snort, which i am sure i had .. but things didnt work out!! :(

---

### Post by phr0ze on 2008-05-06
Now that i am downloading a 32bit version, would the same procedure work with wubi? would it run the installation on finding ubuntu-8.04-desktop-i386.iso inside the folder?

It should.
---
Secondly have a Intel DG31PR motherboard, is ubuntu compatible with tht? googling gave me mixed results, non labeled "IT IS" in my search results  ....anyone?

Run the live CD and try your results. To do this you need to burn the ISO and boot into live mode. If you are happy go back and use Wubi.
---

---

### Post by linuxlizard on 2008-05-06
> The root user has no password on initial setup. how to set a pass for the root user?

Rather than going into root user, ubuntu uses the sudo command.

sudo <whatever command you would run as root>

your user password is the one sudo will want.

---

### Post by xsentinelx on 2008-05-06
well thanks for the quick response!!

sorry for not mentioning the fact that the facility to burn a cd is not available at the moment, hence only trial n err for me : ). Anyone using the same board arnd here?

anyways, anyone regarding a peergardian or a similar sort of app for linux platform? & SNORT!? found something of the similar sort by honeypot (dont recall the exact name L**) ... is it a wise choice?

---

### Post by phr0ze on 2008-05-06
I have peerguardian on a windows box and I like it. Even without CD since you are using WUBI there is practically no risk in trying it anyways.

---

