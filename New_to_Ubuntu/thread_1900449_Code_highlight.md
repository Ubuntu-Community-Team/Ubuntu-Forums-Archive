---
title: "Code highlight"
date: 2011-12-26
forum: New to Ubuntu
---

### Post by mahendra.singh on 2011-12-26
Dear Friends,

Using Ubuntu 9.04 and my requirnment is to highlight echo stmts, ex echo "mahendra"
now after execution of this i want to highlight mahendra in bold and color green.

Thanks in advance for quick response.

Regds
Mahendra Singh

---

### Post by llamabr on 2011-12-26
This is not quite as straightforward as changing the color output of ls, for example.  But something could be coded up.  Why this particular output, though.  If you have some more general goal in mind, it may be easier.  Or just echo?

---

### Post by sisco311 on 2011-12-26
Hi and welcome to the forums!

Check out BashFAQ 037 (link in my signature).

---

### Post by dodo3773 on 2011-12-26
Like this?
```

echo -e "\e[1;032mmahendra\e[0m"

```

---

### Post by mahendra.singh on 2011-12-27
> **dodo3773 said:**
> Like this?
```

echo -e "\e[1;032mmahendra\e[0m"

```

Thank you Guys and have used the below code, which seems fine for the application code:

echo " `tput smso` mahendrs  `tput rmso` "


:)

---

