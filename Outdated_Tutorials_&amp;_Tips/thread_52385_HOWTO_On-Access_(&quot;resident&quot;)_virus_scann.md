---
title: "HOWTO: On-Access (&quot;resident&quot;) virus scanning with clamav + dazuko"
date: 2005-07-27
forum: Outdated Tutorials &amp; Tips
---

### Post by drigloi on 2005-07-27
I managed to bring alive ClamAV's On-Access virus scanning feature (so it detects virus infected files at once when they are accessed/opened) here's how:

NOTE: viruses don't really threat Linux boxes. Virus scanners are actually scan for W32 and MSOffice viruses - this can be handy if you multi boot Ubuntu with a Win or don't want to infect your friends. The HOWTO may seem a bit complicated at first - but it really is not :) well a bit... But I bet you'll enjoy it if you accomplish it!

1. install clamav and clamav-daemon with apt
```
sudo apt-get install clamav clamav-daemon
``` 

2. install dazuko. NOTE: Ubuntu/Debian package is quite old, use the latest one from dazuko.org like this:
```
wget http://www.dazuko.org/files/dazuko-source_2.0.6-1_all.deb
sudo dpkg -i dazuko-source_2.0.6-1_all.deb
``` 

3. configuration of Dazuko is much easier with module-assistant this way:
```
sudo apt-get install module-assistant
m-a a-i dazuko
``` 

4. After you have the Dazuko kernel module you can't modprobe it yet - because kernel module capability conflicts with it. Solution is that you load dazuko PRIOR capability (this way both will work). You can achieve it this way:
```
sudo gedit /etc/modules
``` 
and write in dazuko in this file (I've written it before ide-cd but I don't think it matters).

5. Reboot the computer! You can test if dazuko loaded properly by issuing the "lsmod | grep dazuko" command.

6. Now the problem part: Ubuntu's official clamav package was made without clamuko support unfortunately (clamuko is clamav's interface to interact with dazuko - tricky, eh?). No problem the effort will worth the result - believe me. We will rebuild Ubuntu's clamav to our needs:
```
sudo apt-get install fakeroot build-essential
sudo apt-get build-dep clamav
sudo apt-get source clamav
``` 

7. These commands will setup the required build environment and source files for the package rebuild. You should have a clamav-0.83/ subdir by now so
```
cd clamav-0.83/
gedit debian/rules
``` 

and replace
```
./configure --host=$(DEB_HOST_GNU_TYPE) --build=$(DEB_BUILD_GNU_TYPE) --prefix=/usr --mandir=\$${prefix}/share/man --infodir=\$${prefix}/share/info --disable-clamav --with-dbdir=/var/lib/clamav/ --sysconfdir=/etc/clamav --enable-milter --with-tcpwrappers --disable-clamuko --with-gnu-ld --with-libcurl --with-dns
``` 

with
```
./configure --host=$(DEB_HOST_GNU_TYPE) --build=$(DEB_BUILD_GNU_TYPE) --prefix=/usr --mandir=\$${prefix}/share/man --infodir=\$${prefix}/share/info --disable-clamav --with-dbdir=/var/lib/clamav/ --sysconfdir=/etc/clamav --enable-milter --with-tcpwrappers --with-gnu-ld --with-libcurl --with-dns
``` 

(don't let these scare you: the only difference between them is that we removed "--disable-clamuko" from the ./configure line)

8. Now rebuild the clamav packages with this command:
```
dpkg-buildpackage -rfakeroot -uc -us
``` 

9. You'll find the new packages up one level in the dir hierarchy so do a 
```
cd ..
sudo dpkg -i *.deb
``` 

10. So we've the clamuko enabled packages installed now. Last step is to configure clamav-daemon by editing /etc/clamav/clamd.conf:
```
sudo gedit /etc/clamav/clamd.conf
``` 

Insert the following:
```
ClamukoScanOnAccess
ClamukoScanOnOpen
ClamukoScanArchive
ClamukoIncludePath /home
``` 

Also replace "User clamav" with "User root" to let things work (* will need a fix for this - give your ideas plz *)

11. Restart clamav-daemon to make changes take effect:
```
sudo invoke-rc.d clamav-daemon restart
``` 

12. You'd like to see how it's working? 

You can grab the "eicar" test virus (no malicious code, just for testing) from here:
[http://www.eicar.org/anti_virus_test_file.htm](http://www.eicar.org/anti_virus_test_file.htm)

You can also try it with real-life (!) viruses from here:
[http://vx.netlux.org/vl.php](http://vx.netlux.org/vl.php)

You won't be able to open virus infected files/archives - clamav+dazuko immediately bans access to them (deletion is possible though). Also "tail /var/log/clamav/clamav.log" tells you about the virus. Try man clamd.conf for more options. I suggest to look after the "VirusEvent" option. The possibilities from here are limitless.

NOTE: Ubuntu's official clamav package and the dazuko-source (I bet it is not in main/restricted:) package are outdated. Backport has a more current clamav package but unfortunately both repos has the "clamuko" feature disabled and that's why on-access scanning doesn't work out-of-the-box. I hope this will change with time. I hope you liked my howto and clamav/dazuko. Clamav is btw an excellent virus scanner and is updated multiple times a day.

---

### Post by drigloi on 2005-07-28
I've developed a simple script (called **ClamDazer**) for handling virus events. You can see a screenshot here:

[IMG]http://xpedition.mine.nu/clamdazer/clamdazer.jpg[/IMG] 

You can easily set it up this way:

1.
```
sudo gedit /opt/clamdazer
``` 

2. copy and paste to /opt/clamdazer:
```
#!/bin/sh
#Clamdazer script by Gabor Igloi (2005) GPL

v=`tail -n 1 /var/log/clamav/clamav.log`
v=${v#*: }
v=${v%:*}

f=${v##*/}

zenity --title ClamDazer --warning --text '"'"$f"$'" CONTAINS A VIRUS!\n[ '"$1"$' ]\nWould you like to delete it?'

if [ $? -eq 0 ]; then
	rm $v
	zenity --title ClamDazer --info --text '"'"$f"$'"\nRemoved successfully!'
fi
``` 

3. making it executable
```
sudo chmod a+x /opt/clamdazer
``` 

4. finally add VirusEvent option to /etc/clamav/clamd.conf
```
sudo gedit /etc/clamav/clamd.conf
``` 

Add this line to the end of clamd.conf:
```
VirusEvent /opt/clamdazer %v &
``` 

5. Don't forget to restart clamav-daemon by "sudo invoke-rc.d clamav-daemon restart"

Now you'll get a warning dialog everytime you click on an infected file/archive and you can delete it easily.

---

### Post by sal on 2005-10-15
[QUOTE=drigloi]I managed to bring alive ClamAV's On-Access virus scanning feature (so it detects virus infected files at once when they are accessed/opened) here's how:

NOTE: viruses don't really threat Linux boxes. Virus scanners are actually scan for W32 and MSOffice viruses - this can be handy if you multi boot Ubuntu with a Win or don't want to infect your friends. The HOWTO may seem a bit complicated at first - but it really is not :) well a bit... But I bet you'll enjoy it if you accomplish it!

1. install clamav and clamav-daemon with apt
```
sudo apt-get install clamav clamav-daemon
``` 

2. install dazuko. NOTE: Ubuntu/Debian package is quite old, use the latest one from dazuko.org like this:
```
wget http://www.dazuko.org/files/dazuko-source_2.0.6-1_all.deb
sudo dpkg -i dazuko-source_2.0.6-1_all.deb
``` 

3. configuration of Dazuko is much easier with module-assistant this way:
```
sudo apt-get install module-assistant
m-a a-i dazuko
``` 

4. After you have the Dazuko kernel module you can't modprobe it yet - because kernel module capability conflicts with it. Solution is that you load dazuko PRIOR capability (this way both will work). You can achieve it this way:
```
sudo gedit /etc/modules
``` 
and write in dazuko in this file (I've written it before ide-cd but I don't think it matters).

5. Reboot the computer! You can test if dazuko loaded properly by issuing the "lsmod | grep dazuko" command.

6. Now the problem part: Ubuntu's official clamav package was made without clamuko support unfortunately (clamuko is clamav's interface to interact with dazuko - tricky, eh?). No problem the effort will worth the result - believe me. We will rebuild Ubuntu's clamav to our needs:
```
sudo apt-get install fakeroot build-essential
sudo apt-get build-dep clamav
sudo apt-get source clamav
``` 

7. These commands will setup the required build environment and source files for the package rebuild. You should have a clamav-0.83/ subdir by now so
```
cd clamav-0.83/
gedit debian/rules
``` 

and replace
```
./configure --host=$(DEB_HOST_GNU_TYPE) --build=$(DEB_BUILD_GNU_TYPE) --prefix=/usr --mandir=\$${prefix}/share/man --infodir=\$${prefix}/share/info --disable-clamav --with-dbdir=/var/lib/clamav/ --sysconfdir=/etc/clamav --enable-milter --with-tcpwrappers --disable-clamuko --with-gnu-ld --with-libcurl --with-dns
``` 

with
```
./configure --host=$(DEB_HOST_GNU_TYPE) --build=$(DEB_BUILD_GNU_TYPE) --prefix=/usr --mandir=\$${prefix}/share/man --infodir=\$${prefix}/share/info --disable-clamav --with-dbdir=/var/lib/clamav/ --sysconfdir=/etc/clamav --enable-milter --with-tcpwrappers --with-gnu-ld --with-libcurl --with-dns
``` 

(don't let these scare you: the only difference between them is that we removed "--disable-clamuko" from the ./configure line)

8. Now rebuild the clamav packages with this command:
```
dpkg-buildpackage -rfakeroot -uc -us
``` 

9. You'll find the new packages up one level in the dir hierarchy so do a 
```
cd ..
sudo dpkg -i *.deb
``` 

10. So we've the clamuko enabled packages installed now. Last step is to configure clamav-daemon by editing /etc/clamav/clamd.conf:
```
sudo gedit /etc/clamav/clamd.conf
``` 

Insert the following:
```
ClamukoScanOnAccess
ClamukoScanOnOpen
ClamukoScanArchive
ClamukoIncludePath /home
``` 

Also replace "User clamav" with "User root" to let things work (* will need a fix for this - give your ideas plz *)

11. Restart clamav-daemon to make changes take effect:
```
sudo invoke-rc.d clamav-daemon restart
``` 

12. You'd like to see how it's working? 

You can grab the "eicar" test virus (no malicious code, just for testing) from here:
[http://www.eicar.org/anti_virus_test_file.htm](http://www.eicar.org/anti_virus_test_file.htm)

You can also try it with real-life (!) viruses from here:
[http://vx.netlux.org/vl.php](http://vx.netlux.org/vl.php)

You won't be able to open virus infected files/archives - clamav+dazuko immediately bans access to them (deletion is possible though). Also "tail /var/log/clamav/clamav.log" tells you about the virus. Try man clamd.conf for more options. I suggest to look after the "VirusEvent" option. The possibilities from here are limitless.

NOTE: Ubuntu's official clamav package and the dazuko-source (I bet it is not in main/restricted:) package are outdated. Backport has a more current clamav package but unfortunately both repos has the "clamuko" feature disabled and that's why on-access scanning doesn't work out-of-the-box. I hope this will change with time. I hope you liked my howto and clamav/dazuko. Clamav is btw an excellent virus scanner and is updated multiple times a day.[/QUOTE]


after using this method would i have to do it again every time ubuntu releses a new kernel or a kernel update? and will this work with the clamav front end gui i think its called klamAV [http://www.kde-apps.org/content/show.php?content=12388](http://www.kde-apps.org/content/show.php?content=12388)

thanks.

---

### Post by sal on 2005-10-28
[QUOTE=drigloi]I've developed a simple script (called **ClamDazer**) for handling virus events. You can see a screenshot here:

[IMG]http://xpedition.mine.nu/clamdazer/clamdazer.jpg[/IMG] 

You can easily set it up this way:

1.
```
sudo gedit /opt/clamdazer
``` 

2. copy and paste to /opt/clamdazer:
```
#!/bin/sh
#Clamdazer script by Gabor Igloi (2005) GPL

v=`tail -n 1 /var/log/clamav/clamav.log`
v=${v#*: }
v=${v%:*}

f=${v##*/}

zenity --title ClamDazer --warning --text '"'"$f"$'" CONTAINS A VIRUS!\n[ '"$1"$' ]\nWould you like to delete it?'

if [ $? -eq 0 ]; then
	rm $v
	zenity --title ClamDazer --info --text '"'"$f"$'"\nRemoved successfully!'
fi
``` 

3. making it executable
```
sudo chmod a+x /opt/clamdazer
``` 

4. finally add VirusEvent option to /etc/clamav/clamd.conf
```
sudo gedit /etc/clamav/clamd.conf
``` 

Add this line to the end of clamd.conf:
```
VirusEvent /opt/clamdazer %v &
``` 

5. Don't forget to restart clamav-daemon by "sudo invoke-rc.d clamav-daemon restart"

Now you'll get a warning dialog everytime you click on an infected file/archive and you can delete it easily.[/QUOTE]

should this go in /etc/opt or /var/opt?

---

### Post by drigloi on 2005-10-30
I placed it under /opt.

---

### Post by fourchannel on 2005-12-09
my clamav will detect the eicar virus. but when i'm in console and open it, it does nothing to stop me. no warning, and i set up the clamdazer script.

my clamd.conf
```
#Automatically Generated by clamav-base postinst
#To reconfigure clamd run #dpkg-reconfigure clamav-base
#Please read /usr/share/doc/clamav-base/README.Debian.gz for details

#-------from the insta-scan manual
ClamukoScanOnAccess
ClamukoScanOnOpen
ClamukoScanArchive
ClamukoIncludePath /home



LocalSocket /var/run/clamav/clamd.ctl
FixStaleSocket
User root
ScanMail
ScanArchive
ArchiveMaxRecursion 5
ArchiveMaxFiles 1000
ArchiveMaxFileSize 10M
ArchiveMaxCompressionRatio 250
ReadTimeout 180
MaxThreads 12
MaxConnectionQueueLength 15
LogFile /var/log/clamav/clamav.log
LogTime
LogFileMaxSize 0
PidFile /var/run/clamav/clamd.pid
DatabaseDirectory /var/lib/clamav
SelfCheck 3600
VirusEvent /opt/clamdazer %v &
``` 
and clamdazer, with root:root 755 own, perm 

```
#!/bin/sh
#Clamdazer script by Gabor Igloi (2005) GPL

v=`tail -n 1 /var/log/clamav/clamav.log`
v=${v#*: }
v=${v%:*}

f=${v##*/}

zenity --title ClamDazer --warning --text '"'"$f"$'" CONTAINS A VIRUS!\n[ '"$1"$' ]\nWould you like to delete it?'

if [ $? -eq 0 ]; then
    rm $v
    zenity --title ClamDazer --info --text '"'"$f"$'"\nRemoved successfully!'
fi
```

---

### Post by ZoltanPatay on 2006-01-06
Dazuko module can be loaded properly also using modules.d and then you wont need reboot, since "modprobe dazuko" will work. See it here: [http://www.ubuntuforums.org/showpost.php?p=634418&postcount=13](http://www.ubuntuforums.org/showpost.php?p=634418&postcount=13)

---

### Post by ameerirshad on 2006-01-18
[quote=drigloi]
7. These commands will setup the required build environment and source files for the package rebuild. You should have a clamav-0.83/ subdir by now so
```
cd clamav-0.83/
gedit debian/rules
``` 

and replace
```
./configure --host=$(DEB_HOST_GNU_TYPE) --build=$(DEB_BUILD_GNU_TYPE) --prefix=/usr --mandir=\$${prefix}/share/man --infodir=\$${prefix}/share/info --disable-clamav --with-dbdir=/var/lib/clamav/ --sysconfdir=/etc/clamav --enable-milter --with-tcpwrappers --disable-clamuko --with-gnu-ld --with-libcurl --with-dns
``` 

with
```
./configure --host=$(DEB_HOST_GNU_TYPE) --build=$(DEB_BUILD_GNU_TYPE) --prefix=/usr --mandir=\$${prefix}/share/man --infodir=\$${prefix}/share/info --disable-clamav --with-dbdir=/var/lib/clamav/ --sysconfdir=/etc/clamav --enable-milter --with-tcpwrappers --with-gnu-ld --with-libcurl --with-dns
``` 

(don't let these scare you: the only difference between them is that we removed "--disable-clamuko" from the ./configure line)[/quote]

Ok untill point 7 everything went rite! But I can't find 
cd clamav-0.83/
gedit debian/rulesAnd as such everything further down the line I can't perform I guess!

---

### Post by Video Toaster on 2006-03-18
Wow, great how-to!  This was exactly what I was looking for!

However, I ran into a slight problem - when I try to download the source for clamav, apt tells me that a source package cannot be found.  (Dapper Drake, ClamAV 0.84).  Any ideas?

EDIT:  Never mind... I uncommented Universe in my source list and the source package was found.  Oops.  :D

---

### Post by Yun_Pilgrim on 2006-04-06
I have followed the instructions until after I installed the module assistant, i ran
> m-a a-i dazuko
and got the following error in the log (after it stopped on about 2%):
>  dh_clean
 &#9474; /usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules     &#9618;
 &#9474; make[1]: Entering directory `/usr/src/modules/dazuko'                      &#9618;
 &#9474; dh_clean                                                                   &#9618;
 &#9474; make[1]: dh_clean: Command not found                                       &#9618;
 &#9474; make[1]: *** [kdist_clean] Error 127                                       &#9618;
 &#9474; make[1]: Leaving directory `/usr/src/modules/dazuko'                       &#9618;
 &#9474; make: *** [kdist_build] Error 2

Im a newbie running Ubuntu 5.10.
Could it be the kernel source or headers or something?
Please help.

Thanks.

---

### Post by Yun_Pilgrim on 2006-04-06
> The first time you run module-assistant, you have to run the prepare. Using the module-assistant prepare command will download the kernel headers, matching your installed kernel version, and other files necessary to insert modules into the kernel. Issue the following command in the Terminal window:

sudo module-assistant prepare

...from [ here ]("http://allyourtech.com/content/articles/15_01_2006_installing_antivir_with_on_access_scanning_in_ubuntu_linux.php")
This solved my problem.
:-D 8)

---

### Post by stell86 on 2006-12-15
> cd clamav-0.83/
gedit debian/rules
I've tried with both 0.88.2 (from 'normal' repositories) and 0.88.4 (from backports), but I can't find 'debian' or 'rules'
I new to compiling, so much of this was a walk in dark park for me - i'll bring the flashlght next time...

retief

---

### Post by Hormat Grak on 2007-07-19
Excuse me, can anyone here tell me how to change dazuko file permission to a+rwx automatically on boot. Thanks

---

### Post by yel on 2007-08-24
[QUOTE="Hormat Grak"]how to change dazuko file permission to a+rwx automatically on boot[/QUOTE]

[QUOTE="drigloi"]Also replace "User clamav" with "User root" to let things work (* will need a fix for this - give your ideas plz *)[/QUOTE]


You can add the chmod command to the file /etc/modprobe.d/dazuko :

```
sudo gedit /etc/modprobe.d/dazuko 

```
And copy and paste the following code:

```
install dazuko modprobe -r capability;\
modprobe -i dazuko; \
chmod a+rwx /dev/dazuko; \
modprobe -i capability
```

But I think that to give some right for all users can raise problems of securities.

To by-pass it, I prefer to create a group, ie dazuko, which I add as secondary group to the user clamav. As it clamuko has access to dazuko without giving the right for all users.

You have to replace the chmod line in /etc/modprobe.d/dazuko by:

```
chgrp dazuko /dev/dazuko; \
```

---

### Post by salman01 on 2008-01-04
i have the same problem...

---

### Post by vitorio on 2008-01-09
I'm having similar problem in Gutsy.  Dazuko is installed (from latest source), module is loaded, device is created.

Clamav is installed from Gutsy repository and seems to be working.  The only problem I've noticed that clamDscan does not have access to /home unless I change "User clamav" to "User root" in clamd.conf.  But then I can use clamscan and freshclam only as root.

But the major problem clamd.conf reports:"Clamuko is not available".  Even if "User root" is set in clamd.conf.

Since this howto was created in year 2006 and based on the fact that Ubuntu Clamav package at that time was built with --desable-clamuko option, my question is whether this is still applicable to Gutsy Clamav package?

Shoud I rebuild my installation or things changed and I'm having a different problem here?

Thank you.

---

### Post by ambiman2 on 2008-09-10
Hi guys,

i've patched my current kernel (rel. 2.6.26) with dazuko. Removed sec compatibilities and SELinux support. Device /dev/dazuko exists (full rights for everyone :-) ). I've compilied clamav 0.94 (without --disable-clamuko) but i'm still unable to scan my files realtime cause:
In the logfile i can see "ERROR: Unable to start Clamuko."

Sorry, but i've no further debugging information.

Any ideas?

Kind regards,

Daniel

---

### Post by stuffystuff200681 on 2009-08-04
can't compile it :( this is what i get

> user@user-laptop:~/clamav-0.95.1+dfsg$ dpkg-buildpackage -rfakeroot -uc -us  
dpkg-buildpackage: set CFLAGS to default value: -g -O2                       
dpkg-buildpackage: set CPPFLAGS to default value:                            
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions    
dpkg-buildpackage: set FFLAGS to default value: -g -O2                       
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2                     
dpkg-buildpackage: source package clamav                                     
dpkg-buildpackage: source version 0.95.1+dfsg-1ubuntu1.2                     
dpkg-buildpackage: source changed by Imre Gergely <gimre@narancs.net>        
dpkg-buildpackage: host architecture i386                                    
dpkg-checkbuilddeps: warning: can't parse dependency ooobasis31-en_us        
dpkg-checkbuilddeps: warning: can't parse dependency ooobasis31-en_us-res    
dpkg-checkbuilddeps: warning: can't parse dependency ooobasis31-en_us-base   
dpkg-checkbuilddeps: warning: can't parse dependency ooobasis31-en_us-binfilter
dpkg-checkbuilddeps: warning: can't parse dependency ooobasis31-en_us-math     
dpkg-checkbuilddeps: warning: can't parse dependency ooobasis31-en_us-draw     
dpkg-checkbuilddeps: warning: can't parse dependency ooobasis31-en_us-impress  
dpkg-checkbuilddeps: warning: can't parse dependency ooobasis31-en_us-calc     
dpkg-checkbuilddeps: warning: can't parse dependency ooobasis31-en_us-writer   
dpkg-checkbuilddeps: warning: can't parse dependency ooobasis31-en_us-help     
 fakeroot debian/rules clean                                                   
debconf-updatepo                                                               
dh_testdir                                                                     
dh_testroot                                                                    
/usr/bin/make distclean                                                        
make[1]: Entering directory `/home/user/clamav-0.95.1+dfsg'                    
Making distclean in clamdtop                                                   
make[2]: Entering directory `/home/user/clamav-0.95.1+dfsg/clamdtop'           
 rm -f clamdtop clamdtop                                                       
rm -rf .libs _libs                                                             
rm -f *.o                                                                      
rm -f *.lo                                                                     
rm -f *.tab.c                                                                  
test -z "" || rm -f                                                            
rm -f TAGS ID GTAGS GRTAGS GSYMS GPATH tags                                    
rm -rf ./.deps                                                                 
rm: cannot remove `./.deps/misc.Po': Permission denied                         
rm: cannot remove `./.deps/optparser.Po': Permission denied                    
rm: cannot remove `./.deps/getopt.Po': Permission denied                       
rm: cannot remove `./.deps/clamdtop.Po': Permission denied                     
make[2]: [distclean] Error 1 (ignored)                                         
rm -f Makefile                                                                 
make[2]: Leaving directory `/home/user/clamav-0.95.1+dfsg/clamdtop'            
Making distclean in unit_tests                                                 
make[2]: Entering directory `/home/user/clamav-0.95.1+dfsg/unit_tests'         
 rm -f check_clamav check_clamav                                               
 rm -f check_clamd check_clamd                                                 
test -z "lcov.out *.gcno *.gcda *.log clam-phish-exe test-stderr.log clamscan.log valgrind-*.log duma.log duma2.log clamscan2.log" || rm -f lcov.out *.gcno *.gcda *.log clam-phish-exe test-stderr.log clamscan.log valgrind-*.log duma.log duma2.log clamscan2.log                                                                                  
rm -rf .libs _libs                                                                                                
rm -f *.o                                                                                                         
rm -f *.lo                                                                                                        
rm -f *.tab.c                                                                                                     
test -z "" || rm -f                                                                                               
rm -f TAGS ID GTAGS GRTAGS GSYMS GPATH tags                                                                       
rm -rf ./.deps                                                                                                    
rm: cannot remove `./.deps/check_clamav-check_matchers.Po': Permission denied                                     
rm: cannot remove `./.deps/check_clamd-check_clamav_skip.Po': Permission denied                                   
rm: cannot remove `./.deps/check_clamav-check_regex.Po': Permission denied                                        
rm: cannot remove `./.deps/check_clamav-check_uniq.Po': Permission denied                                         
rm: cannot remove `./.deps/check_clamav-check_htmlnorm.Po': Permission denied                                     
rm: cannot remove `./.deps/check_clamav-check_str.Po': Permission denied                                          
rm: cannot remove `./.deps/check_clamav-check_clamav_skip.Po': Permission denied                                  
rm: cannot remove `./.deps/check_clamav-check_jsnorm.Po': Permission denied                                       
rm: cannot remove `./.deps/check_clamd-check_clamd.Po': Permission denied                                         
rm: cannot remove `./.deps/check_clamav-check_clamav.Po': Permission denied                                       
rm: cannot remove `./.deps/check_clamav-check_disasm.Po': Permission denied                                       
make[2]: [distclean] Error 1 (ignored)                                                                            
rm -f Makefile                                                                                                    
make[2]: Leaving directory `/home/user/clamav-0.95.1+dfsg/unit_tests'                                             
Making distclean in test                                                                                          
make[2]: Entering directory `/home/user/clamav-0.95.1+dfsg/test'                                                  
rm -rf .libs _libs                                                                                                
rm -f clam-v2.rar clam-v3.rar clam.cab clam.exe.bz2 clam.exe clam.zip clam.arj clam.exe.rtf clam.exe.szdd clam.tar.gz clam.chm clam.sis clam-aspack.exe clam-pespin.exe clam-upx.exe clam-fsg.exe clam-mew.exe clam-nsis.exe clam-petite.exe clam-upack.exe clam-wwpack.exe clam.pdf clam.mail clam.ppt clam.tnef clam.ea05.exe clam.ea06.exe clam.d64.zip clam.exe.mbox.base64 clam.exe.mbox.uu clam.exe.binhex clam.ole.doc clam.impl.zip clam.exe.html clam.bz2.zip  
rm -f *.lo                                                                                                        
test -z "" || rm -f                                                                                               
rm -f Makefile                                                                                                    
make[2]: Leaving directory `/home/user/clamav-0.95.1+dfsg/test'                                                   
Making distclean in clamav-milter                                                                                 
make[2]: Entering directory `/home/user/clamav-0.95.1+dfsg/clamav-milter'                                         
test -z "*.gcda *.gcno" || rm -f *.gcda *.gcno                                                                    
rm -rf .libs _libs                                                                                                
 rm -f clamav-milter clamav-milter                                                                                
rm -f *.o                                                                                                         
rm -f *.lo                                                                                                        
rm -f *.tab.c                                                                                                     
test -z "" || rm -f                                                                                               
rm -f TAGS ID GTAGS GRTAGS GSYMS GPATH tags                                                                       
rm -rf ./.deps                                                                                                    
rm: cannot remove `./.deps/clamfi.Po': Permission denied                                                          
rm: cannot remove `./.deps/connpool.Po': Permission denied                                                        
rm: cannot remove `./.deps/misc.Po': Permission denied                                                            
rm: cannot remove `./.deps/optparser.Po': Permission denied                                                       
rm: cannot remove `./.deps/whitelist.Po': Permission denied                                                       
rm: cannot remove `./.deps/output.Po': Permission denied                                                          
rm: cannot remove `./.deps/getopt.Po': Permission denied                                                          
rm: cannot remove `./.deps/netcode.Po': Permission denied                                                         
rm: cannot remove `./.deps/clamav-milter.Po': Permission denied                                                   
make[2]: [distclean] Error 1 (ignored)                                                                            
rm -f Makefile                                                                                                    
make[2]: Leaving directory `/home/user/clamav-0.95.1+dfsg/clamav-milter'                                          
Making distclean in etc                                                                                           
make[2]: Entering directory `/home/user/clamav-0.95.1+dfsg/etc'                                                   
rm -rf .libs _libs                                                                                                
rm -f *.lo                                                                                                        
test -z "" || rm -f                                                                                               
rm -f Makefile                                                                                                    
make[2]: Leaving directory `/home/user/clamav-0.95.1+dfsg/etc'                                                    
Making distclean in docs                                                                                          
make[2]: Entering directory `/home/user/clamav-0.95.1+dfsg/docs'                                                  
rm -rf .libs _libs                                                                                                
rm -f *.lo                                                                                                        
test -z "" || rm -f                                                                                               
rm -f Makefile                                                                                                    
make[2]: Leaving directory `/home/user/clamav-0.95.1+dfsg/docs'                                                   
Making distclean in database                                                                                      
make[2]: Entering directory `/home/user/clamav-0.95.1+dfsg/database'                                              
rm -rf .libs _libs                                                                                                
rm -f *.lo                                                                                                        
test -z "" || rm -f                                                                                               
rm -f Makefile                                                                                                    
make[2]: Leaving directory `/home/user/clamav-0.95.1+dfsg/database'                                               
Making distclean in clamconf                                                                                      
make[2]: Entering directory `/home/user/clamav-0.95.1+dfsg/clamconf'                                              
 rm -f clamconf clamconf                                                                                          
test -z "*.gcda *.gcno" || rm -f *.gcda *.gcno                                                                    
rm -rf .libs _libs                                                                                                
rm -f *.o                                                                                                         
rm -f *.lo                                                                                                        
rm -f *.tab.c                                                                                                     
test -z "" || rm -f                                                                                               
rm -f TAGS ID GTAGS GRTAGS GSYMS GPATH tags                                                                       
rm -rf ./.deps                                                                                                    
rm: cannot remove `./.deps/misc.Po': Permission denied                                                            
rm: cannot remove `./.deps/optparser.Po': Permission denied                                                       
rm: cannot remove `./.deps/getopt.Po': Permission denied                                                          
rm: cannot remove `./.deps/clamconf.Po': Permission denied                                                        
make[2]: [distclean] Error 1 (ignored)                                                                            
rm -f Makefile                                                                                                    
make[2]: Leaving directory `/home/user/clamav-0.95.1+dfsg/clamconf'                                               
Making distclean in sigtool                                                                                       
make[2]: Entering directory `/home/user/clamav-0.95.1+dfsg/sigtool'                                               
 rm -f sigtool sigtool                                                                                            
test -z "*.gcda *.gcno" || rm -f *.gcda *.gcno                                                                    
rm -rf .libs _libs                                                                                                
rm -f *.o                                                                                                         
rm -f *.lo                                                                                                        
rm -f *.tab.c                                                                                                     
test -z "" || rm -f                                                                                               
rm -f TAGS ID GTAGS GRTAGS GSYMS GPATH tags                                                                       
rm -rf ./.deps                                                                                                    
rm: cannot remove `./.deps/tar.Po': Permission denied                                                             
rm: cannot remove `./.deps/cdiff.Po': Permission denied                                                           
rm: cannot remove `./.deps/misc.Po': Permission denied                                                            
rm: cannot remove `./.deps/sigtool.Po': Permission denied                                                         
rm: cannot remove `./.deps/vba.Po': Permission denied                                                             
rm: cannot remove `./.deps/optparser.Po': Permission denied                                                       
rm: cannot remove `./.deps/output.Po': Permission denied                                                          
rm: cannot remove `./.deps/getopt.Po': Permission denied                                                          
make[2]: [distclean] Error 1 (ignored)                                                                            
rm -f Makefile                                                                                                    
make[2]: Leaving directory `/home/user/clamav-0.95.1+dfsg/sigtool'                                                
Making distclean in freshclam                                                                                     
make[2]: Entering directory `/home/user/clamav-0.95.1+dfsg/freshclam'                                             
 rm -f freshclam freshclam                                                                                        
test -z "*.gcda *.gcno" || rm -f *.gcda *.gcno                                                                    
rm -rf .libs _libs                                                                                                
rm -f *.o                                                                                                         
rm -f *.lo                                                                                                        
rm -f *.tab.c                                                                                                     
test -z "" || rm -f                                                                                               
rm -f TAGS ID GTAGS GRTAGS GSYMS GPATH tags                                                                       
rm -rf ./.deps                                                                                                    
rm: cannot remove `./.deps/execute.Po': Permission denied                                                         
rm: cannot remove `./.deps/tar.Po': Permission denied                                                             
rm: cannot remove `./.deps/cdiff.Po': Permission denied                                                           
rm: cannot remove `./.deps/nonblock.Po': Permission denied                                                        
rm: cannot remove `./.deps/notify.Po': Permission denied                                                          
rm: cannot remove `./.deps/misc.Po': Permission denied                                                            
rm: cannot remove `./.deps/mirman.Po': Permission denied                                                          
rm: cannot remove `./.deps/dns.Po': Permission denied                                                             
rm: cannot remove `./.deps/freshclam.Po': Permission denied                                                       
rm: cannot remove `./.deps/optparser.Po': Permission denied                                                       
rm: cannot remove `./.deps/output.Po': Permission denied                                                          
rm: cannot remove `./.deps/getopt.Po': Permission denied                                                          
rm: cannot remove `./.deps/manager.Po': Permission denied                                                         
make[2]: [distclean] Error 1 (ignored)                                                                            
rm -f Makefile                                                                                                    
make[2]: Leaving directory `/home/user/clamav-0.95.1+dfsg/freshclam'                                              
Making distclean in clamdscan                                                                                     
make[2]: Entering directory `/home/user/clamav-0.95.1+dfsg/clamdscan'                                             
 rm -f clamdscan clamdscan                                                                                        
test -z "*.gcda *.gcno" || rm -f *.gcda *.gcno                                                                    
rm -rf .libs _libs                                                                                                
rm -f *.o                                                                                                         
rm -f *.lo                                                                                                        
rm -f *.tab.c                                                                                                     
test -z "" || rm -f                                                                                               
rm -f TAGS ID GTAGS GRTAGS GSYMS GPATH tags                                                                       
rm -rf ./.deps                                                                                                    
rm: cannot remove `./.deps/client.Po': Permission denied                                                          
rm: cannot remove `./.deps/misc.Po': Permission denied                                                            
rm: cannot remove `./.deps/clamdscan.Po': Permission denied                                                       
rm: cannot remove `./.deps/actions.Po': Permission denied                                                         
rm: cannot remove `./.deps/strlcpy.Po': Permission denied                                                         
rm: cannot remove `./.deps/optparser.Po': Permission denied                                                       
rm: cannot remove `./.deps/output.Po': Permission denied                                                          
rm: cannot remove `./.deps/getopt.Po': Permission denied                                                          
rm: cannot remove `./.deps/proto.Po': Permission denied                                                           
make[2]: [distclean] Error 1 (ignored)                                                                            
rm -f Makefile                                                                                                    
make[2]: Leaving directory `/home/user/clamav-0.95.1+dfsg/clamdscan'                                              
Making distclean in clamd                                                                                         
make[2]: Entering directory `/home/user/clamav-0.95.1+dfsg/clamd'                                                 
test -z "*.gcda *.gcno" || rm -f *.gcda *.gcno                                                                    
rm -rf .libs _libs                                                                                                
 rm -f clamd clamd                                                                                                
rm -f *.o                                                                                                         
rm -f *.lo                                                                                                        
rm -f *.tab.c                                                                                                     
test -z "" || rm -f                                                                                               
rm -f TAGS ID GTAGS GRTAGS GSYMS GPATH tags                                                                       
rm -rf ./.deps                                                                                                    
rm: cannot remove `./.deps/server-th.Po': Permission denied                                                       
rm: cannot remove `./.deps/others.Po': Permission denied                                                          
rm: cannot remove `./.deps/network.Po': Permission denied                                                         
rm: cannot remove `./.deps/dazukoio_compat12.Po': Permission denied                                               
rm: cannot remove `./.deps/misc.Po': Permission denied                                                            
rm: cannot remove `./.deps/thrmgr.Po': Permission denied                                                          
rm: cannot remove `./.deps/clamd.Po': Permission denied                                                           
rm: cannot remove `./.deps/localserver.Po': Permission denied                                                     
rm: cannot remove `./.deps/scanner.Po': Permission denied                                                         
rm: cannot remove `./.deps/dazukoio.Po': Permission denied                                                        
rm: cannot remove `./.deps/tcpserver.Po': Permission denied                                                       
rm: cannot remove `./.deps/optparser.Po': Permission denied                                                       
rm: cannot remove `./.deps/output.Po': Permission denied                                                          
rm: cannot remove `./.deps/getopt.Po': Permission denied                                                          
rm: cannot remove `./.deps/clamuko.Po': Permission denied                                                         
rm: cannot remove `./.deps/session.Po': Permission denied                                                         
make[2]: [distclean] Error 1 (ignored)                                                                            
rm -f Makefile                                                                                                    
make[2]: Leaving directory `/home/user/clamav-0.95.1+dfsg/clamd'                                                  
Making distclean in clamscan                                                                                      
make[2]: Entering directory `/home/user/clamav-0.95.1+dfsg/clamscan'                                              
 rm -f clamscan clamscan                                                                                          
test -z "*.gcda *.gcno" || rm -f *.gcda *.gcno                                                                    
rm -rf .libs _libs                                                                                                
rm -f *.o                                                                                                         
rm -f *.lo                                                                                                        
rm -f *.tab.c                                                                                                     
test -z "" || rm -f                                                                                               
rm -f TAGS ID GTAGS GRTAGS GSYMS GPATH tags                                                                       
rm -rf ./.deps                                                                                                    
rm: cannot remove `./.deps/others.Po': Permission denied                                                          
rm: cannot remove `./.deps/misc.Po': Permission denied                                                            
rm: cannot remove `./.deps/actions.Po': Permission denied                                                         
rm: cannot remove `./.deps/optparser.Po': Permission denied                                                       
rm: cannot remove `./.deps/output.Po': Permission denied                                                          
rm: cannot remove `./.deps/getopt.Po': Permission denied                                                          
rm: cannot remove `./.deps/clamscan.Po': Permission denied                                                        
rm: cannot remove `./.deps/manager.Po': Permission denied                                                         
make[2]: [distclean] Error 1 (ignored)                                                                            
rm -f Makefile                                                                                                    
make[2]: Leaving directory `/home/user/clamav-0.95.1+dfsg/clamscan'                                               
Making distclean in libclamav                                                                                     
make[2]: Entering directory `/home/user/clamav-0.95.1+dfsg/libclamav'                                             
Making distclean in lzma                                                                                          
make[3]: Entering directory `/home/user/clamav-0.95.1+dfsg/libclamav/lzma'                                        
rm -rf .libs _libs                                                                                                
test -z "liblzma.la" || rm -f liblzma.la                                                                          
rm -f "./so_locations"                                                                                            
rm -f *.o                                                                                                         
rm -f *.lo                                                                                                        
rm -f *.tab.c                                                                                                     
test -z "" || rm -f                                                                                               
rm -f TAGS ID GTAGS GRTAGS GSYMS GPATH tags                                                                       
rm -rf ./.deps                                                                                                    
rm: cannot remove `./.deps/LzmaStateDecode.Plo': Permission denied                                                
make[3]: [distclean] Error 1 (ignored)                                                                            
rm -f Makefile                                                                                                    
make[3]: Leaving directory `/home/user/clamav-0.95.1+dfsg/libclamav/lzma'                                         
Making distclean in .                                                                                             
make[3]: Entering directory `/home/user/clamav-0.95.1+dfsg/libclamav'                                             
test -z "version.h version.h.tmp *.gcda *.gcno lzma/*.gcda lzma/*.gcno" || rm -f version.h version.h.tmp *.gcda *.gcno lzma/*.gcda lzma/*.gcno                                                                                      
test -z " libclamav.la" || rm -f  libclamav.la                                                                    
rm -f "./so_locations"                                                                                            
rm -rf .libs _libs                                                                                                
test -z "libclamav_internal_utils.la libclamav_internal_utils_nothreads.la" || rm -f libclamav_internal_utils.la libclamav_internal_utils_nothreads.la                                                                              
rm -f "./so_locations"                                                                                            
rm -f "./so_locations"                                                                                            
rm -f *.o                                                                                                         
rm -f *.lo                                                                                                        
rm -f *.tab.c                                                                                                     
test -z "" || rm -f                                                                                               
rm -f TAGS ID GTAGS GRTAGS GSYMS GPATH tags                                                                       
make[3]: Leaving directory `/home/user/clamav-0.95.1+dfsg/libclamav'                                              
rm -rf ./.deps                                                                                                    
rm: cannot remove `./.deps/libclamav_la-chmunpack.Plo': Permission denied                                         
rm: cannot remove `./.deps/unrar_iface.Plo': Permission denied                                                    
rm: cannot remove `./.deps/libclamav_la-version.Plo': Permission denied                                           
rm: cannot remove `./.deps/libclamav_internal_utils_la-strlcpy.Plo': Permission denied                            
rm: cannot remove `./.deps/libclamav_la-ole2_extract.Plo': Permission denied                                      
rm: cannot remove `./.deps/libclamav_la-wwunpack.Plo': Permission denied                                          
rm: cannot remove `./.deps/libclamav_la-petite.Plo': Permission denied                                            
rm: cannot remove `./.deps/libclamav_la-phishcheck.Plo': Permission denied                                        
rm: cannot remove `./.deps/libclamav_la-msexpand.Plo': Permission denied                                          
rm: cannot remove `./.deps/libclamav_la-elf.Plo': Permission denied                                               
rm: cannot remove `./.deps/libclamav_la-cvd.Plo': Permission denied                                               
rm: cannot remove `./.deps/libclamav_la-pdf.Plo': Permission denied                                               
rm: cannot remove `./.deps/unrarhlp.Plo': Permission denied                                                       
rm: cannot remove `./.deps/libclamav_la-scanners.Plo': Permission denied                                          
rm: cannot remove `./.deps/libclamav_la-rtf.Plo': Permission denied                                               
rm: cannot remove `./.deps/libclamav_la-cab.Plo': Permission denied                                               
rm: cannot remove `./.deps/libclamav_internal_utils_nothreads_la-regcomp.Plo': Permission denied                  
rm: cannot remove `./.deps/libclamav_la-mspack.Plo': Permission denied                                            
rm: cannot remove `./.deps/libclamav_la-upx.Plo': Permission denied                                               
rm: cannot remove `./.deps/libclamav_la-aspack.Plo': Permission denied                                            
rm: cannot remove `./.deps/libclamav_la-infblock.Plo': Permission denied                                          
rm: cannot remove `./.deps/libclamav_internal_utils_nothreads_la-others_common.Plo': Permission denied            
rm: cannot remove `./.deps/libclamav_la-unzip.Plo': Permission denied                                             
rm: cannot remove `./.deps/libclamav_la-vba_extract.Plo': Permission denied                                       
rm: cannot remove `./.deps/libclamav_la-upack.Plo': Permission denied                                             
rm: cannot remove `./.deps/libclamav_la-phish_whitelist.Plo': Permission denied                                   
rm: cannot remove `./.deps/libclamav_la-special.Plo': Permission denied                                           
rm: cannot remove `./.deps/libclamav_la-rebuildpe.Plo': Permission denied                                         
rm: cannot remove `./.deps/libclamav_la-dconf.Plo': Permission denied                                             
rm: cannot remove `./.deps/libclamav_la-blob.Plo': Permission denied                                              
rm: cannot remove `./.deps/libclamav_internal_utils_la-others_common.Plo': Permission denied                      
rm: cannot remove `./.deps/libclamav_la-sha256.Plo': Permission denied                                            
rm: cannot remove `./.deps/libclamav_la-mbox.Plo': Permission denied                                              
rm: cannot remove `./.deps/libclamav_la-text.Plo': Permission denied                                              
rm: cannot remove `./.deps/libclamav_la-textnorm.Plo': Permission denied                                          
rm: cannot remove `./.deps/libclamav_la-mew.Plo': Permission denied                                               
rm: cannot remove `./.deps/libclamav_la-line.Plo': Permission denied                                              
rm: cannot remove `./.deps/libclamav_internal_utils_la-regexec.Plo': Permission denied                            
rm: cannot remove `./.deps/unrarvm.Plo': Permission denied                                                        
rm: cannot remove `./.deps/libclamav_internal_utils_la-str.Plo': Permission denied                                
rm: cannot remove `./.deps/libclamav_internal_utils_nothreads_la-strlcpy.Plo': Permission denied                  
rm: cannot remove `./.deps/libclamav_la-readdb.Plo': Permission denied                                            
rm: cannot remove `./.deps/libclamav_la-fsg.Plo': Permission denied                                               
rm: cannot remove `./.deps/unrarppm.Plo': Permission denied                                                       
rm: cannot remove `./.deps/libclamav_la-table.Plo': Permission denied                                             
rm: cannot remove `./.deps/libclamav_la-js-norm.Plo': Permission denied                                           
rm: cannot remove `./.deps/libclamav_internal_utils_la-regfree.Plo': Permission denied                            
rm: cannot remove `./.deps/libclamav_internal_utils_nothreads_la-str.Plo': Permission denied                      
rm: cannot remove `./.deps/libclamav_internal_utils_la-regcomp.Plo': Permission denied                            
rm: cannot remove `./.deps/libclamav_la-others.Plo': Permission denied                                            
rm: cannot remove `./.deps/libclamav_la-regex_list.Plo': Permission denied                                        
rm: cannot remove `./.deps/libclamav_la-nulsft.Plo': Permission denied                                            
rm: cannot remove `./.deps/libclamav_la-entconv.Plo': Permission denied                                           
rm: cannot remove `./.deps/libclamav_la-disasm.Plo': Permission denied                                            
rm: cannot remove `./.deps/unrar.Plo': Permission denied                                                          
rm: cannot remove `./.deps/libclamav_la-message.Plo': Permission denied                                           
rm: cannot remove `./.deps/libclamav_la-regex_suffix.Plo': Permission denied                                      
rm: cannot remove `./.deps/libclamav_la-uniq.Plo': Permission denied                                              
rm: cannot remove `./.deps/unrarfilter.Plo': Permission denied                                                    
rm: cannot remove `./.deps/libclamav_la-dsig.Plo': Permission denied                                              
rm: cannot remove `./.deps/libclamav_internal_utils_nothreads_la-md5.Plo': Permission denied                      
rm: cannot remove `./.deps/unrarcmd.Plo': Permission denied                                                       
rm: cannot remove `./.deps/libclamav_la-filetypes.Plo': Permission denied                                         
rm: cannot remove `./.deps/libclamav_la-matcher-bm.Plo': Permission denied                                        
rm: cannot remove `./.deps/libclamav_la-yc.Plo': Permission denied                                                
rm: cannot remove `./.deps/libclamav_la-is_tar.Plo': Permission denied                                            
rm: cannot remove `./.deps/libclamav_la-packlibs.Plo': Permission denied                                          
rm: cannot remove `./.deps/libclamav_la-hashtab.Plo': Permission denied                                           
rm: cannot remove `./.deps/libclamav_la-untar.Plo': Permission denied                                             
rm: cannot remove `./.deps/libclamav_la-dlp.Plo': Permission denied                                               
rm: cannot remove `./.deps/libclamav_la-matcher.Plo': Permission denied                                           
rm: cannot remove `./.deps/unrar20.Plo': Permission denied                                                        
rm: cannot remove `./.deps/libclamav_la-bignum.Plo': Permission denied                                            
rm: cannot remove `./.deps/libclamav_la-tnef.Plo': Permission denied                                              
rm: cannot remove `./.deps/libclamav_la-bzlib.Plo': Permission denied                                             
rm: cannot remove `./.deps/libclamav_la-uuencode.Plo': Permission denied                                          
rm: cannot remove `./.deps/libclamav_internal_utils_nothreads_la-regerror.Plo': Permission denied                 
rm: cannot remove `./.deps/libclamav_la-matcher-ac.Plo': Permission denied                                        
rm: cannot remove `./.deps/libclamav_internal_utils_nothreads_la-regfree.Plo': Permission denied                  
rm: cannot remove `./.deps/libclamav_la-htmlnorm.Plo': Permission denied                                          
rm: cannot remove `./.deps/libclamav_la-textdet.Plo': Permission denied                                           
rm: cannot remove `./.deps/libclamav_la-inflate64.Plo': Permission denied                                         
rm: cannot remove `./.deps/unrar15.Plo': Permission denied                                                        
rm: cannot remove `./.deps/libclamav_la-phish_domaincheck_db.Plo': Permission denied                              
rm: cannot remove `./.deps/libclamav_la-unsp.Plo': Permission denied                                              
rm: cannot remove `./.deps/libclamav_la-sis.Plo': Permission denied                                               
rm: cannot remove `./.deps/libclamav_internal_utils_nothreads_la-regexec.Plo': Permission denied                  
rm: cannot remove `./.deps/libclamav_la-unarj.Plo': Permission denied                                             
rm: cannot remove `./.deps/libclamav_la-pe.Plo': Permission denied                                                
rm: cannot remove `./.deps/libclamav_internal_utils_la-md5.Plo': Permission denied                                
rm: cannot remove `./.deps/libclamav_la-explode.Plo': Permission denied                                           
rm: cannot remove `./.deps/libclamav_la-mpool.Plo': Permission denied                                             
rm: cannot remove `./.deps/libclamav_la-autoit.Plo': Permission denied                                            
rm: cannot remove `./.deps/libclamav_internal_utils_la-regerror.Plo': Permission denied                           
rm: cannot remove `./.deps/libclamav_la-spin.Plo': Permission denied                                              
rm: cannot remove `./.deps/libclamav_la-lzma_iface.Plo': Permission denied                                        
rm: cannot remove `./.deps/libclamav_la-binhex.Plo': Permission denied                                            
make[2]: [distclean] Error 1 (ignored)                                                                            
rm -f Makefile                                                                                                    
make[2]: Leaving directory `/home/user/clamav-0.95.1+dfsg/libclamav'                                              
Making distclean in libltdl                                                                                       
make[2]: Entering directory `/home/user/clamav-0.95.1+dfsg/libltdl'                                               
test -z "libltdl.la libltdlc.la libdlloader.la lt__strl.o lt__strl.lo" || rm -f libltdl.la libltdlc.la libdlloader.la lt__strl.o lt__strl.lo                                                                                        
test -z "" || rm -f                                                                                               
rm -rf .libs _libs                                                                                                
rm: cannot remove `.libs/libltdlc_la-lt__alloc.o': Permission denied                                              
rm: cannot remove `.libs/libltdlc.a': Permission denied                                                           
rm: cannot remove `.libs/dlopen.la': Permission denied                                                            
rm: cannot remove `.libs/libltdlc_la-ltdl.o': Permission denied                                                   
rm: cannot remove `.libs/libltdlc_la-slist.o': Permission denied                                                  
rm: cannot remove `.libs/dlopen.o': Permission denied                                                             
rm: cannot remove `.libs/libltdlc_la-preopen.o': Permission denied                                                
rm: cannot remove `.libs/dlopen.a': Permission denied                                                             
rm: cannot remove `.libs/lt__strl.o': Permission denied                                                           
rm: cannot remove `.libs/libltdlc_la-lt_dlloader.o': Permission denied                                            
rm: cannot remove `.libs/libltdlcS.o': Permission denied                                                          
rm: cannot remove `.libs/libltdlc_la-lt_error.o': Permission denied                                               
rm: cannot remove `.libs/libltdlc.la': Permission denied                                                          
make[2]: [clean-libtool] Error 1 (ignored)                                                                        
test -z "dlopen.la libltdlc.la" || rm -f dlopen.la libltdlc.la                                                    
rm -f "./so_locations"                                                                                            
rm -f "./so_locations"                                                                                            
rm -f *.o                                                                                                         
test -z "argz.h argz.h-t" || rm -f argz.h argz.h-t                                                                
rm -f *.lo                                                                                                        
rm -f *.tab.c                                                                                                     
test -z "" || rm -f                                                                                               
rm -f TAGS ID GTAGS GRTAGS GSYMS GPATH tags                                                                       
rm -rf ./.deps                                                                                                    
rm: cannot remove `./.deps/dyld.Plo': Permission denied                                                           
rm: cannot remove `./.deps/libltdl_la-slist.Plo': Permission denied                                               
rm: cannot remove `./.deps/libltdl_la-lt_error.Plo': Permission denied                                            
rm: cannot remove `./.deps/dld_link.Plo': Permission denied                                                       
rm: cannot remove `./.deps/libltdlc_la-lt_error.Plo': Permission denied                                           
rm: cannot remove `./.deps/libltdl_la-ltdl.Plo': Permission denied                                                
rm: cannot remove `./.deps/libltdlc_la-preopen.Plo': Permission denied                                            
rm: cannot remove `./.deps/libltdlc_la-lt__alloc.Plo': Permission denied                                          
rm: cannot remove `./.deps/libltdl_la-lt_dlloader.Plo': Permission denied                                         
rm: cannot remove `./.deps/libltdl_la-preopen.Plo': Permission denied                                             
rm: cannot remove `./.deps/libltdlc_la-lt_dlloader.Plo': Permission denied                                        
rm: cannot remove `./.deps/shl_load.Plo': Permission denied                                                       
rm: cannot remove `./.deps/libltdlc_la-slist.Plo': Permission denied                                              
rm: cannot remove `./.deps/load_add_on.Plo': Permission denied                                                    
rm: cannot remove `./.deps/libltdlc_la-ltdl.Plo': Permission denied                                               
rm: cannot remove `./.deps/lt__strl.Plo': Permission denied                                                       
rm: cannot remove `./.deps/dlopen.Plo': Permission denied                                                         
rm: cannot remove `./.deps/loadlibrary.Plo': Permission denied                                                    
rm: cannot remove `./.deps/libltdl_la-lt__alloc.Plo': Permission denied                                           
make[2]: [distclean] Error 1 (ignored)                                                                            
rm -f Makefile                                                                                                    
make[2]: Leaving directory `/home/user/clamav-0.95.1+dfsg/libltdl'                                                
Making distclean in .                                                                                             
make[2]: Entering directory `/home/user/clamav-0.95.1+dfsg'                                                       
rm -rf .libs _libs                                                                                                
rm -f *.lo                                                                                                        
test -z "clamav-config libclamav.pc docs/man/clamav-milter.8 docs/man/clamconf.1 docs/man/clamd.8 docs/man/clamd.conf.5 docs/man/clamdscan.1 docs/man/clamscan.1 docs/man/freshclam.1 docs/man/freshclam.conf.5 docs/man/sigtool.1 docs/man/clamdtop.1" || rm -f clamav-config libclamav.pc docs/man/clamav-milter.8 docs/man/clamconf.1 docs/man/clamd.8 docs/man/clamd.conf.5 docs/man/clamdscan.1 docs/man/clamscan.1 docs/man/freshclam.1 docs/man/freshclam.conf.5 docs/man/sigtool.1 docs/man/clamdtop.1                                                                            
test -z "target.h" || rm -f target.h                                                                              
rm -f clamav-config.h stamp-h1                                                                                    
rm -f libtool                                                                                                     
rm -f TAGS ID GTAGS GRTAGS GSYMS GPATH tags                                                                       
make[2]: Leaving directory `/home/user/clamav-0.95.1+dfsg'                                                        
rm -f config.status config.cache config.log configure.lineno config.status.lineno                                 
rm -f Makefile                                                                                                    
make[1]: Leaving directory `/home/user/clamav-0.95.1+dfsg'                                                        
rm -f target.h config.log                                                                                         
rm -f build-arch-stamp build-indep-stamp install-indep-stamp install-arch-stamp build-stamp install-stamp         
rm -f debian/clamav-base.config                                                                                   
rm -f debian/clamav-base.postinst                                                                                 
rm -f debian/clamav-daemon.postinst                                                                               
rm -f debian/clamav-daemon.init                                                                                   
rm -f debian/clamav-milter.init                                                                                   
rm -f debian/clamav-milter.config                                                                                 
rm -f debian/clamav-milter.postinst                                                                               
rm -f debian/clamav-freshclam.init                                                                                
rm -f debian/clamav-freshclam.config                                                                              
rm -f debian/clamav-freshclam.postinst                                                                            
dh_clean                                                                                                          
 dpkg-source -b clamav-0.95.1+dfsg                                                                                
dpkg-source: info: using source format `1.0'                                                                      
dpkg-source: info: building clamav using existing clamav_0.95.1+dfsg.orig.tar.gz                                  
dpkg-source: info: building clamav in clamav_0.95.1+dfsg-1ubuntu1.2.diff.gz                                       
dpkg-source: error: cannot represent change to clamav-0.95.1+dfsg/libltdl/.libs/libltdlc_la-lt__alloc.o: binary file contents changed                                                                                               
dpkg-source: error: cannot represent change to clamav-0.95.1+dfsg/libltdl/.libs/libltdlc.a: binary file contents changed                                                                                                            
dpkg-source: error: cannot represent change to clamav-0.95.1+dfsg/libltdl/.libs/dlopen.la:
dpkg-source: error:   new version is symlink to ../dlopen.la
dpkg-source: error:   old version is nonexistent
dpkg-source: error: cannot represent change to clamav-0.95.1+dfsg/libltdl/.libs/libltdlc_la-ltdl.o: binary file contents changed
dpkg-source: error: cannot represent change to clamav-0.95.1+dfsg/libltdl/.libs/libltdlc_la-slist.o: binary file contents changed
dpkg-source: error: cannot represent change to clamav-0.95.1+dfsg/libltdl/.libs/dlopen.o: binary file contents changed
dpkg-source: error: cannot represent change to clamav-0.95.1+dfsg/libltdl/.libs/libltdlc_la-preopen.o: binary file contents changed
dpkg-source: error: cannot represent change to clamav-0.95.1+dfsg/libltdl/.libs/dlopen.a: binary file contents changed
dpkg-source: error: cannot represent change to clamav-0.95.1+dfsg/libltdl/.libs/lt__strl.o: binary file contents changed
dpkg-source: error: cannot represent change to clamav-0.95.1+dfsg/libltdl/.libs/libltdlc_la-lt_dlloader.o: binaryfile contents changed
dpkg-source: error: cannot represent change to clamav-0.95.1+dfsg/libltdl/.libs/libltdlcS.o: binary file contentschanged
dpkg-source: error: cannot represent change to clamav-0.95.1+dfsg/libltdl/.libs/libltdlc_la-lt_error.o: binary file contents changed
dpkg-source: error: cannot represent change to clamav-0.95.1+dfsg/libltdl/.libs/libltdlc.la:
dpkg-source: error:   new version is symlink to ../libltdlc.la
dpkg-source: error:   old version is nonexistent
dpkg-source: warning: ignoring deletion of file libclamav/version.h
dpkg-source: unrepresentable changes to source
dpkg-buildpackage: failure: dpkg-source -b clamav-0.95.1+dfsg gave error exit status 1


looks like fakeroot is not working! WHY!?!:confused:

EDIT: just sudo it (sorry for using all the space)

---

### Post by stuffystuff200681 on 2009-08-04
> **stell86 said:**
> I've tried with both 0.88.2 (from 'normal' repositories) and 0.88.4 (from backports), but I can't find 'debian' or 'rules'
I new to compiling, so much of this was a walk in dark park for me - i'll bring the flashlght next time...

retief
just type it in the terminal

and you will find it (worked with me anyway

---

### Post by faizyunus on 2010-06-05
Does anybody have those instructions for ubuntu 10.04 karmic koala? TQ

---

### Post by wyrdrat on 2010-06-08
I'd like to use clam to real time scan emails in Thunderbird 3.  I understand that clamdrib addon doesn't work in TB3 and I'm getting very confused with Dazuko, DazukoFS and ClamFS.

I'm using 10.04 Lucid.  Any pointers?

Thanks

---

### Post by BarryDocks on 2010-10-02
Does this work for file accessed by a windows box via samba share?
Thanks

Sorry, just found this:
[http://dazuko.dnsalias.org/wiki/index.php/FAQ#Does_DazukoFS_detect_file_accesses_over_Samba.2C_Netatalk.2C_and_NFS.3F]("http://dazuko.dnsalias.org/wiki/index.php/FAQ#Does_DazukoFS_detect_file_accesses_over_Samba.2C_Netatalk.2C_and_NFS.3F")
:oops:

---

### Post by BarryDocks on 2010-10-02
Having trouble loading the dazuko module on boot and hence nothing works.  Running 32bit 9.10:

Have done this:
```
gedit /etc/modules
```
and added dazuko

but I then get nothing after the reboot: ```
:~# lsmod | grep dazuko
:~# 
```
I tried adding the following to /etc/modprobe.d/dazuko.conf
```
install dazuko modprobe -r capability;\
modprobe -i dazuko; \
chmod a+rwx /dev/dazuko; \
modprobe -i capability
```

And tried changing the chmod line to:```
chgrp dazuko /dev/dazuko; \
```

But get: 
```
:~# modprobe dazuko
FATAL: Module capability not found.
FATAL: Module dazuko not found.
chmod: cannot access `/dev/dazuko': No such file or directory
FATAL: Error running install command for dazuko
```

I also tried the following to the same file, from here [http://ubuntuforums.org/showpost.php?p=634418&postcount=13]("http://ubuntuforums.org/showpost.php?p=634418&postcount=13"):
```
install dazuko /sbin/modprobe -r capability;\
/sbin/modprobe --ignore-install dazuko; \
/sbin/modprobe --ignore-install capability
```

Now I get:
```
:~# modprobe dazuko
FATAL: Module capability not found.
FATAL: Module dazuko not found.
FATAL: Module capability not found.
FATAL: Error running install command for dazuko

```

There's got to be something simple I'm missing?](*,)

---

