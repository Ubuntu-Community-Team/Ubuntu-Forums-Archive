---
title: "How do you connect to the database without exposing password?"
date: 2012-01-23
forum: Programming Talk
---

### Post by anon0 on 2012-01-23
The tutorials I followed showed mysql_connect($server, $db_user_name, $password); 
where $db_user_name and $password were explicitly shown in the same text file.

Someone said "Internet user cannot see your PHP source code, so there is no risk exposing password when you use mysql_connect() function in PHP. Only developers or network admin who has access to the server can see the PHP source code."

Would you say this is a BAD IDEA? 

If so, what are the standard ways to encrypt the password when connecting the server?

---

### Post by Bachstelze on 2012-01-23
That's not how encryption works. If you store the password "encrypted", then it has to be decrypted at some point, which means the decryption key must be available, which defeats the point of encryption. You just have to make sure that no untrusted user will be able to read the file.

---

### Post by dargaud on 2012-01-23
In a simple situation, your database should only be accessible from the PC hosting the php files (often the same one). So even if for some reason the password becomes known to the outside (for instance if text/x-php turns to text/plain), it's still useless.

---

### Post by Bachstelze on 2012-01-23
> **dargaud said:**
> In a simple situation, your database should only be accessible from the PC hosting the php files (often the same one). So even if for some reason the password becomes known to the outside (for instance if text/x-php turns to text/plain), it's still useless.

I can't let you say that. It's always a bad thing when your password is compromised. Besides, what if the guy with the password also finds your phpmyadmin?

---

### Post by ofnuts on 2012-01-23
> **Bachstelze said:**
> I can't let you say that. It's always a bad thing when your password is compromised. Besides, what if the guy with the password also finds your phpmyadmin?It's unfortunately how it works. Access to the DB is always plainly password-protected so the password is always buried somewhere in the application configuration files, hopefully with some obfuscation (encryption is useless, since you would have to keep the decode key also in the application config files). So security consists in preventing access to the application configuration, plus some firewalling to prevent access to the DB directly from the outside.

Of course the pwd is very often found elsewhere. When I am assigned on an already existing project, all the useful passwords can be found in the installation/deployment scripts.

---

### Post by Bachstelze on 2012-01-23
> **ofnuts said:**
> It's unfortunately how it works. Access to the DB is always plainly password-protected so the password is always buried somewhere in the application configuration files, hopefully with some obfuscation (encryption is useless, since you would have to keep the decode key also in the application config files). So security consists in preventing access to the application configuration, plus some firewalling to prevent access to the DB directly from the outside.

Of course the pwd is very often found elsewhere. When I am assigned on an already existing project, all the useful passwords can be found in the installation/deployment scripts.

And this contradicts what I said how?

---

### Post by Habitual on 2012-01-23
[http://mysqldatabaseadministration.blogspot.com/2006/08/storing-passwords-in-mysql.html](http://mysqldatabaseadministration.blogspot.com/2006/08/storing-passwords-in-mysql.html)

---

### Post by memilanuk on 2012-01-23
> **Habitual said:**
> [http://mysqldatabaseadministration.blogspot.com/2006/08/storing-passwords-in-mysql.html](http://mysqldatabaseadministration.blogspot.com/2006/08/storing-passwords-in-mysql.html)

Not even the same thing, man.  He's not asking about storing passwords *in* mysql (what your link talks about), he's asking about storing the password *to* the mysql database.

Usually the info I see recommends storing them somewhere outside the web document root directory, just in case something happens to the server configuration and it happens to start serving up php scripts as plain text files... it still can't/won't (shouldn't?) show external users the script files containing the plain text database login info because they are outside ~/public_html.  In the event of a server problem that still may not be the safest place in the world, but I'm not sure there is a better way...

---

### Post by hockey97 on 2012-01-23
The standard way is to use mysql_conect and put the password as plain text.

PHP is server sided and only the source can be read on the server.

If you have issues with employees or someone that will work with them or if you think a hacker could hack into your server and read these  source code.

Then make a class for mysql connections have it written in php and then change the permission to that file that it's not readable nor writeable but excutable.

you can make only your own user on the server the user account you use to have access to it. Yet, programmers can include that file and it will work but they won't have viewable access to it.

They can't look at the source noone but you yet, it's runable script so your server will still run it and the programmers can still include the file where they can then utilize the functions you created to connect to your database.

that is the only alternative solution. 

You can't encrypt and decrypt the password unless you write a plugin for mysql.. but still if someone wants to get access they can open up your plugin and read the source code.

the proper way is to have a root user, your own user account and set sensitive scripts to be accessible to you and root user. For, everyone else set it to excitable. It just means that any other user on the system has permission to run the script.

they can't read it or write it. reading will allow the user to be able open the file and read it but not make any changes to it.

write permissions allows the user to read and modify the code.

executable allows that user to just run it.

For example, apache needs to run the php scripts. So the user apache will get permission to just run the script.

so if someone writes a php script they can include that file and then they can use the class functions etc. yet, they won't be able to view whats inside that script.

so hackers would need to either hack your root user or your own user account to get access to such information.

If you have programmers or employees working on such projects then you need to crate them their own account.

Then you be the only one that will write the code to access the mysql database or access anything.

that way programmers will be controlled they will most likely just write the code to add functionality to your website like effects or programs but anything critical like your password information to your webserver, or mysql database or any other sensitive type of information.

if you give them no permission then the script they won't be able to read, write to it to make changes and won't be able to execute it.

to be honest all you need is to allow php, apache, mysql the execute permissions. their the ones that will end up running the script. If you give them those permissions you will have the scripts working without any permission issues.

Yet, this isn't standard. The standard is what most suggested to you. Just write the password in plain text.

if you have programmers then you should trust them they won't do anything fishy with you.

If you don't trust them then find a new employee. This is the standard motto.

Yet, if your a nut freak like me. I would read about your OS more about the permission structure and find books and tutorials on how to limit permissions on files without getting those nasty permissions errors on your website.

just saying all your doing is waste more space on your server to add that security level. 

me myself. I never done it. I have seen tutorials about it and read about it but never persue it. I have it saved in my favs. Since currently it's just me working on my server.

If I ever do expand to get my own office. I do plan to set my employees to have user accounts.

What I suggested is how I would handle the situation.

yet, it still boils down to the employee knowing your username and password you use to get access to the script files.

Plus if you notice in termial command line if you talk with mysql you notice there isn't any command to spit out the current password of the user account with mysql.

it's a security system to not allow your own programmers to find your user name and password.

Other then that if it's just you working on your server. then I would suggest you to not use what I suggested. Only use what I suggested if your running your own firm  and most employees you can't trust. So this be the only true way to have a Handel over your employees. 

other then that it's more code which requires more space on your servers hard drive. Also if you don't know what your doing you can easily mess up the permissions on your website where maybe half of your website is working and the other half stopped working spitting out these nice permission errors. Which if your not advance enough on how to handle such errors you will go bonkers.

So, before doing what I suggest you better know the OS you have and how to set and unset permissions. 

if you do this by terminal then before doing anything make sure you know exactly what permission value you had before... before you make any changes. This will help you revert back to any changes you made.

Hope this help.

---

### Post by hockey97 on 2012-01-23
> **memilanuk said:**
> Not even the same thing, man.  He's not asking about storing passwords *in* mysql (what your link talks about), he's asking about storing the password *to* the mysql database.

Usually the info I see recommends storing them somewhere outside the web document root directory, just in case something happens to the server configuration and it happens to start serving up php scripts as plain text files... it still can't/won't (shouldn't?) show external users the script files containing the plain text database login info because they are outside ~/public_html.  In the event of a server problem that still may not be the safest place in the world, but I'm not sure there is a better way...

No, OP is talking about using mysql_connect() in php.

where your giving the hostname,username,password. 

This allows you to connect to mysql and then start executing sql query code aka having access to his database server.

by default and standard you give this information in plain text.

He is asking if there is a way where at least the password you can encrypt it and salt it.

so like using hasing MD5 or something like that to the password.

My answer in short is no, it's not standard to do it and mysql dosen't support passwords to be given in encrypted format.

Yet, like justin  beaver says... never say never. I am not sayingi it's impossible you will need to create a module for mysql which would decrypt your password.

yet, I don't know OP'S intentions if he is worried about hackers, then my method will be good enough, if he is worried about hiring programmers that later on will use the information to get back at him, my method will work. yet, my method nor any method is bullet proof. all they need is your username and password you use to log into the server. yet, it would prevent employees to actually get to see your passwords in plain text without actually encrypting them. Just set the permissions properly and you would be fine.

mysql dosen't have a built in feature to decrypt your password. postfix mail servers do.

it's because mysql is server sided and assume the person working on the server are trusted people and if not you can always delegate proper permissions. there is no true need to protect your own password to the database. Since the passwords stored in the database are encrypted.

when you store passwords you encrypt them and then with your own code you just encrypt the login attempted password tossed to your script and then grab whats in the database and do a match or comparison. 

the mysql database never encrypts the passwords for you.

I am sure there are plugins/ modules that you can download and it will allow mysql to decrypt standard encryption type like MD5.

if you want to really have it secure I suggest you write your own module for mysql and have your own decryption that way if you use MD5 and then salted the password a bit you would know how to decryption it. mysql dosen't need to decrypt it just need if mysql stores the encrypted password. all you need to do is just encrypt the input and then do a match.

the same way you use php to encrypt passwords to be stored in the database mysql needs to do the same.

---

### Post by memilanuk on 2012-01-23
> **hockey97 said:**
> No, OP is talking about using mysql_connect() in php.

where your giving the hostname,username,password. 

This allows you to connect to mysql and then start executing sql query code aka having access to his database server.

by default and standard you give this information in plain text.

I think thats pretty much what I said, without so many line-breaks ;)

> 
He is asking if there is a way where at least the password you can encrypt it and salt it.


Yes he is, and no there isn't, at least not easily, as you pointed out.

> it's because mysql is server sided and assume the person working on the server are trusted people and if not you can always delegate proper permissions. there is no true need to protect your own password to the database.

Yes, there is.  If something happens to the *web* server software to where it starts serving up php files as plain text - say someones screwed up the installation, or an upgrade, or whatever - and your database login info is in a php file inside document_root, you just gave up your login info to whoever wanted it.  If, however, your login info is stored in a script file *outside* the document_root, say up one directory from ~/public_html/ but still inside your user home... your scripts can access it as needed, but the web server cannot just serve up *that* info to an external user.

---

