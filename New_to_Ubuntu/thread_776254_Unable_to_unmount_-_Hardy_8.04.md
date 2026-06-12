---
title: "Unable to unmount - Hardy 8.04"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Cris(c) on 2008-04-30
Hi everybody,

    I've been experiencing the following problem: I wanted to unmount two partitions so I went to the /etc/fstab file and commented the two lines refering to these partions. However, when I restart my laptop the partitions still are there! I have no idea what's wrong since I used to do the exact same thing with Gutsy and it always worked! I currently am using the kernel 2.6.24-16 image, though I've experienced the same problem with the 2.6.22-14 one...does someone have a clue of what's going on here? How can I fix it?

---

### Post by mikeyphi on 2008-04-30
Don't know the answer to that - had a similar problem and had to use gparted to unmount a partition!

---

### Post by Cris(c) on 2008-05-01
Nobody there with some suggestion how to overcome this problem??? it'd be greatly appreciated it!

---

### Post by sisco311 on 2008-05-01
Try to create a /etc/hal/fdi/policy/10-dont-mount.fdi file:
```
gksu gedit /etc/hal/fdi/policy/10-dont-mount.fdi
``````
[FONT=monospace]
<deviceinfo version="0.2">
  <device>
    <match key="storage.hotpluggable" bool="false">
      <match key="storage.removable" bool="false">
        <merge key="storage.automount_enabled_hint" type="bool">false</merge>
      </match>
    </match>
  </device>
[/FONT]</deviceinfo>
 
```
Read the /etc/hal/fdi/policy/preferences.fdi file.

---

### Post by Cris(c) on 2008-05-01
Thanks sisco311 for your suggestion. This is surely a stupid question, but reading the /etc/hal/fdi/policy/preferences.fdi file I notice that the code you pasted is exactly the same I already have in my preferences.fdi file. Do I still need to create the 10-dont-mount.fdi file? By the way, what are we exactly doing here? 

Thanks a lot!

---

### Post by sisco311 on 2008-05-01
> **Cris(c) said:**
> Thanks sisco311 for your suggestion. This is surely a stupid question, but reading the /etc/hal/fdi/policy/preferences.fdi file I notice that the code you pasted is exactly the same I already have in my preferences.fdi file. Do I still need to create the 10-dont-mount.fdi file? By the way, what are we exactly doing here? 

Thanks a lot!

The code in the preferences.fdi file is commented out. You can uncomment it  or create the separate .fdi file.

EDIT: I don't know to much about comments in xml files. So try to create the new file.

---

### Post by Cris(c) on 2008-05-01
> **sisco311 said:**
> The code in the preferences.fdi file is commented out. You can uncomment it  or create the separate .fdi file.

EDIT: I don't know to much about comments in xml files. So try to create the new file.

I wasn't commented out actually...

---

