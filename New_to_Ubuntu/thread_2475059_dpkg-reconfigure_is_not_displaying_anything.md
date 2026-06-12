---
title: "dpkg-reconfigure is not displaying anything"
date: 2022-05-15
forum: New to Ubuntu
---

### Post by mrmike512 on 2022-05-15
Hello, i have Ubuntu 22.04 just recently installed
i want to change my display manager from gdm3 to another manager.  I tried running the command from terminal:
 
    sudo dpkg-reconfigure gdm3

i was expecting the terminal to show the package configuration display, but instead it just goes to the next line in the terminal and nothing happens.  
I also tried this with a few other things:

   sudo dpkg-reconfigure wireshark
   sudo dpkg-reconfigure python3

neither one of these displays the package configuration display either.

what could be wrong?

---

### Post by Impavidus on 2022-05-16
Most packages don't ask any configuration questions. I don't know about gdm3. It's not on my Xubuntu system.

---

### Post by mrmike512 on 2022-05-16
well i think the reason it wasn't working like i thought was because there was no other display manager option installed.  

sudo apt install lxde

then it shows the package configuration display as a i expected where i can select between gdm3 and lxde.  after a reboot, i can also run the command 

sudo dpkg-reconfigure gdm3 

and now it shows the package configuration options for display manager like i thought when i made the post.  So it's good now.

---

