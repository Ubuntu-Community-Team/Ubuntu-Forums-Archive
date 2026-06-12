---
title: "is debian unstable repo good for ubuntu?"
date: 2006-04-22
forum: Repositories &amp; Backports
---

### Post by kroiz on 2006-04-22
Hi,
I need to upgrade my qt 4.0.0 which I got with synaptic to qt 4.1.2.
I found the package in debian unstable repo

can I add that repo to my list and upgrade qt that way?

---

### Post by Mustard on 2006-04-22
I wouldn't advise it.  It's not really recommended to use the debian repos.

---

### Post by AGS on 2006-04-22
Theoretically it has been possible to interchange Ubuntu and Debian packages, but as time has passed, several Ubuntu-packs are not longer usable by standard Debian. I wouldn't be surprised if the opposite direction would do the same :-k - do not work, that is. The differences have grown over the last months...

BTW: If you want to use Debian unstable/Sid, have you ever thougt about testing Kanotix? It is an installable live-CD based on Knoppix (which, in turn, is based on Debian) but purely Debian Sid - all repos in it's default sources.lst are unstable. Standard WM is KDE, but Gnome should be installable easy enough. A side project actually tries to build a Gnome-based Kanotix, but that is still in development.
After quitting SuSe in January I used Kanotix until now and am very fond of it - it's quite stable and very usable. It's to be found on [kanotix.com]("http://www.kanotix.com") in english and german and some info's can be read at [distrowatch.com.]("http://distrowatch.com/table.php?distribution=kanotix")
I still like it ;)

---

### Post by az on 2006-04-22
[QUOTE=AGS]Theoretically it has been possible to interchange Ubuntu and Debian packages, but as time has passed, several Ubuntu-packs are not longer usable by standard Debian. I wouldn't be surprised if the opposite direction would do the same :-k - do not work, that is. The differences have grown over the last months...[/QUOTE]

Ubuntu is not a fork of Debian.  Ubuntu syncs back with Debian after every release.  There are some diffs that remain after a sync, but strictly speaking, Ubuntu is not a fork - it's maybe a spoon of Debian.

The main reason why there is no binary compatibility with debian is that the toolchain is not always the same.  Ubuntu may use a different version of libc than Debian at any point in time.

---

### Post by kroiz on 2006-04-22
Thanks guys, Things makes more sense to me now. because I added the sid and selected upgrading qt but it required unistallation of some basic ubuntu stuff, so I did not do it.

I guess I would need to find another way to upgrade qt. :(
maybe I could read its deb file to figure out what is need to be done?

AGS, thanks but my linux XP is still very low. I think I need to level up some more before I can use a linux based on unstable packages.

---

### Post by AGS on 2006-04-27
[quote=azz]Ubuntu is not a fork of Debian. Ubuntu syncs back with Debian after every release. There are some diffs that remain after a sync, but strictly speaking, Ubuntu is not a fork - it's maybe a spoon of Debian.[/quote]
 
OK - so it seems my knowledge was already outdated. Sorry if I created confusion.
 
@Kroiz: My Linux-XP has been very small too. I started with SuSe10.0 last fall and it crashed me twice. After doing some research I found Kanotix in January, which works very stable once it is installed (which is a very easy process due to a very good installer gui). The Forum provides answers for nearly anything (just like this one does ;) ), and if you don't have to use the very latest s/w like x.Org7 or the KDE-release-of-10minutes-ago, there shouldn't be greater problems. My KX worked very well and stable without that much knowledge until I crashed it a few days ago - by installing the very latest s/w too fast... but recovery is on the way as this is a common problem for many users, and several scripts are on their way.
 
BTW: Why am I doing advertisement here?

---

### Post by kroiz on 2006-04-28
AGS, but why is the site full of german.
I dont think this distro is for non-german.
most of the posts on the forum are in german too.
what is up with that.

---

