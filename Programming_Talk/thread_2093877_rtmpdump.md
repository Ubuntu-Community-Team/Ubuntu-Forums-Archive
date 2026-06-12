---
title: "rtmpdump"
date: 2012-12-12
forum: Programming Talk
---

### Post by iebo on 2012-12-12
Hello i need help  to make bash script from this commands 

1.sudo iptables -t nat -A OUTPUT -p tcp --dport 1935 -m owner  \! --uid-owner usernamexx  -j REDIRECT 

2.sudo su usernamexx

3. start  rtmpsuck


i 'm not sure if that possible but i would like to get help

---

### Post by TheFu on 2013-07-05
I realize this is late, but .... did you try this?

```
#!/bin/bash
sudo iptables -t nat -A OUTPUT -p tcp --dport 1935 -m owner \! --uid-owner usernamexx -j REDIRECT
sudo su usernamexx
rtmpsuck
```

The simple shell scripts are really just commands that you would normally type into a shell prompt.

Of course, there are coding techniques to make the script "smarter" or more bullet proof, but those aren't needed for something this small.

The only changes I'd make would be to parametrize the username and to specify the full path to programs called like rtmpsuck.  Trusting a PATH is dangerous and considered poor form - though on a single-user system, it will usually work.

```
#!/bin/bash
USER=usernamexx
SUDO=/usr/bin/sudo
IPT=/sbin/iptables
RTMPSUCK=/usr/sbin/rtmpsuck

$SUDO $IPT -t nat -A OUTPUT -p tcp --dport 1935 -m owner \! --uid-owner $USER  -j REDIRECT
$SUDO su $USER
$RTMPSUCK
```

Simple.

It might be nice to setup sudo for these specific commands to not require a password too.  The sudo and sudoers **man pages** explain how-to clearly.

---

### Post by iebo on 2013-07-09
tnx i didn't realized that someone answer my question after 7 months i think its working =D>... but the program "rtmpsuck" does not show up in terminal that it has been started even though its running  

  normally i  have  this 
> RTMP Proxy Server v2.4 df6c518~git
(c) 2010 Andrej Stepanchuk, Howard Chu; license: GPL

Streaming on rtmp://0.0.0.0:1935



i made another thread before reading your solution](*,) 

[http://ubuntuforums.org/showthread.php?t=2161227&p=12724939#post12724939](http://ubuntuforums.org/showthread.php?t=2161227&p=12724939#post12724939)

---

### Post by TheFu on 2013-07-14
Sorry for the delay. It has been one of the roughest weeks of my life and there are very few things that can happen which will be worse in the future.

I skimmed the other thread - I don't think the last answer about running all the commands as sudo understands that setup you are trying to accomplish. It is important that the rtmpsuck command NOT be run as root/sudo.

OTOH, it could be very helpful to remove the iptables rule when you are completed. That would be better than rebooting the box every time, right?

---

### Post by iebo on 2013-07-14
np ,thanks for being here to answer my questions this become much easier 
yes i remove the rule with   sudo iptables -t nat -F  :popcorn:i would use rtmpdump over rtmpsuck but it never worked for me  

cheers

---

### Post by TheFu on 2013-07-15
In my searches, it appears that most people use the highly manual method of rtmpdump for some reason.  I guess rtmpsuck doesn't work for their needs?  For me, it seems 1000x easier, but to each their own.

---

### Post by iebo on 2013-07-17
yes rtmpdump is the typical tool for this task rtmpsuck used much more  when someone trying  to find the source of video feed while playing it  on browser ..  of course  the website must support this protocol "rtmp" ,both  tools are good and does help u to download live shows :D

---

