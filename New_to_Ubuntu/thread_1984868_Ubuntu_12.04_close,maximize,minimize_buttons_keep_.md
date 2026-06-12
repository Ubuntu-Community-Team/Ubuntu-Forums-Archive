---
title: "Ubuntu 12.04 close,maximize,minimize buttons keep moving to the right?"
date: 2012-05-22
forum: New to Ubuntu
---

### Post by cyb3r_sn4k3 on 2012-05-22
A few days ago, all of a sudden all the buttons on the windows like close,maximize,minimize moved to the right. And so I tried using gconf-editor (Went to apps/metacity/general-->>button layout.) But mostly after restart it comes back to the right. How can I fix this ?

---

### Post by Frogs Hair on 2012-05-22
What DE are you using ? I can't seem to keep buttons on the left in the Gnome Shell and it may be update related . The configuration seems to reset to default when certain updates are applied. Unity always defaults to the left.

---

### Post by cyb3r_sn4k3 on 2012-05-22
> **Frogs Hair said:**
> What DE are you using ? I can't seem to keep buttons on the left in the Gnome Shell and it may be update related . The configuration seems to reset to default when certain updates are applied. Unity always defaults to the left.
 
I am using unity.

---

### Post by tawfekov on 2012-05-22
yes i am using unity and i am facing the same issue

---

### Post by codingman on 2012-05-22
try this:

```
unity --reset
```

---

### Post by Frogs Hair on 2012-05-22
Ubuntu Tweak may be another option if the command doesn't solve the problem .

---

### Post by cyb3r_sn4k3 on 2012-05-27
Found It. I tried unity --reset but it didnt work then I went to gconf-editor again then apps>metacity>general>button_layout then changed it to wat I want then right clicked and used set as default and set as mandatory. And it Works like a charm! :guitar:

But Now I just feel stupid that I didnt check the right click menu b4.:lolflag:

---

### Post by amireldor on 2012-05-29
I faced the same problem myself. I just set the buttons to the left as a default setting as you suggested. Hope this will solve it :)

---

### Post by flyingman15 on 2012-07-12
cyb3r_sn4k3 can I thank you enough ? Just installed 12.04 on new laptop, I'm lost because of some really small details, and that was one, AND I couldn't find any solution to put my icons back at top right !! :)
THANK YOU

---

### Post by cyb3r_sn4k3 on 2012-07-13
> **flyingman15 said:**
> cyb3r_sn4k3 can I thank you enough ? Just installed 12.04 on new laptop, I'm lost because of some really small details, and that was one, AND I couldn't find any solution to put my icons back at top right !! :)
THANK YOU

Glad I could help!

---

