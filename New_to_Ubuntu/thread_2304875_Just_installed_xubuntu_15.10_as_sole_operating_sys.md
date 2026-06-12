---
title: "Just installed xubuntu 15.10 as sole operating system for small notebook"
date: 2015-11-30
forum: New to Ubuntu
---

### Post by stompin-tom on 2015-11-30
I was told that 14.04 would be better as it is supported and would last longer. I do not understand what this means. Will it suddenly quit working? I am also trying to find out if i have a wireless card already installed. How do I determine that? Thanks

---

### Post by Sweet_Baby_Jamie on 2015-11-30
**Supported with updates.**  14.04 is a _L_ong _T_erm _S_upport version and is supported with software updates until April of 2017!  If it's not one of the LTS releases, it is supported with software updates for only 6 months!

---

### Post by stompin-tom on 2015-11-30
Thanks, Jamie. Will it still work without the software updates? Would I have to install another os at that time? Tom.

---

### Post by grahammechanical on 2015-11-30
Ubuntu does not stop working when it reaches end of life but it will no longer receive security fixes. And that increases the security risk to ourselves and others.

With a Long Term Support version we can upgrade directly to the next LTS release and bypass any interim releases. But with Interim releases we can only upgrade to the next release and if that is an interim release and it has also reached end of life, then upgrading becomes very difficult.

Basically, each release of Ubuntu has it own set of software repositories from which we install programs and into which the updates are put. When a version of Ubuntu reaches end of life its set of repositories are closed and archived. So, running an out of life version also means that we cannot install software. To get newer versions of software we should upgrade. Either from LTS to LTS release or from interim to interim release. Whatever is our choice for using Ubuntu.

Oh, one more thing. As you have already installed 15.10, stay with it and upgrade to 16.04 a month or two are 16.04 is released at the end of April next year.

Regards.

---

### Post by Bucky Ball on 2015-11-30
> **Sweet_Baby_Jamie said:**
> If it's not one of the LTS releases, it is supported with software updates for only 6 months!

If it is not an LTS it is an interim release and is supported, with updates, for nine months. :)

Welcome. Just to add to other's comments, no, it won't stop working, but it will stop getting updates/upgrade, and that includes security updates. The longer that situation goes on the more vulnerable your machine will become. 

Keep using an unsupported release for as long as you like, but be aware that your computer becomes more vulnerable the longer you do and you may get other issues that can't be fixed arising from using an out-of-support release. The forums also do not give support for unsupported releases (logically enough) so running an unsupported release puts you in not great place. 

As for wifi, start a new thread and include the output of this command:

```
sudo lshw -C network
```

If you have a wireless card, hopefully we can get it up and running, but that support request doesn't belong here. Good luck. :)

Hope that helps. And this, the Ubuntu release schedule:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by stompin-tom on 2015-12-04
Thanks, Bucky= I got the wireless working.

---

