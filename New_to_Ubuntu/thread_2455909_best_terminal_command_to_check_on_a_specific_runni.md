---
title: "best terminal command to check on a specific running process"
date: 2020-12-30
forum: New to Ubuntu
---

### Post by rburkartjo on 2020-12-30
running 20.04
how to check o this process running in terminal
maldet --scan-all / 
tks

---

### Post by The Cog on 2020-12-30
```
pgrep -af maldet
```
will show you if it's running. Is that what you're after?

---

### Post by TheFu on 2020-12-30
I have an alias:
```
alias psg='ps -eaf | grep $*'
```
or if you don't want to see the grep in the output:
```
alias psg='ps -eaf | grep $* | egrep -v grep'
```

Use:
```
$ psg maldet
```

If running at least, 2 lines should be returned. If only 1, then that will probably the the 'grep' from the alias.

It doesn't display the headers, which some people might really want. That makes for a more complex alias.

---

### Post by rburkartjo on 2020-12-30
tks guys just messing around and trying to keep my sanity during covid

---

