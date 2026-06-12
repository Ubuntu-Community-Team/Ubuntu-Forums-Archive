---
title: "32 or 64 bit Ubuntu?"
date: 2012-05-26
forum: New to Ubuntu
---

### Post by linux12 on 2012-05-26
I recently did a reinstall of Ubuntu. The aim was to apply the 64-bit version. How can I check to see if I'm running 64 bit? Is there a terminal command for that or something? :confused:

---

### Post by wojox on 2012-05-26
```
uname -p
```

Should say :P

---

### Post by PaulW2U on 2012-05-26
```
uname -a
```

If the output line includes i386/i686 then it's 32-bit.

If you see amd64 or x64 then it's 64-bit.

Sorry, I can't be exact as I only have 32-bit Kubuntu available at the moment.

---

### Post by xedi on 2012-05-26
> **PaulW2U said:**
> 

Sorry, I can't be exact as I only have 32-bit Kubuntu available at the moment.

It's  ```
x86_64
```

You can also open the system-monitor and it will tell you under the first tab.

---

### Post by PaulW2U on 2012-05-26
Deleted

---

### Post by linux12 on 2012-05-26
Where is the system monitor? Also, I found it is indeed 64 bit.

---

### Post by linux12 on 2012-05-26
How do you delete a post?

---

### Post by xedi on 2012-05-26
> **linux12 said:**
> Where is the system monitor? Also, I found it is indeed 64 bit.

Just open the dash (Ubuntu symbol in the top left corner or push windows/super key) and start typing system monitor.

---

### Post by linux12 on 2012-05-26
placeholder

---

### Post by linux12 on 2012-05-26
> **xedi said:**
> Just open the dash (Ubuntu symbol in the top left corner or push windows/super key) and start typing system monitor. That will be very useful!

---

