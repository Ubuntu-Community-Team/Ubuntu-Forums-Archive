---
title: "Distributing improved ppa-purge"
date: 2024-11-05
forum: Packaging and Compiling Programs
---

### Post by jis on 2024-11-05
I have improved the old ppa-purge, but for some reason it was not merged into the Universe repository release. However, I created a [PPA]("https://launchpad.net/~jarnos/+archive/ubuntu/ppa-purge") of my fork. Later I forgot how to update the PPA and maintain it for newer Ubuntu releases. Because [ppa-purge]("https://code.launchpad.net/~jarnos/ppa-purge/+git/ppa-purge") is basically a script, and does not require extra software, I don't have to define dependencies for the package necessarily. Later, to save my time, I just added instructions in the description of the PPA to install it on newer releases than Eoan. But recently on Focal I tried to install my PPA and thereafter `sudo apt update`  gives error:

```
Err:6 http://ppa.launchpad.net/jarnos/ppa-purge/ubuntu eoan InRelease      
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8FB7507974CA87C9
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net/jarnos/ppa-purge/ubuntu eoan InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8FB7507974CA87C9
E: The repository 'http://ppa.launchpad.net/jarnos/ppa-purge/ubuntu eoan InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

I just would like to get my fork easily available for Ubuntu users so that they don't have to use the official buggy ppa-purge that has been unmaintained since December 2016. And distributing the software should be easy as well so that I could concentrate on developing the software. Maybe I should move my script as a separate program so that it wasn't just a fork of ppa-purge in Launchpad. I think it should have a separate bug tracker, if it is not merged. Maybe distribute it as snap package?

There are still issues in my version of ppa-purge. I still don't know, if separate handling of so called soname bumps is needed. Why wouldn't libraries be downgraded as dependencies? Separate handling is an option in my version. Removing many PPAs by single command could be handy, see [here]("https://superuser.com/questions/1854084/ubuntu-24-04-1-lts-update-what-to-do-with-ppa-purge"). 

I have also made a separate script for merely downgrading packages system wide and removing ones that are not available in repositories anymore, but I have not yet released it.

---

