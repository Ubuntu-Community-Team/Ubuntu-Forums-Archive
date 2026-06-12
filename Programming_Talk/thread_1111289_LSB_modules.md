---
title: "LSB modules"
date: 2009-03-30
forum: Programming Talk
---

### Post by NaF on 2009-03-30
Hello :)
I'm trying to write a little script, that'll grab just the version number of the machine's distro I'm running on. (I don't know if this'll work at all on other than ubuntu variants, but it matters little for now)
I've come to the conclusions that this is a way to go:
```
echo "`lsb_release -a | grep 'Description:' | awk '{print $2 " " $3 }'`"
```
does what I intended for it to do - cuts everything away except "Ubuntu 8.04.2" (in this case mind you). But on top of that, no matter what I try and cut away from the output, I get a > No LSB modules are available. 
 above the modified output. What is that and how do I make sure it doesn't appear? :confused:
Kind regards.

---

### Post by mister_pink on 2009-03-30
Don't really know what the message means as such, but you always get it because that line is written to standard error rather than standard out, and your pipe ('|') only takes the standard out. To hide it you can pipe standard error to standard out with "2>&1" then pipe the whole lot:
```

echo "`lsb_release -a 2>&1 | grep 'Description:' | awk '{print $2 " " $3 }'`"

```

---

### Post by NaF on 2009-03-30
> **mister_pink said:**
> Don't really know what the message means as such, but you always get it because that line is written to standard error rather than standard out, and your pipe ('|') only takes the standard out. To hide it you can pipe standard error to standard out with "2>&1" then pipe the whole lot:
```

echo "`lsb_release -a 2>&1 | grep 'Description:' | awk '{print $2 " " $3 }'`"

```

I don't fully understand what you're saying. But I'll look into it. Thanks for the help, solved my problem. Good day to you :)

---

### Post by bapoumba on 2009-03-30
Moved to PT.

---

### Post by Tibuda on 2009-03-30
```
lsb_release -ds
```

---

### Post by NaF on 2009-03-30
> **danielrmt said:**
> ```
lsb_release -ds
```
haha, yea ok that was easy. On the bright side, I learned a little about grep, awk and piping by not finding the -s parameter :) Thanks for the heads up.

---

