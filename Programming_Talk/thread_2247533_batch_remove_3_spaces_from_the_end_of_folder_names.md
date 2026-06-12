---
title: "batch remove 3 spaces from the end of folder names?"
date: 2014-10-08
forum: Programming Talk
---

### Post by sohlinux on 2014-10-08
Hello, how can I batch remove 3 spaces from the end of all folder names including sub folders?

thanks

---

### Post by varunendra on 2014-10-09
I guess you must run something like this -
```
find ***[COLOR="#0000FF"]<target directory>/[/COLOR]*** -type d -iname "*[[:graph:]]   " -exec rename 's/   $//' "{}" \;
```
..multiple times until you get no more errors about 'no such file or directory'. Unless of course we can turn the above into a much more smart script that can perform the operation recursively from the maximum depth to the root of the target directory.

Or maybe some smart expression formula in GUI tools like 'Krename' can do the job. I tried its "Find and Replace" function and it ran into same error where it couldn't find the subdirectories because the name of their parent directory was changed.

---

### Post by ofnuts on 2014-10-09
> **varunendra said:**
> I guess you must run something like this -
```
find ***[COLOR=#0000FF]<target directory>/[/COLOR]*** -type d -iname "*[[:graph:]]   " -exec rename 's/   $//' "{}" \;
```
..multiple times until you get no more errors about 'no such file or directory'. Unless of course we can turn the above into a much more smart script that can perform the operation recursively from the maximum depth to the root of the target directory.

Or maybe some smart expression formula in GUI tools like 'Krename' can do the job. I tried its "Find and Replace" function and it ran into same error where it couldn't find the subdirectories because the name of their parent directory was changed.

No time to come up with actual code, but getting the list of affected directories, sorting it in reverse (which will put the children first) and then applying rename to the result could work)(will require -print0, among other things)

---

### Post by sohlinux on 2014-10-09
thanks guys, ill test that :)

---

### Post by Vaphell on 2014-10-09
no need to rerun or sort, *find -depth -exec* to the rescue. It will go subdirs first, parents last.

---

### Post by ofnuts on 2014-10-09
> **Vaphell said:**
> no need to rerun or sort, *find -depth -exec* to the rescue. It will go subdirs first, parents last.

Good to know :)

---

### Post by varunendra on 2014-10-09
> **Vaphell said:**
> no need to rerun or sort, *find **[COLOR="#0000FF"]-depth[/COLOR]** -exec* to the rescue. It will go subdirs first, parents last.

Wow! The manpages are amazing, and so is ignorance!! Of the hundred times of having looked at the manpage of find, I never noticed the '-depth' option itself, let alone what it does and how. :-\"

Thanks for handing us the precious gem from our left pocket into our right hands! :p

---

