---
title: "Fast Neural Network (FANN) library for C"
date: 2014-05-09
forum: Programming Talk
---

### Post by joe_cool2 on 2014-05-09
The package [libfann2]("http://packages.ubuntu.com/precise/libfann2") contains FANN version 2.1.0, which is 7 years old out dated, according to [FANN's official changelog]("http://leenissen.dk/fann/wp/help/changelog/"). I would like to install the newest version, 2.2.0, which was released 2 years ago (why isn't it on Ubuntu yet?). Is there a way to install it using Ubuntu's repositories or some PPA?

---

### Post by joe_cool2 on 2014-05-11
Up.

---

### Post by dwhitney67 on 2014-05-11
Download the source code, and then build it per the instructions given.  Not every software application/library/utility in the world is available in the Ubuntu Repos; sorry, but you just have to accept that.

---

### Post by joe_cool2 on 2014-05-13
The fact is that it actually IS on the repositories, but it's severely out dated.

---

### Post by dwhitney67 on 2014-05-13
> **joe_cool2 said:**
> The fact is that it actually IS on the repositories, but it's severely out dated.

Out dated?  Compared to what... to the release available with the source code tar-ball?

Nobody at Ubuntu, and for that fact probably on this forum, maintain FANN.  It is what it is... either perfected software, or an extremely buggy/neglected software.

---

### Post by joe_cool2 on 2014-05-15
> **dwhitney67 said:**
> Out dated?  Compared to what... to the release available with the source code tar-ball?

Compared to whatever you wan't to compare. The version on the repository is 7 years old.


> **dwhitney67 said:**
> 
Nobody at Ubuntu, and for that fact probably on this forum, maintain FANN.  It is what it is... either perfected software, or an extremely buggy/neglected software.

The new version adds a lot of important improvements and new features that are a must to anyone willing to develop top of the line IA algorithms. And you should study before saying about FANN. It's a spetacular artificial neural network library. Actually, it's the fastest and most used neural network library there exists. Even NASA uses it. And concerning the topic, whatever, I've already installed it from the source code since I posted this thread (I had no time to wait a reply). So, really, whatever if it's totally out dated on Ubuntu's repositories.

---

### Post by sudodus on 2014-05-16
I was developing and using artificial neural networks during the 1990'ies. I'm glad to read about new features and applications :-)

---

### Post by joe_cool2 on 2014-05-16
> **sudodus said:**
> I was developing and using artificial neural networks during the 1990'ies. I'm glad to read about new features and applications :-)

Why don't you use artificial neural networks anymore?

---

### Post by dwhitney67 on 2014-05-16
> **joe_cool2 said:**
> And you should study before saying <snip> about FANN.

I have no need to study anything about FANN at this point in my career.  I've never heard of it prior to you mentioning it (goes to show it's not widely known), and frankly I'm surprised that you took the time to rant that the latest release is not available in the repos on a programming forum.  You should have sought out another venue to voice your concerns.

> **joe_cool2 said:**
> 
Even NASA uses it.

Yay.  NASA -- the large organization that it is -- use many tools, including M$ Office and staplers.  I'm sure that at least a handful of s/w engineers are, or may have considered, using FANN.

> **joe_cool2 said:**
> And concerning the topic, whatever, I've already installed it from the source code since I posted this thread (I had no time to wait a reply). So, really, whatever if it's totally out dated on Ubuntu's repositories.
Again, it's great that you took the high/smart road to move along.  The repos don't always have what you want.  If you do want the repos to carry the latest version (and I agree that they should), then I'm sure that there's another avenue to achieve this that does not involve ranting on this forum.

Peace!

---

### Post by joe_cool2 on 2014-05-16
> **dwhitney67 said:**
> I have no need to study anything about FANN at this point in my career.  I've never heard of it prior to you mentioning it (goes to show it's not widely known), and frankly I'm surprised that you took the time to rant that the latest release is not available in the repos on a programming forum.  You should have sought out another venue to voice your concerns.


Yay.  NASA -- the large organization that it is -- use many tools, including M$ Office and staplers.  I'm sure that at least a handful of s/w engineers are, or may have considered, using FANN.


Again, it's great that you took the high/smart road to move along.  The repos don't always have what you want.  If you do want the repos to carry the latest version (and I agree that they should), then I'm sure that there's another avenue to achieve this that does not involve ranting on this forum.

Peace!

Ok, congratulations for not helping at all and just causing trouble, I've reported you. Thanks for nothing.

---

### Post by sudodus on 2014-05-16
> **joe_cool2 said:**
> Why don't you use artificial neural networks anymore?

I have retired from work.

---

### Post by joe_cool2 on 2014-05-16
> **sudodus said:**
> I have retired from work.

But do you think neural networks are still largely used nowadays?

---

### Post by bapoumba on 2014-05-16
I'm closing this for review, mainly because I do not have the time right now to look around about FANN. Inparticular what is the state of debian repos regarding this package.

One thing to keep in mind is that building and maintaining a package for a distribution requires people do to it.

---

### Post by bapoumba on 2014-05-16
Reopening because I took the time to look around nonetheless.

[https://packages.debian.org/search?keywords=libfann](https://packages.debian.org/search?keywords=libfann)
Ubuntu packages are at the same version than debian (2.1), including unstable. Here are the details in unstable including the person in charge : [https://packages.debian.org/sid/libfann-dbg](https://packages.debian.org/sid/libfann-dbg) and the install procedure for the latest 2.2 version : [http://leenissen.dk/fann/wp/help/installing-fann/](http://leenissen.dk/fann/wp/help/installing-fann/). Their forums : [http://sourceforge.net/p/fann/discussion/](http://sourceforge.net/p/fann/discussion/)

---

### Post by joe_cool2 on 2014-05-16
> **bapoumba said:**
> Reopening because I took the time to look around nonetheless.

[https://packages.debian.org/search?keywords=libfann](https://packages.debian.org/search?keywords=libfann)
Ubuntu packages are at the same version than debian (2.1), including unstable. Here are the details in unstable including the person in charge : [https://packages.debian.org/sid/libfann-dbg](https://packages.debian.org/sid/libfann-dbg) and the install procedure for the latest 2.2 version : [http://leenissen.dk/fann/wp/help/installing-fann/](http://leenissen.dk/fann/wp/help/installing-fann/). Their forums : [http://sourceforge.net/p/fann/discussion/](http://sourceforge.net/p/fann/discussion/)

I did some research on this issue and I think the reason that FANN is so outdated in Ubuntu's repository is to maintain FANN's bindings compatibility. As far as I know, most of FANN's bindings weren't upgraded yet to version 2.2. So, if FANN's was upgraded, PyFANN and all the other bindings would stop working. I guess Ubuntu's developers prefered to keep an out dated package rather than removing a lot of other packages from their repositories. Anyway, it's plain simple to install FANN's 2.2 if someone needs too.

PS: <snip>

---

### Post by bapoumba on 2014-05-17
Most packages from the Ubuntu distributions are directly coming from debian unstable once the ubuntu release is freezed. Unless there is an ubuntu maintainer for FANN or a ppa dev, no changes are applied. So the Ubuntu package is the debian package from last feature freeze. 

As to why and the binding things, I cannot answer.

---

### Post by Elfy on 2014-05-17
> **joe_cool2 said:**
> I did some research on this issue and I think the reason that FANN is so outdated in Ubuntu's repository is to maintain FANN's bindings compatibility. As far as I know, most of FANN's bindings weren't upgraded yet to version 2.2. So, if FANN's was upgraded, PyFANN and all the other bindings would stop working. I guess Ubuntu's developers prefered to keep an out dated package rather than removing a lot of other packages from their repositories. Anyway, it's plain simple to install FANN's 2.2 if someone needs too.

PS: <snip>

The reason that it is outdated in the repositories is that it is community maintained - it is in the universe [repository]("https://help.ubuntu.com/community/Repositories/Ubuntu#What_are_Repositories.3F").

So - if you want there to be an up to date version in the repository for the community, be part of the community and maintain it for those that want it.

---

