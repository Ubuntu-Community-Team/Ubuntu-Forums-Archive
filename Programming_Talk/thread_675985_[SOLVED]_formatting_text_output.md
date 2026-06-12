---
title: "[SOLVED] formatting text output"
date: 2008-01-23
forum: Programming Talk
---

### Post by sagarhshah on 2008-01-23
Hi,

I am working on a little script that does a little bit of processing on a text file.

I get a bit of output which I have to put in a suitable format.

At the moment I am formatting the output in this style
echo $1" "$2" "$3" "$4

At the moment I get this:
Nov 20 14:13:11 200.xx.114.131
Nov 18 18:55:06 6x.x2.248.243
Nov 17 19:26:43 200.xx.72.129
Nov 17 10:57:11 2xx.71.188.192
Nov 17 10:57:11 2xx.71.188.192
Nov 17 10:57:11 2xx.71.188.192
Nov 11 16:37:29 6x.x44.180.27
Nov 11 16:37:29 6x.x44.180.27
Nov 11 16:37:24 6x.x44.180.27
Nov 5 18:56:00 212.xx.13.130
Nov 5 18:56:00 212.xx.13.130
Nov 5 18:56:00 212.xx.13.130
Nov 3 01:52:31 2xx.54.67.197
Nov 3 01:52:01 2xx.54.67.197
Nov 3 01:52:00 2xx.54.67.197
Oct 31 16:11:17 xx.192.39.131
Oct 31 16:11:17 xx.192.39.131
Oct 31 16:11:17 xx.192.39.131
Oct 31 16:10:51 xx.192.39.131
Oct 31 16:10:51 xx.192.39.131
Oct 31 16:10:51 xx.192.39.131

As you can see the output doesnt line up properly because some dates have single numbers e.g. Nov 5 and others have double letters.

Is there anyway I can use tabs to format the output instead of using blanks
so that everything lines up properly

---

### Post by sagarhshah on 2008-01-23
never mind

just figured it out

I need to use

echo $1"\t"$2"\t"$3"\t"$4

and that did the trick

---

