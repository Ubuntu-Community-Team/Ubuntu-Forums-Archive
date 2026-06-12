---
title: "How to uninstall Adobe Acrobat"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by txtinman on 2008-10-19
I installed Acrobat from their website, but would now like to uninstall it. I know I can delete the files and directory, but is there a correct way to uninstall software that is not installed with the synaptic package manager?

---

### Post by gjoellee on 2008-10-19
1.that's easy... ok, fire up the Terminal...
2. Enter this command
```
sudo dpkg -r <packagename>
```
remember to replace "<packagename> with the real package name.

---

### Post by txtinman on 2008-10-19
> **gjoellee said:**
> 1.that's easy... ok, fire up the Terminal...
2. Enter this command
```
sudo dpkg -r <packagename>
```
remember to replace "<packagename> with the real package name.

I don't think this was a package file. I got the following error:

```
dpkg - warning: ignoring request to remove acroread, only the config
 files of which are on the system.  Use --purge to remove them too.
```

---

### Post by knix on 2008-10-19
Can you still run acrobat?
If not, use dpkg -r --purge acroread
You can try it for good measure anyhow
Adobe does distribute debs
Otherwise, try to find the installer you used and run it with the --uninstall option (I don't know if this works, but it might, since it does for some other installers)

---

### Post by kkruecke on 2008-12-17
System->Adminstration->Synaptic Package Manager. Install xpdf-reader.

---

### Post by sayems on 2008-12-17
sudo apt-get remove acroread

---

### Post by donkyhotay on 2008-12-17
Umm... are you trying to uninstall adobe acrobat (a costs-money program that doesn't have a native linux client) or adobe reader (PDF viewer thats a no-money download with native linux client)? If your uninstalling reader then you would want to follow the instructions mentioned above, if it is actual acrobat on the other hand you would want to uninstall via wine. Pretty certain your working with reader though.

---

