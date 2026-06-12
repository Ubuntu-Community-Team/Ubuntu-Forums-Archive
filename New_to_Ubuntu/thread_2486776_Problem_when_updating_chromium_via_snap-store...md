---
title: "Problem when updating chromium via snap-store.."
date: 2023-05-10
forum: New to Ubuntu
---

### Post by yatski on 2023-05-10
So, today I tried to update chromium via snap-store.
Instead I got "no updates available"-message.

I've already tried ```
sudo snap refresh
```.

What should I do?

I use Ubuntu 22.04 LTS.

---

### Post by poorguy on 2023-05-10
What version of Chromium is installed.

The latest versions are here.

[https://snapcraft.io/chromium](https://snapcraft.io/chromium)

---

### Post by yatski on 2023-05-10
For some reason Chromium shows that it's version is 113.0.5672.63.
This should mean I have latest installed, huh..

---

### Post by BBQdave on 2023-05-10
> **yatski said:**
> I've already tried ```
sudo snap refresh
```

You are correct using ```
sudo snap refresh
```

Possible a newer version that is beta, as sometimes *snaps* are available for current-stable and beta.

---

### Post by poorguy on 2023-05-10
> **yatski said:**
> So, today I tried to update chromium via snap-store.
```
sudo snap refresh
```.


Yep once a month or whenever I see the Snap update message usually upper right hand corner of the desktop.

---

### Post by deadflowr on 2023-05-10
> **yatski said:**
> For some reason Chromium shows that it's version is 113.0.5672.63.
This should mean I have latest installed, huh..

You can use
```
snap info chromium
```
and scroll down to the bottom it'll list both what current (stable, candidate, beta or edge) channels are and what the current Installed version is.
Default is the stable channel, and looks like current stable is a match for the version you posted.

---

### Post by yatski on 2023-05-10
```
heta@heta-vaio:~$ snap info chromium
name:      chromium
summary:   Chromium web browser, open-source version of Chrome
publisher: Canonical&#10003;
store-url: https://snapcraft.io/chromium
contact:   https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bugs?field.tag=snap
license:   unset
description: |
  An open-source browser project that aims to build a safer, faster, and more
  stable way for all Internet users to experience the web.
commands:
  - chromium.chromedriver
  - chromium
snap-id:      XKEcBqPM06H1Z7zGOdG5fbICuf8NWK5R
tracking:     latest/stable
refresh-date: today at 12:05 EEST
channels:
  latest/stable:    113.0.5672.63 2023-05-10 (2465) 157MB -
  latest/candidate: 113.0.5672.92 2023-05-10 (2468) 157MB -
  latest/beta:      114.0.5735.16 2023-05-05 (2463) 155MB -
  latest/edge:      114.0.5735.6  2023-05-03 (2458) 155MB -
installed:          113.0.5672.63            (2465) 157MB -
```

So, I take is nothing for me to worry... Except the annoying notice on Snap Store. (It probably solves itself out with restart?)

---

