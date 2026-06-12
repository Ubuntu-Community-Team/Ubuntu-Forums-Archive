---
title: "Complete Terminal Command List"
date: 2012-07-06
forum: New to Ubuntu
---

### Post by Febri Ichsan on 2012-07-06
Can anybody gimme some pdf of complete terminal command list if there's any.
thanks before.

---

### Post by krustenBrot on 2012-07-06
You can find a lot command line resources in the wiki:  [https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

Hope that helps. :)

---

### Post by dargaud on 2012-07-06
Giving a 'complete' list of commands is impossible because it depends on what is installed on your system. The nearest would be:
```
$ ls /bin /sbin /usr/bin /usr/sbin
```

---

### Post by MG&amp;TL on 2012-07-06
> **Febri Ichsan said:**
> Can anybody gimme some pdf of complete terminal command list if there's any.
thanks before.

There has to be thousands of them, bearing in mind you can install lots of other ones not included in Ubuntu.

For a list of all programs you can currently run:

```
 paths=$(echo $PATH | tr ':' '\n') && for path in $paths; do ls $path; done
```You'll want to do some research before you run any of them though. Try

```
man <command>
```or 

```
<command> --help
```

---

### Post by Febri Ichsan on 2012-07-06
@dargaud : whooaa, what a list, anyway, is there any meaning on the color of the list? coz it's so colorful, i have no idea, what the meaning of the color is.
thousands of thanks bro...

---

### Post by MG&amp;TL on 2012-07-06
> **Febri Ichsan said:**
> @dargaud : whooaa, what a list, anyway, is there any meaning on the color of the list? coz it's so colorful, i have no idea, what the meaning of the color is.
thousands of thanks bro...

Yes, that's the colour feature of the ls command. A couple come to mind:

green-executables (programs).
blue - links to files (probably programs).
red-broken links (what they point to doesn't exist any more.

---

