---
title: "apt-get  sources.list file configuration for RTEMS"
date: 2013-10-07
forum: New to Ubuntu
---

### Post by daveerickson2 on 2013-10-07
Hello;
I'm not new to Linux, I'm a Fedora user but I'd like to start ubuntu.

I'm having problems with the apt-get config file sources.list configuration.
I want to install RTEMS build tools and I don't know how to explain where to find the files to apt-get:

Here is the rtems.list file I made:

> deb [http://www.rtems.org/ftp/pub/rtems/linux/4.11/ubuntu/dists/squeeze/rtems4.11/binary-amd64/](http://www.rtems.org/ftp/pub/rtems/linux/4.11/ubuntu/dists/squeeze/rtems4.11/binary-amd64/) /

Now the Release file is located at [http://www.rtems.org/ftp/pub/rtems/linux/4.11/ubuntu/dists/raring/rtems4.11/binary-amd64/](http://www.rtems.org/ftp/pub/rtems/linux/4.11/ubuntu/dists/raring/rtems4.11/binary-amd64/)

And the tool files are located at: [http://www.rtems.org/ftp/pub/rtems/linux/4.11/ubuntu/pool/rtems4.11/r/](http://www.rtems.org/ftp/pub/rtems/linux/4.11/ubuntu/pool/rtems4.11/r/)
is subfolders like [http://www.rtems.org/ftp/pub/rtems/linux/4.11/ubuntu/pool/rtems4.11/r/rtems-4.11-autoconf/](http://www.rtems.org/ftp/pub/rtems/linux/4.11/ubuntu/pool/rtems4.11/r/rtems-4.11-autoconf/)
and so on,

So, how do I format the file to compensate for that?

Thanks,

Dave

---

### Post by heir4c on 2013-10-07
Just to inform you:

There is a wrong word in the link of your rtems.list file that you made:
http: //www.rtems.org/ftp/pub/rtems/linux/4.11/ubuntu/dists/**squeeze**/rtems4.11/binary-amd64/
There is no squeeze distro in ubuntu. 
You write: ...the release file is located a: http: //www.rtems.org/ftp/pub/rtems/linux/4.11/ubuntu/dists/**raring**/rtems4.11/binary-amd64/
squeeze is here raring

---

### Post by daveerickson2 on 2013-10-07
Ok thanks;

I recopied it in as rtems-4.11.list  inside sources.list.d  as:

> deb [http://www.rtems.org/ftp/pub/rtems/linux/4.11/ubuntu/dists/raring/rtems4.11/binary-amd64](http://www.rtems.org/ftp/pub/rtems/linux/4.11/ubuntu/dists/raring/rtems4.11/binary-amd64)  /
deb [http://www.rtems.org/ftp/pub/rtems/linux/4.11/ubuntu/pool/rtems4.11/r](http://www.rtems.org/ftp/pub/rtems/linux/4.11/ubuntu/pool/rtems4.11/r)  /

and this was the output from apt-get install rtems-4.11-autoconf

:
> dave@fury:/tmp$ sudo apt-get install rtems-4.11-autoconf
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package rtems-4.11-autoconf
E: Couldn't find any package by regex 'rtems-4.11-autoconf'

This may also be pertinent that autoconf is located at:

[http://www.rtems.org/ftp/pub/rtems/linux/4.11/ubuntu/pool/rtems4.11/r/rtems-4.11-autoconf/](http://www.rtems.org/ftp/pub/rtems/linux/4.11/ubuntu/pool/rtems4.11/r/rtems-4.11-autoconf/)

so I added a line for [http://www.rtems.org/ftp/pub/rtems/linux/4.11/ubuntu/pool/rtems4.11/r](http://www.rtems.org/ftp/pub/rtems/linux/4.11/ubuntu/pool/rtems4.11/r)
as another source directory.

The RTEMS team did not make the conf.rpm they promised and maybe this is my problem?  If you could explain to me what the text entries are in a sources.list file I could help too.

NB
This is the entry from Packages inside ubuntu/dists/raring/rtems-4.11 folder:

"
Package: rtems-4.11-autoconf
Version: 2.69-1precise1
Architecture: all
Maintainer: Ralf Corsépius <ralf.corsepius@rtems.org>
Installed-Size: 2309
Depends: m4 (>= 1.4.13)
Homepage: [http://www.gnu.org/software/autoconf](http://www.gnu.org/software/autoconf)
Priority: extra
Section: rtems4.11
Filename: pool/rtems4.11/r/rtems-4.11-autoconf/rtems-4.11-autoconf_2.69-1precise1_all.deb
Size: 1036764
SHA256: d25919f32be76f0f8b7a053307c7705e8dfd0c9fb246651253b4068b8efe0bb3
SHA1: 8bdb6ce911841e0e0cea3d32243985dede33f691
MD5sum: d83e1726d463a617ca4459ecdb67be94
Description: Tool for automatically generating GNU style Makefile.ins
 GNU's Autoconf is a tool for configuring source code and Makefiles.
 Using Autoconf, programmers can create portable and configurable
 packages, since the person building the package is allowed to
 specify various configuration options.
 You should install Autoconf if you are developing software and you'd
 like to use it to create shell scripts which will configure your
 source code packages.
 Note that the Autoconf package is not required for the end user who
 may be configuring software with an Autoconf-generated script;
 Autoconf is only required for the generation of the scripts, not
 their use.
"
it says the file is at  
pool/rtems4.11/r/rtems-4.11-autoconf/rtems-4.11-autoconf_2.69-1precise1_all.deb

but that is outside the base folder.  Seems to me they made this convoluted...

Thanks for your reply.

Dave

---

### Post by heir4c on 2013-10-07
I don't know anything from that program and what you will do but this is important I expect. (I'm not a expert or something Just give a helping hand.)

I click the links for the packages and so I can see if it exist. So I could see that there was no files in and even don't exist, so removed some words in the address-bar so I came on the right page. 
Have you look on the site of RTEMS? There is a manual for Ubuntu. Maybe that help. (I search with Google with: RTEMS ubuntu )
[http://www.rtems.org/wiki/index.php/Building_the_RTEMS_toolset_on_Ubuntu](http://www.rtems.org/wiki/index.php/Building_the_RTEMS_toolset_on_Ubuntu)

You write something about .rpm, you can't use .rpm for Ubuntu, Ubuntu used .deb

---

