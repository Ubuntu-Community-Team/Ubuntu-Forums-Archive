---
title: "[SOLVED] Rejoystick error..."
date: 2008-05-16
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-05-16
I keep getting an error with rejoystick can anyone tell me how to fix it?

```
 X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  150 (XTEST)
  Minor opcode of failed request:  2 (X_XTestFakeInput)
  Value in failed request:  0x0
  Serial number of failed request:  9
  Current serial number in output stream:  9


```

---

### Post by kamitsukai on 2008-05-17
<bump> anyone?

---

### Post by kamitsukai on 2008-05-18
Looks like nobody knows...Has anyone ever maped a gamepad in ubuntu?

---

### Post by d58e7 on 2008-06-01
I have the same error. When I press a button the keystroke just keeps going and I'm guessing it doesn't know how to shut it off.

---

### Post by samel_tvom on 2008-09-29
I just released a new version of rejoystick which ought to fix the problem. I heard that the Xtest library reacted differently when passing an argument to a fuction.

This guy wrote me a patch and a made a new relase, 0.8.1

Otherwise, what you could do is map all your keys and there will probably be less problem.

Hope this helps

---

