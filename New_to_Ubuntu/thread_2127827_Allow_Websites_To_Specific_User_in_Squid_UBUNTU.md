---
title: "Allow Websites To Specific User in Squid UBUNTU"
date: 2013-03-21
forum: New to Ubuntu
---

### Post by kaushikvarma on 2013-03-21
[h=2][SIZE=2]please forgive me if there is any mistakes in my message.  
this is my  first[SIZE=2] message[/SIZE] to "ubuntuforms.org" 
[SIZE=2]you people [/SIZE]can sole my problem. 
what i am  facing in my office.  
_my problem_ :
 i have 400 system's in my office. and  we are using squid proxy with full secure. but "i want to give full  access for specific user" not for particular ip-address. i hope you  people will respond for this mail.    please guide me how to give full  access for specific user in "SQUID" 				.[/SIZE][/h]

---

### Post by SeijiSensei on 2013-03-21
I don't think there is a simple solution to this problem.  I manage a Squid transparent proxy for a client, and we control access by IP address.

One possible approach is to set up another parallel instance of Squid on a different port with [authentication]("http://wiki.squid-cache.org/Features/Authentication") and have the blessed user configure the browser's proxy settings to use that port then log in.

---

### Post by kaushikvarma on 2013-03-21
thanks for your reply and I'll go throw it.
& may be i need better suggestions.

---

