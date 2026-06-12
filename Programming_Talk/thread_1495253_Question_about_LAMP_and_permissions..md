---
title: "Question about LAMP and permissions."
date: 2010-05-27
forum: Programming Talk
---

### Post by CoreInsanity on 2010-05-27
I have searched around and I am not quite sure what the best solution is for this, so I figured I would ask here. Who knows, maybe some one else will have this question too.

Basically, I have seen people tell you to modify permissions on stuff, or just move the document root in apache, and so on. But none of them seemed to be applied to my case.

I saw some one said you should just sudo cp the files into the /var/www directory after you modify them, but this would get to be kind of annoying for me. I am setting LAMP up as a development environment for my PHP code - nothing more. No one but me will have access to this.

Also, I am not wanting my document root in the default /var/www folder, instead I want to stick it in one of my other internal hard drives (I already have it pointing there: /media/p/ where p is my projects drive/partition).

What is the best solution to fit what I am wanting to do?

Thanks,
Thomas.

---

### Post by nmccrina on 2010-05-27
I no longer have Apache set up (the computer I was using as a server got commandeered :( ) so I'm just going by memory, but in Ubuntu you can create a file in /etc/apache/sites-available that redirects traffic coming from 127.0.0.1 to /path/to/project. There should be an example site file already in sites-available. Then you just run

```
sudo a2ensite <name-of-file-in-sites-available
```

which basically just creates a symlink in /etc/apache/sites-enabled to the file you just created in sites-available, "enabling" the site. Restart apache, and traffic coming from 127.0.0.1 (i.e. you) will go to wherever you specified. 

Just use the file already there as a guide and refer to the [apache docs]("http://httpd.apache.org/docs/2.2/") when in doubt.

Hopefully that's what you were asking ;)

---

### Post by CoreInsanity on 2010-05-27
I thank you for your reply :)

I actually have that part setup, though. My main issue right now is figuring out which is the best way to go about assigning permissions to the drive I am sticking the files on.

See, right now it redirects but gives an error when going to the site:

```

Forbidden

You don't have permission to access / on this server.

```

I am mostly wondering what the best solution to this is :)


From what I understand this issue is between the permissions on the driver/folder/files in question, and not directly apache.

Thanks,
Thomas

---

### Post by nmccrina on 2010-05-27
Hang on, I'm going to try it real quick on my computer and see what happens :)

---

### Post by CoreInsanity on 2010-05-27
Alright, thanks for the help :)

If it's any help or makes a difference, the drive was freshly formated to ext4 with the option "Take ownership of filesystem" checked.

---

### Post by nmccrina on 2010-05-28
Wow, sorry it took so long. I was able to change the documentroot to a directory on my main hard drive, but it still failed on the USB drive as you described, using the exact same settings. Then I realized my USB drive is FAT, so I don't know if that affects anything. The only other thing I can think of is maybe changing the permissions on your DocumentRoot of choice to 777 temporarily, just to see if it works.

---

### Post by CoreInsanity on 2010-05-28
It's no problem, I thank you for looking into it in this much depth.

When you say USB Device, I have to wonder, is media not the place for mounted internal drives?

The drive I am using it on is a 500GB internal. I don't have anything installed on it, so if that is the case would making a sub directory on it fix that problem?

IE: /media/p/somesub/?

Edit: Just saw your edit :)

Yea, I'm not really sure what to do :/

Thanks,
Thomas.

---

### Post by CoreInsanity on 2010-05-28
Decided to make a new reply to update the post:
Just saw your edit, again.

Alright, I ran a

```
sudo chmod 777 p
``` 

and it seems to work fine. Made an index.php and put the standard phpinfo in it and that works.

I will stick to this for now, until a better alternative comes a long (From what I have heard leaving it as 777 can be bad, as some one could easily deface my website. But it should be ok, as it's just a dev environment.)

Thanks for your help, :)
Thomas

---

### Post by nmccrina on 2010-05-28
```

```> **CoreInsanity said:**
> It's no problem, I thank you for looking into it in this much depth.

When you say USB Device, I have to wonder, is media not the place for mounted internal drives?

The drive I am using it on is a 500GB internal. I don't have anything installed on it, so if that is the case would making a sub directory on it fix that problem?

IE: /media/p/somesub/?

Edit: Just saw your edit :)

Yea, I'm not really sure what to do :/

Thanks,
Thomas.

I just tried my ext4 external hard drive, and it works. Here's the virtual host thing I used (placed under sites-available):

```

NameVirtualHost *:80

<VirtualHost *:80>
	ServerName 127.0.0.1
	DocumentRoot /media/b81bfd6c-ceaa-4518-8c91-4c777e80431d/www
	
	<Directory />
		Options FollowSymLinks
		AllowOverride None
		Order deny,allow
		allow from all
	</Directory>
</VirtualHost>


```

Edit: just saw your post. Yeah, I just suggested 777 so you could get *something*. :D FWIW, the permissions that I used for the index.html above were 644 (755 for directories of course) i.e. normal.

---

### Post by CoreInsanity on 2010-05-28
Alright, I just formated the drive again (To reset all the permissions, as I didn't know the bases and had nothing on it anyway) and then made a testsite, disabling my old one.

I based my testsite format off of yours:
```

NameVirtualHost *:80

<VirtualHost *:80>
	ServerName 127.0.0.1
	DocumentRoot /media/p
	
	<Directory />
		Options FollowSymLinks
		AllowOverride None
		Order deny,allow
		allow from all
	</Directory>
</VirtualHost>

```

And it still gets the permissions error. So it looks like it will just have to have a chmod 777 on the /p so it works, for now anyway.


I thank you again for your help :)

---

