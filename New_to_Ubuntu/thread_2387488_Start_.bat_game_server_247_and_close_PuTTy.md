---
title: "Start .bat game server 24/7 and close PuTTy"
date: 2018-03-19
forum: New to Ubuntu
---

### Post by hajzlixer on 2018-03-19
I need run 3x servers on Ubuntu which are running on .bat and this .bat file runs .exe file too.. I need .bat file due to port and some other information which start server.

I need it run 24/7 nonstop on my VPS but I cant get it...

Only how I can run server is thanks to this codes ```
[COLOR=#555555][FONT=monospace]wineconsole --backend=user ./start.bat;[/FONT][/COLOR]
``` which start server in console but when I close PuTTy, server will shutdown too. When I gonna start run server another way I get this error
```
[FONT=Monaco]err:winediag:nulldrv_CreateWindow Application tried to create a window, but no driver could be loaded.[/FONT]
[FONT=Monaco]err:winediag:nulldrv_CreateWindow Make sure that your X server is running and that $DISPLAY is set correctly.[/FONT]
```

I don't know how to run it 24/7 as well PuTTy is not loged on VPS. Please tell me somebody how to run it corectlly. Thank you..

---

