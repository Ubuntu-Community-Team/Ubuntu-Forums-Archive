---
title: "GIMP doesn't start."
date: 2011-09-16
forum: New to Ubuntu
---

### Post by maqtanim on 2011-09-16
I am using Kubuntu 11.04. Recently I can't start/run the Gimp in my Kubuntu. If I double click the icon it shows a busy mouse pointer for a few seconds and then does nothing. If I try to run it from the terminal I get the following message:

```
(gimp:2221): GLib-WARNING **: /build/buildd/glib2.0-2.28.6/./glib/goption.c:2132: ignoring no-arg, optional-arg or filename flags (8) on option of type 0
Segmentation fault

```

Any idea how to solve it?

---

### Post by P05TMAN on 2011-09-17
> **maqtanim said:**
> I am using Kubuntu 11.04. Recently I can't start/run the Gimp in my Kubuntu. If I double click the icon it shows a busy mouse pointer for a few seconds and then does nothing. If I try to run it from the terminal I get the following message:

```
(gimp:2221): GLib-WARNING **: /build/buildd/glib2.0-2.28.6/./glib/goption.c:2132: ignoring no-arg, optional-arg or filename flags (8) on option of type 0
Segmentation fault

```Any idea how to solve it?

Have you already tried to reinstall it? Perhaps a purge, then reinstall from the command line?

---

### Post by SeijiSensei on 2011-09-17
Did you install GIMP from the repositories or somewhere else?  There's no guarantee another build will work on Ubuntu because of differences in libraries.  The error you report sounds like such a problem.

---

### Post by donkyhotay on 2011-09-17
> **SeijiSensei said:**
> Did you install GIMP from the repositories or somewhere else?  There's no guarantee another build will work on Ubuntu because of differences in libraries.  The error you report sounds like such a problem.

Yeah it sounds like a problem with libraries to me as well. Most likely caused by either not installing GIMP from the repos or by adding 3rd party repos to your sources and either GIMP or the libraries updating and becoming out of sync.

---

### Post by realzippy on 2011-09-17
Also had this problem when escaped to Kubuntu.
Solution:
Set your gtk appearance (System Settings > Application Appearance > GTK+ Appearance ) back to Raleigh, launch Gimp once, then you can change gtk appearance back.
Gimp will start then...

---

### Post by josephmills on 2011-09-17
I ran across this hope that it helps :)


[http://ubuntuforums.org/showthread.php?t=1746905](http://ubuntuforums.org/showthread.php?t=1746905)

---

### Post by maqtanim on 2011-09-17
> **realzippy said:**
> Also had this problem when escaped to Kubuntu.
Solution:
Set your gtk appearance (System Settings > Application Appearance > GTK+ Appearance ) back to Raleigh, launch Gimp once, then you can change gtk appearance back.
Gimp will start then...

Thanks a lot... it worked for me! Is this a common problem for Kubuntu? They should fix it!

By the way, I've installed gimp from the official Ubuntu repo.

---

### Post by realzippy on 2011-09-17
Yes,many kde 4.x users installing gimp seem to be affected.
[Link]("http://ubuntuforums.org/showthread.php?t=1746905") in post #6 confirms this...

---

