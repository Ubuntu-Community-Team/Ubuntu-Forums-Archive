---
title: "A wtf ..."
date: 2009-03-22
forum: Programming Talk
---

### Post by slavik on 2009-03-22
The following is true and actually happened, multiple times ... (it was in cron set to run monthly)

script goes as follows:

```

cd /dir1/dir2
wget http://somesite.com/tarball.tar
tar xf tarball.tar
cd *
cd dir3
command somefile
command another_file
cd ..
cd ..
rm -rf *

```

---

### Post by ghostdog74 on 2009-03-22
and the problem is the rm -rf * ?

---

### Post by linuxisevolution on 2009-03-22
> **slavik said:**
> The following is true and actually happened, multiple times ... (it was in cron set to run monthly)

script goes as follows:

```

cd /dir1/dir2
wget http://somesite.com/tarball.tar
tar xf tarball.tar
cd *
cd dir3
command somefile
command another_file
cd ..
cd ..
rm -rf *

```

I was like wtf too until I saw the last line... lmao made my day :)

---

### Post by jimi_hendrix on 2009-03-22
you told me the guy who wrote that was a grad from some great school too right :)

---

### Post by slavik on 2009-03-23
well, there were a couple of "great school e-mails in there" (new york area).

btw, the rm -rf * by itself is not a problem ... the problem appears earlier.

---

### Post by DocForbin on 2009-03-23
what is cd * supposed to do, go to the first directory I guess?

---

### Post by samjh on 2009-03-23
> **DocForbin said:**
> what is cd * supposed to do, go to the first directory I guess?

Yup.

I'm guessing the "tar xf" is the WTF line (note the lack of "-" for the parameters).

---

### Post by tneva82 on 2009-03-23
> **samjh said:**
> Yup.

I'm guessing the "tar xf" is the WTF line (note the lack of "-" for the parameters).

What is that supposed to do? Created temp directory and copied tar file there and tried it. It unpacked without issues. Why should that be WTF line?

---

### Post by Xiong Chiamiov on 2009-03-23
> **samjh said:**
> Yup.

I'm guessing the "tar xf" is the WTF line (note the lack of "-" for the parameters).
You don't need - for flags with tar, for some odd reason.  In fact, I almost always see it without.

---

### Post by sujoy on 2009-03-23
lol @
```

cd ..
cd ..

```

why couldn't he just do a cd ../.. ? or pass the path to rm?

---

### Post by samjh on 2009-03-23
> **tneva82 said:**
> What is that supposed to do? Created temp directory and copied tar file there and tried it. It unpacked without issues. Why should that be WTF line?

> **Xiong Chiamiov said:**
> You don't need - for flags with tar, for some odd reason.  In fact, I almost always see it without.

Oh well, scrap it. :p

---

### Post by Simian Man on 2009-03-23
The WTF is it downloads and unpacks a tarball, then runs a few commands only to delete the whole thing moments later.  You guys can't see the forest for the trees :).

---

