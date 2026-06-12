---
title: "New to ubuntu (Wordpress Developer Background)"
date: 2015-09-21
forum: New to Ubuntu
---

### Post by soamz on 2015-09-21
Hi, I normally use Windows WAMP, but now I decided to move to ubuntu for my development machine, and Im looking to make this machine a web server too for my clients dmo websites. 

So, here are few hiccups which I came across. 

1. When I switch on the PC, it shows me this [http://i.imgur.com/33Tz6l7.png](http://i.imgur.com/33Tz6l7.png) and then I have to enter password and then I get this [http://i.imgur.com/TwIyhc0l.jpg](http://i.imgur.com/TwIyhc0l.jpg)

2. When the PC then comes, it asks for password and I enter my password and the computer is on. But I dont think its root login. While installation too, it never told me if its root login or a new user login. Confusing. 

3. Then In followed this tutorial and installed LAMP,
[https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu)

4. Then I installed wordpress using this tutorial,
[https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-on-ubuntu-14-04)

5. But why am I not able to see where are the files getting stored ? 

6. If I try to access /var/www/html/ . Im not able to paste anything. I dont see wordpress folder. I dont know how to access my phpmyadmin and where is everything. 
Completely lost.

---

### Post by Geoffrey_Arndt on 2015-09-21
Just a couple quick points (and others will also fill in the blanks):

>   so, you opted for disk encryption during install.  Not necessary to do that and 90% of Ubuntu users don't.   that's why you get the add'l screens.
>   in Ubuntu, there is only the user account - no root account is active UNTIL someone needs to do an admin function.   Then "sudo" is used.   This is the trend now in Linux . . considered by default to be more secure.   The very first user registered upon install, is the "su-doer" (added to sudo group).   You can also add others to this group if needed.
>   re file write - since /var is owned by root - the user cannot change (write) to those directories outside of their personal /home directories.   To do CRUD to the system folders, one needs to use sudo in the CLI environment.

Maybe it's best to start over, and do the install, with the proper way to setup disks, and setup users.   MUCH simpler.

---

### Post by soamz on 2015-09-21
> **Geoffrey_Arndt said:**
> Just a couple quick points (and others will also fill in the blanks):

>   so, you opted for disk encryption during install.  Not necessary to do that and 90% of Ubuntu users don't.   that's why you get the add'l screens.
>   in Ubuntu, there is only the user account - no root account is active UNTIL someone needs to do an admin function.   Then "sudo" is used.   This is the trend now in Linux . . considered by default to be more secure.   The very first user registered upon install, is the "su-doer" (added to sudo group).   You can also add others to this group if needed.
>   re file write - since /var is owned by root - the user cannot change (write) to those directories outside of their personal /home directories.   To do CRUD to the system folders, one needs to use sudo in the CLI environment.

Maybe it's best to start over, and do the install, with the proper way to setup disks, and setup users.   MUCH simpler.

1. So, no way to switch off the disk encrypt thing now ?
2. Okay cant I login as root, as I will be only using this machine for LAMP work, means hosting wordpress sites, editing files directly, etc. 
Cant I directly open folders files and edit on a code editor thing and save and view changes ?
3. Re installing the Ubuntu again will lose a complete day of work, as it took me whole day to install LAMP, wordpress, everything as Im not very comfortable with terminal line.

---

### Post by Geoffrey_Arndt on 2015-09-21
OK, I just provided a bit of "qucik info" . . . but not complete.    I'm not sure (until checking) IF full disck encryption can be turn-off now.   But others here at Ubuntu Forums will likely know more based on experience.   It is possible it's too late tho.

Also, no need to login as root - ever - in any of the 50 or so "Buntu" distributions.   You CAN do everything you need without it.   Thousands of devs do so everyday.   (just need to learn how).   YES - you can open editors and edit with admin/root rights (sudo gedit /path/to/file).   Instead of gedit, it can be many other editors , IDE's, etc.   Linux and Ubuntu is designed for dev work of all kinds.

And yes, you will have to invest a little time up-front to learn the linux file system and where files, programs, etc. are stored.   There is a ton of info at this website and even more intuitive info on youtube, but you do have to spend a day or two to learn.  It would have been worth you time to do some of this before the install . . . remember, Linux is based on Unix standards, which were around well before Windows and while Mr. Gates was still in junior high school.

This thread will likely have a bunch of responses (more info/better info) so stand by.

---

### Post by soamz on 2015-09-21
For now, if I can simply access where the wordpress is sitting and if I can edit my LAMP hosted files, then Im good to go. 
Any clue ?

How do I first act as root, as I really need to edit something at /var/www/html/

---

### Post by grahammechanical on 2015-09-21
When I need to edit a system configuration file I open the Gedit text editor with this command

```
sudo -H gedit
```

Then I enter my password. All the while the editor is open I am working as administrator but only when using the editor. The rest of the system is still working as a standard user. This is much safer than running the OS using an Administrator/Root account.

If I need to create/delete folders or move folders around and the file manager cannot do that unless I am using administrator priviledges as in the case of creating a folder on another partition, then I run

```
sudo -H nautilus
```

You will see some error messages but ignore them. We all see those messages. We have to be careful when creating files and folders as root/administrator as Root becomes the owner of the file and folder. We need to change the permissions to allow not just access but also to delete and create files in the folder for other users including ourselves when we are not working as administrator. The file manager (nautilus) when launched with sudo -H will let us change those permissions.


Regards.

---

### Post by Geoffrey_Arndt on 2015-09-21
re editing your html file . . . just use nautilus to navigate (multiple ways to do this) to your file and then do as graham advises (using gedit preceded by sudo).    You can change the file and resave it (after making bu of course via nautilus file tools).

But, here is an older (but still 90% accurate) video on doing specifically what you are trying to do . . .    (well worth watching - - unless you live in a restricted zone, Youtube is your friend).   But, I don't know if you'll see any glitches because of the non-standard install you have.


[https://www.youtube.com/watch?v=fLg025p8jNE](https://www.youtube.com/watch?v=fLg025p8jNE)

---

### Post by soamz on 2015-09-21
Okay!
But I already installed wordpress. 
How do I find its path or URL or whatever ?
I simply dont find its location anywhere. 

Isn't there a way to login as root completely ?

IM okay with it, as its my development system only. 
I need to do everything as admin, rather than getting stopped without permission.

---

### Post by Geoffrey_Arndt on 2015-09-21
Well, I'm not a regular CLI user (but I know it has great tools to search for anything on the system.   So, I would open Nautilus (it's also called "files" and should be in your Launcher strip at left of screen (it looks like a file cabinet).

Then,  in the "sidebar" of Nautilus, go down to "computer" and select it.   Then, click on the search window tool and input a key word such as wordpress or something else associated with wordpress.   I don't have it installed, but for a normal install, you would find some of the files in the hidden directories in your /home drive.  (all hidden files and folders can be viewed (ctrl + h) in nautilus).   Other files will also be shown and the paths will be visible in the location column.   Some of those hidden folders/files may be your wordpress config files.

That should let you know exactly where your files are at including the binaries (Remember in linux there are no exe files).

There are for sure much better search methods in the cli - a google search would also show you those inputs.

EDIT:   see here for a search on linux search tools:   [http://www.binarytides.com/linux-find-command-examples/](http://www.binarytides.com/linux-find-command-examples/)

---

### Post by buzzingrobot on 2015-09-22
> **soamz said:**
> Okay!
But I already installed wordpress. 
How do I find its path or URL or whatever ?
I simply dont find its location anywhere. 

Isn't there a way to login as root completely ?

IM okay with it, as its my development system only. 
I need to do everything as admin, rather than getting stopped without permission.

You don't need to be root, or "admin" (a Windows-ism).  Prefacing any command with "sudo" runs that command as if the user was the special user called root. 

Being root won't help you locate where Wordpress was installed. The most common location for executables installed by users is /usr/bin.  Less likely, but possible, are /opt or a directory in the /usr/share tree. Browse those folders with the file manager.  If the Wordpress executable is located in any folder that's in the direcotory path, as any competent install routine would do, it will run fine.

Running as root in Linux is, arguably, more dangerous than running as admin in Windows. Unlike Windows, Unix/Linux are multi-user systems built to support multiple users logged in simultaneously on a single system. That's why there are the structures of permissions and ownership, and home folders, and such.  It's all intended to protect and secure one user and that user's files from other users. It's a benefit, as well, when you're the only user, as almost all of us are.
(One thing that can happen running as root is that applications will typically create configuration files they will store in the user's home directory.  Running as root, they will be deposited in the root user's home directory.  Later, when you are back logged in normally, that application will look for those files in *your* home directory and they will not be there. Also, a number of GUI apps are really not intended to run as root, throwing off innocent and not-so-innocent eorror messages.)

Getting up to speed on how Linux handles users, permissions, etc., versus Windows is a bit of a hurdle.  But, don't try to contort Linux into behaving as Windows.  it won't.

---

### Post by JKyleOKC on 2015-09-22
If you installed Wordpress from the repositories (that is, using Software Center or some other Ubuntu utility) then it will be at /usr/share/wordpress. The wp-content directory, however, may be at /srv/www/wp-content. That's a custom change made by the folk at Debian, from which Ubuntu is derived.

And of course, if you did a manual installation following normal WordPress procedures, then it will be wherever you put it.

Note that the version of WordPress in the repositories is at least three critical updates out of date. After I installed it here to serve as a test platform for the two web sites I maintain out at GoDaddy, I had to manually update my local copy by downloading the zip file and unpacking it into the active wp-content directory. I also had to create symbolic links at several points to force WordPress and the Ubuntu file system to play together nicely. I had to link /var/www/html/wordpress to the /usr/share/wordpress location, since Apache by default is confined to the /var/www path, and also had to link /usr/share/wordpress/wp-content to the folder in /srv/www. After all this, I had to modify permissions on all the WordPress directories and files so that I could update them and do my development.

For permission changes, I set them all to be writable by the "group owner" and set the "group owner" of everything to my personal user group. This could be a security breach but as a simple test platform I didn't consider that a critical matter.

The WAMP background won't be useful under Linux; you'll need the LAMP stack instead. Best search the forums here for "WordPress" to get your feet on the ground. Once you get it all working, then WordPress itself will be pretty much the same thing with which you're already familiar -- but the devil is in the details while you're getting it all set up, and the Devian customization certainly doesn't help!

---

### Post by JKyleOKC on 2015-09-22
> **soamz said:**
> 
5. But why am I not able to see where are the files getting stored ? 

6. If I try to access /var/www/html/ . Im not able to paste anything. I dont see wordpress folder. I dont know how to access my phpmyadmin and where is everything. 
Completely lost.I wrote that long message before reviewing the tutorial that you followed. That was a mistake!

I can now answer both the questions quoted above. You couldn't see where the files were getting stored because the tutorial tells you to put them into "~/wordpress" and then to use the "rsync" command to move everything in that directory into "/var/www/html" -- which did NOT keep the name "wordpress" to identify them.

Because of those two steps in the tutorial, your "/var/www/html" folder is now your "wordpress" folder.

You can disregard everything I wrote about setting up links. There's no need for them.

However, you do need to make yourself the owner of the folder. The tutorial tells you to use the command "sudo chown -R demo:www-data *" while in the "/var/www/html" folder to do so -- but the word "demo" in that line should be replaced by your own user name! Once you do that, you will be able to access the folder, write to it, and perform updates, without all the complication that I inflicted on myself.

Hope this helps!

---

