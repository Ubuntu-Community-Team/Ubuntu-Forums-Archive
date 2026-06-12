---
title: "How do you post your html/php files to /var/www?"
date: 2005-09-16
forum: Programming Talk
---

### Post by vayu on 2005-09-16
I've got Apache, PHP and MySQL all installed and working well.  I've been using "sudo cp" in terminal mode to copy my php and html files into /var/www to make them show up on my browser under localhost.  Is there an easier GUI way to do this?  This system is just for my local use, after development I will upload them to a server connected to the web, so there are no security issues to be concerned about,  I'm only interested in convenience.

---

### Post by KingBahamut on 2005-09-16
[QUOTE=vayu]I've got Apache, PHP and MySQL all installed and working well.  I've been using "sudo cp" in terminal mode to copy my php and html files into /var/www to make them show up on my browser under localhost.  Is there an easier GUI way to do this?  This system is just for my local use, after development I will upload them to a server connected to the web, so there are no security issues to be concerned about,  I'm only interested in convenience.[/QUOTE]
 I think NVU supports such a "publishing"-esque type feature. Bluefish does too I think. You could probably use either of those. Quanta Plus may as well. 

I have a directory that I dump all my finished stuff into, and a shell script that dumps them into the proper folders on /var/www , so id never use such a feature in either of the above mentioned progs.

---

### Post by fjleal on 2005-09-16
[QUOTE=vayu]This system is just for my local use, after development I will upload them to a server connected to the web, so there are no security issues to be concerned about,  I'm only interested in convenience.[/QUOTE]
Try "chown <your_user_name>:<your_user_name> /var/www". Also ensure others can read the files. This way, you may freely copy your files to /var/www, and edit'em directly from there.

---

### Post by JEDIDIAH on 2005-09-16
Why not just put your own development stuff under ~/public_html and have [http://localhost/~you](http://localhost/~you) be where you test all of your html/php?

---

### Post by vayu on 2005-09-17
Thanks everyone for all the good ideas.

[QUOTE=JEDIDIAH]Why not just put your own development stuff under ~/public_html and have [http://localhost/~you](http://localhost/~you) be where you test all of your html/php?[/QUOTE]

Are these directory assignments already set up through Apache or do I have to set Apache to look there?

---

### Post by der_joachim on 2005-09-17
[QUOTE=JEDIDIAH]Why not just put your own development stuff under ~/public_html and have [http://localhost/~you](http://localhost/~you) be where you test all of your html/php?[/QUOTE]

Ooohhh I know this one! I had some issues with file writing in PHP. When the webserver tries to write a file in your homedir, by default that will not be possible.  A simple chmod dows the trick, hoewver. ;)

---

### Post by mostwanted on 2005-09-17
[QUOTE=vayu]I've got Apache, PHP and MySQL all installed and working well.  I've been using "sudo cp" in terminal mode to copy my php and html files into /var/www to make them show up on my browser under localhost.  Is there an easier GUI way to do this?  This system is just for my local use, after development I will upload them to a server connected to the web, so there are no security issues to be concerned about,  I'm only interested in convenience.[/QUOTE]

what about $ sudo nautilus?

---

### Post by deuce868 on 2005-09-17
Where are your dev files now? Why not just setup a folder in /home/$user/webdev

Then in your apache2 config change the web root from /var/www to /home/$user/webdev

Let's all be happy now.

---

### Post by JEDIDIAH on 2005-09-19
[QUOTE=vayu]Thanks everyone for all the good ideas.



Are these directory assignments already set up through Apache or do I have to set Apache to look there?[/QUOTE]

    I don't remember. I'm pretty sure it's in the standard httpd.conf, 
even if it's commented out to begin with. Either way, this is a one 
time change as root instead of ongoing maintenance.

Here's the relevant section from my httpd.conf file:

```
#
# UserDir: The name of the directory which is appended onto a user's home
# directory if a ~user request is received.
#
<IfModule mod_userdir.c>
    UserDir public_html
#
# Control access to UserDir directories.  The following is an example
# for a site where these directories are restricted to read-only.
#
    <Directory /home/*/public_html>
        AllowOverride FileInfo AuthConfig Limit
        Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
        <Limit GET POST OPTIONS PROPFIND>
            Order allow,deny
            Allow from all
        </Limit>
        <Limit PUT DELETE PATCH PROPPATCH MKCOL COPY MOVE LOCK UNLOCK>
            Order deny,allow
            Deny from all
        </Limit>
    </Directory>
</IfModule>
```

---

### Post by majikstreet on 2005-09-19
[QUOTE=JEDIDIAH]
```

    <Directory /home/*/public_html>
       
```[/QUOTE]

I believe that is the relevant part :)

---

### Post by blastus on 2005-09-20
Why not create a soft link in /var/www to a directory in your home directory? That way you don't have to mess with permissions or chown /var/www.

---

### Post by David Marrs on 2005-09-20
[QUOTE=blastus]Why not create a soft link in /var/www to a directory in your home directory? That way you don't have to mess with permissions or chown /var/www.[/QUOTE]
 I was about to suggest the same thing. :)

---

### Post by Rick Z on 2007-08-23
Hi I was reading how to create php & mysql in this forum.  How do you create softlink?  I am a newbie in linux.  thanks.

---

### Post by mahalie on 2007-08-23
> **deuce868 said:**
> Where are your dev files now? Why not just setup a folder in /home/$user/webdev

Then in your apache2 config change the web root from /var/www to /home/$user/webdev

Let's all be happy now.

The reason I'd rather not do that is that it's for my corporate intranet and someday I won't be here. If they ever hire another web-dev they should be given ownership rights to /var/www and not some redirect to a user directory. Did that make sense? Or if I change the web root from /var/www to /home/$user/webdev, will everything be preserved if later another webdev came along (suppose I left my job) and it was changed to /home/$newuser/webdev and chown was run for the new user on all the files/dirs copied from my current user to the new  user account?

In retrospect, I wish I'd created my account as a generic ITStaff account or Webmaster account instead of my network username. Then pointing to home/webmaster/ for instance, wouldn't be bad.

In the meantime, the following (with the really important recursive switch) finally solved my FTP problem (I wasn't able to upload to certain subdirectories). 

```
chown myusername:myusername /var/www -R
```

---

