---
title: "Restricted Drivers Manager disappeared"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by AngelfireGR on 2008-04-29
I am facing problems with my video card and i tried to install the new nvidia  drivers and i realized that my Restricted Drivers Manager disappeared from the administration menu!!! Can any one help me to get back ?

Thanks

---

### Post by Calash on 2008-04-29
It is called "Hardware" something now....I forget the exact name.  It is in the same menu.

---

### Post by AngelfireGR on 2008-04-29
> **Calash said:**
> It is called "Hardware" something now....I forget the exact name.  It is in the same menu.

It was there before 10 min with the name Restricted Drivers Manager and I did something and it is now disappeared . I searched all the menu and it is not under a different name ..probably i uninstalled it by accident and now it is disappeared .

Can any help me to have it back in order to fix my graphics card work properly ...

Thanks in advance

---

### Post by Perfect Storm on 2008-04-29
Look under System tab ---> Administration ---> Hardware Drives

(jockey-gtk is the name of the application in synaptic)

---

### Post by f37u5g0d on 2008-04-29
System > Admin > Hardware drivers is the new "restricted drivers manager."  If you go into system > preferences > main menu you can change which items show up in the applications, and system menus.  Is hardware drivers unchecked and italics?  If it is this means that it's still installed on your system its just hidden from few.  Re-check it and it will be back where it should be.

---

### Post by f37u5g0d on 2008-04-29
> **f37u5g0d said:**
> If it is this means that it's still installed on your system its just hidden from **few**.  Re-check it and it will be back where it should be.

That should be "view".  lol.

---

### Post by forrestcupp on 2008-04-29
> **AngelfireGR said:**
> I am facing problems with my video card and i tried to install the new nvidia  drivers and i realized that my Restricted Drivers Manager disappeared from the administration menu!!! Can any one help me to get back ?

Thanks

Are you still using Gutsy?  Just like others said, in Hardy, they changed the name.  But if you're still in Gutsy, you can try reinstalling it:
```
sudo apt-get install restricted-manager
```If it says it's already installed, try running **restricted-manager** in the terminal.
```
gksu restricted-manager
```

---

### Post by AngelfireGR on 2008-04-30
> **forrestcupp said:**
> Are you still using Gutsy?  Just like others said, in Hardy, they changed the name.  But if you're still in Gutsy, you can try reinstalling it:
```
sudo apt-get install restricted-manager
```If it says it's already installed, try running **restricted-manager** in the terminal.
```
gksu restricted-manager
```

I am using hardy .. I have upadted from 7.10 and I ma facing major problems with me graphics cards (nvidia 7600 gt) .I was trying with  envy or with the procedure that the site of nvidia mentions but with no result .

With your help I managed to find the restricted driver in the menu but the nvidia graphics card in not shown in it ... I am realy tired with all this mess and propably I will install 8.04 from scratch .

Thanks though for your help

---

