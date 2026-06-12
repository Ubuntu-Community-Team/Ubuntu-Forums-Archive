---
title: "Anti virus?"
date: 2008-11-24
forum: Recurring Discussions
---

### Post by Craig A on 2008-11-24
I have ubuntu 8.10 and I don't know if it needs anti virus software like an windows op system needs anti virus :confused:

---

### Post by Skripka on 2008-11-24
> **Craig A said:**
> I have ubuntu 8.10 and I don't know if it needs anti virus software like an windows op system needs anti virus :confused:

There are really no viruses of note to worry about circulating on Linux.  Due to the way the OS works and permissions work--even if you get one, the virus could do very little without your admin password.

---

### Post by jakupl on 2008-11-24
It really doesn't, but you can always install clamtk

```
sudo apt-get install clamtk
```


EDIT: if you download it, you might have to update the virus signatures.

Open clamtk as root.

```
gksudo clamtk
```

goto help---> update signatures.

---

### Post by Oliver.BS on 2008-11-24
Im not worried about not having one really I feel as safe as a pork chop on a vegetarians plate.

---

### Post by Sef on 2008-11-24
The only time you would need an anti-virus would be if you ran an email client such as Thunderbird or Evolution.   Then you would run it because you could infect your friends who run Windows,   The virus would just sit upon your system not harming it.

---

### Post by giantdut on 2008-11-24
Can ubuntu inject by virus? what virus? i'm newbie...just installed ubuntu 8.04.1 LTS 1 hour ago

---

### Post by sonu 1807 on 2008-11-24
Anti-Virus what's that? :)

---

### Post by jakupl on 2008-11-24
> **giantdut said:**
> Can ubuntu inject by virus? what virus? i'm newbie...just installed ubuntu 8.04.1 LTS 1 hour ago

I can't understand the question. Could you rephrase?

---

### Post by hyper_ch on 2008-11-24
> **Sef said:**
> Then you would run it because you could infect your friends who run Windows,

If they don't protect themselves then they will get infected sooner or later anyway. The chance that it's "you" who infects "them" is very low...

---

### Post by Skripka on 2008-11-24
> **sonu 1807 said:**
> Anti-Virus what's that? :)

It's the industry that a certain "Bill Gates" gave birth too.

---

### Post by sydbat on 2008-11-24
> **giantdut said:**
> Can ubuntu inject by virus? what virus? i'm newbie...just installed ubuntu 8.04.1 LTS 1 hour ago
If I understand, you are asking if a virus will move from Ubuntu to Windows? If this is what you are asking, then yes. 

The virus (most likely written for Windows) will be sent to whomever you send email to. Of course that is the key - sending the virus laden email. Clam (or other anti-virus programs) may catch the virus and disable it, but the people you send email to using Windows should have their own AV installed.

If the virus was acquired in another fashion (like surfing to the wrong sites, etc), I do not think it would leave your machine because, as I stated above, they are written for windows and are not going to execute on your Linux box, so they will not do damage to your computer or be passed on to others.

This is what I understand to be true, and others better versed will correct me if I am wrong.

---

### Post by Craig A on 2008-11-24
No worries then for having a virus on ubuntu then :)

I forgot to say how much I like ubuntu now :D

---

### Post by wizard10000 on 2008-11-24
I've always run a virus scanner on my Linux machines so I don't inadvertently infect a Windows box as others have mentioned.  It's possible to infect a Windows machine through email or removable media and I think it's just part of responsible computing to insure that files I send around are safe.

---

