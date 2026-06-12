---
title: "Wired and Wireless not working in Ubuntu 12.04"
date: 2012-09-07
forum: New to Ubuntu
---

### Post by janardhanmuthya on 2012-09-07
Hi all,

I bought a fujitsu lh531 this april and installed Ubuntu 12.04. Till now there is no problem with the network connections. But, all in a once from today morning i am unable to connect wired and wireless connections which i am using from april also i had checked this connections with other machine and all is well with them.

Can anyone please guide me regading this.

Regards,
Janardhan

---

### Post by Epodx64 on 2012-09-07
Try plugging in the ethernet cable and running this from a terminal

sudo ifconfig auto eth0 up

if that brings up your wired connection next try updating your system sudo apt-get update && sudo apt-get upgrade

---

### Post by NikTh on 2012-09-07
> **janardhanmuthya said:**
> Hi all,

I bought a fujitsu lh531 this april and installed Ubuntu 12.04. Till now there is no problem with the network connections. But, all in a once from today morning i am unable to connect wired and wireless connections which i am using from april **also i had checked this connections with other machine and all is well with them.**

Hello , 
do you mean router ? Cuz we want to exclude the possibility of router's fault or fail. 

If router works correct on other machines , then open a terminal (Ctrl+alt+t) and apply bellow command 

```
nmcli nm enable
``` and see if network awakened. 

Thanks

---

### Post by janardhanmuthya on 2012-09-07
> **Epodx64 said:**
> Try plugging in the ethernet cable and running this from a terminal

sudo ifconfig auto eth0 up

if that brings up your wired connection next try updating your system sudo apt-get update && sudo apt-get upgrade
Dear Epodx64,

i had tried sudo ifconfig auto eth0 up

then reply is

eth0: Unknown host

Also i had gone to network in system settings,

the error message is The system network services are not compatible with this version.

please help me.

---

### Post by janardhanmuthya on 2012-09-07
> **Epodx64 said:**
> Try plugging in the ethernet cable and running this from a terminal

sudo ifconfig auto eth0 up

if that brings up your wired connection next try updating your system sudo apt-get update && sudo apt-get upgrade

Dear Epodx64,

i had tried sudo ifconfig auto eth0 up

then reply is

eth0: Unknown host

Also i had gone to network in system settings,

the error message is The system network services are not compatible with this version.

please help me.

---

### Post by acoluthus on 2012-11-03
Hi-
I'm trying this fix as well and am stuck at this point.
I tried a couple of other 'fixes' to this problem but as a newbie/(ignorant of _any_ programming type) 1> working in Terminal makes me nervous and 2> I don't understand the results/what it means if the 'reply' in Terminal doesn't equal what's expected (I stop there)
I'll follow the path step by step,(though it feels quite blindfolded to my understanding) I didn't 'get' what those were saying/describing. 

SO: if someone could show the resolution on this thread/path, that'd be greatly appreciated.

---

