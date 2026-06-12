---
title: "HOWTO: wildcard localhost subdomains"
date: 2011-04-02
forum: Outdated Tutorials &amp; Tips
---

### Post by Stex on 2011-04-02
Subdomains on localhost are a really useful tool for web developers. It allows separation of cookies and also the ever useful domain root shortcut: Start a URL with a forward slash and it will be relative to domain you put the file on, which means you can copy files to another site without worrying about URLs.

I've written a few tutorials on this in the past, but now have a complete solution that makes adding subdomains just a matter of adding a folder.

To start out you will need to have apache installed, and a folder where you want your subdomains to live. This can either be standard folders or, as I prefer, symlinks to folders.

[COLOR="RoyalBlue"]If you are not familiar with the term symlink then please look it up for this tutorial. It is similar to a shortcut, except that instead of redirecting you it appears to be housing the linked file/folder's contents. To create a symlink in nautilus just drag the target file/folder and hold down shift+ctrl before dropping.[/COLOR]

You will need to rename your folders (or symlinks) to the full domain name that they will relate to. For example: localhost, alpha.localhost, and beta.localhost


**1. Creating wildcard localhost domain**

Generally when making test domains we add it to /etc/hosts, but that does not support wildcards. So instead we'll install a local DNS server and direct all localhost subdomains back to localhost:
```
sudo apt-get install dnsmasq
sudo echo "address=/[COLOR="DarkGreen"]localhost[/COLOR]/127.0.0.1" > /etc/dnsmasq.d/localhost
sudo /etc/init.d/dnsmasq restart
```

[COLOR="DarkGreen"]localhost[/COLOR] is the domain to be redirected, you could put anything in here, such as dev or even example.com

To get Ubuntu to use this new DNS server we need to add a rule to the networking tool dhclient:
```
gksudo gedit /etc/dhcp3/dhclient.conf
```
Around line 20 of that file will be the line:
```
#prepend domain-name-servers 127.0.0.1;
```
All you have to do is delete the leading #, save & exit. For the changes to take effect you will need to right click on your networking indicator to disable and then re-enable networking.

Now all requests to .localhost will be directed back to 127.0.0.1, but Apache still doesn't know what to do with them.


**2. Apache wildcard localhost domain**

These instructions are easier to follow graphically. To open the file browser (nautilus) as root pres Alt+f2 and run the following command:
```
gksudo nautilus /etc/apache2
```

**2.1 Apache wildcard module**

To handle wildcard subdomains Apache requires the module vhost_alias, this is already installed with Apache but may need to be enabled. To do this go to /etc/apache2/mods-available in there should be the file **vhost_alias.load**. You need to symlink to this file in the /etc/apache2/mods-enabled folder (open up mods-enabled in a new tab then drag&drop the file to it with shift+ctrl held down).

**2.2 Apache configuration**

First we need to remove the current rules that make localhost work. Go to /etc/apache2/sites-enabled and delete the 000-default file (don't worry, it's a symlink, the original will still exist in sites-available).

Now we can write our own rules for the wildcard domains. Go to /etc/apache2/sites-available and create a new file, then open it to edit the contents. Here is a very simple example file:
```
# Remember to enable: vhost_alias
# Create folders in [COLOR="DarkGreen"]/path/to/sites[/COLOR] with full domain name (localhost, alpha.localhost, etc.)

<VirtualHost *:80>
	
	VirtualDocumentRoot [COLOR="DarkGreen"]/path/to/sites[/COLOR]/%0
	VirtualScriptAlias [COLOR="DarkGreen"]/path/to/sites[/COLOR]/%0
	
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory [COLOR="DarkGreen"]/path/to/sites[/COLOR]/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>
    
</VirtualHost>

```

Make sure you replace [COLOR="DarkGreen"]/path/to/sites[/COLOR] with the full path to the folder where your subdomain folders (or symlinks) live.

[COLOR="RoyalBlue"]This configuration file, like the default, leaves your local webserver unsecured, which means anyone on your network can view the sites on it. If you don't want this then look up allow/deny configuration for Apache and put them in the second Directory section.[/COLOR]

**2.3 Enable Apache configuration**

Now we enable our new configuration file, just make a symlink to it in the /etc/apache2/sites-enabled folder.

All that is left is to restart apache for the settings to take hold. Just run:
```
sudo /etc/init.d/apache2 restart
```


**3. All Done**

If all went well then you should be able to put anything.localhost into your browser and get a file not found error. Just create a folder with that name in your sites directory and it should instantly work!

If you kept the domain name as localhost then you will need to move your original website files into a folder in the sites folder called localhost for them to work again.

---

