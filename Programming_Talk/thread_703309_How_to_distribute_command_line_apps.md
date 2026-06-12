---
title: "How to distribute command line apps?"
date: 2008-02-21
forum: Programming Talk
---

### Post by Torajima on 2008-02-21
I'm finishing up work on a command line application that I've written in Python, and I'm wondering how to distribute it.

It would be nice if folks could install it with apt-get.

Also, how does one go about creating a man page? I found a FAQ, but it was... confusing.

Thanks!

---

### Post by pmasiar on 2008-02-21
Is your application in one file? Or it has multiple files, config files etc?

Single file app can be just dropped into directory in path and is usable. Packaging program for distribution by apt is more complicated - and you need to persuade  people  to add your repository, which might have strange consequences. Simpler is to get google code account and host it there, allowing checkout via subversion.

---

### Post by Torajima on 2008-02-21
It is one large file.... I thought it might be easier to distribute if I didn't break it into modules.

And since it is a command line app, I'd like to create a man page for it... but I'm not sure where to begin.

---

### Post by LaRoza on 2008-02-21
> **Torajima said:**
> It is one large file.... I thought it might be easier to distribute if I didn't break it into modules.

And since it is a command line app, I'd like to create a man page for it... but I'm not sure where to begin.

You would be better of just using the -h and --help flags, it would be easier.

---

### Post by nick_h on 2008-02-21
> Also, how does one go about creating a man page?
man pages are just zipped text files with formatting macros.  Have a look in /usr/share/man/man1 for some examples.

A quick google should give you the basics:
[http://www.fnal.gov/docs/products/ups/ReferenceManual/html/manpages.html](http://www.fnal.gov/docs/products/ups/ReferenceManual/html/manpages.html)
[http://www.unixreview.com/documents/s=8925/ur0312i/](http://www.unixreview.com/documents/s=8925/ur0312i/)
[http://wiki.redbrick.dcu.ie/mw/Creating_Man_Pages](http://wiki.redbrick.dcu.ie/mw/Creating_Man_Pages)

There is also a program called manedit which is in the repositories which would be worth investigating.

---

### Post by WW on 2008-02-21
One way you could distribute a .deb package is to use the  [Ubuntu Personal Package Archive](https://launchpad.net/ubuntu/+ppas).

---

### Post by Torajima on 2008-02-22
> **LaRoza said:**
> You would be better of just using the -h and --help flags, it would be easier.

What is the proper method to display said help files?

How do you make the display behave properly ('space' to go forward, 'b' to move back, 'q' to quit)?

---

### Post by nick_h on 2008-02-22
The -h and --help flags normally just output simple usage instructions without paging.  If you wanted navigation you could pipe the output to *less*. e.g.
```
ls --help | less
```
If you have a large help file perhaps a man page would be appropriate in addition to help flags.

---

### Post by bobbocanfly on 2008-02-22
Stick this code at the top of your script and fill in the information and you should be good to go. Otherwise you could use the getopt library (recommended if your users are submitting information via command line args).

```
import sys

if sys.argv[1] == "-h" or sys.argv[1] == "--help":
    print "How -to use your code"
```

---

