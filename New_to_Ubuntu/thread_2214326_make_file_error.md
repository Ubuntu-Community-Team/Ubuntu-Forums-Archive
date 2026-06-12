---
title: "make file error"
date: 2014-03-31
forum: New to Ubuntu
---

### Post by snifer2 on 2014-03-31
[COLOR=#000000]this is my make file[/COLOR]
[COLOR=#000000]# The original zip file, MUST be specified by each product[/COLOR]
[COLOR=#000000]local-zip-file := stockrom.zip[/COLOR]
[COLOR=#000000]# The output zip file of MIUI rom, the default is porting_miui.zip if not specified[/COLOR]
[COLOR=#000000]local-out-zip-file := MIUI_IOCEAN.zip[/COLOR]
[COLOR=#000000]local-miui-modified-apps :=[/COLOR]
[COLOR=#000000]# All apps from original ZIP, but has smali files chanded[/COLOR]
[COLOR=#000000]local-modified-apps :=[/COLOR]
[COLOR=#000000]# All apks from MIUI[/COLOR]
[COLOR=#000000]local-miui-removed-apps :=[/COLOR]
[COLOR=#000000]# All apps need to be removed from original ZIP file[/COLOR]
[COLOR=#000000]local-phone-apps :=[/COLOR]
[COLOR=#000000]# To include the local targets before and after zip the final ZIP file,[/COLOR]
[COLOR=#000000]# and the local-targets should:[/COLOR]
[COLOR=#000000]# (1) be defined after including porting.mk if using any global variable(see porting.mk)[/COLOR]
[COLOR=#000000]# (2) the name should be leaded with local- to prevent any conflict with global targets[/COLOR]
[COLOR=#000000]local-pre-zip := local-zip-misc[/COLOR]
[COLOR=#000000]# The local targets after the zip file is generated, could include 'zip2sd' to[/COLOR]
[COLOR=#000000]# deliver the zip file to phone, or to customize other actions[/COLOR]
[COLOR=#000000]include $(PORT_BUILD)/porting.mk[/COLOR]
[COLOR=#000000]local-zip-misc:[/COLOR]
[COLOR=#000000]local-test:[/COLOR]
[COLOR=#000000]echo "an example action"[/COLOR]



[COLOR=#000000]and this is what terminal give me[/COLOR]

[COLOR=#000000]root@ubuntu:~/MIUI# make workspace[/COLOR]
[COLOR=#000000]Makefile:22: *** missing separator. Stop[/COLOR]

[COLOR=#000000]any ideas?[/COLOR]

---

### Post by steeldriver on 2014-03-31
The 'action' line MUST be tabbed in

```

[COLOR=#000000]local-test:[/COLOR]
[COLOR=#0000ff]TAB--->[/COLOR][COLOR=#000000]echo "an example action"
[/COLOR]
```[COLOR=#000000]
[/COLOR]

---

### Post by oldos2er on 2014-03-31
Duplicate of [http://ubuntuforums.org/showthread.php?t=2212180](http://ubuntuforums.org/showthread.php?t=2212180) closed. Please don't create more than one thread for the same or similar questions; it dilutes community effort and is confusing.

---

