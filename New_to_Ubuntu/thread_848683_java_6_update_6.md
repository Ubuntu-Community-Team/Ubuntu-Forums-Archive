---
title: "java 6 update 6"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by nintendorulz55 on 2008-07-03
i have tried everything to get the newest java! synaptic, add/remove, and even java's site. it doesnt work. what's worse is my friend comes over with his laptop wanting me to reformat it with ubuntu again (something went wrong last time..) so i do. we get flash and then i go to gendou.com, the site i've been trying to get to work. the "plugins are required to view all the media..." bar comes down so i click it. it downloads the newest version of java and the site works. all within seconds. i tried totally erasing java from my computer and doing the same.. but it seems i still somehow have java 5. can someone help?!

---

### Post by Daveth on 2008-07-03
why are you failing to pick up java 6 in Synaptic? What happens when you type "java", and go down the list to jre6, tick it, and try to install it? Have you got all the standard Ubuntu repositories ticked in settings/admin/ software sources?

---

### Post by nintendorulz55 on 2008-07-03
there is no jre6.....

---

### Post by nintendorulz55 on 2008-07-03
wait... somehow i uninstalled restricted extras *installs and reloads* ....nope.

---

### Post by nintendorulz55 on 2008-07-03
i installed restricted extras and now i have jre6.0 the problem is, the site i want to get into needs jre6.6!!

---

### Post by nintendorulz55 on 2008-07-03
if nothing else, can someone tell me how to wipe java off my computer?

---

### Post by jamesstansell on 2008-07-04
> **nintendorulz55 said:**
> i installed restricted extras and now i have jre6.0 the problem is, the site i want to get into needs jre6.6!!

This assumes that you are running 32bit 8.04 with Firefox 3.  Other combinations may require other actions.

```
$ sudo apt-get remove icedtea-gcjwebplugin
$ sudo apt-get install sun-java6-plugin
$ sudo update-java-alternatives -s java-6-sun
```

Does that work better for you?

---

### Post by nintendorulz55 on 2008-07-04
the last code gives me this error:
E: Invalid operation update-java-alternatives

and yes, i am running 32 bit 8.04 and firefox 3.0

---

### Post by Jeff250 on 2008-07-04
He accidentally wrote 'apt-get' in the last command.  Try it without 'apt-get':
```
sudo update-java-alternatives -s java-6-sun
```

---

### Post by nintendorulz55 on 2008-07-04
well, i guess that doesnt matter! i went to java and clicked check version and i've got it! gendou's chat works now! thanks a ton, james!

---

