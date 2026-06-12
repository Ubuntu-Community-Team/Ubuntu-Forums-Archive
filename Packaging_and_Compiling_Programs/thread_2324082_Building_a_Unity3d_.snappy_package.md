---
title: "Building a Unity3d .snappy package?"
date: 2016-05-10
forum: Packaging and Compiling Programs
---

### Post by hhoria on 2016-05-10
[COLOR=#242729][FONT=Arial]Has anyone tried so far to package a linux app with snapcraft for Ubuntu store distribution?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Unity exports 1 or 2 executables for x86 and/or x86_64 and a Data folder. How should these files and folder be mentioned in the snapcraft.yaml file? I have no understanding of snapcraft documentation's example (webserver part and the others) ...

the Data hierarchy is
[COLOR=#222222][FONT=Verdana]Data[/FONT][/COLOR][/FONT][/COLOR]
&#9500;&#9472;&#9472; globalgamemanagers
&#9500;&#9472;&#9472; globalgamemanagers.assets
&#9500;&#9472;&#9472; level0
&#9500;&#9472;&#9472; level1
&#9500;&#9472;&#9472; Managed
&#9474;   &#9500;&#9472;&#9472; Assembly-CSharp.dll
&#9474;   &#9500;&#9472;&#9472; Mono.Security.dll
&#9474;   &#9500;&#9472;&#9472; mscorlib.dll
&#9474;   &#9500;&#9472;&#9472; System.Core.dll
&#9474;   &#9500;&#9472;&#9472; System.dll
&#9474;   &#9500;&#9472;&#9472; UnityEngine.dll
&#9474;   &#9500;&#9472;&#9472; UnityEngine.dll.mdb
&#9474;   &#9500;&#9472;&#9472; UnityEngine.Networking.dll
&#9474;   &#9492;&#9472;&#9472; UnityEngine.UI.dll
&#9500;&#9472;&#9472; Mono
&#9474;   &#9500;&#9472;&#9472; etc
&#9474;   &#9474;   &#9492;&#9472;&#9472; mono
&#9474;   &#9474;       &#9500;&#9472;&#9472; 1.0
&#9474;   &#9474;       &#9474;   &#9500;&#9472;&#9472; DefaultWsdlHelpGenerator.aspx
&#9474;   &#9474;       &#9474;   &#9492;&#9472;&#9472; machine.config
&#9474;   &#9474;       &#9500;&#9472;&#9472; 2.0
&#9474;   &#9474;       &#9474;   &#9500;&#9472;&#9472; Browsers
&#9474;   &#9474;       &#9474;   &#9474;   &#9492;&#9472;&#9472; Compat.browser
&#9474;   &#9474;       &#9474;   &#9500;&#9472;&#9472; DefaultWsdlHelpGenerator.aspx
&#9474;   &#9474;       &#9474;   &#9500;&#9472;&#9472; machine.config
&#9474;   &#9474;       &#9474;   &#9500;&#9472;&#9472; settings.map
&#9474;   &#9474;       &#9474;   &#9492;&#9472;&#9472; web.config
&#9474;   &#9474;       &#9500;&#9472;&#9472; browscap.ini
&#9474;   &#9474;       &#9500;&#9472;&#9472; config
&#9474;   &#9474;       &#9492;&#9472;&#9472; mconfig
&#9474;   &#9474;           &#9492;&#9472;&#9472; config.xml
&#9474;   &#9500;&#9472;&#9472; x86
&#9474;   &#9474;   &#9492;&#9472;&#9472; libmono.so
&#9474;   &#9492;&#9472;&#9472; x86_64
&#9474;       &#9492;&#9472;&#9472; libmono.so
&#9500;&#9472;&#9472; Plugins
&#9474;   &#9500;&#9472;&#9472; x86
&#9474;   &#9474;   &#9492;&#9472;&#9472; ScreenSelector.so
&#9474;   &#9492;&#9472;&#9472; x86_64
&#9474;       &#9492;&#9472;&#9472; ScreenSelector.so
&#9500;&#9472;&#9472; Resources
&#9474;   &#9500;&#9472;&#9472; unity_builtin_extra
&#9474;   &#9492;&#9472;&#9472; unity default resources
&#9500;&#9472;&#9472; sharedassets0.assets
&#9500;&#9472;&#9472; sharedassets0.assets.resS
&#9500;&#9472;&#9472; sharedassets0.resource
&#9500;&#9472;&#9472; sharedassets1.assets
&#9500;&#9472;&#9472; sharedassets1.assets.resS
&#9492;&#9472;&#9472; sharedassets1.resource


Thankyou

---

