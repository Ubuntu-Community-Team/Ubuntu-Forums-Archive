---
title: "Difficulty creating a virtual network"
date: 2015-02-12
forum: New to Ubuntu
---

### Post by anthonymccracken89 on 2015-02-12
Hi All, 
I hope someone can help me please. :)
i'm attempting to create a virtual network following the below document for testing and practicing with Linux etc....
[https://sandilands.info/sgordon/creating-a-virtual-network-of-linux-guests-using-virtualbox#new_vm](https://sandilands.info/sgordon/creating-a-virtual-network-of-linux-guests-using-virtualbox#new_vm)

However i'm stuck when trying to edit the following /etc/udev/rules.d/70-persistent-net.rules it is empty when from what i can understand it is meant to have some information inside that i can modify according to the document.

To edit this document i'm using the following command 
sudo nano /etc/udev/rules.d/70-persistent-net.rules

Does anyone know why this is and how i get the system to add the entries?

Thanks
Anthony

---

### Post by ian-weisser on 2015-02-12
The instructions tell you what the content of that rules file is supposed to be.
Why not simply copy-and-paste it into the rules file?

---

### Post by anthonymccracken89 on 2015-02-12
I didnt think it would be as simple as that, just having a few issues trying to copy and paste Virtual box, so once i have sorted that i will try and hopefully it will work! :)

---

### Post by SeijiSensei on 2015-02-12
Shut down the virtual machine, then right-click the entry for the VM in the VirtualBox manager and pick Settings.  If you browse around, you'll see an option to enable the shared clipboard.  Choose "bidirectional," then start the machine.  Any better?

---

### Post by anthonymccracken89 on 2015-02-13
I have tried that and it didnt work :( i have been doing a bit of googling on the problem and apparently if i install Guest additions it should work???

---

### Post by SeijiSensei on 2015-02-13
Perhaps.  I always install the "Extension Pack" as the "Guest Additions" are now called.  Too many things like USB ports and advanced video modes won't work without them.

---

### Post by anthonymccracken89 on 2015-02-16
I will try this tonight and let you know how it goes :) Thanks

---

