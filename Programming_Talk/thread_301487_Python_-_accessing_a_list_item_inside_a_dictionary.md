---
title: "Python - accessing a list item inside a dictionary"
date: 2006-11-17
forum: Programming Talk
---

### Post by ironfistchamp on 2006-11-17
Hey all

I am a little confused. I assume I can have a list inside of a dictionary. If this is true how can access a certain item in the list. For example

```


#first I create an empty dicitonary
thisdict = {}

#later I add in some values

thisdict["firstval"] = "1stval"
thisdict["secondval"] = ["2ndval", "3rdval"] #some values in the list

#later access the list item with the index of 1 (here is the prob)

theval = thisdict["secondval(1)"]

```

That isn't the right way to do it but I hope it illustrates what I want. Does anyone know how I can do it?

Thanks

Ironfistchamp

---

### Post by gareththegeek on 2006-11-17
You wanna do it this way I think

theval = thisdict["secondval"][1]

thisdict["secondval"] gives you access to the array
and then afterwards you ask for the 1th element of it.

HTH
G!

---

### Post by ghostdog74 on 2006-11-17
you ask for it like this:
```

...
firstval = thisdict["secondval"][0] #get first element
...

```

---

### Post by NewWithoutClue on 2006-11-17
Such a wonderful language.

---

### Post by dataw0lf on 2006-11-17
> **NewWithoutClue said:**
> Such a wonderful language.

I'd marry it if it was a woman.

:-#

---

### Post by ironfistchamp on 2006-11-17
Thanks guys for the replies I am going to check it out right now. 

I overcame the problem this way but your way is much cleaner

```


avar = thisdict["secondval"]
avar[0]


```

Oh and btw dataw0lf you woudn't if I got there first :p 

Thanks again

Ironfistchamp

---

### Post by dataw0lf on 2006-11-17
> **ironfistchamp said:**
> 

Oh and btw dataw0lf you woudn't if I got there first :p 



Pssh!  You'd be my wingman. You'd get Perl.

So Sorry Charlie.

;)

---

### Post by ironfistchamp on 2006-11-18
Hehe.. Hmm Perl. Is she a looker?

---

### Post by po0f on 2006-11-18
No.

```
@P=split//,".URRUU\c8R";@d=split//,"\nrekcah xinU / lreP rehtona tsuJ";sub p{
@p{"r$p","u$p"}=(P,P);pipe"r$p","u$p";++$p;($q*=2)+=$f=!fork;map{$P=$P[$f^ord
($p{$_})&6];$p{$_}=/ ^$P/ix?$P:close$_}keys%p}p;p;p;p;p;map{$p{$_}=~/^[P.]/&&
close$_}%p;wait until$?;map{/^r/&&<$_>}%p;$_=$d[$q];sleep rand(2)if/\S/;print
```

---

