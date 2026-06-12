---
title: "Chrome browser doing weird things"
date: 2014-12-17
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2014-12-17
When I try to use my installed version of Chrome, a message pops up saying something like: This version of Chrome no longer supported....

When I type in about:Chrome, or Chrome://Chrome, nothing happens.

When I click on Settings, nothing happens

When I go to the software center, it does not show Chrome as an installed program, and when I search for Chrome, it doesn't seen ti even know it exists.

How do I uninstall the version (that my computer does not seem to know is there) and install a new version?

---

### Post by vasa1 on 2014-12-17
What does ```
dpkg --get-selections | grep "chrome"
```return?

---

### Post by nerdtron on 2014-12-17
And what version of Ubuntu are we talking here?

---

### Post by GrouchyGaijin on 2014-12-17
> **Odyssey1942 said:**
> 
When I go to the software center, it does not show Chrome as an  installed program, and when I search for Chrome, it doesn't seen ti even  know it exists.

How do I uninstall the version (that my computer does not seem to know is there) and install a new version?

Firstly, forget that old and in the way stuff I read in your signature!  Everyone starts a total noob.  I've been running Linux as my primary OS since Ubuntu 10.10 and there are a lot of things I have no clue about.  The great thing about this forum is that people here **genuinely** like to help others.  I don't think I've seen more than a handful of "RTFM" type replies in the four years I've been visiting this site.

What happens when you run: (You will be asked for your password to run the command as sudo.)
```
sudo apt get-remove google-chrome-stable 
```
assuming that you installed the stable version.  If you installed the beta then replace stable with beta.
You *may* not even need the -stable.  ```
sudo apt-get remove google-chrome
``` may suffice.

Can I ask, why do you want to run Chrome?  I used Chromium for a long time.  Chromium is in the repository and is basically the same as Chrome, but not a Google product.  I switched over to Firefox because I kept having problems with the default profile not being able to be opened.

---

### Post by j0sk on 2014-12-17
To find what chrome package you have installed:

```
$ dpkg --get-selections | grep 'chrome'
```

---

### Post by vasa1 on 2014-12-17
> **GrouchyGaijin said:**
> ...
Can I ask, why do you want to run Chrome?  I used Chromium for a long time.  Chromium is in the repository and is basically the same as Chrome, but not a Google product. ...
Most of the Chromium devs are Google employees, AFAICT.

Chromium is not "basically the same as Chrome" because flash is missing in the former. As it stands, it's easier to install Google Chrome and have flash running OOTB even though Google Chrome is not in the repos than it is to install Chromium (which unfortunately is often not updated in a timely manner in the repo maybe because it's in Universe and not in Main) and then install pepper flash (which AFAICT involves a behind-the-scenes download of Google Chrome in any case).

Oh, and pepper flash is a "Google product" in that it is made by Google in collaboration with Adobe.

---

### Post by GrouchyGaijin on 2014-12-21
> **vasa1 said:**
> Most of the Chromium devs are Google employees, AFAICT.

Chromium is not "basically the same as Chrome" because flash is missing in the former. As it stands, it's easier to install Google Chrome and have flash running OOTB even though Google Chrome is not in the repos than it is to install Chromium (which unfortunately is often not updated in a timely manner in the repo maybe because it's in Universe and not in Main) and then install pepper flash (which AFAICT involves a behind-the-scenes download of Google Chrome in any case).

Oh, and pepper flash is a "Google product" in that it is made by Google in collaboration with Adobe.

Well then, my mistake.  Thank you for the clarification.

---

