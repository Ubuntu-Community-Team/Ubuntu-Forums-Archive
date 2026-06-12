---
title: "Not getting Cube effect"
date: 2013-05-12
forum: New to Ubuntu
---

### Post by tusharkoshti on 2013-05-12
Hi friends , 
I am not getting cube effect in Ubuntu 13.04.
1) 
I fired following command : 
[COLOR=red]/usr/lib/nux/unity_support_test -p 
[/COLOR][COLOR=#000000]And it's o/p is :
[/COLOR][COLOR=red][/COLOR]
 /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NVD9
OpenGL version string:  3.0 Mesa 9.1.1

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

2) 
Then I install compiz setting manager 

[COLOR=red]sudo apt-get install compizconfig-settings-manager[/COLOR]

[COLOR=red][/COLOR] sudo apt-get install compizconfig-settings-manager
[sudo] password for tushar: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compizconfig-settings-manager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

3)
But in CCSM , in Desktop , I got only 4 option. 

i) Desktop wall 
ii) Expo
iii) Ubuntu Unity Plugin 
iv) Viewport switcher

Didn't find  Desktop cube and rotate cube options. 
Plz help me. 

[COLOR=red]  
[/COLOR]

---

### Post by deadflowr on 2013-05-12
You need to install the plugins.

Not sure if it's compiz-plugins-extras anymore or something different.

I'm on precise ATM.
But I do have the plugins loaded on my raring install.

---

### Post by zombifier25 on 2013-05-12
It's compiz-plugins-extra. Installing it will give you all the Cube-related goodness.

---

### Post by tusharkoshti on 2013-05-12
Thank you friends ... Now it is working :)

---

