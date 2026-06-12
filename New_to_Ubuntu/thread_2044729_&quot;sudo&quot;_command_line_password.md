---
title: "&quot;sudo&quot; command line password"
date: 2012-08-19
forum: New to Ubuntu
---

### Post by ender323 on 2012-08-19
I use a sudo command, it asks for a password. However, it only gives me a few seconds to enter it, and I just cant type that fast! How can I make it give me more time or not require a password? I have seen directions to disable the password, but it requires that I become root, and THAT needs a password!

---

### Post by anewguy on 2012-08-19
> **ender323 said:**
> I use a sudo command, it asks for a password. However, it only gives me a few seconds to enter it, and I just cant type that fast! How can I make it give me more time or not require a password? I have seen directions to disable the password, but it requires that I become root, and THAT needs a password!

I personally have never seen it time out.  Perhaps you are pressing the "enter" key by accident instead of key near it.  The password will be your normal password and won't show on the screen as you type it, then press "enter" when you're done.

---

### Post by Hadaka on 2012-08-19
Hi, when you type a sudo command and it asks for a password
you enter the password. You will NOT see it echo the password back
nor do you hit enter and then the password.....you enter the password
and then hit enter. As a test..I issued a sudo command and waiter 3 minutes
without entering anything....then, entered my password followed by <enter>
and it responded as it should.  Does this help?

---

### Post by lisati on 2012-08-19
Random thought:
Sometimes the words used in instructions can get confusing and seem a little bit strange. When a computer asks you to *enter* some information, it usually means for you to *type* the information, and doesn't necessarily mean that you need to press the 'enter' key. Similarly, when you are asked to *hit* a key, *pressing* the key is usually sufficient.

---

### Post by dodo3773 on 2012-08-20
> **Hadaka said:**
> Hi, when you type a sudo command and it asks for a password
you enter the password. You will NOT see it echo the password back


If this isn't your problem I don't know what is. This has got to be it. After the sudo part it drops to this:
```

Password: 

```

At that time you type in your password and then hit enter. While you are typing it in it's invisible.

---

