---
title: "Strange html page"
date: 2008-11-04
forum: Programming Talk
---

### Post by Nonno Bassotto on 2008-11-04
Not sure where to put a html question... I'm trying to customize Konqueror start page for a live cd I am creating. It seems that the default page is located under
```

/usr/share/apps/konqueror/about/launch.html

```
The problem is that I don't understand how to edit that page since each content is replaced by a %1
For example you have
```

<td valign="bottom">
<a href="%1">
<img src="%1" height="%1" width="%1" /></a>
</td>
<td valign="bottom">
<a href="%1">%1</a>
<br>
<span id="subtext"><nobr>%1</span>
</td>

```
and so on.

What do all these %1 mean? I don't want to rewrite the whole page, because it has to look like the standard one, just with a couple of links changed.

---

