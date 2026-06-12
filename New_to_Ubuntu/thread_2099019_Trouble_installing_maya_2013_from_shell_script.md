---
title: "Trouble installing maya 2013 from shell script"
date: 2012-12-28
forum: New to Ubuntu
---

### Post by lee2912 on 2012-12-28
Hi everyone new to ubuntu and so far really enjoying it. Im have a problem installing maya 2013 ( I know it not officially supported but some people are using it on ubuntu). Ive found a shell script at [https://gist.github.com/3250500](https://gist.github.com/3250500) and opened this in my terminal and it downloads it but doesn't seem to install it. I've attached the a copy of what the terminal said. Please someone help as I've looked on the internet but found nothing. Thanks.

```
lee@lee-Amilo-Desktop-Pi3635A:~$ cd /home/lee/Downloads/gist3250500-ffabb562fae0e9354f5bc9d6ba5b61269e0368b8
lee@lee-Amilo-Desktop-Pi3635A:~/Downloads/gist3250500-ffabb562fae0e9354f5bc9d6ba5b61269e0368b8$ sh mayaOnUbuntu.sh
Please run this script using sudo
Just type &#8220;sudo !!&#8221;
lee@lee-Amilo-Desktop-Pi3635A:~/Downloads/gist3250500-ffabb562fae0e9354f5bc9d6ba5b61269e0368b8$ sudo !!
sudo sh mayaOnUbuntu.sh
[sudo] password for lee: 
mayaOnUbuntu.sh: 16: mayaOnUbuntu.sh: [uname: not found
You&#8217;re about to download and install Autodesk Maya 2013

Do you wish to continue [Y/n]?
y
If you have not already done so, you can get your serial number from: http://students.autodesk.com
Enter the serial number
(I entered my serial here)

mkdir: cannot create directory `/home/lee/mayaTempInstall': File exists
Creating mayaTempInstall folder

mayaOnUbuntu.sh: 54: cd: can't cd to /home/lee/MAYAINSTALL
--2012-12-28 12:44:12--  http://download.autodesk.com/us/maya/service_packs/Autodesk_Maya_2013_SP1_English_Linux_64bit.tgz
Resolving download.autodesk.com (download.autodesk.com)... 23.65.22.24, 23.65.22.8
Connecting to download.autodesk.com (download.autodesk.com)|23.65.22.24|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 798135468 (761M) [text/plain]
Saving to: `Autodesk_Maya_2013_SP1_English_Linux_64bit.tgz'

100%[=======================================================================================================>] 798,135,468 3.70M/s   in 3m 38s  

2012-12-28 12:47:50 (3.49 MB/s) - `Autodesk_Maya_2013_SP1_English_Linux_64bit.tgz' saved [798135468/798135468]

Reading package lists... Done
Building dependency tree       
Reading state information... Done
alien is already the newest version.
libaudiofile-dev is already the newest version.
ttf-liberation is already the newest version.
csh is already the newest version.
elfutils is already the newest version.
gamin is already the newest version.
libglw1-mesa is already the newest version.
libglw1-mesa-dev is already the newest version.
mesa-utils is already the newest version.
tcsh is already the newest version.
xfonts-100dpi is already the newest version.
xfonts-75dpi is already the newest version.
xfs is already the newest version.
xfstt is already the newest version.
ttf-mscorefonts-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  libasprintf0c2:i386 libgomp1:i386 linux-headers-3.5.0-17
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tar: /home/lee/MAYAINSTALL/Autodesk*.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
sudo: for: command not found
You must specify a file to convert.

Usage: alien [options] file [...]
  file [...]                Package file or files to convert.
  -d, --to-deb              Generate a Debian deb package (default).
     Enables these options:
       --patch=<patch>      Specify patch file to use instead of automatically
                            looking for patch in /var/lib/alien.
       --nopatch        Do not use patches.
       --anypatch           Use even old version os patches.
       -s, --single         Like --generate, but do not create .orig
                            directory.
       --fixperms           Munge/fix permissions and owners.
       --test               Test generated packages with lintian.
  -r, --to-rpm              Generate a Red Hat rpm package.
      --to-slp              Generate a Stampede slp package.
  -l, --to-lsb              Generate a LSB package.
  -t, --to-tgz              Generate a Slackware tgz package.
     Enables these options:
       --description=<desc> Specify package description.
       --version=<version>  Specify package version.
  -p, --to-pkg              Generate a Solaris pkg package.
  -i, --install             Install generated package.
  -g, --generate            Generate build tree, but do not build package.
  -c, --scripts             Include scripts in package.
  -v, --verbose             Display each command alien runs.
      --veryverbose         Be verbose, and also display output of run commands.
  -k, --keep-version        Do not change version of generated package.
      --bump=number         Increment package version by this number.
  -h, --help                Display this help message.
  -V, --version            Display alien's version number.

dpkg: error processing /home/lee/MAYAINSTALL/*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/lee/MAYAINSTALL/*.deb
mkdir: cannot create directory `/usr/tmp': File exists
mayaOnUbuntu.sh: 78: mayaOnUbuntu.sh: cannot create /usr/autodesk/maya2013-x64/bin/License.env: Directory nonexistent
mayaOnUbuntu.sh: 80: mayaOnUbuntu.sh: /usr/autodesk/maya2013-x64/bin/adlmreg: not found
/usr/lib/x86_64-linux-gnu/libssl.so.0.9.8 not found. Using Autodesk&#8217;s libssl
ln: failed to create symbolic link `/usr/autodesk/maya2013-x64/lib/libssl.so.6': No such file or directory
/usr/lib/x86_64-linux-gnu/libcrypto.so.0.9.8 not found. Using Autodesk&#8217;s libssl
ln: failed to create symbolic link `/usr/autodesk/maya2013-x64/lib/libcrypto.so.6': No such file or directory
ln: failed to create symbolic link `/usr/lib/libtiff.so.3': File exists
Installation Complete.

Start Maya Now?

```

---

### Post by matt_symes on 2012-12-29
Hi

You're not really doing anything wrong. The install script is full of bugs and is not working because of that.

Do you still need any help installing the software ?

Might i suggest not attaching tar,gz files into your post but posting the contents between code tags.

Kind regards

---

