---
title: "wxpython help"
date: 2007-07-26
forum: Programming Talk
---

### Post by Somenoob on 2007-07-26
```
Traceback (most recent call last):
  File "wxgui.py", line 17, in <module>
    app.Mainloop()
AttributeError: 'App' object has no attribute 'Mainloop'
```

What is an AttributeError? this is suppose to be the last line.

---

### Post by raja on 2007-07-26
An attribute error is when you are asking for some attribute that is not there.
Here it means that your 'App' has no 'Mainloop'.
Remember python is case-senstive. I think what you want is ```
app.MainLoop()
```

---

### Post by Somenoob on 2007-07-26
> **raja said:**
> An attribute error is when you are asking for some attribute that is not there.
Here it means that your 'App' has no 'Mainloop'.
Remember python is case-senstive. I think what you want is ```
app.MainLoop()
```

Thanks.

---

