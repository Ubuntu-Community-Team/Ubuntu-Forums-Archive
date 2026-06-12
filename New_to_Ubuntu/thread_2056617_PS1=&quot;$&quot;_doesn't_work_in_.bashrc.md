---
title: "PS1=&quot;$&quot; doesn't work in .bashrc?"
date: 2012-09-11
forum: New to Ubuntu
---

### Post by wilson888888888 on 2012-09-11
I want to make the prompt shorter, but I don't want to type the same command every time I open terminal. Why doesn't it work in .bashrc?

---

### Post by sisco311 on 2012-09-11
Most likely something overwrites it. Did you add the variable assignment (PS1=$) to the bottom of your .bashrc file?

Also please check out:  [http://mywiki.wooledge.org/DotFiles](http://mywiki.wooledge.org/DotFiles)

---

### Post by dniMretsaM on 2012-09-11
Ninja'd.

Also, it might look better like this:
```
PS1="\$ "
```

---

### Post by wilson888888888 on 2012-09-11
I moved the command to the bottom, and now it works. Thanks!

---

### Post by wilson888888888 on 2012-09-11
What's the difference between "$" and "/$"?

---

### Post by sisco311 on 2012-09-11
> **wilson888888888 said:**
> I moved the command to the bottom, and now it works. Thanks!

You are welcome!

---

### Post by sisco311 on 2012-09-11
> **wilson888888888 said:**
> What's the difference between "$" and "/$"?

[http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)

---

### Post by dniMretsaM on 2012-09-11
> **wilson888888888 said:**
> What's the difference between "$" and "/$"?

"$" will make your prompt just that. "\$ " is a dynamic prompt ("#" for root and "$" for normal users). The extra space is just for easier reading.

---

### Post by sisco311 on 2012-09-11
> **dniMretsaM said:**
> "$" will make your prompt just that. "\$ " is a dynamic prompt ("#" for root and "$" for normal users). The extra space is just for easier reading.

Thanks! I didn't know this. 


:redface: Although it's well documented in the man page: 
```
man bash | less +/"^PROMPTING"
```

---

