---
title: "Problem with if and integer"
date: 2012-03-03
forum: Programming Talk
---

### Post by ryanrio95 on 2012-03-03
Code:
```
if [ du -s resources | sed 's/\tresources//g' < "720000" ]; then
echo "Directory is smaller then 720 MB "
fi
```

Output:
```
bash: [: missing `]'
bash: 720000: No such file or directory
```

This isn't working, who can help me?

Regards

---

### Post by MadCow108 on 2012-03-03
you must put the commands into backticks so they are executed and the output inserted in this spot:
if```
 [ `du -s resources | sed 's/\tresources//g'` -lt 720000 ]; then
echo "Directory is smaller then 720 MB "
fi
```
for integer comparison you should use -eq -lt -gt -le -ge etc, see man test

---

### Post by Vaphell on 2012-03-03
if you use bash you can use (( )) to switch to integer arithmetic mode

```
if (( $(du -s resources | cut -f1) < 720000 )); then ...; fi
```

backticks are deprecated and $( ) should be used instead.

---

### Post by Khayyam on 2012-03-03
el al ...

```
du -s resources | awk '{if($1<720000) {print "Directory is smaller than 720MB"}}'
```


Vaphell's suggestion of using bash to evaluate the expression is probably more what your looking for ... 
 
HTH ... khay

---

### Post by MadCow108 on 2012-03-03
> **Vaphell said:**
> 
backticks are deprecated and $( ) should be used instead.

citation needed.

to my knowledge backticks are more portable.

---

### Post by matt_symes on 2012-03-03
Hi

> **MadCow108 said:**
> citation needed.

to my knowledge backticks are more portable.

I think command substution using $( ) is part of the POSIX standard, whereas using backticks was the previous standard.

[manuals.ts.fujitsu.com/file/8867/posix_k.pdf](manuals.ts.fujitsu.com/file/8867/posix_k.pdf)

Backticks are more portable but trying to read them... :)

Kind regards

---

### Post by Khayyam on 2012-03-03
> **MadCow108 said:**
> citation needed. to my knowledge backticks are more portable.

I think the only instance in which backticks will prove more 'portable' is if the target is an old bourne shell, most machines 'sh' will either be bash or dash. I don't think there will be any calculable chance of running into trouble with $().

Anyhow, the [Bash FAQ has this to say about backticks](http://mywiki.wooledge.org/BashFAQ/082).

best ... khay

---

### Post by MadCow108 on 2012-03-03
> **Khayyam said:**
> I don't think there will be any calculable chance of running into trouble with $().

famous last words.

but I agree $() are preferable to the ugly backticks if you don't care about legacy systems.

---

### Post by Khayyam on 2012-03-03
> **MadCow108 said:**
> famous last words.

Ya well, better than, "*kiss me Hardy*" :)

> **MadCow108 said:**
> but I agree $() are preferable to the ugly backticks if you don't care about legacy systems.

Those things exist (ummm ... like =< Solaris 10), but we should remember that bourne shell had the "^" (caret) for "|" adopted from the Thompson shell, and that too was depreciated. So "legacy" has some timelimit, besides the target here is not legacy but a modern posix complient OS.

best ... khay

---

### Post by ryanrio95 on 2012-03-04
i go for the way madcow108 said.

thanks for helping me.

regarrds

---

### Post by Khayyam on 2012-03-04
> **ryanrio95 said:**
> i go for the way madcow108 said. thanks for helping me.

I dunno .. even if you **must** use backticks rather than brace expansion vaphell's solution does seem to me the most proper ..

```
if (( $(du -s resources | cut -f1) < 720000 )); then
    echo "Directory is smaller than 720MB"
fi
```

Anyhow, each to their own I guess.

best ... khay

---

### Post by matt_symes on 2012-03-04
Hi

Backticks ? Honesty, i don't use them. What shell and version are you targeting ?

Kind regards

---

