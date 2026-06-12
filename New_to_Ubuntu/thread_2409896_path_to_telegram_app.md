---
title: "path to telegram app"
date: 2019-01-08
forum: New to Ubuntu
---

### Post by dolceremy on 2019-01-08
I'm sorry but I can't find the path for telegram app, so I can add it to autostart
I use ubuntu 18.10 x86_64
Thank you

---

### Post by Tadaen_Sylvermane on 2019-01-08
From a terminal

```
whereis telegram
```

---

### Post by howefield on 2019-01-08
The telegram path is where ever you have extracted the executable to. If you downloaded the application package from the telegram website and extracted to the default folder the path would look like..

```
/home/$USER/Downloads/Telegram/Telegram
```

---

### Post by dolceremy on 2019-01-08
on terminal the reply is-->telegram (and stop)

---

### Post by dolceremy on 2019-01-08
> **howefield said:**
> The telegram path is where ever you have extracted the executable to. If you downloaded the application package from the telegram website and extracted to the default folder the path would look like..

```
/home/$USER/Downloads/Telegram/Telegram
```

I've installed telegram from ubuntu software buil-in app, so in the path you've described I can't find nothing

---

### Post by howefield on 2019-01-08
That being the case, sounds like a snap package.

Try..

```
/var/lib/snapd/desktop/applications/telegram-desktop_telegramdesktop.desktop
```

---

### Post by dolceremy on 2019-01-08
> **howefield said:**
> That being the case, sounds like a snap package.

Try..

```
/var/lib/snapd/desktop/applications/telegram-desktop_telegramdesktop.desktop
```
Thank you so much: works well!

---

### Post by howefield on 2019-01-08
> **dolceremy said:**
> Thank you so much: works well!

You are very welcome, glad it works.

---

