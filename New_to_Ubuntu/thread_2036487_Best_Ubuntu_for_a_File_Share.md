---
title: "Best Ubuntu for a File Share"
date: 2012-08-02
forum: New to Ubuntu
---

### Post by Living2007 on 2012-08-02
I'm tossing up between either a Server Verison, or a desktop verison for a network fileshare on a Windows Network, primarly accessed by iMacs.
 
I want to use minimal system resources, but use a desktop environment when other admins (who don't know the CLI commands) use it.
 
Our Windows Machines also need access to it so we can monitor the data storage.
 
What is the best Ubuntu to use, and what is the best File Sharing protocol to use?

---

### Post by papibe on 2012-08-02
Hi Living2007.

In terms of services, there's no significant difference between any version of Ubuntu.

The only difference will be that the GUI versions will require more hardware (mainly RAM).

Although there are specialty windows manager that use significant less memory that the known players (xmonad, awesome, etc), the easiest solution would be to install either Xubuntu or Lubuntu.

Just my thoughts.
Regards.

P.S.: I'm not well verse on Macs, but for what I can tell, NFS will be a suitable solution.

---

### Post by Paqman on 2012-08-02
> **Living2007 said:**
> 
I want to use minimal system resources, but use a desktop environment when other admins (who don't know the CLI commands) use it.


What about [Webmin]("http://www.webmin.com/")?

---

### Post by Living2007 on 2012-08-02
From my last experience with Ubuntu Server, I had issues with login and no interface. Maybe it was just the way I installed it...

---

### Post by Dawnbandit on 2012-08-02
> **Living2007 said:**
> I'm tossing up between either a Server Verison, or a desktop verison for a network fileshare on a Windows Network, primarly accessed by iMacs.
 
I want to use minimal system resources, but use a desktop environment when other admins (who don't know the CLI commands) use it.
 
Our Windows Machines also need access to it so we can monitor the data storage.
 
What is the best Ubuntu to use, and what is the best File Sharing protocol to use?
You could always use Lubuntu, its used LXDE which doesnt take that much CPU to run.

---

### Post by mapes12 on 2012-08-03
> What about Webmin?I read somewhere that Canonical dropped support for Webmin way back at version 5 because of compatibility issues with how Webmin handles packages.

If you're installing a basic LAMP server then Fluxbox has some good write ups for Admins that need a GUI Window Manager.

---

### Post by Paqman on 2012-08-03
> **mapes12 said:**
> I read somewhere that Canonical dropped support for Webmin way back at version 5 because of compatibility issues with how Webmin handles packages.


Indeed [they did]("https://help.ubuntu.com/community/WebMin"). However, Webmin is tested on Ubuntu and works, third party sources will be disabled on upgrade these days anyway, so it's unlikely to cause b0rkage, which is what they seemed to be concerned about in the first place.

---

### Post by mlentink on 2012-08-03
Webmin runs without a problem, I've used it since 2006, never encountered one.

---

### Post by Primefalcon on 2012-08-03
Run a server enviro and read this if you really need a gui: [https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

---

