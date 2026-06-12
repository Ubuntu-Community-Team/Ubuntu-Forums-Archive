---
title: "HOWTO: easy general server setup (LAMP, SVN, webmin, samba, multiple hard drives)"
date: 2007-04-23
forum: Outdated Tutorials &amp; Tips
---

### Post by jeremy12 on 2007-04-23
Ok i have had this page on my laptop for my own reference for a long time now but i decided with 7.04 i would finally put it up into the public view. any comments/suggestions are very welcome.

[COLOR="Blue"][I have also posted this on a external site HERE]("http://ww4.preytontech.net-a.googlepages.com/linuxserversetup")[/COLOR]

**Section 1 (Main Server):**

Install Ubuntu Linux web server, below is where you can get Ubuntu Linux server 7.04 (Feisty Fawn)

    [LIST]
[*][Download page]("http://www.ubuntu.com/getubuntu/download")
[/LIST]

Now you can go 2 ways, install Ubuntu desktop (this will give you a GUI) or install a command line only system

If you went the route of installing the GUI then follow these steps so it does not start every time the server does(unneeded system resources being used):

[LIST]
[*] click System/Administration/Services and unclick Graphical Logic Manager (gdm)
[*] reboot
[/LIST] 
Now to enter into your GUI login at the command line then simply type "startx"


**Section 2 (Enable all Repositories, and update your system)**

Run these at a command line

[LIST]
[*]sudo -i
[*]    sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
[*]    sudo apt-get update
[*]    sudo apt-get update (yes 2 times)
[*]    sudo apt-get upgrade
[*]    sudo apt-get install apache2 php5 mysql-server libapache2-mod-auth-mysql php5-mysql php5-gd
[/LIST]

run this command to install some additional programs, SSH, perl, openssl, if u want to use Webmin these are required

[LIST]
[*]sudo apt-get install ssh libmd5-perl libio-pty-perl libauthen-pam-perl libnet-ssleay-perl libpam-runtime openssl perl perl-modules
[/LIST]

**Section 3 (Windows Networking):**

Now we will update your system, and setup your sources.list file so you have access to all programs that are installable, type each of the following lines into the command prompt

[LIST]
[*]sudo apt-get install samba
[/LIST]

Now im not going to go into depth on how to setup Samba here the documentation and [This Page on Ubuntu Forums]("http://www.ubuntuforums.org/showthread.php?t=202605") will be more then enough (note: editing samba settings can be easier with webmin, even just editing the config file), the only thing ill go into is if you do not want to make everything shared (no login needed) under [global] set "security = share"

**Section 4 (Webmin, Web based server administration):**

Webmin could not be easier, as long as u installed perl, ssh, openssl back in step 2. At time of writing this the latest version is "1.310", if u want the latest version go to [webmin Site]("http://webmin.com/") and get the URL to download the .deb so once u figure out what u want At command line type

[LIST]
[*]wget [http://site.com/path/webmin.?????.deb](http://site.com/path/webmin.?????.deb)
      or
      wget [http://ww4.preytontech.net/webmin_1.310.deb](http://ww4.preytontech.net/webmin_1.310.deb)
[*]dpkg --install webmin.?????.deb
      or
      dpkg --install webmin_1.310.deb
[/LIST]

And you are done with webmin

**Section 5 (MySQL Setup):**

For this we need to set the root password and we will install phpmyadmin for easier administration of mysql, yes u can do it in webmin but i just see phpmyadmin as much better for this

    [LIST]
[*]sudo apt-get install phpmyadmin
[*]    sudo mysql -u root
[*]    SET PASSWORD FOR 'root'@'localhost' = PASSWORD('yourpassword');
[/LIST]/q 

**Section 6 (SVN Server):**

Svn server Installation:

    [LIST]
[*]sudo apt-get install subversion subversion-tools websvn
[/LIST]

Create a repository

[LIST]
[*]mkdir /svn/
[*]    mkdir /svn/MYREPOSITORYNAME -Repeat as necessary
[*]    svnadmin create /svn/MYREPOSITORYNAME
[/LIST]

Setup Users

[LIST]
[*]Edit the file "/svn/MYREPOSITORYNAME/conf/passwd" to contain:
[/LIST]

      [users]
      user1name = user1pass
      user2name = user2pass
      user3name = user3pass

Setup Access to repository

    [LIST]
[*]Edit file "/svn/MYREPOSITORYNAME/conf/svnserve.conf" to conatin:
[/LIST]

      [general]
      anon-access = read
      auth-access = write
      password-db = passwd
      realm = MY REPOSITORY NAME

General Information on connecting/submitting SVN can be found [here]("http://ww4.preytontech.net-a.googlepages.com/svnsetupandusageinstructions") the page refers to connecting and using Preytontech SVN but the basis of what it is saying stays the same(specifically note the bottom) to connect to your repository you would use "svn://IP-or-DOMAIN/svn/MYREPOSITORYNAME/"

**Section 7 (Multiple Hard drives):**

First off Format the hard drive with Ext3 (i will leave this up to you)

Now we need to see the Linux path to the Drive:

[LIST]
[*]sudo fdisk -l
[*]     for my system returned:

      Disk /dev/hda: 30.0 GB, 30020272128 bytes
      255 heads, 63 sectors/track, 3649 cylinders
      Units = cylinders of 16065 * 512 = 8225280 bytes

         Device Boot      Start         End      Blocks   Id  System
      /dev/hda1   *           1          31      248976   83  Linux
      /dev/hda2              32        3649    29061585    5  Extended
      /dev/hda5              32         124      746991   82  Linux swap / Solaris
      /dev/hda6             125        3649    28314531   8e  Linux LVM

      Disk /dev/hdb: 160.0 GB, 160041885696 bytes
      255 heads, 63 sectors/track, 19457 cylinders
      Units = cylinders of 16065 * 512 = 8225280 bytes

         Device Boot      Start         End      Blocks   Id  System
      /dev/hdb1               1       19457   156288321   83  Linux
[/LIST]


The part we need i made a little bit bigger "/dev/hdb1" 

So now create a mount point for that partition/drive:
[LIST]
[*]sudo mkdir /storage
[/LIST]

Then we will edit your /etc/fstab file, but first back it up:
[LIST]
[*]sudo cp /etc/fstab /etc/fstab_backup
[*]    sudo nano /etc/fstab
[/LIST]

Once in there, add in this line at the bottom:

[LIST]
[*]/dev/hdb1 /storage ext3 defaults 0 0
[/LIST]

Then save the modified fstab file (Control-X), confirm (Y), and exit (Enter).

Since we've made changes to the /etc/fstab file, we need to have Ubuntu acknowledge those changes:

[LIST]
[*]sudo mount -a
[/LIST]

And of course to pay back the source of this text: [http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux%20")

**Section 8 (Setting up FTP):**

This is to come once i play with setting up ftp more, if u want tho use "proftpd", I have not got this setup yet simply for the reason i have not had the need for FTP on my server as all info from PC's not on my network go into the SVN server then from there i have a cron job setup through webmin to export svn nightly. If you have any tips for this section let me know


Resources:
[LIST]
[*][http://rubbervir.us/projects/](http://rubbervir.us/projects/) - the ubuntu media server tutorials
[*][http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[*][http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)
[/LIST]


Basic installation/setup - no configuration just all the installation:
```
sudo -i

sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list

sudo apt-get update
sudo apt-get update
sudo apt-get upgrade

sudo apt-get install apache2 php5 mysql-server libapache2-mod-auth-mysql php5-mysql php5-gd

sudo apt-get install subversion websvn samba ssh libmd5-perl libio-pty-perl libauthen-pam-perl libnet-ssleay-perl libpam-runtime openssl perl perl-modules

sudo /etc/init.d/samba stop

wget http://path.com/path/webmin.deb

dpkg --install webmin.deb

sudo apt-get update
sudo apt-get upgrade

shutdown -r now

sudo mysql -u root
SET PASSWORD FOR 'root'@'localhost' = PASSWORD('yourpassword');
/q


```

---

### Post by rocknrolf77 on 2007-04-24
Loving the webmin gui to handle grub entrys. Just found it today, nice to have all that config in one place :)

---

### Post by twowheeler on 2007-05-02
Excellent!  I am loving this, thanks very much.

---

### Post by donheff on 2007-06-06
Can you use the update process to add the GUI to the server addition or do you need to download and upgrade from a CD?

---

### Post by donheff on 2007-06-06
Nevermind my post about a GUI.  I realized I should have started with a desktop install.  I am redoing it now.

---

### Post by bodhi.zazen on 2007-06-11
Nice How-to

This thread has been added to the UDSF wiki.

[Easy_Server](http://doc.gwos.org/index.php/Easy_Server)

If you do a major update to your how-to please send me a PM. Either I can teach you how to add to the wiki or I can try to maintain the wiki myself (as time allows), thank you.

Peace be with you,

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

