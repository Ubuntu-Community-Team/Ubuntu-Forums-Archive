---
title: "Is firewall necessary?"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by worldy on 2008-05-25
Should i install a firewall on my Ubuntu Hardy PC ? I just use it to browse internet and download stuffs.
Will it enhance my PC security ?

---

### Post by wolfen69 on 2008-05-25
ubuntu already has one installed. it is called iptables. you are safe.

---

### Post by Deeta on 2008-05-25
> **wolfen69 said:**
> ubuntu already has one installed. it is called iptables. you are safe.

Yeah, but is it not like set to be quite permissive in its default mode?

---

### Post by ubuntu27 on 2008-05-25
Hello worldy :)

Ubuntu Linux has an internal firewall called "IP Tables", you will need to configure it since it is permissive by default. 
Reason for this? When you install Ubuntu, ALL the programs installed **does not** try to connect to the Internet unlike some other Operating Systems. 

Search the forums for IP tables, and you will see many threads about it.

---

### Post by Tatty on 2008-05-25
As said by previous posters, you do not need to worry about a firewall in ubuntu unless you start installing apps like apache or other server apps, as by default there are no apps listening.

If you feel you need firewalling then firestarter is a good GUI frontend to set up and manage your iptables:

```
sudo apt-get install firestarter
```

Then use the simple wizard in firestarter to configure it for your machine.

---

### Post by ardvark71 on 2008-05-25
> **Tatty said:**
> As said by previous posters, you do not need to worry about a firewall in ubuntu unless you start installing apps like apache or other server apps, as by default there are no apps listening.

If you feel you need firewalling then firestarter is a good GUI frontend to set up and manage your iptables:

```
sudo apt-get install firestarter
```

Then use the simple wizard in firestarter to configure it for your machine.

Or Guard Dog for kubuntu...

sudo apt-get install guarddog

Best Regards...

---

### Post by buntunub on 2008-05-25
Hardy comes with ufw. Try using that instead, but its cli only. Should be some guides for that on google.

---

### Post by hyper_ch on 2008-05-25
if you have a firewall on your router and if that is properly configured I see no reason as to why you should bother with a FW on linux.

---

### Post by brian_p on 2008-05-25
> **worldy said:**
> Should i install a firewall on my Ubuntu Hardy PC ? I just use it to browse internet and download stuffs.
Will it enhance my PC security ?

With a default install all unsolicited packets are rejected; that's about as non-permissive as you can get. For what you want to do there is no possibility of anyone connecting to your machine and a firewall will do nothing to alter that state of affairs.

---

### Post by misfitpierce on 2008-05-25
Firestarter is easier for beginners in my opinion than trying to tinker with terminal ufw. Try sudo apt-get install firestarter in terminal as said and download that. Then simply set the rules you want set and hit the X to close firestarter. The rules will remain permanantly even when program is closed and on system restart until you change them again. I prefer Firestarter myself as well :)

---

### Post by barbedsaber on 2008-05-25
afaik (and I could well be wrong)
hardy comes with ufw (uncomplicated firewall)

dont know much about it tho.

---

### Post by hyper_ch on 2008-05-25
why do you think you need to change the default iptables settings?

---

### Post by lisati on 2008-05-25
> **worldy said:**
> Should i install a firewall on my Ubuntu Hardy PC ? I just use it to browse internet and download stuffs.
Will it enhance my PC security ?

If we could count on everyone being as skilled, nice and decent as the majority of Linux users, and if we could count on the occasional accidental muck-up by programmers not causing problems, then tools like firewalls wouldn't be necessry....trouble is, there are rascals out there.....

---

### Post by hyper_ch on 2008-05-25
I still see no reason to use a firewall...

---

### Post by HunterThomson on 2008-05-25
I am looking into PaX PIE/SSP, AppArmor, intuition detection systems, setting up a old computer to sync log files too.... True you don't need to worry about viruses but your Linux box can still be attacked. You mite get a email one day or cops at your door claming that your computer was attacking some government computer systems. 

Granted that is an extreme scenario:lolflag:

I ipfilter to block IP ranges from [http://www.bluetack.co.uk](http://www.bluetack.co.uk) with. And I block lists of domain names.

---

### Post by hyper_ch on 2008-05-25
Hunter:
Please be more specific why a normal homeuser would need a firewall on the ubuntu box?

---

### Post by buntunub on 2008-05-27
A firewall closes open ports. Thats what IPTables does, which comes standard on all distro's. IPTables (and ufw) default settings are quite permissive, but still much more protection that anything windows has out of the box. Configuring IPTables via cli is VERY complicated, so alot of people like to use Firestarter, which is really nothing more than a GUI frontend for IPTables. It has a cool setup wizard that makes it seem like its changing all kinds of values under the hood for you, although it really does not change much at all. Its a very useful tool if you want to have a really complex setup, and it builds in support for a DHCP server, so thats kinda nice. Hardy's new ufw tool is really about the same thing, and setup is really very simple via cli. So, whats the scoop? IPTables at default settings gives you a very secure system as is, so unless you are administering a huge LAN, is there really a good reason to be messing with it?.. Probably not, but it cant hurt when using Firestarter defaults.

---

### Post by sayakb on 2008-05-27
Well, I use Firestarter since it has ICMP filtering. It restricts sending of packets to password stealing apps on the LAN which by default is **permitted**.

---

