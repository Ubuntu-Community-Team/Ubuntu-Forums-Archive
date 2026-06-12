---
title: "looking to add upload option to web site -- what to use?"
date: 2015-07-14
forum: Programming Talk
---

### Post by tross2 on 2015-07-14
I'm looking to add upload file option to my web site and would like to know what to use?
I would like to have a link on the site to allow users to upload images, files, etc...

could I use owncloud or should I use something else. ( some ftp pgm, or the like)

I would like to use a very secure pgm. 
I know that ftp could be a security risk, but I know very little about owncloud.

I've seen some videos about installing owncloud or ftp, but 
if there a any video link about using, securing, and/or overviews about ftp vs owncloud. ( I would Appreciate it )

also someone mentioned that one of the Cloud pgms (not sure which) uses that companies server connect to my cloud server ( similar to a VPN connection)
I really don't want to go thru anyone to get to my server,( well, we still need to use internet providers but that can't be helped) 

Tia

Tim

---

### Post by Lars Noodén on 2015-07-14
One easy way is to use the SFTP server that is built into the package OpenSSH-server.  It will allow you to upload and download fairly securely and is supported by FileZilla and even the many native file managers found in Ubuntu and its variants.

---

### Post by tross2 on 2015-07-14
I would like to have a link on the website start the upload process, could a link from the website be used to start the sftp process?

---

### Post by sandyd on 2015-07-14
Not a Ubuntu support question, moved to *Programming Talk*

---

### Post by Lars Noodén on 2015-07-14
> **tross2 said:**
> I would like to have a link on the website start the upload process, could a link from the website be used to start the sftp process?

Not out of the box, but the web browser can be set to launch Nautilus or some other SFTP-capable application when a URL starting with sftp:// is found.

---

### Post by SeijiSensei on 2015-07-15
You can write [simple uploading scripts with PHP]("http://www.w3schools.com/php/php_file_upload.asp").  If you have any programming experience, you might consider this route.

---

### Post by tross2 on 2015-07-16
I'll give this a look. I've started using php and this might be a good option.

---

