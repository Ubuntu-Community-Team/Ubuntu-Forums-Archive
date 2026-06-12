---
title: "[SOLVED] Must be On-Line to Start Gnome?????"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by Kellemora on 2008-09-23
Hi Gang

I just lost about 3 hours of work trying to figure out WHY nothing in Ubuntu would work this afternoon.

Ubuntu is the ONLY OS on the particular machine in question.
Always worked fine, NO Problems, Ever!

Switched monitors and it adjusted to that just fine too.

Moved the box to a new location after a shut down.  Did a cold boot and BAM, Big error message about Gnome not being able to load it's Daemon.  

Tried putting the old monitor back, same problem.
Could NOT get ANY Terminal to open.
No Application would open.
It would show on the lower panel for a few seconds then go away.

Booted into failsafe and did a sudo dpkg-reconfigure -phigh xserver-xorg and then rebooted.
Although I got no more error messages, nothing would work.

I plugged the network cable back in and rebooted, then everything started working again.  Unplugged the network cable and rebooted, back to the same problems.

Does this mean that Ubuntu MUST be used ON-LINE in order to use GNOME??????

In other words, as long as I'm on-line, everything works great, no problems.  But pull the plug and you can't even boot up!

Is there a setting somewhere that says work-offline that you cannot get to unless you do it before shutting down while on-line?

Curious minds want to know, hi hi.....

TTUL
Gary

---

### Post by Pro-reason on 2008-09-23
All I can think is that there must be some sort of hostname and IP-address error, which is affected by being part of a network.

---

### Post by Tatty on 2008-09-23
What is the exact error message you get?

---

### Post by Kellemora on 2008-09-24
Hi Tatty & Pro

I no longer get the error messages to jot them down.

But here is what happens when the LAN cable is unplugged, which also connect me to the internet.

ANYTHING I try to open from like Applications or System from the top panel, it appears in the bottom panel like it normally does when you open something, like Terminal for example.  But Terminal NEVER Opens and eventually the info in the lower Panel goes away.

If I plug the LAN cable back up, then all works fine again.

I did an Ubuntu install on a small 4 gig drive I have laying around without the computer connected to the LAN and it loaded and ran fine.

So it's obviously something I changed or IS changed when you Install Ubuntu while connected to a LAN/Cable Internet?

It's no biggie really since all of my computers are linked, BUT, what if the cable goes out?  Then Ubuntu won't work?????

Just an oddity that has me slightly confused for now.

As an aside, something interesting about that 4 gig hard drive.
Ubuntu shows it as being 7.5 gigs, used 4.4 gigs, available 3.0 gigs.  It's ONLY a 4 gig hard drive!

Thanks for the help and things to look for!

TTUL
Gary

---

### Post by Pro-reason on 2008-09-25
I don't think it is anything to do with the Internet.  If you like, you can connect all your computers to the LAN, but disable the LAN's access to the Internet.  I bet it still works OK.

Post the output of this:
```

ifconfig
cat /etc/hostname
cat /etc/hosts
uname -a

```

You could also try pulling the plug and then typing “ifconfig” again into the same window.

---

