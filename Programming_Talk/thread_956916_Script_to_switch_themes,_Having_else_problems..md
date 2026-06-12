---
title: "Script to switch themes, Having else problems."
date: 2008-10-23
forum: Programming Talk
---

### Post by niccholaspage on 2008-10-23
So I made a script to switch themes, But I also wanted the user to be able to change the metacity theme. For example, If A user typed this:
```
sh switch-theme Human
```Now this would switch the Gnome Theme And the Metacity Theme.
This code is the problem.
```
sh switch-theme Human Glossy
```But this will change the Metacity theme and Gnome Theme to Human, When it should change the metacity theme to Glossy and change the gnome theme to Human.((Changing the gnome theme works fine.)
Here is the script's code.
```

#!/bin/bash
gconftool-2 --type string --set /desktop/gnome/interface/gtk_theme $1
if [ $2=0 ]
then
gconftool-2 --type string --set /apps/metacity/general/theme $1
else
gconftool-2 --type string --set /apps/metacity/general/theme $2
fi

```

---

### Post by gnusci on 2008-10-26
Try replacing the line 

**if [ $2=0 ]**

by

**if [ -z "$2" ]**

---

