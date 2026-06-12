---
title: "rsync script to rewrite suffix - BASH, awk, sed, perl?"
date: 2013-03-20
forum: Programming Talk
---

### Post by alienprdkt on 2013-03-20
[COLOR=#000000][FONT=Arial]trying to write up a script to put the suffix back.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]heres what I have but can't get it to do anything :([/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]would like it to be name.date.suffix[/FONT][/COLOR]

```
[COLOR=#333333]    rsync [/COLOR][COLOR=#888888]-[/COLOR][COLOR=#333333]zrlpoDtub [/COLOR][COLOR=#888888]--[/COLOR][COLOR=#333333]suffix[/COLOR][COLOR=#888888]=[/COLOR][COLOR=#4E0000]".`date +%Y%m%d%k%M%S`.~"[/COLOR][COLOR=#888888]--[/COLOR][COLOR=#333333]bwlimit[/COLOR][COLOR=#888888]=[/COLOR][COLOR=#4E0000]1024[/COLOR][COLOR=#888888]/[/COLOR][COLOR=#333333]mymounts[/COLOR][COLOR=#888888]/[/COLOR][COLOR=#333333]test1[/COLOR][COLOR=#4E0000]/ /[/COLOR][COLOR=#333333]mymounts[/COLOR][COLOR=#888888]/[/COLOR][COLOR=#333333]test2[/COLOR][COLOR=#888888]/[/COLOR]
``````
[COLOR=#0C2D53]while[/COLOR][COLOR=#333333] IFS[/COLOR][COLOR=#888888]=.[/COLOR][COLOR=#333333] read [/COLOR][COLOR=#888888]-[/COLOR][COLOR=#333333]r [/COLOR][COLOR=#888888]-[/COLOR][COLOR=#333333]u [/COLOR][COLOR=#4E0000]9[/COLOR][COLOR=#888888]-[/COLOR][COLOR=#333333]d [/COLOR][COLOR=#4E0000]''[/COLOR][COLOR=#333333] name suffix date tilde[/COLOR][COLOR=#0C2D53]do[/COLOR][COLOR=#333333]    mv [/COLOR][COLOR=#4E0000]"${name}.${suffix}.${date}.~"[/COLOR][COLOR=#4E0000]"${name}.${date}.${suffix}"[/COLOR][COLOR=#0C2D53]done[/COLOR][COLOR=#4E0000]9[/COLOR][COLOR=#888888]<[/COLOR][COLOR=#888888]<([/COLOR][COLOR=#333333]find [/COLOR][COLOR=#888888].[/COLOR][COLOR=#888888]-[/COLOR][COLOR=#333333]type f [/COLOR][COLOR=#888888]-[/COLOR][COLOR=#333333]name [/COLOR][COLOR=#4E0000]"*.~"[/COLOR][COLOR=#888888]-[/COLOR][COLOR=#333333]print0[/COLOR][COLOR=#888888])[/COLOR]
```[COLOR=#333333]```
    rsync 
```[/COLOR]```
[COLOR=#888888]-[/COLOR][COLOR=#333333]zrlpoDtub [/COLOR][COLOR=#888888]--[/COLOR][COLOR=#333333]suffix[/COLOR][COLOR=#888888]=[/COLOR][COLOR=#4E0000]".`date +%Y%m%d%k%M%S`.~"[/COLOR][COLOR=#888888]--[/COLOR][COLOR=#333333]bwlimit[/COLOR][COLOR=#888888]=[/COLOR][COLOR=#4E0000]1024[/COLOR][COLOR=#888888]/[/COLOR][COLOR=#333333]mymounts[/COLOR][COLOR=#888888]/[/COLOR][COLOR=#333333]test2[/COLOR][COLOR=#4E0000]/ /[/COLOR][COLOR=#333333]mymounts[/COLOR][COLOR=#888888]/[/COLOR][COLOR=#333333]test1[/COLOR][COLOR=#888888]/[/COLOR]
``````
[COLOR=#0C2D53]while[/COLOR][COLOR=#333333] IFS[/COLOR][COLOR=#888888]=.[/COLOR][COLOR=#333333] read [/COLOR][COLOR=#888888]-[/COLOR][COLOR=#333333]r [/COLOR][COLOR=#888888]-[/COLOR][COLOR=#333333]u [/COLOR][COLOR=#4E0000]9[/COLOR][COLOR=#888888]-[/COLOR][COLOR=#333333]d [/COLOR][COLOR=#4E0000]''[/COLOR][COLOR=#333333] name suffix date tilde[/COLOR][COLOR=#0C2D53]do[/COLOR][COLOR=#333333]    mv [/COLOR][COLOR=#4E0000]"${name}.${suffix}.${date}.~"[/COLOR][COLOR=#4E0000]"${name}.${date}.${suffix}"[/COLOR][COLOR=#0C2D53]done[/COLOR][COLOR=#4E0000]9[/COLOR][COLOR=#888888]<[/COLOR][COLOR=#888888]<([/COLOR][COLOR=#333333]find [/COLOR][COLOR=#888888].[/COLOR][COLOR=#888888]-[/COLOR][COLOR=#333333]type f [/COLOR][COLOR=#888888]-[/COLOR][COLOR=#333333]name [/COLOR][COLOR=#4E0000]"*.~"[/COLOR][COLOR=#888888]-[/COLOR][COLOR=#333333]print0[/COLOR][COLOR=#888888])[/COLOR]
```[FONT=Arial]still not rewriting as I would like, got file renamed as "test1.txt.20130320 95325.~"[/FONT]
[FONT=Arial]Thanks in advance,[/FONT]

---

### Post by papibe on 2013-03-20
Hi alienprdkt.

There are several syntax errors on your commands (lines split, commands joined together).

My guess is it was a copy/paste problem.

Could you edit your post so we can take a look at your actual scripts?

Kind Regards.

---

### Post by schragge on 2013-03-21
Besides the copy-paste problem, there's another: your code presumes that files have only one suffix. How would you handle *file.tar.gz*? Also note that since the *find* is executed on the current directory (.), it will prepend *./* to each file name and the first variable you're reading into ($name) will be assigned empty value.

Try
```
find -type -f -name '.*.*.~' -exec rename -v[COLOR=red]n[/COLOR] 's:(\.[^./]+)(\.[^./]+)\.~$:$2$1:' {} +
```
[COLOR=#ff0000]n[/COLOR] is there for testing purposes. When you're sure the command does what you want, remove [COLOR=#ff0000]n[/COLOR] and rerun the command to do the actual renaming.

BTW, why would you use space-padded hours (%k) in the date format expression?

---

