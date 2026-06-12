---
title: "C/GTK Stopwatch"
date: 2008-09-20
forum: Programming Talk
---

### Post by sq377 on 2008-09-20
I wrote a program I find useful, now what?  If others find it useful, I'd like to share it, but how should I go about it?

Also, I'd like some criticism on the code if anyone wants to look over it.

[IMG]http://i37.tinypic.com/i1xu6h.png[/IMG]

Thanks

---

### Post by ad_267 on 2009-06-02
Well it's a long time since you posted this but thought I'd just say thanks, I've found this little application quite useful. :)

---

### Post by lyman18 on 2010-05-07
I would like to test this.  I tried to compile this code with gcc, and create an output file.  Is there a step I am missing.
Thanks
-Matt

---

### Post by ad_267 on 2010-05-07
Here's step by step instructions in terminal commands, assuming you're in the directory where you downloaded the .tar.gz file. You might have to install the cmake package first:

```
tar -xzf stopwatch.tar.gz
cd stopwatch
cmake .
make
./stopwatch
```

At the cmake step it might also complain about any missing libraries you have to install. Install them and run cmake again.

---

### Post by nvteighen on 2010-05-08
Hm... maybe this really deserves to be a Launchpad project. There you'll find an easy way to distribute your application (and maybe even get collaboration). The only requirement is that you release your project under a FOSS license.

---

### Post by lyman18 on 2010-05-10
Thanks! Worked Great


> **ad_267 said:**
> Here's step by step instructions in terminal commands, assuming you're in the directory where you downloaded the .tar.gz file. You might have to install the cmake package first:

```
tar -xzf stopwatch.tar.gz
cd stopwatch
cmake .
make
./stopwatch
```

At the cmake step it might also complain about any missing libraries you have to install. Install them and run cmake again.

---

