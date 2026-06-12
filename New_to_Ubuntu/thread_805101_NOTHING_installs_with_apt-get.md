---
title: "NOTHING installs with apt-get"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by rockerphil on 2008-05-23
ok, i just set up a minimalist desktop installation on my ancient Dell Dimension desktop that's running a 500 MHz Intel Pentium processor and 128 MB of SD RAM by installing a bare command line interface and then installing XDM as my login manager, the xorg window system and the IceWM. well things have been installing fine up untill about 10 minutes ago when i got this string of errors when trying to install the Synaptic package manager

phil@phil:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libvte-common libvte9
Suggested packages:
  dwww
Recommended packages:
  deborphan libgnome2-perl
The following NEW packages will be installed:
  libvte-common libvte9 synaptic
0 upgraded, 3 newly installed, 0 to remove and 7 not upgraded.
Need to get 2056kB of archives.
After unpacking 8626kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main libvte-common 1:0.16.9-0ubuntu3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main libvte9 1:0.16.9-0ubuntu3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main synaptic 0.60ubuntu5
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte-common_0.16.9-0ubuntu3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte-common_0.16.9-0ubuntu3_all.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte9_0.16.9-0ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte9_0.16.9-0ubuntu3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/synaptic/synaptic_0.60ubuntu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/synaptic/synaptic_0.60ubuntu5_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


i've tried running both sudo apt-get update and running it with --fix-missing, neither one seems to work. i've also looked at my /etc/apt/sources.list file, and everything seems to be in order, so i'm just lost, any suggestion guys? thanx

---

### Post by Paqman on 2008-05-23
Have you got it connected to the network/internet?

---

### Post by rockerphil on 2008-05-23
yea, i'm browsing fine, it's my only computer

---

### Post by mrtomservo on 2008-05-23
Can you ping the repository you're trying to connect to?

---

### Post by Paqman on 2008-05-23
Reason I ask is that it looks like it's trying to connect to 127.0.0.1, which is your own box. Frankly, I haven't a clue how to check what server apt-get is configured to connect to, I tend to use Synaptic to manage that.

---

### Post by KingTermite on 2008-05-23
Did you disable any ports?

---

### Post by kerry_s on 2008-05-23
did you try running-> sudo apt-get update
again?

if that don't work try removing the us. part to switch to different servers.

[http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)
to
[http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)

---

### Post by wootah on 2008-05-23
Do you have aptitude installed? Perhaps try that ?

---

### Post by HotShotDJ on 2008-05-23
Please open Applications --> Accessories --> Terminal and type in:```
gksudo gedit /etc/hosts
```It should look like this:```
127.0.0.1	localhost
127.0.1.1	phil
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```Edit as necessary and then reboot and try to install software again.

---

### Post by arpanaut on 2008-05-23
What have you installed recently that may have changed your network settings?

---

### Post by rockerphil on 2008-05-23
i can ping the repo just fine, and as far as the "unable to connect to loacalhost" i'm clueless, and i personally prefer Synaptic myself, but uh I CAN'T INSTALL IT. LOL

---

### Post by HotShotDJ on 2008-05-23
> **rockerphil said:**
> i can ping the repo just fine, and as far as the "unable to connect to loacalhost" i'm clueless, and i personally prefer Synaptic myself, but uh I CAN'T INSTALL IT. LOLPlease examine your /etc/hosts file as suggested in my previous post.  While I cannot promise you that the problem lies there, the symptoms you report point to that as the source of your problem.

---

### Post by RDL89 on 2008-05-23
Suddenly I'm having the same problem.

---

### Post by rockerphil on 2008-05-23
ok, the /etc/hosts file i'm not to keen on, but here's what it's got if anyone can give a hand

127.0.0.1       localhost
127.0.1.1       phil.grandenetworks.net phil

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


thanx guys

---

### Post by HotShotDJ on 2008-05-23
> **rockerphil said:**
> ok, the /etc/hosts file i'm not to keen on, but here's what it's got if anyone can give a hand

127.0.0.1       localhost
127.0.1.1       phil.grandenetworks.net phil

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


thanx guysAs I suspected, this is your problem... the second line should simply say "phil"  Please edit it, save it and reboot.

---

### Post by rockerphil on 2008-05-23
> **HotShotDJ said:**
> As I suspected, this is your problem... the second line should simply say "phil"  Please edit it, save it and reboot.

ok, that's a bit vague, could you please elaborate? do you mean delete the second "phil" or delete the entire line and simply have "phil"?

---

### Post by HotShotDJ on 2008-05-23
> **rockerphil said:**
> ok, that's a bit vague, could you please elaborate? do you mean delete the second "phil" or delete the entire line and simply have "phil"?As I said in my first post to this thread, your /etc/hosts file should look like this:```
127.0.0.1	localhost
127.0.1.1	phil
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by rockerphil on 2008-05-23
much appreciated HotShot, and sorry, i didn't see your first post, but it fixed the problem

---

### Post by HotShotDJ on 2008-05-23
> **rockerphil said:**
> much appreciated HotShot, and sorry, i didn't see your first post, but it fixed the problemI figured you missed it. I'm pleased that i was able to assist. :)

---

### Post by rockerphil on 2008-05-23
guess what guys? it's back, i go to install the game Ltris through Synaptic (pretty simple right?) and i get this:


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/smpeg/libsmpeg0_0.4.5+cvs20030824-2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/smpeg/libsmpeg0_0.4.5+cvs20030824-2_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/sdl-mixer1.2/libsdl-mixer1.2_1.2.6-3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/sdl-mixer1.2/libsdl-mixer1.2_1.2.6-3_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/l/ltris/ltris_1.0.11-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/l/ltris/ltris_1.0.11-1ubuntu1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


i checked my /etc/hosts file, this is what i got:

127.0.0.1       localhost
127.0.1.1       phil

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts





so now i'm startin to get a little aggrivated, so any help in solving this would be GREATLY appreciated, thanx guys

---

### Post by HotShotDJ on 2008-05-23
> **rockerphil said:**
>   Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

127.0.0.1       localhost
127.0.1.1       phil
:shock:

I'm not quite certain, so I've done a little research and found the following:> The above method didn't work for me. If I remove the domain through System > Admin > Network and save it then the domain comes back in the /etc/hosts. Editing /etc/hosts solved the issue temporarily, however, after taking my laptop home and after changing the settings through System > Admin > Network again brought back the same issue (domain name appended)I wonder if something like that could be happening... although you report that /etc/hosts didn't get changed this time.  I must admit, I'm perplexed.:-k

---

### Post by rockerphil on 2008-05-24
sorry bout the late reply, but i finally decided to go to sleep rather than hurl my computer out a window. if it helps any i used the minimal CD to make the command line interface install then built up from the command line, but i really don't see how it would make a differece, i guess i'm just gonna have to reinstall :'(

---

### Post by brettg on 2008-05-24
Can you pls post the contents of /etc/apt/sources.list

---

### Post by rockerphil on 2008-05-24
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) gutsy-security main restricted
# see [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

here ya go, it seems to be in order to me, but maybe there's something wrong that i'm not seeing

---

### Post by brettg on 2008-05-24
That seems OK

If you paste [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) into your browser do you get to the "Index of /ubuntu" page?

If you do sudo apt-get update does it return any errors? (any errors at all will pretty much break everything for apt)

I have had problems with apt-get in the past whereas aptitude has worked fine.

ie:
sudo aptitude update
sudo aptitude install *package*

Good luck

P.S. It might be some time before I respond again, almost midnight where I am and being an aging old bugger I need to go to bed now, sorry.

---

### Post by rockerphil on 2008-05-24
i just ran the commands using aptitude in the place of apt-get and i'm still recieving error messages, and as stated in my earlier posts it's not just apt-get or aptitude, it's any time i try to install anything, weather it's through the terminal or through Synaptic, the problem was temporarily solved by editing my /etc/hosts list, but the problem persists, and the /etc/hosts.list file was not changed this time, anybody else having this problem? in other words HEEEEEELLLLLLLLLPPPPPP

---

### Post by brettg on 2008-05-24
The question is, why is it trying to connect to localhost:4001

Do you have an anon proxy server running or something whacky like that?

If you do stop that service and type;

sudo dpkg-reconfigure anon-proxy

---

