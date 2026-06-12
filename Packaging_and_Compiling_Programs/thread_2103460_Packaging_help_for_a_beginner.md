---
title: "Packaging help for a beginner"
date: 2013-01-10
forum: Packaging and Compiling Programs
---

### Post by David Kerr on 2013-01-10
Hi everyone.

This is my first post and I am very new to packaging.

I have been working on creating packages for a few days now. I am using pbuilder as I want to start off by making my packages as well as I can and not just throwing them together.

I have been doing a lot of reading and now have my package created.

My issue is when the package is extracted the file ownership is set as root. I know that these are being set by the machine that created the package.

How do you set the uids of the files to the user that installed it (user as in who they were before they became root).

I have extracted the spotify deb and had a look at there postinst file to try and get a feel for how others are doing it.

---

### Post by sudodus on 2013-01-10
Do you use sudo?

In that case, if you call a script with

```
sudo script-name
``` it will run with the user variable $USER equal to root.

If you call a script without sudo, but have sudo commands inside it, or call another script with sudo inside it, you can use $USER with the value of the current user. Set an internal variable if you like, and use that value to set the ownership of the files that should be owned by the current user. For example

```
myname=$USER
```

---

