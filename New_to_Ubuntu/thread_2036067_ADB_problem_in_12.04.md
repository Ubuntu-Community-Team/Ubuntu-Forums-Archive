---
title: "ADB problem in 12.04"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by amin021023 on 2012-08-01
Hi and Love

the **udev rules is ok** I belive , and flashtool works fine , but when I do** adb devices** , adb starts but cant find my device: 

I have the latest version of sdk and using ubuntu 12.04...and the usb debug is on and...

---

### Post by levlaz on 2012-08-01
Try 

```
./adb devices 
```

---

### Post by amin021023 on 2012-08-01
solved! thanks alot!!!

---

### Post by levlaz on 2012-08-01
You're welcome! Glad I could help. 

Make sure you use the same format if you are installing .apk or anything else that requires the adb command.

---

