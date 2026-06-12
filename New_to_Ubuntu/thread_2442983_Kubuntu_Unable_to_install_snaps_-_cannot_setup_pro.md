---
title: "Kubuntu Unable to install snaps - cannot setup profiles for snap &quot;&lt;app name&gt;&quot;:"
date: 2020-05-10
forum: New to Ubuntu
---

### Post by bvz on 2020-05-10
**[COLOR="#0000FF"]EDIT: I rebooted my system and it seems to be working now. I will leave this post up in case anyone else has the same issue. Still no snaps listed in the software center though[/COLOR]**

Hello,

I am new to Ubuntu and new to snaps, but relatively comfortable in Linux (and the command line).

I am curious about snap packages and want to give them a try. Unfortunately, I cannot seem to get them to install.

1st - the software center does not seem to offer them to me (when I look at a particular app - say Gimp - it shows the source to be ubuntu-focal-universe (Ubuntu 20.04 LTS). That, as far as I know, is not a snap package.

2nd - if I try to install manually via the command line:

```
sudo snap install gimp
```

I get the following error:

```
error: cannot perform the following tasks:
- Setup snap "gimp" (252) security profiles (cannot setup profiles for snap "gimp": cannot load apparmor profiles: exit status 1
apparmor_parser output:
Cache read/write disabled: interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Warning: unable to find a suitable fs in /proc/mounts, is it mounted?
Use --subdomainfs to override.
)

```


It appears that I am missing something in the kernel?  I am surprised by this because I thought Ubuntu was snap ready out of the box. Or is this because I am running Kubuntu instead of Ubuntu?

Any guidance appreciated.

---

