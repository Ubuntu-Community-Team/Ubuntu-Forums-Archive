---
title: "[help] String in python"
date: 2007-10-26
forum: Programming Talk
---

### Post by alvinistic on 2007-10-26
Hi all,

I'm having this problem when programming using python-crypto.

Basically, I encrypt a plain text using AES
the resulting cipher is:
pF\xa3\x9c\xe0\xe7\xa3\r3q\xf2l\nUm\xb3 <\xb8J(\xf1\x14;TkG\xef\xc6\x11\xf5`

When i do len(cipher), it gives me 32.

Then I send that cipher through socket as string. I have confirmed the other end get the exact cipher. 
cipher2 = pF\xa3\x9c\xe0\xe7\xa3\r3q\xf2l\nUm\xb3 <\xb8J(\xf1\x14;TkG\xef\xc6\x11\xf5`
But, the problem is that when I do len(cipher2) at the resulting string, it gives me 76.

I think it is something related to the way the string is read (the '\' character, etc.). How can I address this problem so that the cipher2 can be treated as cipher1?

Thanks for your help.

---

### Post by alvinistic on 2007-10-26
Never mind, I found out that I can work around this by encoding the cipher with base64. Then I can do the comparison. 

Thx anyway :D

---

