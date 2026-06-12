---
title: "tar.gz can someone walk me through this."
date: 2012-09-24
forum: New to Ubuntu
---

### Post by Jackalyn on 2012-09-24
I have looked at lots of things that say 'how to' but I am obviously not getting something. I have various things downloaded and stored in a file on my desktop - all are tar.gz files. I know you don't install them and then you open them with an archive manager, but that is as far as I get. Most of them, once opened in the manager then seem to ping back to the tar.gz state. The folder is just called usr

I have tried following instructions using the terminal and always get 'not such file or directory.' So I am obviously missing some vital step.

Taking say: /home/jacky/Desktop/usr/Apache_OpenOffice_incubating_3.4.1_Linux_x86_install-deb_en-GB.tar.gz

as an example, what exactly do I do next? (and to the end of the process?)

Please can you put the exact steps how they should be written into the terminal for me as I am sure that this is my problem.....then I can try to run the others I have! 

I think my problem may be I just cannot seem to create a file pathway to add the files to that is 
cd /usr/local/src but 
/usr/local/src exists according to the terminal and I have tried and tried to copy the tar.gz files to that location but seem to be doing something wrong.  

So far I have done this...


Thanks.

---

### Post by Lars Noodén on 2012-09-24
(Did you pick the version (32-bit or 64-bit) that matches your system?)

Well you would go to the folder where the tarball resides and then extract.  After that, you will have to look for what's new.  It might be a directory or it might be a bunch of files, in this case it seems to be a directory.   

```

cd /home/jacky/Desktop/usr/
tar zxf Apache_OpenOffice_incubating_3.4.1_Linux_x86_insta ll-deb_en-GB.tar.gz

gnome-open en-GB/readmes/README_en-GB.html
cd en-GB/DEBS/
sudo dpkg -i *.deb

```

If I recall correctly there was some add-on that you had that did not work properly with LibreOffice.  Have you filed your bug report on it yet?

---

### Post by Jackalyn on 2012-09-24
> **Lars Noodén said:**
> (Did you pick the version (32-bit or 64-bit) that matches your system?)

Well you would go to the folder where the tarball resides and then extract. 

Whenever I extract the folder just seems to ping back to the same state?

After that, you will have to look for what's new.  It might be a directory or it might be a bunch of files, in this case it seems to be a directory.   

[code]
cd /home/jacky/Desktop/usr/
tar zxf Apache_OpenOffice_incubating_3.4.1_Linux_x86_insta ll-deb_en-GB.tar.gz

and I get this

jacky@jacky-Aspire-6930G:~$ [code]
[code]: command not found
jacky@jacky-Aspire-6930G:~$ cd /home/jacky/Desktop/usr/
jacky@jacky-Aspire-6930G:~/Desktop/usr$ tar zxf Apache_OpenOffice_incubating_3.4.1_Linux_x86_insta ll-deb_en-GB.tar.gz
tar (child): Apache_OpenOffice_incubating_3.4.1_Linux_x86_insta: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
jacky@jacky-Aspire-6930G:~/Desktop/usr$ cd /home/jacky/Desktop/usr/
jacky@jacky-Aspire-6930G:~/Desktop/usr$ tar zxf Apache_OpenOffice_incubating_3.4.1_Linux_x86_insta ll-deb_en-GB.tar.gz
tar (child): Apache_OpenOffice_incubating_3.4.1_Linux_x86_insta: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
jacky@jacky-Aspire-6930G:~/Desktop/usr$ 


gnome-open en-GB/readmes/README_en-GB.html
cd en-GB/DEBS/
sudo dpkg -i *.deb
[/code

Opened the open office website 'read me' page

]If I recall correctly there was some add-on that you had that did not work properly with LibreOffice.  Have you filed your bug report on it yet?

Yes think I did that a while ago.

Thanks

---

### Post by agillator on 2012-09-24
Tar will extract the tarball to your current directory. So, cd to the directory where you wish the files to be (which may or may NOT be the /usr/local/src) and then extract the tarball using the command in the message above. I use the zxvf instead of zxf so I can get some idea of what is where; the v is for 'verbose'. Then look for a README or INSTALL file or some other file that is obviously intended to contain instructions. 

What you have in a 'tar.gz' file is simply a group of files that have been archived (many files combined into one) and compressed (gz, bz2 or some other system, see the man page for tar). Any group of files can be 'tarred'. A tarball is not necessarily (or not only) an installation file, so you need to know what to do with it after you expand it.

---

### Post by Jackalyn on 2012-09-24
This is what actually happened next with the above:

```
jacky@jacky-Aspire-6930G:~$ 
: command not found
jacky@jacky-Aspire-6930G:~$ cd /home/jacky/Desktop/usr/
jacky@jacky-Aspire-6930G:~/Desktop/usr$ tar zxf Apache_OpenOffice_incubating_3.4.1_Linux_x86_insta ll-deb_en-GB.tar.gz
tar (child): Apache_OpenOffice_incubating_3.4.1_Linux_x86_insta: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
jacky@jacky-Aspire-6930G:~/Desktop/usr$ cd /home/jacky/Desktop/usr/
jacky@jacky-Aspire-6930G:~/Desktop/usr$ tar zxf Apache_OpenOffice_incubating_3.4.1_Linux_x86_insta ll-deb_en-GB.tar.gz
tar (child): Apache_OpenOffice_incubating_3.4.1_Linux_x86_insta: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
jacky@jacky-Aspire-6930G:~/Desktop/usr$ 
jacky@jacky-Aspire-6930G:~/Desktop/usr$ gnome-open en-GB/readmes/README_en-GB.html
jacky@jacky-Aspire-6930G:~/Desktop/usr$ cd en-GB/DEBS/
jacky@jacky-Aspire-6930G:~/Desktop/usr/en-GB/DEBS$ sudo dpkg -i *.deb
[sudo] password for jacky: 
Sorry, try again.
[sudo] password for jacky: 
Selecting previously unselected package ooobasis3.4-base.
(Reading database ... 279171 files and directories currently installed.)
Unpacking ooobasis3.4-base (from ooobasis3.4-base_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-binfilter.
Unpacking ooobasis3.4-binfilter (from ooobasis3.4-binfilter_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-calc.
Unpacking ooobasis3.4-calc (from ooobasis3.4-calc_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-core01.
Unpacking ooobasis3.4-core01 (from ooobasis3.4-core01_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-core02.
Unpacking ooobasis3.4-core02 (from ooobasis3.4-core02_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-core03.
Unpacking ooobasis3.4-core03 (from ooobasis3.4-core03_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-core04.
Unpacking ooobasis3.4-core04 (from ooobasis3.4-core04_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-core05.
Unpacking ooobasis3.4-core05 (from ooobasis3.4-core05_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-core06.
Unpacking ooobasis3.4-core06 (from ooobasis3.4-core06_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-core07.
Unpacking ooobasis3.4-core07 (from ooobasis3.4-core07_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-draw.
Unpacking ooobasis3.4-draw (from ooobasis3.4-draw_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-en-gb.
Unpacking ooobasis3.4-en-gb (from ooobasis3.4-en-gb_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-en-gb-base.
Unpacking ooobasis3.4-en-gb-base (from ooobasis3.4-en-gb-base_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-en-gb-binfilter.
Unpacking ooobasis3.4-en-gb-binfilter (from ooobasis3.4-en-gb-binfilter_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-en-gb-calc.
Unpacking ooobasis3.4-en-gb-calc (from ooobasis3.4-en-gb-calc_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-en-gb-draw.
Unpacking ooobasis3.4-en-gb-draw (from ooobasis3.4-en-gb-draw_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-en-gb-help.
Unpacking ooobasis3.4-en-gb-help (from ooobasis3.4-en-gb-help_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-en-gb-impress.
Unpacking ooobasis3.4-en-gb-impress (from ooobasis3.4-en-gb-impress_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-en-gb-math.
Unpacking ooobasis3.4-en-gb-math (from ooobasis3.4-en-gb-math_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-en-gb-res.
Unpacking ooobasis3.4-en-gb-res (from ooobasis3.4-en-gb-res_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-en-gb-writer.
Unpacking ooobasis3.4-en-gb-writer (from ooobasis3.4-en-gb-writer_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-gnome-integration.
Unpacking ooobasis3.4-gnome-integration (from ooobasis3.4-gnome-integration_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-graphicfilter.
Unpacking ooobasis3.4-graphicfilter (from ooobasis3.4-graphicfilter_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-images.
Unpacking ooobasis3.4-images (from ooobasis3.4-images_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-impress.
Unpacking ooobasis3.4-impress (from ooobasis3.4-impress_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-javafilter.
Unpacking ooobasis3.4-javafilter (from ooobasis3.4-javafilter_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-math.
Unpacking ooobasis3.4-math (from ooobasis3.4-math_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-ogltrans.
Unpacking ooobasis3.4-ogltrans (from ooobasis3.4-ogltrans_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-onlineupdate.
Unpacking ooobasis3.4-onlineupdate (from ooobasis3.4-onlineupdate_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-ooofonts.
Unpacking ooobasis3.4-ooofonts (from ooobasis3.4-ooofonts_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-ooolinguistic.
Unpacking ooobasis3.4-ooolinguistic (from ooobasis3.4-ooolinguistic_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-pyuno.
Unpacking ooobasis3.4-pyuno (from ooobasis3.4-pyuno_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-testtool.
Unpacking ooobasis3.4-testtool (from ooobasis3.4-testtool_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-writer.
Unpacking ooobasis3.4-writer (from ooobasis3.4-writer_3.4.1-1_i386.deb) ...
Selecting previously unselected package ooobasis3.4-xsltfilter.
Unpacking ooobasis3.4-xsltfilter (from ooobasis3.4-xsltfilter_3.4.1-1_i386.deb) ...
Selecting previously unselected package openoffice.org3.
Unpacking openoffice.org3 (from openoffice.org3_3.4.1-1_i386.deb) ...
Selecting previously unselected package openoffice.org3-base.
Unpacking openoffice.org3-base (from openoffice.org3-base_3.4.1-1_i386.deb) ...
Selecting previously unselected package openoffice.org3-calc.
Unpacking openoffice.org3-calc (from openoffice.org3-calc_3.4.1-1_i386.deb) ...
Selecting previously unselected package openoffice.org3-draw.
Unpacking openoffice.org3-draw (from openoffice.org3-draw_3.4.1-1_i386.deb) ...
Selecting previously unselected package openoffice.org3-en-gb.
Unpacking openoffice.org3-en-gb (from openoffice.org3-en-gb_3.4.1-1_i386.deb) ...
Selecting previously unselected package openoffice.org3-impress.
Unpacking openoffice.org3-impress (from openoffice.org3-impress_3.4.1-1_i386.deb) ...
Selecting previously unselected package openoffice.org3-math.
Unpacking openoffice.org3-math (from openoffice.org3-math_3.4.1-1_i386.deb) ...
Selecting previously unselected package openoffice.org3-writer.
Unpacking openoffice.org3-writer (from openoffice.org3-writer_3.4.1-1_i386.deb) ...
Selecting previously unselected package openoffice.org-ure.
Unpacking openoffice.org-ure (from openoffice.org-ure_3.4.1-1_i386.deb) ...
Setting up openoffice.org-ure (3.4.1-1) ...
Setting up ooobasis3.4-core01 (3.4.1-1) ...
Setting up ooobasis3.4-core02 (3.4.1-1) ...
Setting up ooobasis3.4-core03 (3.4.1-1) ...
Setting up ooobasis3.4-core04 (3.4.1-1) ...
Setting up ooobasis3.4-core05 (3.4.1-1) ...
Setting up ooobasis3.4-core06 (3.4.1-1) ...
Setting up ooobasis3.4-core07 (3.4.1-1) ...
Setting up ooobasis3.4-draw (3.4.1-1) ...
Setting up ooobasis3.4-en-gb (3.4.1-1) ...
Setting up ooobasis3.4-en-gb-base (3.4.1-1) ...
Setting up ooobasis3.4-en-gb-binfilter (3.4.1-1) ...
Setting up ooobasis3.4-en-gb-calc (3.4.1-1) ...
Setting up ooobasis3.4-en-gb-draw (3.4.1-1) ...
Setting up ooobasis3.4-en-gb-help (3.4.1-1) ...
Setting up ooobasis3.4-en-gb-impress (3.4.1-1) ...
Setting up ooobasis3.4-en-gb-math (3.4.1-1) ...
Setting up ooobasis3.4-en-gb-res (3.4.1-1) ...
Setting up ooobasis3.4-en-gb-writer (3.4.1-1) ...
Setting up ooobasis3.4-gnome-integration (3.4.1-1) ...
Setting up ooobasis3.4-graphicfilter (3.4.1-1) ...
Setting up ooobasis3.4-images (3.4.1-1) ...
Setting up ooobasis3.4-impress (3.4.1-1) ...
Setting up ooobasis3.4-javafilter (3.4.1-1) ...
Setting up ooobasis3.4-math (3.4.1-1) ...
Setting up ooobasis3.4-ogltrans (3.4.1-1) ...
Setting up ooobasis3.4-onlineupdate (3.4.1-1) ...
Setting up ooobasis3.4-ooofonts (3.4.1-1) ...
Setting up ooobasis3.4-ooolinguistic (3.4.1-1) ...
Setting up ooobasis3.4-pyuno (3.4.1-1) ...
Setting up ooobasis3.4-testtool (3.4.1-1) ...
Setting up ooobasis3.4-writer (3.4.1-1) ...
Setting up ooobasis3.4-xsltfilter (3.4.1-1) ...
Setting up openoffice.org3 (3.4.1-1) ...
Setting up openoffice.org3-draw (3.4.1-1) ...
Setting up openoffice.org3-en-gb (3.4.1-1) ...
Setting up openoffice.org3-impress (3.4.1-1) ...
Setting up openoffice.org3-math (3.4.1-1) ...
Setting up openoffice.org3-writer (3.4.1-1) ...
Setting up ooobasis3.4-base (3.4.1-1) ...
Setting up ooobasis3.4-binfilter (3.4.1-1) ...
Setting up ooobasis3.4-calc (3.4.1-1) ...
Setting up openoffice.org3-base (3.4.1-1) ...
Setting up openoffice.org3-calc (3.4.1-1) ...
jacky@jacky-Aspire-6930G:~/Desktop/usr/en-GB/DEBS$ 
jacky@jacky-Aspire-6930G:~/Desktop/usr/en-GB/DEBS$ ^C
jacky@jacky-Aspire-6930G:~/Desktop/usr/en-GB/DEBS$
``` 

 At least all the files are at that location but I still do not know how to make the application work??? Right clicking on a file says 'open with Ubuntu software manager as first choice' and doing that I get 'Dependency is not satisfiable.' 

Have I just proved again that there is no way to get Open Office in Ubuntu 12.4?

Ok going to try the Calligra Author I could not open...

---

### Post by agillator on 2012-09-24
I was typing a response while you were posting yours. 

Are you sure the file is in the directory you think? Do an ls -l on that directory to make sure, and make sure you have the necessary permissions (although the error message should be different if you don't). With a long filename like that, check, double and triple check for typos (that is usually my problem). Remember it must be EXACT. Make sure you are either in the directory where the file is located or you use the entire path as part of the filename. If nothing else, try copying the file and naming it something simpler and then try untarring it. Changing the name should make no difference in the output of the expansion.

---

### Post by Jackalyn on 2012-09-24
> **agillator said:**
> I was typing a response while you were posting yours. 

Are you sure the file is in the directory you think? Do an ls -l on that directory to make sure, and make sure you have the necessary permissions (although the error message should be different if you don't). With a long filename like that, check, double and triple check for typos (that is usually my problem). Remember it must be EXACT. Make sure you are either in the directory where the file is located or you use the entire path as part of the filename. If nothing else, try copying the file and naming it something simpler and then try untarring it. Changing the name should make no difference in the output of the expansion.

"Do an ls -l "
The trouble is I am so new to this I have no idea what this is or how to do it!

---

### Post by Jackalyn on 2012-09-24
Here is the rest of what I have done this morning following a website till I got stuck...

```
jacky@jacky-Aspire-6930G:~$ 
jacky@jacky-Aspire-6930G:~$ 
jacky@jacky-Aspire-6930G:~$ sudo apt-get install build-essential checkinstall
[sudo] password for jacky: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
checkinstall is already the newest version.
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  language-pack-kde-en language-pack-kde-en-base kde-l10n-engb
  calligra-l10n-engb calligra-l10n-zhcn calligra-l10n-de
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.
jacky@jacky-Aspire-6930G:~$ sudo apt-get install subversion git-core mercurial
Reading package lists... Done
Building dependency tree       
Reading state information... Done
git-core is already the newest version.
subversion is already the newest version.
mercurial is already the newest version.
The following packages were automatically installed and are no longer required:
  language-pack-kde-en language-pack-kde-en-base kde-l10n-engb
  calligra-l10n-engb calligra-l10n-zhcn calligra-l10n-de
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.
jacky@jacky-Aspire-6930G:~$ usr/local/src
bash: usr/local/src: No such file or directory
jacky@jacky-Aspire-6930G:~$ sudo chown $USER /usr/local/src
jacky@jacky-Aspire-6930G:~$ sudo chmod u+rwx /usr/local/src
jacky@jacky-Aspire-6930G:~$ sudo apt-get install apt-file
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  language-pack-kde-en language-pack-kde-en-base kde-l10n-engb
  calligra-l10n-engb calligra-l10n-zhcn calligra-l10n-de
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libapt-pkg-perl libconfig-file-perl liblist-moreutils-perl
  libregexp-assemble-perl
The following NEW packages will be installed
  apt-file libapt-pkg-perl libconfig-file-perl liblist-moreutils-perl
  libregexp-assemble-perl
0 upgraded, 5 newly installed, 0 to remove and 17 not upgraded.
Need to get 253 kB of archives.
After this operation, 920 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe libconfig-file-perl all 1.50-2 [10.1 kB]
Get:2 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main libapt-pkg-perl i386 0.1.25build2 [82.2 kB]
Get:3 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main liblist-moreutils-perl i386 0.33-1build1 [47.2 kB]
Get:4 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe libregexp-assemble-perl all 0.35-2 [87.5 kB]
Get:5 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe apt-file all 2.5.0ubuntu1 [25.6 kB]
Fetched 253 kB in 8s (30.7 kB/s)                                               
Selecting previously unselected package libconfig-file-perl.
(Reading database ... 279067 files and directories currently installed.)
Unpacking libconfig-file-perl (from .../libconfig-file-perl_1.50-2_all.deb) ...
Selecting previously unselected package libapt-pkg-perl.
Unpacking libapt-pkg-perl (from .../libapt-pkg-perl_0.1.25build2_i386.deb) ...
Selecting previously unselected package liblist-moreutils-perl.
Unpacking liblist-moreutils-perl (from .../liblist-moreutils-perl_0.33-1build1_i386.deb) ...
Selecting previously unselected package libregexp-assemble-perl.
Unpacking libregexp-assemble-perl (from .../libregexp-assemble-perl_0.35-2_all.deb) ...
Selecting previously unselected package apt-file.
Unpacking apt-file (from .../apt-file_2.5.0ubuntu1_all.deb) ...
Processing triggers for man-db ...
Setting up libconfig-file-perl (1.50-2) ...
Setting up libapt-pkg-perl (0.1.25build2) ...
Setting up liblist-moreutils-perl (0.33-1build1) ...
Setting up libregexp-assemble-perl (0.35-2) ...
Setting up apt-file (2.5.0ubuntu1) ...
The system-wide cache is empty. You may want to run 'apt-file update'
as root to update the cache. You can also run 'apt-file update' as
normal user to use a cache in the user's home directory.
jacky@jacky-Aspire-6930G:~$ sudo apt-file update
Downloading complete file [http://gb.archive.ubuntu.com/ubuntu/dists/precise/Contents-i386.gz](http://gb.archive.ubuntu.com/ubuntu/dists/precise/Contents-i386.gz)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
 44 21.3M   44 9803k    0     0   4662      0  1:20:02  0:35:53  0:44:09     0^CDownload of [http://gb.archive.ubuntu.com/ubuntu/dists/precise/Contents-i386.gz](http://gb.archive.ubuntu.com/ubuntu/dists/precise/Contents-i386.gz) failed
Command died with signal 2
E: Update aborted by signal 2
jacky@jacky-Aspire-6930G:~$ sudo apt-file update
[sudo] password for jacky: 
jSorry, try again.
[sudo] password for jacky: 
jDownloading complete file [http://gb.archive.ubuntu.com/ubuntu/dists/precise/Contents-i386.gz](http://gb.archive.ubuntu.com/ubuntu/dists/precise/Contents-i386.gz)
a  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 21.3M  100 21.3M    0     0  41852      0  0:08:54  0:08:54 --:--:-- 44571ys
Downloading complete file [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/Contents-i386.gz](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/Contents-i386.gz)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 4052k  100 4052k    0     0  36939      0  0:01:52  0:01:52 --:--:-- 27354
Downloading Index [http://gb.archive.ubuntu.com/ubuntu/dists/precise/Contents-i386.diff/Index:](http://gb.archive.ubuntu.com/ubuntu/dists/precise/Contents-i386.diff/Index:)
No Index available.
Downloading complete file [http://gb.archive.ubuntu.com/ubuntu/dists/precise/Contents-i386.gz](http://gb.archive.ubuntu.com/ubuntu/dists/precise/Contents-i386.gz)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:--  0:00:10 --:--:--     0
File is up-to-date.
Downloading Index [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/Contents-i386.diff/Index:](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/Contents-i386.diff/Index:)
No Index available.
Downloading complete file [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/Contents-i386.gz](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/Contents-i386.gz)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
File is up-to-date.
Downloading Index [http://gb.archive.ubuntu.com/ubuntu/dists/precise/Contents-i386.diff/Index:](http://gb.archive.ubuntu.com/ubuntu/dists/precise/Contents-i386.diff/Index:)
No Index available.
Downloading complete file [http://gb.archive.ubuntu.com/ubuntu/dists/precise/Contents-i386.gz](http://gb.archive.ubuntu.com/ubuntu/dists/precise/Contents-i386.gz)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
File is up-to-date.
Downloading Index [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/Contents-i386.diff/Index:](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/Contents-i386.diff/Index:)
No Index available.
Downloading complete file [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/Contents-i386.gz](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/Contents-i386.gz)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
File is up-to-date.
Downloading complete file [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/Contents-i386.gz](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/Contents-i386.gz)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  226k  100  226k    0     0  30040      0  0:00:07  0:00:07 --:--:-- 44214
Downloading complete file [http://security.ubuntu.com/ubuntu/dists/precise-security/Contents-i386.gz](http://security.ubuntu.com/ubuntu/dists/precise-security/Contents-i386.gz)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 2264k  100 2264k    0     0  43453      0  0:00:53  0:00:53 --:--:-- 44896
Downloading Index [http://security.ubuntu.com/ubuntu/dists/precise-security/Contents-i386.diff/Index:](http://security.ubuntu.com/ubuntu/dists/precise-security/Contents-i386.diff/Index:)
No Index available.
Downloading complete file [http://security.ubuntu.com/ubuntu/dists/precise-security/Contents-i386.gz](http://security.ubuntu.com/ubuntu/dists/precise-security/Contents-i386.gz)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
File is up-to-date.
Downloading Index [http://security.ubuntu.com/ubuntu/dists/precise-security/Contents-i386.diff/Index:](http://security.ubuntu.com/ubuntu/dists/precise-security/Contents-i386.diff/Index:)
No Index available.
Downloading complete file [http://security.ubuntu.com/ubuntu/dists/precise-security/Contents-i386.gz](http://security.ubuntu.com/ubuntu/dists/precise-security/Contents-i386.gz)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
File is up-to-date.
Ignoring source without Contents File:
  [http://archive.canonical.com/ubuntu/dists/precise/Contents-i386.gz](http://archive.canonical.com/ubuntu/dists/precise/Contents-i386.gz)
Ignoring source without Contents File:
  [http://extras.ubuntu.com/ubuntu/dists/precise/Contents-i386.gz](http://extras.ubuntu.com/ubuntu/dists/precise/Contents-i386.gz)
Downloading complete file [http://gb.archive.ubuntu.com/ubuntu/dists/precise-proposed/Contents-i386.gz](http://gb.archive.ubuntu.com/ubuntu/dists/precise-proposed/Contents-i386.gz)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  790k  100  790k    0     0  35993      0  0:00:22  0:00:22 --:--:-- 46132
Ignoring source without Contents File:
  [http://archive.canonical.com/ubuntu/dists/precise/Contents-i386.gz](http://archive.canonical.com/ubuntu/dists/precise/Contents-i386.gz)
Ignoring source without Contents File:
  [http://ppa.launchpad.net/shane2peru/bibleanalyzer-stable/ubuntu/dists/precise/Contents-i386.gz](http://ppa.launchpad.net/shane2peru/bibleanalyzer-stable/ubuntu/dists/precise/Contents-i386.gz)
Ignoring source without Contents File:
  [http://ppa.launchpad.net/upubuntu-com/office/ubuntu/dists/precise/Contents-i386.gz](http://ppa.launchpad.net/upubuntu-com/office/ubuntu/dists/precise/Contents-i386.gz)
Ignoring source without Contents File:
  [http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/precise/Contents-i386.gz](http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/precise/Contents-i386.gz)
jacky@jacky-Aspire-6930G:~$
```

---

### Post by Jackalyn on 2012-09-24
Here is the rest of what I have done this morning following a website till I got stuck...

```
jacky@jacky-Aspire-6930G:~$ 
jacky@jacky-Aspire-6930G:~$ 
jacky@jacky-Aspire-6930G:~$ sudo apt-get install build-essential checkinstall
[sudo] password for jacky: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
checkinstall is already the newest version.
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  language-pack-kde-en language-pack-kde-en-base kde-l10n-engb
  calligra-l10n-engb calligra-l10n-zhcn calligra-l10n-de
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.
jacky@jacky-Aspire-6930G:~$ sudo apt-get install subversion git-core mercurial
Reading package lists... Done
Building dependency tree       
Reading state information... Done
git-core is already the newest version.
subversion is already the newest version.
mercurial is already the newest version.
The following packages were automatically installed and are no longer required:
  language-pack-kde-en language-pack-kde-en-base kde-l10n-engb
  calligra-l10n-engb calligra-l10n-zhcn calligra-l10n-de
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.
jacky@jacky-Aspire-6930G:~$ usr/local/src
bash: usr/local/src: No such file or directory
jacky@jacky-Aspire-6930G:~$ sudo chown $USER /usr/local/src
jacky@jacky-Aspire-6930G:~$ sudo chmod u+rwx /usr/local/src
jacky@jacky-Aspire-6930G:~$ sudo apt-get install apt-file
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  language-pack-kde-en language-pack-kde-en-base kde-l10n-engb
  calligra-l10n-engb calligra-l10n-zhcn calligra-l10n-de
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libapt-pkg-perl libconfig-file-perl liblist-moreutils-perl
  libregexp-assemble-perl
The following NEW packages will be installed
  apt-file libapt-pkg-perl libconfig-file-perl liblist-moreutils-perl
  libregexp-assemble-perl
0 upgraded, 5 newly installed, 0 to remove and 17 not upgraded.
Need to get 253 kB of archives.
After this operation, 920 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe libconfig-file-perl all 1.50-2 [10.1 kB]
Get:2 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main libapt-pkg-perl i386 0.1.25build2 [82.2 kB]
Get:3 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main liblist-moreutils-perl i386 0.33-1build1 [47.2 kB]
Get:4 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe libregexp-assemble-perl all 0.35-2 [87.5 kB]
Get:5 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe apt-file all 2.5.0ubuntu1 [25.6 kB]
Fetched 253 kB in 8s (30.7 kB/s)                                               
Selecting previously unselected package libconfig-file-perl.
(Reading database ... 279067 files and directories currently installed.)
Unpacking libconfig-file-perl (from .../libconfig-file-perl_1.50-2_all.deb) ...
Selecting previously unselected package libapt-pkg-perl.
Unpacking libapt-pkg-perl (from .../libapt-pkg-perl_0.1.25build2_i386.deb) ...
Selecting previously unselected package liblist-moreutils-perl.
Unpacking liblist-moreutils-perl (from .../liblist-moreutils-perl_0.33-1build1_i386.deb) ...
Selecting previously unselected package libregexp-assemble-perl.
Unpacking libregexp-assemble-perl (from .../libregexp-assemble-perl_0.35-2_all.deb) ...
Selecting previously unselected package apt-file.
Unpacking apt-file (from .../apt-file_2.5.0ubuntu1_all.deb) ...
Processing triggers for man-db ...
Setting up libconfig-file-perl (1.50-2) ...
Setting up libapt-pkg-perl (0.1.25build2) ...
Setting up liblist-moreutils-perl (0.33-1build1) ...
Setting up libregexp-assemble-perl (0.35-2) ...
Setting up apt-file (2.5.0ubuntu1) ...
The system-wide cache is empty. You may want to run 'apt-file update'
as root to update the cache. You can also run 'apt-file update' as
normal user to use a cache in the user's home directory.
jacky@jacky-Aspire-6930G:~$ sudo apt-file update
Downloading complete file [http://gb.archive.ubuntu.com/ubuntu/dists/precise/Contents-i386.gz](http://gb.archive.ubuntu.com/ubuntu/dists/precise/Contents-i386.gz)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
 44 21.3M   44 9803k    0     0   4662      0  1:20:02  0:35:53  0:44:09     0^CDownload of [http://gb.archive.ubuntu.com/ubuntu/dists/precise/Contents-i386.gz](http://gb.archive.ubuntu.com/ubuntu/dists/precise/Contents-i386.gz) failed
Command died with signal 2
E: Update aborted by signal 2
jacky@jacky-Aspire-6930G:~$ sudo apt-file update
[sudo] password for jacky: 
jSorry, try again.
[sudo] password for jacky: 
jDownloading complete file [http://gb.archive.ubuntu.com/ubuntu/dists/precise/Contents-i386.gz](http://gb.archive.ubuntu.com/ubuntu/dists/precise/Contents-i386.gz)
a  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 21.3M  100 21.3M    0     0  41852      0  0:08:54  0:08:54 --:--:-- 44571ys
Downloading complete file [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/Contents-i386.gz](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/Contents-i386.gz)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 4052k  100 4052k    0     0  36939      0  0:01:52  0:01:52 --:--:-- 27354
Downloading Index [http://gb.archive.ubuntu.com/ubuntu/dists/precise/Contents-i386.diff/Index:](http://gb.archive.ubuntu.com/ubuntu/dists/precise/Contents-i386.diff/Index:)
No Index available.
Downloading complete file [http://gb.archive.ubuntu.com/ubuntu/dists/precise/Contents-i386.gz](http://gb.archive.ubuntu.com/ubuntu/dists/precise/Contents-i386.gz)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:--  0:00:10 --:--:--     0
File is up-to-date.
Downloading Index [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/Contents-i386.diff/Index:](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/Contents-i386.diff/Index:)
No Index available.
Downloading complete file [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/Contents-i386.gz](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/Contents-i386.gz)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
File is up-to-date.
Downloading Index [http://gb.archive.ubuntu.com/ubuntu/dists/precise/Contents-i386.diff/Index:](http://gb.archive.ubuntu.com/ubuntu/dists/precise/Contents-i386.diff/Index:)
No Index available.
Downloading complete file [http://gb.archive.ubuntu.com/ubuntu/dists/precise/Contents-i386.gz](http://gb.archive.ubuntu.com/ubuntu/dists/precise/Contents-i386.gz)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
File is up-to-date.
Downloading Index [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/Contents-i386.diff/Index:](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/Contents-i386.diff/Index:)
No Index available.
Downloading complete file [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/Contents-i386.gz](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/Contents-i386.gz)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
File is up-to-date.
Downloading complete file [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/Contents-i386.gz](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/Contents-i386.gz)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  226k  100  226k    0     0  30040      0  0:00:07  0:00:07 --:--:-- 44214
Downloading complete file [http://security.ubuntu.com/ubuntu/dists/precise-security/Contents-i386.gz](http://security.ubuntu.com/ubuntu/dists/precise-security/Contents-i386.gz)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 2264k  100 2264k    0     0  43453      0  0:00:53  0:00:53 --:--:-- 44896
Downloading Index [http://security.ubuntu.com/ubuntu/dists/precise-security/Contents-i386.diff/Index:](http://security.ubuntu.com/ubuntu/dists/precise-security/Contents-i386.diff/Index:)
No Index available.
Downloading complete file [http://security.ubuntu.com/ubuntu/dists/precise-security/Contents-i386.gz](http://security.ubuntu.com/ubuntu/dists/precise-security/Contents-i386.gz)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
File is up-to-date.
Downloading Index [http://security.ubuntu.com/ubuntu/dists/precise-security/Contents-i386.diff/Index:](http://security.ubuntu.com/ubuntu/dists/precise-security/Contents-i386.diff/Index:)
No Index available.
Downloading complete file [http://security.ubuntu.com/ubuntu/dists/precise-security/Contents-i386.gz](http://security.ubuntu.com/ubuntu/dists/precise-security/Contents-i386.gz)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
File is up-to-date.
Ignoring source without Contents File:
  [http://archive.canonical.com/ubuntu/dists/precise/Contents-i386.gz](http://archive.canonical.com/ubuntu/dists/precise/Contents-i386.gz)
Ignoring source without Contents File:
  [http://extras.ubuntu.com/ubuntu/dists/precise/Contents-i386.gz](http://extras.ubuntu.com/ubuntu/dists/precise/Contents-i386.gz)
Downloading complete file [http://gb.archive.ubuntu.com/ubuntu/dists/precise-proposed/Contents-i386.gz](http://gb.archive.ubuntu.com/ubuntu/dists/precise-proposed/Contents-i386.gz)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  790k  100  790k    0     0  35993      0  0:00:22  0:00:22 --:--:-- 46132
Ignoring source without Contents File:
  [http://archive.canonical.com/ubuntu/dists/precise/Contents-i386.gz](http://archive.canonical.com/ubuntu/dists/precise/Contents-i386.gz)
Ignoring source without Contents File:
  [http://ppa.launchpad.net/shane2peru/bibleanalyzer-stable/ubuntu/dists/precise/Contents-i386.gz](http://ppa.launchpad.net/shane2peru/bibleanalyzer-stable/ubuntu/dists/precise/Contents-i386.gz)
Ignoring source without Contents File:
  [http://ppa.launchpad.net/upubuntu-com/office/ubuntu/dists/precise/Contents-i386.gz](http://ppa.launchpad.net/upubuntu-com/office/ubuntu/dists/precise/Contents-i386.gz)
Ignoring source without Contents File:
  [http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/precise/Contents-i386.gz](http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/precise/Contents-i386.gz)
jacky@jacky-Aspire-6930G:~$
```

I have no idea really what happened or what I have done but assume all things I have got updated in some way or changed or something or other...LOL I would liken using linux when u have no idea to using a slot machine and occassionally getting a payout because I get more and more confused!

---

### Post by agillator on 2012-09-24
OK, open a command terminal (you obviously have learned how to do that), change to the directory you want the listing for, and type 'ls -l' without the quotes.  That will give you a listing of the files in that directory as well as a lot of other information. The information you are looking for will be toward the left, the permissions, which will be a series of dashes and/or letters. Don't worry about the first (probably a -, could be a 'd' or something else), look at the next nine. They should be read in groups of three. The first position should be a dash or an r for read, then a dash or a w for write and then a dash or an x for execute. The first group of three is for the owner of the file, the second group is for members of the file's group and the third is for everyone else. The dash means they do NOT have that permission, the letter means they do. 

Now, it has been a long time since I have done anything with OpenOffice. I use LibreOffice. Any reason for specifically using OpenOffice? I can't speak for OO, but if you go to the LibreOffice site, their installation instructions are pretty good as I remember. At least I have never had any trouble.

---

### Post by Lars Noodén on 2012-09-24
All that text shows that OOo installed correctly.  Now for the bad news:  Because these were not official Ubuntu packages, they were not integrated into your Desktop Environment's menus.  You must either do that manually or else run them from the terminal each time.  

Also, because they were not official Ubuntu packages you'll find your OpenOffice.org programs in a weird place, [font=Courier New]/opt/openoffice.org3/program/[/font]

You can launch OOo with the main program:

```

 /opt/openoffice.org3/program/soffice.bin 

```

Or you can launch the subcomponents individually by name: sbase, scalc, sdraw, simpress, smath, or swriter.

---

### Post by Jackalyn on 2012-09-24
> **Lars Noodén said:**
> All that text shows that OOo installed correctly.  Now for the bad news:  Because these were not official Ubuntu packages, they were not integrated into your Desktop Environment's menus.  You must either do that manually or else run them from the terminal each time.  

Ah now I understand. Some things are 'official'.......ok that is not too bad if it wwill run from the terminal. So that just means I save some code? Oh then does that also mean the same for calligra author as I also have all the files for that?

Also, because they were not official Ubuntu packages you'll find your OpenOffice.org programs in a weird place, [FONT=Courier New]/opt/openoffice.org3/program/[/FONT]

I typed that into the terminal and got 

[FONT=Courier New]jacky@jacky-Aspire-6930G:~$ /opt/openoffice.org3/program/
bash: /opt/openoffice.org3/program/: Is a directory
jacky@jacky-Aspire-6930G:~$ ^C

[/FONT]

You can launch OOo with the main program:

```

 /opt/openoffice.org3/program/soffice.bin 

```Or you can launch the subcomponents individually by name: sbase, scalc, sdraw, simpress, smath, or swriter.

WOOOOOOOOOOOOOOOOOOOOOOOOO!!!!!!!!!!!!!!!!!!!!!!  That worked!!!!! 

So hopefully we could draw out these elements and put it out there for the other people who have asked as I have seen other posts?

OK so for calligra...presumably the same process.....now let me try 

```

 /opt/calligra-latest/program/calligra.bin 

```

Nope that is not it....

I again have the files

intrepo.sh which stands alone and somewhere it said I need to run it. 
and [code]
 /calligra/git and lots of folders

---

### Post by Jackalyn on 2012-09-24
> **agillator said:**
> OK, open a command terminal (you obviously have learned how to do that), change to the directory you want the listing for, and type 'ls -l' without the quotes.  That will give you a listing of the files in that directory as well as a lot of other information. The information you are looking for will be toward the left, the permissions, which will be a series of dashes and/or letters. Don't worry about the first (probably a -, could be a 'd' or something else), look at the next nine. They should be read in groups of three. The first position should be a dash or an r for read, then a dash or a w for write and then a dash or an x for execute. The first group of three is for the owner of the file, the second group is for members of the file's group and the third is for everyone else. The dash means they do NOT have that permission, the letter means they do. 

Now, it has been a long time since I have done anything with OpenOffice. I use LibreOffice. Any reason for specifically using OpenOffice? I can't speak for OO, but if you go to the LibreOffice site, their installation instructions are pretty good as I remember. At least I have never had any trouble.

I do have libre...just found it was not always taking the add on for readability which is invaluable to me for lost of reasons and also just found it easier to install that particular add on in O.O. Ethically, i prefer libre.......I just hate Microsoft Office as a program and dislike monopolies.  I have never wanted or liked using Word although did get that part of the European Computer Driver's Licence once. It was enough to tell me it was not for me even if I could use it.

My other reason is that although some editors for books understand and work with open office they get a bit phased by my mentioning libre. 

I have been looking at Calligra but so far as I can see, it is not going to be better than OO or libre. I cannot see any improvement as a whole but still wanted to take a closer look.

 I think probably it is time to start working on making a really functional set of toolbars for either libre or open office that work for my books.

 Each author will have some pretty different needs I think.  LOL I end up with more tool bars than writing space if I am not careful!

 Basically I like the concept of an author package that goes through from first draft to publishing. An integrated ebook maker is a wonderful idea but people do not realise that it is not as simple as converting what you write by the touch of a button.

You can really get all you need now, but have to build your own package as it were by using add ons and new toolbars. It takes time and I guess what is really needed it a ready made package in libre or OO for this. 

Ideally it would come with some templates for both books and magazines incorporated and a cover maker...............Talking to people in the publishing world there is a lot that gives away a book as a self-published attempt apart from the face they are often poorly edited........A program that had things set up with everything to publisher standard would be a gift from heaven but it is quite hard to set things right. 

Hence, I wanted to see what author did in Calligra.....Most of us are just not savvy enough to use some of the programs out there and need an easy set up but a lot of us write......

Anyway thanks for this morning because I feel now like I have started to get what I want downloaded. 

:P:P:P:P:P

---

### Post by Lars Noodén on 2012-09-24
> **Jackalyn said:**
> WOOOOOOOOOOOOOOOOOOOOOOOOO!!!!!!!!!!!!!!!!!!!!!!  That worked!!!!!

Excellent.  You can even link an icon or menu item to it now that you have it.

Keep in mind that since you installed manually, you will also have to update manually when the occasion arises.  It is  basically the same process. 

If your next adventure will be [Calligra](apt://calligra), might I recommend using the package manager (either Synaptic or the Software Center) so that all those things will happen automatically?

---

### Post by Jackalyn on 2012-09-24
> **agillator said:**
> OK, open a command terminal (you obviously have learned how to do that), change to the directory you want the listing for, and type 'ls -l' without the quotes.  That will give you a listing of the files in that directory as well as a lot of other information. The information you are looking for will be toward the left, the permissions, which will be a series of dashes and/or letters. Don't worry about the first (probably a -, could be a 'd' or something else), look at the next nine. They should be read in groups of three. The first position should be a dash or an r for read, then a dash or a w for write and then a dash or an x for execute. The first group of three is for the owner of the file, the second group is for members of the file's group and the third is for everyone else. The dash means they do NOT have that permission, the letter means they do. 

Now, it has been a long time since I have done anything with OpenOffice. I use LibreOffice. Any reason for specifically using OpenOffice? I can't speak for OO, but if you go to the LibreOffice site, their installation instructions are pretty good as I remember. At least I have never had any trouble.

And yes, eventually libre was easy to install.

---

