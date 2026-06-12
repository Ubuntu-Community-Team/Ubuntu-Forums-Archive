---
title: "Any Gui based alternative to the dash for applications as it never works"
date: 2015-01-24
forum: New to Ubuntu
---

### Post by mrnewtothis on 2015-01-24
Since the update from 10.4 to twelve what ever then thirteen what ever have had this dash that seems to not want to give access to applications so I was wondering if there is any gui that can list applications and allow them to be started with a double click.

Used this to temp fix it 

rm ~/.cache/software-center -R

 need to run:

unity --reset &



Sorry don't have the page but it is only a temp fix that is working while it is using the alternative to unity as it resets unity.

Also tried an add unity home that i found which did not work either

So figure maybe others that have had this problem have found a gui that lists and allows access to applications?

Thanks for any help

---

### Post by Bucky Ball on 2015-01-24
13 whatever is not very specific, but if you are using 13 anything, it is no longer supported. If you are using 13 anything, please upgrade to a supported version. 12.04 LTS is actually a long term support release and is supported until 2017. 14.04 LTS is supported until 2019. Please see [here]("http://ubuntuforums.org/showthread.php?t=2229730"). Good luck.

---

### Post by vasa1 on 2015-01-24
What about [http://www.webupd8.org/2015/01/albert-fast-lightweight-quick-launcher.html](http://www.webupd8.org/2015/01/albert-fast-lightweight-quick-launcher.html) ?

And **Kupfer** is in the software center.

---

### Post by buzzingrobot on 2015-01-24
> **mrnewtothis said:**
> Since the update from 10.4 to twelve what ever then thirteen what ever have had this dash that seems to not want to give access to applications...


That's a long time to go with no "access to applications".  What, exactly, is (not) happening?  If you tap the Super/Windows key and begin entering the name of an application, what happens?

If you've found you constantly need to reset Unity over these various upgrades, perhaps a problem in the initial upgrade is carrying over to subsequent upgrades.

---

### Post by Bucky Ball on 2015-01-24
> **buzzingrobot said:**
> 
If you've found you constantly need to reset Unity over these various upgrades, perhaps a problem in the initial upgrade is carrying over to subsequent upgrades.

And perhaps upgrading to the unsupported '13 whatever' has added to your woes.

---

### Post by mrnewtothis on 2015-01-24
Only updated to 12.04 from 10.4 but as the next offer on the list is 14 assumed 13 that i heard of was coming through updates that I get. Plus I'm sure I keep seeing it listed in the updates that are offered. So just assumed.

What happens when I open Dash is there is no applications offered in the list and all I see is recent files and downloads  and if I search for an application then it comes up with sorry there is no match.

Read a few things on here about the problem and if I need anything then I use the fix that I have above that I found on here to get to the applications I want and then just pin them to the side bar. But that only works the time terminal is open and it is getting a bit messy for that. So will take a look at those applications.

---

### Post by philinux on 2015-01-24
Try this command from a terminal.

```
 sudo apt-get install --reinstall unity-lens-applications unity-lens-files
```

Then restart unity

```
setsid unity
```

---

### Post by buzzingrobot on 2015-01-24
> **mrnewtothis said:**
> 

What happens when I open Dash is there is no applications offered in the list and all I see is recent files and downloads  and if I search for an application then it comes up with sorry there is no match.



Centered along the bottom of the Dash window do you see a row of icons? Also, if you look at the /usr/share/applications folder, do should see many files bearing the names of applications? (An "ls /usr/share/applications' in a terminal should show they all have a '.desktop' extension.  Nautilus won't display the extension.)

Still, given the lengthy upgrade path you've attempted, lack of insight into what was installed on the original 10.04 system, PPA use, etc., and the resulting difficulty diagnosing given all that, simply doing a fresh install of the current 14.04 LTS (assuming you want an LTS) might well be the quickest route to returning to normal.

---

### Post by greg69 on 2015-01-25
You could always switch to Xubuntu. It's the same in most regards apart from using XFCE instead of Unity. It's faster, And more customisable. And it doesn't have that annoying dash :>
Instead it has a top bar which has a dropdown menu. You can add applications to it for quick accessing.

---

### Post by Jonathan Precise on 2015-01-25
Since your saying you had 10.04 LTS (with GNOME 2), let me suggest to you Ubuntu MATE, a lightweight unofficial Ubuntu distro with the MATE desktop, a fork of the GNOME 2 you're used to.

---

### Post by JeQhdMD on 2015-01-25
Jonathan,  10.4 with gnome2 was the normal, standard desktop for Ubuntu (Unity came later).

Mr.New2This,  the dash and ability to filter, find apps, etc. _is second to none_ IMHO.   Something else is totally hosed in your installs if you're experiencing those kind of issues.  The fixes you've been doing are unneeded on a normal, functioning Ubuntu install. 

Suggest you do a "fresh" install of Ubuntu 14.04.1 after backup or saving your critical files.

---

### Post by Jonathan Precise on 2015-01-26
> **JeQhdMD said:**
> Jonathan,  10.4 with gnome2 was the normal, standard desktop for Ubuntu (Unity came later).

Yes, however the OP said that he/she originally installed 10.04 with GNOME 2, so I just suggested he change to another Ubuntu unofficial flavor with similar look-and-feel as before. My suggestion is to install Ubuntu MATE 14.04 LTS.

> **JeQhdMD said:**
> Suggest you do a "fresh" install of Ubuntu 14.04.1 after backup or saving your critical files.

+1. Either Ubuntu MATE or plain Ubuntu, "fresh" installs are recommended when things are messed up.

---

### Post by Bucky Ball on 2015-01-26
I would suggest Xubuntu. Fast, light and highly configuarable. Also an officially supported flavour in the main support areas here. Mate is not. There is a sub-forum for Mate support though and they may have a forum. Good luck whatever you decide.

---

