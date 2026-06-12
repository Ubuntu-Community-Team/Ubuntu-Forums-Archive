---
title: "Tips &amp; Tricks: Simple APT Tips for Ubuntu"
date: 2010-09-14
forum: Outdated Tutorials &amp; Tips
---

### Post by Christmas on 2010-09-14
*This is a collection of tips I initially published a while ago on my blog, [**here**]("http://tuxarena.blogspot.com/2008/10/5-simple-apt-tricks-for-debian-and.html") and [**here**]("http://tuxarena.blogspot.com/2008/07/5-simple-apt-tips-for-debian-and-ubuntu.html") (divided in two different articles).*

**View all the packages installed on a system**
The easiest way to do it is:

```
dpkg --get-selections
```

It does not require to be root, and will display all the packages installed via APT. For example, the first lines may look something like:

```
$ dpkg --get-selections | head
acetoneiso2                                     install
acidrip                                         install
acpi-support-base                               install
acpid                                           install
adduser                                         install
akregator                                       install
alien                                           install
alsa-base                                       install
alsa-oss                                        install
alsa-utils                                      install
```

You can also put the entire list in a text file by redirecting the output, like this:

```
dpkg --get-selections > installed_packages.txt
```

Then read this file with a text editor or using less installed_packages.txt.

**List files which get installed by a package**
-L is a handy parameter to dpkg which will show you what files a package will install.

```
dpkg -L package_name
```

For example:

```
dpkg -L amarok
```

Will show all the files which are going to be installed by package amarok. You don't have to be root to run it.

**Upgrade your system using a one-liner**
Type as root:

```
apt-get update && apt-get dist-upgrade
```

This command will update your list of packages, and if its return status is successful, it will proceed to the next command, apt-get dist-upgrade, which will upgrade all of your packages and will install new dependencies if needed. Use dist-upgrade when you want all of your packages to be installed, and no package left as being kept back.

**Install the dependencies of an application**
Sometimes you need to compile from source a newer version of an application which is already included in the repositories. For example, to install the development libraries for BasKet, you would run as root:

```
apt-get build-dep basket
```

And then you can proceed to compile your application. Note that sometimes newer versions of applications may depend on newer libraries or other packages than you do not have in the repositories, so this won't always work.

**Remove unused package files**
When you install software using APT, the DEB packages are kept inside the /var/cache/apt/archives directory. In time, the size of it could get very large. To see what is the size of that directory, you can use:

```
$ du -h /var/cache/apt/archives/
4.0K    /var/cache/apt/archives/partial
956M    /var/cache/apt/archives/
```

In order to clean up all these packages you can use, as root:

```
apt-get clean
```

This command will remove all the packages except files which are locked. There is another command, apt-get autoclean, which will remove all the packages which are no longer available in the repository (older versions of packages which can't be downloaded any more).

Notice: I specified which commands need root privileges. In Debian, type su, followed by your root password, while in Ubuntu just precede each command which needs root privileges with sudo. Notice that by default there is no feedback when entering the password, so you won't be able to see it, but it goes in. Just press Enter when you're done.

**Add repositories from a CD or DVD**
If you need an offline repository for packages, you can download all the ISO images for your distribution, eventually burn them on CDs/DVDs and add them manually to the /etc/apt/sources.list file using apt-cdrom (as root):

```
apt-cdrom add
```

Enter the CD/DVD in the drive and let APT scan for packages.

Another great solution is to not even burn the ISO images to CD, just mount them and add them to your sources.list this way. Here's what you have to do:

First, type:

```
apt-cdrom -d=/cdrom add
```

Or replace /cdrom with some empty directory of your choice, that's where the ISO images will be mounted. I use here /mnt/iso0, /mnt/iso1 etc. Just make sure the directory is empty. The output of the above command looks something like this:

```
# apt-cdrom -d=/cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
```

Now don't press Enter, instead open another terminal session and mount the image in that directory (as root):

```
mount -o loop /path/to/iso/file.iso /cdrom
```

Then return to the shell where you started apt-cdrom and press Enter. It should scan the directory where the ISO image was mounted. I'm not very sure this is the only method, but this worked very well for me. If you mount the ISO the first time and then execute apt-cdrom, it first umounts it and then it fails with the message E: Failed to mount the cdrom.

**Use dpkg -S to search for a specific file**
dpkg -S filename will search for filename in all the packages available and return all the packages which have a file (or the path to that file) with the same name. Notice that the name can also be included in the found files. For example, typing dpkg -S bash will return all the packages which contain the name 'bash' in their files, including mybashburn, bash and several other packages. On the other hand, searching for dpkg -S /bin/bash will only return package bash, since dpkg will match the whole path to the bash binary.

**Use apt-file to search for files in packages**
This is a tool which creates a cache with info about all the packages available in the repositories, and it allows to search for specific files in a package and show what files a package will install (including packages which are not already installed). To get it, type as root:

```
sudo apt-get install apt-file
```

Next, update its cache:

```
sudo apt-file update
```

Use it like this:

```
apt-file search filename
```

Or:

```
apt-file search file_path
```

This will also return paths which include the name file_path. To show what files a package will install, use:

```
apt-file show package_name
```

Here's a more comprehensive tutorial I wrote a while ago about apt-file.

**Remove unnecessary packages**
This was a feature which existed for while in aptitude, but not in apt. Once you remove an application, it may be possible that some libraries on which that application depended to remain installed in the system. In order to get rid of those too, use:

```
apt-get autoremove --purge
```

Notice that this command will only remove packages which are not needed any more by some other application or that are not marked as 'installed manually'. This means packages which you did not specifically installed yourself.

**List files in a package**
Just use dpkg -L package_name for this one. Example:

```
dpkg -L amarok
dpkg -L bash
...
```

This will list all the packages installed by the respective package. Notice that it won't list anything if the specified package is not installed.

Hope this will be useful. Have some more, or maybe something wrong in the article? Please share other APT-related tips and tricks in the comments below.

---

### Post by dmizer on 2010-09-22
Courtesy bump. Thanks for posting this.

---

