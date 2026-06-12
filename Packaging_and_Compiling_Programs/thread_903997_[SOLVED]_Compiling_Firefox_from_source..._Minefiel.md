---
title: "[SOLVED] Compiling Firefox from source... Minefield??"
date: 2008-08-28
forum: Packaging and Compiling Programs
---

### Post by jvincent08 on 2008-08-28
Alright, so I decided to compile Firefox from source myself for optimization and such, aside from simply being bored. Well, I downloaded firefox-3.0.1-source.tar.bz2 from [here]("http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.1/source/"). After I finished compiling and installing it, I started it up for a test drive. To my surprise, Minefield was the name of my new program, not Firefox. Concerned, I Googled for more information on this "Minefield" and discovered that it is a code name for pre-release, beta, or otherwise development builds of Firefox.... Well, hold on just one minute! I compiled version 3.0.1, which is an official, stable, release. Why am I getting Minefield instead? Is there no way to compile the stable releases from source?

Thanks in advance for any information you may be able to share with me on this subject.

---

### Post by tuxxy on 2008-08-28
Should be one here

[http://releases.mozilla.org/pub/mozilla.org/firefox/releases/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/)

---

### Post by jvincent08 on 2008-08-28
> **tuxxy said:**
> Should be one here

[http://releases.mozilla.org/pub/mozilla.org/firefox/releases/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/)

That's where I went. I started there, then went to 3.0.1 > source > firefox-3.0.1-source.tar.bz2

---

### Post by tuxxy on 2008-08-28
Thats unusual it shouldnt be minefield thats for sure im on 3.01 now

---

### Post by jvincent08 on 2008-08-28
> **tuxxy said:**
> Thats unusual it shouldnt be minefield thats for sure im on 3.01 now

Did you compile it from source? I had the binary of 3.0.1 installed before, and it was Firefox, but now it's Minefield.

---

### Post by Fixman on 2008-08-29
Minefield is 3.1.0, not 3.0.1

You probably got wrong the numbers.

---

### Post by jvincent08 on 2008-08-29
> **Fixman said:**
> Minefield is 3.1.0, not 3.0.1

You probably got wrong the numbers.

*sigh*... I went [here,]("http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.1/source/") which says 3.0.1. Even the "about" box reports 3.0.1, look!

---

### Post by moliones on 2008-08-29
This page on configuring the mozilla build might help:
[http://developer.mozilla.org/en/Configuring_Build_Options]("http://developer.mozilla.org/en/Configuring_Build_Options")

Specifically, I have
```
export MOZILLA_OFFICIAL=1
export BUILD_OFFICIAL=1
mk_add_options MOZILLA_OFFICIAL=1
mk_add_options BUILD_OFFICIAL=1
ac_add_options --enable-official-branding
```
at the top of my .mozconfig file

---

### Post by jvincent08 on 2008-08-30
> **moliones said:**
> This page on configuring the mozilla build might help:
[http://developer.mozilla.org/en/Configuring_Build_Options]("http://developer.mozilla.org/en/Configuring_Build_Options")

Specifically, I have
```
export MOZILLA_OFFICIAL=1
export BUILD_OFFICIAL=1
mk_add_options MOZILLA_OFFICIAL=1
mk_add_options BUILD_OFFICIAL=1
ac_add_options --enable-official-branding
```
at the top of my .mozconfig file

Thank you, Moliones, that did the trick! :)

---

