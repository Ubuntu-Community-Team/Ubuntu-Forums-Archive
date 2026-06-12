---
title: "Compiling get_flash_videos from git"
date: 2011-02-25
forum: Packaging and Compiling Programs
---

### Post by ron999 on 2011-02-25
Hi
This seems to be the location for the git:- [https://github.com/monsieurvideo/get-flash-videos]("https://github.com/monsieurvideo/get-flash-videos")

I've compiled it like this:-
```
git clone git://github.com/monsieurvideo/get-flash-videos.git
cd get-flash-videos
make
sudo checkinstall --pakdir "$HOME/Desktop" --pkgname get-flash-videos \
--pkgversion "1.2.5-git-$(date +%Y%m%d)" --backup=no --deldoc=yes --default

```
This gives me a deb package like this:- **get-flash-videos_1.2.5-git-20110225-1_i386.deb** :D

The version in git is **1.2.5**.
Is there a way that I can automatically find the version number so that this part of the command:-
> --pkgversion "**1.2.5**-git-$(date +%Y%m%d)"
is future-proof.

Something like this:-
> --pkgversion "**$VERSION**-git-$(date +%Y%m%d)"

How can I find **$VERSION** automatically? :confused:

---

### Post by MadCow108 on 2011-02-26
usually you use *git describe* for that.

it will print the latest tag and the number of commits since then + the latest sha (prepended with g). Its better than using a date.
you can parse it as you wish e.g. with
```
git describe | awk -F- '{print $3}' | sed -e "s/^g//" | xargs git show --pretty="format:%cd"
Fri Feb 25 16:27:13 2011 -0600

```

for the master branch it gives:
v1.22-117-g27e30c5
meaning there have been 117 commits since the last annotated tag.

interestingly the 1.23 is not annotated and 1.24 is on another branch, 1.24_0X are also not annotated. This should actually be done by the author.

so you might want to use *git describe --tag* to use the latest tag instead of the lastest annotated tag.
v1.24_02-32-g27e30c5

---

### Post by ron999 on 2011-02-26
Hi, thanks for your reply MadCow.
How do I use **git describe --tag**?
How do I incorporate it in my checkinstall command?
I agree, commits would be much better than the date.

---

### Post by TeoBigusGeekus on 2011-02-26
Try this:
```
sudo checkinstall --pakdir "$HOME/Desktop" --pkgname get-flash-videos \
--pkgversion "$(git describe | awk -F- '{print $3}' | sed -e "s/^g//" | xargs git show --pretty="format:%cd"
Fri Feb 25 16:27:13 2011 -0600)-git-$(date +%Y%m%d)" --backup=no --deldoc=yes --default
```

---

### Post by ron999 on 2011-02-26
Yes TeoBigus, the command works OK.
This is the result:-

**get-flash-videos_1.2.5-git-20110226-1_i386.deb** :)

But what does all this mean here?
sudo checkinstall --pakdir "$HOME/Desktop" --pkgname get-flash-videos \
--pkgversion "$(git describe | awk -F- '{print $3}' | sed -e "s/^g//" | xargs git show --pretty="format:%cd"
[COLOR="Red"]Fri Feb 25 16:27:13 2011 -0600[/COLOR])-git-$(date +%Y%m%d)" --backup=no --deldoc=yes --default

Will I need to change that date each time that I compile?
What is the significance of Fri Feb 25 16:27:13 2011 -0600 ?

---

### Post by ron999 on 2011-02-26
No the command isn't working Teo.
I was mistaken.
The result is **get-flash-videos_0-1_i386.deb**

---

### Post by ron999 on 2011-03-03
Hi
I've thought again about this program.
It's not in the Karmic repo.
So it's not important to me which 'version' is shown in Synaptic, it won't be over-written.:)

I've modified the process like this:-
```
git clone git://github.com/monsieurvideo/get-flash-videos.git && \
cd get-flash-videos && make && \
sudo checkinstall --pakdir "$HOME/Desktop" --pkgname get-flash-videos \
	--pkgversion "`date +%Y%m%d`-git" --backup=no --deldoc=yes --default
```

This is the result:- **get-flash-videos_20110303-git-1_i386.deb**

When I need to know which version is installed I can enter a command like this:-
```
ron@ubuntu:~$ get_flash_videos -v
get_flash_videos version 1.25 (http://code.google.com/p/get-flash-videos/)

```
:cool:

---

### Post by andrew.46 on 2011-08-12
I have not fully tested this one (I am on my other distro at the moment) but perhaps something like this would be useful:

```

--pkgversion "$(grep '  $VERSION' get_flash_videos | cut -d '"' -f 2)\
             -git$(git rev-parse --short HEAD)"

```

Could do with a bit more tinkering though I suspect....

---

### Post by kle on 2011-08-13
*

---

### Post by davidesamulson on 2011-08-14
I wannt to now that how How do I use git describe --tag?Or any other option which i can use in its place.

---

