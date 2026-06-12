---
title: "Ubuntu wireless problems"
date: 2011-11-23
forum: New to Ubuntu
---

### Post by Farharbour on 2011-11-23
Every time I  attempt to use UBUNTU on  different  computers, connecting to wireless has been  a problem. I  recently  partitioned the  disk of my old  Dell  and  now the wireless will  work in  WINDOWS , but not on UBUNTU.  I  have gone through the terminal  commands given in  the help  section  a number of times to no avail. I  believe that the wireless switch on  the DELL ( FN : F2) has been  disabled in  UBUNTU , although I can turn the wireless on and off this way  in  WINDOWS.  The network  manager states "Firmware missing" and  when using the  commands in  the terminal  the STATE = message is that the  driver is not available. 

Previously,  I  have mounted WUBI on  another  computer and the  wireless stopped  working after an upgrade that  resulted in having to re-install UBUNTU entirely.  

Why is wireless connectivity so  difficult in UBUNTU? Is there an add-on  that will help avoid these  repeated and t  futile terminal sessions? Most  frustrating are instructions that suggest that you go online to  fix the problem when indeed the  computer cannot get on line. Does anyone know of how to fix this?

---

### Post by Gone fishing on 2011-11-23
If it says firmware missing its almost certainly  a Broadcom wireless adapter - they can be a problem. 

However if you connect to the Internet using a cable run ```
sudo apt-get update
``` in a terminal then run the additional drivers application it will almost certainly suggest the most suitable driver and install it.

---

### Post by Farharbour on 2011-11-27
I will  see if i can  find a cable connection somewhere.... But do you know if anyone or group is working on this  persistent  weakness in  the Ubuntu  system? One time  I let the battery run  low on  my  Ubuntu installed laptop and the wireless disappeared permanently. Wireless capability  is so important that the inability to  install and maintain wireless without advanced knowledge   seems like a major barrier to adoption of Ubuntu.

---

### Post by vangop on 2011-11-28
I'm sure it's not only ubuntu. I was trying some distros and none of them had drivers for my wifi out of the box. Not sure why. But anyway ubuntu makes it easy for the most part to install the drivers.
Now assume you're winXP user with a fresh install. How many drivers do you have out of the box? Most of your devices would need drivers downloaded and installed.

---

### Post by grahammechanical on 2011-11-28
Microsoft has solved this problem by forcing manufacturers to provide drivers in order to put a Windows Certified sticker on the product. Linux developers do not have the same power of persuasion as Microsoft does. Mostly we cannot rely on the maker to provide a Linux driver with the product. We rely on the Linux developers.

Regards.

---

