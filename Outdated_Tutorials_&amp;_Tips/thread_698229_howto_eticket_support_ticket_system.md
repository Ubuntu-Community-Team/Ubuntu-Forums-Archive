---
title: "howto: eticket support ticket system"
date: 2008-02-16
forum: Outdated Tutorials &amp; Tips
---

### Post by bmathis on 2008-02-16
I have been using eticket support/trouble ticket system to track helpdesk issues for awhile now and thought I would share how to install it.

First download the latest version of eticket from the [sourceforge website]("http://eticket.sourceforge.net"), then move the file to your server via ftp, ssh, etc&#8230; and unzip the archive to an appropriate directory.

create a mysql database and assign a user for the database.

```
mysql -u root -p

create database eticket;

grant select, insert, update, delete, create, drop, index, alter, create temporary tables, lock tables on eticket.* to &#8216;eticket&#8217;@'localhost&#8217; identified by &#8216;eticketpassword&#8217;;

quit;
```

make sure you are in the eticket directory and set the permission of settings.php and automail-settings.pl to 666

```
sudo chmod 666 settings.php automail-settings.pl
```

go to the eticket installation directory in your web browser, it should look like [http://yourserver/eticket/install](http://yourserver/eticket/install) and follow the instructions to begin installation. once completed, you&#8217;ll need to change the permissions of settings.php to 644 and automail.pl to 755

```
sudo chmod 644 settings.php && sudo chmod 755 automail.pl
```

now remove or rename the install directory and you&#8217;re ready to go. login to the admin panel and configure your new support/trouble ticket system. for more info, please visit the eticket website

note: to allow attachments, you will need to chmod the attachments directory to 666

```
sudo chmod 666 -R attachments
```

Please let me know if this howto was helpful and if there are any errors/problems. Thanks

[SIZE="1"]originally posted on my [blog]("http://www.brianmathis.net").[/SIZE]

Here is a screen shot of eticket 
[IMG]http://ticket.bmnetworking.com/eticket.png[/IMG]

---

### Post by rbkrazy on 2008-02-18
Hi and thanks for the howto, this is really going to help me out. One question, for the attachments, I did as told and chmod 666 -R attachments but how do I enable them so my users can upload an attachment?

---

### Post by bmathis on 2008-02-18
> **rbkrazy said:**
> I did as told and chmod 666 -R attachments but how do I enable them so my users can upload an attachment?
in the admin section, go to preferences and check the box for "accept file attachments:" you can also add or remove file extensions in this section.

---

### Post by postingid on 2010-04-26
Can anyone tell me how to change my **eticket **administrator password?
 
Kenneth

---

### Post by Hauzer on 2010-05-03
[FONT=Arial][SIZE=2]If you are the owner of the eticket support system and can access  the database using phpMyAdmin, then please do the following to reset your own  password.[/SIZE][/FONT]
[FONT=Arial][SIZE=2]
[/SIZE][/FONT]
 [FONT=Arial] [COLOR=red]_ **BEFORE DOING THIS DO A SQL BACKUP**_[/COLOR][SIZE=2]

1. Open your Database (SQL) file with phpMyAdmin in your web host's control  panel.
2. Click the browse icon (first icon) on the "ticket_reps" table.
3. Look down the column named "name" till you find your user name.
4. Click the edit icon (pencil) beside your name.
5. On the password row, you'll see your password encrypted in MD5. Replace it  with the following code:
 [/SIZE][/FONT]     [FONT=Arial][SIZE=2]Code:[/SIZE][/FONT]
      [FONT=Arial][COLOR=#ff0000]d8578edf8458ce06fbc5bb76a58c5ca4[/COLOR][/FONT] 
 [FONT=Arial][SIZE=2]And click "Go". This changes your password to: [COLOR=#ff0000]qwerty
[/COLOR]6. In your browser type in the web address of where your eticketsupport script  admin section is located.
7. Login with your user name and the password: [COLOR=#ff0000]qwerty[/COLOR][/SIZE][/FONT]
** [FONT=Arial][SIZE=2]8. Once logged in click the "My Account" tab and change your  password to your custom and hit "Save Changes".[/SIZE][/FONT]**

---

