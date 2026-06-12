---
title: "Adding repositories for custom installed software"
date: 2013-05-02
forum: New to Ubuntu
---

### Post by DenHeldert on 2013-05-02
Hello,

I have Ubuntu 13.04 installed together with the KDE desktop environment.
As recommended in many places, I only install software using the Software Center. (recommended for beginners, that is)
I feel, - no, I noticed - I am missing out on software-updates.

I wanted to install the Virtualbox Extension Package, and it was not available for the release I have installed.
(4.2.10 vs 4.2.12) I could not find a repository so that leaves me with an outdated (not in the long run obsolete though) version.

KeePass gave me a notice that an update is available.
I searched Google for an Ubuntu repository and right away the Update Manager gave me an update notice.
Same for SABnzbd - I added the repository and it was automatically updated like any other part of Ubuntu.

Now my question:

- how do I automatically add all software repositories, so that I do not  have to search Google to find repositories for every piece of software I  install in order to update them automatically?
- Is this even possible?

Regards,

Nick.

---

### Post by alan9800 on 2013-05-02
you may use [launchpad]("https://launchpad.net/") for finding the PPAs (i.e. the software repositories) you need of.

---

### Post by DenHeldert on 2013-05-02
How? What do I do when I'm at the launchpad website?
So this means I have to lookup repositories by hand?
Is there is no automated way of adding them, even when I obtained the software from within the software-center?

When I type ´virtualbox ppa´ in the searchbox I find this:
[INDENT]
[I]Adding this PPA to your system
You can update your system with unsupported packages from           this untrusted PPA by
adding ppa:debfx/virtualbox           to your system's Software Sources.[/I]
[/INDENT]
[INDENT][/INDENT]

How do I know if I can can trust this ppa?

Regards,

Nick.

---

### Post by ibjsb4 on 2013-05-02
> How do I know if I can can trust this ppa?

Look at what it says.

> You can update your system with unsupported packages from           this untrusted PPA by adding **ppa:debfx/virtualbox**           to your system's Software Sources.

---

### Post by DenHeldert on 2013-05-02
Yes, that is exactly what I mean.
Because people advise me to only install software using the Software Center, and Launchpad is an external website and stating that the ppa is untrusted...
How do I know whether it is genuine?

Or should I take another road here?

---

### Post by ibjsb4 on 2013-05-02
> Or should I take another road here? 

I would say you should stick with the software center until you feel comfortable with ubuntu.  There's a lot of good ppa's out there and there are bad ones.  A bad one can screw with your entire system  and can make you take to drink :)

Check to see what comments have been made.  Check to see if it being maintain.  The ppa page will tell you when it was last updated.  

There's "ppa-purge" in the software center.  It can remove a ppa and replace it with the stable version.  A nice way to get out of trouble :)

---

### Post by ibjsb4 on 2013-05-02
Is there a reason your looking at vBox ppa?  I use vBox and instead of getting it from the software center,I get it from the site.  Some say (me too) it just works better.

---

### Post by DenHeldert on 2013-05-02
> **ibjsb4 said:**
> Is there a reason your looking at vBox ppa?

Yes there is.
Please read my very first post.

The software I have installed all comes from the software center, but many just do not update until I add a repository myself.
I want the software I pull out of the Software Center to update just like the rest of Ubuntu.
Like I said, please read the first post.

Regards,

[I]EDIT: I slightly edited my main question from
- how do I automatically add all software repositories, so that I do not  have to search Google for every piece of software I  install?

to

- how do I automatically add all software repositories, so that I do not  have to search Google to find repositories for every piece of software I  install in order to update them automatically?[/I]

---

### Post by alan9800 on 2013-05-02
first of all, you've to verify, by using the "Filter" menu in launchpad, if the PPA contains software for your release; for instance, the ppa:debfx/virtualbox is for Ubuntu 12.10 and earlier versions, while you use the 13.04.
The following PPA might be interesting for your needs regarding to virtualbox:
[https://launchpad.net/~jacob/+archive/virtualisation?field.series_filter=raring](https://launchpad.net/~jacob/+archive/virtualisation?field.series_filter=raring)

---

### Post by DenHeldert on 2013-05-02
> **alan9800 said:**
> first of all, you've to verify if the PPA contains software for your release; for instance, the ppa:debfx/virtualbox is for Ubuntu 12.10 and earlier versions, while you use the 13.04.

I will definitely look into that, although I am aware of different Ubuntu versions.

But I think we're driften off my main question here. Sorry if I did not make my question clear.
In no way I ***want*** to use ppa-packages or custom repositories or whatsoever.

I just want to know how to automatically update the software I download off the software center.
Because in many cases, at least on my system, they dont.

---

### Post by alan9800 on 2013-05-02
> **DenHeldert said:**
> I just want to know how to automatically update the software I download off the software center.
Because in many cases, at least on my system, they dont.Software Centre uses the software sources that it finds in the /etc/apt/sources.list and in the /etc/apt/sources.list.d directories and in their subdirectories.
Hence if the link to the source of a given software isn't in those directories there's no way to update that software via Software Centre.

---

### Post by Mopar1973Man on 2013-05-02
Ok. 

The easiest way to plugin a new PPA to your system is using the Synaptic package manager. Which I'm going to assume is not installed. Type or copy and paste to terminal.

```
sudo apt-get install synaptic
```

Then once that's installed then you can fire up Synaptic and go to **Settings** and the **Repositories** then click the **Other Software** tab. Then click the **Add** button. Now you can copy and paste a PPA or type one in by hand.

As for good PPA's and bad one's you'll have to be careful of what you use. I've found a few nVidia driver PPA's that turn my system into a non-booting hung up mess. Backups are a key feature don't get relaxed... Or like in my case I split my /home folder off and create a seperate partition so if the system crashes I can just re-install Ubuntu again and all my personal stuff is rather safe.

---

### Post by ibjsb4 on 2013-05-02
You was clear, I just got lost :) the Extension Package:

[URL="https://www.virtualbox.org/wiki/Download_Old_Builds_4_2"]https://www.virtualbox.org/wiki/Download_Old_Builds_4_2


[/URL]

---

### Post by DenHeldert on 2013-05-02
The 2nd and third replies above make a lot of sense to me, I get that.

So... my fairly limited-computer-skilled brain learned the following today:
- Software downloaded from the software center adds its own repositories in most cases, and will update automatically just fine.
- For software that does not add a repository on its own, and you want it to update automatically, you have to add a repository yourself, there is just no way around that.
- For software that does not automatically update, I search Launchpad for missing ppa's.
- If that doesn't get me anywhere, I can search the developers website, or Google as a last resort.
- I make a backup before updating from a customly added source.


- That is basically how it is done in the Ubuntu-universe.

Correct?

If I got this all right, I'll mark the thread as solved.

---

### Post by ibjsb4 on 2013-05-02
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by DenHeldert on 2013-05-02
> **ibjsb4 said:**
> You was clear, I just got lost :) the Extension Package:

[URL="https://www.virtualbox.org/wiki/Download_Old_Builds_4_2"]https://www.virtualbox.org/wiki/Download_Old_Builds_4_2


[/URL]

Thank you for that (although I did find it myself).
But I rather just use the latest version of Virtualbox with the latest extension package.
I will look into updating using the method I mentioned above when someone confirms that is the way to go.

---

### Post by DenHeldert on 2013-05-02
> **ibjsb4 said:**
> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Will do.
Thanks all, time for a beer I guess.

---

### Post by Cheesemill on 2013-05-02
> **DenHeldert said:**
> - Software downloaded from the software center adds its own repositories in most cases, and will update automatically just fine.
Not really. The software you install using the Software Centre is already in the standard Ubuntu repositories. No additional repositories are added.
> - For software that does not add a repository on its own, and you want it to update automatically, you have to add a repository yourself, there is just no way around that.
- For software that does not automatically update, I search Launchpad for missing ppa's.
All of the software available in the Software Centre automatically updates to the latest version *in the repositories*.

Here's a question that you probably wanted to ask...

**Q** - Why doesn't all of the software in the Ubuntu repositories get updated to the latest available version?

**A** - The only updates that make it into the standard Ubuntu repositories are security updates and bug fixes. Major version bumps aren't usually included.

Take LibreOffice as an example. When 12.04 was released it came with version 3.5 of LibreOffice installed, the only updates that will make it into the 12.04 repositories are the bug fixes and security updates for example 3.5.1, 3.5.2, 3.5.3 etc. Even though LibreOffice 4.0 has since been released it will never make it into the standard repositories. Even if you install 12.04 in a few years time and perform all of the updates you will still find yourself with version 3.5.x of LibreOffice (even if they have released version 5 by that time).

This is mainly done for stability reasons, version 3.5.x of LibreOffice will have been heavily tested by the Ubuntu developers to make sure that it works correctly with 12.04 whereas later versions won't have been tested at all (they didn't exist when 12.04 was being developed). For this reason only minor fixes will make it into the standard repositories as they are a lot less likely to break anything.

To update software that is in the standard repositories beyond the version that Ubuntu provides then you will need to add a repository for it to your system, most likely in the form of a PPA (which is just the name for a repository hosted on launchpad.net)..

---

### Post by DenHeldert on 2013-05-02
Thank you for clarifing that.
It makes no difference in the approach I mentioned earlier though, correct?

---

