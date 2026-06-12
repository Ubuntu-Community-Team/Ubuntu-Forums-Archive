---
title: "Cannot log into my University wifi"
date: 2014-10-12
forum: New to Ubuntu
---

### Post by Christian_Styliano on 2014-10-12
Hey guys,
Im quite new to Ubuntu and Linux, and im having some trouble logging into my university wifi, i can connect to the newtork but i cannot log into it after I have connected using my username and password.
hope you understand.

my laptop is HP pavillion dm1 4027sa

thanks,
From Christian

---

### Post by sotiris2 on 2014-10-12
Is it an open wifi network? Does it have any kind of protection (WEP , WPA) ? When you say you can't login do you mean that you have to open a browser and you get a login page instead of any webpage? If so did you have to do a similar procedure with another system (or the same laptop in windows?) Did you do it recently?

---

### Post by Christian_Styliano on 2014-10-12
yes it is an open network but when i connect to it the login page doesnt appear,but when i did it on windows the login page loaded. i have been trying to sort it out since last monday,
im using firefox so should I try chromium a go?

---

### Post by sotiris2 on 2014-10-12
So the page doesn't even load? And you can't load any other web-page I suppose? Can you run the following commands while you are 'connected'? ```
ifconfig
``````
ping -c 3 8.8.8.8
```

You could try chromium or also maybe a user-agent plugin for FF that can identify you as a Firefox/Windows user in case it's simply some filtering case.

---

### Post by wildmanne39 on 2014-10-12
Hi, click on the wireless script in my signature and follow the directions for running it and posting the results here.
Thanks

---

### Post by Vladlenin5000 on 2014-10-12
I suspect the problem is the "walled garden" definitions many of this open network plus login have. Many are so badly 'coded' as to depend on ActiveX !!!!!!

---

### Post by amanchesterman on 2014-10-12
The university I worked at, the IT department published a whole series of help pages about connecting from different operating sytems and using various browsers and email clients, and they would usually respond to requests for help within 48 hours. Does your university offer similar support? Have you contacted them?

---

### Post by Christian_Styliano on 2014-10-19
thanks for all the help, the Internet works now

---

### Post by sammiev on 2014-10-19
> **Christian_Styliano said:**
> thanks for all the help, the Internet works now

Can you please share how you worked through your problem and mark this thread as solved to possible help others.

---

