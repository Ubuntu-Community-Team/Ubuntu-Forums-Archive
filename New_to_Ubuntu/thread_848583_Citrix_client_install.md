---
title: "Citrix client install"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by bharper34 on 2008-07-03
I am trying to install the citrix client onto Edubuntu but cannot get past the first step suggested by many of the older posts out there.  I tried to follow the instructions on the following site ([http://michaeljaylissner.com/blog/install-citrix-in-ubuntu-hardy-heron](http://michaeljaylissner.com/blog/install-citrix-in-ubuntu-hardy-heron)), but failed...I am extremely new to Linux with no programming background...Please help.

Below is the error message I get...It may or may not be important to note that I have no CD drive, but do have a flash drive that I can use to as an external device.


demo@demo-laptop:~$ tar -zxvf en.linuxx86.tar.gz
tar: en.linuxx86.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

### Post by bharper34 on 2008-07-03
Okay so now I have tried a new way to install and got to the last step before getting the following error message...Please look at the link and then at my last terminal message...Thank you.

[http://keystoneit.wordpress.com/2006/03/21/citrix-client-install-for-ubuntu/](http://keystoneit.wordpress.com/2006/03/21/citrix-client-install-for-ubuntu/)

demo@demo-laptop:~/Desktop$ sudo ln -s /usr/lib/ICAClient/npica.so /usr/lib/mozilla-firefox/plugins/npica.so
ln: creating symbolic link `/usr/lib/mozilla-firefox/plugins/npica.so': No such file or directory
demo@demo-laptop:~/Desktop$

---

### Post by milosz.galazka on 2008-07-03
Hello,

I am using citrix client too.
I just unpacked *en.linuxx86.tar.gz* and I am just using *wfica* (*linuxx86/linuxx86.cor/wfica*) to open *citrix* files from firefox.

Maybe you need to link/copy file from:
*linuxx86/linuxx86.cor/npica.so*

---

### Post by avtolle on 2008-07-03
Thinking out loud: cd /usr/lib/mozilla-firefox/plugins
mkdir npica.so

then retry the symbolic link.

---

### Post by cariboo on 2008-07-03
IF you are using version 8.04 there is no /usr/lib/mozilla-firefox it should be /usr/lib/mozilla/plugins or /usr/lib/firefox/plugins

Jim

---

### Post by bharper34 on 2008-07-03
> **cariboo907 said:**
> IF you are using version 8.04 there is no /usr/lib/mozilla-firefox it should be /usr/lib/mozilla/plugins or /usr/lib/firefox/plugins

Jim

Jim,

Thank you.  So that worked, but the last line did not allow for the Citrix Client to run porperly.  It is installed and I can track down the files, but I have no idea what to do next to enable it to work when I click on Citrix fed icon on the desktop.  Any ideas?

Thanks again for the help.

---

### Post by bharper34 on 2008-07-05
So, the client is installed, but I still do not have ICA functionality...I get a message asking me what to use to open the ICA file...any ideas on how to get this working?

---

### Post by crjackson on 2008-07-19
> **bharper34 said:**
> So, the client is installed, but I still do not have ICA functionality...I get a message asking me what to use to open the ICA file...any ideas on how to get this working?

I actually downloaded the rpm file and converted it to a deb.  Now I get the exact same message as you.  Is there anyway to get a citrix webapp to work under Ubuntu at all.  I just installed 8.04 on my bosses machine and he is about to have a cow about this.

Now I've had to make it a dual boot machine just because of this citrix issue.  He wants to kill windows all the way but it can't be done I guess.

---

### Post by crjackson on 2008-07-20
Well, I've got it working perfectly.

It seems that I should have just downloaded the tarball and installed using the included script, rather than converting the rpm to a deb.

I ran the script and installed and viola.  It works perfectly.

---

### Post by rahmath on 2008-08-01
This note is prepared for our team... have a look at it.. it is straight to the task... Hope this will help u...



HOWTO: Citrix ICA Client Installation on Linux Box
Date: 22/07/2008
Author: Rahmathulla K M
Linux Admin
IT Department


Introduction
------------

This HOWTO defines the easy procedures to perform a successfull installation of Citrix ICA Client on Linux Box. Practically i had done this only on Ubuntu 8.04. But accroding to my experience, most probably this procedure should work with many of the other distribution as in the same way.

Downloading ICA
---------------
Citrix ICA Client is free to download from Citrix website. Current version of ICA client can be downloaded from [http://download2.citrix.com/FILES/en...inuxx86.tar.gz](http://download2.citrix.com/FILES/en...inuxx86.tar.gz)

Installation - A,b,c...
------------

Once you compelte the download, you will have a file called en.linuxx86.tar.gz in your local hard disk. Keep in your mind that this is a zipped archive file (in this file name, the .gz specifies that its a gzipped file and the .tar specifies that its a tape archive file).

So its always better to do the extraction and other installation related activities from a temporary directory, so that if something goes wrong, we can
easily delete the entire directory without causing any problem to our working environment

Right now, i am in my home directory --> /home/kmr (and our downloaded file is in my home directory --> /home/kmr/en.linuxx86.tar.gz

So create a directory called citrix (it can be any name) in the /tmp
$ mkdir /tmp/citrix

Then copy our dowloaded package file to this newly created directory
$ cp en.linuxx86.tar.gz /tmp/citrix

Now unpack the zipped file
kmr@KMRLapBEM:~$ cd /tmp/citrix/
kmr@KMRLapBEM:/tmp/citrix$
kmr@KMRLapBEM:/tmp/citrix$ ls
en.linuxx86.tar.gz
kmr@KMRLapBEM:/tmp/citrix$ gunzip en.linuxx86.tar.gz

Now if you run 'ls' command on /tmp/citrix, you will see the pacakge file which is extracted, without the .gz extension
kmr@KMRLapBEM:/tmp/citrix$ ls
en.linuxx86.tar
kmr@KMRLapBEM:/tmp/citrix$

Next is to unpack the archive with 'tar' command
kmr@KMRLapBEM:/tmp/citrix$ tar xf en.linuxx86.tar
kmr@KMRLapBEM:/tmp/citrix$ ls
en.linuxx86.tar eula.txt install.txt linuxx86 PkgId readme.txt setupwfc
kmr@KMRLapBEM:/tmp/citrix$

note that, few more files and directories and files are in place after the successfull extraction from the tape archive

Now run the installation script with 'sudo'
kmr@KMRLapBEM:/tmp/citrix$ sudo ./setupwfc

Answer the questions prompted during installation. When it prompts for install directory, go with the default location (/usr/lib/ICAClient) itself. But when it prompts for "Integrate Citrix Automatically", say NO. We will do it manually.

Now the installation is over, and its the time to place a link on our desktop for an easy access to our citrix server.

Required Dependencies
---------------------

In order to go further, we need 3 dependent packages to run our Citrix client. So, now we are going to install those dependencies.

kmr@KMRLapBEM:~$ sudo aptitude install menu motif-clients libmotif3

This command will install those 3 dependencies.

Creating Desktop Link
---------------------

For this, go to your 'Desktop' directory in your home directory.
kmr@KMRLapBEM:~$ cd Desktop
kmr@KMRLapBEM:~/Desktop$ pwd
/home/kmr/Desktop
kmr@KMRLapBEM:~/Desktop$

Then run the following command;
kmr@KMRLapBEM:~/Desktop$ ln -s /usr/lib/ICAClient/wfcmgr citrix-client
kmr@KMRLapBEM:~/Desktop$ ls
citrix-client
kmr@KMRLapBEM:~/Desktop$

Thats all!!! Alhamdulillahhh, things are configured and now you can just double click on the 'citrix-client' icon shown in your desktop.

Conclusion
----------

The document is prepared straight to the point. So you will find it easy for installation but at the same time, this will not save you in troubleshooting
this procedures. So if anything goes wrong, or if you are in need of a supportive hand, please feel free to post here...

---

