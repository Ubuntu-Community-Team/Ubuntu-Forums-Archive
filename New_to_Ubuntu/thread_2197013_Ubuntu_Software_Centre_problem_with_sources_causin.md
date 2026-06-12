---
title: "Ubuntu Software Centre problem with sources causing internal error"
date: 2014-01-01
forum: New to Ubuntu
---

### Post by catrionalfyffe on 2014-01-01
Hi all,

I was trying to Uninstall Wine 1.4 so I could then update to the most recent version (to solve a problem I was having with a Windows program I was trying to install) and when I clicked Uninstall Software Centre closed. I tried to open it and it would come up showing it was loading then close again. I have restarted the computer twice but it still has the same problem and it says it can't report the problem because it can't determine the package or source name. 

Following from other similar posts I ran 
apt-get update 
[FONT=trebuchet ms]
and got the following message[/FONT]

E: Type ‘ain’ is not known on line 2 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list
E: The list of sources could not be read.

[FONT=verdana]Now I think this may be my fault because I added a Source in the software list following the how to install wine
how to from Wine HQ (added *ppa:ubuntu-wine/ppa),* but then read somewhere in Ubuntu documentation that
it was better to add software from the Software Centre so I installed the Wine version that came up in the Software
Centre without deleting this source(though I think I have deleted it and added it when trying to get one of my programs
to work, so who knows what I may have broken).

I am using 32 bit Ubuntu 12.04.

Any help anyone has on how to fix this would be much appreciated,

Cheers
Cat[/FONT]

---

### Post by Jonathan Precise on 2014-01-01
Post the url of:
```
cat /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list | pastebinit
```

---

### Post by monkeybrain20122 on 2014-01-01
Just remove the ppa entry (entries) and add it again. Sometimes it may get corrupted.

```
cd /etc/apt/sources.list.d
sudo rm ubuntu-wine-ppa*
sudo add-apt-repository [FONT=verdana]ppa:ubuntu-wine/ppa[/FONT]
sudo apt-get update

```

P.S. Install synaptic. It is a much better gui for managing your packages then the software centre. It is a lot faster and allows more control. Only thing missing is the catalogue of paid apps.

---

### Post by catrionalfyffe on 2014-01-01
Thanks, that was quick :)

I got 
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) precise main
ain

---

### Post by catrionalfyffe on 2014-01-01
Wooo Software Centre is working again, thanks folks!! I will install Synaptic now too.
Cheers
Cat

---

### Post by raphael-platte on 2014-01-01
> **catrionalfyffe said:**
> Wooo Software Centre is working again, thanks folks!! I will install Synaptic now too.
Cheers
Cat

Isn't synaptic included?

---

### Post by monkeybrain20122 on 2014-01-01
> **raphael-platte said:**
> Isn't synaptic included?

No, not in Ubuntu, It is included in some flavours like xubuntu and lubuntu but Ubuntu uses the Software Centre by default, it is pretty, glossy but slow, resource demanding and not very informative except for(IMO useless) info like user rating.

---

