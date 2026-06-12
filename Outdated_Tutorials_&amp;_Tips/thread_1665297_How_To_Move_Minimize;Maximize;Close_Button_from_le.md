---
title: "How To Move Minimize;Maximize;Close Button from left to right, ONE COMMAND!!!!"
date: 2011-01-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Bazzi313 on 2011-01-12
Press Alt+f2 Or Simply Open a terminal and copy and paste the following command:

***gconftool-2 --set /apps/metacity/general/button_layout --type string menu:minimize,maximize,close***

And Then If you want to Change the Order Of the Buttons, For Eg Max,Min,Close

Simply Press Alt+f2

Type **Gconf-Editor** and Press run

The key that we want to edit is in apps/metacity/general.

The button layout can be changed by changing the “button_layout” key. Double-click button_layout to edit it.

And then put them in the order you like from Left - Right

---

