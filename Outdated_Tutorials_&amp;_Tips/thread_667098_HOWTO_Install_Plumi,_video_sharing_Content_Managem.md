---
title: "HOWTO: Install Plumi, video sharing Content Management System"
date: 2008-01-14
forum: Outdated Tutorials &amp; Tips
---

### Post by datakid on 2008-01-14
To install [Plumi]("http://plumi.org") on ubuntu 7.10 (Gutsy):

1. Grab the Plone 2.5.5 Unified Installer from here:

[http://plone.org/products/plone/releases/2.5.5](http://plone.org/products/plone/releases/2.5.5)

```

 wget https://launchpad.net/plone/2.5/2.5.5/+download/Plone-2.5.5-UnifiedInstaller.tgz

```

2. unzip etc:

```
tar zxvf Plone-2.5.5-UnifiedInstaller.tgz
```

This gives us a copy of the folder Plone-2.5.5-UnifiedInstaller

We are going to move this to /opt and change it's permissions so wear our fingers down with sudo. It presumes that you have a group called www-data, if you don't, you can add one to your /etc/group:


```
sudo mv Plone-2.5.5-UnifiedInstaller /opt/
[sudo] password for User: ********
sudo chgrp -R www-data Plone-2.5.5-UnifiedInstaller

```

3. Apply the patch found [here]("http://dev.plone.org/plone/ticket/5935")

ie, edit /opt/Plone-2.5.5-UnifiedInstaller/install.sh by adding this:

```

echo "patching PIL to disable TK support ..."
# patch to disable TK support in PIL
cat >> setup.py.patch << _PIL_PATCH
--- setup.py    2005-03-23 10:16:40.000000000 -0800
+++ setup.py.modified   2006-11-13 13:27:00.000000000 -0800
@@ -83,6 +83,7 @@
      import _tkinter
  except ImportError:
      _tkinter = None
 +_tkinter = None
 
  def add_directory(path, dir, where=None):
 _PIL_PATCH
 patch setup.py < setup.py.patch

```

at line 456 with your favourite text editor (vim/pico/nano/gedit/etc). It should look like this:

```
455 cd $PIL_DIR
456 echo "patching PIL to disable TK support ..."
457 # patch to disable TK support in PIL
458 cat >> setup.py.patch << _PIL_PATCH
459 --- setup.py    2005-03-23 10:16:40.000000000 -0800
460 +++ setup.py.modified   2006-11-13 13:27:00.000000000 -0800
461 @@ -83,6 +83,7 @@
462      import _tkinter
463  except ImportError:
464      _tkinter = None
465 +_tkinter = None
466 
467  def add_directory(path, dir, where=None):
468 _PIL_PATCH
469 patch setup.py < setup.py.patch
470 $PY ./setup.py build_ext -i

```

4. Install Plone-2.5.5:
```
cd Plone-2.5.5-UnifiedInstaller
sudo ./install.sh

```

Either remember or take note of the admin password. Or, preferably, notice that there is a file called /opt/Plone-2.5.5/adminPassword.txt that has this info in it.

5. Grab the plumi trunk from svn:
```

cd /opt
sudo svn co https://svn.plone.org/svn/collective/Plumi/trunk/ plumi-trunk
```

This creates a folder called plumi-trunk which contains all the extra Products you need.

6. Edit the configs to notice the Plumi products. The two files are:

/opt/Plone-2.5.5/zeocluster/client1/etc/zope.conf
/opt/Plone-2.5.5/zeocluster/client2/etc/zope.conf

add the following line under the products section:

```
products /opt/plumi-trunk
```

7. Install the python egg imsvdex

```
sudo /opt/Plone-2.5.5/Python-2.4.4/bin/easy_install imsvdex
```

8. Start the Zope/Plone server:

```
sudo /opt/Plone-2.5.5/zeocluster/bin/startcluster.sh
```

9. Grab yr browser, go to [http://localhost:8080/manage](http://localhost:8080/manage) (or [http://localhost:8081/manage](http://localhost:8081/manage), they point to the same place). You will need to enter the admin/password combo from step 4 at this point.

In  the top right corner you will see the Add Products drop down menu. Choose "Plone Site", and fill out the form. Whatever you put into the ID field will be the URL of your site. Eg: http:// localhost:8080/the_id_field


10. Goto yr new Plone site and in the top right you will see Preferences. Click that, then choose Add/Remove Products from the top of the left column.

You should only need to install 'ATVideo', 'PlumiSkin', 'PressRoom' - all the rest of the products will be pulled in by the installers of those three products.

Now you have a video sharing site!

To configure transcoding, see /opt/plumi_trunk/indytube/INSTALL.plone

If you have any problems,  see  /opt/plumi-trunk/INSTALL.txt

---

### Post by boltorg on 2008-01-29
Get this error after adding the patch lines...

Compiling and installing PIL ...
patching PIL to disable TK support ...
Python 2.4.4 (#1, Jan 29 2008, 13:58:54) 
[GCC 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)] on linux2
Type "help", "copyright", "credits" or "license" for more information.

---

### Post by datakid on 2008-02-25
Sorry about the long delay to reply, I had no idea this post had been approved :)

Ok, so I don't know heaps about that patch or patching in general - in fact most of what I know I learnt from having to do that.

I discovered that the patch process is highly dependent upon spacing - if you miss or add a single space that doesn't need to be there, it throw's errors. I would check to make sure that you have added the patch exactly as it is shown in teh howto. In fact, don't trust me - go here and take a look [http://dev.plone.org/plone/ticket/5935](http://dev.plone.org/plone/ticket/5935)

I hope that helps.

---

