---
title: "Apache PHP MYsql"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by Socca on 2008-08-08
Hey

I used to use Windows and with Windows..wamp server. Now i have read that all you need to do is use the sudo install apache php mysql in terminal and I have fully installed it. I have also tested by going to localhost and it says "It Works" lol.

Now i am wondering, where I can access phpmyadmin + the /www/ folder so I can add files to test using a mysql database (php files)

Thanks

Socca

---

### Post by iaculallad on 2008-08-08
To access phpmyadmin, open you browser and point it to: [http://localhost/phpmyadmin](http://localhost/phpmyadmin)
For the test files, you could change directory to the /www folder:
```
cd /var/www
```

---

### Post by dfreer on 2008-08-08
> **Socca said:**
> Hey

I used to use Windows and with Windows..wamp server. Now i have read that all you need to do is use the sudo install apache php mysql in terminal and I have fully installed it. I have also tested by going to localhost and it says "It Works" lol.

Now i am wondering, where I can access phpmyadmin + the /www/ folder so I can add files to test using a mysql database (php files)

Thanks

Socca

Did you also remember to actually install phpmyadmin? PHP != phpmyadmin.

---

### Post by Socca on 2008-08-08
First of all thanks for the www root. Would never have found it there.

2nd, I used the following for the terminal installation
```
sudo apt-get install php5 mysql-server apache2 phpmyadmin
```

It says Phpmyadmin at the back so I presumed it had installed it but I tried [http://localhost/phpmyadmin](http://localhost/phpmyadmin) and it doesnt work. Any ideas? Or did I presume wrong?

Thanks 

Socca

---

### Post by iaculallad on 2008-08-08
Uuuhh.. It's working fine with my Apache2/mySQL server. Try this on your terminal:

```
sudo ln -s /usr/share/phpmyadmin/ /var/www/phpmyadmin
```

Then open your browser and point it to: [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

---

### Post by Socca on 2008-08-08
Now when I enter [http://localhost/phpmyadmin](http://localhost/phpmyadmin) , It downloads a file called gC0otHiP.phtml.part 

Suggestions

If you dont know thanks for trying

Socca

---

### Post by iaculallad on 2008-08-08
> **Socca said:**
> Now when I enter [http://localhost/phpmyadmin](http://localhost/phpmyadmin) , It downloads a file called gC0otHiP.phtml.part 

Suggestions

If you dont know thanks for trying

Socca

Try reinstalling your phpmyadmin:

```
sudo apt-get remove phpmyadmin
sudo apt-get install phpmyadmin
```

---

### Post by ad_267 on 2008-08-08
Have you installed libapache2-mod-php5, libapache2-mod-auth-mysql and php5-mysql?

---

### Post by anewguy on 2008-08-08
Please excuse me for jumping in here, but I have a similar problem:

My browser returns the following:

You don't have permission to access /phpmyadmin on this server.

Thanks!:)

---

### Post by scott_g on 2008-08-08
> **anewguy said:**
> Please excuse me for jumping in here, but I have a similar problem:

My browser returns the following:

You don't have permission to access /phpmyadmin on this server.

Thanks!:)

If it isn't a production machine, you could try a:
```
sudo chmod 777 /var/www/phpmyadmin -R
```

If it is open to the internet, you need a different # (other than 777), I'm not sure what it is though...

Scott

---

### Post by PCessna on 2008-08-08
> **Socca said:**
> Hey

I used to use Windows and with Windows..wamp server. Now i have read that all you need to do is use the sudo install apache php mysql in terminal and I have fully installed it. I have also tested by going to localhost and it says "It Works" lol.

Now i am wondering, where I can access phpmyadmin + the /www/ folder so I can add files to test using a mysql database (php files)

Thanks

Socca

This is how I did it, she tells how to install and access and get databases running, 6/5 star tutorial :D

[http://www.lullabot.com/node/289/play](http://www.lullabot.com/node/289/play)

---

### Post by Socca on 2008-08-09
Like iaculallad said, try removing and installing phpmyadmin . I did but when i got on the link for phpmyadmin it still asks me if i want to download this PHTML file. Why?

Now ad_267 asked "Have you installed libapache2-mod-php5, libapache2-mod-auth-mysql and php5-mysql?" 

Maybe, any way I can find out?

I used this ```
sudo apt-get install php5 mysql-server apache2 phpmyadmin
``` this in the terminal. Would that not have installed the packages your asking me?

---

### Post by ad_267 on 2008-08-09
I'm not sure, it depends if they are a dependency of those packages. If you run this to install them it will say if they are already installed:
```
sudo apt-get install libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql
```

---

### Post by Socca on 2008-08-09
Yes! Got it working finally thanks to ad_267. The package which wasn't installed was  libapache2-mod-auth-mysql . Thanks everbody for helping!

Socca

---

### Post by Socca on 2008-08-13
Now thats its all working. I want it to work efficient as well. The thing I hate is that if I want to access wwww root folder i need to be root. In order to be root I need to run gksudo nautilus. Is there anyway I can promote myself to become root admin top user so I don't need to run that nautilus file browser. It would be much faster.

Any ideas?

---

### Post by ad_267 on 2008-08-14
Well it's possible but definitely not recommended. What you could do is put yourself in a group called webusers or something and give that group write privileges to the www directory. You could also make the directory writeable for anyone but that's probably not such a good idea either.

---

### Post by Martje_001 on 2008-08-14
Or you could do:
```
sudo mount --bind /var/www/ /home/yourname/www
sudo chown yourname:yourname /home/yourname/www
```
You could also do this in fstab. Google for it ;)

---

### Post by ad_267 on 2008-08-14
> **Martje_001 said:**
> Or you could do:
```
sudo mount --bind /var/www/ /home/yourname/www
sudo chown yourname:yourname /home/yourname/www
```
You could also do this in fstab. Google for it ;)

Hmm could you just use a symbolic link? "mkdir ~/www && sudo ln -sf /var/www ~/www"
What would the difference be?

---

### Post by Martje_001 on 2008-08-14
A soft link is the same as the directory where it's linked to. So you still need root privileges.

---

### Post by ad_267 on 2008-08-14
> **Martje_001 said:**
> A soft link is the same as the directory where it's linked to. So you still need root privileges.

If you link /var/www to ~/www then you don't need root privileges because you own your own home directory and ~/www. I just don't really understand what your commands do. Guess I've got some reading to do!

---

### Post by Socca on 2008-08-14
So What do I have to do really?

Because i'm getting three different options not knowing which one to choose

---

### Post by checho4 on 2008-08-15
> **Martje_001 said:**
> Or you could do:
```
sudo mount --bind /var/www/ /home/yourname/www
sudo chown yourname:yourname /home/yourname/www
```
You could also do this in fstab. Google for it ;)

Try this!  It worked well for me!

---

### Post by Socca on 2008-08-16
Ok Thats that. But the problem is..if I wanna edit something in one of the files and then save it...it says you don't have the permission. How can i get it unlocked?

---

### Post by checho4 on 2008-08-17
In the console, type in *sudo gedit /path/to/file*.  This will allow you to edit and save the file in gedit.

If you're in KDE, you use *sudo kate /path/to/file*.

---

### Post by Martje_001 on 2008-08-17
> **checho4 said:**
> In the console, type in *sudo gedit /path/to/file*.  This will allow you to edit and save the file in gedit.

If you're in KDE, you use *sudo kate /path/to/file*.
First: For grapical programs you have to use gksudo.
Second: He doesn't want that (read the whole thread, please).

> Ok Thats that. But the problem is..if I wanna edit something in one of the files and then save it...it says you don't have the permission. How can i get it unlocked?
And if you chmod it?
```
sudo chmod 777 /directory
```

---

