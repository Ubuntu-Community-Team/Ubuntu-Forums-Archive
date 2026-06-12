---
title: "how to edit open source programs"
date: 2010-02-16
forum: Programming Talk
---

### Post by surfboard3r on 2010-02-16
I am just learning C right now and I am interested in learning how to edit some open source applications for ubuntu 9.10, I have Emacs installed, i just dont know where to go in order to find the files to edit.

---

### Post by Bachstelze on 2010-02-16
Do you have a particular app in mind? Normally, you can just download the source code from the developer's website.

---

### Post by s.fox on 2010-02-16
> **surfboard3r said:**
> I am just learning C right now and I am interested in learning how to edit some open source applications for ubuntu 9.10, I have Emacs installed, i just dont know where to go in order to find the files to edit.

Welcome to the forum.

In order to get the source code you will need to run the following command in terminal:

```
apt-get source packagename
```


-Silver Fox

---

### Post by blur xc on 2010-02-16
> **Silver_fox_ said:**
> Welcome to the forum.

In order to get the source code you will need to run the following command in terminal:

```
apt-get source packagename
```
-Silver Fox

I've also been curious about this- so when you apt-get the source code- where does it go in your filesystem?

Thanks,
BM

---

### Post by Bachstelze on 2010-02-16
> **blur xc said:**
> I've also been curious about this- so when you apt-get the source code- where does it go in your filesystem?

Thanks,
BM

In your current working dir (so no, you shouldn't run it with sudo).

---

### Post by blur xc on 2010-02-16
> **Bachstelze said:**
> In your current working dir (so no, you shouldn't run it with sudo).

Wow- that's pretty cool...

Thanks,
BM

---

### Post by nvteighen on 2010-02-17
Moreover, the best to do is:

```

mkdir some-fancy-name
cd some-fancy-name
apt-get source some-fancy-package

```

Otherwise, you'll see apt-get download several files into your current directory and that may get a bit messy.

---

### Post by s.fox on 2010-02-17
> **nvteighen said:**
> Moreover, the best to do is:

```

mkdir some-fancy-name
cd some-fancy-name
apt-get source some-fancy-package

```Otherwise, you'll see apt-get download several files into your current directory and that may get a bit messy.

I was actually just thinking that myself :D    I hate moving stuff afterwards.  Keeps it all tidy

-Silver Fox

---

