---
title: "libgstreamer package?"
date: 2018-08-23
forum: New to Ubuntu
---

### Post by mborl on 2018-08-23
I was trying to download one of my favorite time management apps/trackers, Toggl. I downloaded the .deb, but found out it needed the following packages: 

libgstreamer-plugins-base0.10-0_0.10.36-1_amd64.deb
libgstreamer0.10-0_0.10.36-1.5ubuntu1_amd64.deb

The instructions on Toggl's website advises using wget for them (I was just planning on using apt install). In any case, I have never heard of these packages and was curious if they are widely used. I couldn't find much about them searching the web that didn't come from sites marked as dangerous or risky by my WOT browser extension. Any input you guys have is helpful. Thanks!

By the way, here is the page with the instructions [https://support.toggl.com/toggl-desktop-for-linux/](https://support.toggl.com/toggl-desktop-for-linux/)

---

### Post by Impavidus on 2018-08-24
libgstreamer0.10-0 and libgstreamer-plugins-base0.10-0 are pretty standard packages. I think they are even installed by default and in any case available from the repositories. However, that's on Ubuntu 14.04 and 16.04. On Ubuntu 18.04 they have been replaced by libgstreamer1.0-0 and libgstreamer-plugins-base1.0-0.

---

