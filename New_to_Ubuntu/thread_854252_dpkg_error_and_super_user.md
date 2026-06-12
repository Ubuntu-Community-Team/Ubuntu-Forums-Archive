---
title: "dpkg error and super user?"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by ReeyferMadness on 2008-07-09
Hey, I had limewire freeze mid-install (when installing some java stuff) and afterwards updates don't work, spm doesn't work, etc.  Every time I try to install something I get the error 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

So I go to the terminal and enter this and get the return 

dpkg: requested operation requires superuser privilege

I type su or su reeyfermadness and no go.  Don't really know what I'm doing :D  When I just type su it rejects my password, standard one it doesn't reply to when I use su username.  

I'm sure this is something simple, but I couldn't find anything using search function.  Someone plz help because this has me kinda stuck :D

---

### Post by Bigtime_Scrub on 2008-07-09
Are you using su or sudo? Ubuntu uses sudo.

---

### Post by drs305 on 2008-07-09
As Bigtime_Scrub says, su won't work in ubuntu for this command. Run:
```
sudo dpkg --configure -a
```

---

### Post by ReeyferMadness on 2008-07-09
awesomeness guys, you rock!

Fixed now, I think.  I love having an error and the computer tells you the command to input to fix the error :D  And then having the support community to figure out the right way to put in the command lol

---

### Post by poliltimmy on 2008-08-16
I installed alien, no errors. I tried to convert .rpm to .deb, it keeps telling me:

timmy@pawspawsliltoy:~$ sudo alien flash-plugin-9.0.124.0-release.i386.rpm
File "flash-plugin-9.0.124.0-release.i386.rpm" not found.
timmy@pawspawsliltoy:~$

 I have down loaded the file. It is in my documents folder. I'm running Kubuntu 8.o4

---

### Post by drs305 on 2008-08-16
> **poliltimmy said:**
> I installed alien, no errors. I tried to convert .rpm to .deb, it keeps telling me:

timmy@pawspawsliltoy:~$ sudo alien flash-plugin-9.0.124.0-release.i386.rpm
File "flash-plugin-9.0.124.0-release.i386.rpm" not found.
timmy@pawspawsliltoy:~$

 I have down loaded the file. It is in my documents folder. I'm running Kubuntu 8.o4

Are you running the command from the folder in which the rpm file is located? The command should be:
```
sudo alien -k /path.to.file/filename
```

I use the -k switch to keep the original version number.

The easiest way to make sure you are in the right place and don't make a typo is to navigate to the folder in which the rpm is located and then begin to type the command. When you get to "flash" just hit the tab key and it will autocomplete. If it doesn't autocomplete, you are probably not in the correct directory.

If the download folder is Desktop, the command would be:
```

sudo alien -k /home/*username*/Desktop/flash-plugin-9.0.124.0-release.i386.rpm

```
Again, I recommend using tab's autocomplete feature vs typing out the entire filename.

---

### Post by poliltimmy on 2008-08-16
I'm not sure what is wrong. I went to the folder clicked run in terminal. typed:
sudo alien -k /home/timmy/Documents/flash-plugin-9.0.124.0-release.i386.rpm

Igot this: 

Warning: Skipping conversion of scripts in package flash-plugin: postinst prerm
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
parsechangelog/debian: warning:     debian/changelog(l7): badly formatted heading line
LINE: - Flash Player 9.4
parsechangelog/debian: warning:     debian/changelog(l8): badly formatted heading line
LINE: - security updates
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/flash-plugin
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: failure: couldn't find library libdl.so.2 needed by debian/flash-plugin/usr/lib/flash-plugin/libflashplayer.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: command returned error code 512
make: [binary-arch] Error 1 (ignored)
dh_gencontrol
parsechangelog/debian: warning:     debian/changelog(l7): badly formatted heading line
LINE: - Flash Player 9.4
parsechangelog/debian: warning:     debian/changelog(l8): badly formatted heading line
LINE: - security updates
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: flash-plugin-9.0.124.0: No such file or directory

---

### Post by poliltimmy on 2008-08-16
I now have a folder in documents with a debian and usr sub folder

---

### Post by dje on 2008-08-16
to install the flash plugin just do this:
```
sudo apt-get install flashplugin-nonfree
```
there is a deb package available in the repositories so why convert an rpm?

dje

---

### Post by poliltimmy on 2008-08-16
Thanks a bunch. 
                 Timmy

---

### Post by dje on 2008-08-16
> **poliltimmy said:**
> Thanks a bunch. 
                 Timmy

no worries, in future it's always a good idea to check the repositories (synaptic, add/remove) for the program you want as it is be far the easiest way of installing software ;)

dje

---

