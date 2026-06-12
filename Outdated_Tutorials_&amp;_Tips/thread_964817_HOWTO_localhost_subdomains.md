---
title: "HOWTO: localhost subdomains"
date: 2008-10-31
forum: Outdated Tutorials &amp; Tips
---

### Post by Stex on 2008-10-31
It's a simple and very useful hack. This was done on Apache2 under Ubuntu 8.10 (Ibex).

------
**For versions of ubuntu earlier than 8.10 see the outdated tutorial: [http://ubuntuforums.org/showthread.php?t=592456](http://ubuntuforums.org/showthread.php?t=592456)**
Both stages have had to be edited for 8.10 as the network manager has disappeared and Apache isn't recognizing the httpd.conf file like it used to.
-------

**1. Add your subdomain(s) to your hosts file:**
Open up a terminal or the Run Application diaogue (Alt+f2), then run the command: [COLOR="DarkGreen"]gksudo gedit /etc/hosts[/COLOR]
(KDE users run [COLOR="DarkGreen"]kdesu kate /etc/hosts[/COLOR] from terminal)
[LIST]
[*]after the first line (ending in "localhost") create a new line
[*]For each subdomain you want write in a new line in the format:
[COLOR="Sienna"]127.0.0.#	name.localhost[/COLOR]
The # must be a unique number for each domain
[*]Save and close. You should now have a file beginning something like:
[/LIST]
e.g:
[COLOR="Sienna"]127.0.0.1	localhost
127.0.0.2	extra.localhost
127.0.0.3	another.localhost[/COLOR]

**2. Apply subdomains to folders:**
Open up a terminal or the Run Application diaogue (Alt+f2), then run the command: [COLOR="DarkGreen"]gksudo gedit /etc/apache2/sites-available/subdomains[/COLOR]
(KDE users run [COLOR="DarkGreen"]kdesu kate /etc/apache2/sites-available/subdomains[/COLOR] from terminal)

For each subdomain you need to add a VirtualHost clause, **you also need to add one for the base localhost**. The clause for each uses the template:
[COLOR="Sienna"]<VirtualHost 127.0.0.#>
ServerName **{Domain (e.g. localhost)}**
DocumentRoot **{Absolute path to folder for this domain (e.g. /var/www/)}**
</VirtualHost>[/COLOR]

Your file should end up looking something like this:
```
<VirtualHost 127.0.0.1>
ServerName localhost
DocumentRoot /var/www/
</VirtualHost>

<VirtualHost 127.0.0.2>
ServerName extra.localhost
DocumentRoot /var/www/extra/
</VirtualHost>

<VirtualHost 127.0.0.3>
ServerName another.localhost
DocumentRoot /var/www/anothersite/
</VirtualHost>
```
Make sure the IPs match up with the ones you defined in the hosts file.
Save and exit.

**3. Restart apache with subdomains:**
Open up the terminal and run:
```
sudo a2ensite subdomians
sudo /etc/init.d/apache2 restart
```
You should now be able to view your subdomains through whatever browser you use (but obviously only from your computer). All done!

**Making use of it:**
I write and test websites on my localhost before uploading them to my public sites and I don't want to go through my code renaming localhost to example.com every time I change something. Nor do I want to use relative URLs as they can get messy once you get folders involved. By putting each site I make on it's own local subdomain I can start all my URLs with a slash which means the URL starts at the base of the subdomain.

That's why I use it anyway.


**-- Notes:**
- Thanks to [firmit's post](http://ubuntuforums.org/showpost.php?p=4545464&postcount=4) for help with the new way of doing this
- I couldn't find a way to apply wildcards to the hosts file (e.g. *.localhost), does anyone know?

---

### Post by Nano on 2008-11-04
Nice one, dude!

---

### Post by Eliot Rosewater on 2009-12-07
Excellent guide. Just got it working in Karmic.

You just have one typo under step 3. The guide reads:

```
sudo a2ensite subdomians
```[FONT=monospace]
It should read
[/FONT]```
sudo a2ensite subdom**ai**ns
```

Thanks again!

---

