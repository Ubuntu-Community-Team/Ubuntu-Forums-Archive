---
title: "When will the latest release of Firefox be available in Software Updater?"
date: 2016-07-20
forum: New to Ubuntu
---

### Post by eharman on 2016-07-20
I have been waiting to use [Firefox 47.0.1]("https://www.mozilla.org/en-US/firefox/47.0.1/releasenotes/") in an Ubuntu 14.04.4 LTS VM, but the Software Updater keeps assuring me that the 47.0 I have is up to date. 

I know that 47.0.1 was released on 06/28/2016. How long does it usually take for new updates to make it into Software Updater?

I'm aware I can download and install the latest directly from Mozilla, but I wonder what will happen to future updates if I do that. 

Thanks

---

### Post by QIII on 2016-07-20
Unless a software release constitutes a security update, it usually will not hit the repos at all.

What do the release notes for the release say?

Most major releases of FF are considered security releases.  A minor one from 47.0 to 47.0.1 may not be.

---

### Post by vasa1 on 2016-07-20
> **QIII said:**
> ...
What do the release notes for the release say?
...
[https://www.mozilla.org/en-US/firefox/47.0.1/releasenotes/:](https://www.mozilla.org/en-US/firefox/47.0.1/releasenotes/:) essentially they fixed "Selenium WebDriver may cause Firefox to crash at startup".

I don't know how significant that is. It seems to be a cross-platform issue:
[https://developer.mozilla.org/en-US/docs/Mozilla/QA/Marionette/WebDriver](https://developer.mozilla.org/en-US/docs/Mozilla/QA/Marionette/WebDriver)
[https://lists.opensuse.org/opensuse-factory/2016-07/msg00020.html](https://lists.opensuse.org/opensuse-factory/2016-07/msg00020.html)

Anyway, v48 isn't too far off ;)

Edit: re. "*I'm aware I an download and install the latest directly from Mozilla, but I wonder what will happen to future updates if I do that.*", you should know that installing software from anywhere other than the official Ubuntu repos (aka the Software Center) *could* be risky. But, just to answer your question, Firefox will update by itself because the version you'll get direct from Mozilla has a built-in internal updater and the updates will mostly be speedier than the ones provided by the Ubuntu repos because, in the latter case, certain checks and modifications may need to be done before the update is made available to Ubuntu users.

---

### Post by eharman on 2016-07-22
Thanks very much for the information. Since I want it for running WebDriver I think I'll go ahead and download it from Mozilla. 

Again, thanks.

---

