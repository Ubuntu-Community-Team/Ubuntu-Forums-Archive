---
title: "Python - Bundle your applications/softwares."
date: 2015-04-17
forum: Programming Talk
---

### Post by flaymond on 2015-04-17
Hello people of Ubuntu's, I'm looking for a guide of how to bundle Python intrepreter with your program into a single click executable program. Most of the Linux distro got Python installed, while my target is the other distro(for a reason) that don't have python installed. I wanna try to learn in this way, since freeze tools is failing to "freeze" a program that use 3rd party library/frameworks. I already Googled for pyinstaller and other stuff related to it, and all of them failed to bundle my app (it's PySide/PyQt app). So for short, how can I bundle my app with python intrepreter or make the user auto install the dependencies (like interpreter and the Qt libs) before executing the app(yeah, the user failed to run the app, if there is no depends)?

Any guide or tutorial, will be a lot of help here.

Thanks.

---

### Post by ofnuts on 2015-04-18
It's fairly easy to make a .DEB package dependent on Python, so that its installation includes a python install from the repository if none is present. For instance, a .deb I have contains a "control.tar.gz" that itself contains a "control" file that has a line:
```

Depends: python (>= 2.4), python-support (>= 0.90.0), python-xlib, python-gtk2, librsvg2-common

```

Plenty of .DEB packaging tutorials on Google...

---

### Post by flaymond on 2015-04-18
Is .deb really hard to make actually? I understand, .deb is better for the user, but from my view, the process is hard to make a non-basic one. I found a lot of tutorials about it, but none of them worked for me....can you please provide me the guide or learning resources that worked for you, or that might worked in my case. I'm sorry to ask addtional favor here.

---

### Post by ian-weisser on 2015-04-18
> **InterProg said:**
> my target is the other distro(for a reason) that don't have python installed.
You are talking about the python interpreter as dependency of your application.
How does that distro handle dependencies? Do they have a standard way? A set of packages or equivalent?

---

### Post by flaymond on 2015-04-19
It's based ubuntu, and Python 3 is probably not included with it (modified core). They use apt as usual like Ubuntu, it handle depends just like Ubuntu, but because I'm still a beginner, I want to learn bundle the app with the interpreter or at least..force the user to install depends before running the app.(I know .deb make this easier to link the depends, for making it automatic)

---

### Post by ian-weisser on 2015-04-19
Here's a [good overview of how-to-package]("https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0CB8QFjAA&url=https%3A%2F%2Fwww.debian.org%2Fdoc%2Fmanuals%2Fpackaging-tutorial%2Fpackaging-tutorial.en.pdf"). It's not python-specific, but it will get you started on the right path.
Here's a [good list of python-specific settings]("https://wiki.debian.org/Python/LibraryStyleGuide") and instructions for your package's debian/ directory.

The first package is challenging, sometimes a bit overwhelming. However, it's mostly tedious - not actually difficult.
There are lots of conflicting tutorials out there. Everybody does packaging a slightly different way, and uses different helper-tools, to match their workflow.

ofnuts is right - your package should *depend *upon python in the debian/control file. Bundling done.

---

### Post by flaymond on 2015-04-20
Thank you for all of your help, and also thanks for the links ian-weisser.

I build the package smoothly after reading those stuff. DEB package concept is not hard for me anymore, :D

---

