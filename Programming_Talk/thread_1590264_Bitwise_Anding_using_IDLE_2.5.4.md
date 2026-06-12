---
title: "Bitwise Anding using IDLE 2.5.4"
date: 2010-10-07
forum: Programming Talk
---

### Post by 2simple on 2010-10-07
Hi, 
 
im using IDLE 2.5.4 and im laying the ground work for a more complexed program, but im having some learner issues as follows:
 
a = [36, 31, 35]
b = a[0] & 0x0f
c = a[1] & 0x0f
d = a[2] & 0x0f
 
I expect b, c & d to be 6, 1 & 5 respectively, however IDLE's Python shell returns 4, 15 and 3 respectively. Can any one point out what Im missing ?
 
much thanks,
2simple

---

### Post by spjackson on 2010-10-07
4, 15 and 3 are what I'd expect in any of the languages I know. Why do you expect 6, 1 & 5? e.g.
```

      36 ==> 00100100
&     15 ==> 00001111
=        ==> 00000100

```which is 4.

---

### Post by 2simple on 2010-10-07
Hi sp, I should have stated that the 3 numbers in "a" are hex. So 36:
0x36: 0011 0110
   &  0000 1111
   =  0000 0110 

Regards,

---

### Post by spjackson on 2010-10-07
If you had written
```

a = [0x36, 0x31, 0x35]

```then yes, you would get the results you expected. However, you didn't write that.

---

### Post by 2simple on 2010-10-07
Thanks a lot !!

Regards!

---

