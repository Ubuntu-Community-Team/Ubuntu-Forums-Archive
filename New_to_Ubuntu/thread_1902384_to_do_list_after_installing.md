---
title: "to do list after installing"
date: 2011-12-30
forum: New to Ubuntu
---

### Post by JeremySchubert on 2011-12-30
The following website suggests that one housekeeping task after installing is to "Expand the software repository list' by replacing my source list with his.  Such an action sounds a bit fishy to me...how can I know that his code is correct and wouldn't there be an official source list of some sort on the Ubuntu site somewhere?
[http://theindexer.wordpress.com/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://theindexer.wordpress.com/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

---

### Post by MG&amp;TL on 2011-12-30
[B]I really wouldn't. Things can be out of date, incorrect, or even malicious.
[/B]


Instead (answering the title), update your system, install the "ubuntu-restricted-extras" package, and surf the software centre for anything else you might want. Ubuntu is good enough that you don't need extra repos. if you ever end up using experimental software, I might enable some PPAs, but if you get that far, I'll assume you know what you're doing with that file. :) Rule of thumb: if you're not installing software or updating, root access ("sudo") is bad.

---

### Post by oldos2er on 2011-12-30
After a cursory examination of the blogger's natty.sources.list I don't see anything out of line; he's added Medibuntu and Google. But the advice to delete one's own sources.list is ill-advised without making a backup copy first.

You've done the correct thing by asking here before making any big changes.

---

### Post by MG&amp;TL on 2011-12-30
If you do decide to replace your sources list (ill-advisable), which version of ubuntu are you using? Not much point in enabling natty repos on oneiric...

---

### Post by JeremySchubert on 2011-12-30
Using 11.10.  Don't think I'll revise the list, I don't know enough about this yet to know how much I can trust the author.  

1.  When I go to install restricted extras, I get a message stating that 
-Liav codec library livavcodec53 
-Libav utility library libavutil41
must both be removed.  Can you explain what this is about?

2. 11.10 seems to ship with ver 8 of Thunderbird.  I note the current version is 9.1.  And I've also read that it's recommended to go through the Software Center to get software packages. Does this mean at some point a PPA for Thunderbird 9.1 will show up in the Software Center, or will it naturally update and I'll see an update notification for it at some point?

---

### Post by Miljet on 2011-12-30
Normally whatever version of a software package is shipped with a version of Ubuntu stays at that version. The next version of Ubuntu will pick up the the newer version of that software.

---

### Post by JeremySchubert on 2011-12-30
> he next version of Ubuntu will pick up the the newer version of that software. 	
OK, so if I want to upgrade an app (FireFox for example), do I have to remove the existing version before upgrading to the new version?  Or can I run the install on top of the existing version?  Or is it best not to upgrade until the next version is released?
Thanks,
Jeremy

---

### Post by larrypg on 2011-12-30
Hello,

When it comes to firefox this does not apply.  They update it without having to upgrade to a newer version of Ubuntu.

---

### Post by wildmanne39 on 2011-12-30
Hi, as far as updating other software besides firefox if you do not have a good reason to I would just wait for the next version of ubuntu to come out, it is a bad idea to manually edit your source list it will most likely cause problems with installing applications and updates.
Thanks

---

### Post by oldos2er on 2011-12-30
> **JeremySchubert said:**
> Using 11.10.  

Then you don't want a Natty (11.04) list. Medibuntu is a fairly standard repository to add, see [http://medibuntu.org/](http://medibuntu.org/)

---

