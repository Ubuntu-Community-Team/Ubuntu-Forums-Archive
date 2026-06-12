---
title: "getting restricted codecs to work"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by DarkPhantomBT on 2008-09-06
i tried installing ubuntu-restricted-extras so i could play my wma files
but it froze in the middle of installing
when i got back on after resetting the following came up when trying to install it

"
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

"


then when i tried to mess with it through the terminal i got this far

"

brian@brian-laptop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for brian: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
brian@brian-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
brian@brian-laptop:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0002' near line 1:
 field name `ign_Class_3_Public_Primary_OCSP_Responder.crt,' must be followed by colon
brian@brian-laptop:~$ sudo dpkg -r ubuntu-restricted-extras
dpkg: parse error, in file `/var/lib/dpkg/updates/0002' near line 1:
 field name `ign_Class_3_Public_Primary_OCSP_Responder.crt,' must be followed by colon
brian@brian-laptop:~$ 


"

somebody please help, the lives of my pink floyd songs are at stake!

---

### Post by psycosmyth on 2008-09-06
reboot after typing dpkg -a blah blah
this resets Aptitude. Sometimes a glitch will interrupt the download and you end up with broken packages. Use synaptic instead. This will ensure a better dependency grab than Apt-get.

---

### Post by DarkPhantomBT on 2008-09-06
tried rebooting and nothing happend
when i open synaptic package manager the first message shows up
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

---

### Post by wolfen69 on 2008-09-06
```
*sudo* dpkg --configure -a
```

---

### Post by anjilslaire on 2008-09-06
Looks like he tried that originally:
> 
```

brian@brian-laptop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for brian:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
brian@brian-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
***brian@brian-laptop:~$ sudo dpkg --configure -a***
dpkg: parse error, in file `/var/lib/dpkg/updates/0002' near line 1:
field name `ign_Class_3_Public_Primary_OCSP_Responder.crt,' must be followed by colon
brian@brian-laptop:~$ sudo dpkg -r ubuntu-restricted-extras
dpkg: parse error, in file `/var/lib/dpkg/updates/0002' near line 1:
field name `ign_Class_3_Public_Primary_OCSP_Responder.crt,' must be followed by colon
brian@brian-laptop:~$ 

```


---

### Post by DarkPhantomBT on 2008-09-06
yeah it won't even let me install flash player now
the same message comes up when i try to install it

---

### Post by DarkPhantomBT on 2008-09-06
alright so i went to the file in question and i tried to add the colon, but it said i didn't have permission to do that
i am so lost

---

### Post by redactech on 2008-09-06
That is corrupted cache 

Found the answer here :

[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/35534](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/35534)

and point there : 

[http://www.linuxquestions.org/questions/debian-26/apt-get-dpkg-error-files-list-file-...-missing-final-newline-271118/](http://www.linuxquestions.org/questions/debian-26/apt-get-dpkg-error-files-list-file-...-missing-final-newline-271118/)

the idea is to delete the offending file and start over

Hope it helps

---

