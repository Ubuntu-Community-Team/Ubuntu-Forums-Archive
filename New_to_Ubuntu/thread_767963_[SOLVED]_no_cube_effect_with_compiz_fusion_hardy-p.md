---
title: "[SOLVED] no cube effect with compiz fusion hardy-please help"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by huntwell on 2008-04-26
I just installed Hardy and have gone through great pains to get compiz fusion up and running. I have used both Ubuntu Gutsy and Mint Daryna and have been able to get compiz fusion working flawlessly in both, but with Hardy it has been a different story.

I use Envy since it works the best with my ATI Radeon X1150 graphics card. I have the latest driver installed and also have the compizconfig-settings-manager installed. I am also using the fusion-icon for compiz fusion settings. 

I can get most if not all other settings to work properly, but cannot get the cube working like it should. When I use ctrl-alt and the left right arrows, it flips to another side but no cube. Also, when I use ctrl+alt and the left tab button, rather than getting a cube I get a flat screen that I can manipulate much like the cube, but it is only 2 sided.

Any suggestions? I was also wondering why I can't get compiz-switch to work with hardy. I really have enjoyed linux and am willing to give hardy a try, but I have never had to work so hard to get a linux distro working the way I want it. Still better than Windows however.

Thanks in advance for any suggestions and advice anyone can give me on this issue.

Huntwell

---

### Post by warbread on 2008-04-26
Sounds like you need to up the amount of virtual desktops compiz draws.  Go to Compiz Settings > General > Desktop Size and increase the horizontal size to whatever  you want it to be.  4 sides is a cube (since top and bottom are implied), and three is a triangle sort of deal.

---

### Post by sam_delta on 2008-04-26
yeah, change to 4 horizontal size , and then, go to system>administrator>Advanced desktop settings, and activate the "desktop cube" plug-in and "rotate cube" plug-in, you must deactivate "Desktop wall" plug-plug in in order to activate desktop cube.

tell us how it goes

sam

---

### Post by huntwell on 2008-04-26
SWEET! Thanks guys! It worked perfectly. Any ideas on the compiz-switch, or is that something that has not been worked out for hardy yet?

If only I would have known to look at the settings. Just goes to show how much of a noob I still am.

Take care,
Huntwell

---

### Post by Dr.Gringo on 2008-04-26
For smoother transitions with compiz you might want to install EnvyNG

---

### Post by sam_delta on 2008-04-26
you dont need a switch, to turn compiz off just type ALT-F2 and type

```
 metacity --replace 
```

to re-activate compiz, type ALT-F2 and type

```
 compiz --replace 
```


sam

---

### Post by pastalavista on 2008-04-26
I got compiz working great with help from this site:

[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

---

### Post by riptreeper on 2008-04-26
pastalavista thanks a lot that's exactly what I have been looking for. Your a life saver as is the person responsible for writing the article thanks again.

---

