---
title: "joining NT domain"
date: 2008-05-20
forum: Oregon Team - US
---

### Post by Garmuar on 2008-05-20
Did Hardy Heron have a tool to authenticate to NT domain?  I had thought it did.  I have 2 Advanced 2000 servers,running AD, along with assorted 2003 servers, and I need to add new ubuntu machines to the domain and connect to Mapped drives and such.

Any help is appreciated.

---

### Post by Lord_Dicranius on 2008-05-21
[likewise-open](https://help.ubuntu.com/community/LikewiseOpen) - That what you're looking for?

---

### Post by Garmuar on 2008-05-21
> **Lord_Dicranius said:**
> [likewise-open](https://help.ubuntu.com/community/LikewiseOpen) - That what you're looking for?

Yes.  Thankyou.

I don't know why I was having trouble finding that application name  in the forum.  I tried every Key word I could think of.  LOL

"Likewise" it is.

---

### Post by Lord_Dicranius on 2008-05-21
hah Yeah, I went Google searching for a bit and finally came across that.  The only stuff I could find on the forums were stuff about manually configuring Winbind and PAM.

Glad that helps :)

---

### Post by Garmuar on 2008-05-21
well it looks like I have to do that next.  I get the same dns errors using the GUI and cli for likewise.

It says it cant find the DC.  and to check if DNS is configured in nsswitch. 

As far as I can tell nsswitch or nsswitch.conf does not exit.

I got winbind installed but then I still couldn't find nsswitch in /etc or any place else.  I am rather confused at this point.

when trying sudo domainjoin-cli join My.domain username
i get: sudo can not resolve host name "username-desktop"
Then I enter password and get the "cant resolve DC name" error.

Something is not right. lol

---

### Post by Lord_Dicranius on 2008-05-21
No nsswitch.conf?  Weird.  A little checking, the base-files package is supposed to contain that file.  I'm assuming the command isn't working because the nsswitch.conf file is missing.  Checking my default 8.04 install (desktop install), nsswitch.conf exists on my system (/etc/nsswitch.conf).

My nsswitch.conf:
```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

---

### Post by Garmuar on 2008-05-22
Alright.  I cd to etc and ls which shown me that nsswitch.conf is there.  what do I have to do to access it.  Everything i try says: unknown command.

OK, I sudo vi /etc/nsswitch.conf and the out put was identical to yours above.  I saw no reference to Winbind in these settings.  What configuration change must be made so likewise can resolve my Windows DC host name?

There is a really good chance that at I have absolutely no idea what I am doing. LOL

---

### Post by Lord_Dicranius on 2008-05-22
When I went back and re-read your previous post, reading the issues with DNS and resolving the host name, "resolv.conf" came to mind.  resolv.conf handles hostname resolutions on any "extra" domains other than the local machine (you can read more about resolv.conf in its man page too).

I found a really neat and thorough guide for likewise-open [here](http://www.likewisesoftware.com/resources/user_documentation/Likewise-Open-Guide.pdf).  Page 10 starts a check list for things to check to make sure everything is setup correctly.

Hope this helps :)

---

### Post by Garmuar on 2008-05-27
I do not believe things are setup correctly.  I can't even resolve my local hostname on the local machine. lol

here is nsswitch.conf:
 
test@test-desktop:~$ cat /etc/nsswitch.conf
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis


and here is resolv.conf:
test@test-desktop:~$ cat /etc/resolv.conf
nameserver 192.168.1.13======this is my domain controler
nameserver 192.168.1.11======backup domain controler
nameserver 216.174.194.53
test@test-desktop:~$ 

here is my hosts file:
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
192.168.1.102 test-desktop.local
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
test@test-desktop:~$ 


on the likewise applet where you enter domain name to join, I am entering "allamerican" for the domain.  Should it be allamerican.local or should it be the DC its self as in:  [email]servername@allamerican.loca[/email]l???


I can ping everything on the network by IP but I can't resolve any names at all inside the network.  internet has no problem.

I don't know what other info to provide that may help figure this out.  I just don't know enough yet I guess.

---

### Post by Lord_Dicranius on 2008-05-27
I haven't come across anything that says to modify the nsswitch.conf file, so I'm thinking you should be good there (again, I haven't done this myself before, this is just what I'm researching as to try and help you and learn along the way :) ).  The resolv.conf file looks good to me.  As for the /etc/hosts file though, you should have entries for localhost in there at the beginning of the file:

```

127.0.0.1 localhost
127.0.1.1 (machine_name)

```

*substitute (machine_name) with your actual machine name*

The lack of these lines in your /etc/hosts file is probably why you couldn't resolve your localhost/local hostname hehe  As for the part about entering the domain in the likewise-open GUI app, in the likewise-open user manual it just says to enter the FQDN (fully qualified domain name), doesn't say anything about entering the the server name/DC name specifically (which is good if you have a network with multiple DC's, simplifies it a bit).  According to the manual, it also says the GUI will modify the /etc/hosts accordingly.  For example, say your machine name is laptop1 and the FQDN is allamerican.local, the tool will enter the following to /etc/hosts: laptop1.allamerican.local.

I may just have to set something up and see if I can't get this working here soon...

---

### Post by vaporflux on 2008-05-28
I have the exact same problem, Garumar (aside from your issue with being unable to resolve your local hostname - I don't have any problems there). My nsswitch.conf file is identical to yours. I have tried entering all the combinations I can think of for my FQDN in the "Domain" box in the Likewise GUI, and none of them have worked. The domainjoin terminal command gives me the same error. This is the output of the error log when I try to connect using the Likewise GUI after entering my Active Directory username and password:  

[I]Error code: CENTERROR_DOMAINJOIN_UNRESOLVED_DOMAIN_NAME (0x00080026)

Backtrace:
    main.c:297
    djmodule.c:158
    djfirewall.c:685
    djfirewall.c:609
    djfirewall.c:297 [/I]  

I have the DNS server address in my network configuration set to the address of my domain controller. I haven't been able to find any helpful info about configuring Likewise on Ubuntu, just the same stuff Lord_Dicranius found about using windbind and PAM. I have noticed that I can't ping my AD server by name, don't know if that make any difference or not. I haven't been able to find much info about setting a WINS server for Ubuntu, although I have played around with the WINS settings in smb.conf. Any help would be greatly appreciated, as I have no way of sharing files with my Windows 2003 machine until this is resolved.

---

### Post by Garmuar on 2008-05-28
I noticed that there is loopback info in host file but it is IPv6?
I wonder if shuting down IPv6 my rule some things out?  We have no compatible IPv6 devices on your network.

What is the easiest way to shut IPv6 off? I will look for an answer if you feel IP6 may be a problem.

And yes, Vaporflux's errors are the same as mine using both cli and gui when trying to join domain.

---

### Post by Lord_Dicranius on 2008-05-28
I don't think IPv6 is part of the problem, but as you said, might as well rule it out :)

To disable IPv6:
```
gksudo gedit /etc/modprobe.d/aliases
```

then replace this line:
```
alias net-pf-10 ipv6
```

with this:
```
alias net-pf-10 off
```

and reboot.  As for the authentication issues though, I'm at a loss.  There's a few other threads on the forums regarding likewise that you could check out (just search for "likewise" or "likewise-open").  Imma try and get something setup here at my house soon to dink around with this though.  I'll let you know how my experience goes and any problems that I run into :)

---

### Post by Garmuar on 2008-05-28
Thanks lord_D.  I will keep looking for new posts.  Do yo have Advanced Server 2000 laying around the house to play with??  lol   I wish I did. I have to go to work to tinker with Windows AD and Ubuntu.  hehe

---

### Post by Lord_Dicranius on 2008-05-28
Yes, I do have Windows 2k Adv, and a few spare PC's laying around :)

---

### Post by Garmuar on 2008-06-24
It seems Ubuntu appended a "-desktop" to the machine name when I named it upon creation.  I know Microsoft does not like special charectors in names so I removed the "-" making the host name a single word and it worked.  

Now it is telling me to open certain ports and I'll be in business.  
Now I have to learn to open ports. LOL

---

### Post by Lord_Dicranius on 2008-06-30
hah Awesome!  Glad you got it figured out.  I just started a new job, so it's been hectic.  Sorry I didn't get back sooner.

---

### Post by doughall on 2009-11-03
[http://www.itsolutionskb.com/2009/04/adding-ubuntu-to-a-windows-server-2008-active-directory/](http://www.itsolutionskb.com/2009/04/adding-ubuntu-to-a-windows-server-2008-active-directory/)

---

