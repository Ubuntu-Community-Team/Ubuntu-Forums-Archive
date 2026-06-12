---
title: "Changing /etc/psd.conf to move the web browser profile into RAM"
date: 2013-02-27
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2013-02-27
Following a post at the 'blog [Linux Poison]("http://linuxpoison.blogspot.com/2013/02/tool-to-move-web-browser-profile-to-ram.html"), I changed /etc/psd.conf to USER=mark and un-commented firefox and google-chrome lines. That is all the changes made other than adding the 'bloggers :ppa (since removed). Now, with any use of pacakge install, apt throws an error message as follows. How do I fix this? Google-Chrome throws onscreen messages about not being able to run as root. wtf? I've posted at the 'blog, but have no response a week later. see: 


mark@Lexington-19:~$ sudo aptitude install sysinfo
[sudo] password for mark: 
The following NEW packages will be installed:
  sysinfo 
The following partially installed packages will be configured:
  profile-sync-daemon 
0 packages upgraded, 1 newly installed, 0 to remove and 15 not upgraded.
Need to get 108 kB of archives. After unpacking 367 kB will be used.
Get: 1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe sysinfo all 0.7-8 [108 kB]
Fetched 108 kB in 0s (140 kB/s) 
Selecting previously unselected package sysinfo.
(Reading database ... 351964 files and directories currently installed.)
Unpacking sysinfo (from .../archives/sysinfo_0.7-8_all.deb) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for menu ...
Setting up profile-sync-daemon (5.27.1-1) ...
[7904:7904:0227/103003:ERROR:chrome_browser_main_extra_parts_gtk.cc(51)] Startup refusing to run as root.
dpkg: error processing profile-sync-daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up sysinfo (0.7-8) ...
Processing triggers for menu ...
Errors were encountered while processing:
 profile-sync-daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up profile-sync-daemon (5.27.1-1) ...
[7926:7926:0227/103010:ERROR:chrome_browser_main_extra_parts_gtk.cc(51)] Startup refusing to run as root.
dpkg: error processing profile-sync-daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 profile-sync-daemon

---

### Post by Mark_in_Hollywood on 2013-02-28
The problem was with not understanding and following the instructions 

[http://ubuntuforums.org/showthread.php?t=2115685](http://ubuntuforums.org/showthread.php?t=2115685)

---

