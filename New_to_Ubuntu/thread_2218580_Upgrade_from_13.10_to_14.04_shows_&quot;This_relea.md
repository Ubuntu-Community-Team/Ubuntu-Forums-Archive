---
title: "Upgrade from 13.10 to 14.04 shows &quot;This release is still in development.&quot; ?"
date: 2014-04-21
forum: New to Ubuntu
---

### Post by nikhilbhalwankar on 2014-04-21
Hi,

I am currently using Ubuntu 13.10 64 Bit release. I just now tried running upgrade from 13.10 to 14.04 release. Surprisingly, I am still getting a below message before proceeding ahead with upgrade,

[h=2]Welcome to the Ubuntu 'Trusty Tahr' development release[/h][COLOR=#000000][FONT=sans-serif]*This release is still in development.* *Do not install it on production machines.*


Please let me know whether this is ok? I will wait for upgrade till I get any inputs on this.


--
Thanks in Advance,
Nikhil Bhalwankar
[/FONT][/COLOR]

---

### Post by nikhilbhalwankar on 2014-04-21
I am currently using Ubuntu 13.10 64 Bit release. I just now tried  running upgrade from 13.10 to 14.04 release. Surprisingly, I am still  getting a below message before proceeding ahead with upgrade,

====================================================================
**Welcome to the Ubuntu 'Trusty Tahr' development release**

[COLOR=#000000][FONT=sans-serif]*This release is still in development.* [I]Do not install it on production machines.
==================================================

[/I][/FONT][/COLOR]
I cancelled it and restarted my laptop. I got automatic prompt which stated that latest version 14.04 is available. You can upgrade. Surprisingly, this is not showing the message stated above. I am getting below message,

=================================================================
[h=2]Welcome to Ubuntu 14.04 'Trusty Tahr'[/h][COLOR=#000000][FONT=sans-serif]The Ubuntu team is proud to announce Ubuntu 14.04 'Trusty Tahr'.
[/FONT][/COLOR]
=================================================================


My question is is it a case that if we use update manager -d for upgrade, the upgrade is done to 14.04 under development release and the one tried after reboot lands you in the actual live release? Please let me know.

---

### Post by Danger_Monkey on 2014-04-21
I found this on the subject:

[LEFT][COLOR=#333333][FONT=UbuntuRegular]According to Ubuntu Engineering Foundations team manager Steve Langasek:[/FONT][/COLOR][/LEFT][INDENT]Upgrades between LTS releases are not enabled by default until the first point release, 12.04.1/14.04.1, scheduled for July/August. It is recommended that most LTS users wait until then before upgrading to 12.04/14.04.

[/INDENT]

---

### Post by grahammechanical on 2014-04-21
Are you using Update Manager to upgrade? Or are you using some command. This command will upgrade to a development version.

```
do-release-upgrade -d
```

The d = development. I have been using Trusty Tahr since the start of development and at first the command lsb_release -a said

> Description: Ubuntu Trusty Tahr (development branch) But after daily updating lsb_release -a now says

> Description: Ubuntu 14.04 LTS

So, I am convinced that we no longer have Trusty development but 14.04. I can only think that you are running the wrong command.

[https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html](https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html)

If you did upgrade and got Trusty Tahr I am sure that an update would change it to 14.04 LTS. I say this because 14.04 is using the same repositories as Trusty Tahr did.  Just as 13.10 is still using the raring repositories.

Regards.

---

### Post by Danger_Monkey on 2014-04-21
I'm not sure why the switch hasn't flipped yet, but when I installed the development release, it clearly said so.  After the release date, it no longer said "development" after I finished all the updating..

[core]
Welcome to Ubuntu 14.04 LTS (GNU/Linux 3.13.0-23-generic x86_64)
[/core]

---

### Post by bapoumba on 2014-04-21
ubuntuforums.org/showthread.php?t=2218672
I had seen a similar thread the other day but could not find it. This one just got posted.

---

### Post by Double.J on 2014-04-21
Sounds a lot like the difference between ```
apt-get upgrade
``` and ```
apt-get dist-upgrade
```

I know that update manager doesn't use apt-get per say, rather aptdeamon directly, but I'd imagine it's this difference between a partial and full upgrade that has drawn the updated welcome file?

Jj

---

### Post by nikhilbhalwankar on 2014-04-22
> **bapoumba said:**
> ubuntuforums.org/showthread.php?t=2218672
I had seen a similar thread the other day but could not find it. This one just got posted.

Its me only. I wanted to post that as a reply to one of the threads related to upgrade issues. It looks like by mistake a new thread got created.

---

### Post by nikhilbhalwankar on 2014-04-22
> **grahammechanical said:**
> Are you using Update Manager to upgrade? Or are you using some command. This command will upgrade to a development version.

```
do-release-upgrade -d
```

The d = development. I have been using Trusty Tahr since the start of development and at first the command lsb_release -a said

 But after daily updating lsb_release -a now says



So, I am convinced that we no longer have Trusty development but 14.04. I can only think that you are running the wrong command.

[https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html](https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html)

If you did upgrade and got Trusty Tahr I am sure that an update would change it to 14.04 LTS. I say this because 14.04 is using the same repositories as Trusty Tahr did.  Just as 13.10 is still using the raring repositories.

Regards.


Thanks a lot. I will check the link which you provided. Meanwhile, below is one more input from my side.

I cancelled upgrade and restarted my laptop. I got automatic prompt which  stated that latest version 14.04 is available. You can upgrade.  Surprisingly, this is not showing the message stated above. I am getting  below message,

==================================================  ===============
**Welcome to Ubuntu 14.04 'Trusty Tahr'**

[COLOR=#000000][FONT=sans-serif]The Ubuntu team is proud to announce Ubuntu 14.04 'Trusty Tahr'.
[/FONT][/COLOR]
==================================================  ===============

So it looks like, after reboot the Ubuntu installation is automatically firing correct command.

---

### Post by bapoumba on 2014-04-22
> **nikhilbhalwankar said:**
> Its me only. I wanted to post that as a reply to one of the threads related to upgrade issues. It looks like by mistake a new thread got created.

OK, I merged the two threads.

---

