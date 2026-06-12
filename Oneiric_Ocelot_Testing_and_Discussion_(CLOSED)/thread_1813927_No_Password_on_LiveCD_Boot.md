---
title: "No Password on LiveCD Boot"
date: 2011-07-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by drs305 on 2011-07-28
I just booted the daily build from an ISO on my hard drive. For the first time, I was asked to select a user. 

If selecting the default entry, when I got to the Desktop I could not use "sudo" as there was no password designated for root. Additionally, the "Install" icon did not appear on the Desktop. It was the first item in the Launcher however.

At log in, when I select 'Other' and use [s]"Ubuntu"[/s] "ubuntu" as the user, along with an empty password, the CD boots to a Desktop with the "Install" icon and 'sudo' is available for use (no password required).

This behavior may not be exhibited if booted (normally) via an actual CD, but I thought I'd mention here for those trying to boot from an ISO on a partition, and in case it *does* act the same way when booted from a CD/DVD.

---

### Post by grubu on 2011-07-28
It is just an idea:
As the default user always was called "ubuntu" in lower case with the same permissions 
(no password needed to get root), maybe the team decided to rename the default user to 
"Ubuntu" with a capital U from now on, maybe just for an associating name reason. 
If so the user-folder should then also have changed its name to "/home/Ubuntu" 
in this daily-one, maybe they just forgot to change that also to the login-screen.
But I think this can only be clearly answered by the ubuntu-developing-team.

The only thing I can tell is that in a daily-build which I installed about two weeks ago 
this had not been an issue. Can you specify the daily-build-iso?
Was it this one: [oneiric-desktop-i386.iso]("http://cdimage.ubuntu.com/daily-live/current/oneiric-desktop-i386.iso")            28-Jul-2011 08:29 ?

---

### Post by Starks on 2011-07-28
see the bug i filed a few days ago
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/815271](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/815271)

---

### Post by grubu on 2011-07-28
Aha, good to know but it is a little confusing that drs305 was succesful by logging in as "Ubuntu", hm  :-k ?

---

### Post by drs305 on 2011-07-28
> **grubu said:**
> Aha, good to know but it is a little confusing that drs305 was succesful by logging in as "Ubuntu", hm  :-k ?

That was a typo I think. I expect I used "ubuntu"... I'll change it in the earlier post.

@ Starks - Thanks, subscribed to your report.

---

### Post by mc4man on 2011-07-28
As far as what happens from the live session (try me) login it seems just fine, see 2 options - 
Guest = no sudo. Other > ubuntu = sudo
If you think 'Other' should be top listed (default) and or be filled in w/ ubuntu, or just plain ubuntu  - maybe it will be

Though I could see where someone may think the targeted live session user should be defaulted to a Guest account and if they needed sudo would know to use the ubuntu (other) login.

---

### Post by drs305 on 2011-07-28
> **mc4man said:**
> As far as what happens from the live session (try me) login it seems just fine, see 2 options - 
Guest = no sudo. Other > ubuntu = sudo
If you think 'Other' should be top listed (default) and or be filled in w/ ubuntu, or just plain ubuntu  - maybe it will be

Though I could see where someone may think the targeted live session user should be defaulted to a Guest account and if they needed sudo would know to use the ubuntu (other) login.

The main real problem I saw (once I found the 'install' icon in the Launcher) was that when I used the default user and clicked to install it asked for a password, which of course I didn't have. This could have been because of the way I launched it (via partition ISO and not media) but I don't know. A new user certainly wouldn't know to enter 'ubuntu'.

I did note as it was booting that a message flashed by stating pwconv failed to set /etc/passwd to 600. Don't know if that is normal or not.

---

### Post by mc4man on 2011-07-28
> **drs305 said:**
> The main real problem I saw (once I found the 'install' icon in the Launcher) was that when I used the default user and clicked to install it asked for a password, which of course I didn't have.
I see what you (all) mean now - doesn't seem to make any sense going try me > login, take your pick, instead of try me > directly to ubuntu account. ( where you can add packages, install, ect.
I'd think that the latter would be the way it will be.

---

### Post by jbicha on 2011-07-29
Yes, it's a bug but for now, just click other. Username is ubuntu and leave password blank and hit enter.

---

