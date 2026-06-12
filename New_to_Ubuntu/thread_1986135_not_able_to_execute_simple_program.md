---
title: "not able to execute simple program"
date: 2012-05-24
forum: New to Ubuntu
---

### Post by pritesh80 on 2012-05-24
i m using ubuntu 

as i m learning programming in C-language 

but it showing error


pritesh@pritesh-laptop:~$ gcc -Wall -g math.c -o math
/tmp/ccNBsla6.o: In function `main':
/home/pritesh/math.c:21: undefined reference to `cos'
collect2: ld returned 1 exit status
pritesh@pritesh-laptop:~$ ./math
bash: ./math: No such file or directory

can anyone help me

Pritesh

---

### Post by roelforg on 2012-05-24
Use this command:
```

gcc -Wall -g math.c **-lm** -o math

```
(i added -lm)

---

