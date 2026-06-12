---
title: "Internet Troubles"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by nicholas mccarthy on 2008-10-08
Hey,

I'm trying to go to the next upgrade (I'm a little slow on it, I had to go back to 6.10, and upgrade until i get to 8.04), this pops up:

Error during update

A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.


[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:) 404 Not Found [my IP address here]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz:) 404 Not Found [my IP address here]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz:) 404 Not Found [my IP address here]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz:) 404 Not Found [my IP address here]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:) 404 Not Found [my IP address here]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz:) 404 Not Found [my IP address here]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz:) 404 Not Found [my IP address here]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz:) 404 Not Found [my IP address here]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz:) 404 Not Found [my IP address here]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz:) 404 Not Found [my IP address here]


Know of anything that can help me? I've tried that whole gpg thing, and that didn't work either.

Thanks

---

### Post by iaculallad on 2008-10-08
What gives when you ping ubuntuforums.org in your terminal?

```
ping ubuntuforums.org
```

If you could ping the site, try to change your download server. System->Administration->Software Sources

---

### Post by nicholas mccarthy on 2008-10-09
Yeah, that did nothing, any other help, or am I just stuck with 6.10 and not being able to download things off of Add/Remove Applicatons?

---

### Post by SunnyRabbiera on 2008-10-09
Do you have the ability to make a live CD?

---

### Post by nicholas mccarthy on 2008-10-09
I don't think so, no.

---

### Post by nicholas mccarthy on 2008-10-09
Any new help?

---

### Post by snova on 2008-10-10
How do you connect to the internet?

---

### Post by newlinux on 2008-10-10
edgy repos are dead... 

try this:

Change all your packages in /etc/apt/sources.lst to feisty:

```

sudo sed -e 's/\sedgy/ feisty/g' -i /etc/apt/sources.list

```

should work... You may want to back it up first and if that line doesn't work just manually change edgy repos to feisty repos.

then run:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
I strongly recommend you just reinstall with Hardy or Intrepid when it comes out. Feisty will be reaching end of life in a little over a week I think, an you'll be in the same boat.

---

### Post by nicholas mccarthy on 2008-10-10
> **newlinux said:**
> edgy repos are dead... 

try this:

Change all your packages in /etc/apt/sources.lst to feisty:

```

sudo sed -e 's/\sedgy/ feisty/g' -i /etc/apt/sources.list

```

should work... You may want to back it up first and if that line doesn't work just manually change edgy repos to feisty repos.

then run:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
I strongly recommend you just reinstall with Hardy or Intrepid when it comes out. Feisty will be reaching end of life in a little over a week I think, an you'll be in the same boat.

Yeah, I downloaded an iso of Hardy last night, I just don't have a blank CD to burn it to yet.

---

