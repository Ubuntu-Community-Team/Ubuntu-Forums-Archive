---
title: "how to disable sleep when laptop lid is close"
date: 2013-06-01
forum: New to Ubuntu
---

### Post by totoy on 2013-06-01
Can someone help pls... I installed ubuntu server on my old laptop (Dell 430). I wan't it to keep on running 
after closing the lid. As normal laptops do when their lids are close it turns off all the processes and goes to sleep. I just wan't to be able to access 
my server 24/7 even if the lid is closed and the back light off.
I found some instructions over the net but doesn't work for me like for this ex:
editing a file "lidbtn"...which in my system is empty, nothing to edit.
(edit /etc/acpi/events/lidbtn)
suppose to edit this...


# /etc/acpi/events/lidbtn 
 # Called when the user closes or opens the lid 
 event=button[ /]lid # comment this out with a # at the beginning 
 action=/etc/acpi/lid.sh # same here

---

### Post by cmcanulty on 2013-06-01
system settings-power choose do nothing for both drop down boxes

---

### Post by ajgreeny on 2013-06-01
You need to remove, or better, just make the file /etc/acpi/lid.sh non executable with ```
sudo chmod -x /etc/acpi/lid.sh
```

---

### Post by totoy on 2013-06-02
Thanks "a[COLOR=#000000]jgreeny" for the advice... instead of the path you suggested I did this:

sudo chmod -x /etc/acpi/events/lidbtn[/COLOR]

---

