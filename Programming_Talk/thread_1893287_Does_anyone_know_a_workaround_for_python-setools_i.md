---
title: "Does anyone know a workaround for python-setools in Ubuntu"
date: 2011-12-09
forum: Programming Talk
---

### Post by Dangertux on 2011-12-09
So I'm having an issue with this:[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=645326](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=645326)

Does anyone have a workaround for this or am I kind of out of luck. I'm needing (wanting) to port the RHEL (SELinux toolchain) sandbox python script to make it functional on Debian based distros, unfortunately nobody seems to care about the setools modules, since that bug's status hasn't been updated in a hot minute.


P.S : I know this works fine on RHEL, CentOS , Fedora and pretty much every other non debian distro, however I am wanting to port it for use on debian based distros. So an acceptable solution is NOT use Fedora. Thanks :-)

---

### Post by 11jmb on 2011-12-10
I know that this is no real help, but my response is part curiosity, part trying to narrow down on the problem.

RHEL, CentOS, and Fedora are all Red Hat-based. Does python-setools 
truly work on any non-Debian system (e.g. Arch, Slackware)? Or just Red Hat systems?

I hope somebody here can help you.

---

### Post by Dangertux on 2011-12-10
> **11jmb said:**
> I know that this is no real help, but my response is part curiosity, part trying to narrow down on the problem.

RHEL, CentOS, and Fedora are all Red Hat-based. Does python-setools 
truly work on any non-Debian system (e.g. Arch, Slackware)? Or just Red Hat systems?

I hope somebody here can help you.


It works in gentoo, suse , and slack haven't tried it in arch. Ultimately the problem lies in the bug report I linked, I"m wondering if anyone knows a workaround for that. :-| 

It's something I'd really like the Ubuntu community to have access to functionality wise, and while apparmor can do similar the script I'm wanting to port is both easy and effective to utilize.

Thanks for the reply btw, it's never unhelpful to have an extra opinion or two :-)

---

### Post by 11jmb on 2011-12-10
I'm sure that you have done more extensive google-fu on this than I, but I came across this just in case you haven't seen it: 

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=645008](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=645008)

I guess seinfo is incompatible with Python 2.7? I wonder if it would work on an older Ubuntu release with 2.6.

This kind of thing is way outside of my area, but the forums are pretty quiet on Friday nights, so hopefully I can post help that is slightly better than noise.

---

### Post by Dangertux on 2011-12-10
> **11jmb said:**
> I'm sure that you have done more extensive google-fu on this that I, but I came across this just in case you haven't seen it: 

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=645008](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=645008)

I guess seinfo is incompatible with Python 2.7? I wonder if it would work on an older Ubuntu release with 2.6.

This kind of thing is way outside of my area, but the forums are pretty quiet on Friday nights, so hopefully I can post help that is slightly better than noise.

It's possible I'll give that a shot in the morning thanks for the idea :-)

---

