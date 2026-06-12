---
title: "Issue with ctrl-d and ubuntu"
date: 2008-09-25
forum: Programming Talk
---

### Post by KunoNoOni on 2008-09-25
here is a very simple perl program

```

#!/usr/bin/perl
chomp (@list = <STDIN>);
@list = reverse @list;
print @list;

```

the only problem I have is that when I use CTRL-D to send the end of file command, the program just stops and my prompt looks like this: kuno@Genma:~/perl$ /perl$ (yes I named all the computers after Ranma 1/2 characters =P). this happens in putty and on the box using eterm. its very odd and a hinderence, I know the code is sound. any ideas?

---

### Post by KunoNoOni on 2008-09-26
Ok, forget ideas.... I'll take theories, guesses and tarot card readings at this point :)

---

### Post by slavik on 2008-09-26
could you show a console output when running the script?

Also, what are you trying to do? Are you just trying to print the inputted lines in reverse order?

---

### Post by Greyed on 2008-09-26
What shell are you using?

---

### Post by SecretCode on 2008-09-27
Yes, what shell? And what is your prompt normally? I guess "kuno@Genma:~/perl$" without the extra perl$

I would guess that Ctrl-D has been mapped/intercepted to do something else, like start a child shell.

---

