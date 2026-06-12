---
title: "Recent Difficulty With Updates"
date: 2015-01-07
forum: New to Ubuntu
---

### Post by Javelin Dan on 2015-01-07
I have been trying to run updates (out of command line, Synaptic and Software Center) on three different computers for about 10 days. In each case of Synaptic or Software Center, I would get the repository download error message attached. With the command line attempt, it seemed to run normally, but would show zero updates installed. This kept happening until yesterday when I was finally able to update one of my computers. Another one I tried to update today. I still got the message, but there still was a very large update downloaded including a kernel update. When I ran Computer Janitor afterward, it was possibly the largest clean-out of cruft I have witnessed. Through this entire 10-day (or so) period, I have had uninterrupted use of my internet.

I DO realize this stuff is all done by volunteers and that they like to take time off during the holidays too, but I was just wondering if there have been any other problems with availability to the repositories and if there is anything else I should know about or do. Thanks.

---

### Post by QIII on 2015-01-07
Hello!

The example you posted is a PPA (Personal Package Archive).  It is not part of the official Ubuntu repos.

If the maintainer of that PPA no longer supports whatever you have installed from there, has moved the PPA or has taken it off line, you will get such errors.  There is nothing much we can do about it.  You might try to contact the maintainer.

For now, you can use synaptic to deactivate the PPA to avoid the message.

---

### Post by grahammechanical on 2015-01-07
What version of Ubuntu are you using? I an using Vivid Vervet. It is Ubuntu 15.04 during its development period. I update every day and usually there are many mega bytes of updates but over the holiday period there have been only a few kilo bytes to download. Such is life.

When we are using a released version of Ubuntu we should not expect lots of updates. This is because there is a policy for updating what are called stable releases and this policy is strictly enforced.

[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

and then there is the Phased Updates policy that has been introduced over the last 12 to 18 months

[https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)

The purpose is to keep the LTS releases stable and to reduce the risk of a bug fix breaking something. Which can happen. As for that error message, it speaks for itself. You have a Personal Package Archive (PPA) that cannot be accessed by the Update Manager. Some software provided through a PPA do receive updates but other software does not. It all depends on the developer of that particular piece of software. To stop getting that error message disable the PPA from your software sources.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Regards.

---

### Post by JeQhdMD on 2015-01-07
Even some of the registered "mirror servers" (typically hosted at large sites at colleges, universities, non-profits, etc.) will go offline for maintenance or have their own ISP provider issues.   

In those cases, I either de-activate (unselect that mirror-source) and re-run the Ubuntu utility to search for the fastest download mirrors.   90+% of the time that will take care of the issue, although sometimes it is caused by package mgmt software issues.   Very seldom if ever (in my experience since 2003) is the issue related to the distro itself.

When a person uses PPA's in their sources file . . . these kind of situations are more likely (even though not common for known, trusted PPA's).

---

### Post by coffeecat on 2015-01-07
The error you are getting is from a sub-directory of [http://ppa.launchpad.net/piotr-zagawa/ma2/ubuntu/dists/trusty/](http://ppa.launchpad.net/piotr-zagawa/ma2/ubuntu/dists/trusty/) which also gives a 404. If, however, you go to this URL:

[http://ppa.launchpad.net/piotr-zagawa/ma2/ubuntu/dists/](http://ppa.launchpad.net/piotr-zagawa/ma2/ubuntu/dists/)

You will see there is only one sub-directory for Precise. There is not one for Trusty. That PPA maintainer appears to be only supporting Precise (12.04)

How did you get a non-existent URL for Trusty in your sources? Whatever the reason, that is your problem. As QIII says, you can disable that PPA in Synaptic.

---

### Post by Javelin Dan on 2015-01-07
Thanks to all! My bad, I forgot to mention the OS is Lubuntu 14.04 LTS on all three machines. I thought at first I may have gotten that message because I installed "Remastersys" on my Compaq Presario and since it is no longer maintained, I think it may show up as an obbsolete PPA. However, the installs of Lubuntu on the other two computers were "clean" from an Ubuntu (official mirror) download iso. All three experienced the error message. I was only startled by it because this is the first time I ever experienced it. But hey, if you folks aren't worried about it, neither am I! 

Since my earlier post, I updated the third computer (Samsung NC10 netbook) with no drama. No error messages, about a four minute download (normal for me) including kernel update, normal amount of cruft cleaned. With that, I'll go ahead and mark this Solved!

---

### Post by coffeecat on 2015-01-07
I'm glad you're happy with what you've been told. However.. 

> **Javelin Dan said:**
> However, the installs of Lubuntu on the other two computers were "clean" from an Ubuntu (official mirror) download iso. All three experienced the error message. I was only startled by it because this is the first time I ever experienced it.

Are you sure it was exactly the same error message? Because if it was you must have added the piotr-zagawa/ma2 PPA to all three machines. See:

[https://launchpad.net/~piotr-zagawa/+archive/ubuntu/ma2](https://launchpad.net/~piotr-zagawa/+archive/ubuntu/ma2)

MyAgenda is described about halfway down this page:

[http://www.omgubuntu.co.uk/2012/08/20-must-have-ubuntu-showdown-apps](http://www.omgubuntu.co.uk/2012/08/20-must-have-ubuntu-showdown-apps)

Remastersys is something else.

---

### Post by Javelin Dan on 2015-01-07
I'll take a look. Thanks!

---

