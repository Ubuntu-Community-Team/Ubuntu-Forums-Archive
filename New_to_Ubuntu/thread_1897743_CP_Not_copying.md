---
title: "CP Not copying"
date: 2011-12-19
forum: New to Ubuntu
---

### Post by GiuHei3u on 2011-12-19
Hello. I am doing something wrong. I cannot copy a jpg which is on my desktop to the /usr/share/backgrounds/   I keep getting an error which states "missing destination file operand".

Here is the command I am using.

sudo cp ~/Desktop/Set1.jpg/usr/share/backgrounds

and with this command there is no copy and the error message.

Thanks!

gumshoegrant

---

### Post by lisati on 2011-12-19
Try:
```

sudo cp ~/Desktop/Set1.jpg /usr/share/backgrounds
```
(It needs a space just before /usr)

---

### Post by GiuHei3u on 2011-12-19
> **lisati said:**
> Try:
```

sudo cp ~/Desktop/Set1.jpg /usr/share/backgrounds
```(It needs a space just before /usr)

Thanks Lisati! I was not putting a space between the cp from/to. New at this and learned something.

gumshoegrant

---

