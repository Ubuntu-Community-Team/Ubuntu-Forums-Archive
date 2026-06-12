---
title: "Setting up a web development setup"
date: 2014-03-19
forum: Programming Talk
---

### Post by Dragonbite on 2014-03-19
I am trying to create a web development setup on Ubuntu 12.04 and am running into a snag...

I installed the LAMP server using tasksel and confirmed that Apache works.

In another thread, I mentioned that I wanted to have the files located in some place in my /home directory (so could be synchronized, easily edited, etc.) and was recommended to create a symbolic link to my local files ```
cd /var/www && sudo ln -s /home/drew/Dropbox/Documents/programming/code/webdev 
```

This worked in putting a symbolic link (/var/www/webdev), but Apache doesn't have the permissions necessary it seems to display any of the content, even straight HTML pages.  I get an authorization error, so I know it "sees" it but just cannot display or run it.

The folders under /var are owned by root:root, but my local versions are owned by me (drew:drew).  The directory appears to include rw+x permissions for owner and group (r+x only for the last).

How can I handle the permissions so that I can edit the files locally and have Apache be able to read, use and execute the pages?  Keep in mind that the local files are in a Dropbox folder and gets synchronized and edited on other systems as well.

If I have to make a change to httpd.conf, how is the best way to do this?  I am not familiar with configuring apache for virtual directories and aliases.  I am not sure if this would work for making localhost/drew (or is it drew.localhost?): ```

Alias /drew /home/drew/Dropbox/Documents/programming/webdev

<Directory /home/drew/Dropbox/Documents/programming/webdev>
DirectoryIndex index.html index.php
Options FollowSymLinks
AllowOverride None
order allow,deny
allow from all
</Directory>

``` ([link]("https://sites.google.com/a/azizdev.com/www/ubuntu/howtocreateavirtualdirectoryinapache2"))

Which method would your recommend? Why?

---

### Post by SeijiSensei on 2014-03-19
I just set the DocumentRoot to the appropriate directory.

Apache needs read privileges on all files and directories from /home down to /home/username/whatever/documentroot.  I solve this by putting the apache user in the user's own group.  So if /home/username/mywebsite is owned by seiji:seiji, I'd put the apache user in group seiji.  You can just add "apache" to the list in /etc/group like this:
```

seiji:x:1000:apache

```
Make sure your group has the correct privileges as well.

You can use aliases or symbolic links, but I prefer a more straightforward approach.  I'm serving files for multiple name-based virtual hosts, each of which has its own configuration file and separate DocumentRoot.  Here's an example:
```

<VirtualHost *:80>
ServerName              www.example.com
ServerAlias             example.com
ServerAdmin             webmaster@example.com
TransferLog             logs/access_log-example1
ErrorLog                logs/error_log-example1
CustomLog               logs/referer_log-example1 "%h %{referer}i -> %U"
DocumentRoot            /home/seiji/sites/example1

<Directory "/home/seiji/sites/example1">

        Options                 Indexes FollowSymLinks 
        IndexOptions            FancyIndexing SuppressColumnSorting
        IndexOrderDefault       Descending Date

</Directory>

</VirtualHost>

```

---

### Post by Dragonbite on 2014-03-19
> **SeijiSensei said:**
> I just set the DocumentRoot to the appropriate directory.

Apache needs read privileges on all files and directories from /home down to /home/username/whatever/documentroot.  I solve this by putting the apache user in the user's own group.  So if /home/username/mywebsite is owned by seiji:seiji, I'd put the apache user in group seiji.  You can just add "apache" to the list in /etc/group like this:
```

seiji:x:1000:apache

```
Make sure your group has the correct privileges as well.


Thanks. I wasn't sure what username Apache uses and 1 reference mentioned 'www-data', so I added that to my personal group and that didn't work. I'll have to try adding Apache to the group next.

> **SeijiSensei said:**
> 
You can use aliases or symbolic links, but I prefer a more straightforward approach.  I'm serving files for multiple name-based virtual hosts, each of which has its own configuration file and separate DocumentRoot.  Here's an example:
```

<VirtualHost *:80>
ServerName              www.example.com
ServerAlias             example.com
ServerAdmin             webmaster@example.com
TransferLog             logs/access_log-example1
ErrorLog                logs/error_log-example1
CustomLog               logs/referer_log-example1 "%h %{referer}i -> %U"
DocumentRoot            /home/seiji/sites/example1
<Directory "/home/seiji/sites/example1">
        Options                 Indexes FollowSymLinks 
        IndexOptions            FancyIndexing SuppressColumnSorting
        IndexOrderDefault       Descending Date
</Directory>
</VirtualHost>

```

I am avoiding taking over the Apache root, as this is also the family computer and others may at some point be setting up their own websites.

In your example, the DocumentRoot is /home/seiji/sites/example1, but how would you reference that in the browser?  I am not 100% sure of the relationship between the VirtualHost and access from the browser.

---

### Post by Dragonbite on 2014-03-20
I tried adding "apache" to my user group. That didn't do anything.

I tried adding the virtual directory (based on the code in my post above) and that too didn't fix the permissions error.

I tried making a new group ("webdev") and added "apache" and my user account to it.

Still getting permission denied error.

---

### Post by SeijiSensei on 2014-03-22
Sorry. On Ubuntu Apache runs as the "www-data" user, so use that rather than "apache".

---

### Post by Dimarchi on 2014-03-28
Dragobite, is your home directory encrypted? Even if everything else is correct, that is what happens if it is. Just one possible explanation.

---

### Post by Dragonbite on 2014-03-28
> **Dimarchi said:**
> Dragobite, is your home directory encrypted? Even if everything else is correct, that is what happens if it is. Just one possible explanation.

I don't believe I encrypted the hard drive.

---

