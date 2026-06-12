---
title: "Inteactive .deb files"
date: 2012-05-23
forum: Packaging and Compiling Programs
---

### Post by mhjones on 2012-05-23
Hello.  I ahve been searching to my wits end and really cannot find a definitive answer to my quandry. 

I have an application that uses seperate data files called modules.  These can be included with the app installation or aquired afterward from a web site.

My question deals with the additinal modules.  I want to be able to distribute these in a .deb file.  During installation, I will need to ask the user if they want this module installed into the "default" location, /usr/share/app/modules, or the user local location, ~/Documents/modules.

It is this interactive part that I am having trouble with at the moment and how to incorporate that into a .deb.

I have considered preinst, postinst, or even just doing a .zip file with the module and a shell script.  But i cannot come to a logical conclusion, at least for me.

Thank you in advance for your time.

Any advice would be very much appreciated.

---

### Post by roelforg on 2012-05-24
You could use a preconf script to set those values.
Kinda in the same way the mysqld package asks you to set the root pass

---

