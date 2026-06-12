---
title: "Creating a script and running it via sudo"
date: 2008-03-13
forum: Programming Talk
---

### Post by dacool25 on 2008-03-13
Hey there guys,

I'm trying to run a script so that I don't have to type the commands all the time.  Here is a little background to what is for first though:  Well I am using ISPConfig and whenever it writes any files it overdoes any changes that I do to users and permissions within its folders.  So I would like to create a script that will just automate the commands that i do. 

I have a few problems, one of which being that they all have to be run via sudo or su

Anyways, here is my script, can someone help me why it isn't working?  Just bear in mind that i'm not very good with scripts,

Thanks

```
sudo -s adduser webuser webusers
sudo -s chgrp -R webusers /var/www/web1/web
sudo -s chgrp -R webusers /var/www/web2/web
sudo -s chgrp -R webusers /var/www/web3/web
sudo -s chgrp -R webusers /var/www/web4/web
sudo -s chgrp -R webusers /var/www/web5/web
sudo -s chgrp -R webusers /var/www/web6/web
sudo -s chgrp -R webusers /var/www/web7/web
sudo -s chmod -R 775 /var/www/web1/web
sudo -s chmod -R 775 /var/www/web2/web
sudo -s chmod -R 775 /var/www/web3/web
sudo -s chmod -R 775 /var/www/web4/web
sudo -s chmod -R 775 /var/www/web5/web
sudo -s chmod -R 775 /var/www/web6/web
sudo -s chmod -R 775 /var/www/web7/web
```

PS what should i save it as? 

thanks

---

### Post by ruy_lopez on 2008-03-13
Add this at the top:
```

#!/bin/sh

```

Save it prepended with .sh, eg "myscript.sh". Then make it executable:
```

chmod +x myscript.sh

```

Run like this:
```

./myscript.sh

```

Or save in inside ~/bin and run it normally.

EDIT: you don't need "sudo -s". Normal "sudo" should work. It'll ask for the password on the first attempt, then run the rest without asking. Also, when you are finished editing, remove write privileges from the script.

---

### Post by mssever on 2008-03-13
> **dacool25 said:**
>  Anyways, here is my script, can someone help me why it isn't working?  Just bear in mind that i'm not very good with scripts,

First, you can simplify your script a bit. The -s option is unnecessary, and you should probably drop the sudo altogether and call the script with sudo ```
#!/bin/bash
sudo adduser webuser webusers
sudo chgrp -R webusers /var/www/web{1,2,3,4,5,6,7}/web
sudo chmod -R 775 /var/www/web{1,2,3,4,5,6,7}/web

```
First, save your script in a file (shell scripts often have a .sh extension, but executables conventionally have no extension; I prefer none for scripts such as this, but you might disagree), make it executable, and try running it from the command line. Once you get that working, then you can set up your mechanism for automatically calling it. If you want a GUI password prompt, use gksudo; otherwise, use sudo. Of course, if you're calling it from a process already running as root, then you can drop sudo altogether. I know nothing about ISPConfig, so I can't be too specific there.

---

### Post by dacool25 on 2008-03-13
That second way worked perfectly =)

Okay, now I know I'm asking for trouble.  Is there a way to have it display once it has done something?  For example when it adds the user it says adding user blah blah, but thats only because that is what the adduser script does.

Is there a way to have it say something like, changing permissions of so and so and then something like ..done when it is done?

This may be pretty advanced, but can someone put me in the right direction?

Thanks for all of your help!!!

---

### Post by mssever on 2008-03-13
> **dacool25 said:**
> Okay, now I know I'm asking for trouble.  Is there a way to have it display once it has done something?  For example when it adds the user it says adding user blah blah, but thats only because that is what the adduser script does.

Is there a way to have it say something like, changing permissions of so and so and then something like ..done when it is done?
The echo command is what you need. See [FONT=Courier New]help echo[/FONT] for details.

I'm not sure if I understand you fully. If you're wanting to print someting conditionally, you want the [FONT=Courier New]if[/FONT] statement. Read [FONT=Courier New]man bash[/FONT] (or a web based version) for details.

> This may be pretty advanced, but can someone put me in the right direction?Actually, you can do a lot with bash. What you've asked is only the tip of the iceberg. (and even more if you decide to learn a more advanced language, such as Ruby or Python. You might be interested in reading the "Advanced Bash Scripting Guide," which, despite the name, also includes the basics. I don't have a link handy, but you should be able to Google it up easily.

EDIT: echo prints to stdout (normally the terminal). If you want a GUI instead, try zenity (man zenity for details).

---

### Post by dacool25 on 2008-03-13
The echo statements worked pretty good, I think that i'll fool around with if statements later down the line.

Thanks guys!

:guitar:

---

