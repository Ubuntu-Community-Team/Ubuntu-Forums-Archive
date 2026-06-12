---
title: "Error in starting vnc server"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by syed mehdi on 2008-04-30
Hi Guys,
I have ubuntu 6.06 with me, i want to setup vnc server on it so that i can access the machine using clients on win/mac.
whenever i am trying to type "vncserver" on terminal i am getting this error:
"xauth:  error in locking authority file /tmp/.gdmuK2oxe"
i tried command "sudo vncserver" also, but it gave the same error.

then i tried vnc4server and it also gave the same error. please tell me why this kind of a problem is there.

Thanks & Regards
Syed

---

### Post by Ek0nomik on 2008-04-30
> **syed mehdi said:**
> Hi Guys,
I have ubuntu 6.06 with me, i want to setup vnc server on it so that i can access the machine using clients on win/mac.
whenever i am trying to type "vncserver" on terminal i am getting this error:
"xauth:  error in locking authority file /tmp/.gdmuK2oxe"
i tried command "sudo vncserver" also, but it gave the same error.

then i tried vnc4server and it also gave the same error. please tell me why this kind of a problem is there.

Thanks & Regards
Syed

If you go to System/Preferences/Remote Desktop, you can enable VNC there.

---

### Post by syed mehdi on 2008-04-30
Thats not working.

---

### Post by Ek0nomik on 2008-04-30
> **syed mehdi said:**
> Thats not working.

Care to elaborate?

Make sure you have 'Allow other users to view your desktop' and 'Allow other users to control your desktop' checked.

Then make sure you know the IP of that computer, and try connecting via a VNC Client on Mac/Windows/Linux.

---

### Post by syed mehdi on 2008-05-01
Thanks for the reply, 
I tried it but still it is not working, now when i connect from a remote location (or on localhost on same machine) using vncviewer, than a blank blinking screen is shown.
same thing when i tried on FC8 worked fine.
May be i need to change some settings in some configuration file to make it work.
[IMG]file:///C:/Documents%20and%20Settings/syed/Desktop/Kachra/blank%20vncviewer.JPG[/IMG]

Thanks & regards
syed

---

### Post by Ek0nomik on 2008-05-01
> **syed mehdi said:**
> Thanks for the reply, 
I tried it but still it is not working, now when i connect from a remote location (or on localhost on same machine) using vncviewer, than a blank blinking screen is shown.
same thing when i tried on FC8 worked fine.
May be i need to change some settings in some configuration file to make it work.
[IMG]file:///C:/Documents%20and%20Settings/syed/Desktop/Kachra/blank%20vncviewer.JPG[/IMG]

Thanks & regards
syed

I can't see the picture.  You have to upload it somewhere so people can view it.  (imageshack, photobucket, etc)

Anyways, in Ubuntu you can try:  Internet/Terminal Server Client. Then choose VNC and put in the info.  Any results?

---

