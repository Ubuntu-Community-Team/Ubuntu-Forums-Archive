---
title: "write Microsoft Word file"
date: 2007-12-16
forum: Programming Talk
---

### Post by Lary Grant on 2007-12-16
I have a potential client that wants a web app with a feature to write reports in Microsoft Word.  I would really prefer to develop this on the Linux web server I already have.  Is this possible or would it be best to get a Windows server if I want to take this project?

---

### Post by LaRoza on 2007-12-16
Use what the client has. If it isn't possible then tell the client.

I know Python for Windows has the ability to do such things, but not on Linux.

---

### Post by Lary Grant on 2007-12-16
> **LaRoza said:**
> Use what the client has. If it isn't possible then tell the client.

I know Python for Windows has the ability to do such things, but not on Linux.
 
The thing is... the client does not have any web server.  He wants me to provide the development and the hosting.  So I can pick whatever OS I want.  However, I already have a Linux web server (hosting several low-traffic sites), and I'd prefer to use that for this client (also low-traffic) , rather than having to get a whole new server just for this one client.  Also, I prefer working with Linux, if possible.

---

### Post by LaRoza on 2007-12-16
> **Lary Grant said:**
>  Also, I prefer working with Linux, if possible.

What does your client prefer?

---

### Post by scruff on 2007-12-16
I doubt if the client cares... If this is a web interface, then the backend would be completely transparent to any user, thus leaving this decision to the dev/admin.

---

### Post by pmasiar on 2007-12-17
You can generate ie RTF files which MS Word can import

---

### Post by slavik on 2007-12-17
good question, do you want the microsoft office 2003 document format or the microsoft office 2007 document format or what richtext format be fine?

---

### Post by Ramses de Norre on 2007-12-17
Apache's [POI project](http://poi.apache.org/) is working on libraries for reading, creating and manipulating microsoft office documents with java. I've used it to dynamically create excell files and it worked pretty good. I think their word library is still in development though.

---

### Post by Lary Grant on 2007-12-18
You are correct... the customer does not care about anything except the results.

---

