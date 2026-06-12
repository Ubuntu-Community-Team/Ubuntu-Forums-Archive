---
title: "Newbie chmod question. Permissions for /var/www/HERE"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by Swerve1000 on 2008-11-17
Hi,

I have just installed Ubuntu Server Edition and plan to host some sites on it, which will be visible to the public.

I want to create one directory for each site, within the var/www directory, ie:

var/www/site1
var/www/site2



I created the first directory using:

sudo mkdir site1

Whilst I was located inside /var/www , 

as mkdir site1 gave permission denied.


But when I tried to add files into it, I received 'permission denied'.

So I tried the following chmod command:

sudo chmod 775 site1

To try and give my account permissions on the directory.

But when I tried to copy files into the directory from WinSCP I again received 'permission denied'.



So I'm wondering where I'm going wrong.

Any help is greatly appreciated!

Thanks!

---

### Post by snova on 2008-11-17
Simple. You don't own this directory, root (the administator) does.

You could reconfigure Apache to put the document root in your home directory, but I don't know whether this is considered a "good idea".

---

### Post by DGortze380 on 2008-11-17
> **Swerve1000 said:**
> Hi,

I have just installed Ubuntu Server Edition and plan to host some sites on it, which will be visible to the public.

I want to create one directory for each site, within the var/www directory, ie:

var/www/site1
var/www/site2



I created the first directory using:

sudo mkdir site1

Whilst I was located inside /var/www , 

as mkdir site1 gave permission denied.


But when I tried to add files into it, I received 'permission denied'.

So I tried the following chmod command:

sudo chmod 775 site1

To try and give my account permissions on the directory.

But when I tried to copy files into the directory from WinSCP I again received 'permission denied'.



So I'm wondering where I'm going wrong.

Any help is greatly appreciated!

Thanks!

If you are logged on as the first user you created on the system, then something is wrong, we'll have to look into it.

If you are not logged on as the first user you created on the system, then log on as that first user and try again. You need to have sufficient sudo privileges to access those directories.

---

### Post by karlr42 on 2008-11-17
Same issue I helped you with earlier :D
Either stop using sudo to execute commands or start logging in as root.

---

### Post by Bölvaður on 2008-11-17
I dont know if it is wise but you can change the owner of var/www/site1 to you with ```
sudo chown user var/www/site1
```

---

### Post by Swerve1000 on 2008-11-17
Thanks for the advice!

I was thinking I may have to change permissions on the www directory it'self, but I thought that is wrong.

Just adding permissions to site1 should do it, perhaps I should add a recursive switch to the command?

---

### Post by halitech on 2008-11-17
> **karlr42 said:**
> start logging in as root.

bad idea telling someone to log in as root. First, big security risk and second, not supported on these forums.

OP. If you are creating files and directories in that folder, you should have done```
sudo chown -R yourusername site1
```as well as ```
sudo chmod -R 755 site1
```
the -R will tell it to give the same permissions to all files and folders inside the one you are listing

---

### Post by jenkinbr on 2008-11-17
> **snova said:**
> Simple. You don't own this directory, root (the administator) does.

You could reconfigure Apache to put the document root in your home directory, but I don't know whether this is considered a "good idea".
I don't know if this is a good idea for a public server.

Although it works great on my test rig at home.  I have the doc root set to /home/jenkinbr/www and apache2 is configured to run as user: jenkinbr group: jenkinbr.

Again, I wouldn't do this on a public web server though.

---

### Post by Swerve1000 on 2008-11-17
Brillant!

Thanks everyone!

The command listed by halitech worked exactly, correct permissions and everything.

karlr42 helped explain to me earlier that whoever created the directory, had r/w/x permissions, but within /var/www I was denied permission to create directories, hence my using the sudo prefix, asuming I would be given permissions to the directory I created, but it seemed not to work. So I attempted to alter the permissions to try and include my installation account.

Will have to look into the chown command.

Awesome, props to everyone :)

---

### Post by halitech on 2008-11-17
if you use sudo to create a folder, then root is actually creating the folder so root would still have ownership of the folder and your normal user would still be denied access. 

Another way of doing things would be to hit ALT-F2 and type```
gksu nautilus
``` and browsing to the folder and creating your folders with that and then right click and go to the permissions folder and changing them. NOTE: Be very careful using nautilus in root mode as you can really mess things up.

---

### Post by jenkinbr on 2008-11-17
Been there done that.  +1 on the be careful with root.

---

### Post by louieb on 2008-11-17
its your website you should own it. That has the advantage that you don't need to login as root or use sudo to modify it. The only thing you need to use sudo for is a one time  change to the apache **document root** to wherever you  want to store the files for your website. The defaut is /var/www  just change that to some folder in your home directory or some place  else. 
for example I have a 2nd harddrive it has one partition mounted om /media/stuff.  The html,  photos, php code  is stored in a directory www so my document root reads   
```
DocumentRoot /media/stuff/www/



```
So in my case /meda/stuff/www acts just like /var/www except that I own it and can modify the contents without useing sudo or loggging on as root. 

You could keep it in your home folder just by chaging the document root to 
```
DocumentRoot /home/Swerve1000/www/
```You own it and apache doesn't care where the files for your website are you just need to tell it where.

Edit also need to to change the directory statment from ```
<Directory /var/www/> 
to
<Directory /media/stuff/www/>

```

Good stuff here explaining it. [ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

