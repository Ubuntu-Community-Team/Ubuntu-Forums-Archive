---
title: "File Association in 11.10"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by sm00nie on 2011-10-16
Hi All,

When trying to associate a nzb file type to the application (sabnzbplus), I am unable to do so. I right click the file, select open with and choose Other. However, I have no area to manually enter the application, there is only a list of applications listed.

Would anyone know how I would be able to do this?

---

### Post by jtarin on 2011-10-16
Change the default "Open with" program for a file type

    In Nautilus, right click on the file and choose Properties from the menu that appears. The Properties dialog opens.

    Click on the Open With tab. A list of applications appears.

    Select the default application you want for the file type. If the application is not on the list, use the Add button to add the application to the list.

---

### Post by sm00nie on 2011-10-16
> **jtarin said:**
> Change the default "Open with" program for a file type

    In Nautilus, right click on the file and choose Properties from the menu that appears. The Properties dialog opens.

    Click on the Open With tab. A list of applications appears.

    Select the default application you want for the file type. If the application is not on the list, use the Add button to add the application to the list.
Thanks for the response, but the "Add" button is grayed out and only becomes available for clicking when I select an application that is already on the list.

I am unable to select an application that is NOT listed on the list.

---

### Post by jtarin on 2011-10-16
Then try opening Nautilus as "root" and using the procedure.
```
gksudo nautilus
```

---

### Post by sm00nie on 2011-10-16
> **jtarin said:**
> Then try opening Nautilus as "root" and using the procedure.
```
gksudo nautilus
```

Nope, still no option/field to set a custom application. This is just weird :/

---

### Post by beew on 2011-10-16
Hi,

The solution suggested by jtarin no longer works in 11.10 (based on gnome 3)because the gnome devs think that it is a brilliant idea to remove such a vital option. The big idea seems to be that if the apps are not able to figure out the correct MIME type then it is too *** bad for the users.

Check out this link for a workaround 
[http://ubuntuforums.org/showthread.php?p=11288489](http://ubuntuforums.org/showthread.php?p=11288489)

---

### Post by sm00nie on 2011-10-16
> **beew said:**
> Hi,

The solution suggested by jtarin no longer works in 11.10 (based on gnome 3)because the gnome devs think that it is a brilliant idea to remove such a vital option. The big idea seems to be that if the apps are not able to figure out the correct MIME type then it is too *** bad for the users.

Check out this link for a workaround 
[http://ubuntuforums.org/showthread.php?p=11288489](http://ubuntuforums.org/showthread.php?p=11288489)
Ahh thank you for the link beew, that worked :).

Maybe when 3.3 or 3.4 comes out it'll fix this annoying issue.

---

### Post by jtarin on 2011-10-16
Thanks for pointing out another reason for me not to upgrade to 11.xx.
Let's not forget to thank the Ubuntu devs for following blindly.

---

