---
title: "How to compile fortran programs using gfortran in LINUX OS"
date: 2011-09-15
forum: New to Ubuntu
---

### Post by prudhvim on 2011-09-15
Hi,

I have around 100 files in my project. I am able to compile them using gfortran -o command but I unable to execute the executable as it is not getting created. Can anyone help me with this? I created a simple helloworld program exe using the same command as mentioned above.

Thanks,
Prudhvi

---

### Post by MG&amp;TL on 2011-09-15
Can you post the exact command you're using? And is it giving any errors? Try

```
man gfortran
```

And look for a 'pedantic' or 'thorough' option.

---

### Post by prudhvim on 2011-09-28
I have compiled all the files using "gfortran -c *.f' command. and then I used "gfortran -o "nameof the executable" main.f". I was getting error messages stating "UNDEFINED REFERENCE to 'function name'". Then I used "gfortran -c -o "name of the executable" main.f" command. It solved the problem but its creating an object file(relocatable file) and not an executable.

---

