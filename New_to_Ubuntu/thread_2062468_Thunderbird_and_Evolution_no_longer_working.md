---
title: "Thunderbird and Evolution no longer working"
date: 2012-09-25
forum: New to Ubuntu
---

### Post by basboos on 2012-09-25
Hello :-)

I launched Thunderbird today and got the message that I had exceeded my IMAP server connections. This has happened once before, and by reducing the number of allowed IMAP connections and also by deleting a bunch of .msf files I was able to get it working again. No such luck this time.

I even tried Evolution, but I get a message saying it is not online, even though it is :confused:.

These problems began once I upgraded to Ubuntu 12.04, so I was wondering whether anyone else had encountered this problem, and if they knew of a solution to this:?:

Thank you!

---

### Post by basboos on 2012-09-25
by removing my email account and then setting it up again it begins to work again. Does anyone know why this could happen and if there is an easier way to solve this?

thanks :)

---

### Post by daslinkard on 2012-09-25
This is normally due to the configuration of the IMAP server (such as  Courier-IMAP) which may be configured to only allow a certain number of  connections per IP address. Fortunately you can usually solve the issue  in Thunderbird by changing the number of cached connections in the  advanced settings.

Call up Thunderbird, ```
go to your Account Settings.
``````

Click on Server Settings
``````

Select Advanced Tab
``````
Change Maximum number of server connections to cache to 1
```

Select OK and I would recommend restarting Thunderbird

---

### Post by basboos on 2012-09-26
> **daslinkard said:**
> This is normally due to the configuration of the IMAP server (such as  Courier-IMAP) which may be configured to only allow a certain number of  connections per IP address. Fortunately you can usually solve the issue  in Thunderbird by changing the number of cached connections in the  advanced settings.

Call up Thunderbird, ```
go to your Account Settings.
``````

Click on Server Settings
``````

Select Advanced Tab
``````
Change Maximum number of server connections to cache to 1
```Select OK and I would recommend restarting Thunderbird

Thanks daslinkard :) I actually did do that yesterday, several times and got no joy :(

---

### Post by basboos on 2012-09-28
it happened again today >_<

has anyone encountered this problem before? 

thanks :)

---

