---
title: "Magento Installation In Ubuntu 12.04LTS"
date: 2012-05-04
forum: Programming Talk
---

### Post by ivikas on 2012-05-04
Magento 1.7 Installation Guide Along With Sample Data

Target System
                      
Operating System		:	Ubuntu 12.04 LTS

Apache Version			:	2.2.22

PHP    Version			:	5.3.10-1

MySQL Version			:	5.2.22

Install LAMP in Ubuntu (What i did from terminal)

Install Apache 2 WebServer

          ```
sudo apt-get install apache2
```

Install PHP5
     
          ```
sudo apt-get install php5
```

Install Mysql Server

          ```
sudo apt-get install mysql-server
```


Apart from default installation of LAMP we need to install php5-curl,from terminal issue the command

```
sudo apt-get install php5-curl
```

After this you need to enable mod_rewrite by issuing this command in the terminal(This is for Clean SEO URLS,you can skip this if you do not want)

             ```
sudo a2enmod rewrite
```

Now Open up(Not Sure on this...edit if required ) 

```
/etc/apache2/sites-enabled/000-default
```

And change text FROM &#8220;AllowOverride None&#8221; TO &#8220;AllowOverride All&#8221;

Finally restart the apache

         ```
/etc/init.d/apache2 restart
```


Install Magento 
---------------

1. Download the files.
          
          magento-1.7.0.0.tar.bz2

2. Download the sample data. 
             
          magento-sample-data-1.6.1.0.tar.bz2
		                       
3. Extract the sampledata,you will get a .sql file and a folder named media.This MUST BE DONE before Magento Installation,if you did want Magento Installation with SAMPLE DATA or else skip.

      Create a Database  and import this sql file into it.
    
4. Extract  magento-1.7.0.0.tar.bz2 to your webroot(www) and copy 
   &#8220;catalog&#8221; folder FROM &#8220;sampledata/media&#8221; folder TO &#8220;webroot/ma
    gento/media&#8221;.


5. Give full permission to your Magento Folder in www
            
            chmod -Rv 777 /var/www/magento

6. Now Run the install 

                 [http://localhost/magento](http://localhost/magento)

7.During the installation process,you can select the option 
 'Server (Apache) Rewrites', If you had previously enabled 
  mod_rewrite in Apache2. 

        
Finally after the installation finishes,you won't be able to log into the Admin Area of magento.


This is the fix for it.

Copy the files at THIS LOCATION

```


www/magento/app/code/core/Mage/Core/Model/Session/Abstract/Varien.php

TO

www/magento/app/code/local/Mage/Core/Model/Session/Abstract/Varien.php


```

The above  'TO' LOCATION DOES NOT Exists,you need to create folders and subfolders and paste the file Varien.php and Edit this file.

Open the above file and  locate the following php code 

```

if (isset($cookieParams['domain'])){
            $cookieParams['domain'] = $cookie->getDomain();
 }

```

And Replace it with the below code.

```

if (isset($cookieParams['domain']) && !in_array("127.0.0.1",self::getValidatorData())){
            $cookieParams['domain'] = $cookie->getDomain();
 }

```

Now you will be able to log into the Admin Area.

That's all !! You're Done.

---

### Post by factotum218 on 2012-07-08
This is a great write up and I'm sure it will help me later today when I tackle this, but I have a question.

Say I'm setting this up as a local dev environment on my laptop. Will it be difficult to transfer this over to a live server later on? I only ask out of curiousity because the time it would take to transfer an entire Magento install to another server could be days I would think. Quite a large amount of files to transfer from what I can tell.

---

### Post by ivikas on 2012-07-12
> **factotum218 said:**
> This is a great write up and I'm sure it will help me later today when I tackle this, but I have a question.

Say I'm setting this up as a local dev environment on my laptop. Will it be difficult to transfer this over to a live server later on? I only ask out of curiousity because the time it would take to transfer an entire Magento install to another server could be days I would think. Quite a large amount of files to transfer from what I can tell.

You can zip the file and upload to live server and unzip the files on the server otherwise it will take more time :)

---

### Post by ivikas on 2012-09-13
When installing on online Server,it may happen timeout and you may be unable to install on the online server.In such case you can install on the local server and port on to online Server.

Here is an excellent article by Damián Culotta from Argentina.Just Recreating his post so it may help someone.


If you want to move your installation form directory or domain, you need to follow this setps.

1) Delete the content of the folder /var

2) Change the values of the file /app/etc/local.xml 
There you can find your connection string data (database user, host and name).

3) Once you got your database uploaded, you need to make some changes.

- Run this query:

```

SELECT * FROM core_config_data WHERE path = 'web/unsecure/base_url' OR path = 'web/secure/base_url';

```

You gonna get something like this:

```

+-----------+---------+----------+-----------------------+--------------------------------------+
| config_id | scope   | scope_id | path                  | value                                |
+-----------+---------+----------+-----------------------+--------------------------------------+
|         2 | default |        0 | web/unsecure/base_url | http://www.tudominio.com.ar/magento/ |
|         3 | default |        0 | web/secure/base_url   | http://www.tudominio.com.ar/magento/ |
+-----------+---------+----------+-----------------------+--------------------------------------+

```

- Now, change that values for your new url.

```

UPDATE core_config_data SET value = 'http://www.tudominio.com.ar/' WHERE path LIKE 'web/%/base_url';

```

If you run the first query, now you gonna get something like this:

```

+-----------+---------+----------+-----------------------+------------------------------+
| config_id | scope   | scope_id | path                  | value                        |
+-----------+---------+----------+-----------------------+------------------------------+
|         2 | default |        0 | web/unsecure/base_url | http://www.tudominio.com.ar/ |
|         3 | default |        0 | web/secure/base_url   | http://www.tudominio.com.ar/ |
+-----------+---------+----------+-----------------------+------------------------------+

```


That&#8217;s all. 
Of ocurse, the url&#8217;s that I&#8217;ve used are just examples.

Here is the link to his post as well
[http://www.magentocommerce.com/boards/viewthread/27272/](http://www.magentocommerce.com/boards/viewthread/27272/)

---

### Post by ivikas on 2012-09-13
> **ivikas said:**
> When installing on online Server,it may happen timeout and you may be unable to install on the online server.In such case you can install on the local server and port on to online Server.

Here is an excellent article by Damián Culotta from Argentina.Just Recreating his post so it may help someone.


If you want to move your installation form directory or domain, you need to follow this setps.

1) Delete the content of the folder /var

2) Change the values of the file /app/etc/local.xml 
There you can find your connection string data (database user, host and name).

3) Once you got your database uploaded, you need to make some changes.

- Run this query:

```

SELECT * FROM core_config_data WHERE path = 'web/unsecure/base_url' OR path = 'web/secure/base_url';

```

You gonna get something like this:

```

+-----------+---------+----------+-----------------------+--------------------------------------+
| config_id | scope   | scope_id | path                  | value                                |
+-----------+---------+----------+-----------------------+--------------------------------------+
|         2 | default |        0 | web/unsecure/base_url | http://www.tudominio.com.ar/magento/ |
|         3 | default |        0 | web/secure/base_url   | http://www.tudominio.com.ar/magento/ |
+-----------+---------+----------+-----------------------+--------------------------------------+

```

- Now, change that values for your new url.

```

UPDATE core_config_data SET value = 'http://www.tudominio.com.ar/' WHERE path LIKE 'web/%/base_url';

```

If you run the first query, now you gonna get something like this:

```

+-----------+---------+----------+-----------------------+------------------------------+
| config_id | scope   | scope_id | path                  | value                        |
+-----------+---------+----------+-----------------------+------------------------------+
|         2 | default |        0 | web/unsecure/base_url | http://www.tudominio.com.ar/ |
|         3 | default |        0 | web/secure/base_url   | http://www.tudominio.com.ar/ |
+-----------+---------+----------+-----------------------+------------------------------+

```


That&#8217;s all. 
Of ocurse, the url&#8217;s that I&#8217;ve used are just examples.

Here is the link to his post as well
[http://www.magentocommerce.com/boards/viewthread/27272/](http://www.magentocommerce.com/boards/viewthread/27272/)
I just followed step 1 and 2 and it worked for me and the community version magento iam using is magento-1.7.0.2.tar.bz2.

---

### Post by DenHeldert on 2013-05-05
Could you please explain step 3 of the Magento Installation more in-depth?

- How does one create the database, and how does one import the SQL-file into the newly created database?

EDIT: never mind.
I used MySQL Workbench

```
sudo apt-get install mysql-workbench
```

Which made it a breeze.

---

