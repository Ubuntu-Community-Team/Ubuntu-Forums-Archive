---
title: "Connect to Printer on Vista computer"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by halohunter on 2008-08-31
How do I connect to my shared printer on a vista computer? The printer is a HP Photosmart 7660. 

I did find a driver here: [http://openprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_7660](http://openprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_7660) and downloaded the .ppd file but I have no idea what to do with it.

Thanks for the help!

---

### Post by InfinityCircuit on 2008-08-31
Just go to System -> Administration -> Printing, and hit "Add New Printer."  Select to add one through a SMB share with a Windows computer.  Now browse for the printer.  If it shows up, you're done--hit next, pick the driver from the list (or install it yourself), and it's set up.  

If it doesn't show up then in the URI field, you need to know four things:

1) Password and login for the Vista computer if the printer is on a password-protected share.

2) Name of the windows workgroup (workgroup by default I believe)

3) Name of the Vista machine

4) Name of the printer on the Vista machine.

Then type the following in the URI field and pray:

smb://workgroup/machine/printername

And a password if needed.

---

### Post by halohunter on 2008-08-31
Thanks it works!! I can't believe ubuntu actually works with Vista. Ubuntu has come far.

---

### Post by Durd3n on 2008-09-02
Is there anyway to do this via command line?  I have 8.04 Server and I need to connect to a Vista printer.  I tested this and it works via Gnome/GUI on a different computer.  I don't have X installed for the server.  Thanks.

---

