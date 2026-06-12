---
title: "new connections appear as soon i connect to internet??"
date: 2012-02-21
forum: New to Ubuntu
---

### Post by werty2010 on 2012-02-21
since a few days every time i connect to the internet my pc connects somewhere without me doing anything
note that at the moment i connect to the internet, im not having any applications running,havent configured gwibber or empathy yet

some of these connections are:
```

mil01s17-in-f19.1e100.net:https
OCSP.AMS1.VERISIGN.COM

```

im not sure if this is something i should worry about,so any help would be appreciated

---

### Post by larrypg on 2012-02-21
Hello,

Think that might be google if you have google stuff installed.

---

### Post by werty2010 on 2012-02-23
the only google stuff i have installed is chromium and google-earth
but i dont think its because of them because this started a few days ago

---

### Post by jtarin on 2012-02-23
mil01s17-in-f19.1e100.net:https...That points to the address 173.194.35.36, which is Google.It is also designated as a secure connection.

---

### Post by sadaruwan12 on 2012-02-23
This might be due to google earth not due to chromium.

Also chromium is not from google it's the open source browser that used by google to build chrome you can get chrome for ubuntu from their web site.

---

### Post by werty2010 on 2012-02-23
i think i found out what it is:
probably when i installed chromium, an addition to the "startup applications" was made 
automatically(i hope) with the command:
"/usr/bin/chromium-browser --no-startup-window"

any idea what is this command for?

---

### Post by jtarin on 2012-02-23
> **werty2010 said:**
> i think i found out what it is:
probably when i installed chromium, an addition to the "startup applications" was made 
automatically(i hope) with the command:
"/usr/bin/chromium-browser --no-startup-window"

any idea what is this command for?Don't quote me, but it seems like it loads Chromium on start-up without a window so your clicking on the icon will make Chromium seem to appear to load much faster. If you don't want the desired behavior just uncheck it or remove entirely from start-up.

---

### Post by werty2010 on 2012-02-24
ok thanks
but, if this is the reason, why even connecting somewhere(https) without me knowing it?

---

### Post by Paqman on 2012-02-24
> **werty2010 said:**
> ok thanks
but, if this is the reason, why even connecting somewhere(https) without me knowing it?

Do you have your Google account synced?

---

### Post by werty2010 on 2012-02-24
i do

---

### Post by Paqman on 2012-02-24
Probably that then. It's just phoning home to see if it needs to update itself.

It could be something else though, something like DNS caching for commonly hit websites? Modern browsers do try to stay one step ahead of you so that they're more responsive.

Bottom line: don't worry about it. It's a secure connection to a trusted source.

---

