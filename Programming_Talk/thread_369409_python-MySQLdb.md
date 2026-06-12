---
title: "python-MySQLdb"
date: 2007-02-24
forum: Programming Talk
---

### Post by jvc26 on 2007-02-24
Hi there all, a brief overview of the problem, am looking at how to access MySQL databases from python to put input from databases into my programs. I have been looking at this (this is page2 of the guide)
[http://www.devshed.com/c/a/Python/MySQL-Connectivity-With-Python/1/](http://www.devshed.com/c/a/Python/MySQL-Connectivity-With-Python/1/)
Without this installed, understandably, on logging into python, I type:
```

>>> import MySQLdb
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named MySQLdb

```
Which is unsurprising. I then go to download it (see the guide thing) but when I try to install it I get the following error:
```

sh: mysql_config: not found
Traceback (most recent call last):
  File "setup.py", line 16, in <module>
    metadata, options = get_config()
  File "/home/james/Desktop/MySQL-python-1.2.2b3/setup_posix.py", line 39, in get_config
    libs = mysql_config("libs_r")
  File "/home/james/Desktop/MySQL-python-1.2.2b3/setup_posix.py", line 24, in mysql_config
    raise EnvironmentError, "mysql_config is not on your PATH"
EnvironmentError: mysql_config is not on your PATH

```
So... the question is where is mysql_config located? And could I just add it to my path using:
```

export PATH=$PATH:/path/to/mysql_config

```
I also tried to install python-mysqldb from the repositories and that didnt give me any joy either... any help would be appreciated!
Il

---

### Post by Mirrorball on 2007-02-24
> **Illuvator said:**
> I also tried to install python-mysqldb from the repositories and that didnt give me any joy either... any help would be appreciated!
Why not? apt-get install python-mysqldb should work.

---

### Post by jvc26 on 2007-02-24
I havent the faintest mate- otherwise I wouldnt have the problem surely ;) The output of the command:
```

python-mysqldb is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
And yet even now:
```

>>> import mysqldb
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named mysqldb

```
Any other ideas?
Il

---

### Post by Mirrorball on 2007-02-24
It should be:
```
import MySQLdb
```
Python is case sensitive.

---

### Post by jvc26 on 2007-02-25
To re-post what I put in post #1: Already tried that alas:
```

>>> import MySQLdb
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named MySQLdb

```
Its really bizarre!
Il

---

### Post by Carl H on 2007-02-25
I've just done this:-

```

carl@ground-control:~$ sudo apt-get install python-mysqldb
Password:
Reading package lists... Done
Building dependency tree... Done
python-mysqldb is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
carl@ground-control:~$ python
Python 2.4.3 (#2, Oct  6 2006, 07:49:22)
[GCC 4.0.3 (Ubuntu 4.0.3-1ubuntu5)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import mysqldb
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
ImportError: No module named mysqldb
>>> import mySQLdb
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
ImportError: No module named mySQLdb
>>> import MySQLdb
>>>

```

Not really sure what to suggest. Possibly there's a config file incorrect somewhere - maybe remove python-mysqldb and then re-install it, that might sort it. 

Sorry I can't be more help.

---

### Post by jvc26 on 2007-02-25
The repo mysql db does not work by the looks of things, and my 'mysql_config' is not on my path - you'd have thought if it needs to be on the path the apt-get install command for the mysql would have put it there to save it some effort. Ah wells - any more suggestions guys? Thanks for help thus received - hopefully will get it working before long (the delay just gives me time to get the DB complete.)
Il

---

### Post by Mirrorball on 2007-02-25
Uninstall and install the package again. It does work.
```
apt-get --purge uninstall python-mysqldb && apt-get install python-mysqldb
```
If you still have problems, uninstall and install mysql again.

---

### Post by jvc26 on 2007-02-25
Sorry to disappoint, but no it doesnt work - uninstalled MySQL server, admin, query-browser, and python-mysqldb and then ran through the whole install again - even --purge removed them just for good measure and that made no difference. *sigh* ah wells, any other ideas?
```

apt-get --purge uninstall python-mysqldb && apt-get install python-mysqldb

```
Its --purge remove ;)
Thanks very much for your time, its a pain its not working properly.
Il

---

### Post by pmasiar on 2007-02-25
Did you installed some non-ubuntu libraries? Some automatix goodies or something? Looks like something in your Python path is wrong. 

If you have spare partition, try install another clean version of ubuntu and try it there. Above install tricks should work if you have clean install.

---

### Post by Mirrorball on 2007-02-25
Also create a new user account and see if it works.

---

### Post by yogiudo on 2007-04-13
I am having this error. mysql_config not on path.
Nothing seems to work..


I dont know where mysql_config is even located

Can someone suggest?

---

### Post by yogiudo on 2007-04-13
furthermore,  apt-get uninstall __ANYTHING__ 
gives me:
E: Invalid operation uninstall

The same for apt-get --purge uninstall __ANYTHING__

---

### Post by DerSkw on 2007-05-16
> **yogiudo said:**
> furthermore,  apt-get uninstall __ANYTHING__ 
gives me:
E: Invalid operation uninstall

The same for apt-get --purge uninstall __ANYTHING__

it's called 'remove' not 'uninstall' ;-)

---

### Post by Gerardomal on 2007-05-16
Well I'm having the same problem here, I cant import MySQLdb from python shell, please I really need help with this, I used it on other OS and it worked, I cant find what seems to be wrong with this one, also I tried to install it by-hand but I didn't get a nice experience doing it, please someone help us :(

---

### Post by Gerardomal on 2007-05-16
I tried all the suggestions that you guys give in this thread, but I couldn't get it to work, there must be something wrong, but I just cant find what, I've looked into the files and all of them look to be nicely installed, is there a file that tells pyhton where are these packages installed? like a config file or something like that?

---

### Post by dwblas on 2007-05-19
This link explains mysql-python.  I don't know if that is a different package or not.  Anyway, you may have to install it manually because there appears to be some unknown factor working on your computer.
[http://www.devshed.com/c/a/Python/MySQL-Connectivity-With-Python/1/](http://www.devshed.com/c/a/Python/MySQL-Connectivity-With-Python/1/)
Installing from source
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by seanf on 2007-05-23
installing the libmysqlclient15-dev package solved the "mysql_config" problem for me.

---

### Post by operator on 2007-06-09
I used to have the same problem because of virtual python installed in my ~/bin (~/bin directory placed first in bash PATH if it exists in your home dir - at least for default ubuntu installation)

So what you can do to investigate your problem reason:

1. check if python-mysqldb installed and find where it files located:

```
$ dpkg-query -s python-mysqldb

bla bla bla... 
```

```
$ dpkg-query -L python-mysqldb

/.
/usr
/usr/lib
/usr/lib/python2.4
/usr/lib/python2.4/site-packages
/usr/lib/python2.4/site-packages/_mysql.so
/usr/lib/python2.5
/usr/lib/python2.5/site-packages
[COLOR="Red"]/usr/lib/python2.5/site-packages/_mysql.so[/COLOR]
/usr/share
/usr/share/doc
/usr/share/doc/python-mysqldb
/usr/share/doc/python-mysqldb/FAQ.txt.gz
/usr/share/doc/python-mysqldb/changelog.Debian.gz
/usr/share/doc/python-mysqldb/copyright
/usr/share/doc/python-mysqldb/changelog.gz
/usr/share/doc/python-mysqldb/README.gz
/usr/share/doc/python-mysqldb/MySQLdb.txt.gz
/usr/share/pycentral
/usr/share/pycentral/python-mysqldb
/usr/share/pycentral/python-mysqldb/site-packages
/usr/share/pycentral/python-mysqldb/site-packages/MySQLdb
/usr/share/pycentral/python-mysqldb/site-packages/MySQLdb/constants
/usr/share/pycentral/python-mysqldb/site-packages/MySQLdb/constants/__init__.py
/usr/share/pycentral/python-mysqldb/site-packages/MySQLdb/constants/CR.py
/usr/share/pycentral/python-mysqldb/site-packages/MySQLdb/constants/FIELD_TYPE.py
/usr/share/pycentral/python-mysqldb/site-packages/MySQLdb/constants/ER.py
/usr/share/pycentral/python-mysqldb/site-packages/MySQLdb/constants/FLAG.py
/usr/share/pycentral/python-mysqldb/site-packages/MySQLdb/constants/REFRESH.py
/usr/share/pycentral/python-mysqldb/site-packages/MySQLdb/constants/CLIENT.py
/usr/share/pycentral/python-mysqldb/site-packages/MySQLdb/__init__.py
/usr/share/pycentral/python-mysqldb/site-packages/MySQLdb/converters.py
/usr/share/pycentral/python-mysqldb/site-packages/MySQLdb/connections.py
/usr/share/pycentral/python-mysqldb/site-packages/MySQLdb/cursors.py
/usr/share/pycentral/python-mysqldb/site-packages/MySQLdb/release.py
/usr/share/pycentral/python-mysqldb/site-packages/MySQLdb/times.py
/usr/share/pycentral/python-mysqldb/site-packages/_mysql_exceptions.py
/usr/share/pycentral/python-mysqldb/site-packages/MySQL_python2.5-1.2.1_p2.egg-info
/usr/share/pycentral/python-mysqldb/site-packages/MySQL_python2.4-1.2.1_p2.egg-info
```

Ok, we find binary _mysql.so module. Let's go to /usr/lib/python2.5/site-packages/ and check if this module working...
```
$ cd /usr/lib/python2.5/site-packages/
$ python
Python 2.5.1 (r251:54863, May  2 2007, 16:56:35) 
[GCC 4.1.2 (Ubuntu 4.1.2-0ubuntu4)] on linux2-default ubuntu installation
Type "help", "copyright", "credits" or "license" for more information.
>>> import _mysql
```

Ok, binary module works!

```
>>> import MySQLdb
```

Yes! MySQLdb imports!

If you will get import error here (or some other error) so you have problems with mysql module. Otherwise your python just "looks" for packages in other places and don't looks here.

Let's look where your python start from:

```
$ which python
/usr/bin/python

```

If there is any other path then you run non default ubuntu python. If you add that other python expressly you have to be able to check your PYTHONPATH (where python search for modules) and add site-packages with MySQLdb iunstalled to it.

You can check your PYTHONPATH like this:

```
$ python
Python 2.5.1 (r251:54863, May  2 2007, 16:56:35) 
[GCC 4.1.2 (Ubuntu 4.1.2-0ubuntu4)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import sys
>>> print sys.path
['', '/usr/lib/python25.zip', '/usr/lib/python2.5', '/usr/lib/python2.5/plat-linux2', '/usr/lib/python2.5/lib-tk', '/usr/lib/python2.5/lib-dynload', '/usr/local/lib/python2.5/site-packages', '/usr/lib/python2.5/site-packages', '/usr/lib/python2.5/site-packages/Numeric', '/usr/lib/python2.5/site-packages/gst-0.10', '/var/lib/python-support/python2.5', '/usr/lib/python2.5/site-packages/gtk-2.0', '/var/lib/python-support/python2.5/gtk-2.0']
```

Hope this helps....

---

### Post by kportertx on 2007-06-18
If your still looking for a solution I know there is one out there (I got it to work before), but finding it was difficult.  And I am having to find it all over again :(.

I remember it had something to do w/ mysql client lib file.  Hope that helps...  Cause it isn't helping me re-find the solution... If I find the solution in the mean time I will post it here.

---

### Post by kportertx on 2007-06-18
Here read this should set you up :)
[http://www.mail-archive.com/pylons-discuss@googlegroups.com/msg04191.html]("http://www.mail-archive.com/pylons-discuss@googlegroups.com/msg04191.html")

---

### Post by CyfrMonk on 2007-06-27
apt-get install libmysqlclient15-dev

This will install the mysql_config tool. 

You may need python-dev package too.

---

### Post by lmoxiel on 2007-07-04
I've found a solution by browsing at the code in setup_posix.py

Short Answer:

Just add the /path/to/mysql/bin directory to your $PATH

The mysql/bin directory has a binary called mysql_config.  The setup_posix.py checks for this using..
(in the get_config() function called from setup.py)
<snip>
from setup_common import get_metadata_and_options, enabled, create_release_file
metadata, options = get_metadata_and_options()

if 'mysql_config' in options:
        mysql_config.path = options['mysql_config']
</snip>

Basically if it can't find the program binary called mysql_config, then it fails. 

After setting your path, everything works; You may now build.
python setup.py build
sudo python setup.py install

Note: I'veinstalling MySQL 5.0 by downloading it.

Enjoy!  :popcorn:

~= Chris =~

---

### Post by ablegreen on 2007-07-04
I've never used MySql with Python has anyone noticed that Python always get its Path wrong? I had to fix mine by going in to the registry when mod_python on Apache wouldn't work. Oh and this is on Windows (haven't tried it on Ubuntu or any Linux yet)

---

### Post by pmasiar on 2007-07-04
> **ablegreen said:**
> has anyone noticed that Python always get its Path wrong? I had to fix mine by going in to the registry

It's windows problem. Did docs about installing Python om Windows worked for you? I remember blurb about setting path. Registry is MSFT proprietary database and I guess not enough people are interested enough to learn its quirks. Both Python and Apache came from Linux world, where plain text config files are used. BTW I am not sure what additional perks gives you to have config in database (registry) instead of text files (except easier to get corrupted and harder to repair). 

On Linux, Python "just works" (tm). :-)

---

### Post by ablegreen on 2007-07-04
> **pmasiar said:**
> It's windows problem. Did docs about installing Python om Windows worked for you? I remember blurb about setting path. Registry is MSFT proprietary database and I guess not enough people are interested enough to learn its quirks. Both Python and Apache came from Linux world, where plain text config files are used. BTW I am not sure what additional perks gives you to have config in database (registry) instead of text files (except easier to get corrupted and harder to repair). 

On Linux, Python "just works" (tm). :-)

Bah, didn't bother to read the docs because I just clicked the .msi file and went through it and I thought that was it:p

---

### Post by pmasiar on 2007-07-05
> **ablegreen said:**
> Bah, didn't bother to read the docs 

half-literate persons usually have problems described (with solutions) in docs or FAQs :-)

---

### Post by runningwithscissors on 2007-07-05
@OP: If you get a chance have a look at Sqlalchemy. Very nice. You don't need to touch ugly SQL and it supports at least 3 backends well (mysql, postgres and sqlite). The API is not yet stable though, so it may not be suited for production work.

---

### Post by JasonSilver on 2008-04-18
I hope this is the right place to post this follow-up question. If not, please direct me to a better place if you don't mind.

I've been working on this same problem for two weeks and cannot find a solution that works for me.

I am using Plone and loving it, and have decided to set up a new server with Zope and Plone (the server I am currently using was set up by someone before me).

In the set up process, I am trying to import the old site, and upon doing so run into this familiar mysql error we've been talking about here. 

The first error was:
 An error was encountered while publishing this resource.
 Error Type: ImportError
 Error Value: No module named ZMySQLDA.DA

So I installed the Zope MySQL interface Product:
wget [http://superb-east.dl.sourceforge.net/sourceforge/mysql-python/ZMySQLDA-2.0.8.tar.gz](http://superb-east.dl.sourceforge.net/sourceforge/mysql-python/ZMySQLDA-2.0.8.tar.gz)
cd /opt/Plone-2.5.3
tar -zxvf ~/ZMySQLDA-2.0.8.tar.gz

THIS IS WHERE I HAVE BEEN STUCK:
There is a new error: No module named _mysql

Here are some things I've tried:

wget [http://superb-east.dl.sourceforge.net/sourceforge/mysql-python/MySQL-python-1.2.2.tar.gz](http://superb-east.dl.sourceforge.net/sourceforge/mysql-python/MySQL-python-1.2.2.tar.gz)
cd /opt/Plone-2.5.3
tar -zxvf ~/MySQL-python-1.2.2.tar.gz

Troubleshooting:
1. Searched for error on Google.
2. Tried installing MySQL support for Python:
    sudo apt-get install mysql-server-5.0 python-mysqldb
Still errors, so tried
    sudo apt-get install python-mysqldb

Already latest version...

Tried apt-get install python-mysqldb and apt-get install python-mysql - already latest version.

I think I've traced down the problem to the following cause: Zope uses a different version of Python, which is located:
/opt/Plone-2.5.3/Python-2.4.4

When I run the main version of Python (type python) then all the mysql things seem to be there... but when I run Zope's version of python the tests outlined above fail.

How do I proceed?

Thanks in advance!!
Jason Silver

---

### Post by Can+~ on 2008-04-18
I noticed synaptic has both zope and plone with all the dependencies fixed for you, are you installing from source code?

Try using synaptic and download zope3 from there.

---

### Post by JasonSilver on 2008-04-18
Hmm, I should have stated that I'm installing this on Ubuntu server, so I'm not sure synaptic comes into play there.

To install Plone I did the following:
apt-get update
apt-get install language-pack-en-base
apt-get dist-upgrade
apt-get install wget (may not be necessary)
apt-get install gcc
apt-get install make
apt-get install build-essential
wget [http://downloads.sourceforge.net/plone/Plone-2.5.3-UnifiedInstaller.tgz](http://downloads.sourceforge.net/plone/Plone-2.5.3-UnifiedInstaller.tgz)
    If trouble here, download the file from desktop, and then scp it over to the server's home folder.
tar xvzf Plone2.5-UnifiedInstaller-r2.tgz
cd Plone2.5-UnifiedInstaller

./install.sh

Make a new instance:
    /opt/Plone-2.5.3/bin/mkzopeinstance.py 

Copy all products in zeocluster/client1/Products to the new fammed/Products folder
    cp -r /opt/Plone-2.5.3/zeocluster/Products/* /opt/Plone-2.5.3/fammed/Products

Not sure if this is necessary, but copied these products too:
    cp -r /opt/Plone-2.5.3/zeocluster/client1/Products/* /opt/Plone-2.5.3/fammed/Products
    cp -r /opt/Plone-2.5.3/zeocluster/client2/Products/* /opt/Plone-2.5.3/fammed/Products

Login to the original family medicine server, and zip up all Products in the Products folder.
scp them over to the new server, and extract them all into the products folder of the new fammed instance.

tar -zxvf ./FamMed-Products-Folder.tgz

cd ~/opt/Plone-2.5.3/fammed/Products/
cp -R * /opt/Plone-2.5.3/fammed/Products/

/opt/Plone-2.5.3/fammed/bin/zopectl start

Go the the ZMI:
[http://130.113.77.39:8080/manage](http://130.113.77.39:8080/manage)

chown plone:plone /opt/Plone-2.5.3/fammed/

Any other thoughts?

---

### Post by Can+~ on 2008-04-18
[PHP]sudo apt-get install plone-site[/PHP]

This outputs:
```
canxp@asgard:~$ sudo apt-get install plone-site 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  tofrodos tidy libtidy-0.99-0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  lynx python-docutils python-roman python2.4 python2.4-minimal
  zope-archetypes zope-atcontenttypes zope-atrbw zope-btreefolder2 zope-cmf1.6
  zope-cmfactionicons1.6 zope-cmfcalendar1.6 zope-cmfcore1.6
  zope-cmfdefault1.6 zope-cmfdynamicviewfti zope-cmfformcontroller
  zope-cmfplacefulworkflow zope-cmfplone zope-cmfquickinstallertool
  zope-cmfsetup1.6 zope-cmftopic1.6 zope-cmfuid1.6 zope-common
  zope-dcworkflow1.6 zope-extendedpathindex zope-externaleditor
  zope-genericsetup zope-groupuserfolder zope-kupu zope-marshall
  zope-mimetypesregistry zope-pas zope-passwordresettool
  zope-ploneerrorreporting zope-plonelanguagetool zope-plonepas
  zope-plonetranslations zope-pluginregistry zope-portaltransforms zope-pts
  zope-resourceregistries zope-securemailhost zope-statusmessages
  zope-validation zope2.10 zope2.9
Suggested packages:
  plone python2.4-doc python-profiler zope-plonetestcase zope-filesystemsite
  wv unrtf ppthtml xlhtml python-unit zope-book zope-devguide
Recommended packages:
  zope-linguaplone zope-cachefu
The following NEW packages will be installed:
  lynx plone-site python-docutils python-roman python2.4 python2.4-minimal
  zope-archetypes zope-atcontenttypes zope-atrbw zope-btreefolder2 zope-cmf1.6
  zope-cmfactionicons1.6 zope-cmfcalendar1.6 zope-cmfcore1.6
  zope-cmfdefault1.6 zope-cmfdynamicviewfti zope-cmfformcontroller
  zope-cmfplacefulworkflow zope-cmfplone zope-cmfquickinstallertool
  zope-cmfsetup1.6 zope-cmftopic1.6 zope-cmfuid1.6 zope-common
  zope-dcworkflow1.6 zope-extendedpathindex zope-externaleditor
  zope-genericsetup zope-groupuserfolder zope-kupu zope-marshall
  zope-mimetypesregistry zope-pas zope-passwordresettool
  zope-ploneerrorreporting zope-plonelanguagetool zope-plonepas
  zope-plonetranslations zope-pluginregistry zope-portaltransforms zope-pts
  zope-resourceregistries zope-securemailhost zope-statusmessages
  zope-validation zope2.10 zope2.9
0 upgraded, 47 newly installed, 0 to remove and 0 not upgraded.
Need to get 29.1MB of archives.
After unpacking 173MB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

---

### Post by JasonSilver on 2008-04-21
Wow, having lots of problems with this.

1. I uninstalled my old version of zope/plone.
2. I used your plone-site installation to install again.
3. It didn't ask me at any point what version of Plone I want (I want 2.5.3, not 3).
4. It installed Plone/Zope to non-standard places. (rather than /opt/Plone-x.x.x/ it but it in /etc/Zope/blah/blah)

Then I get this weird dependency error all the time-- so I do sudo apt-get -f install and apt-get autoremove, but it's an endless circle of errors...

I'm sorry to bear bad news. :-( I wish I was able to figure this out on my own and not trouble you. If you can direct me to a place to find more info, that would be terrific.

Thanks so much,
Jason Silver

---

### Post by mssever on 2008-04-21
> **JasonSilver said:**
>  3. It didn't ask me at any point what version of Plone I want (I want 2.5.3, not 3)..deb packages install the most recent version. You can search the Ubuntu package archive for the version you want and see if it's there. If so, read the aptitude man page to see how to specify a specific version. You might also be able to find a soure package of the proper version, either on the Ubuntu website or on Debian's site, that you can build a .deb from.
> 4. It installed Plone/Zope to non-standard places. (rather than /opt/Plone-x.x.x/ it but it in /etc/Zope/blah/blah)You're saying that it puts its configuration in /etc/Zope? That's pretty standard. Ubuntu packages aren't supposed to put anything under /opt.

> Then I get this weird dependency error all the time--What's the error? It's hard to diagnose the error if you don't provide it.

---

### Post by JasonSilver on 2008-04-21
Sorry, you're right-- I should have included the error.
```

Removing zope2.10 ...
/var/lib/dpkg/info/zope2.10.prerm: 7: cannot create /var/lib/zope2.10/_list_of_pyc_pyo_to_be_deleted_: Directory nonexistent
dpkg: error processing zope2.10 (--remove):
 subprocess pre-removal script returned error exit status 2
Removing xsltproc ...
dpkg: python2.4: dependency problems, but removing anyway as you request:
 zope2.10 depends on python2.4 (>= 2.4.3).
 zope-common depends on python2.4.
Removing python2.4 ...
Removing python2.4-minimal ...
Unlinking and removing bytecode for runtime python2.4
dpkg: zope-common: dependency problems, but removing anyway as you request:
 zope2.10 depends on zope-common (>= 0.5.21); however:
  Package zope-common is to be removed.
Removing zope-common ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 zope2.10
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@fammedweb:~# sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  zope2.10: Depends: python2.4 (>= 2.4.3) but it is not installed
            PreDepends: zope-common (>= 0.5.21) but it is not installed
E: Unmet dependencies. Try using -f.
root@fammedweb:~# sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  python2.4 zope2.10 zope-common python2.4-minimal
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  python2.4 python2.4-minimal zope-common
Suggested packages:
  python2.4-doc python-profiler
The following NEW packages will be installed:
  python2.4 python2.4-minimal zope-common
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3994kB of archives.
After unpacking, 13.8MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
Selecting previously deselected package python2.4-minimal.
(Reading database ... 28349 files and directories currently installed.)
Unpacking python2.4-minimal (from .../python2.4-minimal_2.4.4-6ubuntu4.1_amd64.deb) ...
Selecting previously deselected package python2.4.
Unpacking python2.4 (from .../python2.4_2.4.4-6ubuntu4.1_amd64.deb) ...
Selecting previously deselected package zope-common.
Unpacking zope-common (from .../zope-common_0.5.36_all.deb) ...
Setting up python2.4-minimal (2.4.4-6ubuntu4.1) ...
Linking and byte-compiling packages for runtime python2.4...

Setting up python2.4 (2.4.4-6ubuntu4.1) ...

Setting up zope-common (0.5.36) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
root@fammedweb:~# sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python2.4 zope2.10 zope-common python2.4-minimal
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@fammedweb:~# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python2.4 zope2.10 zope-common python2.4-minimal
The following packages will be REMOVED:
  python2.4 python2.4-minimal zope-common zope2.10
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking, 62.2MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 29013 files and directories currently installed.)
Removing zope2.10 ...
/var/lib/dpkg/info/zope2.10.prerm: 7: cannot create /var/lib/zope2.10/_list_of_pyc_pyo_to_be_deleted_: Directory nonexistent
dpkg: error processing zope2.10 (--remove):
 subprocess pre-removal script returned error exit status 2
dpkg: python2.4: dependency problems, but removing anyway as you request:
 zope2.10 depends on python2.4 (>= 2.4.3).
 zope-common depends on python2.4.
Removing python2.4 ...
Removing python2.4-minimal ...
Unlinking and removing bytecode for runtime python2.4
dpkg: zope-common: dependency problems, but removing anyway as you request:
 zope2.10 depends on zope-common (>= 0.5.21); however:
  Package zope-common is to be removed.
Removing zope-common ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 zope2.10
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@fammedweb:~# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  zope2.10: Depends: python2.4 (>= 2.4.3) but it is not installed
            PreDepends: zope-common (>= 0.5.21) but it is not installed
E: Unmet dependencies. Try using -f.

```

Can I just ignore that error?

Jason

---

### Post by mssever on 2008-04-21
Looks like it's complaining about the directory 
/var/lib/zope2.10 not existing. Try creating the directory, then uninstalling again.

If you ignore the error, apt will keep complaining.

---

### Post by JasonSilver on 2008-04-22
OK, that helps that problem.

Still stuck on the same python problem.

I read something somewhere about changing an environment variable or something that will tell other versions of Python where to locate things like the _mysql module. 

I don't remember where I read that, and I may have completely misunderstood. :(

Any thing else I could try?

Jason

---

### Post by JasonSilver on 2008-04-22
Or maybe I can copy the right bits to my zope install folder (in the Python subfolder?) I found this: [http://www.zopezone.com/discussions/general/00000270](http://www.zopezone.com/discussions/general/00000270)

I tried this: 
cp /var/lib/python-support/python2.4/_mysql.so /opt/Plone-2.5.3/Python-2.4.4/
And restarted Zope, but no go.

---

### Post by JasonSilver on 2008-04-22
OK, I found the solution!!!

instead of just:

python setup.py build
python setup.py install

It's 

/opt/Plone-2.5.3/Python-2.4.4/bin/python setup.py build
/opt/Plone-2.5.3/Python-2.4.4/bin/python setup.py install

Simple!

Thanks for everyone's help.

---

### Post by EugenZglimbea on 2008-05-13
I am having the same problem after upgrading from Ubuntu 6.06LTS to 8.04LTS.  This was working just fine on 6.06, meaning that I just installed python-mysqldb and started using it, didn't have to change my python path variable at all.  

After the upgrade, I started getting the ImportError.  Python-mysqldb is still installed on the system, but my python scripts cannot find it.

A quick fix I did was to add to the path the path to the _mysql.so library in my script before importing MySQLdb.

import sys
sys.path.append('/var/lib/python-support/python2.5')
import MySQLdb

However, this is only temporary, since when we upgrade python this line will break.  Is there any way to permanently add the path to the _mysql.so library to the python path, via command line?

I'm still slightly a newbie so please reply with step by step instructions.  Thanks greatly

Eugen Z.

---

### Post by JasonSilver on 2008-05-14
> **EugenZglimbea said:**
> I am having the same problem after upgrading from Ubuntu 6.06LTS to 8.04LTS.  This was working just fine on 6.06, meaning that I just installed python-mysqldb and started using it, didn't have to change my python path variable at all.  

After the upgrade, I started getting the ImportError.  Python-mysqldb is still installed on the system, but my python scripts cannot find it.


This might work:


```
cd ~
wget http://superb-east.dl.sourceforge.net/sourceforge/mysql-python/ZMySQLDA-2.0.8.tar.gz
tar -zxvf ~/ZMySQLDA-2.0.8.tar.gz
mv ~/lib/python/Products/ZMySQLDA/ /opt/Plone-2.5.3/lib/python/Products/

wget http://superb-east.dl.sourceforge.net/sourceforge/mysql-python/MySQL-python-2.4.4.tar.gz
tar -zxvf ~/MySQL-python-1.2.2.tar.gz
apt-get install libmysqlclient15-dev

```

Install _mysql in Plone's special version of Python:
```
/opt/Plone-2.5.3/Python-2.4.4/bin/python setup.py build
/opt/Plone-2.5.3/Python-2.4.4/bin/python setup.py install

```

Zope needs to be restarted now-- if it's already running, issue this command:

```
/opt/Plone-2.5.3/fammed/bin/zopectl restart
```

---

### Post by trinaryouroboros on 2009-10-30
:KS **I'm writing this as a thank you to forum posters, and to hopefully clear the air for other users who want to use this module.** :KS

*(no thanks to the lunkheads who make this module though, once in Two Years it gets updated? Give me a Break!)*

My original problem, was that I was toying with the Synaptic installed packages for python-mysqldb, and I was receiving the following error whenever trying to run a python script that used the MySQLdb module:

```
/var/lib/python-support/python2.6/MySQLdb/__init__.py:34: DeprecationWarning: the sets module is deprecated
  from sets import ImmutableSet
```

More importantly, tons of functionality was broken or not working as designed - it was impossible to use it to reference a cursor, even!

After a short bit of hunting, I figured out that, for some reason, _Ubuntu is really behind on this package_.  

The author/team responsible for the MySQL modules themselves have a current version of MySQL-python-1.2.3c1, while, as of this time - **on the 64-bit repositories, the only stable package is currently python-mysqldb 1.2.2-7ubuntu1**, and on the package maintainers site, it explicitly says that 1.2.3 is on their to do list...however, there was a 32-bit package, but I didn't want to mess around with it, frankly, so I went straight to the author to compile this business from scratch.

So, I downloaded the tar [from here]("http://sourceforge.net/projects/mysql-python/"), and unpacked it, ran "python setup.py build", but got the following hold up:

```
EnvironmentError: mysql_config not found
```

**Thanks to [seanf]("http://ubuntuforums.org/member.php?u=1779"), I used the following command and it got around this problem:**

```
sudo apt-get install libmysqlclient15-dev
```

However, when trying to run "python setup.py build" the following smorgasboard of errors appeared:

```
root@******:/home/*********/MySQL-python-1.2.3c1# python setup.py build
running build
running build_py
creating build
creating build/lib.linux-x86_64-2.6
copying _mysql_exceptions.py -> build/lib.linux-x86_64-2.6
creating build/lib.linux-x86_64-2.6/MySQLdb
copying MySQLdb/__init__.py -> build/lib.linux-x86_64-2.6/MySQLdb
copying MySQLdb/converters.py -> build/lib.linux-x86_64-2.6/MySQLdb
copying MySQLdb/connections.py -> build/lib.linux-x86_64-2.6/MySQLdb
copying MySQLdb/cursors.py -> build/lib.linux-x86_64-2.6/MySQLdb
copying MySQLdb/release.py -> build/lib.linux-x86_64-2.6/MySQLdb
copying MySQLdb/times.py -> build/lib.linux-x86_64-2.6/MySQLdb
creating build/lib.linux-x86_64-2.6/MySQLdb/constants
copying MySQLdb/constants/__init__.py -> build/lib.linux-x86_64-2.6/MySQLdb/constants
copying MySQLdb/constants/CR.py -> build/lib.linux-x86_64-2.6/MySQLdb/constants
copying MySQLdb/constants/FIELD_TYPE.py -> build/lib.linux-x86_64-2.6/MySQLdb/constants
copying MySQLdb/constants/ER.py -> build/lib.linux-x86_64-2.6/MySQLdb/constants
copying MySQLdb/constants/FLAG.py -> build/lib.linux-x86_64-2.6/MySQLdb/constants
copying MySQLdb/constants/REFRESH.py -> build/lib.linux-x86_64-2.6/MySQLdb/constants
copying MySQLdb/constants/CLIENT.py -> build/lib.linux-x86_64-2.6/MySQLdb/constants
running build_ext
building '_mysql' extension
creating build/temp.linux-x86_64-2.6
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -Dversion_info=(1,2,3,'gamma',1) -D__version__=1.2.3c1 -I/usr/include/mysql -I/usr/include/python2.6 -c _mysql.c -o build/temp.linux-x86_64-2.6/_mysql.o -DBIG_JOINS=1 -fPIC -fno-strict-aliasing
In file included from _mysql.c:29:
pymemcompat.h:10:20: error: Python.h: No such file or directory
_mysql.c:30:26: error: structmember.h: No such file or directory
_mysql.c:62: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:63: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:64: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:65: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:66: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:67: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:68: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:69: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:70: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:71: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:72: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:75: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
_mysql.c:85: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘_mysql_ConnectionObject_Type’
_mysql.c:88: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
_mysql.c:96: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘_mysql_ResultObject_Type’
_mysql.c:105: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:227: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:318: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:336: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:359: error: expected declaration specifiers or ‘...’ before ‘PyObject’
_mysql.c:360: error: expected declaration specifiers or ‘...’ before ‘PyObject’
_mysql.c: In function ‘_mysql_ResultObject_Initialize’:
_mysql.c:362: error: ‘NULL’ undeclared (first use in this function)
_mysql.c:362: error: (Each undeclared identifier is reported only once
_mysql.c:362: error: for each function it appears in.)
_mysql.c:364: warning: initialization from incompatible pointer type
_mysql.c:366: error: ‘PyObject’ undeclared (first use in this function)
_mysql.c:366: error: ‘conv’ undeclared (first use in this function)
_mysql.c:366: error: invalid operands to binary * (have ‘char **’ and ‘char **’)
_mysql.c:366: warning: statement with no effect
_mysql.c:370: warning: implicit declaration of function ‘PyArg_ParseTupleAndKeywords’
_mysql.c:370: error: ‘args’ undeclared (first use in this function)
_mysql.c:370: error: ‘kwargs’ undeclared (first use in this function)
_mysql.c:373: warning: implicit declaration of function ‘PyDict_New’
_mysql.c:373: warning: statement with no effect
_mysql.c:375: error: ‘_mysql_ResultObject’ has no member named ‘conn’
_mysql.c:375: error: expected expression before ‘)’ token
_mysql.c:375: error: invalid operands to binary * (have ‘char **’ and ‘char **’)
_mysql.c:375: warning: statement with no effect
_mysql.c:376: warning: implicit declaration of function ‘Py_INCREF’
_mysql.c:377: error: ‘_mysql_ResultObject’ has no member named ‘use’
_mysql.c:377: warning: statement with no effect
_mysql.c:378: error: ‘Py_BEGIN_ALLOW_THREADS’ undeclared (first use in this function)
_mysql.c:378: warning: statement with no effect
_mysql.c:380: error: ‘_mysql_ConnectionObject’ has no member named ‘connection’
_mysql.c:380: warning: passing argument 1 of ‘mysql_use_result’ from incompatible pointer type
_mysql.c:382: error: ‘_mysql_ConnectionObject’ has no member named ‘connection’
_mysql.c:382: warning: passing argument 1 of ‘mysql_store_result’ from incompatible pointer type
_mysql.c:383: error: ‘_mysql_ResultObject’ has no member named ‘result’
_mysql.c:383: warning: statement with no effect
_mysql.c:384: error: ‘Py_END_ALLOW_THREADS’ undeclared (first use in this function)
_mysql.c:384: warning: statement with no effect
_mysql.c:386: error: ‘_mysql_ResultObject’ has no member named ‘converter’
_mysql.c:386: warning: implicit declaration of function ‘PyTuple_New’
_mysql.c:386: warning: statement with no effect
_mysql.c:390: error: ‘_mysql_ResultObject’ has no member named ‘nfields’
_mysql.c:390: warning: statement with no effect
_mysql.c:391: error: ‘_mysql_ResultObject’ has no member named ‘converter’
_mysql.c:394: error: ‘tmp’ undeclared (first use in this function)
_mysql.c:394: error: invalid operands to binary * (have ‘char **’ and ‘char **’)
_mysql.c:394: error: ‘fun’ undeclared (first use in this function)
_mysql.c:394: warning: left-hand operand of comma expression has no effect
_mysql.c:394: warning: statement with no effect
_mysql.c:395: warning: implicit declaration of function ‘PyInt_FromLong’
_mysql.c:395: warning: statement with no effect
_mysql.c:397: warning: implicit declaration of function ‘PyObject_GetItem’
_mysql.c:397: warning: statement with no effect
_mysql.c:398: warning: implicit declaration of function ‘Py_DECREF’
_mysql.c:400: warning: implicit declaration of function ‘PyErr_Clear’
_mysql.c:401: error: ‘Py_None’ undeclared (first use in this function)
_mysql.c:401: warning: statement with no effect
_mysql.c:404: warning: implicit declaration of function ‘PySequence_Check’
_mysql.c:405: warning: implicit declaration of function ‘PySequence_Size’
_mysql.c:406: error: ‘fun2’ undeclared (first use in this function)
_mysql.c:406: error: invalid operands to binary * (have ‘char **’ and ‘char **’)
_mysql.c:406: warning: statement with no effect
_mysql.c:408: error: ‘t’ undeclared (first use in this function)
_mysql.c:408: error: invalid operands to binary * (have ‘char **’ and ‘char **’)
_mysql.c:408: warning: implicit declaration of function ‘PySequence_GetItem’
_mysql.c:408: warning: statement with no effect
_mysql.c:410: warning: implicit declaration of function ‘PyTuple_Check’
_mysql.c:411: warning: implicit declaration of function ‘PyTuple_GET_SIZE’
_mysql.c:413: error: ‘pmask’ undeclared (first use in this function)
_mysql.c:413: error: invalid operands to binary * (have ‘char **’ and ‘char **’)
_mysql.c:413: warning: statement with no effect
_mysql.c:414: warning: implicit declaration of function ‘PyTuple_GET_ITEM’
_mysql.c:414: warning: statement with no effect
_mysql.c:415: warning: statement with no effect
_mysql.c:416: warning: implicit declaration of function ‘PyInt_Check’
_mysql.c:417: warning: implicit declaration of function ‘PyInt_AS_LONG’
_mysql.c:433: warning: statement with no effect
_mysql.c:436: warning: statement with no effect
_mysql.c:438: warning: implicit declaration of function ‘PyTuple_SET_ITEM’
_mysql.c:438: error: ‘_mysql_ResultObject’ has no member named ‘converter’
_mysql.c: In function ‘_mysql_ResultObject_clear’:
_mysql.c:462: warning: implicit declaration of function ‘Py_XDECREF’
_mysql.c:462: error: ‘_mysql_ResultObject’ has no member named ‘converter’
_mysql.c:463: error: ‘_mysql_ResultObject’ has no member named ‘converter’
_mysql.c:463: error: ‘NULL’ undeclared (first use in this function)
_mysql.c:463: warning: statement with no effect
_mysql.c:464: error: ‘_mysql_ResultObject’ has no member named ‘conn’
_mysql.c:465: error: ‘_mysql_ResultObject’ has no member named ‘conn’
_mysql.c:465: warning: statement with no effect
_mysql.c: At top level:
_mysql.c:472: error: expected declaration specifiers or ‘...’ before ‘PyObject’
_mysql.c:473: error: expected declaration specifiers or ‘...’ before ‘PyObject’
_mysql.c: In function ‘_mysql_ConnectionObject_Initialize’:
_mysql.c:475: error: ‘NULL’ undeclared (first use in this function)
_mysql.c:475: warning: initialization from incompatible pointer type
_mysql.c:476: error: ‘PyObject’ undeclared (first use in this function)
_mysql.c:476: error: ‘conv’ undeclared (first use in this function)
_mysql.c:476: error: invalid operands to binary * (have ‘char **’ and ‘char **’)
_mysql.c:476: warning: statement with no effect
_mysql.c:477: error: ‘ssl’ undeclared (first use in this function)
_mysql.c:477: error: invalid operands to binary * (have ‘char **’ and ‘char **’)
_mysql.c:477: warning: statement with no effect
_mysql.c:479: warning: initialization from incompatible pointer type
_mysql.c:479: warning: initialization from incompatible pointer type
_mysql.c:479: warning: initialization from incompatible pointer type
_mysql.c:480: warning: initialization from incompatible pointer type
_mysql.c:480: warning: initialization from incompatible pointer type
_mysql.c:482: warning: initialization from incompatible pointer type
_mysql.c:482: warning: initialization from incompatible pointer type
_mysql.c:482: warning: initialization from incompatible pointer type
_mysql.c:483: warning: initialization from incompatible pointer type
_mysql.c:483: warning: initialization from incompatible pointer type
_mysql.c:493: error: initializer element is not constant
_mysql.c:493: error: (near initialization for ‘kwlist[16]’)
_mysql.c:496: warning: initialization from incompatible pointer type
_mysql.c:497: warning: initialization from incompatible pointer type
_mysql.c:498: warning: initialization from incompatible pointer type
_mysql.c:500: error: ‘_mysql_ConnectionObject’ has no member named ‘converter’
_mysql.c:500: warning: statement with no effect
_mysql.c:501: error: ‘_mysql_ConnectionObject’ has no member named ‘open’
_mysql.c:501: warning: statement with no effect
_mysql.c:502: warning: implicit declaration of function ‘_mysql_Exception’
_mysql.c:503: error: ‘args’ undeclared (first use in this function)
_mysql.c:503: error: ‘kwargs’ undeclared (first use in this function)
_mysql.c:518: warning: statement with no effect
_mysql.c:525: error: ‘_mysql_ConnectionObject’ has no member named ‘converter’
_mysql.c:525: warning: statement with no effect
_mysql.c:533: error: ‘value’ undeclared (first use in this function)
_mysql.c:533: error: invalid operands to binary * (have ‘char **’ and ‘char **’)
_mysql.c:533: warning: statement with no effect
_mysql.c:534: warning: implicit declaration of function ‘PyMapping_GetItemString’
_mysql.c:534: warning: statement with no effect
_mysql.c:534: warning: implicit declaration of function ‘PyString_AsString’
_mysql.c:534: warning: assignment makes pointer from integer without a cast
_mysql.c:535: warning: statement with no effect
_mysql.c:535: warning: assignment makes pointer from integer without a cast
_mysql.c:536: warning: statement with no effect
_mysql.c:536: warning: assignment makes pointer from integer without a cast
_mysql.c:537: warning: statement with no effect
_mysql.c:537: warning: assignment makes pointer from integer without a cast
_mysql.c:538: warning: statement with no effect
_mysql.c:538: warning: assignment makes pointer from integer without a cast
_mysql.c:546: error: ‘Py_BEGIN_ALLOW_THREADS’ undeclared (first use in this function)
_mysql.c:546: warning: statement with no effect
_mysql.c:547: error: ‘_mysql_ConnectionObject’ has no member named ‘connection’
_mysql.c:547: warning: passing argument 1 of ‘mysql_init’ from incompatible pointer type
_mysql.c:550: error: ‘_mysql_ConnectionObject’ has no member named ‘connection’
_mysql.c:551: warning: passing argument 1 of ‘mysql_options’ from incompatible pointer type
_mysql.c:554: error: ‘_mysql_ConnectionObject’ has no member named ‘connection’
_mysql.c:554: warning: passing argument 1 of ‘mysql_options’ from incompatible pointer type
_mysql.c:558: error: ‘_mysql_ConnectionObject’ has no member named ‘connection’
_mysql.c:558: warning: passing argument 1 of ‘mysql_options’ from incompatible pointer type
_mysql.c:559: warning: comparison of distinct pointer types lacks a cast
_mysql.c:560: error: ‘_mysql_ConnectionObject’ has no member named ‘connection’
_mysql.c:560: warning: passing argument 1 of ‘mysql_options’ from incompatible pointer type
_mysql.c:561: warning: comparison of distinct pointer types lacks a cast
_mysql.c:562: error: ‘_mysql_ConnectionObject’ has no member named ‘connection’
_mysql.c:562: warning: passing argument 1 of ‘mysql_options’ from incompatible pointer type
_mysql.c:563: warning: comparison of distinct pointer types lacks a cast
_mysql.c:564: error: ‘_mysql_ConnectionObject’ has no member named ‘connection’
_mysql.c:564: warning: passing argument 1 of ‘mysql_options’ from incompatible pointer type
_mysql.c:567: error: ‘_mysql_ConnectionObject’ has no member named ‘connection’
_mysql.c:567: warning: passing argument 1 of ‘mysql_options’ from incompatible pointer type
_mysql.c:571: error: ‘_mysql_ConnectionObject’ has no member named ‘connection’
_mysql.c:572: warning: passing argument 1 of ‘mysql_ssl_set’ from incompatible pointer type
_mysql.c:575: error: ‘_mysql_ConnectionObject’ has no member named ‘connection’
_mysql.c:576: warning: passing argument 1 of ‘mysql_real_connect’ from incompatible pointer type
_mysql.c:578: error: ‘Py_END_ALLOW_THREADS’ undeclared (first use in this function)
_mysql.c:578: warning: statement with no effect
_mysql.c:590: error: ‘_mysql_ConnectionObject’ has no member named ‘open’
_mysql.c:590: warning: statement with no effect
_mysql.c: At top level:
_mysql.c:648: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c: In function ‘_mysql_ConnectionObject_clear’:
_mysql.c:680: error: ‘_mysql_ConnectionObject’ has no member named ‘converter’
_mysql.c:681: error: ‘_mysql_ConnectionObject’ has no member named ‘converter’
_mysql.c:681: error: ‘NULL’ undeclared (first use in this function)
_mysql.c:681: warning: statement with no effect
_mysql.c: At top level:
_mysql.c:688: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:716: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:732: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:750: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:769: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:795: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:817: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:849: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:875: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:902: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:917: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:934: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:950: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:968: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1003: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1034: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1036: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1066: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1096: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1130: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1162: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1198: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1222: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1247: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1272: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1311: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1350: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1355: error: expected declaration specifiers or ‘...’ before ‘PyObject’
_mysql.c:1358: error: expected declaration specifiers or ‘...’ before ‘_PYFUNC’
_mysql.c: In function ‘_mysql__fetch_row’:
_mysql.c:1364: error: ‘PyObject’ undeclared (first use in this function)
_mysql.c:1364: error: ‘v’ undeclared (first use in this function)
_mysql.c:1364: error: invalid operands to binary * (have ‘char **’ and ‘char **’)
_mysql.c:1364: warning: statement with no effect
_mysql.c:1365: error: ‘_mysql_ResultObject’ has no member named ‘use’
_mysql.c:1366: error: ‘_mysql_ResultObject’ has no member named ‘result’
_mysql.c:1366: warning: passing argument 1 of ‘mysql_fetch_row’ from incompatible pointer type
_mysql.c:1368: error: ‘Py_BEGIN_ALLOW_THREADS’ undeclared (first use in this function)
_mysql.c:1368: warning: statement with no effect
_mysql.c:1369: error: ‘_mysql_ResultObject’ has no member named ‘result’
_mysql.c:1369: warning: passing argument 1 of ‘mysql_fetch_row’ from incompatible pointer type
_mysql.c:1370: error: ‘Py_END_ALLOW_THREADS’ undeclared (first use in this function)
_mysql.c:1370: warning: statement with no effect
_mysql.c:1372: error: ‘_mysql_ResultObject’ has no member named ‘conn’
_mysql.c:1372: error: ‘_mysql_ConnectionObject’ has no member named ‘connection’
_mysql.c:1372: warning: passing argument 1 of ‘mysql_errno’ from incompatible pointer type
_mysql.c:1373: error: ‘_mysql_ResultObject’ has no member named ‘conn’
_mysql.c:1377: warning: implicit declaration of function ‘_PyTuple_Resize’
_mysql.c:1377: error: ‘r’ undeclared (first use in this function)
_mysql.c:1380: warning: implicit declaration of function ‘convert_row’
_mysql.c:1380: warning: statement with no effect
_mysql.c: At top level:
_mysql.c:1398: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1477: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1505: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1527: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1567: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1596: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1611: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1626: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1641: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1657: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1692: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1710: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1733: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1750: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1766: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1795: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1818: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1848: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1870: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1897: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1918: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1959: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:1979: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c: In function ‘_mysql_ConnectionObject_dealloc’:
_mysql.c:2013: error: ‘PyObject’ undeclared (first use in this function)
_mysql.c:2013: error: ‘o’ undeclared (first use in this function)
_mysql.c:2013: error: invalid operands to binary * (have ‘char **’ and ‘char **’)
_mysql.c:2013: warning: statement with no effect
_mysql.c:2016: error: ‘_mysql_ConnectionObject’ has no member named ‘open’
_mysql.c:2017: warning: implicit declaration of function ‘_mysql_ConnectionObject_close’
_mysql.c:2017: error: ‘NULL’ undeclared (first use in this function)
_mysql.c:2017: warning: statement with no effect
_mysql.c:2020: warning: implicit declaration of function ‘PyMem_Free’
_mysql.c: At top level:
_mysql.c:2023: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:2040: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:2055: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:2077: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c: In function ‘_mysql_ResultObject_dealloc’:
_mysql.c:2099: error: ‘_mysql_ResultObject’ has no member named ‘result’
_mysql.c:2099: warning: passing argument 1 of ‘mysql_free_result’ from incompatible pointer type
_mysql.c: At top level:
_mysql.c:2104: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:2114: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘_mysql_ConnectionObject_methods’
_mysql.c:2329: error: array type has incomplete element type
_mysql.c:2330: error: ‘T_INT’ undeclared here (not in a function)
_mysql.c:2330: warning: implicit declaration of function ‘offsetof’
_mysql.c:2330: error: expected expression before ‘_mysql_ConnectionObject’
_mysql.c:2330: error: ‘RO’ undeclared here (not in a function)
_mysql.c:2337: error: ‘T_OBJECT’ undeclared here (not in a function)
_mysql.c:2337: error: expected expression before ‘_mysql_ConnectionObject’
_mysql.c:2344: error: ‘T_UINT’ undeclared here (not in a function)
_mysql.c:2344: error: expected expression before ‘_mysql_ConnectionObject’
_mysql.c:2351: error: expected expression before ‘_mysql_ConnectionObject’
_mysql.c:2358: error: expected expression before ‘_mysql_ConnectionObject’
_mysql.c:2365: error: ‘NULL’ undeclared here (not in a function)
_mysql.c:2368: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘_mysql_ResultObject_methods’
_mysql.c:2420: error: array type has incomplete element type
_mysql.c:2421: error: expected expression before ‘_mysql_ResultObject’
_mysql.c:2431: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:2459: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:2489: error: expected declaration specifiers or ‘...’ before ‘PyObject’
_mysql.c: In function ‘_mysql_ConnectionObject_setattr’:
_mysql.c:2491: error: ‘v’ undeclared (first use in this function)
_mysql.c:2492: warning: implicit declaration of function ‘PyErr_SetString’
_mysql.c:2492: error: ‘PyExc_AttributeError’ undeclared (first use in this function)
_mysql.c:2497: warning: implicit declaration of function ‘PyMember_Set’
_mysql.c: At top level:
_mysql.c:2514: error: expected declaration specifiers or ‘...’ before ‘PyObject’
_mysql.c: In function ‘_mysql_ResultObject_setattr’:
_mysql.c:2516: error: ‘v’ undeclared (first use in this function)
_mysql.c:2517: error: ‘PyExc_AttributeError’ undeclared (first use in this function)
_mysql.c: At top level:
_mysql.c:2535: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘_mysql_ConnectionObject_Type’
_mysql.c:2619: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘_mysql_ResultObject_Type’
_mysql.c:2705: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘_mysql_methods’
_mysql.c:2777: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_mysql.c:2809: warning: return type defaults to ‘int’
_mysql.c: In function ‘DL_EXPORT’:
_mysql.c:2809: error: expected declaration specifiers before ‘init_mysql’
_mysql.c:2887: error: expected ‘{’ at end of input
error: command 'gcc' failed with exit status 1

```

**I spotted [CyfrMonk]("http://ubuntuforums.org/member.php?u=151413")'s message in regards to possibly needing "python-dev" package, so I ran this:**

```
sudo apt-get install python-dev
```

Finally, I was able to run "python setup.py build":

```
root@******:/home/*********/MySQL-python-1.2.3c1# python setup.py build
running build
running build_py
copying MySQLdb/release.py -> build/lib.linux-x86_64-2.6/MySQLdb
running build_ext
building '_mysql' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -Dversion_info=(1,2,3,'gamma',1) -D__version__=1.2.3c1 -I/usr/include/mysql -I/usr/include/python2.6 -c _mysql.c -o build/temp.linux-x86_64-2.6/_mysql.o -DBIG_JOINS=1 -fPIC -fno-strict-aliasing
gcc -pthread -shared -Wl,-O1 -Wl,-Bsymbolic-functions build/temp.linux-x86_64-2.6/_mysql.o -L/usr/lib/mysql -lmysqlclient_r -o build/lib.linux-x86_64-2.6/_mysql.so
```

Then I was able to run "python setup.py install":

```
root@******:/home/*********/MySQL-python-1.2.3c1# python setup.py install
running install
running bdist_egg
running egg_info
writing MySQL_python.egg-info/PKG-INFO
writing top-level names to MySQL_python.egg-info/top_level.txt
writing dependency_links to MySQL_python.egg-info/dependency_links.txt
reading manifest file 'MySQL_python.egg-info/SOURCES.txt'
reading manifest template 'MANIFEST.in'
writing manifest file 'MySQL_python.egg-info/SOURCES.txt'
installing library code to build/bdist.linux-x86_64/egg
running install_lib
running build_py
copying MySQLdb/release.py -> build/lib.linux-x86_64-2.6/MySQLdb
running build_ext
creating build/bdist.linux-x86_64
creating build/bdist.linux-x86_64/egg
copying build/lib.linux-x86_64-2.6/_mysql_exceptions.py -> build/bdist.linux-x86_64/egg
creating build/bdist.linux-x86_64/egg/MySQLdb
copying build/lib.linux-x86_64-2.6/MySQLdb/connections.py -> build/bdist.linux-x86_64/egg/MySQLdb
copying build/lib.linux-x86_64-2.6/MySQLdb/__init__.py -> build/bdist.linux-x86_64/egg/MySQLdb
creating build/bdist.linux-x86_64/egg/MySQLdb/constants
copying build/lib.linux-x86_64-2.6/MySQLdb/constants/__init__.py -> build/bdist.linux-x86_64/egg/MySQLdb/constants
copying build/lib.linux-x86_64-2.6/MySQLdb/constants/FIELD_TYPE.py -> build/bdist.linux-x86_64/egg/MySQLdb/constants
copying build/lib.linux-x86_64-2.6/MySQLdb/constants/ER.py -> build/bdist.linux-x86_64/egg/MySQLdb/constants
copying build/lib.linux-x86_64-2.6/MySQLdb/constants/CR.py -> build/bdist.linux-x86_64/egg/MySQLdb/constants
copying build/lib.linux-x86_64-2.6/MySQLdb/constants/CLIENT.py -> build/bdist.linux-x86_64/egg/MySQLdb/constants
copying build/lib.linux-x86_64-2.6/MySQLdb/constants/FLAG.py -> build/bdist.linux-x86_64/egg/MySQLdb/constants
copying build/lib.linux-x86_64-2.6/MySQLdb/constants/REFRESH.py -> build/bdist.linux-x86_64/egg/MySQLdb/constants
copying build/lib.linux-x86_64-2.6/MySQLdb/cursors.py -> build/bdist.linux-x86_64/egg/MySQLdb
copying build/lib.linux-x86_64-2.6/MySQLdb/converters.py -> build/bdist.linux-x86_64/egg/MySQLdb
copying build/lib.linux-x86_64-2.6/MySQLdb/release.py -> build/bdist.linux-x86_64/egg/MySQLdb
copying build/lib.linux-x86_64-2.6/MySQLdb/times.py -> build/bdist.linux-x86_64/egg/MySQLdb
copying build/lib.linux-x86_64-2.6/_mysql.so -> build/bdist.linux-x86_64/egg
byte-compiling build/bdist.linux-x86_64/egg/_mysql_exceptions.py to _mysql_exceptions.pyc
byte-compiling build/bdist.linux-x86_64/egg/MySQLdb/connections.py to connections.pyc
byte-compiling build/bdist.linux-x86_64/egg/MySQLdb/__init__.py to __init__.pyc
byte-compiling build/bdist.linux-x86_64/egg/MySQLdb/constants/__init__.py to __init__.pyc
byte-compiling build/bdist.linux-x86_64/egg/MySQLdb/constants/FIELD_TYPE.py to FIELD_TYPE.pyc
byte-compiling build/bdist.linux-x86_64/egg/MySQLdb/constants/ER.py to ER.pyc
byte-compiling build/bdist.linux-x86_64/egg/MySQLdb/constants/CR.py to CR.pyc
byte-compiling build/bdist.linux-x86_64/egg/MySQLdb/constants/CLIENT.py to CLIENT.pyc
byte-compiling build/bdist.linux-x86_64/egg/MySQLdb/constants/FLAG.py to FLAG.pyc
byte-compiling build/bdist.linux-x86_64/egg/MySQLdb/constants/REFRESH.py to REFRESH.pyc
byte-compiling build/bdist.linux-x86_64/egg/MySQLdb/cursors.py to cursors.pyc
byte-compiling build/bdist.linux-x86_64/egg/MySQLdb/converters.py to converters.pyc
byte-compiling build/bdist.linux-x86_64/egg/MySQLdb/release.py to release.pyc
byte-compiling build/bdist.linux-x86_64/egg/MySQLdb/times.py to times.pyc
creating stub loader for _mysql.so
byte-compiling build/bdist.linux-x86_64/egg/_mysql.py to _mysql.pyc
creating build/bdist.linux-x86_64/egg/EGG-INFO
copying MySQL_python.egg-info/PKG-INFO -> build/bdist.linux-x86_64/egg/EGG-INFO
copying MySQL_python.egg-info/SOURCES.txt -> build/bdist.linux-x86_64/egg/EGG-INFO
copying MySQL_python.egg-info/dependency_links.txt -> build/bdist.linux-x86_64/egg/EGG-INFO
copying MySQL_python.egg-info/top_level.txt -> build/bdist.linux-x86_64/egg/EGG-INFO
writing build/bdist.linux-x86_64/egg/EGG-INFO/native_libs.txt
zip_safe flag not set; analyzing archive contents...
creating dist
creating 'dist/MySQL_python-1.2.3c1-py2.6-linux-x86_64.egg' and adding 'build/bdist.linux-x86_64/egg' to it
removing 'build/bdist.linux-x86_64/egg' (and everything under it)
Processing MySQL_python-1.2.3c1-py2.6-linux-x86_64.egg
Copying MySQL_python-1.2.3c1-py2.6-linux-x86_64.egg to /usr/local/lib/python2.6/dist-packages
Adding MySQL-python 1.2.3c1 to easy-install.pth file

Installed /usr/local/lib/python2.6/dist-packages/MySQL_python-1.2.3c1-py2.6-linux-x86_64.egg
Processing dependencies for MySQL-python==1.2.3c1
Finished processing dependencies for MySQL-python==1.2.3c1
```

Then I just purely changed directory to my home directory, ran python, and "import MySQLdb" works perfectly this way, plus my scripts don't complain, and the world is a better place!

:guitar:

---

### Post by schworak on 2010-03-06
> **trinaryouroboros said:**
> :KS **I'm writing this as a thank you to forum posters, and to hopefully clear the air for other users who want to use this module.** :KS


Well I am writing to offer you a HUGE THANK YOU!

Yours was the first place that I could find simple instructions for getting MySQLdb installed which was required for gMySQL plugin for gedit.

---------------

It is no wonder that Linux can't break into the main stream desktop OS market. Installing anything that isn't pre-packaged by the makers of your destro is a nightmare!

Install this... Oh wait, it doesn't work because you need that... Oh wait, that doesn't work because it needs the other... Oh wait, none of us area going to tell you upfront all the parts that are required, just keep trying till you figure them all out.

What takes 15 minutes under Windows can be an all day task under Linux just trying to figure all the parts needed.

If the install process could become more streamlined (unlikely any time soon) Linux would have a chance at being more than a "computer nerd" operating system or a dedicated use OS and break on to the general public desktop OS scene.

Sorry for the rant, but you can't honestly disagree.

---

### Post by douglegge on 2010-05-28
[LEFT]Thanks to mirrorball for the hint re apt-get install python-mysqldb which fixed my problem instantly (it's always the quirks with the apt-get names that get me ;-)
Whilst I appreciate this is a Linux/Ubuntu forum does anyone have any experience of exactly this same problem on a Windows platform?
&#12288;
I have Python, MySQL and mysqltools installed without a problem. Can I simply "unzip" the mysqldb download and place the resulting folder & files in a directory which I configure a PATH to? Or is it an install/build job?
I tried the .exe install at [http://www.thescotties.com/mysql-python/test/](http://www.thescotties.com/mysql-python/test/) which appeared to work for many people but I get the MSCVR90.dll issue despite having the tools installed!

Any tips?
 

Thanks
 

Doug[/LEFT]

---

### Post by trinaryouroboros on 2010-06-01
> **douglegge said:**
> [LEFT]Thanks to mirrorball for the hint re apt-get install python-mysqldb which fixed my problem instantly (it's always the quirks with the apt-get names that get me ;-)
Whilst I appreciate this is a Linux/Ubuntu forum does anyone have any experience of exactly this same problem on a Windows platform?
&#12288;
I have Python, MySQL and mysqltools installed without a problem. Can I simply "unzip" the mysqldb download and place the resulting folder & files in a directory which I configure a PATH to? Or is it an install/build job?
I tried the .exe install at [http://www.thescotties.com/mysql-python/test/](http://www.thescotties.com/mysql-python/test/) which appeared to work for many people but I get the MSCVR90.dll issue despite having the tools installed!

Any tips?
 

Thanks
 

Doug[/LEFT]

Not sure, have you tried asking the .exe builder at thescotties.com?

---

### Post by nugroho.redbuff on 2011-08-18
I have the same problem too. I can not run python-mysql instlalation script wrote in python. Seems the problem is located in libmysqlclient. I solve it by do this action
uninstall the installed libmysqlcleint16
sudo apt-get --purge remove libmysqlclient16

and.. install it again
sudo apt-get install libmysqlclient16

it works. Here is all of my way:
> 1. wget [http://nchc.dl.sourceforge.net/project/mysql-python/mysql-python/1.2.3/MySQL-python-1.2.3.tar.gz](http://nchc.dl.sourceforge.net/project/mysql-python/mysql-python/1.2.3/MySQL-python-1.2.3.tar.gz)

2. tar -zxf MySQL-python-1.2.3.tar.gz
3. cd MySQL-python-1.2.3
4. sudo apt-get install python-setuptools
5. sudo apt-get install python-dev
6. arahkah path python ke mysql export PATH=$PATH:/usr/local/mysql/bin
7. sudo apt-get install libmysqlclient16-dev < here is the main trouble
   7.a uninstall libmysqlclient16 sudo apt-get --purge remove libmysqlclient16
       but the phpmyadmin is broken, gambas too. :(
   7.b reinstall libmysqlclient16 sudp-apt get install libmysqlclient16
8. run installation script
   8.a sudo python setup.py build
   8.b sudo python setup.py install

and here is the test example
algopar@byonegopar:~$ python
Python 2.6.5 (r265:79063, Apr 16 2010, 13:09:56) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import MySQLdb
>>>

---

### Post by Ram_Krishna on 2011-12-02
This helped me to solve my problem..thanks a lot..

---

### Post by jfgencarnacao on 2012-05-08
Installing the mysqlclient15-dev package and then easy_install mysql-python fixed it for me. 

If you landed on this page because of a dist-upgrade breaking your enviroments try this:

```
sudo apt-get install mysqlclient15-dev
```

and then inside your enviroment (you can also do it outside, but someone better than me will have to explain how to make sure the enviroment will access it) do:

```
easy_install mysql-python
```

or 

```
pip install mysql-python
```

Hope it helps

---

