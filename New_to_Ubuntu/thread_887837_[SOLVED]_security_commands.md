---
title: "[SOLVED] security commands"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by Toliot on 2008-08-12
hey guys i was wondering what are some security like tools like nmap and telnet that are on ubuntu and what are the commands for them?
im wondering about this bcuz i wanna do some security testing if u can plz tell me some good security toos and how i can use them and install them thx so much :)

---

### Post by tamoneya on 2008-08-12
nmap can easily be installed as it is in the repositories:```
sudo apt-get install nmap
nmap -v -A 127.0.0.1
```
As for telnet that is a protocol not a program.  So, yes ubuntu supports telnet.

You should also look at wireshark. [http://www.wireshark.org/](http://www.wireshark.org/)

---

### Post by Toliot on 2008-08-12
> **tamoneya said:**
> nmap can easily be installed as it is in the repositories:```
sudo apt-get install nmap
nmap -v -A 127.0.0.1
```
As for telnet that is a protocol not a program.  So, yes ubuntu supports telnet.

You should also look at wireshark. [http://www.wireshark.org/](http://www.wireshark.org/)

no i already have telnet and nmap and i know how to use them and what is wireshark whats it for? how do i set it up? thx:)

---

### Post by t0p on 2008-08-12
If you want to know the commands for nmap, check out its man pages - ie, in terminal type

```
man nmap
```

For a "friendlier" nmap experience, install its GUI front end, **zenmap**

```
sudo apt-get install zenmap
```

The **telnet** protocol works in Ubuntu, again read its man pages.

**Netstat** is another useful tool for network security issues.

---

### Post by tuxxy on 2008-08-12
> Wireshark is a network traffic analyzer, or "sniffer", for Unix and Unix-like operating systems. A sniffer is a tool used to capture packets off the wire

[http://packages.ubuntu.com/hardy/wireshark](http://packages.ubuntu.com/hardy/wireshark)

[http://en.wikipedia.org/wiki/Wireshark](http://en.wikipedia.org/wiki/Wireshark)

---

### Post by t0p on 2008-08-12
> **Toliot said:**
> what is wireshark whats it for? how do i set it up? thx:)

Tamoneya already referred you to the wireshark website.  You'll find the answers to your questions there.

---

### Post by Toliot on 2008-08-12
> **t0p said:**
> Tamoneya already referred you to the wireshark website.  You'll find the answers to your questions there.

yeah thx but what are some other security/network tools?

---

### Post by tamoneya on 2008-08-12
> **Toliot said:**
> no i already have telnet and nmap and i know how to use them and what is wireshark whats it for? how do i set it up? thx:)

Click here: [apt://wireshark]("apt://wireshark")

---

### Post by tamoneya on 2008-08-12
> **Toliot said:**
> yeah thx but what are some other security/network tools?

we have give several suggestions.  You should have plenty of stuff to try out.  Is there something specific that you are looking for.  Something that accomplishes some specific task.

---

### Post by finer recliner on 2008-08-12
download, burn, and boot backtrack3 distro. it has everything you would ever want and more.


good luck finding documentation on how to use the included tools though.

---

### Post by barney385 on 2008-08-12
> **Toliot said:**
> yeah thx but what are some other security/network tools?

You might want to look at kismet and airsnort...

Both are in the repos I believe.

I think you have to have certain NIC's to use them properly though.

---

### Post by t0p on 2008-08-12
> **Toliot said:**
> yeah thx but what are some other security/network tools?

Open synaptic (**System > Administration > Synaptic Package Manager**) and use its search function - ie, in the search field, type "security".  This will turn up all the security-related apps you could wish to find. :)

---

### Post by Toliot on 2008-08-12
> **tamoneya said:**
> we have give several suggestions.  You should have plenty of stuff to try out.  Is there something specific that you are looking for.  Something that accomplishes some specific task.

something to scan ports and find ips on a website and stuff related to telnet thx :) and backtrack 3 doesnt rly let me run anything when i open it it doesnt fit on my screen :s if u could help me how i could fix that that would kik*ss thx :)

---

### Post by Toliot on 2008-08-12
> **t0p said:**
> Open synaptic (**System > Administration > Synaptic Package Manager**) and use its search function - ie, in the search field, type "security".  This will turn up all the security-related apps you could wish to find. :)

hey thx im gunna try that right now :)

---

### Post by tamoneya on 2008-08-12
> **Toliot said:**
> something to scan ports and find ips on a website and stuff related to telnet thx :) and backtrack 3 doesnt rly let me run anything when i open it it doesnt fit on my screen :s if u could help me how i could fix that that would kik*ss thx :)

scan ports: nmap
find IPs: ping google.com
telnet: use the built in telnet command: [http://nersp.cns.ufl.edu/~dicke3/nerspcs/telnet.html](http://nersp.cns.ufl.edu/~dicke3/nerspcs/telnet.html)

---

### Post by Toliot on 2008-08-12
> **barney385 said:**
> You might want to look at kismet and airsnort...

Both are in the repos I believe.

I think you have to have certain NIC's to use them properly though.

can u explain to me how to install kismet and airsnort? thx

---

### Post by tamoneya on 2008-08-12
kismet [click here]("apt://kismet")

As for airsnort you have to compile from scratch as they detail on their site.

[http://airsnort.shmoo.com/](http://airsnort.shmoo.com/)

---

### Post by barney385 on 2008-08-12
> **Toliot said:**
> can u explain to me how to install kismet and airsnort? thx

I didn't have the right NIC to use it.

Go to their website for more info...

I tried to post the link, but it keeps becoming corrupted?

sorry

---

### Post by Toliot on 2008-08-12
> **tamoneya said:**
> kismet [click here]("apt://kismet")

As for airsnort you have to compile from scratch as they detail on their site.

[http://airsnort.shmoo.com/](http://airsnort.shmoo.com/)
so how would i compile them from scratch :P(sry noob talking)

---

### Post by tamoneya on 2008-08-12
> **Toliot said:**
> so how would i compile them from scratch :P(sry noob talking)

Like i said there are instructions on their site. This is directly quote from the page I linked:>     # tar -xzf airsnort-0.2.6.tar.gz
    # cd airsnort-0.2.6
    # ./configure
    # make
    # make install       (optional)


You should however read that whole first page.  Read it and try to get it compiled first.  Then reply here and we will help you out.  We are glad to help here but we also expect you to do some of the work yourself.

---

### Post by Toliot on 2008-08-12
> **tamoneya said:**
> Like i said there are instructions on their site. This is directly quote from the page I linked:

You should however read that whole first page.  Read it and try to get it compiled first.  Then reply here and we will help you out.  We are glad to help here but we also expect you to do some of the work yourself.

sry for asking this but how do i find the tar. file bcuz it said Cannot open: No such file or directory:confused:

---

### Post by Nerdriot on 2008-08-12
> **Toliot said:**
> sry for asking this but how do i find the tar. file bcuz it said Cannot open: No such file or directory:confused:

You could just use, say, "sudo apt-get install aircrack-ng". It's term-based, but it's still just as powerful. Plus, you don't have to compile any source (unless you just WANT to).

---

### Post by tamoneya on 2008-08-12
> **Toliot said:**
> sry for asking this but how do i find the tar. file bcuz it said Cannot open: No such file or directory:confused:

by following the download link you eventually get here: [http://sourceforge.net/project/downloading.php?group_id=33358&use_mirror=voxel&filename=airsnort-0.2.7e.tar.gz&79430970](http://sourceforge.net/project/downloading.php?group_id=33358&use_mirror=voxel&filename=airsnort-0.2.7e.tar.gz&79430970)

This allows you to download the tar.gz file.

---

### Post by Toliot on 2008-08-12
> **Nerdriot said:**
> You could just use, say, "sudo apt-get install aircrack-ng". It's term-based, but it's still just as powerful. Plus, you don't have to compile any source (unless you just WANT to).

thx i got it installed :)

---

### Post by nicedude on 2008-08-12
How to use Nmap and Wireshark well -> thats like a degree in computer security penetration right there as there are no easy answers for how to use these tools since they are extremely complex and require you to have allot of knowledge about how networks work. I would focus on some simpler tools to start like maybe "angry ip scanner" you can't get it from the repositories but you can get it in a deb package simple install from deb you find with a google search. If you are having problems unzipping things and haven't learned how to compile a program from source code yet then I would recommend you start looking at things like that to learn first. Then once you feel comfortable with things like that you could start trying hacker tools ( since with allot of them Ubuntu doesn't have the newest versions anyway and you will need to compile your own from source code ) . But by all means the suggestion to get a backtrack3 disk is a great one but I would tell you not to expect to be breaking into anything without allot more knowledge about what your doing, but hey BT3 is live disk so you can't break anything so go nuts. Also I didn't see anyone mention it but if you want to learn Nmap then you might try installing Zenmap from the repositories since it is a GUI frontend for nmap and lets you go through menus etc to craft a scan command and might help you learn what command line parameters do what.

Well Good Luck With Your Learning Adventure

---

