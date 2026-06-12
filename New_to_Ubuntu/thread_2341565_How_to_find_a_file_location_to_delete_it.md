---
title: "How to find a file location to delete it"
date: 2016-10-29
forum: New to Ubuntu
---

### Post by tonma on 2016-10-29
I've seen many suggestions on how to search a file on the entire system, including find or locate, but none seems to find my specific file that I'm looking for: composer.phar

I've installed composer and now I want to completely remove it and everything it installed. I saw that composer is just a binary file that I can delete (instead of sudo apt purge composer and then sudo apt autoremove < I did that, but just want to try the other method)

---

### Post by mikewhatever on 2016-10-29
Really not sure what other method. Aren't find and locate good enough?

---

### Post by leunam12 on 2016-10-29
If find doesn't find it then there must be a syntax error.
```
sudo find / -iname *composer*
```
If that doesn't find it then the file does not exist or has a different name.

---

### Post by vasa1 on 2016-10-29
And how exactly and from where did you install "composer"? Sudo apt-get purge is the recommended way to uninstall software installed from the repos. It will automatically handle dependencies. Why do you want to try some "other method" whatever that is?

---

### Post by oldos2er on 2016-10-29
> **leunam12 said:**
> If find doesn't find it then there must be a syntax error.
```
sudo find / -iname *composer*
```
If that doesn't find it then the file does not exist or has a different name.

+1

And just to be certain I would run ```
sudo updatedb
``` first.

---

### Post by steeldriver on 2016-10-29
I wouldn't recommend running any [FONT=courier new]find[/FONT] command with a bare glob such as [FONT=courier new]*command*[/FONT] - always best to surround search terms in quotes, else the shell will try to expand it to any matching files in the current directory - which may have unexpected results.

Also probably best to skip troublesome filesystems such as /proc and /sys when searching from /

```

sudo find / \( -path /dev -o -path /proc -o -path /run -o -path /sys \) -prune -o -iname '*composer*'

```

AFAIK running  [FONT=courier new]updatedb [/FONT]would only   (potentially) affect the results of [FONT=courier new]locate [/FONT]- not those of [FONT=courier new]find [/FONT]

---

### Post by kevdog on 2016-10-29
Honestly make use of your package manager man.  Use apt to remove it.  Don't make things difficult.

---

