---
title: "[SOLVED] dpkg -r program not working"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by Bölvaður on 2008-09-16
This should be easy enough.
I installed a .deb package cxchromium_0.9.0-1_i386.deb which is crossove + chromium, and worked fine until I wanted to go to webpages with it ^^

I can start chromium up with terminal and the deb package seems to have set everything up except so it would be able to be uninstalled.

dpkg -r chromium does not work :
```

gummi@BlackBobcat:~$ sudo dpkg -r chromium
dpkg - warning: ignoring request to remove chromium which isn't installed.
```

So obviusly it is'nt listed... and I am not sure how to do that.

I'd rather want to learn how to make dpkg work it out, than locate and delete every file manualy.

Help?

---

### Post by Mornedhel on 2008-09-16
It doesn't show in Synaptic, under "Local installation" or something ? There's a tab for this, but I don't remember the exact name, and I'm running Mandriva at the moment. From there you should be able to remove it.

---

### Post by iaculallad on 2008-09-16
Try:

```
sudo dpkg -r cxchromium
```

---

### Post by szymon_g on 2008-09-16
dpkg is a tool, that should be used when you work with local .deb files, e.g.- when you downloaded program that isnt in repo.
in most cases, if you want to install application, type

sudo aptitude install name_of_application

---

### Post by Mornedhel on 2008-09-16
> **szymon_g said:**
> dpkg is a tool, that should be used when you work with local .deb files, e.g.- when you downloaded program that isnt in repo.
in most cases, if you want to install application, type

sudo aptitude install name_of_application

You think Chromium is in the repositories ? He's not talking about Chromium the side-scroller game here, he's talking about the Crossover port of Google Chrome.

Edit : iaculallad has it right.

---

### Post by Bölvaður on 2008-09-16
> **iaculallad said:**
> Try:

```
sudo dpkg -r cxchromium
```


omf[nonexisting]g, why didn't I think of that -.-

btw isn't there a lookup command that finds part of the name, like there I could have looked for "chrom" and it would give me every program that includes that in the name.

perhaps is it possible to make dpkg list all installed programs and use grep to find my program?

---

### Post by iaculallad on 2008-09-16
To get the applications installed, use:

```
dpkg --get-selections
```

and to save it to a file:

```
dpkg --get-selections > installed_apps
```

and to locate your applications name using grep:

```
dpkg --get-selections | grep application_name
```

---

### Post by Bölvaður on 2008-09-16
> **iaculallad said:**
> To get the applications installed, use:

```
dpkg --get-selections
```

and to save it to a file:

```
dpkg --get-selections > installed_apps
```

and to locate your applications name using grep:

```
dpkg --get-selections | grep application_name
```

 I dont see the reason for saving it to a file, but this is great tool to remember imo, thank you very much.

---

### Post by Mornedhel on 2008-09-16
> **Bölvaður said:**
> I dont see the reason for saving it to a file

Backup for future reinstallations. Better than spending an hour in Synaptic trying to remember what else I installed last time.

---

### Post by iaculallad on 2008-09-16
> **Bölvaður said:**
> I dont see the reason for saving it to a file, but this is great tool to remember imo, thank you very much.

-You can use it to do application re-installation-

To create backup of the applications installed:

```
dpkg --get-selections **[COLOR="DarkRed"]>[/COLOR]** ~/installed_apps
```

To do the re-installation:

```
sudo dpkg --get-selections **[COLOR="DarkRed"]<[/COLOR]** ~/installed_apps
```

---

