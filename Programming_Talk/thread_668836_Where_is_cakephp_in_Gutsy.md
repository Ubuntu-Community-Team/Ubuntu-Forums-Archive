---
title: "Where is cakephp in Gutsy?"
date: 2008-01-15
forum: Programming Talk
---

### Post by dallasray on 2008-01-15
After ensuring dependencies, I did

sudo apt-get install cakephp

and all seemed to go nicely...

But where the heck is it?

I checked /var/www and other places but can't find it.

Thanks in advance!

---

### Post by Compyx on 2008-01-16
It's installed in /usr/share/php/cake.

Seems like it's up to you to configure the whole thing, perhaps by creating a symlink to /usr/share/app/cake in /var/www?

Personally I think you're better off installing cakephp by hand (untarring into /var/www/cake or something similar) than using ubuntu's package.

---

### Post by dallasray on 2008-01-16
I agree, and it's what I shall do.

Thank you!

---

### Post by azad on 2008-01-16
1. Install the LAMP stack and change the server root to /home/user/www
2. Download CakePHP from cakephp.org
3. Extract it on /home/user/www

Much easier.

P.S. Have you tried CodeIgniter? Its much more flexible and easier for developers.

---

### Post by g4m3b0y on 2008-01-17
You should try setting up named virtual hosting with apache. I was having issues trying to make it work and didn't like the fact that my cake app had to reside in my /var/www directory so I set up named virtual hosting. I have a copy of the Apache Definitive Guide book at home but if you don't have it check out this site:

[http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/](http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/)

This site should help someone out. The reason I chose to stick with cakephp over codeignitor is only for the amfphp integration (cakeswxphp).

I use aptana and configured the bake.php script to run as an external tool and use the console from the ide.  Add the new project after I run the script to point to my workspace and then point the virtual host's "DocumentRoot" to the newly created directory.

Aptana + flex sdk + cakephp + amfphp = pretty decent flash development in linux.

Also using sandy 3D with the blender export python script to actionscript 3.0.... hmm.... the possibilities of what could be made to reach the masses :)

---

### Post by martin_prince on 2008-02-27
> **azad said:**
> 1. Install the LAMP stack and change the server root to /home/user/www
2. Download CakePHP from cakephp.org
3. Extract it on /home/user/www

Much easier.

P.S. Have you tried CodeIgniter? Its much more flexible and easier for developers.

There's a reason it's not install to the web root directory when installed via the package.  Using an apache alias isolates the cake PHP code from the rest of your webserver code.  Also, if you install the package, you can get updates automatically.  Probably would be easiest just to take the time to see what the apache alias for it is, restart apache and type in that alias...

---

### Post by justin whitaker on 2008-02-27
The cakephp is a lie. :)




Sorry, couldn't resist.

---

### Post by motin on 2008-08-15
> **dallasray said:**
> After ensuring dependencies, I did

sudo apt-get install cakephp

and all seemed to go nicely...

But where the heck is it?

I checked /var/www and other places but can't find it.

Thanks in advance!

Install cakephp-scripts in order to get a cakephp app installation available in /usr/share/php/cake/app, as well as getting acl.php and bake.php available from the console. 

Even though you probably can try out some cake console stuff this way, you better install cakephp in a matter suggested above. 

Personally, I use webmin+virtualmin to create local development websites in where I install cakephp manually. 

In general: Use Synaptic or "dpkg -L <package-name>" to check where the installed package has it's files:
```
dpkg -L cakephp
dpkg -L cakephp-scripts

```

---

