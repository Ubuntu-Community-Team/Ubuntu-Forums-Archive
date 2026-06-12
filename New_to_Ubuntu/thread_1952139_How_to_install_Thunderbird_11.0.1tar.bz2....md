---
title: "How to install Thunderbird 11.0.1tar.bz2..."
date: 2012-04-03
forum: New to Ubuntu
---

### Post by sillyboy on 2012-04-03
I've downloaded the file.  How do I install t-bird V 11.0.1 tar.bz2?

Why is this stuff still a mystery to some, this tar ball thing.  Can't this be simplified?

Thanks

---

### Post by QIII on 2012-04-03
Why are you using a tarball?

I believe the latest Tbird is available in the repos.

Version 11.0.1, I think.

---

### Post by sillyboy on 2012-04-03
> **QIII said:**
> Why are you using a tarball?

I believe the latest Tbird is available in the repos.

Version 11.0.1, I think.

When I clicked on the "Time for an Update", on the splash screen of T-bird, it lead me to a tar ball.

I did a search in SPM and nothing showed up.  I looked for a .deb file, and nothing again.

If you or someone else can help me...please do.

Thanks

---

### Post by QIII on 2012-04-03
How did you install it initially?  What version do you have?

11.0.1 is the most recent stable release.  There is a 12.0 Beta, but you don't want a Beta.

11.0.1 is available in the Ubuntu repositories.  My recommendation is to uninstall it however you installed it and reinstall it from the repositories using the Software Center or Synaptic.  It is definitely available in Synaptic.  If you type "thunderbird" it should be the very first selection.  Make sure you have main, universe, restricted and multiverse enabled in your sources.  I'm pretty sure it's in main.

---

### Post by babsaai on 2012-04-04
Open Terminal and add thunderbird to the repositories, then update your system:

sudo add-apt-repository ppa:mozillateam/thunderbird-stable
sudo apt-get update
sudo apt-get upgrade
**

---

### Post by sillyboy on 2012-04-05
> **babsaai said:**
> Open Terminal and add thunderbird to the repositories, then update your system:

sudo add-apt-repository ppa:mozillateam/thunderbird-stable
sudo apt-get update
sudo apt-get upgrade
**

Thank You babsaai!!!!  Installed and running great!

---

