---
title: "Use a variable within quotation marks: &quot;$variable&quot;"
date: 2012-09-09
forum: Programming Talk
---

### Post by ugm6hr on 2012-09-09
I'm writing a simple (-ish) bash script to automate variant annotation for genetic sequencing data.

I need to put a variable within quotation marks - see below.

```

gatkname=$vcfname".gatk"
gatktable="g"$vcfname

vtools select variant --samples 'sample_name="[COLOR="red"]$gatkname[/COLOR]"' -t $gatktable

```

Just to confirm, the entries work when done manually:
```
vtools select variant --samples 'sample_name = "20AA02205.gatk"' -t g20AA02205
```

I can't find any way for the variable to be recognised as text within quotation marks. I'm sure this must be easy - but googling hasn't helped.

---

### Post by Bachstelze on 2012-09-09
Single quotes mean everything in-between is interpreted literally:

```
bash-3.2$ foo=bar
bash-3.2$ echo '$foo'
$foo
bash-3.2$ echo "$foo"
bar
```


You want

```
vtools select variant --samples "sample_name=\"$gatkname\"" -t $gatktable
```

---

### Post by ugm6hr on 2012-09-09
Thanks.
I knew it was simple. I was confused by the difference between ' and "
Seems obvious now.
I'm just about to run my script... Will be a few hours before I get results - but at least I'm on track.

---

### Post by MadCow108 on 2012-09-09
you can also escape the $:
```
echo "\$foo"
```

---

### Post by Habitual on 2012-09-09
[http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html) 
[http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html) 
[http://www.gnu.org/software/bash/manual/html_node/index.html](http://www.gnu.org/software/bash/manual/html_node/index.html)
[http://www.grymoire.com/Unix/Sh.html](http://www.grymoire.com/Unix/Sh.html)
[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/) 
[http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ)
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)

---

