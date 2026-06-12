---
title: "How do I change the &quot;Computer Name?&quot;"
date: 2011-12-23
forum: New to Ubuntu
---

### Post by GregA on 2011-12-23
Hello All, 

I've setup an older laptop with Kubuntu, Xubuntu, and Lubuntu.  Everthing runs well, but I made a typo when adding the Computer name during the install process.   

What file would I edit to change the Computer Name?  . . . or maybe there's a gui application to accomplish the same?

Appreciate any info . . . thanks.

Greg

---

### Post by haqking on 2011-12-23
> **GregA said:**
> Hello All, 

I've setup an older laptop with Kubuntu, Xubuntu, and Lubuntu.  Everthing runs well, but I made a typo when adding the Computer name during the install process.   

What file would I edit to change the Computer Name?  . . . or maybe there's a gui application to accomplish the same?

Appreciate any info . . . thanks.

Greg

```
/etc/hostname
```
```
/etc/hosts
```

if it a temporary thing thing then just

```
hostname <desired name>
```

this will take immediate effect but will be lost after reboot.

If you want the prompt to change then

```
PS1="desired name at prompt : "
```

this can be different to actual hostname.

---

### Post by drmrgd on 2011-12-23
From a quick Google search, here is a link that might help ya:

[How to change your Hostname in Ubuntu]("http://www.liberiangeek.net/2011/03/change-hostname-computer-name-ubuntu-11-04-natty/")

Looks like this is written from Unity, however, changing it from one of the other DE should be just as easy.  Instead of using gedit, for example, you might use Kate if you're in Kubuntu at the moment.

Hope it helps!

---

### Post by BC59 on 2011-12-23
And Ubuntu Tweak has an easy tool to change the name.

---

### Post by GregA on 2011-12-23
Thanks everyone!   I will try the file fixes first, . . . that method should work for all desktop variants.

About Ubuntu tweak, is that only a gnomish or unity tool?   

Where would I find that application? . . . via Synaptic and is that the right name to use for the search (I didn't see it in Synaptic).

Greg

---

### Post by haqking on 2011-12-23
when editing the files make sure you use sudo for CLI like nano and vi, and gksudo for graphical editors such as gedit etc.

Cheers

---

### Post by BC59 on 2011-12-23
> **GregA said:**
> Thanks everyone!   I will try the file fixes first, . . . that method should work for all desktop variants.

About Ubuntu tweak, is that only a gnomish or unity tool?   

Where would I find that application? . . . via Synaptic and is that the right name to use for the search (I didn't see it in Synaptic).

Greg

Look here
[http://www.webupd8.org/2011/12/ubuntu-tweak-06-has-been-released.html](http://www.webupd8.org/2011/12/ubuntu-tweak-06-has-been-released.html)

---

