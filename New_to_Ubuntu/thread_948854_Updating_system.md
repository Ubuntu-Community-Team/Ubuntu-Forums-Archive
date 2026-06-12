---
title: "Updating system"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by ozbolt on 2008-10-15
I've installed Ubuntu Hardy in school (teacher is great) and now I have couple of settings, programs and other stuff already on there. But for some reason I need to get newest kernel (2.6.27) and I have no idea how to do it and honnestly I am so scared to do something wrong. 
And I am searching for a way to do it. If it is just normal Synaptic installation I would be thrilled. If it is a deb package (almost sure it isn't) even better. I have not succesfully compiled anything from source so that isn't answer. If there is a way to update to Intrebit beta, go for it. 
Thankyou for answers.

---

### Post by SunnyRabbiera on 2008-10-15
Currently I would not recommend intrepid for regular use, especially in a school setting.

---

### Post by Nxion on 2008-10-15
> **ozbolt said:**
> I've installed Ubuntu Hardy in school (teacher is great) and now I have couple of settings, programs and other stuff already on there. But for some reason I need to get newest kernel (2.6.27) and I have no idea how to do it and honnestly I am so scared to do something wrong. 
And I am searching for a way to do it. If it is just normal Synaptic installation I would be thrilled. If it is a deb package (almost sure it isn't) even better. I have not succesfully compiled anything from source so that isn't answer. If there is a way to update to Intrebit beta, go for it. 
Thankyou for answers.

You are like me :) I was always nervous to compile anything. Don't be afraid of it though, compiling can be your friend :)

You say that you need the newest kernel (2.6.27). I am curious to know, it there a specific application that needs it? Or do you just want the latest and greatest.

Cheers,
Nx

---

### Post by ozbolt on 2008-10-16
I need my Wi-Fi card to work, because I cannot use wired network - it is protected. It works quite bad in Hardy (it is disconnecting every couple of minutes) and by newest kernel it should be fixed. My wi-fi card is Asus wl-167. Any how to on compiling it?

---

### Post by Keen101 on 2008-10-16
```
sudo apt-get upgrade -d
```

the code posted above should force upgrade you to the beta version, however be warned that there may be bugs. I'd try a live-cd version of the beta first if you really think it will have better wireless drivers....



if you decide to use the command:

after you use that command you may need to open the upgrade manager. It should now say that 8.10 is available to upgrade to.

---

