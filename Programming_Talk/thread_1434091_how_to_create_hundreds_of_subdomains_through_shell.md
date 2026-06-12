---
title: "how to create hundreds of subdomains through shell"
date: 2010-03-19
forum: Programming Talk
---

### Post by 007casper on 2010-03-19
I would like to create hundreds of subdomains from a list I have on a text file. I figured this could be done through the shell, but I am not sure how to go about it.

What is the best way to create hundreds of subdomains through shell?

Thank you.

---

### Post by 007casper on 2010-03-19
Maybe I am not being clear, or the question is too simple for the community. :-({|=](*,)

---

### Post by Hellkeepa on 2010-03-19
HELLo!

You have to be a bit more specific, I'm afraid. Starting with what kind of web server you're using, and the format of this text file. Along with any other details that you want to have the script do, such as which port numbers to set up, things that should differ between the different domains, and such things.

You also need to be a lot more patient. Two hours is almost nothing on a global forum, like this. Give it at least 3 days before bumping a thread, to avoid coming off as nagging. ;-)

Happy codin'!

---

### Post by 007casper on 2010-03-31
oh, I was excited about my mini project, no nagging... 

but wondered if I wasnt being cleared at all. I also thought it might be too
easy for some after reading some of the threads over here.

I was wondering if it is possible to create a bash script.  

I just want to create series of subdomains from a simple text/csv file.

lets say this text file is called subdomain.csv and it list all the subdomains
one by one.
-
subdomains
channel1.maindomain.com
channel2.maindomain.com
channel3.maindomain.com
.
.
.
.
channel250.maindomain.com
-
The server is debian. 

will be using php.  

I'd love to load wordpress to each subdomain.
Then, create  database name, lets say "achannel01", "bchannel02" etc... on a specific domain such as mysql.maindomain.com, with specific given username, and password for the msyql wordpress database.

any suggestions how I can go about this.  

Thank you.

---

### Post by Hellkeepa on 2010-03-31
HELLo!

I'm going to guess that the web server you're using is Apache. (Which was what I was asking for, not the distro, btw.)

Anyway, what you need to do first is to set up a template for the sub domains. Use the "default" file in "/etc/apache2/sites-available" as your base, and just remove the superfluous entries for  "/" and "doc". In this file there are four places where you need to insert the domain-name; Two for the actual domain-association itself, and two to point to the document root (could use the username instead, for this part).
Then you need to set up a MySQL script template, that creates a new database, and then grants (and creates) the correct user with privileges on the DB, before it finally flushes the privileges.
Next you need to create the script that reads the domain source file, and returns the entries as an array with one entry per newline. Then you need to loop through this array, and to the following for each of the domains:
[li=1][*]Generate the username and password.
[*]Read the beforementioned files.
[*]Add the correct data at the correct places.
[*]Writes the new apache config file, and adds a symlink to it in the "sites-enabled" directory.
[*]Execute the MySQL queries.[/li]
After the loop is finished it'll have to restart Apache (gracefully), to make it update its configuration.

If you want to add more features to this, like a Wordpress installation and a FTP/SSH user, it should be a simple case to just expand upon the script after you've got it working. The principles are the same, just with some added file copying for the Wordpress source files.

Happy codin'!

---

