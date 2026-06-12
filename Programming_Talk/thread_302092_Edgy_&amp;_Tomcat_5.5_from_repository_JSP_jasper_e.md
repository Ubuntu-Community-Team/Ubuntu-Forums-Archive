---
title: "Edgy &amp; Tomcat 5.5 from repository: JSP jasper error"
date: 2006-11-18
forum: Programming Talk
---

### Post by Robvdl on 2006-11-18
Hi, I'm setting up Ubuntu Edgy Server with Tomcat 5.5 from the universe repositories. I haven't found any examples on the net on how to do this from the actual repositories in Edgy, as most examples seem to install Tomcat 5.5 manually as downloaded from the Apache Tomcat website. But I figured... if Tomcat 5.5 is actually in the repositories, it's ought to work... so why not try to use these instead.

Anyway, I posted this question in the server section, but just don't seem to get any replies. I really want to get Tomcat 5.5 up and running, but just can't seem to find the info about this particular issue with Edgy anywhere.

Rather than reposting the post here and doubling up, I will link to it instead (sorry about this):

[http://ubuntuforums.org/showthread.php?t=301897](http://ubuntuforums.org/showthread.php?t=301897)

---

### Post by Robvdl on 2006-11-18
I have found out that this is because of a bug in Debian (#393905), apparently it is already fixed in Debian with Tomcat 5.5.20-1, but not yet in Edgy.

[https://launchpad.net/distros/ubuntu/+source/tomcat5.5/+bug/69043](https://launchpad.net/distros/ubuntu/+source/tomcat5.5/+bug/69043)

In other words, looks like a manual install is required for now to get Tomcat 5.5 going in Edgy, but let's hope it gets fixed for Feisty :-)

---

