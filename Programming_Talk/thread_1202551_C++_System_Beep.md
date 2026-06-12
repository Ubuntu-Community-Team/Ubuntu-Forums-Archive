---
title: "C++ System Beep?"
date: 2009-07-02
forum: Programming Talk
---

### Post by Swenghk on 2009-07-02
Is there any command to use the system beep in C++? I know I can use some commands like system("clear"), but is there one for the beep?

---

### Post by JordyD on 2009-07-02
Can't you just `printf("\a")'?

I'm not sure what it would be with iostream. Maybe `cout << "\a"'?

EDIT: That `cout << "\a"' compiles for me.

---

### Post by Swenghk on 2009-07-02
I thought that may work...AND IT DID...That's how it worked in Python I just wasn't sure how to implement it in C++...man...Your great :]

Much thanks!

---

### Post by smartbei on 2009-07-02
You can also use the program 'beep', available in the repositories. It allows for changing the frequency, length, etc.

---

### Post by sdlynx on 2009-07-02
printf("%c",07);

also works I believe

---

### Post by soltanis on 2009-07-02
Same thing (\a is ASCII 07, terminal bell).

Changing frequency and duration sounds cool to me though, if you were a baller you'd use beep.

---

### Post by Mirge on 2009-07-02
> **soltanis said:**
> Same thing (\a is ASCII 07, terminal bell).

Changing frequency and duration sounds cool to me though, if you were a baller you'd use beep.

lol... I may play around with that sometime. Bet I could really have some fun with my cats..

---

