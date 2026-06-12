---
title: "tranfering files from Hardy to XP"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by Old Jimma on 2008-11-07
Hi All:

I'm having trouble transfering files from Hardy to XP.

On my XP machine, I've right clicked on my C: drive and checked the boxes that allow file sharing, and created a folder on c: and right clicked and checked boxes to allow sharing.

On my hardy machine, I go to places > network and I see the icon for Windows Network. 

Then I click on the Windows Network icon, and I see the windows domain icon that my XP machine belongs to.

When I click on that icon, I can't get in.

I've turned off the Windows firewall... and still no luck.

Can anybody help me out?

Thank you!
Phil Smith
Duluth, GA

---

### Post by _sAm_ on 2008-11-07
I think you need smbfs to use smb shares, so try;

> sudo aptitude install smbfs

Then try again to browse the shares.

---

### Post by Old Jimma on 2008-11-07
Hi Sam:

Thanks for your reply.

I did the installation and it went smoothly.

However, when I do: places > network and then click on the Windows network icon, it can't find the XP computer.

Any further help you may provide will very gratefully received!

Thanks,
Phil Smith
Duluth, GA

---

### Post by _sAm_ on 2008-11-07
I tried myself and same thing happen, I cant see the shares:-/

But if I go to: Places > Connect to Server
And enter;
Service type: Windows Share
Server: enter the hostname of the XP box
Share: enter the name of the share
Username: Enter your username on XP box

Hit Connect, type in your password 
(Or in Nautilus press Ctrl+L and type; smb://hostname/sharename  ).

Did that work?

Its also possible to mount the Windows share with cifs on your system, witch works great.

---

