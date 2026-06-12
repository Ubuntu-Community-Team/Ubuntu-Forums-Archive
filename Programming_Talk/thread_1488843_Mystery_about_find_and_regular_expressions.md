---
title: "Mystery about find and regular expressions"
date: 2010-05-20
forum: Programming Talk
---

### Post by denarced on 2010-05-20
Now, as I understand the following two commands should be exactly equal
```

find . -regex '.*[A-Z].*'
find . -regex '.*[ABCDEFGHIJKLMNOPQRSTUVWXYZ].*'

```
But they are not. First I just noticed that I wasn't getting the result I wanted and then I piped the result to wc and it was confirmed: not equal.

Why ?

---

### Post by uOpt on 2010-05-20
```

find . -regex '.*[A-Z].*' > l1
find . -regex '.*[ABCDEFGHIJKLMNOPQRSTUVWXYZ].*' | diff l1 -

```

---

### Post by denarced on 2010-05-25
> **uOpt said:**
> ```

find . -regex '.*[A-Z].*' > l1
find . -regex '.*[ABCDEFGHIJKLMNOPQRSTUVWXYZ].*' | diff l1 -

```

Yes, different results.
Anyone know why ?

---

### Post by denarced on 2010-05-25
Here's an even more thorough look into this:
```

denarced@narbuntu:~/f/Desktop/testdir$ ls -a
.  ..  abc  ABC
denarced@narbuntu:~/f/Desktop/testdir$ find . -maxdepth 1 -regextype posix-extended -regex '.*[A-Z]'
./ABC
./abc
denarced@narbuntu:~/f/Desktop/testdir$ find . -maxdepth 1 -regextype posix-egrep -regex '.*[A-Z]'
./ABC
./abc
denarced@narbuntu:~/f/Desktop/testdir$ find . -maxdepth 1 -regextype posix-basic -regex '.*[A-Z]'
./ABC
./abc
denarced@narbuntu:~/f/Desktop/testdir$ find . -maxdepth 1 -regextype posix-awk -regex '.*[A-Z]'
./ABC
./abc
denarced@narbuntu:~/f/Desktop/testdir$ find . -maxdepth 1 -regex '.*[A-Z]'./ABC
./abc


```
To my mind, none of these work properly or I'm really missing something

---

### Post by trent.josephsen on 2010-05-25
You're right, that doesn't seem right.  However I'm on Gentoo right now and it works as I would expect.  Can't test it on Ubuntu.  If anyone can verify this you will want to submit a bug report.  It seems a pretty significant bug -- I'd be surprised if it slipped through the cracks, but I suppose it does happen every once in a while.

---

### Post by uOpt on 2010-05-25
> **denarced said:**
> Yes, different results.
Anyone know why ?

Why don't you post the different results you get?

---

### Post by denarced on 2010-05-25
> **uOpt said:**
> Why don't you post the different results you get?

Here we go.
```

denarced@narbuntu:~/f/Desktop/testdit$ ls -a
.  ..  abcd  abCd  AbcD  ABcd  ahtmlb  axmlb
denarced@narbuntu:~/f/Desktop/testdit$ find . -regex '.*[A-Z].*'
./axmlb
./abCd
./ahtmlb
./ABcd
./abcd
./AbcD
denarced@narbuntu:~/f/Desktop/testdit$ find . -regex '.*[ABCDEFGHIJKLMNOPQRSTUVWXYZ].*'
./abCd
./ABcd
./AbcD


```
In other words (unless I'm missing something), listing the all the alphabets works and the other one( [A-Z] ) doesn't.
Unless I ****ed up ( much possible ).

---

### Post by uOpt on 2010-05-25
Looks like Ubuntu brokenness. Works fine on Debian/stable.

---

### Post by denarced on 2010-05-25
Can someone else using Ubuntu(9.04-10.04) verify this behavior so I'll know that it's not just my system doing this..

---

### Post by stylishpants on 2010-05-25
I confirm identical results on both Ubuntu 10.04 and SLES 10 SP1:
```
bob@cob:~/test$ find . -regex '.*[ABCDEFGHIJKLMNOPQRSTUVWXYZ].*'
./AbcD
./ABcd
./abCd

bob@cob:~/test$ find . -regex '.*[A-Z].*'
./ahtmlb
./AbcD
./ABcd
./axmlb
./abCd
./abcd

bob@cob:~/test$ dpkg -l findutils
ii  findutils                                      4.4.2-1ubuntu1 
               
```

```
190-29:~ # cat /etc/issue

Welcome to SUSE Linux Enterprise Server 10 SP1 (i586) - Kernel \r (\l).

190-29:~ # rpm -q findutils
findutils-4.2.27-14.10

```

190-29:~ # 


I also tested on Debian SID and can confirm that it's not present there:
```
bob@sid:~/test$ find . -regex '.*[ABCDEFGHIJKLMNOPQRSTUVWXYZ].*'
./abCd
./AbcD
./ABcd

bob@sid:~/test$ find . -regex '.*[A-Z].*'
./abCd
./AbcD
./ABcd

bob@sid:~/test$ dpkg -l findutils
ii  findutils                        4.4.0-2                          

```

---

### Post by geirha on 2010-05-25
[A-Z] is not necessarily the ascii characters A to Z, it is locale dependant, and may match both upper and lower case characters and non-ascii alphabet characters depending on which locale you are using.

Try: ```
LANG=C find . -regex '.*[A-Z].*'
```

---

### Post by denarced on 2010-05-25
> **geirha said:**
> [A-Z] is not necessarily the ascii characters A to Z, it is locale dependant, and may match both upper and lower case characters and non-ascii alphabet characters depending on which locale you are using.

Try: ```
LANG=C find . -regex '.*[A-Z].*'
```

This is the answer. Now I get the correct result.
I had the default, LANG=en_US.UTF-8.

---

### Post by denarced on 2010-05-25
Althou, usually in Unicode and also in UTF-8, the basic ascii characters are still valid so A-Z (41-5a) is still ABCDEFGHIJKLMNOPQRSTUVWXYZ

I wonder why it's not in this case also ..
And furthermore, how would I find out the characters between A and Z ?

---

### Post by geirha on 2010-05-25
Well, in POSIX/C locale, «A B C» are ordered before «a b c», but in some locales they are ordered like «Aa Bb Cc» etc. And then A-Z will encompass both the uppercase and the lowercase letters. You'll see this by sorting

```
echo $'a\nb\nA\nB' | LC_COLLATE=en_US.UTF-8 sort
# vs
echo $'a\nb\nA\nB' | LC_COLLATE=C sort

```
So, if you want to match only the ascii uppercase letters, make sure to use LC_COLLATE=C (or LANG=C or LC_ALL=C). If you want uppercase letters, including locale specific uppercase letters, use [:upper:] instead of A-Z.

[http://opengroup.org/onlinepubs/007908775/xbd/locale.html](http://opengroup.org/onlinepubs/007908775/xbd/locale.html)

---

