---
title: "Apt-get not working"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by Psycle on 2008-08-12
I am new to linux / Ubuntu and my job had asked me to install snort onto Ubuntu 7.10 Gutsy. These are not installed on VM. I had some issues with snort, but finally figured it out. But now the problem is when I try to run snort and log. I thought I had installed ACID on the machine, and when I ran aptitude I found that itwas not installed, so I ran apt-get install acid and this was the result:

root@danko:~# apt-get install acid
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package acid

so then I tried to update the repos. and this is the result:
root@danko:~# apt-get update
0% [Connecting to us.archive.ubuntu.com (91.189.88.45)] [Connecting to archive.

I had gone into the sources list and commented out what I thought was the issue. No deal. I also tried to use apt-get on acid lab and these were the results: 

root@danko:~# apt-get install acidlab
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  defoma fontconfig-config libapache2-mod-php5 libfontconfig1 libfreetype6
  libgd2-xpm libjpeg62 libphp-phplot libpng12-0 libt1-5 libx11-6 libx11-data
  libxau6 libxdmcp6 libxpm4 php5-common php5-gd php5-mysql ttf-dejavu
  ttf-dejavu-core ttf-dejavu-extra wwwconfig-common x11-common
Suggested packages:
  defoma-doc psfontmgr x-ttcidfont-conf dfontmgr php-pear libfreetype6-dev
  libgd-tools postgresql-client apache apache-ssl
Recommended packages:
  libft-perl
The following NEW packages will be installed:
  acidlab defoma fontconfig-config libfontconfig1 libfreetype6 libgd2-xpm
  libjpeg62 libphp-phplot libpng12-0 libt1-5 libx11-6 libx11-data libxau6
  libxdmcp6 libxpm4 php5-gd ttf-dejavu ttf-dejavu-core ttf-dejavu-extra
  wwwconfig-common x11-common
The following packages will be upgraded:
  libapache2-mod-php5 php5-common php5-mysql
3 upgraded, 21 newly installed, 0 to remove and 55 not upgraded.
Need to get 10.4MB of archives.
After unpacking 17.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  x11-common libxau6 libxdmcp6 libx11-data libx11-6 defoma ttf-dejavu-core
  ttf-dejavu-extra ttf-dejavu fontconfig-config php5-mysql libapache2-mod-php5
  php5-common libfreetype6 libfontconfig1 libjpeg62 libpng12-0 libxpm4
  libgd2-xpm libt1-5 php5-gd libphp-phplot wwwconfig-common acidlab
Install these packages without verification [y/N]? y
0% [Connecting to us.archive.ubuntu.com (91.189.88.31)]

I then naturally tried to install such as libapache2-mod-php5 using apt-get and it gives the same as trying to run and install acidlab. 

I thought it might of just been the connection but I had ping'd some sites and I am getting no loss of packets. 

Any suggestions or help with this would really be a god send. If you need any more info please I will give what you need. 
Thanks. :confused:

---

### Post by pytheas22 on 2008-08-12
I think it may be the repository servers; they're just being really slow.  Occasionally that happens.  There are mirror repositories that you can find through Google, if you want to try that, or you can wait a few hours and see if it improves.  It might also help to switch to a different server than the American one.

Usually apt-get tells you if there's a problem with the connection on your end.

---

### Post by SunnyRabbiera on 2008-08-12
also use sudo in your commands, that way you can enter it as root.

---

### Post by t0p on 2008-08-12
> **SunnyRabbiera said:**
> also use sudo in your commands, that way you can enter it as root.

He *is* entering it as root.  He is logged in as root.

---

### Post by Psycle on 2008-08-12
> **pytheas22 said:**
> I think it may be the repository servers; they're just being really slow.  Occasionally that happens.  There are mirror repositories that you can find through Google, if you want to try that, or you can wait a few hours and see if it improves.  It might also help to switch to a different server than the American one.

Usually apt-get tells you if there's a problem with the connection on your end.
I kinda figured that the servers might be a bit stressed or overworked, but this has been going on now for about a week and a half. It is driving me nuts. 

I will look for other repositories (not from the US) and add them to the list and see what happens

---

### Post by pytheas22 on 2008-08-12
> I will look for other repositories (not from the US) and add them to the list and see what happens

Alright, let us know if it helps.  There are other ways to get this stuff installed (e.g., download all of the packages individually) if you really can't get apt-get to work.

---

### Post by Psycle on 2008-08-12
Thanks I will let you know.

---

### Post by ramjet_1953 on 2008-08-13
Perhaps the reason why apt-get couldn't find [COLOR="Blue"]acid[/COLOR], is because it doesn't exist?

If you check, using Synaptic, you will see the following files:

[COLOR="Blue"]acidbase
acidlab
acidlab-doc
acidladlab-mysql
acidlab-pgsql[/COLOR]

No mention of acid!

Regards,
Roger :cool:

---

### Post by mev03465 on 2008-08-13
> **Psycle said:**
> I kinda figured that the servers might be a bit stressed or overworked, but this has been going on now for about a week and a half. It is driving me nuts. 

I will look for other repositories (not from the US) and add them to the list and see what happens

Although new to Linux, whenever I want to download a Windows program, I look for a d/l location where it is the middle of the night, or close to it. I am assuming that server traffic is consistent no matter what you are doing. Since I am in the U.S., during the day I find I get the best responses from servers in Australia or New Zealand. If it is 6:00 AM - Noon here on the East Coast(US), then I will look for servers/mirrors that are on the West Coast(US).

Usually, no matter what time it is where you are, there is a server/mirror somewhere that will have a relatively low volume of traffic simply because it is the middle of the night at that location.

I don't bother with Asian servers because they are *always *busy.

---

### Post by Psycle on 2008-08-19
I have tried using new sources from new zealand and then I had tried with other sources. I had commented out the originals and tried it that way then I tried agian with out them commented out. Still the same reults, the only difference is, is that when I commented them out I did not stall at 0% I had moved up to 4% then it stalled...Any suggestions. Do you think that the apt-get app is missing files or something and that I might need to re-install it? or do you think it might be something different? I am running out of thoughts on this one...thanks for your help in advance.

---

### Post by Psycle on 2008-08-19
> **ramjet_1953 said:**
> Perhaps the reason why apt-get couldn't find [COLOR="Blue"]acid[/COLOR], is because it doesn't exist?

If you check, using Synaptic, you will see the following files:

[COLOR="Blue"]acidbase
acidlab
acidlab-doc
acidladlab-mysql
acidlab-pgsql[/COLOR]

No mention of acid!

Regards,
Roger :cool:


I tried to install those but It stalls at 0% and now it stalls at 4% with the new repos. The only acid that I know that is installed is acid base and I have tried to install the others with no luck.
Thanks.

---

### Post by pytheas22 on 2008-08-19
Do you have any better luck if you use aptitude to try to install the package:
```

sudo aptitude
```

The interface is a little strange, but you can use the mouse.  Click search>find package and search for acid.

---

### Post by Psycle on 2008-08-25
I want to thank everyone for their helpin this matter....but I found that it is not theservers nor the repositories...The whole problem lay in my firewall rules....Had to delete onerule for it to work.

Thanks again for your help. 


:lolflag:

---

### Post by egalvan on 2008-08-25
> **Psycle said:**
> ...The whole problem lay in my firewall rules....Had to delete onerule for it to work.:lolflag:

could you post the rule you had to delete? This may help others with similar problems.

:popcorn:

---

