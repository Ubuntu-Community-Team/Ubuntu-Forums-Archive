---
title: "How Does ubuntu-bug lubuntu-desktop work?"
date: 2013-09-01
forum: New to Ubuntu
---

### Post by toady2 on 2013-09-01
I read the man pages and it was pretty confusing. Could someone provide me with an example of how to use that command? I have an issue with lxde desktop environment and openbox.

Thanks

---

### Post by vasa1 on 2013-09-01
What happens when you run "apport-bug" from your terminal? Just for completeness, are you running Lubuntu 13.04 or what?

And what is your issue with lxde/openbox? Could you describe it?

---

### Post by toady2 on 2013-09-01
The thread that I started a couple of days ago describes this issue with lxde and openbox. --> [http://ubuntuforums.org/showthread.php?t=2171042](http://ubuntuforums.org/showthread.php?t=2171042)

If i run that command you told me I get an error message from a new window that says  "You need to specify a package or a PID."
Yes, I'm running Lubuntu 13.04

*EDIT*
I think it's an issue with openbox and LXDE. It could be something else.

---

### Post by vasa1 on 2013-09-01
Can't help you with the linked issue but I suggested "apport-bug" because of this:
>        You  should  always  start  with  running apport-bug without arguments,
       which will present a list of known symptoms.  This  will  generate  the
       most useful bug reports.

       If  there  is  no  matching symptom, you need to determine the affected
       program or package yourself. You can provide a package name or  program
       name to apport-bug, e. g.:

           apport-bug firefox
           apport-bug /usr/bin/unzip

Let's hope someone can help!

---

### Post by cariboo on 2013-09-01
Ubuntu-bug or apport-bug is used to report a bug in a particular package, for example if you have a problem, and you aren't really sure what package is the problem, you can use:

```
apport-bug linux
```

the bug triagers will have a look at it, and advise what the problem seems to be. Using the bug report utility assumes that you have a working desktop, and your default browser works.

---

### Post by phillw on 2013-09-01
I'd suggest having a read of the classroom sessions that were held on bugs for the QA / Testing people a couple of months ago. The session run by Brian goes into ubuntu-bug in more detail.

[https://wiki.ubuntu.com/Testing/Activities/Classroom/Saucy#Reporting_Bugs](https://wiki.ubuntu.com/Testing/Activities/Classroom/Saucy#Reporting_Bugs)

Regards,

Phill.

---

### Post by IbsUser on 2013-09-01
Besides the useful information we have above, I'd like to add some more links.

Ubuntu Packages: good place to find the packages names:
[http://packages.ubuntu.com/search?keywords=lubuntu-desktop&searchon=names&suite=raring&section=all](http://packages.ubuntu.com/search?keywords=lubuntu-desktop&searchon=names&suite=raring&section=all)

From the search result above, you'll see that lubuntu-destktop is a metapackage, full of lots of other packages:
[http://packages.ubuntu.com/search?keywords=lubuntu-desktop&searchon=names&suite=raring&section=all](http://packages.ubuntu.com/search?keywords=lubuntu-desktop&searchon=names&suite=raring&section=all)

When looking for bugs and not sure about the package name, a good tool is:
```
apport-cli -w
```

This tool will enable you to click on the bug window/software and it'll recognize the package name automatically.

More info about apport-cli:
```
man apport-cli
```

Don't forget to read the other links on the other comments. They're really useful.

Best regards and good luck finding bugs!

---

