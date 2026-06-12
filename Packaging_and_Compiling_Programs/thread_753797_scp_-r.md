---
title: "scp -r"
date: 2008-04-13
forum: Packaging and Compiling Programs
---

### Post by frankos44 on 2008-04-13
It would be extremely convenient to be able to copy only php files using scp.

scp -r /var/www/myfolder user@ipadress:/var/www/myfolder works OK but it copies everything including images etc..

What i would like is something like this:

scp -r /var/www/myfolder/*.php user@ipadress:/var/www/myfolder, but this of course does not work.

Any ideas please?

---

### Post by jaddle on 2008-04-13
Lots of ways to copy just the php. Easiest I can think of is using 'find', like this:

scp `find -name *.php` [email]me@remote.host[/email]:/dir/

Note that those are backticks, not normal single quotes.

You could also use something like rsync with the --exclude switch to transfer everything except jpgs.

---

### Post by frankos44 on 2008-04-13
> **jaddle said:**
> Lots of ways to copy just the php. Easiest I can think of is using 'find', like this:

scp `find -name *.php` [email]me@remote.host[/email]:/dir/

Note that those are backticks, not normal single quotes.

You could also use something like rsync with the --exclude switch to transfer everything except jpgs.

Thanks for the reply, much appreciated.

I think rsync might be the better option but I  use scp out of habit I guess. Can I make rsync ignore symbolic linked folders?

---

### Post by unutbu on 2008-04-13
Note that rsync does not use encryption while scp does.

---

### Post by frankos44 on 2008-04-13
> **unutbu said:**
> Note that rsync does not use encryption while scp does.

It does if you use ssh as follows:

$ rsync -rae ssh /var/www/myfolder/*  user@ipaddress:/var/www/myfolder

I remember now while I don't use rsync - it's painfully slow. This is probable due to the initial delay with ssh connection being repeated for each file it transfers or checks.

What I would really like is:

Securely recursively copy all files changed since the last upload but  exclude symbolic linked files and folders.

---

### Post by jaddle on 2008-04-13
the -l option causes rsync to copy links as links, instead of copying their contents.

Also, rsync uses ssh by default these days, so you don't have to worry about encryption. With lots of files, it can take a while to start transferring since it makes lists, and then checks if the file exists and is up to date. However, it can save a lot of time if most of the files are already copied, and just a few are missing or have changed - especially over a slow connection.

I'm surprised that you find it painfully slow - I haven't noticed a big difference in speed. It certainly doesn't have to redo the ssh connection for each file - that would definitely be sluggish!

---

### Post by unutbu on 2008-04-13
Thanks for the info about rsync, jaddle and frankos44!

Here is another way to do it which I think satisfies the other criterion you mentioned:

```
find /var/www/myfolder/ -depth -type f -mtime -7 -name *.php -print0 | tar --create --null --files-from=- | ssh user@ipaddress 'cd /var/www/myfolder; tar xvf -'
```

This ignores symlinks.
This will only copy files of the form *.php modified within the last 7 days.
It will handle files with spaces in its name properly.

---

### Post by frankos44 on 2008-04-14
> **unutbu said:**
> Thanks for the info about rsync, jaddle and frankos44!

Here is another way to do it which I think satisfies the other criterion you mentioned:

```
find /var/www/myfolder/ -depth -type f -mtime -7 -name *.php -print0 | tar --create --null --files-from=- | ssh user@ipaddress 'cd /var/www/myfolder; tar xvf -'
```

This ignores symlinks.
This will only copy files of the form *.php modified within the last 7 days.
It will handle files with spaces in its name properly.

Thanks, That is a very neat trick indeed. Only problem now is its creates a folder /var/www/var/www/........... and puts the updated files in another folder tree.

---

### Post by frankos44 on 2008-04-14
> **jaddle said:**
> the -l option causes rsync to copy links as links, instead of copying their contents.

Also, rsync uses ssh by default these days, so you don't have to worry about encryption. With lots of files, it can take a while to start transferring since it makes lists, and then checks if the file exists and is up to date. However, it can save a lot of time if most of the files are already copied, and just a few are missing or have changed - especially over a slow connection.

I'm surprised that you find it painfully slow - I haven't noticed a big difference in speed. It certainly doesn't have to redo the ssh connection for each file - that would definitely be sluggish!

Thanks, I never realised. After some experimenting,  this seems to work well.

rsync --verbose --links --delete-excluded -ae ssh /var/www/myfolder/* user@ipaddress:/var/www/myfolder

It only copies files with a newer date/time.
It deals with symbolic links.
Removes orphaned files.

Initially it was slow compared to scp when myfolder was empty on the target server but after that only changes are sent so became the faster option.

---

### Post by kevdog on 2008-04-15
I found ssh can connect to site and change to directories with spaces in the path -- add single quotes -- however scp is unable to do this.  Any workaround possible.  The only way that I have managed to get around this was to connect to the remote server, run a script to replace spaces with underscores, sync or transfer the files, and then run a script to replace underscores with spaces.  Really a very clumsy workaround.

---

### Post by unutbu on 2008-04-15
Could you describe your problem some more? I was not able to reproduce it:
```

% cd
% mkdir source
% mkdir target
% cd source
% mkdir dir\ with\ spaces
% cd dir\ with\ spaces/
% touch file\ with\ spaces
% cd
% ls -lR source/
source/:
total 4
drwxr-xr-x 2 dark dark 4096 2008-04-15 10:24 dir with spaces

source/dir with spaces:
total 0
-rw-r--r-- 1 dark dark 0 2008-04-15 10:24 file with spaces
% scp -r source/*  dark@matter:/home/dark/target
dark@matter's password: 
file with spaces                              100%    0     0.0KB/s   00:00    
% ls -lR target/
target/:
total 4
drwxr-xr-x 2 dark dark 4096 2008-04-15 10:25 dir with spaces

target/dir with spaces:
total 0
-rw-r--r-- 1 dark dark 0 2008-04-15 10:25 file with spaces

```

---

### Post by frankos44 on 2008-04-15
> **kevdog said:**
> I found ssh can connect to site and change to directories with spaces in the path -- add single quotes -- however scp is unable to do this.  Any workaround possible.  The only way that I have managed to get around this was to connect to the remote server, run a script to replace spaces with underscores, sync or transfer the files, and then run a script to replace underscores with spaces.  Really a very clumsy workaround.

I cant reproduce this either.

I created a folder called "This is a folder" which contains a file called "This is a test"

$ scp -r This\ is\ a\ folder/ user@domain:~

and it worked fine.

I never include spaces in files or directory names anyway.. Reminds me of "My Documents" or "My Pictures" or "Letter to my mate round the corner.doc"

---

### Post by komaruloh on 2008-12-23
> **unutbu said:**
> Thanks for the info about rsync, jaddle and frankos44!

Here is another way to do it which I think satisfies the other criterion you mentioned:

```
find /var/www/myfolder/ -depth -type f -mtime -7 -name *.php -print0 | tar --create --null --files-from=- | ssh user@ipaddress \'cd /var/www/myfolder; tar xvf -\'
```

This ignores symlinks.
This will only copy files of the form *.php modified within the last 7 days.
It will handle files with spaces in its name properly.



I found that this is the answer to my problem.
My thanks to frankos44, you help me up.

---

