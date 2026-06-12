---
title: "Launch Gambas3 without installing?"
date: 2012-01-30
forum: Programming Talk
---

### Post by fallenshadow on 2012-01-30
I just compiled Gambas3 and I want to launch the app via a binary rather than installing it manually.

Is this possible? Where can I find the compiled executable? :confused:

---

### Post by kalaharix on 2012-01-31
Hi

Not sure whether the app you refer to is Gambas itself or an app created with Gambas.

Gambas exectubles are in /usr/local/bin but you should be able to just 'gambas3' from command line. I just put a shortcut on the desktop.

For the app you have made with Gambas: there is a button and menu entry for create executable. This creates <application>.gambas in a directory of your choosing. The Gambas executable is tokenised and needs the Gambas runtime which you will have installed with the package.

You can also create a .deb installation package from the menu. This will bundle dependencies, runtime and application for installation on other machines which don't need the development package.

---

### Post by fallenshadow on 2012-01-31
Oh I am talking about Gambas3 itself not a Gambas application.

I compiled it but I don't wanna manually install it as I hate doing that. Since it is not installed the executables will not be in /usr/local/bin.

Do you know the name of the executable? I could do a search in the compiled source to find it.

EDIT: Never mind I just went ahead and manually installed it.

---

