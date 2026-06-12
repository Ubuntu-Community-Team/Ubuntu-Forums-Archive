---
title: "Ubuntu version and sources.list file version different"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by number3 on 2008-05-09
As I was going through the beginners documentation I got to the part where you're supposed to open your sources.list file.

However I noticed that the version, at the top of the file says

Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)

However, I know that I've updated to 8.x and when I click on System - About Ubuntu I see 

Thank you for your interest in Ubuntu 8.04
                - the Hardy Heron - released in April 2008.
				

Also, I know this has nothing to do with the subject of this thread.  But it appears that my regular account is seen as a super user.  Every time I load up an app that requires a password, my regular account appears in the drop down box and I'm requested for my password.

However in an ideal situation, I'd like actions that require special permission to be done by the root.  Meaning that if authentication is required then it should require the root permissions and authentication, rather than just my regular/power user.

Any anyone please help me out with that?

Thanks

---

### Post by overdrank on 2008-05-09
> **number3 said:**
> As I was going through the beginners documentation I got to the part where you're supposed to open your sources.list file.

However I noticed that the version, at the top of the file says

Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)

However, I know that I've updated to 8.x and when I click on System - About Ubuntu I see 

Thank you for your interest in Ubuntu 8.04
                - the Hardy Heron - released in April 2008.
				

Also, I know this has nothing to do with the subject of this thread.  But it appears that my regular account is seen as a super user.  Every time I load up an app that requires a password, my regular account appears in the drop down box and I'm requested for my password.

However in an ideal situation, I'd like actions that require special permission to be done by the root.  Meaning that if authentication is required then it should require the root permissions and authentication, rather than just my regular/power user.

Any anyone please help me out with that?

Thanks

Hi and when you updated to Hardy 8.04 did you leave the grub intact? You may be booting to another kernel.

---

### Post by number3 on 2008-05-09
Hello,

Yes, I did leave my grub in tact.  All I did to upgrade was clicked on System - Administration - <the menu option to get updates>

That was it.  Not sure if I needed to do anything additional after that.

---

### Post by Xiong Chiamiov on 2008-05-09
When you upgrade, your sources.list isn't remade from scratch (thank goodness!), so it keeps the comment that was put there when you first installed on 7.10.  If it bothers you, you can change it, or delete it for that matter.

On the issue of root, there's a nice read [here]("https://help.ubuntu.com/community/RootSudo").

---

### Post by number3 on 2008-05-09
Oh okay.  In that case it's not a big deal.  Just thought there that something might have been missed.

Thanks for the replies.

---

