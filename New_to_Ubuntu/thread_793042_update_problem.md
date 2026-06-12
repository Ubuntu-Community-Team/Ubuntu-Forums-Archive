---
title: "update problem"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by lunaluna on 2008-05-13
i think i'm having a problem with the updates...

when the last 2 updates took place (gstreamer & libspeex1 )?
or when ubuntu notified you for download...?

---

### Post by lunaluna on 2008-05-13
i think some servers might have some problems...anyone facing the same problem?

---

### Post by rob09 on 2008-05-13
i haven't been able to get updates also i can't get into my synaptic package manager either. they open the administration folder for about 10 seconds and never prompt me for a password, then the window goes black and i can't close it with out rebooting and it doesn't update

---

### Post by lunaluna on 2008-05-13
> **rob09 said:**
> i haven't been able to get updates also i can't get into my synaptic package manager either. they open the administration folder for about 10 seconds and never prompt me for a password, then the window goes black and i can't close it with out rebooting and it doesn't update

which server are you using because it's seems to me the problem comes only  
from the uk servers-but i'm not sure

---

### Post by paulsmith on 2008-05-13
New to Linux... Ububtu 6 to present 8.x... Update notices make it
thru to me.  Can finally update apparently successfully.. BUT
first try stops before password dialog appears.  Check with system
monitor shows update manager asleep..I end the process & retry and
its works then...Anybody else experience this!!??

HP Pavillion 5200 series laptop.. intel pent-4  lgb memory

---

### Post by rockerphil on 2008-05-13
if y'all are having problems with the GUI update manager just open up your terminal and run this code

sudo apt-get dist-upgrade

it does the same thing as your update manager, just not graphically

---

### Post by lunaluna on 2008-05-13
> **paulsmith said:**
> New to Linux... Ububtu 6 to present 8.x... Update notices make it
thru to me.  Can finally update apparently successfully.. BUT
first try stops before password dialog appears.  Check with system
monitor shows update manager asleep..I end the process & retry and
its works then...Anybody else experience this!!??

HP Pavillion 5200 series laptop.. intel pent-4  lgb memory

did you also have any other problems from the servers themselves

---

### Post by rob09 on 2008-05-13
thanks it worked for me how would i get  other applications that way? i'm in the us

---

### Post by lunaluna on 2008-05-14
i'm not sure... but when i first started using it nothing like this happened...

---

### Post by thevikingking on 2008-05-14
im having issues with updating as well... 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.87.27_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.87.27_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.87.27_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.87.27_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/ssl-cert/ssl-cert_1.0.14-0ubuntu2.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/s/ssl-cert/ssl-cert_1.0.14-0ubuntu2.1_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


i dont know why the connection is being refused, please help!!!

---

### Post by wrgb2 on 2008-05-14
Have a look at [this blog post]("http://nocostsoftware.blogspot.com/2008/05/what-to-do-if-your-ubuntu-updates-and.html") to see how to select the best download server for your location.

---

### Post by thevikingking on 2008-05-14
ok so i tried what the blog post said, and then that didn't work because ubuntu asked me to check my internet connection... 

so i am still at the same place getting the same error messages about not being able to connect to the server, yet i am on the internet.

---

### Post by Matt640 on 2008-05-24
Hey.
I'm sorta having the same problem here only the cause was something different. I'm using the ordinary Desktop Edition of Ubuntu 8.04 not the 64AMD one. So I read from the Forums that by installing Sun Java 6, I can get my FrostWire up and running again. So I use my SPM to find it and download it. In the middle of Download/Installing, it hanged/jammed and my only option was to reboot. After I did, I realize that I can't open my SPM and it ask me to manually run sudo dpkg --configure -a. When I do, this turns up:
Setting up sun-java6-doc (6-06-0ubuntu1) ...
This package is an installer package, it does not actually contain the
JDK documentation. You will need to go download one of the
archives:

jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

[http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download. The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

As you can see, I'm in desperate need of HELP! Can anyone encrypt this for me?

---

