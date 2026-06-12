---
title: "need help setting up ventrilo"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by fignig on 2008-05-08
i'm having some problems and don't rly know what to do. i've gotten ventrilo installed and i have it running and i can connect to servers, but i can't hear anyone or talk on my mic. i'm getting the error:

Failed to get encoder for specified Codec.

Unable to initialize outbound codec (GSM 6.10 - 44 KHz, 16 bit): Unable to find the specified codec.

can anyone help me setup ventrilo? i miss playing cs.

---

### Post by Trogdor809 on 2008-10-30
Me to same problem.

---

### Post by ethoxyethaan on 2008-10-30
[http://www.ventrilo.com/download.php](http://www.ventrilo.com/download.php)

where did you get the linux version. or are you talking about running ventrillo on wine?
if so you need press ctrl + F2 and type: winecfg

and change some of the settings on in the sound tab, (i think alsa is the best choice in most cases).

---

### Post by lH)4~mK0e on 2008-10-31
You should try mumble.  Normally I would direct you to the repositories, but the keyboard shortcut function is broken (and I need it for PTT).

[[color="blue"]Mumble PPA for Ubuntu[/color]]("https://launchpad.net/~slicer/+archive")

We use it for our WoW guild.  I have it running on a Ubuntu server here hosted on a cable connection and it doesn't have a problem with latency.

Oh and if you are using Steam for CS, the voice chat function should work through wine.

---

