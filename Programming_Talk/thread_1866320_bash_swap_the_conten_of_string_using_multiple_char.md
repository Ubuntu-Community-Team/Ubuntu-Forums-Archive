---
title: "bash swap the conten of string using multiple character delimiter"
date: 2011-10-21
forum: Programming Talk
---

### Post by Mr.Pytagoras on 2011-10-21
hi

an example of my problem is the best way to understand what i can't figure out :)

I have a string for example str
```

str="something1 next_colum something2"

```

And I want to take the "next_colum" substring to be my delimiter and swap the "something1" with the "something2" and after that replace the "next_colum" with for example ">>>" characters 

I was thinking maybe awk would do it however so far I haven't been able to achive anything. So I am asking you for your help

Thanks

---

### Post by ofnuts on 2011-10-21
> **Mr.Pytagoras said:**
> hi

an example of my problem is the best way to understand what i can't figure out :)

I have a string for example str
```

str="something1 next_colum something2"

```And I want to take the "next_colum" substring to be my delimiter and swap the "something1" with the "something2" and after that replace the "next_colum" with for example ">>>" characters 

I was thinking maybe awk would do it however so far I haven't been able to achive anything. So I am asking you for your help

Thanks
Something like

```

sed -e 's/\(.*\)__\(.*\)/\2++\1/'

```
(where "__" and "++" can be replaced by the required delimiters)

---

### Post by Mr.Pytagoras on 2011-10-21
thanks

I have figured it out using awk

But thanks for you help, my awk solution is on 3 lines so your solution is better i guess :)

---

### Post by Vaphell on 2011-10-21
seriously?
```
$ echo something1 next_colum something2 | awk 'BEGIN { FS=" next_colum "; OFS=" >>> " }; { print $2, $1 }'
something2 >>> something1
```

---

### Post by ofnuts on 2011-10-21
> **Mr.Pytagoras said:**
> thanks

I have figured it out using awk

But thanks for you help, my awk solution is on 3 lines so your solution is better i guess :)
I don't know much awk, but there could be  a one-liner in awk too. All these regexp-based programs are very similar.

---

