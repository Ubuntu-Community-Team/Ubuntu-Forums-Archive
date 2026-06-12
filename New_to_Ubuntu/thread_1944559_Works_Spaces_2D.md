---
title: "Works Spaces 2D"
date: 2012-03-21
forum: New to Ubuntu
---

### Post by Frogs Hair on 2012-03-21
I was trying out Unity 2D and found my workspace switcher was not working and located the following command , which solved the problem . ```
gconftool-2 -s /apps/metacity/general/num_workspaces --type int 5
```

By changing the number at the end of the command it is possible to change the number of workspaces . When an application is open right click the title bar and use the "Move to Workspace" options . Bring the workspace forward by selecting the icon for open applications on the Unity Launcher.

---

