---
title: "Transparent Conky Background?"
date: 2017-09-16
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2017-09-16
I'm having trouble getting transparency on my conky background. Can someone give me the magic recipe for that? I find examples online but they are pre lua .conkyrc so they don't match up exactly. Driving me crazy.

---

### Post by Frogs Hair on 2017-09-16
Posing the .conkyrc may help, and also make sure the syntax is version 1.10 compatible.
  [https://github.com/brndnmtthws/conky/wiki/Convert-to-new-1.10-syntax](https://github.com/brndnmtthws/conky/wiki/Convert-to-new-1.10-syntax)

---

### Post by again? on 2017-09-17
If you want full transparency use this  lua syntax in your lua conky config
```
own_window_transparent = true,
own_window_argb_visual = true,
own_window_argb_value = 0,
```


If you want a semi-transparent background with rounded corners you
can use a **draw_bg.lua** script.
With the newer conky lua configs, the syntax to load the script would look like this. 
```
lua_load = '[COLOR="#0000CD"]/home/glen/conky/lua/draw_bg.lua[/COLOR]',
lua_draw_hook_pre = 'draw_bg',
```
Use [COLOR="#0000CD"]your path[/COLOR] to a lua background script.

You can find a lua backgound script and an explanation of conky transparency [**HERE**]("https://ubuntuforums.org/showthread.php?t=2361842&page=6&p=13648650#post13648650").
The link is using the old conky syntax.

---

