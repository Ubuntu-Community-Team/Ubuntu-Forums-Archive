---
title: "GmailFS how to for Ubuntu 5.10"
date: 2006-03-05
forum: Outdated Tutorials &amp; Tips
---

### Post by Prospero2006 on 2006-03-05
Hello folks:

-Gmailfs essentially creates a virtual 2 gig hard drive on your desktop using a google gmail account. 

-I'm not one to cross-post generally, but a good suggestion was made in a different forum to put this here. I didn't think about it, but yes. This is definitely where this 'how to' belongs. I had to poke at it all day to get it right, and I really don't think anyone has gotten it right yet.  (I have a feeling some of the alterations here are unnecessary, but just go ahead and follow it step by step. These directions make Gmailfs  work very nicely under Breezy 5.10.)


All packages are installed from source except FUSE.

So, if you have gmailfs or libgmailfs installed, remove them now.

(Keep Fuse.)

-Download libgmail from [http://libgmail.sourceforge.net/](http://libgmail.sourceforge.net/)

-Download gmailfs-0.7.2.tar.gz from the author's site

-Unpack those directories and copy everything into /usr/local/bin

-Copy gmailfs.conf to /etc

-Change username/password in gmailfs.conf

Open up:
/usr/lib/python2.4/site-packages/fuse.py in a text editor:
-Line 68
-Replace:
```
 self.mountpoint = None 
```
```
 self.mountpoint = "YOUR_MOUNTPOINT_HERE"
```

Mount it once with this command

mount.gmailfs "/usr/local/bin/libgmail.py" YOUR/MOUNT/POINT/ -o username=YOUR_ACTUAL_USERNAME,password=YOUR_ACTUAL_PASSWORD,fsname=zOlRRa

type:

chmod 777 YOUR/MOUNT/POINT
umount YOUR/MOUNT/POINT

Fstab entries won't work so:

Add this line to /etc/init.d/bootmisc.sh at the end:

mount.gmailfs "/usr/local/bin/libgmail.py" YOUR/MOUNT/POINT/ -o username=YOUR_ACTUAL_USERNAME,
password=YOUR_ACTUAL_PASSWORD,
fsname=zOlRRa

(This will mount it at bootup.)


Please leave feedback here to tell me if this worked for you. I just figured all of this out. So, I'm not sure if I missed something.

[http://www.webloguniverse.com](http://www.webloguniverse.com)
-Click on the email link. (I'm the admin)
Thanks, 
Pros

________________________________________________________
Problem and Solution:

Problem:
-When I created an icon on the desktop for my nifty new gmail hard drive, gmail promptly froze my account for 15 minutes citing a 'Sector 4 Lockdown.'
It did not like the 'create link to location' choice for creating a new icon.

Solution:
-I created a link to the folder just below the mount point.
My gmail drive is mounted a /mnt/gmail
My icon on the desktop points to /mnt

-I haven't experienced any problems.
Although, **I have to delete files using  a shell command line.**
Deleting from the konquerer window causes 'Lockdown Sector 4' 
Good Luck,
Pros

---

### Post by i3dmaster on 2006-03-05
```
mount.gmailfs "/usr/local/bin/libgmail.py" /mnt/gmail/ -o username=XXXXX, password=XXXXXX, fsname=zOIRRa
usage: mount.gmailfs none mountpoint [options]
```
Looks like the syntax is wrong. Let me give you some suggestions.
1. pls put any dependencies that may need in cmd, for instance, ```
apt-get install python-fuse python2.4-fuse
``` in this case. It will be much easier to read.
2. review your Howto again once you've done so that typos can be eliminated to the minimum. Such as ```
/usr/lib/python2.5/site-packages/fuse.py
```, there is no such thing python2.5 and I assume that you did mean "python2.4" and without install the fuse module, you wouldn't have fuse.py there.
3. It will be much better if you put your cmds in b/w the CODE quotation marsk. "["CODE"]" AND "[""/"CODE"]" w/o all the double quotes.

EDIT: looks like the error is because of the space b/w the commas. fixed that and got the LoginFailure error.
```
Traceback (most recent call last):
  File "/usr/local/bin/mount.gmailfs", line 164, in ?
    main(mountpoint, namedOptions, useEncfs)
  File "/usr/local/bin/mount.gmailfs", line 90, in main
    gmailfs.main(mountpoint, namedOptions)
  File "/usr/local/bin/gmailfs.py", line 1130, in main
    server = Gmailfs(mountpoint, **namedOptions)
  File "/usr/local/bin/gmailfs.py", line 602, in __init__
    self.ga.login()
  File "/usr/local/bin/libgmail.py", line 317, in login
    raise GmailLoginFailure("Login failed. (Wrong username/password?)")
libgmail.GmailLoginFailure: 'Login failed. (Wrong username/password?)'

```
and I have to add my username and password into the /etc/gmailfs.conf file even though I've changed those places that you pointed out. very strange. After mount, there is no error message so I was thinking it was working but when I went to /mnt/gmailfs, there is nothing there. And do you know how to umount it?

---

### Post by Prospero2006 on 2006-03-05
Like I said, I made all of those changes, and finally it worked. 

Here's what I did:
   -I erased all references to changing username password variables
    in gmailfs.py from my orginal post. (They aren't necessary.)

   -Python 2.5 is now Python 2.4

   -Got rid of those pesky spaces in the 'mount.gmailfs' command.

When you mount your drive, and I'm glad it worked, you won't see anything there. You have to copy a file or something into it. It won't see any of your mail or files uploaded using, say, GSPACE. It only reads gmailfs data. 

To unmount:
    umount /YOUR/MOUNT/POINT


Does that help?

Thanks for the info
Pros

---

### Post by i3dmaster on 2006-03-05
Strange enough, when I retry it today (the box got rebooted during the night), I can't mount it anymore.
```

mount.gmailfs "/usr/local/bin/libgmail.py" /mnt/gmail/ -o username=xxxxx,password=xxxxx,fsname=zOIRRa
fusermount: failed to open /dev/fuse: No such file or directory
fuse: reading device: Bad file descriptor

```

---

### Post by Prospero2006 on 2006-03-05
That's strange. I'm no expert with fuse, but apparently it's a kernel module.

I would try these things:
   lsmod | grep fuse

    modprobe fuse

For me, I see the module loaded. So, if it doesn' load, try using adept to install Gmailfs.

Then remove it.

That may install the missing piece there. I don't know whether that will work or not.

Pros

---

### Post by i3dmaster on 2006-03-06
You'd man! That is the problem. After ```
modprobe fuse
```, everything worked like a charm! Thanks for help.

---

### Post by Viriiguy on 2006-03-06
I thought Gmail put an end to allowing the GmailFS to work?

---

### Post by i3dmaster on 2006-03-06
not sure. Seems like it is still working. But the stuff you put into the gmailfs doesn't seem to be readable from anyway but just the gmailfs. I saved a chm file to my gmailfs and I went back to gmail account and want to take a look, all I got are just a couple of junk emails sent to myself with one of them attached with a garbled file named like tmpX0jGp...

---

### Post by Prospero2006 on 2006-03-06
I'm glad to hear you got it working.

Here's the only real hang-up, and if anyone can solve it I'm all ears.

When I choose, 'Move to Trash' in KDE, Gmail locks my account out for 
15 minutes citing a 'Sector 4 lockdown.' Everything else seems to come off without a hitch.

Pros

---

### Post by forbmj on 2006-03-06
I got something wrong after the command 

mount.gmailfs "/usr/local/bin/libgmail.py" /mnt/gmail/ -o username=xxxxxxxxxxxxxx,password=xxxxxx,
fsname=zOIRRa

fuse: failed to exec fusermount: No such file or directory
fuse: reading device: Bad file descriptor

$ lsmod |grep fuse
fuse                   37964  0


any idea?

---

### Post by Prospero2006 on 2006-03-06
Please post: 

/usr/lib/python2.4/site-packages/fuse.py

-Line 68

I believe you probably have that entered incorrectly. 

Pros

---

### Post by forbmj on 2006-03-06
[QUOTE=Prospero2006]Please post: 

/usr/lib/python2.4/site-packages/fuse.py

-Line 68

I believe you probably have that entered incorrectly. 

Pros[/QUOTE]

my fuse.py, line 68:

self.mountpoint = "/mnt/gmail/"

after I installed the fuse-utils, the above error disappeared, but I couldn't use the normal user account to mount.gmailfs though I have added this account into the fuse group.

error:
fusermount: failed to create device node: Operation not permitted
fusermount: fuse device not found, try 'modprobe fuse' first
fuse: reading device: Bad file descriptor

if I use 'sudo ...', everything is fine, but the normal user account couldn't access /mnt/gmail/.

Any idea?

---

### Post by Prospero2006 on 2006-03-07
try this sudo chmod 777 /mnt/gmail

What are the current file permissions?

Pros

---

### Post by forbmj on 2006-03-08
Have done that

ls -l /mnt/gmail
drwxrwxrwx  2 root root 4096 2006-03-07 01:02 gmail

---

### Post by Prospero2006 on 2006-03-08
when you say your normal user account can't access 
/mnt/gmai --What error are you receiving exactly?

Can you access it with root?

Pros

---

### Post by Zottan on 2006-03-14
mount.gmailfs "/usr/local/bin/libgmail.py" /media/gdrive/  -o username=XXXXXXXX,password=XXXXXXXXX,fsname=zOlRRa
fuse: failed to exec fusermount: Permission denied
fuse: reading device: Bad file descriptor

with sudo i dont get any error , but i acceed to the directory and is a simply dir on my disc....

---

### Post by souteneur3190 on 2006-03-21
i feel dum, i have no idea what the mount point should be.

---

### Post by tuxcantfly on 2006-03-22
If you're having trouble with fuse, check out:

[http://ubuntuforums.org/showthread.php?t=148359](http://ubuntuforums.org/showthread.php?t=148359)

---

### Post by AndreAPL on 2006-03-26
hi there.i still can't get it work ](*,) 
had followed the steps, and have fuse loaded...

> 
Traceback (most recent call last):
  File "/sbin/mount.gmailfs", line 164, in ?
    main(mountpoint, namedOptions, useEncfs)
  File "/sbin/mount.gmailfs", line 90, in main
    gmailfs.main(mountpoint, namedOptions)
  File "/usr/local/bin/gmailfs.py", line 1130, in main
    server = Gmailfs(mountpoint, **namedOptions)
  File "/usr/local/bin/gmailfs.py", line 602, in __init__
    self.ga.login()
  File "/usr/lib/python2.4/site-packages/libgmail/__init__.py", line 281, in login
    raise GmailLoginFailure
libgmail.GmailLoginFailure

Was looking in the official gmailfs page, still no clue ...
(and user/pass are correct...)

---

### Post by mdofl1 on 2006-04-13
Hello everyone, I have followed the directions to get gmailfs to work to the letter and i get the following error message when type the command to mount it:   File "/usr/local/bin/mount.gmailfs", line 159, in ?
    import gmailfs
  File "/usr/local/bin/gmailfs.py", line 20, in ?
    from fuse import Fuse
  File "/usr/lib/python2.4/site-packages/fuse.py", line 68
    self.mountpoint = /home/charles/gmail
                      ^


Is there anyone that can help me fix this?

Cheers, 
Charles

---

### Post by rayTerrace on 2006-04-14
> Mount it once with this command

mount.gmailfs "/usr/local/bin/libgmail.py" YOUR/MOUNT/POINT/ -o username=YOUR_ACTUAL_USERNAME,password=YOUR_ACTUAL _PASSWORD,fsname=zOlRRa

When I try to mount it I get the following message

bash: mount.gmailfs: command not found

---

### Post by misiek2000 on 2006-04-19
after type this:

```
misiek@zlom:/mnt/gmail$ mount.gmailfs "/usr/local/bin/libgmail.py" /mnt/gmail/ -o username=*****,password=******,fsname=zOlRRa

```

i have that:
```

Traceback (most recent call last):
  File "/usr/local/bin/mount.gmailfs", line 155, in ?
    pyfile, mountpoint, namedOptions, useEncfs = parseCommandLineArgs(sys.argv[1:])
  File "/usr/local/bin/mount.gmailfs", line 67, in parseCommandLineArgs
    log.error("file %s doesn't exist, or is not a file" % pyfile)
NameError: global name 'log' is not defined

```
what i must do with this ?;/

---

### Post by franke on 2006-04-23
I get:

```
Traceback (most recent call last):
  File "/sbin/mount.gmailfs", line 164, in ?
    main(mountpoint, namedOptions, useEncfs)
  File "/sbin/mount.gmailfs", line 90, in main
    gmailfs.main(mountpoint, namedOptions)
  File "/usr/local/bin/gmailfs.py", line 1133, in main
    server.main()
  File "/usr/lib/python2.4/site-packages/fuse.py", line 115, in main
    apply(main, (), d)
TypeError: argument 21 must be string, not None

```

Frustrating errors

---

### Post by willhurt on 2006-05-23
me too, im getting:

```

Traceback (most recent call last):
  File "/usr/local/bin/mount.gmailfs", line 159, in ?
    import gmailfs
  File "/usr/local/bin/gmailfs.py", line 20, in ?
    from fuse import Fuse
  File "/usr/lib/python2.4/site-packages/fuse.py", line 68
    self.mountpoint = /media/gdrive/


```

---

### Post by ZavezPasVu on 2006-07-09
I get exactly the same error than misiek2000.:mad: 
```
mount.gmailfs "/usr/local/bin/libgmail.py" /media/gmail -o username=******,password=******,fsname=zOlRRa
Traceback (most recent call last):
  File "/usr/bin/mount.gmailfs", line 153, in ?
    pyfile, mountpoint, odata, useEncfs = parseCommandLineArgs(sys.argv[1:])
  File "/usr/bin/mount.gmailfs", line 66, in parseCommandLineArgs
    log.error("file %s doesn't exist, or is not a file" % pyfile)
NameError: global name 'log' is not defined
```
I'm using Dapper, Fuse seems OK.
Is there any solution found since April?

---

### Post by wedge2k on 2006-07-18
the log error i fixed by moving gmailfs.py to /usr/local/bin/

or you can look at mount.gmailfs and its like line 8 default_gmailfs_location, modify that to where ever you want gmailfs.py to reside. 

Although, I'm getting the same error as franke:

```
Traceback (most recent call last):
  File "/usr/bin/mount.gmailfs", line 165, in ?
    main(mountpoint, namedOptions, useEncfs)
  File "/usr/bin/mount.gmailfs", line 91, in main
    gmailfs.main(mountpoint, namedOptions)
  File "/usr/local/bin/gmailfs.py", line 1133, in main
    server.main()
  File "/usr/lib/python2.4/site-packages/fuse.py", line 115, in main
    apply(main, (), d)
TypeError: argument 21 must be string, not None

```

---

### Post by proteusdeimos on 2006-07-24
> **ZavezPasVu said:**
> I get exactly the same error than misiek2000.:mad: 
```
mount.gmailfs "/usr/local/bin/libgmail.py" /media/gmail -o username=******,password=******,fsname=zOlRRa
Traceback (most recent call last):
  File "/usr/bin/mount.gmailfs", line 153, in ?
    pyfile, mountpoint, odata, useEncfs = parseCommandLineArgs(sys.argv[1:])
  File "/usr/bin/mount.gmailfs", line 66, in parseCommandLineArgs
    log.error("file %s doesn't exist, or is not a file" % pyfile)
NameError: global name 'log' is not defined
```
I'm using Dapper, Fuse seems OK.
Is there any solution found since April?

I am also getting this exact error.  any help would be appreciated.

---

### Post by Third Thoughts on 2006-07-24
> **proteusdeimos said:**
> I am also getting this exact error.  any help would be appreciated.

I was getting that error to and it was because I was using the wrong path to the file libgmail.py. 

In the command
```

mount.gmailfs "/usr/local/bin/libgmail.py" /media/gmail -o username=******,password=******,fsname=zOlRRa

```

Is /usr/local/bin really where you put libgmail.py? Or did you (like me) put it in /usr/local/bin/libgmail-0.1.4? If you just copied the folder libgmail-0.1.4 to /usr/local/bin, then you did the second. So your mount command should be
```

mount.gmailfs "/usr/local/bin/libgmail-0.1.4/libgmail.py" /media/gmail -o username=******,password=******,fsname=zOlRRa

```

~Andrew S.

---

### Post by jackn on 2006-08-25
Many thanks to Prospero on the procedure to follow, and to Andrew S. for the pointer on correct file address.

I've gone through this twice by now, removing everything and reinstalling. Realize this is not the cleverest way, but just don't know better yet.

When I get to the mount.gmailfs command, I always get the following:
```
Traceback (most recent call last):
  File "/sbin/mount.gmailfs", line 159, in ?
    import gmailfs
ImportError: No module named gmailfs
```

There *is* an /sbin/mount.gmailfs file, and I have no idea what is meant by 'No module named gmailfs"...

What can I do?

Thanks,
Jackn

---

### Post by jaranguren on 2006-09-06
Hroit,

You're most likely missing gmailfs.py.  I put mine under /usr/local/bin

---

### Post by jackn on 2006-09-06
> **jaranguren said:**
> Hroit,

You're most likely missing gmailfs.py.  I put mine under /usr/local/bin

Very grateful for the help, jaranguren.

I do have gmailfs.py, however:
```

$locate gmailfs.py
/usr/local/bin/gmailfs-0.7.2/gmailfs.py
/usr/local/bin/gmailfs.py

```

Is there sth wrong with the above?
Other ideas?

Jackn

No luck yet.

I've removed the first gmailfs.py () above, as it seemed like a duplication. 
Likewise, I've removed a duplicate of mount.gmailfs and of gmailfs.conf, also in the gmail-0.7.2 folder.

This time, I got this as an error message:

$ mount -t gmailfs /usr/local/bin/gmailfs.py /home/gmailfs -o username=haim.roitgrund,password=<password>,fsname=zOlRRa
Ignored option :rw
Traceback (most recent call last):
  File "/sbin/mount.gmailfs", line 159, in ?
    import gmailfs
  File "/usr/local/bin/gmailfs.py", line 20, in ?
    from fuse import Fuse
  File "/usr/lib/python2.4/site-packages/fuse.py", line 68
    self.mountpoint = /home/gmailfs
                      ^
SyntaxError: invalid syntax


Sorry, but I don't understand...

Jackn

---

### Post by nyxynyx on 2006-12-28
Is there an updated howto for edgy?

---

