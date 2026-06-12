---
title: "[Python] Checking if ubuntu is connected to *given* wireless network"
date: 2009-10-05
forum: Programming Talk
---

### Post by exutable on 2009-10-05
Hey guys,

I am working on a script that logs into my schools hotspot when it connects.  I have the http-request done, that was pretty easy but how would I check if ubuntu is connected to the AAU-INS wireless network?

Here is my code so far(just the http request):
```
#! /usr/bin/python

import urllib
import urllib2
import sys
import cookielib
import hashlib

#Accept cookies to browse telmore website
cookieJar = cookielib.LWPCookieJar()
opener = urllib2.build_opener(urllib2.HTTPCookieProcessor(cookieJar))

#Add headers
opener.addheaders = [('User-agent', "Mozilla/5.0")]

#Accept arguments for username and password
username = sys.argv[1]
password = sys.argv[2]

#Url request
url = "https://hotspot.tnb.aau.dk/nwa_auth/action/smb"

#Fill the forms with the username and password arguments
form = { "auth_smb_user" : username,
         "auth_smb_pass" : password }

#Encode the form and create request         
encodedForm = urllib.urlencode(form)
request = urllib2.Request(url, encodedForm)
page = opener.open(request)
contents = page.read()
```


Thanks,

Dane

---

### Post by kavon89 on 2009-10-05
```
iwconfig wlan0 | grep -o AAU-INS
```

---

### Post by j7%&lt;RmUg on 2009-10-05
> **kavon89 said:**
> ```
iwconfig wlan0 | grep -o AAU-INS
```

I think he wants to do that IN his code.

---

### Post by kavon89 on 2009-10-05
> **nisshh said:**
> I think he wants to do that IN his code.

Oh, right. Does python have the ability to execute commands in the system's shell and get the output?

---

### Post by Reiger on 2009-10-05
I may be missing something of course, but I assume your script is supposed to be run &#8216;on connect&#8217;: it should not automatically connect your machine to the wireless network by itself.

If this is simply a case of &#8216;I want it to work, and don't care much how&#8217;: you could use WICD as network manager. WICD allows you to run scripts on &#8216;events&#8217; like "lost connection", "connected" etc on a per network basis: so all you would have to do is configure WICD to run your script once it is connected to your university network.

---

### Post by exutable on 2009-10-05
> **Reiger said:**
> I may be missing something of course, but I assume your script is supposed to be run ‘on connect’: it should not automatically connect your machine to the wireless network by itself.

If this is simply a case of ‘I want it to work, and don't care much how’: you could use WICD as network manager. WICD allows you to run scripts on ‘events’ like "lost connection", "connected" etc on a per network basis: so all you would have to do is configure WICD to run your script once it is connected to your university network.

Well I do want it to just work but if there is a better way or maybe a more built in way then I would like to use that.  Yes it is "on connect"

---

### Post by nbo10 on 2009-10-05
> **kavon89 said:**
> Oh, right. Does python have the ability to execute commands in the system's shell and get the output?

Check out the pexpect module.

---

