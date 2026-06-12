---
title: "How to Setup Bugzilla in Ubuntu 9"
date: 2010-02-02
forum: Outdated Tutorials &amp; Tips
---

### Post by anauj0101 on 2010-02-02
I have posted this due to the fact most walkthroughs on the subject are lacking

**1. Perl**
  Verify Perl is installed
      $ perl -v
  If not installed
      $ sudo apt-get install perl
  **2. MySQL**
  Verify MySQL is installed
      $ mysql --version
  If not installed
      $ sudo apt-get install mysql-client mysql-server mysql-admin
  **3. Create new user with strong password (used "bugzilla" here as example)**
      $ sudo useradd -d /home/bugzilla -m bugzilla
      $ sudo passwd bugzilla
  **4. Apache2**
  Verify Apache is installed
      $ apache2 -v
  If not installed
      $ sudo apt-get install apache2
  **5. Bugzilla**
  Download bugzilla from [http://www.bugzilla.org/](http://www.bugzilla.org/)
   Untar the file you downloaded
      $ sudo tar -xvf bugzilla-x.x.x.tar
  move to directory /usr/local/
      $ sudo mv /currentBugzillaLocation/bugzilla-x.x.x /usr/local/
  Make symbolic link from /usr/local/bugzilla-x.x.x to /var/www/bugzilla
      $ sudo ln -s /usr/local/bugzilla-x.x.x /var/www/bugzilla
  **6. Perl Modules**
  Verify all perl modules are installed
      $ cd /usr/local/bugzilla-x.x.x
      $ sudo ./checksetup.pl --check-modules
  If anything is missing
      $ cd /home/NewUserYouCreatedEarlier/
      $ sudo perl -MCPAN -e install
      $ cd /usr/local/bugzilla-x.x.x
  Then run the check for modules again, keep running until all required and optional modules are found
  **BE SURE TO EXCLUDE THE MODULES FOR THE 2 OTHER DATABASES THAT ARE NOT MYSQL!!**
       $ sudo ./checksetup.pl --check-modules
  At the end of the script it will give you a list of all mandatory and optional modules, the commands to install the modules are also listed at the end of the script.  If the commands do not work to install the intended modules, search the package manager to install what is missing.
  After all modules have been satisfied run checksetup.pl again with no arguments
       $ sudo ./checksetup.pl
  It will fail, this is ok
  **7. Configure bugzilla**
  Edit the "localconfig" file
      $ sudo gedit localconfig
  Change $webservergroup to the group the web server will run under (here we will use "apache2")
      ex. $webservergroup = 'apache2';
  Change $db_name to the name of the database you want to use (here we will use "bugs")
   Change $db_user to the user name we created earlier ("bugzilla" that we created above)
  Change db_pass to the password you set for the new user name you created earlier
  **8. Configure MySQL**
      $ mysql -u root -p
  Create database that you specified in "localconfig"
      mysql> create database bugs;
  Grant all privileges on "bugs" to user name we created earlier
      mysql> grant all privileges on bugs.* to bugzilla@localhost;
      mysql> quit
   **9. Finish install of Bugzilla**
      $ sudo ./checksetup.pl
  **10. Additional security measures**
  Create user "apache2" (this is a user who will be in the webserver group we setup earlier in the "localconfig")
      $ sudo useradd -d /home/apache2 -m apache2
      $ sudo passwd apache2
  Edit /etc/apache2/envvars
      $ sudo gedit /etc/apache2/envvars
  Add the lines  (APACHE_RUN_USER is the user you created in the step above, and APACHE_RUN_GROUP is the group you set in $webservergroup in localconfig)
       export APACHE_RUN_USER=apache2
      export APACHE_RUN_GROUP=apache2
  Re-run checksetup.pl
      $ sudo ./checksetup.pl
  Restart Apache2
      $ sudo /etc/init.d/apache2 restart
  **11. Start using Bugzilla**
      [http://localhost/bugzilla/](http://localhost/bugzilla/)

---

### Post by arul33 on 2011-07-04
Hi Anauj0101,
currently i'm trying to install bugzilla 3.6.5 in my system with ubuntu 10.10 OS, ur setup instruction works almost 80% there but after step 8 i.e configure MySQL i ran sudo ./checksetup.pl in order complete bugzilla setup and i receive following error and the bugzilla page doest work.

[COLOR=Red]COMMANDS TO INSTALL OPTIONAL MODULES:

             GD: /usr/bin/perl install-module.pl GD
          Chart: /usr/bin/perl install-module.pl Chart::Lines
    Template-GD: /usr/bin/perl install-module.pl Template:lugin::GD::Image
     GDTextUtil: /usr/bin/perl install-module.pl GD::Text
        GDGraph: /usr/bin/perl install-module.pl GD::Graph
       mod_perl: /usr/bin/perl install-module.pl mod_perl2[/COLOR]


To attempt an automatic install of every required and optional module
with one command, do:

  /usr/bin/perl install-module.pl --all

Reading ./localconfig...

OPTIONAL NOTE: If you want to be able to use the 'difference between two
patches' feature of Bugzilla (which requires the PatchReader Perl module
as well), you should install patchutils from:

    [http://cyberelk.net/tim/patchutils/](http://cyberelk.net/tim/patchutils/)

Checking for           DBD-mysql (v4.00)   ok: found v4.016 
There was an error connecting to MySQL:

    Access denied for user 'bugzilla'@'localhost' (using password: YES)

[COLOR=Red]This might have several reasons:

* MySQL is not running.
* MySQL is running, but there is a problem either in the
  server configuration or the database access rights. Read the Bugzilla
  Guide in the doc directory. The section about database configuration
  should help.
* Your password for the 'bugzilla' user, specified in $db_pass, is 
  incorrect, in './localconfig'.
* There is a subtle problem with Perl, DBI, or MySQL. Make
  sure all settings in './localconfig' are correct. If all else fails, set
  '$db_check' to 0.[/COLOR]

arul@arul-OptiPlex-960:/usr/local/bugzilla-3.6.5$

Do you any idea what went wrong? i really need some help and struggling with this installation almost 10 days without rest..

Thank You..

Best Rgds,
Arul.Nathan

---

