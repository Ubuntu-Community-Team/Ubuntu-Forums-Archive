---
title: "Kexi"
date: 2017-06-25
forum: New to Ubuntu
---

### Post by dfergfla on 2017-06-25
I need to install Kexi.  I can see that some of the Calligra Office, but Kexi isn't there.  Why would you do that???  That doesn't make sense.  I used to be able to use Kexi on Ubuntu.  Now I can't???  I have tried everything I can find on the Internet to install Kexi on ubuntu but nothing works.  Do I really have to go to a different entire distro just because of needing Kexi?

---

### Post by QIII on 2017-06-25
> **dfergfla said:**
> Why would you do that???

"We" didn't do anything.  "We" are all volunteers and we aren't employed by Canonical.  "We" can't do anything like that.

Which flavor and release of Ubuntu are you using?

---

### Post by gifford on 2017-06-25
Have you tried this link for the Kexi Project? [http://www.kexi-project.org/](http://www.kexi-project.org/)
They do have releases for Ubuntu.

---

### Post by howefield on 2017-06-26
Ubuntu 16.04 supported till 2021 would be the easy route to installing Kexi.

As mentioned above, what release are you using ?

```
cat /etc/*-release
```

---

### Post by dfergfla on 2017-06-26
I realize this is stupid, but I am just not finding the ubuntu install on this site.

---

### Post by gifford on 2017-06-26
What version of Ubuntu are you using? Do you have Synaptic Package Manager installed? If so, open it up and look for Kexi. If not installed, do so as it is available.

---

### Post by Frogs Hair on 2017-06-26
Looks like Kexi is not in the repository for supported versions of Ubuntu. Building from source or PPA (16.04) might be the only option. Search Kexi PPA Ubuntu.   

[https://apps.ubuntu.com/cat/applications/precise/kexi/](https://apps.ubuntu.com/cat/applications/precise/kexi/)

---

### Post by howefield on 2017-06-26
> **Frogs Hair said:**
> Looks like Kexi is not in the repository for supported versions of Ubuntu. Building from source or PPA (16.04) might be the only option. Search Kexi PPA Ubuntu.   

[https://apps.ubuntu.com/cat/applications/precise/kexi/](https://apps.ubuntu.com/cat/applications/precise/kexi/)

It is available for 16.04 (and also 16.10 but of course that goes end of life next month)

```
hugh@xenial-laptop:~$  apt-cache policy kexi
kexi:
  Installed: (none)
  Candidate: 1:2.9.7-0ubuntu12
  Version table:
     1:2.9.7-0ubuntu12 500
        500 http://gb.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
hugh@xenial-laptop:~$ 
```

---

### Post by PopsTheSailor on 2018-02-25
I'm on 17.04 and it's still in Synaptic. I just installed it. For me there was a but and some icons were missing. After installing via snyaptic, I opened a terminal and did a "sudo apt-get install <name of missing icons including extension>. They installed and then Kexi opened fine.

---

### Post by Geoffrey_Arndt on 2018-02-25
Are the repo's for 17.04 still accessible?   [https://fridge.ubuntu.com/2018/01/17/ubuntu-17-04-zesty-zapus-reached-end-of-life-on-january-13-2018/](https://fridge.ubuntu.com/2018/01/17/ubuntu-17-04-zesty-zapus-reached-end-of-life-on-january-13-2018/)

So maybe that's why the missing "pieces" like icon files, etc.

But the Original Poster is long gone . . . don't think he quite "grokked" where he was at (as in "Stranger in a Strange Land") . .

---

### Post by PopsTheSailor on 2018-02-25
Actually type on my part, I'm on 17.10 but as you say the OP is history so doesn't matter at this point.

---

