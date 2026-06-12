---
title: "installed repository query"
date: 2015-09-29
forum: New to Ubuntu
---

### Post by spandan_pradhan on 2015-09-29
I recently upgraded from ubuntu 12 to ubuntu 14.04, i want to know which repository i had installed in ubuntu 12 or which repository i am using now or do i have to install new repo ?

---

### Post by grahammechanical on 2015-09-29
Each version of Ubuntu has its own set of repositories. If you go to /etc/apt/ you will find a file called sources.list. Open that file in Gedit and you will see the URLs for the software sources/repositories for your version of Ubuntu. When you were using 12.04 the URLs had the word "precise" as part of the URL. Now that you are using 14.04 the URLs have "trusty" as part of the URL. You will see this fact also if you run this command.

```
sudo apt-get update
```

You can also go to System Settings>Software & Updates and see what repositories are enabled. But why do you think that you need to install a new repository? If we add a repository such as a PPA and then we upgrade, the PPA will be disabled to prevent the upgrade from breaking. You see the maintainer of the PPA needs to provided URLs for each version of Ubuntu. And some PPAs are not maintained and cannot be used with a newer version of Ubuntu.

Regards.

---

### Post by ian-weisser on 2015-09-29
See your current list(s) of sources (repositories) at /etc/apt/sources.list and /etc/apt/sources.list.d/
If you really installed Ubuntu 14.04 using the proper Ubuntu 14.04  installer, then you should have the proper repositories on that list  ('installed').
Those lists may or may not still contain your old release ('12') information. If not, that information is gone forever.

Your question is worded in a way that suggest you may not fully understand how sources (repositories) work yet. Are you asking for some specific reason?

---

### Post by spandan_pradhan on 2015-09-29
@[**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323") : Thanks for the prompt reply.

I was skeptical if i need to update repository also , after upgrading to new version. I am also getting errors since i upgraded to new version.

---

### Post by spandan_pradhan on 2015-09-29
@ian-weisser: Thanks for the reply. 
I did the third party disable and remove obsolete package which was asked during upgrade process. 
Also , i am getting some errors since installation.

---

### Post by ian-weisser on 2015-09-29
> **spandan_pradhan said:**
> I did the third party disable and remove obsolete package which was asked during upgrade process. 

Ah, so you did not *install*. You did a *release-upgrade*. Very different than an install.

You also did not disable your non-Ubuntu repositories nor uninstall your non-Ubuntu software before doing your release-upgrade.
Non-Ubuntu software and sources are the #1 cause of failed release-upgrades.


> **spandan_pradhan said:**
> Also , i am getting some errors since installation.

What kind of errors?
Please show us the entire output of a session containing an example of such errors.

---

### Post by spandan_pradhan on 2015-09-29
Sorry , Ubuntu 14.04 has experienced an internal error,

executable path /usr/sbin/cupsd

and

sorry gtk-update-icon-cache-3.0 has stopped unexpectedly

---

