---
title: "Celsius in weather panel - Ubuntu 13.04"
date: 2013-10-14
forum: New to Ubuntu
---

### Post by angelsimon on 2013-10-14
Hi, i've been using Ubuntu since 10.04 LTS. I haven't used the forums yet but I want to start collaborating and asking as well. My first question is about the weather-indicator panel. It's working okay but it's showing the temperature using Farenheit grades. I know i can change it by going to Preferences and then choosing Celsius. But, no matter how many times I change it, the panel remains in Farenheit.
Is any way to change it using code or something, so I can fix it?

[IMG]http://imageshack.us/a/img191/962/1lex.png[/IMG]

PS: I'm using Ubuntu 13.04

Thanks in advance

---

### Post by ian-weisser on 2013-10-14
When you change the setting, it should stay changed.
Please file a bug report for the issue.

---

### Post by angelsimon on 2013-10-14
Hi, thanks for the reply. I would like to check out other sites before reporting a bug. Considering I've installed gnome-panel and I'm not using Unity. Maybe it's related.

Anyway, I also wanted to add that I could solve my problem using DConf editor that I happened to have installed.

Options are org -> gnome -> GWeather and there you can change all the settings you want in a surprisingly very user-friendly way. Then you have to end session and login again and now changes are permanent.

---

