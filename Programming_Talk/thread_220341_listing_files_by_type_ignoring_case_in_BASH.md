---
title: "listing files by type ignoring case in BASH"
date: 2006-07-21
forum: Programming Talk
---

### Post by mikeym on 2006-07-21
Hi

I have been trying to do this for a couple of days now with no sucess. I want to select a list of files by their file extension - ignoring their case - in a BASH script.

I want to select all the par2 files of the form

abc.Par2
def.PAR2
ghi.par2
jkl.paR2
mno.pAr2
pqr.PaR2

But not files such as,

abc.VOL00+001.PAR2

I thought the following should work but I can't use the [COLOR="Red"]**ignore-case**[/COLOR] switch at the same time as the print or delete commands:

```

PARLIST=$(ls *.* | sed -n -e '/.vol[[:digit:]]\++[[:digit:]]\+.par2$/d[COLOR="Red"]**i**[/COLOR]' -e '/.par2$/p**[COLOR="Red"]i[/COLOR]**')

```

---

### Post by mikeym on 2006-07-22
I'm still stuck on this one. I'm not sure that sed is the way forward any more. I have seen mention of programs like super-sed on the web that do case insensitivity, but there must be a way to do this in standard BASH.

---

### Post by kabus on 2006-07-22
I think this would work:

```
find . -iname '*par2' | grep -vi '.vol[[:digit:]]\++[[:digit:]]\+.par2'
```

But you could probably do it with 'find' alone.

---

### Post by mikeym on 2006-07-22
> **kabus said:**
> I think this would work:

```
find . -iname '*par2' | grep -vi '.vol[[:digit:]]\++[[:digit:]]\+.par2'
```

But you could probably do it with 'find' alone.

Thanks that works.

Also i have jsut discoveded what I was doing wrong with sed. The '[COLOR="Red"]**i**[/COLOR]'s had to be in upper case, like so:

```

ls *.* | sed -n -e '/\.VOL[[:digit:]]\++[[:digit:]]\+\.PAR2$/**[COLOR="Red"]I[/COLOR]**d' -e '/\.par2$/**[COLOR="Red"]I[/COLOR]**p'

```

---

