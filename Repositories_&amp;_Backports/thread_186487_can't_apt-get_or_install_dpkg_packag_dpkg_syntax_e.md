---
title: "can't apt-get or install dpkg packag dpkg: syntax error: unknown group `root' in stat"
date: 2006-06-02
forum: Repositories &amp; Backports
---

### Post by urvaius on 2006-06-02
this is the error I get

dpkg: syntax error: unknown group `root' in statoverride file

i look in the statoverride file and this is what is in there
hplip root 755 /var/run/hplip

i tried to delete this but then it complains statoverride file is empty

i uninstalled a program and then tried to install another package when this happened
any help please

---

### Post by Jussi Kukkonen on 2006-06-02
You of course shouldn't have to do this at all, but... You can use dpkg-statoverride program to edit the file, see *man dpkg-statusoverride*. Maybe something like:
```
dpkg-statoverride --remove /var/run/hplip
```

---

### Post by micahphd on 2006-10-25
Hello,

I've only been running Ubuntu (and Linux for that matter) for a couple days.  I just ran into this problem myself where I tried to run updates and got:

"dpkg: erro: unknown group 'root' in statoverride file"

I don't know if this is a healthy solution for the problem, but I checked Users and Groups and found that there was no "root" group.  I had recently run into some problems messing around with users and groups and had to edit a couple files as root to get myself access to everything as my personal login again. So I wonder if maybe I screwed up the root group or it got wiped or something while I was tinkering with stuff.  I'm not really sure but a friend of mine said there should be a root group on the system.  So since there wasn't, I created the group named "root" (didn't add any users as members) and ran updates again and everything updated fine.

Hope that helps and doesn't break anything further.  If somebody with more experienced could comment on how this might be a feasible fix and won't break anything further, it would be nice =)  But everything seems to be working ok for me now that I did that.

---

### Post by Sonicgoo on 2007-06-24
> **Jussi Kukkonen said:**
> You of course shouldn't have to do this at all, but... You can use dpkg-statoverride program to edit the file, see *man dpkg-statusoverride*. Maybe something like:
```
dpkg-statoverride --remove /var/run/hplip
```

Thanks that worked out.

---

### Post by Sonicgoo on 2007-06-30
So I guess that didn't work out so well, now I have this error when I try and install or uninstall something. 

hplip: subprocess post-installation script returned error exit status 2

So probably want to recreate the hplip?

---

### Post by TechnoBabble4444 on 2007-10-14
Thanks man, That completely solved my problem, too.

Edit:
Oh wait, actually i have the same problem as Sonicgoo.

---

### Post by studotwho on 2009-09-29
I had something smilar:[INDENT][FONT=Courier New]**# apt-get install ddclient**
[COLOR=Blue]Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libio-socket-ssl-perl libnet-libidn-perl libnet-ssleay-perl
The following NEW packages will be installed:
  ddclient libio-socket-ssl-perl libnet-libidn-perl libnet-ssleay-perl
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/343kB of archives.
After this operation, 1528kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
[B][COLOR=DarkOliveGreen]dpkg: unrecoverable fatal error, aborting:
 syntax error: unknown group `mlocate' in statoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)[/COLOR][/B][/COLOR][/FONT]
[/INDENT]I have fixed this problem.

The problem was related to the contents of /etc/group.

I had been running my server a very long time and needed to rebuild it.  I wanted to keep the groups from my old server installation on the new one as I have some external drives attached that are ext2/3 that have permissions stored that are in groups.

I orinally saved /etc/group as /etc/group.default and then copied the group file from my old installation.

After reaching this problem and reading this forum post I noticed the error here states "unknown group `root`, where mine said `mlocate`.  When did this:[INDENT][FONT=Courier New]**# cat /etc/group.default |grep mloc**
[COLOR=Blue]mlocate : x : 106 :[/COLOR][/FONT]
[/INDENT][INDENT]*(I had to put spaces in above to stop text being converted to a smiley)*
[/INDENT]it was clear that I needed to put this 'mlocate' group back onto the system.

To fix it I did:

[LIST=1]
[*]`cat /etc/group`
[*]selected the groups I wanted to preserve for the new installation and copied those lins to the clipboard (user created groups are usually >1000
[*]`cp /etc/group.default /etc/group`
[*]`nano /etc/group`
[*]pasted the lines into the bottom of the file and saved the new /etc/group
[*]ran apt-get again and it's working again
[/LIST]
Hopefully that helps someone.

 -studotwho.

---

### Post by angshu on 2011-09-07
I am getting a similar problem but not quite the same. I cannot seem to install any packages via apt-get. All of them fail with the same error. Is this problem known and is there a way to build the package database again?


sudo apt-get install scons
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  scons
0 upgraded, 1 newly installed, 0 to remove and 364 not upgraded.
Need to get 0B/591kB of archives.
After this operation, 2,519kB of additional disk space will be used.
dpkg: unrecoverable fatal error, aborting:
 syntax error in statoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

