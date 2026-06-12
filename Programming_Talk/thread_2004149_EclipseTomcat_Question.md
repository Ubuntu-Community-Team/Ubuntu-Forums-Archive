---
title: "Eclipse/Tomcat Question"
date: 2012-06-15
forum: Programming Talk
---

### Post by Dan Again on 2012-06-15
I just got Tomcat up and running with Eclipse and everything seems to be working more or less fine, but I'm having one annoying problem. When I point my browser to [http://localhost:8080](http://localhost:8080) I get the Tomcat Welcome page, and I can even navigate to the Document and Example pages, but if I try to go any farther than that (i.e. viewing an actual document or example or trying to access the Manager application), I get a Tomcat 404 error. Where is Tomcat looking for its local web files?

---

### Post by greenpeace on 2012-06-15
> **Dan Again said:**
>  Where is Tomcat looking for its local web files?

Hi Dan, 

I am running tomcat6 on Ubuntu 12.04 - and on my machine the actual (ie. mine) applications are deployed in:
```
/var/lib/tomcat6/webapps/
```

the host-manager application runs from here:
```
/usr/share/tomcat6-admin/host-manager
```

hope that helps!

---

### Post by Dan Again on 2012-06-15
Thanks for your reply. All the Tomcat docs, examples, etc are in /usr/share at the moment. So I went in to /var/lib/tomcat7/webapps and there was a ROOT folder in there. In the same folder as ROOT, I put the docs and examples folder, but I am still getting the same 404 error.

BTW, within /usr/share, the docs and example files are within tomcat7-docs and tomcat7-examples, respectively. Within each of those folders are folders entitled docs and examples. What I moved into /var/lib/tomcat7/webapps was just the docs and examples folders, as when I mouse over a specific document on the Tomcat Documents homepage it shows the URL as localhost:8080/docs/nameofdoc.

---

### Post by Dan Again on 2012-06-15
Bump

---

### Post by r-senior on 2012-06-16
I'd always recommend a simple unpacked archive of Tomcat in your home directory when using it for development, particularly when trying to control it from Eclipse or Netbeans. It saves all sorts of problems with permissions compared to the repository version.

EDIT - Instructions in this thread: [http://ubuntuforums.org/showthread.php?t=1606162&highlight=tomcat](http://ubuntuforums.org/showthread.php?t=1606162&highlight=tomcat)

---

### Post by Dan Again on 2012-06-16
Well, I appreciate your reply, but I'd like to try to figure out my current situation rather than getting myself involved in a new one.

The Tomcat homepage, which I am able to access, says that it is located at /var/lib/tomcat7/webapps/ROOT/index.html, but when I edit that file, I do not see a change in the localhost:8080 page. Isn't there some way I can actually see where the webpage is coming from, like from within my browser or something?

---

### Post by greenpeace on 2012-06-18
Hi!

I just tested installing tomcat7, and the index.html page suggested that I install the following packages to include the docs, examples and admin applications.

tomcat7-docs 
tomcat7-examples 
tomcat7-admin

Once they were installed I was able to access everything... have you installed these packages?

---

### Post by Dan Again on 2012-06-18
Yes, I did have those files with my previous installation. While trying to "fix" this problem, I somehow borked my Tomcat installation and had to reinstall. I followed r-senior's advice, did a manual install and now have access to he web apps.

---

