---
title: "can't print these variables together in bash"
date: 2007-06-06
forum: Programming Talk
---

### Post by RawMustard on 2007-06-06
Hi all...

This is the var \"s$stchm$motoNum\"

What is should print out is s1m1 and then s1m2 and so on, but the only way I can get it to print the second variable is to put a space between them like s$stch m$motorNum. 
This however gives me a space which is undesirable.  Could one of you kind heated guru's tell me how I could solve this problem please.

---

### Post by meatpan on 2007-06-06
The issue doesn't occur when I try to reproduce your problem w/Bash-3.0:
```

bash-3.00$ stchm=lm1
bash-3.00$ motoNum=lm2
bash-3.00$ echo \"s$stchm$motoNum\"
"slm1lm2"

```

Can you give some more context to your script?  Maybe send a minimal script that produces the problem.

---

### Post by Mr. C. on 2007-06-06
You need to uses braces to disambiguate the variable names:

  $var --> ${var}

\"s${stch}m${motorNum}\" 

MrC

---

### Post by hillbilly on 2007-06-06
Just to clarify, meatpan's example on bash was not consistent with the question. It should have been:
> stch=lm1
motoNum=lm2

---

### Post by RawMustard on 2007-06-06
Thanks Guys for the replys.

@Mr. C.  Yep that did it, thanks for your help :)

---

