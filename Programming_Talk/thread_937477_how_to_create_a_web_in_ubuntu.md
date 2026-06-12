---
title: "how to create a web in ubuntu?"
date: 2008-10-03
forum: Programming Talk
---

### Post by eeyjay on 2008-10-03
what software or what application i need to download to create a webpage

---

### Post by Bakon Jarser on 2008-10-03
[http://ubuntuforums.org/showthread.php?t=651977](http://ubuntuforums.org/showthread.php?t=651977)

---

### Post by LaRoza on 2008-10-04
> **eeyjay said:**
> what software or what application i need to download to create a webpage

All you need is a text editor, Gedit is good enough, and you can use any browser to view it.

If you want a WYSIWYG editor, see: [http://ubuntuforums.org/showthread.php?t=606009](http://ubuntuforums.org/showthread.php?t=606009)

---

### Post by taavi on 2008-10-04
I don't want to start new thread, but maybe some more knowledgeable person (Ubuntu stuff) reads it and can answer.

What are the chances to get Django 1.0 into Ubuntu repositories? It's not that important, because I think that anyone who has dealt with Django has always installed it by hand. But it would be nice to get latest stable with apt-get. Right now version 0.96.1 is available.

And another flashing release has been made: Python 2.6. Will Ubuntu 8.10 get it aswell?

---

### Post by Bakon Jarser on 2008-10-04
I think it's waaaaaaaaayyyyy too far past the deadline to include new packages in 8.10.  It's already in beta.

---

### Post by yoda2031 on 2008-10-04
If you want a "bleeding edge" OS, you should opt for something like Gentoo.

Ubuntu can be set to "bleeding edge" mode, but even then it's not as bang-up-to-date as Gentoo or Debian Sid.  The problem comes from Canonical having commercial partners who do not want to have to pay out their nose to support a product that constantly goes wrong if the user doesn't know what they're doing.  Thus, canonical make it so that only users who know their stuff can get bang-up-to-date software by simply not including it in the mainstream repos.

New packages are considered each release, and if you want to suggest a package for the next release of Ubuntu you can do so on the wiki.  I don't think you're able to do so currently as it is so close to Intrepid's release that we've probably gone past the last feature freeze.  Wait for Intrepid to come out, then suggest it for 9.04.

---

### Post by taavi on 2008-10-04
> **yoda2031 said:**
> If you want a "bleeding edge" OS, you should opt for something like Gentoo.Hehe, I moved away from Gentoo early this year. They have problems with stability and aren't so bleeding edge as they used to be...

Ok, ofc it's late for Python 2.6 now, but Django 1.0 has been stable about 1 month now. Okey okey. Was just checking...

---

### Post by yoda2031 on 2008-10-04
I'm not getting it.  You want cutting-edge software repos AND stability from an OS?  

Please, tell me you know why that's not possible...

I don't have much experience with Gentoo, but I do have it on recommendation from a Cambridge graduate so I'm not about to accept criticism of it on face value.  I also don't believe it adds anything to this already off-topic discussion.

Perhaps this thread should be left alone now.

---

### Post by CptPicard on 2008-10-04
> **yoda2031 said:**
> I'm not getting it.  You want cutting-edge software repos AND stability from an OS?  

I left Gentoo for the same reason. It did not have as much to do with stability of software, but stability of the distribution itself. The amount of broken ebuilds just went through the roof, and it was obvious the Gentoo process was not able to keep up. So it has nothing to do with cutting-edgeness, the *distro itself* was more and more broken all the time.


> 
I don't have much experience with Gentoo, but I do have it on recommendation from a Cambridge graduate so I'm not about to accept criticism of it on face value.

Guys don't have to graduate from Cambridge to have valid views of Gentoo after using it, you know...

---

### Post by pmasiar on 2008-10-04
> **taavi said:**
> But it would be nice to get latest stable with apt-get. 

You need first to make your mind: what do you want? Latest, or stable?

As a rule of thumb, if you want to follow closely some project in rapid development, you have to follow it using manual install. For distro developers, some kind of "old and stable" is good enough, because they focus on whole system, not on single package.

Doing it lazy way, relying on distro packagers, is good enough if project is mature and develops slowly, or if you do not care which version is installed. I think this should be obvious for anyone beyond green beginner - it seems like a common sense to me 8-)

---

### Post by taavi on 2008-10-05
> **pmasiar said:**
> You need first to make your mind: what do you want? Latest, or stable?In this case, it really doesn't matter... It's release 1.0. When you have stable version, it really doesn't matter that much, if you have 1.0.3 or 1.2 because you assurance that they won't break your application by changing API. By using term "latest stable" I was referring 1.0, which is the first and latest stable of Django. And as you can understand there isn't "old and stable" version of Django before 1.0

---

