---
title: "howto install dbdesigner4"
date: 2006-02-05
forum: Programming Talk
---

### Post by dave84 on 2006-02-05
hi everybody bothering about how to install dbdesigner!

currently i'm running mysql 5.0 on my notebook and i got dbdesigner working after solving quite a lot of problems.
what helped me a lot were the explanations from 

[http://wiki.splitbrain.org/dbdesigner]("http://wiki.splitbrain.org/dbdesigner")

(you should do everything explained in the *"It needs a shared library from Kylix:"-section.*) and also do:

  download the libborqt-6.9.0-2.i386.rpm from [http://sourceforge.net/project/showfiles.php?group_id=64092&package_id=68416]("http://sourceforge.net/project/showfiles.php?group_id=64092&package_id=68416")
  ```
alien libborqt-6.9.0-2.i386.rpm
  dpkg -i libborqt_6.9.0-3_i386.deb 
``` 
  

when you cannot go along after struggling through these instructions try this:

1. edit the last line of the startdbd script to:
  ```
$app_path/DBDesigner4 $* #2> ~/.DBDesigner4/DBD4.log
```
  now try to start again and take care of the failure message:

  when you get s.th. like 
  
*" symbol lookup error: blablabla/Linuxlib/libqt.so.2: undefined symbol: XftPatternGetString"*

  make a symbolic link with these command (from the dir where you extracted the tarball):

  ```
cd DBDesigner4/Linuxlib
```
  ```
sudo rm libqt.so.2
```
  ```
ln -s /usr/lib/usr/lib/kylix3/libborqt-6.9.0-qt2.3.so ./
```

2. now you should be able to start dbdesigner4
  (maybe there is a missing symlink; try around a little bit)

3. when you try to connect to the mysql-database and you get an error that tells you something about "cannot load libmysqlclient.so" then again:

  ```
sudo rm libmysqlclient.so
```
  ```
ln -s /usr/lib/usr/lib/libmysqlclient.so.14.0.0 libmysqlclient.so
```

4. restart the dbdesigner4 and try to connect again. when an error message pops up and tells you about wrong username and password then enable the use of old passwords with your mysql-administrator and set up a new password with:

  ```
set password for 'mysql'@'localhost' = old_password('mysql');
```
  ```
flush privileges;
```

5. try it again, now it should work!\\:D/ 
  
please correct this post, if I have messed s.th up and apologize my bad english

---

### Post by drippy on 2006-08-05
Dave: thanks a lot for this post, I finally got DBDesigner working after reading through your steps and doing some debugging along the way.  :D

---

### Post by sitedesign on 2006-08-09
I have just tried these instruction and some others I found on the web but I get DBDesigner running, only I can't connect to the MySQL database.

The error is:
Unable to load libsqlmy.so

Any ideas.

Running Dapper.

---

### Post by steparianwolf on 2006-08-11
Hi:

I wrote a small guide to install and keep working DBDesigner in Ubuntu, in fact I'm using Ubuntu Dapper and DBDesigner without problems.. take a look at this: [http://www.ubuntuforums.org/showthre...ght=dbdesigner](http://www.ubuntuforums.org/showthre...ght=dbdesigner)

I hope it works for you

---

### Post by devnulljp on 2006-10-17
> **steparianwolf said:**
> Hi:

I wrote a small guide to install and keep working DBDesigner in Ubuntu, in fact I'm using Ubuntu Dapper and DBDesigner without problems.. take a look at this: [http://www.ubuntuforums.org/showthre...ght=dbdesigner](http://www.ubuntuforums.org/showthre...ght=dbdesigner)

I hope it works for you

Link's dead - any ideas?

---

### Post by talz13 on 2006-10-17
When I tried installing the kylix libs, it complains that xlibs is not installed.  I found xlibs-dev in synaptic and installed that, but still the problem remains.

---

### Post by dragomirov on 2006-10-18
open a console and get/install xlibs

wget [http://www.chorse.org/junkroom/xlibs-dummy/xlibs_6.8.2-77_all.deb](http://www.chorse.org/junkroom/xlibs-dummy/xlibs_6.8.2-77_all.deb)

sudo dpkg -i xlibs_6.8.2-77_all.deb

---

### Post by Marco Modesto on 2006-11-09
The Link for libborqt-6.9.0-2.i386.rpm is broken:
[http://sourceforge.net/project/showfiles.php?group_id=64092&package_id=68416](http://sourceforge.net/project/showfiles.php?group_id=64092&package_id=68416)


I found this package in RPM Find: [http://www.rpmfind.net/](http://www.rpmfind.net/)

Working link:
[ftp://fr2.rpmfind.net/linux/sourceforge/s/sk/skychart/libborqt-6.9.0-2.i386.rpm](ftp://fr2.rpmfind.net/linux/sourceforge/s/sk/skychart/libborqt-6.9.0-2.i386.rpm)


[]s

Marco Modesto.

---

### Post by 21croissants on 2006-12-26
In fact, I'd like to recommand strongly to use wine and the Windows installer. It will save you a lot of time with the configuration and the user interface will be nicer :p

I have put some details on my blog:
[http://21croissants.blogspot.com/2006/12/dbdesigner-4-on-ubuntu-dbdesigner-4-on.html](http://21croissants.blogspot.com/2006/12/dbdesigner-4-on-ubuntu-dbdesigner-4-on.html)

---

### Post by eracerbit on 2007-06-11
Here's a condensed cut-n-paste version =) works great under Ubuntu 7.04 "Feisty" 

```
sudo -s
```
*enter your password*

```

### setting up ###
mkdir ~/dbdesigner-install
cd ~/dbdesigner-install

### downloading rpm packages ###
wget http://213.115.162.124/external/DBDesigner4/DBDesigner4-0.5.4-0.i586.rpm
wget ftp://fr2.rpmfind.net/linux/sourceforge/s/sk/skychart/libborqt-6.9.0-1.i386.rpm
wget ftp://ftp.pbone.net/mirror/ftp.turbolinux.com/pub/TurboLinux/stable/tested/Workstation/7/i586/MySQL-shared-3.23.58-8.i586.rpm

### installing alien ###
apt-get install alien

### converting rpm packages to deb packages ###
alien *.rpm

### installing deb packages ###
dpkg -i *.deb

### creating links to libraries and executable ###
cd /usr/lib
ln -s DBDesigner4/libsqlmy.so
cd /usr/bin
ln -s /opt/DBDesigner4/DBDesigner4 dbdesigner

### exiting root and starting dbdesigner ###
exit
dbdesigner & sleep 5 && killall dbdesigner

### editing user config ###
cd ~/.DBDesigner4
sed s/libmysqlclient.so$/libmysqlclient.so.10/ DBConn_DefaultSettings.ini > temp
cp temp DBConn_DefaultSettings.ini && rm temp

### all done, running dbdesigner ###
dbdesigner

```

Here's whats going on: We download  the dbdesigner rpm, the borland qt rpm, and the mysqlclient 10 rpm, use alien to convert them to deb packages, and install the deb packages. Then, we make some symlinks and run dbdesigner to let it set up some config files, kill it, and then edit the config files. Fun!
:popcorn:

---

### Post by steparianwolf on 2007-06-11
Hi:

You're right, DBDesigner doesn't work with libmysqlclient.so.15, instead install libmysqlclient.so.10, and make the symlink, I'm using Ubuntu Fiesty too, and DBDesigner works fine.

---

### Post by eracerbit on 2007-06-11
> **steparianwolf said:**
> Hi:

You're right, DBDesigner doesn't work with libmysqlclient.so.15, instead install libmysqlclient.so.10, and make the symlink, I'm using Ubuntu Fiesty too, and DBDesigner works fine.

Thanks, steparianwolf - libmysqlclient.so.10 at least gets me connected to the database. Now it crashes when trying to reverse engineer a database. 

[edit]
everything's working great now! check my comment at the bottom of page 1 - [http://ubuntuforums.org/showthread.php?t=125911#postcount2821196](http://ubuntuforums.org/showthread.php?t=125911#postcount2821196) =)
[/edit]

---

### Post by pundip on 2007-07-21
I have tried these instructions but I get the following error when trying to connect to a database
Unable to load libsqlmy.so
Any ideas.  I am running 7.04

---

### Post by nxt on 2007-08-08
> **eracerbit said:**
> Here's a condensed cut-n-paste version =) works great under Ubuntu 7.04 "Feisty" 

```
sudo -s
```
*enter your password*

```

### setting up ###
mkdir ~/dbdesigner-install
cd ~/dbdesigner-install

### downloading rpm packages ###
wget http://213.115.162.124/external/DBDesigner4/DBDesigner4-0.5.4-0.i586.rpm
wget ftp://fr2.rpmfind.net/linux/sourceforge/s/sk/skychart/libborqt-6.9.0-1.i386.rpm
wget ftp://ftp.pbone.net/mirror/ftp.turbolinux.com/pub/TurboLinux/stable/tested/Workstation/7/i586/MySQL-shared-3.23.58-8.i586.rpm

### installing alien ###
apt-get install alien

### converting rpm packages to deb packages ###
alien *.rpm

### installing deb packages ###
dpkg -i *.deb

### creating links to libraries and executable ###
cd /usr/lib
ln -s DBDesigner4/libsqlmy.so
cd /usr/bin
ln -s /opt/DBDesigner4/DBDesigner4 dbdesigner

### exiting root and starting dbdesigner ###
exit
dbdesigner & sleep 5 && killall dbdesigner

### editing user config ###
cd ~/.DBDesigner4
sed s/libmysqlclient.so$/libmysqlclient.so.10/ DBConn_DefaultSettings.ini > temp
cp temp DBConn_DefaultSettings.ini && rm temp

### all done, running dbdesigner ###
dbdesigner

```

Here's whats going on: We download  the dbdesigner rpm, the borland qt rpm, and the mysqlclient 10 rpm, use alien to convert them to deb packages, and install the deb packages. Then, we make some symlinks and run dbdesigner to let it set up some config files, kill it, and then edit the config files. Fun!
:popcorn:

perfect.... dbdesigner working.

only the mysql shared library had 404 error - no file found.
so i just ftp searched
[http://www.filewatcher.com/m/MySQL-shared-3.23.58-8.i586.rpm.186857.0.0.html](http://www.filewatcher.com/m/MySQL-shared-3.23.58-8.i586.rpm.186857.0.0.html)

thanx!!

---

### Post by Rollockybill on 2007-08-11
A sincere newbie thanks for the cut'n'paste solution. It works as advertised. However, I can only run it as root, as it hangs on the splash screen for other users. Any ideas? Thanks.
Rollockybill.

---

### Post by nlbs on 2007-08-30
I am getting this Error ```
libborqt-6.9-qt2.3.so: cannot open shared object file: No such file or directory

```and here is all files and folders under /opt/DBDesigner4 directory```
drwxr-xr-x 3 root root    4096 2007-08-20 20:08 Data
-rwxr-xr-x 1 root root 3826008 2003-10-31 09:09 DBDesigner4
-rwxr-xr-x 1 root root 1508936 2003-10-31 09:09 DBDplugin_DataImporter
-rwxr-xr-x 1 root root 1857972 2003-10-31 09:09 DBDplugin_HTMLReport
-rwxr-xr-x 1 root root 2163060 2003-10-31 09:09 DBDplugin_SimpleWebFront
drwxr-xr-x 4 root root    4096 2007-08-20 20:08 Doc
drwxr-xr-x 2 root root    4096 2007-08-20 20:08 Examples
drwxr-xr-x 6 root root    4096 2007-08-20 20:08 Gfx
lrwxrwxrwx 1 root root      39 2007-08-30 17:55 libborqt-6.9.0-qt2.3.so -> /usr/lib/kylix3/libborqt-6.9.0-qt2.3.so
lrwxrwxrwx 1 root root      37 2007-08-30 17:56 libborqt-6.9-qt2.3.so -> /usr/lib/kylix3/libborqt-6.9-qt2.3.so

```

---

### Post by wolph on 2007-11-06
> **pundip said:**
> I have tried these instructions but I get the following error when trying to connect to a database
Unable to load libsqlmy.so
Any ideas.  I am running 7.04
I also had to edit ~/.DBDesigner4/DBConn.ini and changed libmysqlclient.so to libmysqlclient.so.10 .

---

### Post by itmanvn on 2007-11-07
For people who use Ubuntu 7.10

1. Download DBDesigner from [here]("http://fabforce.net/downloadfile.php?iddownloadfile=2")
2. Type:
```
sudo -s
```
then enter you password
3. Extract the tar archive by executing **tar xvzf DBDesigner4.0.5.4.tar.gz** from the command line. Change to the created directory: **cd DBDesigner4**
4. Type:
```

wget ftp://fr2.rpmfind.net/linux/sourceforge/s/sk/skychart/libborqt-6.9.0-2.i386.rpm
sudo apt-get install alien
alien libborqt-6.9.0-2.i386.rpm
dpkg -i libborqt_6.9.0-3_i386.deb

```
5. Edit the last line of the startdbd script to:
```
$app_path/DBDesigner4 $* #2> ~/.DBDesigner4/DBD4.log
```
6. Type:
```

cd Linuxlib
rm libqt.so.2
ln -s /usr/lib/libborqt-6.9-qt2.3.so ./libqt.so.2
cd ..
./startdbd

```

All done!:popcorn:

---

### Post by Netom on 2007-12-04
Hi, I tried the solutions posted here but they don't work with Amd64 plataform. ¿Any ideas?

---

### Post by mircea.postolache on 2008-01-09
I also had to install libxft-dev.

---

### Post by DarkDragon on 2008-01-22
> **Netom said:**
> Hi, I tried the solutions posted here but they don't work with Amd64 plataform. ¿Any ideas?

Well better late then never... ( Usually I don't visit too much these forums :S )... on my Debian lenny 64bit, I use DB Designer Fork from: [http://sourceforge.net/projects/dbdesigner-fork](http://sourceforge.net/projects/dbdesigner-fork)

I downloaded the linux binaries un compress them on my home folder:

```
$ tar xfvz /home/david/software/DBDesignerFork-1.4-bin-i386-linux.tar.gz 
```

then inside their bin directory, you can find a script named "startdbd_usingAMD64"

```

$ cd bin
$ ./startdbd_usingAMD64

```

I hope it works, It needs linux32 and ia32-libs packages to be installed ;)

---

### Post by FreeJersey2007 on 2008-02-29
I feel like I'm close, but I keep running into the following error:
libqt.so.2: cannot open shared object file: No such file or directory

I can see in the instructions within the post that refer to the removal of this file, but it seems when I execute that step, the file's not there to begin with.  I'm on 7.10.  Any thoughts?

---

### Post by Diabolis on 2008-03-17
For some reason I could not download dbdesigner from its site.

[http://fabforce.net/dbdesigner4/downloads.php](http://fabforce.net/dbdesigner4/downloads.php)

Download would get stuck at 0.8mb every time, but I found this links from where you can download it.

Tar:
[http://209.85.173.104/search?q=cache:cWjyrYqPB5AJ:download.seduc.ce.gov.br/ftp/+DBDesigner4.0.5.4.tar.gz+download+here&hl=en&ct=clnk&cd=9](http://209.85.173.104/search?q=cache:cWjyrYqPB5AJ:download.seduc.ce.gov.br/ftp/+DBDesigner4.0.5.4.tar.gz+download+here&hl=en&ct=clnk&cd=9)

Exe:
[http://209.85.173.104/search?q=cache:diAtyg-WAjAJ:linux.pucp.edu.pe/downloads/win_progs/+DBDesigner4.0.5.6_Setup.exe+download&hl=en&ct=clnk&cd=9](http://209.85.173.104/search?q=cache:diAtyg-WAjAJ:linux.pucp.edu.pe/downloads/win_progs/+DBDesigner4.0.5.6_Setup.exe+download&hl=en&ct=clnk&cd=9)

---

### Post by Diabolis on 2008-03-17
I made an executable script with the commands that **eracerbit**  posted. It worked great. I added this line at the end of the script so It deletes the .rpm and .deb files that are needed during the installation.
```
sudo rm -r dbdesigner-install/
```

Unfortunately I can't use dbdesigner because the gui is totally messed up, see the screenshot. Have anyone had this problem before?
*look at the panels on the right*

---

### Post by bruno.vitorino on 2008-04-05
> **Diabolis said:**
> I made an executable script with the commands that **eracerbit**  posted. It worked great. I added this line at the end of the script so It deletes the .rpm and .deb files that are needed during the installation.
```
sudo rm -r dbdesigner-install/
```

Unfortunately I can't use dbdesigner because the gui is totally messed up, see the screenshot. Have anyone had this problem before?
*look at the panels on the right*

Yes, i have that problem to, the gui is terrible :s

---

### Post by roberto.ur on 2008-04-07
> **bruno.vitorino said:**
> Yes, i have that problem to, the gui is terrible :s

The same problem here... and if I try to open a file, the "open file window" goes behind the main gui...

Maybe changing the font style could help but i don't have and idea of how to do that.

---

### Post by roberto.ur on 2008-04-07
> **roberto.ur said:**
> The same problem here... and if I try to open a file, the "open file window" goes behind the main gui...

Maybe changing the font style could help but i don't have and idea of how to do that.

Meanwhile, I decided to use wine. I know this is no a solution but I really need it.

---

### Post by phaidros on 2008-08-20
> **roberto.ur said:**
> The same problem here... and if I try to open a file, the "open file window" goes behind the main gui...

Maybe changing the font style could help but i don't have and idea of how to do that.

Getting stolen focus (hidden windows) in DBDesigner4 (dbdesigner) is ez:

1 - sudo apt-get install devilspie
2 - echo ‘(if(contains (application_name) "DBDesigner") (focus))’ > $HOME/.devilspie/dbdesigner.ds 
(replace DBDesigner in this line with the actual binary you are running for the programm, I just symlinked and the actual started symlink is called 'dbdesigner', so taken this in the line above)
3 - devilspie

(found here inthe comments: [http://21croissants.blogspot.com/2006/12/dbdesigner-4-on-ubuntu-dbdesigner-4-on.html](http://21croissants.blogspot.com/2006/12/dbdesigner-4-on-ubuntu-dbdesigner-4-on.html), works like a charm)

---

### Post by mranzorbey on 2009-06-21
Thanx to everyone and especially to [**eracerbit**]("http://ubuntuforums.org/member.php?u=253085"), everything works just fine! You saved me a lot of precious time!

---

### Post by jezjones on 2009-07-30
I know this is an old-ish thread but thought i would add my experience;-

The 'cutnpaste' howto on page one was fine except some of the rpms are no longer on RPM find.

SO, did the wine way on 9.10 (32bit) and works very well, sometimes get dialog boxes popping under but once you know they are under you can find them.

---

### Post by aspiredfang on 2009-11-04
*sends out kudos to DarkDragon*  I'm using a 64-bit version of Ubuntu 9.04 and the solution you listed, worked a complete treat; thank you most kindly!

---

### Post by foodfightr on 2009-11-23
I keep getting "Permission denied" for some reason.

I have the execute rights on all the files i extracted but it keeps saying "linux32: ./DBDesignerFork: Permission denied"

Even when i do "sudo ./DBDesignerFork" is says Permission denied.

Any ideas?



edit: Nevermind i installed MySQL Workbench. [http://dev.mysql.com/downloads/workbench/5.1.html](http://dev.mysql.com/downloads/workbench/5.1.html)

---

