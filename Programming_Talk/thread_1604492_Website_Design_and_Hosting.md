---
title: "Website Design and Hosting"
date: 2010-10-24
forum: Programming Talk
---

### Post by beegary on 2010-10-24
Sorry if this is the rwong place for such a question....
I want to create a website to do the following:

Part 1
Homepage, Contacts, Web Enquiry Form


Part 2
Login Page, Form Completion incl. Job Request and File Upload, Job History


I dont currently have a domain or server to host my website. I have some experience in: Shell Scripting, basic WSYWIG Website design, and Database Design. 
I have done some tutorials on Python and Java (using Netbeans).
Where should I start?  I could complete Part1 by using a basic web design tool but I want to start in the right place to enable Part2 (and part3 when it exists).
I would like to hear some opinions on Tools and Languages available on Ubuntu 10.10.
I would assume that the best way to go about ti would be to design the site etc then when it works as I expect deploy it to a hosted server?

---

### Post by worksofcraft on 2010-10-24
oops soz... double post

---

### Post by worksofcraft on 2010-10-24
You can set up your own web server using a so called LAMP stack, that's Apache, MySql and Php running on Linux.

I found the easiest way to develop is to do this on a virtual PC and set it up with it's own IP address on your own virtual network. You can even set it up to be accessible from the www by opening your IP address.

I found some royalty free virtual appliances that are complete and ready to use for exactly this on the web. Just google for Turnkey Lamp.

---

### Post by lykeion on 2010-10-24
Set up a local LAMP server: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
Configure it and make sure PHP work. 

Next I'd setup the database. Figure out whata data needs to be in db, and plan how to structure this data in tables.
W3schools have a good intro to SQL: [http://www.w3schools.com/sql/default.asp](http://www.w3schools.com/sql/default.asp)

Check out the relevant sections in the W3school PHP tutorial: [http://www.w3schools.com/php/default.asp](http://www.w3schools.com/php/default.asp)
[LIST]
[*]PHP Forms
[*]PHP File Upload
[*]PHP Database
[/LIST]

A tip is to avoid wysiwyg html editors and write html manually, that way you'll learn a whole lot faster.

---

### Post by juancarlospaco on 2010-10-24
Dont install nothing, just download, unpack and run [http://www.web2py.com/](http://www.web2py.com/)

---

### Post by Wistful on 2010-10-24
For design/development: **[COLOR="Red"]Drupal[/COLOR]** -> [http://drupal.org/](http://drupal.org/)

[https://secure.wikimedia.org/wikipedia/en/wiki/List_of_content_management_systems](https://secure.wikimedia.org/wikipedia/en/wiki/List_of_content_management_systems)
[http://www.cmsmatrix.org/](http://www.cmsmatrix.org/)

For hosting: [http://www.godaddy.com/](http://www.godaddy.com/) (use code: LINUX or LINUX20 to get a discount)

---

### Post by beegary on 2010-10-24
Ideal, thanks everyone. Plenty to keep me going here. I will let you know how I get on.....

---

### Post by kbryk on 2010-10-25
If this is a test website, I would go with LAMP setup.

If you are looking to make this accessible publicly without fetching the IP of the computer every time your ISP serves out a new address I would go with [http://www.dyndns.com/](http://www.dyndns.com/). 

If you are looking for something a little more dedicated, GoDaddy is a good option, but there are others out there that may suite you better.

---

### Post by rcayea on 2010-10-26
Well,

I was in the same position and I simply went to webhostingpad.com, based on reviews. I bought my ipaddress and domain name from them. I started learning html and css. And, I am currently early on in the learning process but it is still fun. I suggest this route.

---

