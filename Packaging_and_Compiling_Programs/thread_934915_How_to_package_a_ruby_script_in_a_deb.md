---
title: "How to package a ruby script in a deb?"
date: 2008-10-01
forum: Packaging and Compiling Programs
---

### Post by grigio on 2008-10-01
Hi, I have to package a ruby script with 2 dependencies into a deb, what's the best way to do it?
I read about a lot of software that create debs, checkinstall, epm, pbuilder,.. but I don't know which one suits better for my needs.

---

### Post by Nonno Bassotto on 2008-10-02
I asked a similar question a few days ago, and [here]("http://ubuntuforums.org/showthread.php?t=933689") is the answer.

Just create a directory called myrubyscript containing inside the directory structure and a special directory called DEBIAN. Inside the latter put a file called control with all the information about dependencies and so on. In the link above there is an example. Then use
```

sudo dpkg-deb -b myrubyscript

```

---

### Post by grigio on 2008-10-03
I read your thread thanks.

---

