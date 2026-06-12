---
title: "Window scaling problem"
date: 2021-03-10
forum: New to Ubuntu
---

### Post by joubqa on 2021-03-10
I have the display scale set to 200% on my TV. When I go to a TV app and then come back to Ubuntu the windows are stretced. I have to close them and open again to make them right. Here's how Firefox looks like: 
[https://i.imgur.com/ETnvyOQ.png?1](https://i.imgur.com/ETnvyOQ.png?1)

---

### Post by DuckHook on 2021-03-10
This has always been a problem in Xorg with resolution switching midstream. I deal with it by scrupulously avoiding such switching. Games have to be run Windowed, or if they are only built full screen, then in a VM, or just standalone with a logout/login afterwards. It's a pain.

You could try Wayland. I have never done so, as Wayland breaks some of my LXD sandboxing.

---

