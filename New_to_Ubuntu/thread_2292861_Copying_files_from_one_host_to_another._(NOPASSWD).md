---
title: "Copying files from one host to another. (NOPASSWD)"
date: 2015-08-31
forum: New to Ubuntu
---

### Post by martin-lee.cusick on 2015-08-31
What is the preferred method of coping a file from another machine without using a password?

An example:

Client machine checks server machine to see if it's process suite is up to date. If it is not, it copies the latest tar.gz from the server.

For simplicity the server/clients both have the same user.

Thanks.

---

### Post by Geoffrey_Arndt on 2015-08-31
Simplest method . . . . dropbox sync works wonders (as does google drive, azure, spider oak, etc. etc).    Less work by far than a local file server.

Above presumes casual or basic home "buntu" user with a handful or less of machines.

---

### Post by Habitual on 2015-08-31
> **martin-lee.cusick said:**
> What is the preferred method of coping a file from another machine without using a password?scp with ssh keys.

---

### Post by martin-lee.cusick on 2015-08-31
> **Geoffrey_Arndt said:**
> Simplest method . . . . dropbox sync works wonders (as does google drive, azure, spider oak, etc. etc).    Less work by far than a local file server.

Above presumes casual or basic home "buntu" user with a handful or less of machines.


I'm sorry, I do not mention that there is no internet access; this is behind a firewall. Somewhat of an industrial setting.

---

### Post by Habitual on 2015-08-31
you can still scp from behind a firewall in an "industrial setting". Internet or not.
Private LANs use scp all the time.

---

### Post by HermanAB on 2015-08-31
Anonymous FTP has done that successfully since about 1970.

---

### Post by Geoffrey_Arndt on 2015-09-01
If no external internet allowed, and because you want automated copy of most current file (syncing), perhaps you should consider an internal cloud such as ownCloud:   [https://owncloud.org/](https://owncloud.org/)

Or - - software such as advanced "groupware" . . which these days means a wiki.   These wikis provide an easy way to see all the documents that have been updated within a specified time period, allowing for access to the latest data.

See these . . . the Confluence wiki will do it all, but requires some $$ and knowledge.     [http://www.wikimatrix.org/compare/Confluence+DokuWiki+Drupal-Wiki](http://www.wikimatrix.org/compare/Confluence+DokuWiki+Drupal-Wiki)

---

### Post by martin-lee.cusick on 2015-09-01
> **Habitual said:**
> you can still scp from behind a firewall in an "industrial setting". Internet or not.
Private LANs use scp all the time.

Oh yeah, I use scp right now AND rsync. I'm trying to find out which is the preferred method (the best balance between easy of use and security). I've inherited a half breed so to speak that works when the environment is just right... just trying to make things better. With your help of course.

> **HermanAB said:**
> Anonymous FTP has done that successfully since about 1970.

Thanks Herman, I will look into that.

> **Geoffrey_Arndt said:**
> If no external internet allowed, and because you want automated copy of most current file (syncing), perhaps you should consider an internal cloud such as ownCloud:   [https://owncloud.org/](https://owncloud.org/)

Or - - software such as advanced "groupware" . . which these days means a wiki.   These wikis provide an easy way to see all the documents that have been updated within a specified time period, allowing for access to the latest data.

See these . . . the Confluence wiki will do it all, but requires some $$ and knowledge.     [http://www.wikimatrix.org/compare/Confluence+DokuWiki+Drupal-Wiki](http://www.wikimatrix.org/compare/Confluence+DokuWiki+Drupal-Wiki)

Definitely something I should look into, but if we had money and knowledge, we probably wouldn't be asking the good people of the forums for help.

---

### Post by HermanAB on 2015-09-03
OK, so as far as I can figure, you have a bunch of machines with Windows/Linux/Mac behind a firewall in an industrial setup and you want users to download certain files.

The limitation is Windows.  Windows only supports three file transfer protocols: FTP, WebDAV and CIFS (a.k.a. SMB or Samba). Linux and Mac supports many, many transfer protocols, the good, the bad and the ooogly.

FTP is the oldest and simplest transfer protocol to set up and make work.  CIFS is the most complicated - the Samba book is 3 inches thick.  WebDAV requires a web server which is a whole 'nuther ball of wax.  However, for FTP, Windows only supports Anonymous transfers, no username and no password, which happens to be what you require anyway.

There is some info on getting FTP to work with Windows, at the bottom of this:
[http://www.aeronetworks.ca/2015/02/windows-10-on-virtualbox.html](http://www.aeronetworks.ca/2015/02/windows-10-on-virtualbox.html)

---

### Post by The Cog on 2015-09-03
> **HermanAB said:**
> Windows only supports three file transfer protocols: FTP, WebDAV and CIFS (a.k.a. SMB or Samba).
scp works just fine on windows if you install cygwin. I wouldn't be without it.

---

