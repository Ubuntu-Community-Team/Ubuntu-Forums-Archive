---
title: "Ubuntu Server + remote access"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by Trevor-Stone on 2008-06-27
Hi all.
I’m new to ubuntu and all linux platforms. I just downloaded ubuntu server 8.04.
I would like to set the server up so I can have remote access from any where and on any ones computer I read a article on installing and setting up the server

[http://www.ubuntugeek.com/ubuntu-804-hardy-heron-lamp-server-setup.html](http://www.ubuntugeek.com/ubuntu-804-hardy-heron-lamp-server-setup.html)

It says I need to install 
(sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl) 
and them install webmin.

I under stand what I have to do but I got no idea on how to do it.
I need help from any one willing to help. I need some one to explain it to me like I’m a 2 year old. How do I download and install and what codes if any do u use??

I would love to one day never use Window Agane!!!! 

                               Thank you all:(

---

### Post by wormser on 2008-06-27
Welcome to Ubuntu!

That is the command.  The command *apt-get* downloads the software from the repository and installs it.  Read How to [Install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").  Have you opened the repositories yet?

```
sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl
```

---

### Post by UbuntuNerd on 2008-06-27
this guide is very good i used it when i first install my lamp server it also includes the desktop gui in case you are a beginer

Step 1: Install Ubuntu Server Edition with LAMP server components.

Download the disk image (*iso) for Ubuntu Server Edition (currently version 8.04 Hardy Heron) and burn it to a CD. Ensure that your BIOS is configured to boot from the CD-ROM drive. Restart with the Ubuntu disk in the drive and the machine should boot into the Ubuntu installation shell. If you would like to configure a static IP address, select F6 - Other Options and enter
netcfg/disable_dhcp=true

at the end of the options string, and the install script will prompt you for network information during the installation. Otherwise, the static IP must be configured post installation as per the second part of step 2 below, and your network will be automatically configured using DHCP (as long as DHCP is enabled on your router). In either scenario, you must enter a hostname when prompted.
As you work through the installation (most of which is self explanatory), you will also be prompted to select a partitioning method. The most straightforward method is &#8220;use entire disk&#8221;, which will format a drive of your choice before installing system files to it. Finally, you will be prompted to enter a full name and a short name for a non-administrator account (separate from root). After a few more trivial questions (like &#8220;What is your time zone?&#8221;), and a plethora of file copying, the install shell will ask you to select optional software to install. Select LAMP (using the arrow keys and spacebar). If you wish to install a name server as well, you may select DNS and follow the instructions of this post. You may also elect to install an OpenSSH server at this point and bypass the first component of step 3 below. After making selections, continue the installation by pressing enter. At some point, you will be prompted to enter a mysql root user password. If you wish, this password can be left blank for now.
Step 2: Enable root access and configure a static IP address.

After installation finishes and the system reboots, log in using the non-administrator account created during installation. (Note: my system hung after reboot and I had to press enter to get the login prompt.) The first thing you will probably want to do once you log in is set the root password (by default the password is left blank). To do so, type the following at the command prompt.
sudo passwd root

Since you are planning to use the machine as a web server, you will also need to specify a static IP address (if not already configured during the installation). To do so, you must edit the interfaces configuration file (use your favorite text editor; I use vi here).
sudo vi /etc/network/interfaces

If DHCP was enabled during installation, a chunk of this file should look like the following:
auto eth0
iface eth0 inet dhcp

Change dhcp to static and add the lines shown below. Of course you need to use your IP address, netmask, and gateway instead of mine.
auto eth0
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

You also need to specify the DNS server(s) in the resolv.conf file.
sudo vi /etc/resolv.conf

Replace the xxx.xxx.xxx.xxx in the nameserver xxx.xxx.xxx.xxx line with the address of your DNS server. You can add multiple DNS servers if you like by duplicating this line using other DNS server addresses. Now restart your network components.
sudo /etc/init.d/networking restart

Ping [www.zaphu.com](www.zaphu.com) (or some weblog of lesser quality) to make sure your network configuration is working.
Step 3: Install OpenSSH and Ubuntu Desktop components.

If you didn&#8217;t do so during the installation, you will probably want to install an SSH server at this point so you can login to your new LAMP server from other machines on your local area network. Installing packages is a snap with Ubuntu using the built in aptitude package management software. The first step is to update the packages database by typing
sudo aptitude update

Then install the openssh-server package.
sudo aptitude install openssh-server

You need to insert the Ubuntu Server installation disk to complete the installation. Installation of the Ubuntu desktop environment (and all of the goodies that go with it) is also a snap using aptitude. Type
sudo aptitude update
sudo aptitude install ubuntu-desktop

Because a significant number of files need to be downloaded, the Ubuntu GUI installation may take some time. Near the middle of the installation you will be asked to configure the Postfix mail transfer agent. Since my machine is not going to be a mail server I selected &#8216;no configuration&#8217; and continued, but you may want to configure Postfix differently. Check out Ubuntu Forums for information on configuring Postfix. When the Ubuntu desktop installation finishes, fire up the GUI.
sudo /etc/init.d/gdm start

---

### Post by UbuntuNerd on 2008-06-27
hope it works for you i know it did for me just take your time!!!



In a previous post, I shared step-by-step instructions for setting up a Ubuntu LAMP (Linux, Apache, mySQL, PHP) server on your local area network (LAN). I also showed how you could customize the server installation to include all of the niceties of Ubuntu’s Desktop GUI. If this installation was successful, you should be able to view the default site served by Apache (actually an index of the default site) using any machine on your LAN. Type the server’s IP address (or alias if you added the server to your /etc/hosts file) in your browser’s address bar or, if you are browsing on the server itself, type 127.0.0.1 or localhost. If an error occurs, then you will have to edit the apache2.conf file to ensure that Apache can fully resolve the server’s name. Out of good measure you should do this anyway, even if everything seems to be working. Use your favorite text editing program (I use vi here) and open the file.
sudo vi /etc/apache2/apache2.conf

Add the following line somewhere:
ServerName localhost

and restart Apache.
sudo /etc/init.d/apache2 restart

If the default site loads then you are ready to configure Apache to serve your own sites. This configuration process may not be familiar to you if someone else hosts your websites. Here I walk you through the necessary steps. Additionally, I show you how to install phpMyAdmin to administer mySQL databases and how to configure a cgi-bin directory to run CGI programs.




Step 1: Create a new Apache site

To create a new site, first create a directory where you want to keep files associated with this site. I like to keep sites in my home directory so (using my user name of sam) I create a /home/sam/public_html directory. The configuration files for all sites available to Apache are stored in the /etc/apache2/sites-available/ directory. Create a configuration file for your new site (here called zaphu) by copying the configuration file for the default site.
sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/zaphu

Open the new configuration file.
sudo vi /etc/apache2/sites-available/zaphu

You will notice that there is a lot of stuff between <VirtualHost> tags. You have to edit some of this. Change the DocumentRoot path to point to the newly created site directory.
DocumentRoot /home/sam/public_html

In a similar fashion, change one of the Directory directives (it looks something like this)
<Directory /var/www/>

to be consistent with your site path.
<Directory /home/sam/public_html/>

After making these changes, disable the default site using the Apache disable site script.
sudo a2dissite default

Next, use the Apache enable site script to activate the new site.
sudo a2ensite zaphu

Finally, restart Apache.
sudo /etc/init.d/apache2 restart

Create a simple index.html file and save it in /home/sam/public_html/ to test your new site. Something simple like
<html>
<strong>Ubuntu Hardy Heron is Here</strong>

Browse (preferable on another machine) to your new site to test the configuration.
Step 2: Install phpmyadmin and create root mySQL user

In order to make mySQL database administration easy, many hosts provide phpMyAdmin. You can easily install this tool on your Ubuntu LAMP server too using the built in package management software. At the command prompt type
sudo aptitude update
sudo aptitude install phpmyadmin

You will have to insert the Ubuntu install CD to complete this installation. During the installation the script will ask which version of Apache to automatically configure. If you installed apache as per this previous post then select apache2 (with space bar) and continue. After the install completes, the phpMyAdmin script should be in the /usr/share/directory and (after restarting Apache; see above) it should resolve in your browser when you type localhost/phpmyadmin (or xxx.xxx.xxx.xxx/phpmyadmin). If it doesn’t, you must add the following alias and include to the bottom of the apache configuration file apache2.conf in /etc/apache2/.
Include /etc/phpmyadmin/apache.conf
Alias /phpmyadmin /usr/share/phpmyadmin

You can log in by using root as your username and the root password configured during the mySQL installation (if you decided not to enter a mySQL password or were not prompted for a password then the password field is blank by default). Once logged on to phpMyAdmin, you can set a new root password by navigating to the privileges page, clicking the icon that looks like a pencil next to each root account (there may be more than one), and entering a password in the appropriate field of the page that loads.
Step 3: Configure a cgi-bin directory

Configuring Apache to allow CGI program execution is pretty easy. Create a directory to be used for CGI programs (here I create /home/sam/public_html/cgi-bin) and add the following to the site configuration file (again between the <VirtualHost> tags).
ScriptAlias /cgi-bin/ /home/sam/public_html/cgi-bin/
<Directory /home/sam/public_html/cgi-bin/>
          Options ExecCGI
          AddHandler cgi-script cgi pl
</Directory>

The first line creates an alias that points to the directory in which CGI scripts are stored. The final line tells Apache that only files that end with the *.cgi and *.pl extensions should be considered CGI programs and executed.

Congratulations! Your new site is configured. It is worth mentioning that if you are going to be granting computers on the wide area network access to your new Ubuntu LAMP server, you should take some time to learn how to properly secure Apache. Check out these other sites for more information on configuring Apache under Ubuntu. Ubuntu Community, Apache2.2 Documentation

---

### Post by Trevor-Stone on 2008-06-27
Thank you for the welcome:)

Repositories. No I just googled it to see what it is( lol ) ill read up on it 

Hmmmmmmmmm If that is the code now you got me thinking….Did I have a internet connection I no I was plugged in.

Thanks for your help and ill check out that website and do a bit more reading
Ill post how I went.

So in basic words ( for my sake )when I log into the server I just copy and past 

( sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl )

and it should work??

                                                                                                   Thanks

---

### Post by Trevor-Stone on 2008-06-27
wow thank you very much!

Yeah im very new to ubuntu. Thanks again for your help and ill post how I go 


                                                                     
:):):)

---

### Post by UbuntuNerd on 2008-06-27
your welcome im also new to ubuntu but you'll find out that once you get it running right is way better than windows

---

### Post by wormser on 2008-06-27
> **Trevor-Stone said:**
> Thank you for the welcome:)

Repositories. No I just googled it to see what it is( lol ) ill read up on it 

Hmmmmmmmmm If that is the code now you got me thinking&#8230;.Did I have a internet connection I no I was plugged in.

Thanks for your help and ill check out that website and do a bit more reading
Ill post how I went.

So in basic words ( for my sake )when I log into the server I just copy and past 

( sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl )

and it should work??

                                                                                                   Thanks

The repositories have to be opened before you can install software.  By default I believe the server repositories are closed by default.

```
sudo nano /etc/apt/sources.list
```Comment out the CDrom by putting # infront of the CDrom line.  Next uncomment out the Universe and Multiverse lines.  More [here]("https://help.ubuntu.com/community/Repositories/CommandLine").  Save the file and run:

```
sudo apt-get update
```Now you can use that command to install the software.

---

### Post by Trevor-Stone on 2008-06-28
Yeah as like everyone I started with windows. And more I get to now about windows and how Microsoft don’t give two stuffs about us I cant weight for the day I’m windows free.

I’m installing ubuntu server as we speak ill let you all no how I go soon.

---

### Post by hyper_ch on 2008-06-28
how do you want to access the server?

---

### Post by Trevor-Stone on 2008-06-28
Legends its up and running 

Thank you all very much I printed out your notes and I’ll keep them its time to play.

                               One more time THANK YOU:):):guitar:

---

### Post by Trevor-Stone on 2008-06-28
I do have one more question for ya. I no servers run all day and every day but how do I shut it down properly. For now I just hold the button in is that safe??
I don’t wont to lose data when I load it up you never no when things mite go wrong and I got to shut it down.


                           Thanks

---

### Post by wormser on 2008-06-28
Do not hold the button to shut it down!!!  There are a few commands.  Shutdown, halt and reboot.  The shutdown command has lots of options.  The -h stands for halt or you can use -r to reboot.

```
sudo shutdown -h now
```
```
sudo halt
```
```
sudo reboot
```

Make sure you mark the thread Solved when all your issues are solved.

---

### Post by hyper_ch on 2008-06-28
or
```

sudo poweroff

```

---

### Post by Trevor-Stone on 2008-06-30
Thanks again all!

But I got one more for ya all. I have been playing with the server and I installed webmin and all the updates that it needs to work.

In my network it works fine and I can up load from my p/c (windows) to the server and download .Even from my missus lap top (no problem we are in the same network)

My internet is unwired (its crap but I rent and got to move house every year and sick of waiting to get set up again) 

Now I tried it form a mates house and it failed (that’s fine) so I went home and as a test I  turned off the firewall and made my server out side the network so in all rights any one had the opportunity to hack my computers easy.

Still no go (is it my internet provider, do I need to have a special address to make it work I don’t know I’m a bit out of my league right now.:guitar:

---

