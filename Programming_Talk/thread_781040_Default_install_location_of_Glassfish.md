---
title: "Default install location of Glassfish?"
date: 2008-05-03
forum: Programming Talk
---

### Post by mpiskorz on 2008-05-03
Good day,

I'm trying to get netbeans and glassfish working together on 8.04.  I can get netbeans up and running and glassfish is working (I'm able to bring up the admin pages as well as the confirmation page that its running.)  I'm trying to add glassfish to the server section of netbeans so that I can control the server from within netbeas.  

My question: does anyone know where apt-get installs glassfish by default?  Netbeans is asking me to point it to the install location and I'm just not seeing it.  

I am new to this, so I'm still trying to get my hands around the file system layout (I'm coming from windows).

---

### Post by LaRoza on 2008-05-03
> **mpiskorz said:**
> Good day,

I'm trying to get netbeans and glassfish working together on 8.04.  I can get netbeans up and running and glassfish is working (I'm able to bring up the admin pages as well as the confirmation page that its running.)  I'm trying to add glassfish to the server section of netbeans so that I can control the server from within netbeas.  

My question: does anyone know where apt-get installs glassfish by default?  Netbeans is asking me to point it to the install location and I'm just not seeing it.  

I am new to this, so I'm still trying to get my hands around the file system layout (I'm coming from windows).

```

which glassfish

```

---

### Post by mpiskorz on 2008-05-03
glassfishv2

---

### Post by LaRoza on 2008-05-03
> **mpiskorz said:**
> glassfishv2

Type the command I gave into the terminal for the location of glassfish

---

### Post by mpiskorz on 2008-05-04
Ok, Sorry about the last reply.  

So I did that, but nothing came back.  I've learned something though.  I'm pretty sure the location is /home/username/glassfishv2.  It looks like it clears out that folder after a reboot.  Also, I guess glassfish does not automatically restart after a reboot.   So, I restarted glassfish via asadmin start-domain and now the glassfishv2 folder has a domain1 subfolder.  

I'm still having issues with getting netbeans to work with glassfish, but I've figured out my question to the default location.

Thanks for your help on this!

---

### Post by khughitt on 2008-06-10
The default document root is **/var/lib/glassfishv2/domains/domain1/docroot**. Try opening [http://localhost:8080](http://localhost:8080) to verify the install.

---

### Post by dtmilano on 2008-06-10
Try:
> $ dpkg -L glassfishv2

---

### Post by bezgoan on 2011-06-02
What is the installation location of Glassfish / Jboss in Ubuntu 11.04 ?

Thanks
Shashank.

---

