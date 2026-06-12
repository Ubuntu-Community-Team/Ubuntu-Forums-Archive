---
title: "uninstall program that was installed using .bin file"
date: 2013-08-31
forum: New to Ubuntu
---

### Post by Marchello_Lippi on 2013-08-31
Hi all, 

how do I uninstall program that was installed using .bin ? 

Here it says I should go to /utils/uninstall/uninstall 
[http://www.deltalounge.net/wpress/2012/05/uninstall-jdeveloper/](http://www.deltalounge.net/wpress/2012/05/uninstall-jdeveloper/)
but I can not see utils folder at my Oracle home:
 

user@comp:~$ ls /home/user/Oracle/Middleware/Oracle_Home/

cfgtoollogs  coherence  em  inventory  jdeveloper  OPatch  oracle_common  oraInst.loc  oui  wlserver

 

Any suggestions?

---

### Post by ibjsb4 on 2013-08-31
I am not saying that my way is the right way, but it gets the job done when dealing with third party software.

```
sudo apt-get remove --purge jdeveloper
```

Then clean things up

```
sudo apt-get autoremove
```

Then I would open up nautilus and look for leftovers to be removed in the 'Filesystem' by doing a search on jdeveloper.

```
gksudo nautilus
```

I have never ran/removed JDeveloper, so you may want to wait for someone to come along and verify this is ok.  System breakage is always a possibility.

[https://help.ubuntu.com/community/AptGet/Howto#Removal_commands](https://help.ubuntu.com/community/AptGet/Howto#Removal_commands)

---

### Post by Marchello_Lippi on 2013-08-31
> **ibjsb4 said:**
> 

```
sudo apt-get remove --purge jdeveloper
```



it returns error ``can not find package jdeveloper``, maybe that's 'cause it wasn't installed using ``sudo apt-get install`` command... 

Any other suggestions?

---

### Post by ibjsb4 on 2013-08-31
If you will give me a link to your download source, I will try it myself and see what the deal is :)

---

### Post by Marchello_Lippi on 2013-09-01
[**[COLOR=#000000]ibjsb4,[/COLOR]**]("http://ubuntuforums.org/member.php?u=1729120") 	 

thanks for your wish to help. 

Here is JDeveloper deinstall solution: 
[http://docs.oracle.com/middleware/1212/jdev/OJDIG/deinstall.htm#sthref18](http://docs.oracle.com/middleware/1212/jdev/OJDIG/deinstall.htm#sthref18)

---

### Post by steeldriver on 2013-09-01
If you believe there is an uninstaller there somewhere, you can try searching for it with

```
find /home/user/Oracle/ -iname '*install*'
```

or

```
find /home/user/Oracle/ -iname '*.sh'
```

or to find any executable programs or scripts (in case the name isn't *install* or *.sh)

```
find /home/user/Oracle/ -type f -executable
```

---

### Post by ibjsb4 on 2013-09-01
Ok, if we are talking the 1.8 gig download, I fear that I have to back out of downloading that one.  As it would probably take me to Christmas to remove it if the site removal instructions did not work for me.

[ATTACH=CONFIG]245890[/ATTACH]

This removal process looks pretty straight foward to me, is this what you tried?  
[ATTACH=CONFIG]245891[/ATTACH]

Edit: Solved I see, good deal :)

---

