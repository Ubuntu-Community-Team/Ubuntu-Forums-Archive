---
title: "sharing folder"
date: 2012-11-28
forum: New to Ubuntu
---

### Post by darkchaos18 on 2012-11-28
'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Logon failure. 

how to fix it??

---

### Post by Morbius1 on 2012-11-28
Go through the ususal checklist:

[1] Make sure smbd is running:
```
sudo service smbd status
```If it's not running start it:
```
sudo service smbd start
```[2] Check to see if encryption is disabled:
```
testparm -sv | grep "encrypt passwords"
```If it comes back with "no" or "false" then change it:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```find the line and change it to yes:
[COLOR=Blue]**encrypt passwords = yes**[/COLOR]

Then restart samba:
```
sudo service smbd restart
```

---

### Post by XJ12C on 2012-12-09
I am getting the same error.  Checked
testparm -sv | grep "encrypt passwords"as suggested.  It came back as "no" so made the change in smb.conf

restarted samba then checked again and the command now came back with
encrypt passwords = Yes

When trying to share a folder through nautilus, I still get the error

'net usershare' returned error 255: net usershare add: failed to add share pictures. Error was Operation not permitted

Any other thoughts

---

### Post by Morbius1 on 2012-12-10
That's a different error.

Post the output of the following command:
```
ls -al /var/lib/samba/usershares
```

---

### Post by XJ12C on 2012-12-11
Output is

total 36
drwxrwx--T 2 root sambashare 4096 Dec  9 17:35 .
drwxr-xr-x 4 root root       4096 May 28  2012 ..
-rw-r--r-- 1 dad  dad         105 May 28  2012 home folder
-rw-r--r-- 1 dad  dad         134 Jun 30 19:30 mainpcmovies
-rw-r--r-- 1 dad  dad         132 Dec  9 15:49 mainpcmusic
-rw-r--r-- 1 dad  dad         103 May 28  2012 movies
-rw-r--r-- 1 dad  dad         126 Dec  9 16:56 music
-rw-r--r-- 1 root root         98 Dec  9 17:07 pictures
-rw-r--r-- 1 dad  dad         107 May 28  2012 tv shows

---

### Post by s1baker on 2012-12-11
I had problems similar to this trying to set up my shared folders.
I'm not to experienced, but I will throw these in, maybe they
might help in some way.

1) Do you have samba installed on your computer that you have your shared folders on?

2) If you have samba you may have to do what I had to do to my samba config file to get the shared folders to work.
I had to edit the /etc/samba/smb.conf file.
I had to add this:
```

force user = (I put my home folder name here )

```
I had to put this just under the "[global]" label in the smb.conf file.

3) Is your firewall set off? If you have your router turned on you generally won't need your Ubuntu firewall turned on anyway.
Check for ufw ( the default Ubuntu firewall ) is turned off:
```

sudo ufw disable   ( to turn it off )
sudo ufw status     ( to see it's status )
sudo ufw enable    ( to turn it on )

```

If you don't have the ufw firewall set to anything, I don't think it 
matters anyway.

---

### Post by deadflowr on 2012-12-11
Add:

```
usershare owner only = false
```

to the global section of the /etc/samba/smb.conf file.

Or install the samba graphical program in the software center for super ease of use to add and remove shared folders.
It's simply called Samba.

---

### Post by Morbius1 on 2012-12-11
>  'net usershare' returned error 255: net usershare add: [COLOR=Blue]failed to add share** pictures**[/COLOR]. Error was Operation not permitted> **XJ12C said:**
> Output is

total 36
drwxrwx--T 2 root sambashare 4096 Dec  9 17:35 .
drwxr-xr-x 4 root root       4096 May 28  2012 ..
-rw-r--r-- 1 dad  dad         105 May 28  2012 home folder
-rw-r--r-- 1 dad  dad         134 Jun 30 19:30 mainpcmovies
-rw-r--r-- 1 dad  dad         132 Dec  9 15:49 mainpcmusic
-rw-r--r-- 1 dad  dad         103 May 28  2012 movies
-rw-r--r-- 1 dad  dad         126 Dec  9 16:56 music
[COLOR=Blue]** -rw-r--r-- 1 root root         98 Dec  9 17:07 pictures**[/COLOR]
-rw-r--r-- 1 dad  dad         107 May 28  2012 tv shows
You are trying as a regular user to create a share that root has already created with that name.

Either launch Nautilus as root ( gksu nautilus ) and remove the share created by root or just leave it as it is if that's the same folder being shared.

You can always get a listing of all of the Samba Usershares you or anyone else has created and how they are configured by running this command:
```
net usershare info --long
```

---

### Post by XJ12C on 2012-12-11
Thank you all for the suggestions

Morbius1 you were right, the folder is shared when I open Nautilus as root. 

Now back to the issue that started me down this road.  None of the shares can be seen by either of my two other Ubuntu machines.

Any ideas

---

### Post by Morbius1 on 2012-12-12
You do realize that you have hijacked this thread , right? An everyone that's responding to you are accomplices to this crime. 

Anywho......

> None of the shares can be seen by either of my two other Ubuntu machines.Let's start this adventure using standard Samba diagnostics first:

** Does the samba client on your machine see the shares created by the samba server on the same machine? The output of this command will tell us that:
```
smbtree
```It should list all your machine but at the moment we are interested in seeing this machine.

If you see nothing turn off your firewall if you have done anything with it and try smbtree again. If that still doesn't produce output then make sure nmbd is running:
```
sudo service nmbd restart
```
And run smbtree again.

---

### Post by XJ12C on 2012-12-13
Sorry...didn't realize I was hijacking a thread.   

Running the two commands listed did not result in anything.  Didn't think I had a firewall enable but ran the command

sudo ufw disable

anyway

Obviously had the firewall enabled, as this made all of the shares visible on the network

thanks for the help

---

