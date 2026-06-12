---
title: "Simple PHP File Upload not working"
date: 2012-06-23
forum: Programming Talk
---

### Post by PaulM1985 on 2012-06-23
Hi

I have tried setting up a simple PHP file upload so that I can move files about on my local wireless network.

I have copied the code from this tutorial ([http://www.tizag.com/phpT/fileupload.php](http://www.tizag.com/phpT/fileupload.php)) hoping it would just work, but unfortunately I always get the error message.

I guessing it might be to do with permissions on the folder, but I tried setting the ownership from "root" to myself and that didn't fix the problem.

Anyone got any ideas?

Paul

---

### Post by Dimarchi on 2012-06-23
Better minds may clarify - and correct - this, but my understanding of the situation is as follows: it is not root nor you who needs the permission to write a file...it is the server, since it does the job (www-data in case of Apache 2, if I recall correctly).

---

### Post by PaulM1985 on 2012-06-23
Ok, so what do I need to enter into my chown?  Is there a way so that I can use chown to make access available to everyone?  There is no real issue regarding security for me since this is to only be used on a small personal network.

Paul

---

### Post by SeijiSensei on 2012-06-23
You must use a directory to which the www-data has write privileges.  /tmp is the easiest solution since all users can write there.  

I dislike the fact that Ubuntu points the DirectoryRoot to /var/www, much preferring the RedHat model where publicly-visible pages are stored in something like /var/www/htdocs which lets me create other directories under /var/www that are invisible to website visitors.  In this model I'd have:

/var/www/htdocs - DocumentRoot
/var/www/upload - temporary upload storage

The www-data user should have read and list privileges to /var/www/htdocs.  Giving that user write privileges is a potential security hole.  For /var/www/upload the user www-data needs all privileges.

If you have multiple people creating content for the site, I'd put them in a "webauthors" group, and give the group write privileges to /var/www/htdocs. 

```

sudo addgroup webauthors
sudo adduser bill webauthors
sudo adduser mary webauthors
cd /var/www
sudo mkdir htdocs upload
sudo chown www-data:webauthors htdocs 
sudo chown www-data:www-data upload
sudo chmod 575 htdocs
sudo chmod 700 upload

```

If you're the only person who will creating content for the site, you can set just use your own username for the group since every user in Ubuntu has a group created with the same username and that single account as a member.

In the <VirtualHost> configuration, you would have 

```

<VirtualHost *:80>
    ServerName myserver.example.com
    DocumentRoot  /var/www/htdocs
    <Directory "/var/www/htdocs">
         Options Indexes FollowSymLinks
         [other options if appropriate]
    </Directory>
</VirtualHost>

```

---

### Post by PaulM1985 on 2012-06-23
Thanks for the help SeijiSensei.  I have a folder /var/www/uploads so I did:
```

paul@paul-desktop:/var/www$ sudo chown www-data uploads

```
at it is now working.

I have a few PCs running poker AI evolution on an adhoc wireless network and I connect to them using Remote Desktop.  It is a hassle transferring poker players about using USB sticks to test them on my main PC so uploading via a webpage is much easier.

Thanks again.

Paul

---

