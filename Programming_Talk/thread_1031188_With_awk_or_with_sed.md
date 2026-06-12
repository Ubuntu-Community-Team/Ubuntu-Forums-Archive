---
title: "With awk or with sed"
date: 2009-01-05
forum: Programming Talk
---

### Post by davidtuti on 2009-01-05
Hi,

If I have this code:
[HTML]
<td class=lista align=left title="Bajar:&nbsp;[.AG]Las increibles aventuras de Wallace y Gromit.Dvdrip.Xvid.Mp3"><table border=0 cel
lspacing=0 cellpadding=0 align=left onClick="window.open('[B]download.php?id=f0e1d997a36bdd3cf696ea14ba7268351b66a605&f=%5B.AG%5DLas+in
creibles+aventuras+de+Wallace+y+Gromit.Dvdrip.Xvid.Mp3.torrent[/B]','_self')" style="cursor:pointer; cursor:hand;"><tr><td style="backgr
ound-image: url(images/download.gif); background-repeat: no-repeat; width:17px; height:17px;" align=center></td><td>&nbsp;Descargar<
/td></tr></table></td>[/HTML]

How could I extract the value in bold with awk or sed?

Many thanks!

---

### Post by ghostdog74 on 2009-01-05
seriously, with the advent of modern programming tools, using awk/sed to parse HTML is really not suitable. However, if you have to choose between the two, then awk is better.
Here an awk snippet, using <td> as record separator
```

awk 'BEGIN{RS="<td>"}{ gsub("<[^>]*>", "")}1' file

```

here's another way, using PHP
```


$str = <<<DATA
<td class=lista align=left title="Bajar:&nbsp;[.AG]Las increibles aventuras de Wallace y Gromit.Dvdrip.Xvid.Mp3"><table border=0 cel
lspacing=0 cellpadding=0 align=left onClick="window.open('[b]download.php?id=f0e1d997a36bdd3cf696ea14ba7268351b66a605&f=%5B.AG%5DLas+in
creibles+aventuras+de+Wallace+y+Gromit.Dvdrip.Xvid.Mp3.torrent[/b]','_self')" style="cursor:pointer; cursor:hand;"><tr><td style="backgr
ound-image: url(images/download.gif); background-repeat: no-repeat; width:17px; height:17px;" align=center></td><td>&nbsp;Descargar<
/td></tr></table></td>
DATA;

$str = strip_tags($str,"<td>");
$str = preg_split("/<td>/smi",$str);
echo $str[1];

```

---

### Post by davidtuti on 2009-01-05
> **ghostdog74 said:**
> seriously, with the advent of modern programming tools, using awk/sed to parse HTML is really not suitable. However, if you have to choose between the two, then awk is better.
Here an awk snippet, using <td> as record separator
```

awk 'BEGIN{RS="<td>"}{ gsub("<[^>]*>", "")}1' file

```



Many  thanks, I don't use PHP because I don't know, but with bash it gives me an error:

bash-2.03$ awk 'BEGIN{RS="<td>"}{ gsub("<[^>]*>", "")}1' file 
awk: syntax error near line 1
awk: illegal statement near line 1
awk: syntax error near line 1
awk: bailing out near line 1

---

### Post by ghostdog74 on 2009-01-05
> **davidtuti said:**
> Many  thanks, I don't use PHP because I don't know, but with bash it gives me an error:

bash-2.03$ awk 'BEGIN{RS="<td>"}{ gsub("<[^>]*>", "")}1' file 
awk: syntax error near line 1
awk: illegal statement near line 1
awk: syntax error near line 1
awk: bailing out near line 1

what platform are you in?

---

### Post by davidtuti on 2009-01-05
> **ghostdog74 said:**
> what platform are you in?

bash-2.03$ uname -a
SunOS tatiana2 5.8 Generic_117350-28 sun4u sparc SUNW,Ultra-80

---

### Post by ghostdog74 on 2009-01-05
use nawk on solaris
```

nawk '{ gsub("<[^>]*>", "")}1' file

```

---

