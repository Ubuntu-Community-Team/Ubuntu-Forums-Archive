---
title: "Howto: Install Webmin correctly &amp; get rid of the broken package from repository"
date: 2006-01-20
forum: Outdated Tutorials &amp; Tips
---

### Post by calt129 on 2006-01-20
[B]Please note, there's a [more recent and active thread on this howto]("http://ubuntuforums.org/showthread.php?p=674928"), please see that thread for discussions and problems. For the sake of completeness, I'll update this howto with the most recent version.
[/B]

Hi,

*I've posted this howto to howto section, but apparently the moderators thought it's not worth a howto, so that's why I'm posting this here, in case it can help someone.*

If you install the recent webmin package (v1.230-1) from the Ubuntu repository, you might end up with a broken webmin installation :mad: Furthermore, if you uninstall & reinstall it, you might really screw up things to a point where neither installation nor uninstallation is possible. I'm gonna show you how you can uninstall it if you've already installed the broken package (step 1) and install the package from webmin.com.
[LIST=1]
[*]**Run this step only if you have the package from the repository!**
During the uninstallation webmin would complain about 2 missing files: */etc/webmin/webmin.acl* & */etc/webmin/update.conf*. First create them with:
```
sudo touch /etc/webmin/{webmin.acl,update.conf}
```

Now you may proceed with the uninstallation:
```
sudo apt-get remove webmin-core webmin
```
*Note: If you do this via synaptic or aptitude, they might want to uninstall apache & other depended packages in case they are needed **only** for webmin and wouldn't be used otherwise. So **do not use synaptic or aptitude!** We'll need these packages later.*
[*]Now download the latest webmin package (at the time of this posting v1.250) from the [nearest webmin.com mirror]("http://www.webmin.com/index4.html").
[*]Unpack it with, cd to the directory (correct filename if needed):
```
tar xzvf webmin-1.250.tar.gz
cd webmin-1.250

```
and start the installation (change the target location if needed):
```

sudo ./setup.sh /usr/local/webmin/

```
Answer the few questions such as config-dir, etc.
*Note: Do not simply run setup.sh if you want to define the target yourself because setup.sh does **not** ask you for the target dir.*
[*]Most probably webmin can't create the startup script under /etc/init.d, check it with:
```
ls -al /etc/init.d/webmin
```
If this is the case, it is because webmin tries to create the script under */etc/rc.d/init.d*. So we'll create the directory temporarily, let webmin create the startup script, move the script to the correct location and delete the dir back.

First create the temporary directory:
```
sudo mkdir -p /etc/rc.d/init.d
```
And go to to the webmin dir and run the script with:
```
cd /usr/local/webmin/init/
sudo sh -c 'WEBMIN_CONFIG=/etc/webmin WEBMIN_VAR=/var/log/webmin /usr/local/webmin/init/atboot.pl webmin'

```
*Note: please replace the webmin, config & log directories with yours.*
Now move the script to its correct location with:
```
sudo mv /etc/rc.d/init.d/webmin /etc/init.d/
```
and delete the directory:
```
sudo sh -c 'rmdir /etc/rc.d/init.d; rmdir /etc/rc.d'
```
*Note: **Do not use** simply *rm -fr /etc/rc.d/* just in case you might have the directory already and there are files under it, rmdir should avoid this.*
[*]This script does **NOT** automatically start webmin at bootup, you should do this with, for example, with the following:
```
sudo ln -s /etc/init.d/webmin /etc/rc3.d/S13webmin
```
or similar. **_However, do not mess with startup scripts on the commandline if you do not know how init-scripts work and I would definitely recommend that you use webmin to mess with these scripts._**
[/LIST]

Now, finally you may open [http://localhost:10000/](http://localhost:10000/) (or whatever port you've set during the installation and start using webmin.

*EDIT - Post installation notes:*
The official webmin package is not optimized for ubuntu, that is, some paths in module configurations might be wrong. For example, Apache module might expect *apachectl* under /bin/apachectl whereas your system has it under */usr/local/bin/apachectl*, so you might tweak a few configs under apache. A big help here is the command-duo *updatedb* & *locate*. In order to find missing files just do an update first and search for the file with:
```
sudo updateb
locate apachectl

```
Also note, in order to open webmin from another machine, you need to edit webmin.conf first, because only 127.0.0.1 is allowed until specified otherwise.

From there on, you're beyond this howto...

Please inform me, if this does or does not work for you! I'll update it this howto accordingly.

Cheers :D

---

### Post by kkimmell on 2006-02-10
Well after installing the version using apt-get and trying to login only to get a blank white screen I followed your instructions.

I downloaded 1.260 and all of your directions seemed to work (i.e. no errors). webmin is running but when I go to host:10000 I still get the white screen with no login option.

What could I be missing?

-K

---

### Post by kkimmell on 2006-02-10
Nevermind... I'm a dope. I fogot to go to the local console and ad my IP in the access list of webmin. Sorry :)

---

### Post by bikeboy on 2006-02-11
Worked well for me. Made a few v minor mistakes but when I followed exactly, it all went fine.

Thanks

---

### Post by laylap on 2006-09-18
can you help, when i try to instal webmin it all seems fine var and ect, pearl is ok but i get this message, 

The system cannot find the path specified.

-----
Failed to create temp directory C:\DOCUME~1\dakota\LOCALS~1\Temp

does anyone knopw how to get ound this

thanks 
layla

---

### Post by calt129 on 2006-09-20
I'm sorry, you have to supply more information. And it looks like you're using Windows. This howto is for Ubuntu Linux.

---

