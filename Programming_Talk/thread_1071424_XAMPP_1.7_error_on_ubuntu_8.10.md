---
title: "XAMPP 1.7 error on ubuntu 8.10"
date: 2009-02-16
forum: Programming Talk
---

### Post by deepbluegene on 2009-02-16
Hi i have just installed Xampp on Ubuntu and it is giving me following error.

Warning: file_get_contents(lang.tmp) [function.file-get-contents]: failed to open stream: Permission denied in /opt/lampp/htdocs/xampp/index.php on line 2

Warning: Cannot modify header information - headers already sent by (output started at /opt/lampp/htdocs/xampp/index.php:2) in /opt/lampp/htdocs/xampp/index.php on line 4


what  i am doing wrong?

Thanks

---

### Post by deepbluegene on 2009-02-16
[SOLVED] sorry to waste your time. there was an issue with permissions.

---

### Post by prawesh on 2009-03-04
hi

I ve the same problem after installing xampp 1.7. Can you give me the solution asap as I am new in using Ubuntu specifically Linux??? and this appears when i go to phpmyadmin

Existing configuration file (./config.inc.php) is not readable.

---

### Post by ubotlike on 2009-03-10
have problem with extract in /opt 

botlike@Home-7S7D7F4F:~$ sudo tar svfz xampp-linux*.tar.gz -c /opt
[sudo] password for botlike: 
xampp-linux-1.7.tar.gz
tar: Removing leading `/' from member names
/opt/
botlike@Home-7S7D7F4F:~$ sudo tar svfz xampp-linux*.tar.gz -c opt
xampp-linux-1.7.tar.gz
opt/
opt/grisoft/
opt/grisoft/lib/
opt/grisoft/lib/libstdc++.so.6
opt/grisoft/lib/libgcc_s.so.1
opt/grisoft/avg7/
opt/grisoft/avg7/etc/
opt/grisoft/avg7/etc/notify.eml
opt/grisoft/avg7/etc/antispam/
opt/grisoft/avg7/etc/antispam/sc15.bin.full.2007.03.30.04.02.30
opt/grisoft/avg7/etc/antispam/sc2.bin.full.2006.06.27.17.01.01
opt/grisoft/avg7/etc/antispam/sc12.bin.full.2007.03.30.09.04.53
opt/grisoft/avg7/etc/antispam/approvedsenders
opt/grisoft/avg7/etc/antispam/blockedsenders
opt/grisoft/avg7/etc/antispam/sc5.bin.full.2007.01.28.16.09.00
opt/grisoft/avg7/etc/antispam/sc1.bin.full.2007.03.30.01.21.21
opt/grisoft/avg7/etc/antispam/spamcatcher.conf
opt/grisoft/avg7/etc/antispam/sc11.bin.full.2007.03.30.08.40.01
opt/grisoft/avg7/etc/antispam/sc10.bin.full.2007.03.30.08.08.30
opt/grisoft/avg7/etc/antispam/sc6.bin.full.2007.02.13.01.23.26
opt/grisoft/avg7/etc/antispam/sc14.bin.full.2006.06.27.17.01.01
opt/grisoft/avg7/etc/antispam/sc9.bin.full.2007.03.27.22.11.36
opt/grisoft/avg7/etc/init.d/
opt/grisoft/avg7/etc/init.d/avgd.all
opt/grisoft/avg7/etc/init.d/avgdmilter.gentoo
opt/grisoft/avg7/etc/init.d/avgdinit.conf
opt/grisoft/avg7/etc/init.d/functions.ubuntu
opt/grisoft/avg7/etc/init.d/functions.rh
opt/grisoft/avg7/etc/init.d/functions.common
opt/grisoft/avg7/etc/init.d/functions.freebsd
opt/grisoft/avg7/etc/init.d/functions.deb
opt/grisoft/avg7/etc/init.d/functions.suse
opt/grisoft/avg7/etc/init.d/avgdmilter.all
opt/grisoft/avg7/etc/init.d/avgd.gentoo
opt/grisoft/avg7/etc/init.d/functions.slack
opt/grisoft/avg7/etc/init.d/avgdmilterinit.conf
opt/grisoft/avg7/etc/init.d/functions.mdk
opt/grisoft/avg7/etc/avg.conf
opt/grisoft/avg7/man/
opt/grisoft/avg7/man/man1/
opt/grisoft/avg7/man/man1/avgupdate.1.gz
opt/grisoft/avg7/man/man1/avgscan.1.gz
opt/grisoft/avg7/man/man1/avgqrtctl.1.gz
opt/grisoft/avg7/man/man1/avgdmilter.1.gz
opt/grisoft/avg7/man/man1/avgspmctl.1.gz
opt/grisoft/avg7/man/man5/
opt/grisoft/avg7/man/man5/avg.conf.5.gz
opt/grisoft/avg7/doc/
opt/grisoft/avg7/doc/README_cz.exim
opt/grisoft/avg7/doc/README_cz.qmailscanner
opt/grisoft/avg7/doc/README_cz.amavis
opt/grisoft/avg7/doc/README_cz.qmail
opt/grisoft/avg7/doc/ChangeLog
opt/grisoft/avg7/doc/README.qmailscanner
opt/grisoft/avg7/doc/license_cz.txt
opt/grisoft/avg7/doc/README_cz.sendmail
opt/grisoft/avg7/doc/README.postfix
opt/grisoft/avg7/doc/avg_esl_uma_en_75_8.pdf
opt/grisoft/avg7/doc/README_cz
opt/grisoft/avg7/doc/README
opt/grisoft/avg7/doc/README.amavis
opt/grisoft/avg7/doc/README_cz.postfix
opt/grisoft/avg7/doc/README.exim
opt/grisoft/avg7/doc/license_us.txt
opt/grisoft/avg7/doc/README.qmail
opt/grisoft/avg7/doc/README.sendmail
opt/grisoft/avg7/doc/lgpl.txt
opt/grisoft/avg7/doc/avg_esl_uma_cz_75_1.pdf
opt/grisoft/avg7/lib/
opt/grisoft/avg7/lib/libavgutil.so.1
opt/grisoft/avg7/lib/libspamcatcher.so
opt/grisoft/avg7/src/
opt/grisoft/avg7/src/dazuko/
opt/grisoft/avg7/src/dazuko/dazuko-2.3.3.tar.gz
opt/grisoft/avg7/src/qmail/
opt/grisoft/avg7/src/qmail/README
opt/grisoft/avg7/src/qmail/INSTALL
opt/grisoft/avg7/src/qmail/qmail-queue-avg.c
opt/grisoft/avg7/src/qmail/configure
opt/grisoft/avg7/bin/
opt/grisoft/avg7/bin/avgspmctl
opt/grisoft/avg7/bin/avgscan
opt/grisoft/avg7/bin/avgupdate
opt/grisoft/avg7/bin/avgdmilter
opt/grisoft/avg7/bin/avgqrtctl
opt/grisoft/avg7/var/
opt/grisoft/avg7/var/update/
opt/grisoft/avg7/var/update/preinstall/
opt/grisoft/avg7/var/update/log/
opt/grisoft/avg7/var/update/backup/
opt/grisoft/avg7/var/update/download/
opt/grisoft/avg7/var/run/
opt/grisoft/avg7/data/
opt/grisoft/avg7/data/incavi.avm
opt/grisoft/avg7/data/avg7.snu
opt/grisoft/avg7/data/avi7.avg
opt/grisoft/avg7/data/dfncfg.dat
opt/grisoft/avg7/data/avg7.lng
opt/grisoft/avg7/data/microavi.avg
opt/grisoft/avg7/data/set_vers.cfg
opt/grisoft/avg7/data/miniavi.avg
opt/grisoft/avggui/
opt/grisoft/avggui/glade/
opt/grisoft/avggui/glade/avgtest_button_blue.png
opt/grisoft/avggui/glade/avggui.glade
opt/grisoft/avggui/glade/avgname.png
opt/grisoft/avggui/glade/avgfreelogo.png
opt/grisoft/avggui/glade/avgico_big.png
opt/grisoft/avggui/glade/avggui.gladep
opt/grisoft/avggui/glade/avglogo.png
opt/grisoft/avggui/glade/avgupdateico.png
opt/grisoft/avggui/glade/avgtestres_button_blue.png
opt/grisoft/avggui/glade/avgupdate_button_blue.png
opt/grisoft/avggui/glade/avgresultsico.png
opt/grisoft/avggui/glade/avgico.png
opt/grisoft/avggui/glade/avginfo_ico.png
opt/grisoft/avggui/glade/avgmanagerico.png
opt/grisoft/avggui/prog/
opt/grisoft/avggui/prog/scanner.py
opt/grisoft/avggui/prog/rand.py
opt/grisoft/avggui/prog/sysdep.py
opt/grisoft/avggui/prog/misc_widgets.py
opt/grisoft/avggui/prog/main.py
opt/grisoft/avggui/prog/configview.py
opt/grisoft/avggui/prog/testresview.py
opt/grisoft/avggui/prog/update.py
opt/grisoft/avggui/prog/infoview.py
opt/grisoft/avggui/prog/messagebox.py
opt/grisoft/avggui/prog/updater.py
opt/grisoft/avggui/prog/PAMwrap.py
opt/grisoft/avggui/prog/fsh.py
opt/grisoft/avggui/prog/config.py
opt/grisoft/avggui/prog/mainview.py
opt/grisoft/avggui/prog/select.py
opt/grisoft/avggui/prog/sysinfo.py
opt/grisoft/avggui/prog/pixmaps/
opt/grisoft/avggui/prog/pixmaps/password.png
opt/grisoft/avggui/prog/pixmaps/avgscheduler.png
opt/grisoft/avggui/prog/pixmaps/avgtestmanager.png
opt/grisoft/avggui/prog/pixmaps/avgupdate.png
opt/grisoft/avggui/prog/pixmaps/keyring.png
opt/grisoft/avggui/prog/pixmaps/avglicense.png
opt/grisoft/avggui/prog/pixmaps/avgico_big.png
opt/grisoft/avggui/prog/pixmaps/avginfoico.png
opt/grisoft/avggui/prog/pixmaps/avglogo.png
opt/grisoft/avggui/prog/pixmaps/avgupdateico.png
opt/grisoft/avggui/prog/pixmaps/ok_result.png
opt/grisoft/avggui/prog/pixmaps/avgupdatepref.png
opt/grisoft/avggui/prog/pixmaps/avgresultsico.png
opt/grisoft/avggui/prog/pixmaps/avgico.png
opt/grisoft/avggui/prog/pixmaps/avginfo_ico.png
opt/grisoft/avggui/prog/pixmaps/avgmanagerico.png
opt/grisoft/avggui/prog/pixmaps/avgschedulerico.png
opt/grisoft/avggui/prog/pixmaps/nook_result.png
opt/grisoft/avggui/prog/logger.py
opt/grisoft/avggui/prog/testres.py
opt/grisoft/avggui/prog/test.py
opt/grisoft/avggui/prog/cronedit.py
opt/grisoft/avggui/prog/misc.py
opt/grisoft/avggui/doc/
opt/grisoft/avggui/doc/license_cz_utf8.txt
opt/grisoft/avggui/doc/README
opt/grisoft/avggui/config/
opt/grisoft/avggui/config/default.cfg
opt/grisoft/avggui/config/userinfo.cfg
opt/grisoft/avggui/config/avggui
opt/grisoft/avggui/bin/
opt/grisoft/avggui/bin/avggui_update_licinfo.sh
opt/grisoft/avggui/bin/ch_license.sh
opt/grisoft/avggui/bin/avggui
opt/grisoft/avggui/bin/pamwrap
opt/grisoft/avggui/locale/
opt/grisoft/avggui/locale/cs/
opt/grisoft/avggui/locale/cs/LC_MESSAGES/
opt/grisoft/avggui/locale/cs/LC_MESSAGES/avggui.mo

---

### Post by ubotlike on 2009-03-10
why why why ?????????????

botlike@Home-7S7D7F4F:~$ sudo tar svfz xampp-linux*.tar.gz -c opt/limpp
xampp-linux-1.7.tar.gz
tar: opt/limpp: Cannot stat: No such file or directory
tar: Error exit delayed from previous errors
botlike@Home-7S7D7F4F:~$ dir
&#1042;&#1080;&#1076;&#1077;&#1086;	     &#1052;&#1091;&#1079;&#1080;&#1082;&#1072;    &#1064;&#1072;&#1073;&#1083;&#1086;&#1085;&#1080;	 xampp-linux-1.5.3a.tar.gz
&#1044;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1080;    &#1055;&#1083;&#1086;&#1090;      Examples  xampp-linux-1.7.tar.gz
&#1048;&#1079;&#1086;&#1073;&#1088;&#1072;&#1078;&#1077;&#1085;&#1080;&#1103;  &#1055;&#1091;&#1073;&#1083;&#1080;&#1095;&#1085;&#1080;  opt
botlike@Home-7S7D7F4F:~$ cd opt
botlike@Home-7S7D7F4F:~/opt$ dir
grisoft
botlike@Home-7S7D7F4F:~/opt$ sudo mkdir asd
botlike@Home-7S7D7F4F:~/opt$ dir
asd  grisoft
botlike@Home-7S7D7F4F:~/opt$ sudo tar svfz xampp-linux*.tar.gz -c opt/asd
tar: opt/asd: Cannot stat: No such file or directory
tar: Error exit delayed from previous errors
botlike@Home-7S7D7F4F:~/opt$ cd
botlike@Home-7S7D7F4F:~$ sudo tar svfz xampp-linux*.tar.gz -c opt/asd
xampp-linux-1.7.tar.gz
opt/asd/
botlike@Home-7S7D7F4F:~$ sudo tar xvfz xampp-linux*.tar.gz -c opt/asd
tar: You may not specify more than one `-Acdtrux' option
Try `tar --help' or `tar --usage' for more information.

---

### Post by gjoellee on 2009-03-10
If you want to install LAMPP in Ubuntu, it is most easily done with this way:
```
sudo tasksel install lamp-server
```then run this command:

```
sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/mysite 
```then use this command:

```
gksudo gedit /etc/apache2/sites-available/mysite
```change " <Directory /var/www/>" to " <Directory /the/folder/you/would/like>"

add the same path as you decided to add above, after " DocumentRoot" as well.



now run this command: 
```
sudo a2dissite default && sudo a2ensite mysite
```and finally this command:

```
sudo /etc/init.d/apache2 restart
```and to make sure everything works correctly, go to this page: [http://localhost/](http://localhost/)

If it works it should say something like this: Hello, this is working!

Now start adding your files in the folder you changed /var/www to, and go to http://localhost/<your project's folder name>

---

