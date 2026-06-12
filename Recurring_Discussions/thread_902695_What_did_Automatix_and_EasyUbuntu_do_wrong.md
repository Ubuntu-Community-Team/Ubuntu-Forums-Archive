---
title: "What did Automatix and EasyUbuntu do wrong?"
date: 2008-08-27
forum: Recurring Discussions
---

### Post by anotherdisciple on 2008-08-27
I made this simple bash script for myself a while ago. It installs all the things I normally install and removes all the things I normally remove, changes some configuration files, adds things to the sources.list, etc. I have started on making a GUI on it so that I can give it to my friends who don't know how to use the command line and are starting to use Ubuntu.

I noticed that what I'm trying to accomplish seems to be exactly the same idea as Automatix and EasyUbuntu. I've heard a lot of complaints about these programs breaking things and making upgrading a pain. I want to know what they did wrong? My script seems to do everything I would normally do in the terminal, it just does it for you. So, is there any reason that my simple GUI that offers those options would screw anything up?

---

### Post by aysiu on 2008-08-27
I think reports about breakage were more about theory than practice. The danger was very real, but it was also greatly exaggerated. The problem stems from not knowing everyone's situation and forcing certain things to happen if they're not happening. You know exactly what is going on with your computer, so your script works... for you. Probably the same deal with your friends for whom you set up Ubuntu.

To create an interactive script that works for everybody in various situations is quite a bit trickier, especially if you're going to deal with error-handling and possibly other open package managers.

---

### Post by billgoldberg on 2008-08-27
> **anotherdisciple said:**
> I made this simple bash script for myself a while ago. It installs all the things I normally install and removes all the things I normally remove, changes some configuration files, adds things to the sources.list, etc. I have started on making a GUI on it so that I can give it to my friends who don't know how to use the command line and are starting to use Ubuntu.

I noticed that what I'm trying to accomplish seems to be exactly the same idea as Automatix and EasyUbuntu. I've heard a lot of complaints about these programs breaking things and making upgrading a pain. I want to know what they did wrong? My script seems to do everything I would normally do in the terminal, it just does it for you. So, is there any reason that my simple GUI that offers those options would screw anything up?

If I remember correctly, Automatix used shady repos and the stuff in those repos would conflict with the software on the computer from time to time.

I've never heard about EasyUbuntu.

---

### Post by cariboo on 2008-08-27
Your script works, because it is using packages from the repositories, whereas automatix used packages from non-standard sources.

Jim

---

### Post by aysiu on 2008-08-27
You can find technical criticisms of Automatix here:
[http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)

---

### Post by swoll1980 on 2008-08-30
automatix screwed up my sources.list back when i was a noob took forever to figure out what happend

---

### Post by ugm6hr on 2008-08-30
> **swoll1980 said:**
> took forever to figure out what happend

This was the problem.

If you are doing non-standard things, that you have no knowledge of ***if*** things go wrong, there is no way to work out why or how.

Hence this forum was full of ](*,) when, having spent a load of time trying to help someone, it became apparent that their problems were caused by some interaction of Automatix with something else.

Obviously this was unhelpful both for advisers and new users - and it would sometimes come across as unhelpful behaviour from users demonstrating their frustration.

This is always going to be the case when changes have been made to a system, but someone else is trying to help without being aware of those changes.  Examples commonly seen: ndiswrapper for wifi; Wubi; latest ATI drivers; many others I can't hink of right now.  The ATI drivers are a good example - Envy ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)) instructions used to encourage you to remove prior to any kernel upgrade, then reinstall until it became officially supported in Hardy.  If you failed to do that - things would go wrong.

As explained, if your script does nothing other than install / remove apps using aptitude from the standard repos, there should be no issue.

---

