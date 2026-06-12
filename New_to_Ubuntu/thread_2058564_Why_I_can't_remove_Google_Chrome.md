---
title: "Why I can't remove Google Chrome?"
date: 2012-09-16
forum: New to Ubuntu
---

### Post by manudo on 2012-09-16
I want to remove Google Chrome so I run in terminal:

```
sudo apt-get remove google-chrome
```And appears an error that I can't remove it, what I have to do now?

Full error is attached.

Thank in advance! ;)

---

### Post by critin on 2012-09-16
Hello!

It isn't really an error message, it's an information message.  Like it says,* virtual packages like google-chrome can't be removed.*

You can remove it from the desktop or launcher though, and not have to look at it.
Or just not use it.

---

### Post by vasa1 on 2012-09-16
> **manudo said:**
> I want to remove Google Chrome so I run in terminal:

```
sudo apt-get remove google-chrome
```And appears an error that I can't remove it, what I have to do now?

Full error is attached.

Thank in advance! ;)
Do you actually have a functional installation of Google Chrome?

There was a thread some time ago about virtual packages. I'll see if I find a link to it.

---

### Post by vasa1 on 2012-09-16
See if this link makes any sense:
[http://ubuntuforums.org/showpost.php?p=12072314&postcount=9](http://ubuntuforums.org/showpost.php?p=12072314&postcount=9)

---

### Post by itolf on 2012-09-16
Would using --purge to remove the config files help for this?

```
sudo apt-get --purge remove <package name>
```

itolf.

---

### Post by vasa1 on 2012-09-16
> **manudo said:**
> I want to remove Google Chrome so I run in terminal:

```
sudo apt-get remove google-chrome
```And appears an error that I can't remove it, what I have to do now?

Full error is attached.

Thank in advance! ;)
Try 
**sudo apt-get remove google-chrome-stable** or
**sudo apt-get remove google-chrome-beta** or
**sudo apt-get remove google-chrome-unstable**

If you use
**sudo apt-get purge program-name** it will get rid of config files in the system (except for those in /home which have to be removed additionally.)

---

### Post by itolf on 2012-09-16
> **vasa1 said:**
> Try 
**sudo apt-get remove google-chrome-stable** or
**sudo apt-get remove google-chrome-beta** or
**sudo apt-get remove google-chrome-unstable**

If you use
**sudo apt-get purge program-name** it will get rid of config files in the system (except for those in /home which have to be removed additionally.)

That is handy to know, thanks :)

---

### Post by Frogs Hair on 2012-09-16
You will find the Synaptic Package Manager from the software center a good tool for locating correct package names and removing/installing packages.

---

### Post by linuxorunix on 2012-09-16
Dear manudo,

You could try

```
sudo apt-get autoremove google-chrome
```

This will, probably, remove all the Google Chrome files and settings.

**Good luck!** :)

The uninstall process of Google Chrome is also described at AskUbuntu.com, so please follow this link: [http://askubuntu.com/questions/67047/how-to-uninstall-google-chrome]("http://askubuntu.com/questions/67047/how-to-uninstall-google-chrome") 

**It pretty much says the same as I did, but now you can "hear" it form a reliable resource.**

Yours faithfully,
linuxorunix

---

### Post by manudo on 2012-09-16
> **vasa1 said:**
> Try 
**sudo apt-get remove google-chrome-stable**

Finally removed, thanks everyone! :D

---

### Post by kemtnbkr on 2012-09-16
> **manudo said:**
> Finally removed, thanks everyone! :D


Remember to mark thread as solved, then.  Glad that your issue was resolved.

---

### Post by manudo on 2012-09-16
> **kemtnbkr said:**
> Remember to mark thread as solved, then.  Glad that your issue was resolved.

Done.

---

### Post by vasa1 on 2012-09-17
> **linuxorunix said:**
> Dear manudo,

You could try

```
sudo apt-get autoremove google-chrome
```

This will, probably, remove all the Google Chrome files and settings.

**Good luck!** :)

The uninstall process of Google Chrome is also described at AskUbuntu.com, so please follow this link: [http://askubuntu.com/questions/67047/how-to-uninstall-google-chrome]("http://askubuntu.com/questions/67047/how-to-uninstall-google-chrome") 

**It pretty much says the same as I did, but now you can "hear" it form a reliable resource.**

Yours faithfully,
linuxorunix

**sudo apt-get autoremove google-chrome** is **not** what the link you provided suggests.

---

### Post by linuxorunix on 2012-09-17
> **vasa1 said:**
> **sudo apt-get autoremove google-chrome** is **not** what the link you provided suggests.

[B]@vasa1, I'm very sorry, I was just trying to help him, I am, again, very sorry that you can't appreciate my help. I hope that I will not bother you again in the nearby future.
[/B]
Yours faithfully,
linuxorunix

---

### Post by EdBecerra on 2012-11-16
> **Frogs Hair said:**
> You will find the Synaptic Package Manager from the software center a good tool for locating correct package names and removing/installing packages.

Not if Synaptic can't FIND it. I screwed up, installed an old (v11) Chrome on an older Ubuntu 8.04, and now I can't get rid of it.

Help?

---

### Post by GreatDanton on 2012-11-16
8.04 is not supported anymore. Since there are no security updates, it's not advised to run this version (install 12.04). However if you insist make a new thread.

Regards.

---

### Post by Marcelo Ramone on 2013-01-31
Hello,

I deleted google-chrome but now i'm trying to delete config directory...

```
$ rm .config/google-chrome/ -Rfv
«.config/google-chrome/Default/User StyleSheets/Custom.css» borrado
rm: no se puede borrar «.config/google-chrome/Default/User StyleSheets»: El directorio no está vacío

```

"El directorio no está vacío" = "The directory is not empty"

But, no mather the directory is empty or not, I'M doing a rm with -Rfv

rm -rfv should be able to delete recursively .config directory without restrictions...

---

