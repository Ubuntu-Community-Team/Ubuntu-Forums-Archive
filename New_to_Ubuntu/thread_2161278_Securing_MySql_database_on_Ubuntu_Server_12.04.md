---
title: "Securing MySql database on Ubuntu Server 12.04"
date: 2013-07-10
forum: New to Ubuntu
---

### Post by dmitriano on 2013-07-10
Hi, experts!

I have [Ubuntu Server 12.04 with LEMP (Linux + Nginx + MySQL + PHP)]("http://developernote.com/2012/11/setting-up-shared-hosting-with-nginx-on-ubuntu-step-by-step-guide/") that hosts several websites in Joomla and WordPress. All the websites uses separate MySQL databases and some of this databases contains sensitive information like orders and customers so no one (but me) should be permitted to access this information. Currently my server located at a private residence and nobody can physically access it except me. I enabled SSH and FTP so I have a typical situation when everything is OK.

But let assume my server is physically located at some data center and data center workers (or somebody else) can theoretically do with it whatever they want: reboot, boot from a Live CD, reset root password, copy MySQL data files, etc. The obvious solution in this case is to encrypt the entire disk or root partition using a tool like TrueCrypt, but this approach has the following disadvantages (or questions because I did not investigate this well enough): 

[LIST=1]
[*]As far as I see I need to reinstall my Ubuntu and then migrate everything from the old system.
[*]It is not clear how to reboot Ubuntu with TrueCrypt remotely via SSH.
[/LIST]

So the question is what is the simplest way to protect my databases? Probably enctyptfs and/or a tool for database encryption could help? The [FONT=&quot]mandatory[/FONT] requirement is the ability to reboot the system remotely.

---

### Post by SeijiSensei on 2013-07-10
Any data center that would allow its employees to act in the manner you describe would be sued and quickly out of business.  I use virtual servers at [Linode]("http://www.linode.com/").  I have no worries about the behavior of its staff.

I have built applications that handled "patient health information" which must be encrypted under US Government rules (HIPAA).  I wrote algorithms in PHP to encrypt and decrypt the records as needed.  The data are first encrypted with AES256 then converted to a text string with MIME encoding before being written as a varchar field.  That gives me a database that can be dumped to plain-text using tools like mysqldump or pg_dump with no need to encrypt any file systems.

Adding that functionality to WordPress or Joomla would be a pain in the neck.  Are there any add-ons for these products that provide encryption services?

---

### Post by dmitriano on 2013-07-10
My Joomla 1.5 and VirtueMart 1.9 (Joomla plugin that manages orders and customers) do not allow this type of add-on. They access the database via PHP classes like JDatabase that theoretically could be hacked somehow, but looks like it is not a simplest way at least. Furthermore I going to run new Java site on Apache Tomcat so I need some encryption that does not depend on Web Server or CMS.

So, is there another way?

---

### Post by SeijiSensei on 2013-07-10
For MySQL, the minimum would be to encrypt /var/lib/mysql.  You'd probably want to put it on a [separate encrypted partition]("http://www.cyberciti.biz/hardware/howto-linux-hard-disk-encryption-with-luks-cryptsetup-command/").

---

### Post by dmitriano on 2013-07-18
It is a good idea.

I did something like this:

mkdir /usr/local/encrypted
mount -t ecryptfs /usr/local/encrypted /usr/local/encrypted
cd /usr/local/encrypted
mkdir mdf
chown mysql mdf
chgrp mysql mdf
chmod og-rwx mdf

and then I moved MySQL datafiles to mdf directory and even encrypted the swap by using ecryptfs-setup-swap command.

---

