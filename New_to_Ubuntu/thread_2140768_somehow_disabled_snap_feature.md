---
title: "somehow disabled snap feature"
date: 2013-04-30
forum: New to Ubuntu
---

### Post by micahpage on 2013-04-30
i am using Gnome 3, and i read somewhere that gnome 3 no longer has minimize and maximize buttons on the toolbar. Now it worked maybe a month ago. Maybe an update removed them? So i attempted to fix that, and add them back. But I think in the process, i somehow removed the window manager snap feature. Now i finally have min, max, close back, but now the snap feature wont work since doing this. Because that is the first thing i noticed after fixing the buttons.

First thing i did was check
ccsm

but the snap feature is already checked, yet it wont work.

In case i somehow overwrote something, this is the history from the process of attempting to change the min, max buttons
```
257  gconf-editor  258  sudo apt-get update && sudo apt-get upgrade
  259  sudo apt-get install gconf-editor
  260  gconf-editor
  261  sudo apt-get install metacity
  262  metacity --replace
  263  htop
  264  metacity --replace
  265  sudo reboot
  266  metacity --replace
  267  pidof terminal
  268  sudo reboot
  269  sudo apt-get install seahorse
  270  seahorse
  271  gconf-editor
  272  gconftool-2 --set /desktop/gnome/shell/windows/buttom_layout --type string :minimize,maximize,close
  273  gconftool-2 --set /desktop/gnome/shell/windows/button_layout --type string :minimize,maximize,close
  274  gconftool-2 --set /desktop/gnome/shell/windows/button_layout --type string ":minimize,maximize,close"
  275  dconftool-2 --set org/gnome/shell/overrides/button_layout --type string ":minimize,maximize,close"
  276  gconftool-2 --set org/gnome/shell/overrides/button_layout --type string ":minimize,maximize,close"
  277  gconftool-2 --set /org/gnome/shell/overrides/button_layout --type string ":minimize,maximize,close"
  278  dconf-editor
  279  sudo apt-get install dconf-tools
  280  dconf-tools
  281  sudo apt-get install dconf-editor
  282  dconf-editor
  283  ccd 
  284  cd /org/gnome/shell/overrides
  285  cd /
  286  cd org
  287  man dconf
  288  dconf write /org/gnome/shell/overrides/button-layout '"close:maximize,minimize"'
  289  dconf write /org/gnome/shell/overrides/button-layout '":minimize,maximize,close"'
  290  history
  291  seahorse
  292  compiz --replace
  293  sudo apt-get install compizconfig-settings-manager
  294  compizconfig-settings-manager
  295  xinput-list
  296  xinput list
  297  ccsm



```

---

