---
title: "[Ubuntu 12.10] Launcher and Menus disappeared."
date: 2012-12-16
forum: New to Ubuntu
---

### Post by YasinG on 2012-12-16
I know the Ubuntu commuinty forums are littered with this exact same question, but I did do my research and tried all the solutions I could find to no avail. I installed Compiz, and forgot to install any menu tool like AWN as usual, and the result is that the launcher and the top menus are gone.
I tried doing '[COLOR=Blue]Unity --reset[/COLOR]', only to be told it has been depricated. Tried '[COLOR=Blue]Unity reset[/COLOR]' which did what appears to be resetting unity but no resetting took place.
I tried this ...
[COLOR=Blue]dconf reset -f /org/compiz/
setsid unity[/COLOR]
... which I found on some forum that said Ubuntu 12.10 uses Gsetting not Gconf, which is why 'unity --reset' is depricated, and it should work but it didn't. It produced some lines then stops, as 'unity reset' does, but when I get out of terminal, no change has occured.

I tried dumping the configuration of /org/compiz/ and this was the result:
```
[/]
existing-profiles=['Default', 'unity']
current-profile='unity'

[profiles/Default/plugins/core]
active-plugins=['core', 'composite', 'opengl', 'compiztoolbox', 'decor', 'vpswitch', 'snap', 'mousepoll', 'resize', 'place', 'move', 'wall', 'grid', 'regex', 'imgpng', 'session', 'gnomecompat', 'animation', 'fade', 'workarounds', 'scale', 'expo', 'ezoom']

[profiles/unity]
plugins-with-set-keys=['core', 'composite', 'opengl', 'decor', 'vpswitch', 'snap', 'mousepoll', 'resize', 'place', 'move', 'wall', 'grid', 'session', 'animation', 'fade', 'unitymtgrabhandles', 'workarounds', 'scale', 'expo', 'ezoom', 'unityshell', 'screenshot', 'switcher', 'firepaint', 'splash', 'showrepaint', 'scaleaddon', 'resizeinfo', 'annotate', 'maximumize', 'addhelper', 'opacify', 'ring', 'crashhandler', 'staticswitcher', 'showdesktop', 'trailfocus', 'neg', 'titleinfo', 'bench', 'winrules', 'kdecompat', 'workspacenames', 'wobbly', 'widget', 'mblur', 'shelf', 'clone', 'water', 'td', 'mag', 'extrawm', 'put', 'commands', 'rotate', 'fadedesktop', 'imgjpeg', 'shift', 'cube', 'notification', 'showmouse', 'scalefilter', 'obs']

[profiles/unity/plugins/resizeinfo]
gradient-1='#cccce6cc'
gradient-2='#f3f3f3cc'
gradient-3='#d9d9d9cc'

[profiles/unity/plugins/wall]
thumb-highlight-gradient-shadow-color='#dfdfdfff'
arrow-base-color='#e6e6e6d9'
arrow-shadow-color='#dcdcdcd9'

[profiles/unity/plugins/unityshell]
[COLOR=Red]launcher-hide-mode=0[/COLOR]

[profiles/unity/plugins/animation]
unminimize-effects=['animation:Glide 2']

[profiles/unity/plugins/decor]
active-shadow-color='#00000080'
inactive-shadow-color='#000000ff'

[profiles/unity/plugins/expo]
ground-color1='#b3b3b3cc'
ground-color2='#b3b3b300'

[profiles/unity/plugins/firepaint]
fire-color='#ff3305ff'

[profiles/unity/plugins/core]
active-plugins=['core', 'composite', 'opengl', 'decor', 'mousepoll', 'place', 'move', 'gnomecompat', 'put', 'wall', 'compiztoolbox', 'imgpng', 'unitymtgrabhandles', 'snap', 'regex', 'session', 'fade', 'expo', 'ezoom', 'scale', 'unityshell']

[profiles/unity/plugins/shift]
ground-color1='#b3b3b3cc'
ground-color2='#b3b3b300'

[profiles/unity/plugins/showmouse]
color='#ffdf3fff'

[integrated]
command-window-screenshot='gnome-screenshot --window'
```The line in red means that it will be hidden or not ?. It makes sense that 0 should set hidden to false, but if so, why is the launcher still hidden ?. I wanted to try to change it but didn't know how. I tried to use the 'write' command to set it to 1, but there is some error in the value parameter.
That's all I could do. My question is, how do I get back the launcher and menus ?.
Thank you.

---

### Post by DuckHook on 2012-12-16
1. Bring up a terminal with <Ctrl>+<Alt>+<t>
2. Do:

```
ccsm
```3. Find and open *Ubuntu Unity Plugin*
4. Check the box: *Enable Ubuntu Unity Plugin*
5. If Launcher does not appear right away, logout/login

---

### Post by YasinG on 2012-12-17
I did do that, it was the first solution I found. I just did it again now, for whatever reason, but no change.

---

### Post by 3rdalbum on 2012-12-17
What do you mean by "I installed Compiz"?

Compiz is installed by default on Ubuntu. The Compiz settings manager isn't, but if you've installed the settings manager and then played around with it you may have enabled something that conflicts with Unity.

In gconf-editor (or dconf-editor) try removing all Compiz-related keys.

---

### Post by YasinG on 2012-12-17
Yes, I meant the Compiz Settings Manager. But I hadn't played with anything; as soon as I installed it, the menus and launcher were gone.
How do I remove them ?.

---

### Post by Frogs Hair on 2012-12-17
The unity reset command has changed in 12.10.```
setsid unity
```

The Dconf Editor must be installed to use this command. 

```
dconf reset -f /org/compiz/
```

---

### Post by YasinG on 2012-12-17
Yes, I know it has been changed. I did use 'setsid unity', as mentioned in the OP. And Dconf Editor is installed, miraculously by itself since I didn't even know it existed before trying to use it, and I produced the output of reading with it.

---

### Post by YasinG on 2012-12-17
Further information, is that I have no internet connection on that laptop. I use a USB modem and I don't know how to connect to it from the Terminal.
I also remember downloading a driver for my graphics card Nvidia right before it, or maybe right after  it, that I didn't pay much attention to. Could that be the problem ?. I'm getting the same output in terminal when I attempt resetting unity as someone who installed the wrong driver, but his was ATI. It ends with this line: Fatal: glXQueryExtensionsString is NULL for screen 0.

---

