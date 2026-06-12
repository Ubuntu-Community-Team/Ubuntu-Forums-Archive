---
title: "How to download with terminal."
date: 2013-06-03
forum: New to Ubuntu
---

### Post by kriscross07 on 2013-06-03
Hello guys I would like to know if you could download stuff from the  ubuntu software center, if you can please tell me the command to type.

(Optional) It would also be nice to know how to download files from the internet on the terminal.

---

### Post by snowpine on 2013-06-03
To install applications from the terminal (same as software center), use "apt-get":

```
sudo apt-get install foo
```

Where "foo" is the name of the application.

To download a file from the internet, use "wget":

```
wget http://www.example.com/foo
```

---

### Post by kriscross07 on 2013-06-03
Thank you soooo much downloads wouldn't work on software center, internet wouldn't help me (exept for this website).

---

### Post by MidnightGrey on 2013-06-04
If your software centre is not working properly, that isnt a problem you should ignore lightly.

---

### Post by Lars Noodén on 2013-06-04
If you are using [apt-get](http://manpages.ubuntu.com/manpages/raring/en/man8/apt-get.8.html), you should periodically reload the package index so that APT knows the latest versions of the packages.  

```

sudo apt-get update

```

Usually once per session is enough, before you start adding or removing packages.

But if the Software Center is not working for you, you should look into getting that fixed.

---

### Post by Rob Sayer on 2013-06-04
> **MidnightGrey said:**
> If your software centre is not working properly, that isnt a problem you should ignore lightly.

100% here on that.  Get that working properly.  Your software sources may be buggered up somehow, and playing around on the terminal wouldn't help that one bit.  You cpould break them worse.

Actually, my version of that (actually muon installer in kubuntu) may not be working now and I wouldn't have noticed.  I almost always use synaptic package manager to install programs.  It works a lot better and keeps better log records.

It's also much better to stick to beta tested repositories in ubuntu until you really know what you're doing.  You can really mess up your dependencies with some ppa's.

You should realize that software downloads aren't "in software centre".  It's in the repos.  Software centre is just another front end for apt, one of several.  I'd learn how to use synaptic if I were you.

---

