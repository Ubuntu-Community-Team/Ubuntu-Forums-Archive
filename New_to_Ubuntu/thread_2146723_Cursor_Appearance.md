---
title: "Cursor Appearance"
date: 2013-05-19
forum: New to Ubuntu
---

### Post by omgakos17 on 2013-05-19
I have changed my cursor appearance with "Gnome Tweek Tool" by extracting cursor themes on **usr/share/icons** as **administrator** but the cursor takes effect only on program windows. It doesn't take effect on **Desktop** or on **computer files**. Do you know how i can fix this or if this problem has a solution?

---

### Post by Dennis N on 2013-05-19
Somewhat-involved fix for the indecisive-cursor problem from a year ago for Ubuntu 12.04, Unity desktop. 
Theme's folder must contain a file named **cursor.theme**. Check that it does. Some don't. 
If it is missing, create a 2-line text file named cursor.theme with a text editor:

```
[Icon Theme]
Inherits=Theme-Name

```
Replace Theme-Name above with the exact cursor theme name found on the theme folder.

You save this file as **cursor.theme** and _it must be inside the theme-folder_.  

Install the program Alternatives Configurator which is in the Ubuntu repository under the package name **galternatives**.
Follow the steps in this post:

[http://ubuntuforums.org/showpost.php?p=11929215&postcount=17](http://ubuntuforums.org/showpost.php?p=11929215&postcount=17)

Instead of following the last line beginning "For Unity", I would now use the **My Unity** tool to choose the cursor from the Themes>Icons box and close it.
Log out and back in and the new cursor should be working properly.

---

### Post by omgakos17 on 2013-05-21
Thank you very much man! That worked correctly. I just wanna ask you one more question. I have to remain the program to my computer or i can unistal it after i ve done my job?

---

### Post by Dennis N on 2013-05-21
> **omgakos17 said:**
> Thank you very much man! That worked correctly. I just wanna ask you one more question. I have to remain the program to my computer or i can unistal it after i ve done my job?

Glad to hear that the instructions worked for you. 

You could remove galternatives, but I would leave it installed, as it takes very little space. It also has other uses - you may need it again for something in the future.

---

### Post by omgakos17 on 2013-05-22
> **Dennis N said:**
> Glad to hear that the instructions worked for you. 

You could remove galternatives, but I would leave it installed, as it takes very little space. It also has other uses - you may need it again for something in the future.

ok thank you very much!

---

