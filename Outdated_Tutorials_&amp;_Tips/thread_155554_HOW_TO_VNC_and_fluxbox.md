---
title: "HOW TO: VNC and fluxbox"
date: 2006-04-05
forum: Outdated Tutorials &amp; Tips
---

### Post by ninocass on 2006-04-05
Hi all, this is amy first HOW TO so any tips/changes are welcomed

I decided to install fluxbox a few weeks ago and found that connecting to my laptop from my desktop through me into the gnome desktop rather than the fluxbox desktop, after some tinkering i managed to get it jumping to the fluxbox logon but the wrong session.  if this is happening to you heres how to fix it.

Theres a version of VNC called x11vnc which is used to view the default session over VNC [exactly what we want]

to set it up
install the x11vnc server
```

sudo apt-get install x11vnc

```

Set the password file
```

x11vnc -storepasswd password /path/to/passfile

ie:
x11vnc -storepasswd letmein /~/.pass

```

Start the server
```

x11vnc -rfbauth /home/nino/pass

```

theres the usual run of options that you get with a VNc server and a faq here:

[http://www.karlrunge.com/x11vnc/#faq](http://www.karlrunge.com/x11vnc/#faq)

Cheers

Nino

---

### Post by Sudo Sumo on 2010-02-11
Thanks dude!  Great post.

For anyone who'd like it to start up automatically, here's what I did:

Edit the ~/.fluxbox/startup file, and make an entry before the "exec fluxbox" line.

```

x11vnc -rfbauth /home/myusername/.vncpass &

# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

exec fluxbox

```

Reboot, that ought to do it!

---

