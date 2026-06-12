---
title: "How do I manage what workspace specific applications open In?"
date: 2014-04-09
forum: New to Ubuntu
---

### Post by joeslost on 2014-04-09
[FONT=UbuntuRegular][COLOR=#333333]I am new to Ubuntu and am loving it! I would really like to take full advantage of workspaces. I would like to have a workspace for all of one type and one for all of another type. ex. Having chrome always open in Wp 1 and having Libre office always open in Wp 2. But the annoyance I have encountered is when I open an app it will start in my active workspace, not the one I want it assigned or Pined to per say. [/COLOR][/FONT]
[FONT=UbuntuRegular][COLOR=#333333]I am running Ubuntu 13.10. [/COLOR][/FONT]
[FONT=UbuntuRegular][COLOR=#333333]My laptop is an Hp pavilion Dv7. [/COLOR][/FONT]

---

### Post by rburkartjo on 2014-04-09
you could switch to another workspace and open whatever there or you could just move the app to another workspace(once you min an app. if you right click on it you should get the option to move to any workplace). as far as always open an app in a specific workspace dont think it can be done.

---

### Post by grumblebum2 on 2014-04-10
When using unity/compiz you can use the **place windows** plugin of compizconfig-settings-manager (ccsm).
ccsm is not installed by default.
To install via terminal...
```
sudo apt-get install compizconfig-settings-manager
```

Once installed search for and run 
```
ccsm 
```

Goto ccsm > window management > place windows > fixed window placement > windows with fixed viewport
Hit the new button and use the add button to select a window.
Use X and Y values to set your viewport.

If unity buggers up in some way you can set compiz back to default with...
```
dconf reset -f /org/compiz/
```

---

