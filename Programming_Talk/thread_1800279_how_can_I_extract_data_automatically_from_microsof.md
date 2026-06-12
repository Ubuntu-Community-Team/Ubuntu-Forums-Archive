---
title: "how can I extract data automatically from microsoft outlook .pst files?"
date: 2011-07-08
forum: Programming Talk
---

### Post by zhaotianwu on 2011-07-08
I'm currently building my own database for contacts and other stuff. I have some legacy data stored in Microsoft Outlook .pst files. Since it is proprietary, I was wondering if there is any means that allows me to automatically extract all the data from a .pst file, preferably into a xml  database. Can anybody inform me of some known methods or software? Thanks.

---

### Post by Habitual on 2011-07-08
VirtualBox + MSOffice > Outlook > export contacts.

---

### Post by haqking on 2011-07-08
There are lots of tools to look inside and extract from . pst file.

here is the first link that came up in google

[http://www.nucleustechnologies.com/pst-viewer.html](http://www.nucleustechnologies.com/pst-viewer.html)

i used a similar tool years ago cant remember which one but i know there are lots out there

there are also various conversion tools out there also [http://www.convertpstfiles.com/](http://www.convertpstfiles.com/)

---

### Post by zhaotianwu on 2011-07-09
> **haqking said:**
> There are lots of tools to look inside and extract from . pst file.

here is the first link that came up in google

[http://www.nucleustechnologies.com/pst-viewer.html](http://www.nucleustechnologies.com/pst-viewer.html)

i used a similar tool years ago cant remember which one but i know there are lots out there

there are also various conversion tools out there also [http://www.convertpstfiles.com/](http://www.convertpstfiles.com/)

Thank you. By the way, does anyone think there is ANY benefit leaving data there within .pst file? I mean, is there any merit in Microsoft's .pst database schema? Database experts please give me some advice.

---

### Post by haqking on 2011-07-09
> **zhaotianwu said:**
> Thank you. By the way, does anyone think there is ANY benefit leaving data there within .pst file? I mean, is there any merit in Microsoft's .pst database schema? Database experts please give me some advice.


the merit would be using it with apps that support .pst such as outlook.

it is just PIM information, store it in whatever format you want based on how you interact with its contents or view it

---

### Post by zhaotianwu on 2011-07-10
> **haqking said:**
> the merit would be using it with apps that support .pst such as outlook.

it is just PIM information, store it in whatever format you want based on how you interact with its contents or view it



Hi haqking, thank you. I'm a newbie to databse, am I correct to say that .pst is not very popular or friendly to open source community? Considering that both its data structure and applications are proprietary. What do you think? Thanks.

---

### Post by krazyd on 2011-07-11
Install the readpst package - it includes the [pst2ldif]("http://manpages.ubuntu.com/manpages/natty/man1/pst2ldif.1.html") utility.

---

### Post by haqking on 2011-07-11
also Evolution will import .pst files so you could import your it then re-back it up to a tar.gz or mbox format

---

