---
title: "Cant save PHP files"
date: 2006-02-24
forum: Programming Talk
---

### Post by cobbweb on 2006-02-24
Hey, 

  I am trying to save php files in my "www" folder (i installed apache) but every time i do, it say's that there was an error and it "could not save the file" 

 Im really confused on why it would do this. Im saving it as a php file. Im very new to php but have done a lot of Java programming so have I know about program structs but have a hard time with data base stuf (thus the reason im trying to learn php and mysql) Is there a setting off? or im... really not sure. Thanks any help is wanted... 

 Cobbweb

---

### Post by suRoot on 2006-02-24
Can you save the file elsewhere? 

Sounds like a permissions problem to me.

Try saving the file to your home directory & then moving it

```
sudo mv /home/foo/foo.php /path/to/www
```

---

### Post by nemik on 2006-02-24
chmod the folder so you can write to it.

---

### Post by cobbweb on 2006-02-24
should i do a 755? 

 ```


chmod 755 www


```

or is there a diffrent one i should do...

---

### Post by cobbweb on 2006-02-24
[QUOTE=suRoot]Can you save the file elsewhere? 

Sounds like a permissions problem to me.

Try saving the file to your home directory & then moving it

```
sudo mv /home/foo/foo.php /path/to/www
```[/QUOTE]


 Works great, but do i have to move the files into the folder like that every time????

---

### Post by Kurt` on 2006-02-24
Try this command:

> ls -alFh /path/to/folder/where/www/is
and you should see something like this:

> drwxr-xr-x   5 root   root   1.3K 2006-02-23 02:32 htdocs/

And now for a quick lesson on linux file permissions ;)

chmod works like this:

> chmod (-R) xyz files/folder
(-R is used to apply the new permissions recursively, so be careful with it.)

The xyz works like this:

x = owner's permission
y = the group's permission
z = everyone else's permission

And the values work like this:

4 = read
2 = write
1 = execute (probably won't be necessary)

By combining those 3 numbers, you can determine what chmod values to use for a particular folder. For example, if I wanted to make everything inside my htdocs folder readable, writable, and executable for everyone, I could do this:

> chmod -R 777 htdocs

If I want only root (keep in mind, root still owns the folder, use `chown` to change ownership) to be able to write, and only people in the root group to be able to read, I would do this:

> chmod -R 640 htdocs

and everyone else gets denied. ;)

Hopefully, that should clear up any confusion.

---

### Post by mtron on 2006-02-24
it's best to use the www-data group for this. make your user a member of this group and you will have write access, if you set the foler ownerships right.

---

### Post by cobbweb on 2006-02-26
[QUOTE=Kurt`]Try this command:


and you should see something like this:



And now for a quick lesson on linux file permissions ;)

chmod works like this:


(-R is used to apply the new permissions recursively, so be careful with it.)

The xyz works like this:

x = owner's permission
y = the group's permission
z = everyone else's permission

And the values work like this:

4 = read
2 = write
1 = execute (probably won't be necessary)

By combining those 3 numbers, you can determine what chmod values to use for a particular folder. For example, if I wanted to make everything inside my htdocs folder readable, writable, and executable for everyone, I could do this:



If I want only root (keep in mind, root still owns the folder, use `chown` to change ownership) to be able to write, and only people in the root group to be able to read, I would do this:



and everyone else gets denied. ;)

Hopefully, that should clear up any confusion.[/QUOTE]



Wow! Very Helpfull thank you soo much. 

 Cobbweb

---

### Post by cobbweb on 2006-02-26
[QUOTE=mtron]it's best to use the www-data group for this. make your user a member of this group and you will have write access, if you set the foler ownerships right.[/QUOTE]


How would i use this method? The other one is great, but I keep getting this error.   

 ```

Operation is not permitted

```

---

### Post by mtron on 2006-02-27
[QUOTE=cobbweb]How would i use this method?[/QUOTE]

You can use System->Administration->Users and Groups to create groups and give add user account to group, OR you can edit /etc/group file and add you username after the group (on the same line) - you should probably use pre-existing group www-data.

As a root you can do
chgrp -R www-data /var/www/*
to change all the files and directories under /var/www/ to www-data group (except files starting with dot) and then
chmod -R g+rw /var/www/*

to give www-data group read and write permissions to all files and directories. 

Now if your user belongs to group www-data, you can directly copy or save stuff to /var/www (default apache webroot on debian like systems).

You should also make sure that the files are owned by username www-data which is the username apache is run by default. (you can check your apache.conf of apache2.conf for lines like:

User www-data
Group www-data

---

