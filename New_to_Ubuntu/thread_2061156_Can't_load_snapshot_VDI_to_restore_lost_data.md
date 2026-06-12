---
title: "Can't load snapshot VDI to restore lost data"
date: 2012-09-21
forum: New to Ubuntu
---

### Post by just4kixx on 2012-09-21
I had posted previously about trying to access my VM. I've managed to get back into my VM but can't reload any of my previous VDI's to restore most of the files that were in my  Windows XP. When I try, this is the error I get:

 Failed to open the hard disk /home/robert/VirtualBox VMs/Windows XP/Snapshots/{daef7a85-9327-489e-b057-830a84a31bd8}.vdi.
 Parent medium with UUID *{6c512f52-1390-4e36-9c6f-e31f9724fd99}* of the medium '/home/robert/VirtualBox VMs/Windows XP/Snapshots/{daef7a85-9327-489e-b057-830a84a31bd8}.vdi' is not found in the media registry ('/home/robert/.VirtualBox/VirtualBox.xml').


Details:
 Result Code: 
  NS_ERROR_FAILURE (0x80004005)
   Component: 
  Medium
   Interface: 
  IMedium {9edda847-1279-4b0a-9af7-9d66251ccc18}
   Callee: 
  IVirtualBox {d2de270c-1d4b-4c9e-843f-bbb9b47269ff}


Can anyone tell me how I can fix this? I have some very vital data that I need. It seems that it's just a matter of editing  the XML file,  but I don't know exactly what I need to do.

---

### Post by NikTh on 2012-09-21
Hi , 
I don't know how to solve your problem , but I post for a suggestion . 

My suggestion is to make a post in VirtualBox forums too. [https://forums.virtualbox.org/](https://forums.virtualbox.org/) 

Hopefully they will be able to help you. 

Also take a look here : [https://forums.virtualbox.org/viewtopic.php?f=6&t=46264](https://forums.virtualbox.org/viewtopic.php?f=6&t=46264) , similar problem with yours.

Thanks

---

### Post by just4kixx on 2012-09-21
thank you! I had found that forum at work, but hadn't had a chance to save the link and couldn't find it when I got home.  I look at the second link as well, and it does look similar.

ETA... and double, triple, thanks!!!!! - reading that link post helped me figure out what I needed to do - I have my files back!! [Includes a novel that I'm writing/revising for publication]

---

### Post by NikTh on 2012-09-21
OK! 

Glad you solved it . 

**Please use the thread tools and mark as solved. **

Thanks

---

