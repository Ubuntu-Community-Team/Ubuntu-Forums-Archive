---
title: "cant find vmware after install"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by trying hard on 2008-09-24
hi 
i have installed vmware server 2.0 on hardy  ( i think)
but i cant find how to start it 

has anyone got the time to please help me

---

### Post by trying hard on 2008-09-24
i haved typed vmware into the terminal and it opens up a tab in firefox with this error


Secure Connection Failed

      

      
      
      

      
        
        

          

127.0.0.1:8333 uses an invalid security certificate.

The certificate is not trusted because it is self signed.
The certificate is only valid for robin-desktop

(Error code: sec_error_ca_cert_invalid)

        


        
        


    * This could be a problem with the server's configuration, or it could be someone trying to impersonate the server.

    * If you have connected to this server successfully in the past, the error may be temporary, and you can try again later.




        
        

          Or you can add an exception…

---

### Post by Orange_and_Green on 2008-09-24
Hello Robin,

127.0.0.1:8333 means port number 8333 on your own machine. It looks like the program is trying to connect to it (for some reason, possibly to display a help or welcome text in your browser?) I think you are safe to click on the "add an exception" link as you are just connecting to your own port... From there you need to "view the certificate", accept it, and create a permanent exception.

Good luck:KS

---

### Post by trying hard on 2008-09-24
hi well that moves things along a little 
now it asks me to login to the
vmware infrastructure web access

so the command vmware is not launching vmware

---

### Post by Shazaam on 2008-09-24
Try this...
```
vmware-config.pl
```

---

### Post by Dedoimedo on 2008-09-24
Hello,

Also try in terminal:

which vmware

And also

cd /
updatedb
locate vmware

You'll get a list of various binaries (and other files). One of those should correspond to the server binary. You can also consult the installation guide on the vmware site...

Dedoimedo

---

### Post by Orange_and_Green on 2008-09-24
Could this excellent article help you further?

[http://ubuntuforums.org/showthread.php?t=779934]("http://ubuntuforums.org/showthread.php?t=779934")

(Be sure to say thank you to bodhi.zazen)

Good luck:KS

---

### Post by trying hard on 2008-09-24
thanks for helping

this is the reults of your suggestions

robin@robin-desktop:~$ vmware-config.pl
Please re-run this program as the super user.

Execution aborted.

robin@robin-desktop:~$ which vmware
/usr/bin/vmware
robin@robin-desktop:~$ cd/
bash: cd/: No such file or directory
robin@robin-desktop:~$ cd/updatedb
bash: cd/updatedb: No such file or directory
robin@robin-desktop:~$ cd/updatedb locate vmware
bash: cd/updatedb: No such file or directory


as you can see i am very green but i have spent hours trying to work this out so please bear with me

robin

---

### Post by trying hard on 2008-09-24
ok i typed sudo in front of vmware-config.pl
and that started it

I have seen this a couple of times already
so basically it gets to this bit


Your kernel was built with "gcc" version "4.2.3", while you are trying to use 
"/usr/bin/gcc" version "4.2.4". This configuration is not recommended and 
VMware Server may crash if you'll continue. Please try to use exactly same 
compiler as one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.2.4" anyway? [no] 

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and 
"http://www.vmware.com/go/unsup-linux-tools".

Execution aborted.


and if i go with the yes option it keeps telling me that i have the wrong kernel for this

robin

---

### Post by Orange_and_Green on 2008-09-24
I think you might be interested in a good command line tutorial... So you know what you are actually doing... I found one on Youtube that's very enjoyable, please have a look:

[URL="http://www.youtube.com/watch?v=4zmd8dclqPU&feature=related"]http://www.youtube.com/watch?v=4zmd8dclqPU&feature=related
[/URL]

And this is about the way permissions are handled in Ubuntu:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

Specifically to your original question, please refer to [bodhi.zazen's post]("http://ubuntuforums.org/showthread.php?t=779934") if you haven't done so already.

EDIT in response to your new post: may I ask you what release of Ubuntu you are running (8.04/7.10/7.04...) and whether it's 32 or 64 bit?

Good luck:KS

---

### Post by Paqman on 2008-09-24
You need some spaces in your syntax.

EG:

cd / = good!
cd/  = bad!

Just copy and paste the commands if you're unsure.

---

### Post by trying hard on 2008-09-24
so much to learn

is this making any sense 

robin@robin-desktop:~$ cd /
robin@robin-desktop:/$ updatedb
updatedb: can not open a temporary file for `/var/lib/mlocate/mlocate.db'
robin@robin-desktop:/$ locate vmware
/usr/lib/xorg/modules/drivers/vmware_drv.so
/usr/share/app-install/icons/_usr_share_pixmaps_vmware-player.png
/usr/share/bug/xserver-xorg-video-vmware
/usr/share/bug/xserver-xorg-video-vmware/script
/usr/share/doc/xserver-xorg-video-vmware
/usr/share/doc/xserver-xorg-video-vmware/changelog.Debian.gz
/usr/share/doc/xserver-xorg-video-vmware/changelog.gz
/usr/share/doc/xserver-xorg-video-vmware/copyright
/usr/share/man/man4/vmware.4.gz
/usr/share/xserver-xorg/pci/vmware.ids
/var/lib/dpkg/info/xserver-xorg-video-vmware.list
/var/lib/dpkg/info/xserver-xorg-video-vmware.md5sums

---

### Post by Orange_and_Green on 2008-09-24
> **trying hard said:**
> 
robin@robin-desktop:~$ cd /
robin@robin-desktop:/$ updatedb
updatedb: can not open a temporary file for `/var/lib/mlocate/mlocate.db'


How about ```
sudo updatedb
```?;)

---

### Post by clancymf on 2008-11-11
> **Orange_and_Green said:**
> How about ```
sudo updatedb
```?;)

Just wanted to let you know that this worked for me!  Found this thread via google.

---

