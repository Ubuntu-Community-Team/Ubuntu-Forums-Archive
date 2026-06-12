---
title: "SED from a shell script - driving me up the wall!!!"
date: 2013-06-19
forum: Programming Talk
---

### Post by cbillson on 2013-06-19
why does this work

sed -e 's/.*Jun 19//' myfile

And this not

mmm=Jun
dd=19
sed -e 's/.*$mmm $dd//' myfile


both being ran from a shell scrip, not CLI

myfile:[INDENT]< Jun 19 00:00:00 some data
[/INDENT]


I've tried quotes round it, no joy, i'm using *. as i'd like to lose the < too.

---

### Post by steeldriver on 2013-06-19
It's nothing to do with sed specifically - single quotes prevent expansion of shell variables, try double quotes instead

```
sed -e [COLOR=#0000ff]**"**[/COLOR]s/.*$mmm $dd//[COLOR=#0000ff]**"**[/COLOR] myfile
```

Be aware that this *can* allow the shell to expand things you *don't* want it to in certain circumstances

---

### Post by SeijiSensei on 2013-06-19
Because you are using single quotes. That tells bash to treat the quoted string as a literal. Try using double quotes (") instead. Then bash will replace the variables with their values.

---

### Post by cbillson on 2013-06-19
ahh, thank-you very much - you learn something new every day..

---

