---
title: "need help configuring Apache2 running on Ubuntu 13.04"
date: 2013-08-02
forum: New to Ubuntu
---

### Post by 1888software on 2013-08-02
**I need help configuring A[B][FONT=arial]pache2 running on Ubuntu 13.04. I follow the directions and this works:[/FONT]**
[COLOR=#0000cd]
[/COLOR][COLOR=#008000]"Checking Apache 2 installation
[/COLOR][/B]

[COLOR=#008000] With your web browser, go to the URI **http**://localhost : if you read "It works!", which is the content of the file /var/www/index.html , this proves Apache works."

[/COLOR][COLOR=#000000]Yes, but I want to drop more folders into /var/www/ such as /var/www/folder1, /var/www/folder2 and so on. [/COLOR]

How?

---

### Post by m3talman on 2013-08-02
> **1888software said:**
> **I need help configuring A[B][FONT=arial]pache2 running on Ubuntu 13.04. I follow the directions and this works:[/FONT]**
[COLOR=#0000cd]
[/COLOR][COLOR=#008000]"Checking Apache 2 installation
[/COLOR][/B]

[COLOR=#008000] With your web browser, go to the URI **http**://localhost : if you read "It works!", which is the content of the file /var/www/index.html , this proves Apache works."

[/COLOR][COLOR=#000000]Yes, but I want to drop more folders into /var/www/ such as /var/www/folder1, /var/www/folder2 and so on. [/COLOR]

How?

If you, by using the term drop, mean that you want to create these folders, the procedure is to:
Open a terminal (ctrl+alt+t), sudo -s (as /var/www/ probably is owned by root)
cd /var/www/
mkdir <foldername>

If you want to move a folder you already got somewhere, you do 
mv <folder to move> /var/www/

---

