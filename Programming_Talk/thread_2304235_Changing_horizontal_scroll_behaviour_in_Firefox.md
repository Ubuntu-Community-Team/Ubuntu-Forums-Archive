---
title: "Changing horizontal scroll behaviour in Firefox"
date: 2015-11-25
forum: Programming Talk
---

### Post by dsmirnov90 on 2015-11-25
Hello, all!

I'm using a Logitech mouse with the horizontal scroll wheel and I want to use it to switch between tabs in Firefox. I have tried to solve my issue inside the browser, but I haven't succeeded: [https://support.mozilla.org/en-US/questions/1094744](https://support.mozilla.org/en-US/questions/1094744) .

Now I want to make a script which redefines default behaviour of the horizontal scroll in my mouse to send Ctrl+PgUp/PgDown signals when Firefox is an active window. The xev command in terminal gave me:

```
ButtonPress event, serial 37, synthetic NO, window 0x7200001,
    root 0x9d, subw 0x0, time 49090019, (125,107), root:(1407,205),
    state 0x0, button 7, same_screen YES

ButtonRelease event, serial 37, synthetic NO, window 0x7200001,
    root 0x9d, subw 0x0, time 49090019, (125,107), root:(1407,205),
    state 0x0, button 7, same_screen YES

ButtonPress event, serial 37, synthetic NO, window 0x7200001,
    root 0x9d, subw 0x0, time 49095069, (125,107), root:(1407,205),
    state 0x0, button 6, same_screen YES

ButtonRelease event, serial 37, synthetic NO, window 0x7200001,
    root 0x9d, subw 0x0, time 49095069, (125,107), root:(1407,205),
    state 0x0, button 6, same_screen YES
```

But I have no idea what to do next. May be someone can help me?

Thanks in advance!

---

### Post by Dimarchi on 2015-11-26
Add-ons such as [URL="https://addons.mozilla.org/EN-us/firefox/addon/tab-wheel-scroll/"]

[/URL][https://addons.mozilla.org/EN-us/firefox/addon/tab-wheel-scroll/](https://addons.mozilla.org/EN-us/firefox/addon/tab-wheel-scroll/)

don't work for you?

---

