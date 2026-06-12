---
title: "Repo Window Not Opening in Synaptic"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by wpurcell on 2008-08-03
Hello. I'm running gNewSense. I know, but they punted me over here. It's an Ubuntu derivative after all. When I open Synaptic, and click on Repos, the window to change the repos opens for a millisecond, closes, then I'm told the repos have changed, and I should reload. Any ideas as to why this would happen? Thanks in advance.:)

---

### Post by billgoldberg on 2008-08-03
> **wpurcell said:**
> Hello. I'm running gNewSense. I know, but they punted me over here. It's an Ubuntu derivative after all. When I open Synaptic, and click on Repos, the window to change the repos opens for a millisecond, closes, then I'm told the repos have changed, and I should reload. Any ideas as to why this would happen? Thanks in advance.:)

Nope.

You can always your repositories (add or remove or disable) by doing it manually.

The file is located here:

> /etc/apt/sources.list

---

### Post by wpurcell on 2008-08-03
Well, thanks eh! I'll reboot into gNewSense and give it a try.

---

### Post by wpurcell on 2008-08-03
Well, no go. The same thing happens. When I click on sources.list.save I get
deb [http://ca.archive.gnewsense.org/gnewsense/](http://ca.archive.gnewsense.org/gnewsense/) deltah main universe
deb-src [http://ca.archive.gnewsense.org/gnewsense/](http://ca.archive.gnewsense.org/gnewsense/) deltah main universe

deb [http://ca.security.gnewsense.org/gnewsense/](http://ca.security.gnewsense.org/gnewsense/) deltah-security main universe
deb-src [http://ca.security.gnewsense.org/gnewsense/](http://ca.security.gnewsense.org/gnewsense/) deltah-security main universe
If that's any help at all!

---

### Post by Ru$$i@N on 2008-08-03
> **wpurcell said:**
> Well, no go. The same thing happens. When I click on sources.list.save I get
deb [http://ca.archive.gnewsense.org/gnewsense/](http://ca.archive.gnewsense.org/gnewsense/) deltah main universe
deb-src [http://ca.archive.gnewsense.org/gnewsense/](http://ca.archive.gnewsense.org/gnewsense/) deltah main universe

deb [http://ca.security.gnewsense.org/gnewsense/](http://ca.security.gnewsense.org/gnewsense/) deltah-security main universe
deb-src [http://ca.security.gnewsense.org/gnewsense/](http://ca.security.gnewsense.org/gnewsense/) deltah-security main universe
If that's any help at all!

i think what billgoldberg meant was that you can manually change the file, but you need root privileges in order to do that.
you can do it the next way:

launch the terminal (Applications > Accessories > Terminal), and type
```
sudo gedit /etc/apt/sources.list
```
and add/remove/comment/uncomment the repos there :)

---

### Post by wpurcell on 2008-08-03
Hello, Here's the list:
deb [http://ca.archive.gnewsense.org/gnewsense/](http://ca.archive.gnewsense.org/gnewsense/) deltah main universe
deb-src [http://ca.archive.gnewsense.org/gnewsense/](http://ca.archive.gnewsense.org/gnewsense/) deltah main universe

deb [http://ca.security.gnewsense.org/gnewsense/](http://ca.security.gnewsense.org/gnewsense/) deltah-security main universe
deb [http://ca.archive.gnewsense.org/gnewsense/](http://ca.archive.gnewsense.org/gnewsense/) deltah-updates universe main
deb-src [http://ca.archive.gnewsense.org/gnewsense/](http://ca.archive.gnewsense.org/gnewsense/) deltah-updates universe main
deb-src [http://ca.security.gnewsense.org/gnewsense/](http://ca.security.gnewsense.org/gnewsense/) deltah-security main universe
 Are there any other repos that I need?

---

### Post by billgoldberg on 2008-08-03
I don't know the repo's needed for that distro.

But after you added them (to disable add a "#" in front of them)

do

```
sudo apt-get update
```

and then you can use synaptic.

(or apt-get).

---

