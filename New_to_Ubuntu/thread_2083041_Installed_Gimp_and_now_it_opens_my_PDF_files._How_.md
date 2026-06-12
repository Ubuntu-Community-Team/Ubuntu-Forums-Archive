---
title: "Installed Gimp and now it opens my PDF files. How do I get back?"
date: 2012-11-11
forum: New to Ubuntu
---

### Post by brawd on 2012-11-11
Hi All,

I've just installed 12.04 and due to my interests I installed Kicad EDA.
After that I installed Gimp. Now Gimp opens my Kicad Help PDF files. Previously in 10.04 something else opened them.

Anyone know what that was and how I use it again?

regards,

---

### Post by newb85 on 2012-11-11
Right-click a .pdf file and click Properties.  Got to the "Opens With" tab.  Select the program "Document Viewer" and hit "Set as Default".

---

### Post by brawd on 2012-11-11
Easier said than done. I can't find a PDF and the search brings up nothing. But wait! The thought occurs to me to go online and download a PDF and use that.

Thanks for the help.

---

### Post by brawd on 2012-11-11
Yep that worked.

---

### Post by brawd on 2012-11-11
No it didn't!

In a moment of overconfidence I assumed it would work before actually trying to read the Kicad help file.

It turns out that Gimp will not give up it's hold on PDF files.

I downloaded a PDF at random from the web and checked permissions where it indicated that Document Viewer would have the honour of opening this type of file.

In practice Gimp is the one that opens it.

So, after going to Permissions and Open With, I am denied - by a greyed out selection - setting Document Viewer to always open this type of file.

More help/knowledge/goodwill required please.

For the curious the downloaded PDF concerned Urinary tract infections and though I haven't read it I'll pass it on if requested.

regards,

---

### Post by Abhinav Kumar on 2012-11-11
Hi,
Check if you have permissions to use evince.
```

ls -l /usr/bin/evince

```

If not change the permissions .

Regards,
Abhinav

---

### Post by brawd on 2012-11-12
Sorry but I don't understand evince at the moment, that's why I'm in Absolute beginner. But rest assured I shall try to track that down and see what it offers.

I did eventually find where the Kicad Help PDF is stored. Would you believe my document folder!

It opens perfectly well with document viewer from that folder so I think it's a particular Kicad problem, not a Ubuntu problem. I have discovered a Kicad users group in Yahoo so I'll head over there and see if they have something on it.

Many thanks to all who spent time on this your help is greatly appreciated.

regards,

---

### Post by ratcheer on 2012-11-12
This is a good thread. I have a similar problem, except it is Libre Office that has taken over my PDF's. I'll try the suggestions and see if any of them work.

Tim

---

### Post by philinux on 2012-11-12
> **ratcheer said:**
> This is a good thread. I have a similar problem, except it is Libre Office that has taken over my PDF's. I'll try the suggestions and see if any of them work.

Tim

Check in here to see what is allocated to pdfs.

```
cat  /usr/share/applications/mimeinfo.cache | grep pdf
```

---

### Post by ratcheer on 2012-11-12
> **philinux said:**
> Check in here to see what is allocated to pdfs.

```
cat  /usr/share/applications/mimeinfo.cache | grep pdf
```

Interesting. Here is what it says:


```
cat  /usr/share/applications/mimeinfo.cache | grep pdf
application/pdf=gimp.desktop;gimp.desktop;evince.desktop;
application/x-bzpdf=evince.desktop;
application/x-gzpdf=evince.desktop;
application/x-xzpdf=evince.desktop;
image/pdf=display.im6.desktop;
```Tim

PS - Mine is fixed with the original suggestion of going to a pdf file and right-clicking Properties. It said open with Libre Office Writer. I changed that to Document Viewer and, for the time being anyway, it is now opening pdf's, properly.

---

