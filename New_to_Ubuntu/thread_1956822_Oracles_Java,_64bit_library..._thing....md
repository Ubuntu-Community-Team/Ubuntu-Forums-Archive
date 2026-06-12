---
title: "Oracles Java, 64bit library... thing..."
date: 2012-04-11
forum: New to Ubuntu
---

### Post by jerome1232 on 2012-04-11
Ok so I recently installed Oracles Java, I had to add some stuff to /etc/profile as follows

```
JAVA_HOME=/usr/local/java/jre1.7.0
PATH=$PATH:$HOME:/bin:$JAVA_HOME/bin
export JAVA_HOME
export PATH
```

I found that before I ran minecraft I had to run this command for java to find the 64 bit libraries

```
export LD_LIBRARY_PATH="/usr/local/java/jre1.7.0/lib/amd64/"
```

I tried adding that into /etc/profile but I still have to run it before running minecraft. Is there a place to put this export so that it doesn't have to be run prior to minecraft?

I'm not sure if this is specific to minecraft, I guess I can try and find other java programs to try..

---

### Post by jerome1232 on 2012-04-12
Figured it out! Turns out I was victim to this old bug [HERE]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/366728")

The solution was found in comment #21 on that bug.

> I think it is the same problem as [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/380360](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/380360).

I noticed another workaround though:

ssh-agent is already initialised in /etc/gdm/Xsession. Empirically, t seems /etc/gdm/Xsession is initialised before .profile whereas /etc/X11/Xsession.options is initialised after .profile.

As ssh-agent needs to be initialised only once, simply disabling ssh-agent in /etc/X11/Xsession.options stops LD_LIBRARY_PATH from being set to null after .profile has been sourced. This can be done by changing use-ssh-agent to no-use-ssh-agent in /etc/X11/Xsession.options. This still requires root but is simpler..

Once I did that $LD_LIBRARY_PATH was set correctly from my /etc/profile file and everything is just peachy.

My profile ended up looking like this (I moved some stuff around)
```
JAVA_HOME=/usr/local/java/jre1.7.0_03
PATH=$PATH:$HOME:/bin:$JAVA_HOME/bin
export JAVA_HOME
export PATH
export LD_LIBRARY_PATH=$JAVA_HOME/lib/amd64

```

---

