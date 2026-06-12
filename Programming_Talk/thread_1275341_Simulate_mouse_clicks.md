---
title: "Simulate mouse clicks"
date: 2009-09-25
forum: Programming Talk
---

### Post by cam888 on 2009-09-25
Is there a way to simulate mouse clicks in ubuntu, preferably using a compiled language (python, php), but I don't mind having to use C/C++. For example a function like Click(x, y) kind of thing. Anyone know of anything?

Thanks

---

### Post by doas777 on 2009-09-25
> **cam888 said:**
> Is there a way to simulate mouse clicks in ubuntu, preferably using a compiled language (python, php), but I don't mind having to use C/C++. For example a function like Click(x, y) kind of thing. Anyone know of anything?

Thanks

I do it in C# on windows on occasion. check out the mono runtime.

---

### Post by cam888 on 2009-09-25
I don't really know C#, and I'd prefer not to have to learn another language for this. Thank you anyway though. Anyone know of any other way?

---

### Post by unutbu on 2009-09-25
If you install the xdotool package, you can simulate a mouse click by running
```

xdotool click 1   # left mouse click
xdotool click 2   # middle mouse click
xdotool click 3   # right mouse click
xdotool mousemove 500 500  # moves the mouse to (500,500)
```

---

### Post by cam888 on 2009-09-25
Thank you, that looks perfect.

---

