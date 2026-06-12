---
title: "Adobe not allowing me to open secure pdf"
date: 2012-10-02
forum: New to Ubuntu
---

### Post by gfar on 2012-10-02
when I type in the password for a secured adobe pdf, I receive a message that says your security will not allow you to open this pdf and that I must first  allow security to do so. Can anyone help thanks in advance?

---

### Post by daslinkard on 2012-10-02
Have you tried using the terminal to open the pdf?  Such as if the name of the pdf is:

test.pdf

You can try this command:
```

evince test.pdf
```

Let me know if this opens it for you.

---

### Post by gfar on 2012-10-03
Yea it opened the pdf but it still wont allow me to view it .... here is what I got ....


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=225019&stc=1&d=1349277578[/IMG]

---

### Post by Mark Phelps on 2012-10-03
This is a "Wiley" publication -- and I'm not aware of it being available for free - legally.

If you got it through torrents, that's piracy and we don't support that on these forums.

So ... you should go back to site where you PURCHASED this ebook and tell them they need to (1) provide you a download link to an unprotected PDF version, or (2) provide you the password needed to open this.

---

### Post by daslinkard on 2012-10-03
My wife had this happen with one of her Online classes....she had to put in her security credentials for the school to unlock the PDF.

---

### Post by gfar on 2012-10-03
Hi mark no I did not get this illegally It is for my phoenix online class I just changed my operating system to ubuntu from windows and now I am unable to open the document the error message i am getting is after i type in my username and password. I am trying to figure out if I have some type of firewall or something in my defaults from allowing me to open my pdf. Thanks

---

### Post by gfar on 2012-10-03
Yes it is for one of my online classes at phoenix I typed in my password and username but it wont allow me to open, I am thinking maybe default settings or a firewall is restricting me access. My question is how do I turn these things off to allow the document to open. Thanks

---

### Post by windscape on 2012-10-03
Hi,

The eBook may not be supported under Linux, as a lot of DRM content is not. One option would be to try installing Adobe Reader in WINE and see if that works. Another would be to install Virtualbox or libvirt and install Windows in a Virtual Machine and then Adobe Reader in Windows. A third option would be to contact your online class professor/instructor and ask them if reading the eBook in Linux is supported or not.

After thinking about this a bit more, click the Edit menu and then Preferences. Check the settings for Javascript, Security, and Security (Advanced).

---

### Post by daslinkard on 2012-10-03
I looked on Google and you are not the first person to have this issue....one work around is to go to the Ubuntu Software Center and download XPDF.

After you have XPDF downloaded try to open the UOP PDF file then.  Let me know if this fixes it for you.

---

### Post by brdavid on 2013-07-03
> **gfar said:**
> when I type in the password for a secured adobe pdf, I receive a message that says your security will not allow you to open this pdf and that I must first  allow security to do so. Can anyone help thanks in advance?

You must go to the Preferences under the Edit drop-down menu in Adobe reader, then scroll down and select Trust Manager.  The default setting is to block access to external websites.  To change this, select Change Settings and allow access to external sites.  This enables Adobe reader to download the DRM from the publisher's server and you should be good to go.

---

