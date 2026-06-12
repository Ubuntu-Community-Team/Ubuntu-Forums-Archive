---
title: "PHP Expect Module Not Loading - Solved"
date: 2012-05-04
forum: Programming Talk
---

### Post by tgilber1 on 2012-05-04
Had an issue with Ubuntu 12.04 where the expect module was not loading, thereby causing PHP scripts programmed with expect function to fail with undefined function error messages.  The issue is with the libexpect.php5 package.  There is a download available from a ppa source - libexpect-php5 0.3.1-2ppa1 that fixed the issue for me.

Steps

1.  Check with the php command to see if expect.so module loaded

    php -m


You can also write a php file and populate the phpinfo() function to see what modules loaded, but the php -m from the CLI is quicker

2.  If step should show that the module failed to load due to the fact that it could not find libexpect.so.5.44.1.14 or some other version.  If not, then this post will probably not help

3.  Add the ppa source to get access to the latest libexpect.so code with the following commands

   sudo apt-add-repository ppa:coldfff/libexpect-php5;
   sudo apt-get update;
   sudo apt-get dselect-upgrade;

4.  Reload apache2

   sudo invoke-rc.d apache2 reload

5.  Re-run the "php -m" command via the CLI.  It will probably get a failed to load modules.  Copy the name of the libexpect-php5.so.xx.xx from the error message and issue the following command

   cd /usr/lib
   sudo ln -s libexpect.so.5.45 libexpect.so.5.44.1.14

   ##Note:  change the symbolic name (second argument) to whatever version is provided in error message.  Additionally the actual filename (1st argument should match what is installed in the filesystem.

6.  Reload apache2 one more time 

   sudo invoke-rc.d apache2 reload

7.  Check to see if php module is loaded

   php -m or phpinfo()


Lastly, to help with debugging php, issue a tail -f command on the apache error log file

  tail -f /var/log/apache2/error.log

Hope this helps!

---

