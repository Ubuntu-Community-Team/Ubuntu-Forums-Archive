---
title: "Netflix is working, but Amazon isnt, post I read are a few years old"
date: 2013-10-19
forum: New to Ubuntu
---

### Post by merpac91 on 2013-10-19
I started using Ubuntu a few months ago cause my comp died, I harvest parts from other older comps to build a crappy frankenstein only for watching netflix and browsing

Anyways, I didnt have my windows stuff, and Netflix has been going pretty good

But I bought Amazon Prime, it worked for a few days and now it keeps saying Flash not updated--

I read around seeing that Flash wont update Linux anymore, but chrome will have an in-built plug in, nothing

any help?

---

### Post by SeijiSensei on 2013-10-19
The DRM ("digital rights management") system that Amazon Prime uses requires that you install two deprecated packages, **hal** and **libhal1**.  Use "sudo apt-get install hal libhal1" and give Amazon another try.

However I just discovered that I cannot watch an Instant Video film on my newly-upgraded 13.10 system as neither of those packages are included in the [Saucy repositories]("https://launchpad.net/ubuntu/saucy/+source/hal").  I'll look around to see if there is a version in a PPA that is compatible.  However intstalling hal and libhal1 worked for me on versions 12.04-13.04.

---

### Post by merpac91 on 2013-10-19
Thanks a ton, that worked!

---

### Post by sanderj on 2013-10-19
> **merpac91 said:**
> I started using Ubuntu a few months ago cause my comp died, I harvest parts from other older comps to build a crappy frankenstein only for watching netflix and browsing

Anyways, I didnt have my windows stuff, and Netflix has been going pretty good


How do you use Netflix on Ubuntu? [http://movies.netflix.com/WiMessage?msg=51](http://movies.netflix.com/WiMessage?msg=51) tells me I should use Windows, Mac or ChromeOS ...

---

### Post by mörgæs on 2013-10-19
> **merpac91 said:**
> Thanks a ton, that worked!

Good, please mark the thread 'solved'.

---

