---
title: "noob needs help with metasploit"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by amir1979 on 2008-04-23
hi all i need help on installing metasploit 3.0 please...   iv read a lot of instructions and iv tried a lot of different methods but i still cant get the program to function...   

when i type in  ./msfconsole  i receive the following

bash: ./msfconsole: No such file or directory

as far as i know i have all the libraries for ruby and etc that it requires...  can someone please help me with this...   
 
i know there are many many topics on this but im a noob and they havent worked for me so im asking for mercy and help from the linux gods :)   

PS  im brand new to linux/ubuntu i just installed it and began using it a couple of days ago...

---

### Post by Nepherte on 2008-04-23
Here's some installation instructions on the metasploit website:
[http://metasploit.com/dev/trac/wiki/Metasploit3/InstallUbuntu](http://metasploit.com/dev/trac/wiki/Metasploit3/InstallUbuntu)

---

### Post by amir1979 on 2008-05-01
hi sry about the delay in reply...    i have looked at those instructions and i have tried to install it that way and it didnt work it said  

sudo apt-get install ruby libruby rdoc
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package libruby
etc.. for the rest     

again as i said im a noob!  sry im new to linux based systems   any help would be greatly appreciated.

---

### Post by Monicker on 2008-05-01
> **amir1979 said:**
> hi sry about the delay in reply...    i have looked at those instructions and i have tried to install it that way and it didnt work it said  

sudo apt-get install ruby libruby rdoc
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package libruby
etc.. for the rest     

again as i said im a noob!  sry im new to linux based systems   any help would be greatly appreciated.

Those instructions will work, with some slight modifications.  Just do a search on libruby in apt (apt-cache search libruby), and it will pull up the proper package name to install.  Do the same for any other packages where it says not found.

I had no problems getting metasploit to work under Hardy Heron doing it that way.  Metasploit is designed for people who have some experience with linux, so you may have to put in a little more work when using it.

---

### Post by amir1979 on 2008-05-01
thanks im looking into how to install it properly... damm this **** is complicated to me lol

---

### Post by bradmayne04 on 2010-03-09
yeah it is a pain in the ***!  did you ever get it going?    I have the console working but not the GUI.  I've been using the web interface instead.  Hit me up it would be cool to see what someone else is doing with metasploit.

---

### Post by overdrank on 2010-03-09
Hi and welcome. No need to bump a 2 yr old thread :) Thread closed

---

