---
title: "How to retrieve size of software(package) in ubuntu?"
date: 2015-05-31
forum: Programming Talk
---

### Post by wisdom2 on 2015-05-31
Hello, by using pyton-apt i find package's sizes, but it gives wrong results i think. FOr example, for package named eclipse, size is shown in ubuntu software center as shown below :
240,8 MB to download, 316,9 MB when installed

However, by using python apt, i take the following results : 
>  pkg = cache["eclipse"]
>  vrs=pkg.versions
>  vrs[0].size
>  1406L
>  vrs[0].installed_size
>  29696L

As you see, results are completely different.
Why resuts are different, how can i know software's size?

Thanks in advance.

---

### Post by papibe on 2015-05-31
Hi wisdom2.

Probably the Software Center is reporting the same as apt-get on the command line, which includes all dependencies.

If you run this you'll see that installing eclipse would install lots of more packages that are prerequisites for eclipse:
```
sudo apt-get --assume-no install eclipse
```
Does that help?
Regards.

---

### Post by flaymond on 2015-06-01
Hi wisdom2, can you make a thread that simply got all of your related questions (eg. retrieving from backport, data, pictures) and post it to the public in one go? It doesn't seem this forum 'clean' when you found a section that full with almost same topic on every sub-sections. Just saying. Cheers! :D

---

