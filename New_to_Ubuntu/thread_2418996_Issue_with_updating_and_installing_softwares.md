---
title: "Issue with updating and installing softwares"
date: 2019-05-15
forum: New to Ubuntu
---

### Post by nebcinder on 2019-05-15
Hi there,

I'm not only new to Ubuntu but new to programming in general; I'm sorry in advance for the stupidity of my question(s). 

I've been looking around online for a while to troubleshoot my issues, and although I've found questions re: similar problems, I'm too much of a beginner to understand the language used to describe the fixes that are suggested. I need explanations that are a little in-depth/basic.

I've been trying to install new software but I keep getting errors re: Release files, like this when I try to update via terminal

```
Reading package lists... Done
W: The repository 'http://archive.ubuntu.com/ubuntu zesty Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://security.ubuntu.com/ubuntu zesty-security Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

I'm afraid that if I keep trying to fix things on my own with my limited understanding of what I'm doing, I'll just keep breaking stuff...

So yeah, if you don't mind helping a desperate newbie, I'd greatly appreciate it.

---

### Post by howefield on 2019-05-15
Zesty repositories are end of life and no longer supported.

Is it Ubuntu 17.04 that you are using ?

```
cat /etc/*-release
```

---

### Post by wildmanne39 on 2019-05-15
That is because zesty is no longer supported, is 17.04 what you are running? if so please upgrade to a supported version of ubuntu, I recommend 18.04 LTS because it has 5 years of support.

---

### Post by deadflowr on 2019-05-15
Basically, you're running an old and no longer supported version of Ubuntu.
Consider downloading a fresh clean version, such as Ubuntu 18.04 (codename: bionic) from Ubuntu:
[https://www.ubuntu.com/download/desktop]("https://www.ubuntu.com/download/desktop")

Ubuntu 18.04 is a long term supported release.
And is supported until 2023.

(FTR, the version you have was Ubuntu 17.04 (codename: zesty) which was not a long term supported release and only had 9 months of support.
That supported ended in January 2018).

---

### Post by col48 on 2019-05-15
Recommendation is to do a clean install of 18.04 - ie install from scratch, wiping out 17.04, not attempting to upgrade it.
Of course, if you have any precious data, back it up to external media first, and note any non-default settings you value.

---

### Post by nebcinder on 2019-05-15
Thanks a lot, I'll clean the slate and start over!

---

### Post by oldrocker99 on 2019-05-15
If you're reinstalling, it's a good idea to have a separate /home partition. Then, reinstallations are a breeze. Always back up /home, of course.

Here's how:[https://www.maketecheasier.com/install-ubuntu-with-different-root-home-hard-drives/](https://www.maketecheasier.com/install-ubuntu-with-different-root-home-hard-drives/).

---

### Post by vivek0033 on 2019-05-16
i am instaling any sofware

---

