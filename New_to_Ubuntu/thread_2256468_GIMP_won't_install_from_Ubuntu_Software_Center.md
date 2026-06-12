---
title: "GIMP won't install from Ubuntu Software Center"
date: 2014-12-12
forum: New to Ubuntu
---

### Post by Glkanter on 2014-12-12
Hi Guys!

I have a week old installation of 14.04, and I tried to install GIMP.

I got this message:
> Failed to download package files
Check your Internet connection.
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/w/webkitgtk/libjavascriptcoregtk-1.0-0_2.4.4-1~ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/w/webkitgtk/libjavascriptcoregtk-1.0-0_2.4.4-1~ubuntu1_amd64.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/w/webkitgtk/libwebkitgtk-1.0-common_2.4.4-1~ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/w/webkitgtk/libwebkitgtk-1.0-common_2.4.4-1~ubuntu1_all.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/w/webkitgtk/libwebkitgtk-1.0-0_2.4.4-1~ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/w/webkitgtk/libwebkitgtk-1.0-0_2.4.4-1~ubuntu1_amd64.deb) 404  Not Found [IP: 91.189.91.15 80]
I'm pretty sure my ability to post this is proof that I have an internet connection.
Can anyone help?

Thanks!

---

### Post by QIII on 2014-12-12
Hello!

The 404 means the requested resource is unavailable.  One reason that might occur is if you don't have a connection.  But that's not the only reason.  In this case it seems to be on the url end, since I can't reach it either.

It may be down temporarily for updates or maintenance.  Someone may have tripped over a power cord.  Who knows.

Give it a try again in an hour or so or change from the US mirror to Main (using the Software Centre).

---

### Post by haplorrhine on 2014-12-12
QIII, is there any particular resource where we can look up those error codes?

---

### Post by CRYy0OKmKpJgc on 2014-12-12
The error codes you will see in relation to connections are simply HTTP status codes. This will explain what each of them mean. You can run in to the same error codes while browsing the Web.

[http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html)

---

### Post by Glkanter on 2014-12-13
Same result this afternoon.

I'll see if I can figure out how to get to Main.

---

### Post by Glkanter on 2014-12-13
Nothing to it!

GIMP is installed.

Thanks, everyone!

---

### Post by mc4man on 2014-12-13
Next time if this happens first just try updating  your sources which is what happened when you switched servers
The 404 was because it was trying to dl superseded packages, ex.
you were trying to get libjavascriptcoregtk-1.0-0_2.[COLOR="#FF0000"]4.4[/COLOR]-1~ubuntu1 but the current is 2.[COLOR="#0000CD"]4.7[/COLOR]-1~ubuntu1

Edit: the 1st. thing one should do after an install is update the sources

---

### Post by mörgæs on 2014-12-13
Please mark the thread 'solved'.

---

### Post by ajgreeny on 2014-12-13
For some strange reason there was an extra 80 at the end of the IP address (91.189.91.15 [COLOR=#ff0000]80[/COLOR]) that you were trying to access.

---

### Post by mc4man on 2014-12-13
> **ajgreeny said:**
> For some strange reason there was an extra 80 at the end of the IP address (91.189.91.15 [COLOR=#ff0000]80[/COLOR]) that you were trying to access.
The 80 is the port. In any event one can't retrieve what's not there anymore..

---

### Post by CRYy0OKmKpJgc on 2014-12-14
> **ajgreeny said:**
> For some strange reason there was an extra 80 at the end of the IP address (91.189.91.15 [COLOR=#ff0000]80[/COLOR]) that you were trying to access.

80 is the port number.

Never mind, I see now that someone already said that.

---

