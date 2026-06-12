---
title: "c begginer question about io fasilities"
date: 2011-04-24
forum: Programming Talk
---

### Post by geltonas on 2011-04-24
hi, I am trying to figure out what wrong this code:

```

#include <stdio.h>

main() {
int n=0;
scanf("%d",&n);
printf("jusu ivestas skaicius: %d\n",square(n));

}

square (int x)
{
return (x*x);
}

```
but the outcome is not what i am expexting:

cppguy@cppguy-VGN-FE41Z:~$ gcc -o bandymas bandymas.c
cppguy@cppguy-VGN-FE41Z:~$ ./bandymas
8
jusu ivestas skaicius: 0

the problem is I want to get user's entered variable squared and then displayed on a screen...

---

### Post by simeon87 on 2011-04-24
You have already fixed the problem, there can't be any additional text in scanf.

---

### Post by Arndt on 2011-04-24
> **geltonas said:**
> hi, I am trying to figure out what wrong this code:

```

#include <stdio.h>

main() {
int n=0;
scanf("%d",&n);
printf("jusu ivestas skaicius: %d\n",square(n));

}

square (int x)
{
return (x*x);
}

```
but the outcome is not what i am expexting:

cppguy@cppguy-VGN-FE41Z:~$ gcc -o bandymas bandymas.c
cppguy@cppguy-VGN-FE41Z:~$ ./bandymas
8
jusu ivestas skaicius: 0

the problem is I want to get user's entered variable squared and then displayed on a screen...

I don't know. It works for me:

```
$ ./bandymas
8
jusu ivestas skaicius: 64

```

---

### Post by geltonas on 2011-04-24
thanks bro it was simple then it looked like

---

### Post by safarin on 2011-04-24
It also work for me... :confused:

---

