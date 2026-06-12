---
title: "Package manager error"
date: 2013-02-08
forum: New to Ubuntu
---

### Post by lashtl on 2013-02-08
I was attempting to install Turboprint and received this error message:
'Unknown error <type exceptions system error> E: the package turboprint needs to be reinstalled, but I can't find an archive for it'

There was a CD in the drive (E:) at the time but it had nothing to do with turboprint.
I downloaded the .deb file and attempted to install it and that's when the trouble happened.   The package manager or software center won't open at all now.   Is there any way of clearing this error?

Thanks

---

### Post by furything on 2013-02-08
Try remove package first
```
sudo dpkg -r Turboprint
```

---

### Post by lashtl on 2013-02-09
> **furything said:**
> Try remove package first
```
sudo dpkg -r Turboprint
```

I tried this command and the error message was :

dpkg: error processing turboprint (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 turboprint
 
I tried to install turboprint again, but just received the same error message and both software center and package manager are disabled by this error.

I hope I don't have to reinstall ubuntu to get rid of this error.

Thanks for any help

---

### Post by ibjsb4 on 2013-02-09
You can remove any leftover packages manually by opening Nautilus and doing a search on "turboprint" and remove any packages.  You need sudo to do this, so in terminal enter:

```
gksudo nautilus
```You can also try autoremove command.

```
sudo apt-get autoremove turboprint
```

[https://help.ubuntu.com/community/AptGet/Howto#Removal_commands](https://help.ubuntu.com/community/AptGet/Howto#Removal_commands)

---

### Post by lashtl on 2013-02-10
> **ibjsb4 said:**
> You can remove any leftover packages manually by opening Nautilus and doing a search on "turboprint" and remove any packages.  You need sudo to do this, so in terminal enter:

```
gksudo nautilus
```You can also try autoremove command.

```
sudo apt-get autoremove turboprint
```[https://help.ubuntu.com/community/AptGet/Howto#Removal_commands](https://help.ubuntu.com/community/AptGet/Howto#Removal_commands)

I tried the search in nautilus with no results.
I tried the autoremove command .  The same error message cam back:

'the package turboprint needs to be reinstalled, but I can't find an archive for it'

Thanks for your help.  We will eventually find the right solution!

---

### Post by lashtl on 2013-02-10
is there any way to replace package manager and software center without having to reinstall ubuntu?

---

### Post by ibjsb4 on 2013-02-10
Yes you can.  I do not have package manager or software center installed.  Instead I use synaptic package manager.  But why would you want to do this?

---

### Post by lashtl on 2013-02-10
> **ibjsb4 said:**
> Yes you can.  I do not have package manager or software center installed.  Instead I use synaptic package manager.  But why would you want to do this?

I actually have synaptic package manager too.  My thought was that if you reinstalled both package manager and software center then that would eliminate the error.

Actually another question is that if such an error occurred why didn't the program come back with a dialog which would allow you to abort/cancel this install or provide a different path for the install file.

---

