---
title: "Shell scripting: `env` command"
date: 2006-12-31
forum: Programming Talk
---

### Post by cosmolee on 2006-12-31
Edgy 6.10

I'm not getting this `env` command, specifically with the "-i" option.  Running with "-i" supposedly "ignores the inherited environment completely and uses only the supplied variables and values"  and causes it to "start with an empty environment".  

So, "env -i echo howdy" shouldn't run, cuz I didn't indicate a PATH.  Yet:

$ env -i echo howdy
howdy
$ 


Also:

$ echo $HOME $LC_ALL
/home/cosmo C
$ env -i HOME=/NEW/PATHNAME LC_ALL=XYZ echo $HOME $LC_ALL
/home/cosmo C
$

Shouldn't echo have been passed the new values for HOME & LC_ALL??  I was expecting "/NEW/PATHNAME XYZ"  to be output - do I misunderstand something?


Yet this doesn't run (as expected) cuz PATH is bad:

$ env -i PATH=/dev/null echo howdy
env: echo: No such file or directory
$ 

Any clues?  :-k

---

### Post by HadroLepton on 2006-12-31
your problem is because the shell replaces the $variables BEFORE it gives the command to env

this line
```
$ env -i HOME=/NEW/PATHNAME LC_ALL=XYZ echo $HOME $LC_ALL
```
is first interpreted by the shell to
```
$ env -i HOME=/NEW/PATHNAME LC_ALL=XYZ echo /home/cosmo C
```
and then env is executed

unfortunately i don't know how to pass the $variables to env
when i try to hide the $ from bash it seems to also hide from env
```

$ env -i echo \$HOME
$HOME
$ env -i echo '$HOME'
$HOME

```

but i found a workaround, you can put this line in a small helper script
```
echo $HOME $LC_ALL
```
and then execute that script using env
```
$ env -i HOME=/NEW/PATHNAME LC_ALL=XYZ helperscript.sh
```

---

