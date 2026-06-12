---
title: "HOWTO: Bibus Breezy packages"
date: 2006-01-28
forum: Outdated Tutorials &amp; Tips
---

### Post by NeTo on 2006-01-28
From the [Bibus homepage](http://bibus-biblio.sourceforge.net/):
*Bibus is a bibliographic database. As other such tools, Bibus allows to search, edit, sort you bibliographic records, etc. Bibus has however some features that makes its unique among opensource and even commercial bibliographic databases.*

I have built the Bibus debian packages for Ubuntu Breezy, as in Breezy the OOo2 location is different from the one in Debian or Dapper.

**Contents**
1. Installation
2. Package Compilation (Not Required)

**1. Installation**
First you need to install the packages Bibus depends on. Open a terminal window and type:```
sudo apt-get install python-wxgtk2.6 python-uno
```You need to install also a SQL engine.
[LIST]
[*]If you want to use SQLite:
You need to add the bibus repository for the required packages. Run:```
sudo gedit /etc/apt/sources.list
```And add the following line to the *sources.list* file:```
## Bibus
deb http://easynews.dl.sourceforge.net/sourceforge/bibus-biblio ./
deb-src http://easynews.dl.sourceforge.net/sourceforge/bibus-biblio ./
```To download and install the packages:```
sudo apt-get update
sudo apt-get install libsqliteodbc python-pysqlite2
```[*]Or if wou want use MySQL:```
sudo apt-get install libmyodbc mysql-server mysql-common mysql-client python-mysqldb
```[/LIST]

After the packages are installed, type the following to correctly configure python-uno (otherwise the python *pyuno* module may fail to load):```
sudo ldconfig -v /usr/lib/openoffice2/program
```The next step is to download the Bibus packages. Type:```
wget http://netosoft.no-ip.org/Ubuntu/breezy/bibus/bibus_1.2.0-2~neto1_all.deb
wget http://netosoft.no-ip.org/Ubuntu/breezy/bibus/bibus-doc-en_1.2.0-2~neto1_all.deb
```After downloading, you'll end up with 2 .deb files. To install them run:```
sudo dpkg -i bibus_1.2.0-2~neto1_all.deb bibus-doc-en_1.2.0-2~neto1_all.deb
```

Now you are ready to use bibus. Type *bibus* in a terminal window, or run it from *Applications->Office->Bibus bibliographic database*

**2. Package Compilation (Not Required)**
If you want to compile bibus from source, download the following:```
wget http://netosoft.no-ip.org/Ubuntu/breezy-sources/bibus/bibus_1.2.0-2~neto1.diff.gz
wget http://netosoft.no-ip.org/Ubuntu/breezy-sources/bibus/bibus_1.2.0-2~neto1.dsc
wget http://netosoft.no-ip.org/Ubuntu/breezy-sources/bibus/bibus_1.2.0.orig.tar.gz
```Then, run```
dpkg-source -x bibus_1.2.0-2~neto1.dsc
dpkg-buildpackage -uc -nc -rsudo
```After the build process is done, you will end up with two deb files, one containing bibus and the other its documentation.

---

### Post by GrumpyBob on 2006-02-03
Your download command doesn't work for me...

Robert

---

### Post by NeTo on 2006-02-03
[QUOTE=GrumpyBob]Your download command doesn't work for me...

Robert[/QUOTE]

My PC has been down for a few days because I'm doing a major hardware upgrade (which sadly hasn't turn out very well). The download will be down at least until tomorrow. Sorry for any inconvenients.

---

### Post by David Valentine on 2006-02-04
Thanks for this HowTo, NeTo.  Once your server is back up, I'm looking forward to seeing if I can migrate away from ProCite.  BTW, do you know of any good guides for transferring data from ProCite to Bibus?

---

### Post by GrumpyBob on 2006-02-04
[QUOTE=NeTo]My PC has been down for a few days because I'm doing a major hardware upgrade (which sadly hasn't turn out very well). The download will be down at least until tomorrow. Sorry for any inconvenients.[/QUOTE]


No problems - I look forward to installing the file!
And thanks in advance for making this available.

Robert

---

### Post by bgalan on 2006-02-06
yeah, thanks a lot for this howto and hosting the file, NeTo. i also look forward to using this program; i'm writing my dissertation in humanities and i'm learning to use lyx, latex, bibtex, and, hopefully, bibus soon. 
benjamin

---

### Post by malmjako on 2006-02-07
What a great initiative, NeTo! It's a shame, though, that we can't get access to the files. If you send them to me I can put them up on a server at my university, which is available 24/7. (malmjako at the server student.chalmers.se)

---

### Post by NeTo on 2006-02-07
Thank you all for your comments. I have sent you malmjako a mail with the files mentioned in the first post. I'll be still offline a few more days, so your offer has really came in handy. Thank you for your offering.

---

### Post by malmjako on 2006-02-07
The following are the files I got (md5sum ok):

[http://www.dd.chalmers.se/~malmjako/bibus/bibus_1.1.1-2~neto1_all.deb]("http://www.dd.chalmers.se/~malmjako/bibus/bibus_1.1.1-2~neto1_all.deb")
[http://www.dd.chalmers.se/~malmjako/bibus/bibus-doc-en_1.1.1-2~neto1_all.deb]("http://www.dd.chalmers.se/~malmjako/bibus/bibus-doc-en_1.1.1-2~neto1_all.deb")
[http://www.dd.chalmers.se/~malmjako/bibus/bibus_1.1.1-2~neto1_i386.changes]("http://www.dd.chalmers.se/~malmjako/bibus/bibus_1.1.1-2~neto1_i386.changes")

They install and seem to be working well. Thanks  NeTo!

---

### Post by NeTo on 2006-02-07
Wow! That was fast! I have updated the first post with your links. Thank you!

---

### Post by David Valentine on 2006-02-07
After installing according to the directions in NeTo's HowTo (including MySQL), I'm getting the following error when I try to start Bibus:
> Traceback (most recent call last):
  File "/usr/share/bibus/bibus.py", line 118, in ?
    Bibus = Bibus()
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7473, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7125, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "/usr/share/bibus/bibus.py", line 103, in OnInit
    dlg.Run()
  File "/usr/share/bibus/FirstStart.py", line 141, in Run
    import uno
  File "/usr/lib/python2.4/site-packages/uno.py", line 37, in ?
    import pyuno
SystemError: dynamic module not initialized properly
Any ideas about what this all means?

---

### Post by yarri on 2006-02-09
Same problem here :(

---

### Post by flibble on 2006-02-09
I have the same problem. I've been trying on and off for six months to get bibus to work in breezy. I hope someone can help us with this. Good bibliographic software is the last bastion of windows for me :)

---

### Post by NeTo on 2006-02-10
I have been Googling around, and found [this bug report](https://launchpad.net/distros/ubuntu/+source/openoffice.org2/+bug/24983). Looks similar, but I'm not sure.

Do you get the same error if you run the following?:```
python -c 'import uno'
```

---

### Post by yarri on 2006-02-10
This is output of your command:
Traceback (most recent call last):
  File "<string>", line 1, in ?
  File "/usr/lib/python2.4/site-packages/uno.py", line 37, in ?
    import pyuno
SystemError: dynamic module not initialized properly

I am too noobish to understand this.

---

### Post by NeTo on 2006-02-10
[QUOTE=yarri]This is output of your command:
Traceback (most recent call last):
  File "<string>", line 1, in ?
  File "/usr/lib/python2.4/site-packages/uno.py", line 37, in ?
    import pyuno
SystemError: dynamic module not initialized properly

I am too noobish to understand this.[/QUOTE]

As far as I understand, the problem might be related to OpenOffice and not to Bibus. You could follow the steps in [thread=80392]this HOWTO[/thread] to update OOo2 to 2.0.1 (The steps at *Installation from repositories* should suffice), which hopefully has issue sorted out.

---

### Post by flibble on 2006-02-10
Hi NeTo,

Thanks for your input. Yes, I get the same error when trying to load the uno module directly. I have upgraded to openoffice 2.01 but still get the same error. I also tried reinstalling libstdc++6 with no result.
Any idea how to get python to load the uno module?

Matthius Klose seems to think this bug was fixed for openoffice 1.9.121-1ubuntu6
[http://bugzilla.ubuntu.com/show_bug.cgi?id=10003]("http://bugzilla.ubuntu.com/show_bug.cgi?id=10003")

Perhaps by virtue of comment above in the same bug report: "the py uno
bridge can be compiled with ucs2 which will solve this problem."

How can I recompile the py uno bridge with ucs2?

Cheers, :f

---

### Post by David Valentine on 2006-02-10
According to the bibus [installation page]("http://bibus-biblio.sourceforge.net/html/en/LinuxInstall.html#mozTocId825115") accessible through the links flibble provided, it appears that the problem is tricky indeed, and involves uninstalling the py-uno bridge installed with openoffice and installing a different one with bibus.  I may attempt that later, but with some trepidation about potentially breaking my openoffice installation and with concern that no longer will synaptic be able to manage openoffice.

I'm glad to see others are interested in this problem--for the academic community (and others), the ability to manage and cite references is an absolute necessity.  If there's any way to encourage the bibus and/or openoffice developers to resolve the situation such that installing both is a straightforward affair, I'd like to help.  This is just the sort of ammunition we will need to help colleagues buy into the notion that linux *is* ready for the desktop!

---

### Post by manicka on 2006-02-11
From what I can see, this package for sqlite install

libsqliteodbc

Doesn't exist in the repos

---

### Post by manicka on 2006-02-11
[QUOTE=David Valentine]According to the bibus [installation page]("http://bibus-biblio.sourceforge.net/html/en/LinuxInstall.html#mozTocId825115") accessible through the links flibble provided, it appears that the problem is tricky indeed, and involves uninstalling the py-uno bridge installed with openoffice and installing a different one with bibus.  I may attempt that later, but with some trepidation about potentially breaking my openoffice installation and with concern that no longer will synaptic be able to manage openoffice.[/QUOTE]

I believe this solution is only for Ooo1.1.4. 

I to would like to get to the bottom of this one and get the package working. I've been looking for a scholar's aid /endnote replacement for some time.

---

### Post by NeTo on 2006-02-11
[QUOTE=manicka]From what I can see, this package for sqlite install

libsqliteodbc

Doesn't exist in the repos[/QUOTE]

Oops. Correct, the package must be downloaded from the bibus repository. I have edited the HOWTO to reflect this.

[quote=David Valentine]According to the bibus installation page accessible through the links flibble provided, it appears that the problem is tricky indeed, and involves uninstalling the py-uno bridge installed with openoffice and installing a different one with bibus. I may attempt that later, but with some trepidation about potentially breaking my openoffice installation and with concern that no longer will synaptic be able to manage openoffice.[/quote]
What I don't understand is why python-uno works on some Breezy installations and not in some others. 

If you add the bibus repositories, you will notice there is a  *openoffice-pyuno* package listed. I assume that's the replacement bridge mentioned. I haven't checked it out, but I guess it will need some minor modification to work with OOo2.

---

### Post by manicka on 2006-02-11
[QUOTE=NeTo]What I don't understand is why python-uno works on some Breezy installations and not in some others.[/QUOTE]

My guess is that if you already have a database created from a previous install of bibus then it will start ok, but not create new databses. Are you able to run the first run wizard in the help menu? 

[QUOTE=NeTo]
If you add the bibus repositories, you will notice there is a  *openoffice-pyuno* package listed. I assume that's the replacement bridge mentioned. I haven't checked it out, but I guess it will need some minor modification to work with OOo2.[/QUOTE]

That package is made for 1.1.4 and tries to remove Ooo2. 

It appears that the python-uno package is definitely the cause of the problem. If I uninstall the ubuntu version of 0oo2 and install the version from the main Ooo2 site using alien, bibus willl start I am able to setup an sqlite database. Unfortunately though it can't find the Ooo2 install in /opt and all the Ooo2 options are greyed out in the openoffic menu.

Next stop is to compile my own deb from source to see if I can get bibus to find the Ooo2 install correctly.

---

### Post by NeTo on 2006-02-11
[QUOTE=manicka]My guess is that if you already have a database created from a previous install of bibus then it will start ok, but not create new databses. Are you able to run the first run wizard in the help menu?[/quote]Yes, I am able to run it. Before posting the packages I made sure I could reproduce the whole bibus installation procedure, without any configuration files present. What I haven't done is test it in a fresh breezy install. Hopefully I will do so sometime during next week.

> Next stop is to compile my own deb from source to see if I can get bibus to find the Ooo2 install correctly.You don't need to compile the deb again if you want to change the OOo2 location. 
You only need to edit the */usr/share/bibus/bibus.cfg* file. The *oopath* variable tells bibus where to find the *program* subfolder of OOo2.

---

### Post by manicka on 2006-02-11
[QUOTE=NeTo]
You only need to edit the */usr/share/bibus/bibus.cfg* file. The *oopath* variable tells bibus where to find the *program* subfolder of OOo2.[/QUOTE]

hmm, no joy there, Changed the path to /opt/openoffice.org2.0/program. 

I still have all my openoffice menu options greyed out. 

At least the programs running I guess. The python-uno that comes with the installer at the Ooo2 site seems to solve the pyuno problem.

---

### Post by GrumpyBob on 2006-02-12
Is this connected with a need to edit Setup.xcu?
As I recall, I opened 
/usr/lib/openoffice2/share/registry/data/org/openoffice/Setup.xcu
And under
<node oor:name="Office">

I inserted: 

	<prop oor:name="ooSetupConnectionURL" oor:type="xs:string">
<value>pipe,name=OOo_pipe;urp;</value>
</prop>

Anyway, thanks to NeTo, I now have Bibus upgraded to 1.1.1, matching my WinXP box at work.  It was a very smooth upgrade to the already functional install of Bibus.

Robert

---

### Post by bgalan on 2006-02-13
hi everyone,
thanks again for your efforts in getting this package to work. i install it but it's not running (i also have the pyone problem described by yarri). i'm also looking forward to integrating bibus with ooo... it's one of the things that keeps me going back to windows... i wish i could help with this, but i'm too new with linux... thanks for your efforts :) 
benjamin

---

### Post by David Valentine on 2006-02-14
> I believe this solution is only for Ooo1.1.4. The section for Ooo 2.0 is [here]("http://bibus-biblio.sourceforge.net/html/en/introduction.html#mozTocId551738"), not that it helped at all.

---

### Post by manicka on 2006-02-15
Update...

When running the First Connection Wizard, I'm just not seeing this screen

[http://bibus-biblio.sourceforge.net/html/en/setup/setup_firststart.png](http://bibus-biblio.sourceforge.net/html/en/setup/setup_firststart.png)

I have the correct Ooo2 path configured in /usr/share/bibus/bibus.cfg

---

### Post by GrumpyBob on 2006-02-15
[QUOTE=manicka]From what I can see, this package for sqlite install

libsqliteodbc

Doesn't exist in the repos[/QUOTE]

I have just installed Bibus 1.1.1 on a newly set up Ubuntu 5.10 box, with the stock install of OO.o, using SQLite as the database.

I did not try and install the non-existent libsqliteodbc package.

I had to edit the Setup.xcu file to make comms work (I can post the edit tomorrow).

Everything worked fine, including OO.o integration.

Robert.
Feel free to PM me.

---

### Post by manicka on 2006-02-15
[QUOTE=GrumpyBob]
I had to edit the Setup.xcu file to make comms work (I can post the edit tomorrow).
[/QUOTE]

Is it the same edit you talked about in post #25 of this thread?

---

### Post by GrumpyBob on 2006-02-16
[QUOTE=manicka]Is it the same edit you talked about in post #25 of this thread?[/QUOTE]

Yes!, Sorry, I'm losing track of the Bibus threads I've contributed to!

At the moment I have three installs of Bibus 1.1.1:
on WinXP at work, works faultlessly, uses SQLite3
on Ubuntu Breezy laptop, works faultlessy, uses SQLite2 (annoyingly!)
on Ubuntu Desktop PC at work, uses SQLite3.  Unfortunately, it seems not to display publication year or volume number, and there are issues with editing and displaying references.  Can't fathom that one out.

Edited to clarify.

R

---

### Post by David Valentine on 2006-02-21
I'm still getting the following output after following the HowTo:> user@pc:~$ bibus
Traceback (most recent call last):
  File "/usr/share/bibus/bibus.py", line 118, in ?
    Bibus = Bibus()
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7473, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7125, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "/usr/share/bibus/bibus.py", line 103, in OnInit
    dlg.Run()
  File "/usr/share/bibus/FirstStart.py", line 141, in Run
    import uno
  File "/usr/lib/python2.4/site-packages/uno.py", line 37, in ?
    import pyuno
SystemError: dynamic module not initialized properly
Does this mean that Bibus will remain out of reach to us?

---

### Post by stryderjzw on 2006-02-26
Same problem here.  I'm not sure if that's the problems that the thread is talking about.

---

### Post by NeTo on 2006-02-26
[QUOTE=stryderjzw]Same problem here.  I'm not sure if that's the problems that the thread is talking about.[/QUOTE]

If you get something among the lines of:```
File "/usr/lib/python2.4/site-packages/uno.py", line 37, in ?
import pyuno
SystemError: dynamic module not initialized properly
```Then is the same problem that has all of us puzzled :confused:

---

### Post by malmjako on 2006-02-27
I downloaded bibus-1.1.1 source code from sourceforge (sf.net/projects/bibus-biblio) and got it working on **Dapper**. Bibus refused to accept my database until I had converted it to SQLite 3 format (sqlite OLD.db .dump | sqlite3 NEW.db). Two problems persist, however: 
1) I can't see identifiers that I've edited myself. 
2) I can't edit any existing entries, neither old nor newly created. The following is the bibus output when I try to edit an entry:
```
Traceback (most recent call last):
  File "/home/malmjako/Delat/tmp/src/bibus-1.1.1/BibFrame.py", line 777, in onMenuEditRef
    editor = RefEditor.RefEditor(ref[0],self.db,selectedkey,BIB.ALLOWED[id] & BIB.REF_EDIT_OK,self,-1,u'')
  File "/home/malmjako/Delat/tmp/src/bibus-1.1.1/RefEditor.py", line 47, in __init__
    self.__set_properties(ref)
  File "/home/malmjako/Delat/tmp/src/bibus-1.1.1/RefEditor.py", line 291, in __set_properties
    self.__set_fields_values(ref)
  File "/home/malmjako/Delat/tmp/src/bibus-1.1.1/RefEditor.py", line 303, in __set_fields_values
    for item in BIB.BIB_FIELDS[3:]: self.value[item].SetValue( ref[BIB.BIBLIOGRAPHIC_FIELDS[item]] )
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_controls.py", line 1761, in SetValue
    return _controls_.TextCtrl_SetValue(*args, **kwargs)
TypeError: String or Unicode type required
```

---

### Post by cudmore on 2006-03-02
I am having the same problem. I am also another newbie that feels a reference manager is one of my last ties to Windows OS. 

I followed the instructions from NeTo at (opting for mySQL):
[http://ubuntuforums.org/showthread.php?t=122841](http://ubuntuforums.org/showthread.php?t=122841)

To get this:
cudmore@ubuntu:~$ bibus
Traceback (most recent call last):
  File "/usr/share/bibus/bibus.py", line 118, in ?
    Bibus = Bibus()
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7473, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7125, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "/usr/share/bibus/bibus.py", line 103, in OnInit
    dlg.Run()
  File "/usr/share/bibus/FirstStart.py", line 141, in Run
    import uno
  File "/usr/lib/python2.4/site-packages/uno.py", line 37, in ?
    import pyuno
SystemError: dynamic module not initialized properly
cudmore@ubuntu:~$ python -c 'import uno'
Traceback (most recent call last):
  File "<string>", line 1, in ?
  File "/usr/lib/python2.4/site-packages/uno.py", line 37, in ?
    import pyuno
SystemError: dynamic module not initialized properly

A solution to this would be wonderful.

---

### Post by Eproxus on 2006-03-04
I would like to see a solution to this too, please!

Managed to get 'import uno' and 'import pyuno' work through adding /usr/lib/openoffice2/program to LD_LIBRARY_PATH and PYTHONPATH. Although running Bibus returns the same error anyway

```
Traceback (most recent call last):
  File "/usr/share/bibus/bibus.py", line 118, in ?
    Bibus = Bibus()
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7473, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7125, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "/usr/share/bibus/bibus.py", line 103, in OnInit
    dlg.Run()
  File "/usr/share/bibus/FirstStart.py", line 141, in Run
    import uno
  File "/usr/lib/python2.4/site-packages/uno.py", line 37, in ?
    import pyuno
SystemError: dynamic module not initialized properly
```

---

### Post by Eproxus on 2006-03-04
Managed to get it working by typing ```
python /usr/share/bibus/bibus.py
```

Strangely enough, this is (almost) exactly what is in the /usr/bin/bibus script... I'm confused...

---

### Post by manicka on 2006-03-06
[QUOTE=Eproxus]Managed to get it working by typing ```
python /usr/share/bibus/bibus.py
```

Strangely enough, this is (almost) exactly what is in the /usr/bin/bibus script... I'm confused...[/QUOTE]

Who cares, it works a treat...    Well done :)

---

### Post by NeTo on 2006-03-06
You're are genious Eproxus! Thank you :KS. I have tested it on a Dapper Flight 4 install and now Bibus works correctly!.

The reason why Bibus may not be running correctly for you, if run directly, is because LD_LIBRARY_PATH seems to be set for the current bash session only, and not for X sessions. There's a discussion on that topic [thread=2793]in this thread[/thread].

To fix the pyuno error I ran the following instead:```
sudo ldconfig -v /usr/lib/openoffice2/program
```

Can anyone else confirm ldconfig does the trick? If so, I'll quickly update the howto to include this important step.

---

### Post by malmjako on 2006-03-06
NeTo, do you have any of the problems I reported above, i.e. not seeing identifiers and not being able to edit posts, in Dapper?

---

### Post by David Valentine on 2006-03-06
> Can anyone else confirm ldconfig does the trick?Yes!  This did the trick for me--thanks!

---

### Post by NeTo on 2006-03-07
[QUOTE=malmjako]NeTo, do you have any of the problems I reported above, i.e. not seeing identifiers and not being able to edit posts, in Dapper?[/QUOTE]I actually didn't test modifying a database (silly me). I'll try that tomorrow. I quitted the Dapper Virtual Machine just before updating packages, as it seems the OOo2 packages changed names. So I assume the OOo2 path changed recently in Dapper (?).

[QUOTE=David Valentine]Yes! This did the trick for me--thanks![/quote]I have  edited the first post to include this step.

Now, considering this looks like an OOo2 bug, where do we inform the developers about it? Is the [Dapper bug section](https://launchpad.net/distros/ubuntu/dapper/+bugs) the best place?

---

### Post by David Valentine on 2006-03-07
> Now, considering this looks like an OOo2 bug, where do we inform the developers about it? Is the Dapper bug section the best place?It seems, first and foremost, like the OOo developers ought to know about this--or am I missing something?:-k

---

### Post by desiboston on 2006-03-08
It was working like charm but now I am getting this. I am a noob. I have no clue plz help

** (python:9188): WARNING **: IPP request failed with status 1030

** (python:9188): WARNING **: IPP request failed with status 1030

** (python:9188): WARNING **: IPP request failed with status 1030
Traceback (most recent call last):
  File "/usr/share/bibus/BibFrame.py", line 1235, in onMenuSearch
    search = Search.Search(self,self,-1,u'')
  File "/usr/share/bibus/Search.py", line 40, in __init__
    self.key_id,self.user,self.id = self.keytree.GetPyData(self.Selected)
TypeError: unpack non-sequence

** (python:9188): WARNING **: IPP request failed with status 1030
Traceback (most recent call last):
  File "/usr/share/bibus/BibFrame.py", line 1230, in onMenuPubMedSearch
    self.db.deleteOnline()
AttributeError: 'NoneType' object has no attribute 'deleteOnline'

** (python:9188): WARNING **: IPP request failed with status 1030

** (python:9188): WARNING **: IPP request failed with status 1030

---

### Post by NeTo on 2006-03-15
[QUOTE=David Valentine]It seems, first and foremost, like the OOo developers ought to know about this--or am I missing something?:-k[/QUOTE]

This seems to be fixed in the new Dapper development release, most probably because the OOo2 path has changed to /usr/lib/openoffice, as it was in Warty. 

[quote=desiboston]It was working like charm but now I am getting this. I am a noob. I have no clue plz help[/quote]

Have you tried with a different database? I'm sure, but maybe the database could be corrupted.

---

### Post by malmjako on 2006-03-17
I have not gotten converting from sqlite 2 to sqlite 3 databases to work. So
I've instead created a new database for Bibus in Dapper and imported all my references using the RIS format.

A new problem now is that references in my OpenOffice.org document which
were added with the old database do not seem to be recognized with the
new one. Thus, I get duplicates in the References list in the document.
And that's a bit of a pain, actually...

Maybe there is some better way to convert the database into sqlite 3
format?

---

### Post by chambs10 on 2006-03-17
Hi everyone.  I spent quite a while figuring this installation out, but I finally Bibus it to work seamlessly on 5.10 using SQLite! I think (hope) you will find this simple to implement. Because I spent such a significant amount of time working on this, I can't give you a simple step-by-step, but I will make some further suggestions that worked for me.

First try this:

1. Follow these Ubuntu [installation directions]("http://bibus-biblio.sourceforge.net/wiki/index.php/Installation#Debian_and_Ubuntu") on Bibus' webste.
2. Download and run this [sxd]("http://sourceforge.net/project/showfiles.php?group_id=87718&package_id=100069") to enable UNO connection (citer from this w[ebsite]("http://www.oooforum.org/forum/viewtopic.phtml?t=3754"))
3. Open Bibus and select Edit > Preference. You will see a list of tabs, select the "Word Processor" tab.  If you do not see it, use the arrows to scroll through the tabs. "Word Processor" is to the right of "Database".
4. When you have selected the tab, select use TCP/IP.

That should do it. Good Luck!

---

### Post by NeTo on 2006-03-18
[QUOTE=malmjako]
Maybe there is some better way to convert the database into sqlite 3
format?[/QUOTE]

Now I understand the problem you're having. I have not tested the following, but it may work (instructions adapted from [http://www.wpdev.org/wiki/index.php/Convert_sqlite2_to_sqlite3_format)](http://www.wpdev.org/wiki/index.php/Convert_sqlite2_to_sqlite3_format)).

Assuming you still have your sqlite2 database, download the command line tools for both sqlite2 and sqlite3:```
sudo apt-get install sqlite sqlite3
```
Once the packages are installed, run:```
sqlite *old-db* .dump | sqlite3 *new-db*
```

On a sidenote, I have built new packages for bibus-1.2.0. If things go well, I may not need to mirror these, as I'm now able to keep my PC on for a longer time (a situation that will further improve once I buy a pair of [silent cats](http://www.thermaltake.com/2005/dcfans/ComboCool/a1780silentCat8/SilentCat8.htm) :D). Thank you malmjako for hosting the old ones. I hope you can get that sqlite3 working soon.

---

### Post by malmjako on 2006-03-18
[QUOTE=NeTo]Assuming you still have your sqlite2 database, download the command line tools for both sqlite2 and sqlite3:```
sudo apt-get install sqlite sqlite3
```
Once the packages are installed, run:```
sqlite *old-db* .dump | sqlite3 *new-db*
```[/quote]
That is the exact command I issued to convert to sqlite3 and it seemed to get all the information into the new database (I used some SQLite editor to look at the database), but Bibus doesn't show Identifiers, and entries are not editable. 

[quote=NeTo]Thank you malmjako for hosting the old ones. I hope you can get that sqlite3 working soon.[/QUOTE]
You're quite welcome! I didn't realise they were still in use... They're still there, so tell me when I should remove them, to avoid the use of old debs! Thanks for your efforts to get Bibus working.

---

### Post by NeTo on 2006-03-21
[QUOTE=malmjako]You're quite welcome! I didn't realise they were still in use... They're still there, so tell me when I should remove them, to avoid the use of old debs! Thanks for your efforts to get Bibus working.[/QUOTE]

You can remove them if you wish. I'm (now) linking the files from my own pc, which will hopefully online 24/7. 

Btw, it seems that no-ip.com doesn't redirect addresses that look like *membername.no-ip.com* anymore for non-premium members. I didn't realized the issue until now, so the links were down all of this time.

I have now registered a different address, so I have updated the (now hopefully) working links in the first post. Sorry for any inconvenience.

Any feedback on the new bibus packages is welcomed.

---

### Post by shuttleworthwannabe on 2006-04-19
I just used automatix to upgrade OOo to 2.0.1 from 1.9.125 (breezy deafult version).

Here is what I did to mess this whole up;
I had version 1.9.XX of OOo when I did the following
1. I added the bibus sources to the sources.list
2. installed the bibus 1.2 using synaptic, all the dependencies were added automatically
3. But when I fired bibus it would not allow me to activate the OOo_pipe for listening mode

So I decided to upgrade the OOo to 2.0.1 using automatix, but still i have the same problem:
I have pasted the secreen shot to illustrate the errors.

How do I rectify this so that I can use Bibus in OOo 2.0.1?

Thanks in advance

---

### Post by NeTo on 2006-04-19
Have you tried opening the first connection wizard after the OOo 2.0.1 install? It is located in the help menu in Bibus. You can check there if OOo is listening to UNO connections.

---

### Post by shuttleworthwannabe on 2006-04-19
Yes, I have; but I got connection errors; but now a new problem, Bibus does not even start. here is atrace back when run from the terminal. Man am I glad you saw this thread. Thanks

```
$ bibus

** (python:10965): WARNING **: IPP request failed with status 1030
Traceback (most recent call last):
  File "/usr/bin/bibus", line 142, in ?
    bibframe1 = BibFrame.BibFrame(None, -1, BIB.TITLE)
  File "/usr/share/bibus/BibFrame.py", line 31, in __init__
    self.__loadConnectionModule()
  File "/usr/share/bibus/BibFrame.py", line 1480, in __loadConnectionModule
    import OOo
  File "/usr/share/bibus/OOo.py", line 54, in ?
    from bibOOo.bibOOoPlus import *
  File "/usr/share/bibus/bibOOo/bibOOoPlus.py", line 22, in ?
    from bibOOo.bibOOoBase import *
  File "/usr/share/bibus/bibOOo/bibOOoBase.py", line 24, in ?
    import uno
  File "/usr/lib/python2.4/site-packages/uno.py", line 37, in ?
    import pyuno
SystemError: dynamic module not initialized properly

```

---

### Post by NeTo on 2006-04-19
Uhm, try running the following: ```
sudo ldconfig -v /usr/lib/openoffice2/program
``` assuming openoffice installed to */usr/lib/openoffice2*. Hope you can get your problem sorted out soon.

---

### Post by shuttleworthwannabe on 2006-04-19
Thanks something seemed to have happened. At least now i Bibus opens but gets stuck at the "activate" screen when I run the First Connection wizard.
Here is the screenshot-1

UPDATE: I waited for a while, and it seems to be working fine now!!! Thnaks,

---

### Post by shuttleworthwannabe on 2006-04-19
```
$ bibus

** (python:11899): WARNING **: IPP request failed with status 1030

** (python:11899): WARNING **: IPP request failed with status 1030

```

The error persist, but it seems to be working fine? Why so?

---

### Post by NeTo on 2006-04-20
[QUOTE=shuttleworthwannabe]```
$ bibus

** (python:11899): WARNING **: IPP request failed with status 1030

** (python:11899): WARNING **: IPP request failed with status 1030

```

The error persist, but it seems to be working fine? Why so?[/QUOTE]

Dunno what's causing that. Googling only turned out in libgnomecups related errors :(

---

### Post by MagnusL on 2006-04-26
Hi!

Trying to install bibus on a Breezy Badger machine, running OO2. I get bibus installed by adding the sources to apt (taken from [http://bibus-biblio.sourceforge.net/bibus_doc/html/en/introduction.html](http://bibus-biblio.sourceforge.net/bibus_doc/html/en/introduction.html))

Bibus starts and I get the connection / start-wizard. But as I click on Activate to get connection to Openoffice simply nothing happens, no error msgs either. I tried the sudo ldconfig as posted here, still does not work. Any ideas on what to check??

Magnus L

---

### Post by NeTo on 2006-04-26
Have you tried with the Bibus package from the first post. OOo2 in Breezy is installed in a path different from what the debian Bibus packages look for. If you don't want to install the packages I built, you can try changing the [i]
/usr/share/bibus/bibus.cfg[/i] file settings. The line beggining with *oopath* shoud look like:```
oopath = /usr/lib/openoffice2/program
```

---

### Post by MagnusL on 2006-04-26
Thanks!! Hadn't realized that the packages were different. Used your and now it's up and running. Great!! :) 

Magnus

---

### Post by akniss on 2006-05-03
I've got bibus installed, running, and interfacing wonderfully with OOo.  Thanks NeTo!  

However, I've got a problem and was wondering if anyone else has seen it.  After i finalize my bibliography I get an additional OOo doc come up called private:stream.  This doc looks perfect, everything formatted correctly with my custom style and everything.  But I cannot save it...  This is a major problem, as my PhD dissertation is now full of yellow highlighted Bibus reference placeholders, and after finalizing, I cannot save the pretty output.  Any suggestions?  I have attached a screenshot of the error I get when trying to save the private:stream. 

I found one other person having a similar issue in Dapper, but some updated packages in the repos fixed his problem about a week ago (I think one package was pyuno).

---

### Post by malmjako on 2006-05-03
> I found one other person having a similar issue in Dapper, but some updated packages in the repos fixed his problem about a week ago (I think one package was pyuno). Yes, I had this issue running Dapper, and as you say, the problem is now gone for me. I think Bibus might have touched a sore spot in OpenOffice.org, because similar issues are had by other users on the OpenOffice.org forums ( [http://oooforum.org](http://oooforum.org) ). Unfortunately I don't have any new insight to help you. My original post on the Bibus forums on SourceForge can be found at [http://sourceforge.net/forum/forum.php?thread_id=1485749&forum_id=380178](http://sourceforge.net/forum/forum.php?thread_id=1485749&forum_id=380178)

---

### Post by akniss on 2006-05-29
To anyone who's got bibus working on dapper:

Can you define a custom style?  For some reason I could do this on Breezy but cannot since I upgraded to Dapper RC1.  Any help would be appreciated.

---

### Post by grw on 2006-06-12
Can I just ask a question about installing bibus? I am fairly new to linux.

I am running the latest Ubuntu version 6.06. I see that the instructions in teh the first post on how to install bibus (which are wonderful) are for Breezy. If I want to install bibus on Dapper, what do I have to do?

Any help much appreciated
Thanks

---

