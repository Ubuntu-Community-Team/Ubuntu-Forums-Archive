---
title: "Help needed to insert/add text in files with bash and sed"
date: 2007-08-01
forum: Programming Talk
---

### Post by Krijk on 2007-08-01
After manually configuring my servers too many times :( I'm trying to create a script that will change the default config-files with my modifications.

Searching and replacing works ok, but I'm running into problems with inserting lines of text.
inserting several lines at a given location
Adding lines at the end of a file

This is what I brewed up to change apache2.conf . It errors:

sed: -e expression #1, char 130: unterminated address regex

```

#!/bin/bash -x

cp apache2.conf.org apache2.conf 
cp apache2.conf apache2.conf.tmp
cat apache2.conf.tmp | sed -e 's/HostnameLookups Off/HostnameLookups On/' -e 's/ServerSignature On/ServerSignature Off/' -e 's/ *,t/ *,t ,robots.txt/' >apache2.conf.tmp2
sed 'a197 
\<Directory "\/var\/www\/htdocs"\>\
Options -Indexes\
AllowOverride All\
Order allow,deny\
Allow from all\
\<\\Directory\>' apache2.conf.tmp2
cp apache2.conf.tmp2 apache2.conf
rm apache2.conf.tm*

```

I'm having similar problems with appending new lines:
sed: -e expression #1, char 5: unknown command: `S'
According to a tutorial on internet $a is used to append at the end of a file.

```
#!/bin/bash -x

cp apache2.conf.org apache2.conf
sed '$a 
ServerName www.my.lan \
NameVirtualHost 192.168.0.2:80 \
NameVirtualHost 192.168.0.2:443' apache2.conf

```

Obviously I'm having syntax troubles. Can anybody give me a hand with this?
(An url of a good "sed tutorial for dummies" might help too  :confused: )

---

### Post by tjansson on 2007-08-01
I am just think aloud -  but couldn't you just do something like 
```

echo -e 'This is\n a\n test\n' >> foo

```

---

### Post by batrick on 2007-08-01
You can use `cat foo foo2` to con**cat**enate the two files. You can use sed to grab lines and pipe them into cat.

```
echo "add this line" | cat - foo
```

Hope that helps.

---

### Post by Krijk on 2007-08-01
Thanks for the tips, I was so preoccupied with sed  ](*,)  that I didn't see the obvious.

I went for the echo.  This works for appending, but what can be used to insert text  in the middle of a file?


```

echo "<Directory "/var/www/htdocs">">>apache2.conf.tmp2
echo "Options -Indexes">>apache2.conf.tmp2
echo "AllowOverride All">>apache2.conf.tmp2
echo "Order allow,deny">>apache2.conf.tmp2
echo "Allow from all">>apache2.conf.tmp2
echo "</Directory>" >>apache2.conf.tmp2

```

---

### Post by cwaldbieser on 2007-08-02
> **Krijk said:**
> Thanks for the tips, I was so preoccupied with sed  ](*,)  that I didn't see the obvious.

I went for the echo.  This works for appending, but what can be used to insert text  in the middle of a file?


```

echo "<Directory "/var/www/htdocs">">>apache2.conf.tmp2
echo "Options -Indexes">>apache2.conf.tmp2
echo "AllowOverride All">>apache2.conf.tmp2
echo "Order allow,deny">>apache2.conf.tmp2
echo "Allow from all">>apache2.conf.tmp2
echo "</Directory>" >>apache2.conf.tmp2

```

What about something like:
```

#! /bin/bash

#First output the beginning.
head -n 100 infile > outfile;
#Merge the middle.
cat middle >> outfile;
#Output the end.
sed -n -e '101,$p' infile >> outfile;

```

---

