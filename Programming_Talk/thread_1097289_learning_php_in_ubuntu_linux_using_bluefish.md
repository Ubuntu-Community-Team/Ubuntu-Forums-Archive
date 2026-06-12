---
title: "learning php in ubuntu linux using bluefish"
date: 2009-03-15
forum: Programming Talk
---

### Post by InternetDominus on 2009-03-15
Hi,

I just installed bluefish via synaptic, and opens fine phpinfo, and any file I add via terminal; however, bluefish does not let me create files, nor save them.

I had to create a test.php file via terminal using 

```
touch test.php
```

then, I had to chmod 777 via terminal so I could actually use it, and be able to save using bluefish save button.

My question are:
[LIST]
[*]why isn't blue fish letting me create files directly from bluefish?
[/LIST]
[LIST]
[*]why can't I save the files via bluefish?
[/LIST]
[LIST]
[*]Is there some permissions I should give to bluefish?
[/LIST]

Or, will I have to create, move, and chmod every single file via terminal?

Thanks,

ID

---

### Post by manishtech on 2009-03-15
Actually if you are using php with apache then the DocumentRoot would be /var/www which is actually owned by the user "www-data". this is the user under which apache runs (security reasons)

This folder does not have write permission for the user with you logged in. There are three ways to deal with this problem

1. Run BlueFish as root. Press Alt+F2, a dialog box would pop-up, there type
```
gksudo bluefish
```and press enter, type your password and start working without any problems

2. Make /var/www folder owned and writebale by you. 
```
sudo chown user:group /var/www
```Where user is your username and group is your group (usually your username)
Then you should make apache run under your user, press Alt+F2 and type there
```
gksudo gedit /etc/apache/envvars
```Over there change APACHE_RUN_USER and APACHE_RUN_GROUP to that of your user
P.S: This method is dangerous a bit and should be not be used on production environment

3. This is the best method. Create a new Virtual Host.
Open /etc/apache2/sites-available/default using the Alt+f2 method. At the last add

> <VirtualHost *:80>
    DocumentRoot /home/manish/www/
    ServerName altserver
</VirtualHost>

Now open /etc/hosts using the same Alt+F2 method  and add the line
```
127.0.0.1 altserver
```Now restart the server using 
```
sudo /etc/init.d/apache2 restart
```You may get some errors, ignore them
Now open altserver in browser and its voila. Done! Put your code in /home/manish/www directory.

In example 2 you need to restart the server at the last too...

---

### Post by ufis on 2009-03-16
A much simpler way to get by the permissions is to use symbolic links.

See ln man pages:
> man ln

Create your working directory under your normal home directory:
> cd ~
mkdir learnphp
(~ is translated to your home directory: */home/youruser* )

Then go to your apache root:
> cd /var/www
And create the symbolic link to your working directory:
(refer to the man pages for an explanation on this command and parameters
> sudo ln -s ~/learnphp learnphp

If you now do a directory listing > ls -l you will see an entry similar to this:
> lrwxrwxrwx 1 root root   17 2009-03-16 12:39 learnphp -> /home/youruser/learnphp/


if you now create a php / html file in /home/youruser/learnphp and then in your webbrowser go to [http://localhost/learnphp](http://localhost/learnphp) you will find it there.

This way you can easily edit the files without difficulty with permissions and still enable apache to pick it up.

---

### Post by Uchiha_madara on 2009-03-16
I Can write PHP Code by using Vim Editor......

and run it in The terminal too..

but the problem is using Bluefish or any Editor to Save and run The Code..

i well try the steps above ......

thanks a lot ..

---

