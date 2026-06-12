---
title: "update &amp; upgrade latest fresh installed Ubuntu 12.04 causes a conf problem"
date: 2012-06-05
forum: New to Ubuntu
---

### Post by Houmie on 2012-06-05
Hi,


I have taken the Ubuntu 12.04 LTS 64Bit AMI from here:

[http://alestic.com/](http://alestic.com/)

And installed it as an Amazon EC2 instance.

I logged in via SSH and did a
```
sudo get-apt update
```
and then did a
```
sudo get-apt upgrade
```


During the upgrade I got this message (see screenhot):

[IMG]http://i.imgur.com/wjPk5.png[/IMG]

It says 

**Configuring grub-pc**

A new version of configuration file /etc/default/grub is available, but the version installed currently has been locally modified. What do you want to do about the configuration file grub?

Since this is a fresh installation of Ubuntu on Ec2, there is no change from my side, so it must be something set for Amazon EC2. What do you guys suggest to do? Anyone else came across this?

Many thanks for you help,
Houman

---

### Post by editheraven on 2012-06-05
It's always safe to keep the current config and then do a update-grub as root.

---

### Post by Houmie on 2012-06-05
Hi,

Thank you for your reply.

It seems no one in the Ec2 community has attempted an upgrade to the latest canonical images, since I see no other post around this very obvious issue.  Once again I am a pioneer. ha! ;-)

I have now looked at some of the comparison options it was providing, such as "show the differences between version"

[IMG]http://i.imgur.com/XyBCe.png[/IMG]

Here you can see two changes the like with GRUB_HIDDEN_TIMEOUT_QUIET=true seems no longer commented out.
According to the documentation this means 

+GRUB 2 can display a countdown timer to provide visual feedback on the time remaining until the default selection is chosen. The timeout setting is enabled in /etc/default/grub (GRUB_HIDDEN_TIMEOUT_QUIET)+

the other change seems to be GRUB_TERMINAL=console, which is now commented out. which isn't clear to me what it means. It seems to enable the graphical terminal.

There is another option to do a "show a side-by-side difference between the versions"

[IMG]http://i.imgur.com/Gcte2.png[/IMG]

At first this might look scary, but all it does is showing each line twice, before and after. 
You can spot the same two lines have a | in between, which is meant to indicate a change in that line. Therefore quiet timeout is set to true and enable the graphical terminal.


Therefore I think the current version is the previous version and the newer version is the one from the package maintainer.
Hence we want to keep the current version and keep the GRUB_TERMINAL=console and commenting out GRUB_HIDDEN_TIMEOUT_QUIET.

Do you agree? :)

---

### Post by editheraven on 2012-06-05
It's ok.

---

