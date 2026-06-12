---
title: "HOW TO: Install Virtualmin, Webmin &amp; Usermin on Ubuntu Server 8.04 LTS (Easy)"
date: 2009-06-26
forum: Outdated Tutorials &amp; Tips
---

### Post by Francewhoa on 2009-06-26
This how to handbook is for **absolute beginners. **An installation script will do most of the hard work for you. There're lot of steps below but that's easy.
[B] 
OBJECTIVES:[/B]
- Install and setup the following:
    - Ubuntu Server edition 8.04.2
    - Webmin 1.470 GPL
    - Virtualmin 3.69 GPL
    - Usermin 1.400 GPL

**COST IN $ US:**
$0 for the above softwares because we are going to use only Open Source softwares. 
$20 to $50 per month for the hosting.
$10 to $40 per year for a domain name.

**HOW LONG DOES IT TAKES?**
30 to 60 minutes.

**REQUIEREMENTS:**
-    One remote web hosting server with:
                ---------        -    A freshly installed Ubuntu 8.04 LTS Server Edition 32bit version. It works too with 64 bits version. But in this how-to we will be using the 32 bits version. Ubuntu Server is a free open source operating system very performant to host websites. Ubuntu is the most popular Open Source Linux distro. Read more at [http://www.ubuntu.com/getubuntu/download-server](http://www.ubuntu.com/getubuntu/download-server)
                        --------- - Apache most NOT be already installed. It will be install by the below installation script.
                        --------- - At least 512MB of RAM (memory). I never tried with less. If unsure you better install with more RAM then needed. Then reduce the RAM later.
                        --------- - At least 2GB (2048MB) of swap disk (Linux virtual memory). Once Virtualmin is installed the swap disk can be reduce to 512MB. 
                        --------- - Full root access and full SSH access. Such as most VPS, dedicated or your own server. Make sure you have root access. Shared hosting will NOT work.
                        --------- - Access to &#8220;Universe&#8221; and &#8220;Multiverse&#8221; Ubuntu repositories. Read more at [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
-    One local home computer with Ubuntu 8.04 LTS Desktop Edition 32bit version. Nothing will be hosted on this computer. It will be use to access the remote Ubuntu Server via SSH.
[B]
STEPS:[/B] 
Connect to your remote Ubuntu server via SSH on your home computer. To do so open TERMINAL. TERMINAL can be found under Ubuntu desktop panel menu > APPLICATIONS > TERMINAL
The TERMINAL window will open. 
Type in the following command line. Then press RETURN key.
```
ssh root@123.123.123.123 
```(Note: In the above command replace &#8220;root&#8221; with your remote Ubuntu Server username and replace &#8220;123.123.123.123&#8221; with your remote Ubuntu Server IP address. This IP address is provided by your host provider. Username is usually 'root'.)
(Tips: You can copy and paste text or command line to TERMINAL using right click > Select COPY or PASTE)

You are now connected to your remote Ubuntu server.

By default a fresh Ubuntu installation comes with the Fully Qualified Domain Name (FQDN) &#8216;ubuntu&#8217;. But Virtualmin installation script required a third level domain name such as &#8216;ns1.YOURDOMAINNAMEHERE.com&#8217;.

In the following we&#8217;ll set a third level domain name.

We are now going to check the remote Ubuntu Server actual fully qualified domain name (FQDN)
Type in the following command in TERMINAL:
    ```
hostname --fqd
```Note: Make sure it&#8217;s two dash before 'fqd' not one.

If output returns &#8216;ubuntu&#8217; you need to change the FQDN.

We are now going to configuring the remote Ubuntu server network.
Because the Ubuntu installer has configured our system to get its network settings via DHCP, we have to change that now because a server should have a static IP address.
Edit the file 'interfaces' located at:
    ```
/etc/network/interfaces
```Note: One way to edit a file is using your local Ubuntu Desktop and navigate to > PLACES menu > CONNECT TO SERVER >
    Service type: SSH
    Server: [type in your server IP address]
    Port: [leave empty]
    Username: [type in your username. Usually it's &#8221;root&#8221;]
    Check ADD BOOKMARK box. So next time it's easier to connect.
    Bookmark name: [Could be anything.]
    
A new window will open. This is your remote server root folder.
Navigate to /etc/network/interfaces

We are now going to edit the file INTERFACES. To do so right click on the file and select OPEN WITH OTHER APPLICATION... > Select TEXT EDITOR > Click on OPEN button.

(Tips: It is recommended to backup any file before editing it. To do so copy and paste the file in the same directory. Then change the file copy name to &#8220;interface-backup-add_current_date_here&#8221;)

(Note: For now on we assume that you know how to open a file, backup a file and edit it.)

Edit the file INTERFACES. We are editing the last line. And will add a few new lines at the bottom.

[File before:]
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```[File after:]
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 123.123.123.123
        netmask 255.255.255.0
        network 123.123.123.0
        broadcast 123.123.123.255
        gateway 123.123.123.123
```Note: In above AFTER you must replace the numbers:
address 123.123.123.123
    (Change '123.123.123.123' to your remote Ubuntu Server IP.)

netmask 255.255.255.0
    (Paste as is. Do not change it.)

network 123.123.123.0
    (Change '123.123.123.0' to your remote Ubuntu Server IP but you must change the last number to zero '0'.)

broadcast 123.123.123.255
    (Change '123.123.123.255' to your remote Ubuntu Server IP but you must change the last number to 255'.)

gateway 123.123.123.123
    (Change '123.123.123.123' to your remote Ubuntu Server gateway address. Gateway address and IP address are different. Ask your hosting provider.)

Restart your network on your remote Ubuntu Server. 
To do so open TERMINAL and type in the following command.
    ```
/etc/init.d/networking restart
```If [COLOR=black]succes[/COLOR]sful terminal will output the following
    > * Reconfiguring network interfaces...
 [ OK ]On your remote Ubuntu Server.
Edit the file 'hosts' located at
        ```
/etc/hosts
```We are going to edit the first two lines only.

[File before:]
```
127.0.0.1    localhost
127.0.1.1    ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```[File after:]
```
127.0.0.1    localhost.localdomain    localhost
123.123.123.123    ns1.YOURDOMAINNAMEHERE.com    ns1

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```Note 1: In above AFTER you must keep the following line as is:
```
127.0.0.1    localhost.localdomain    localhost
```                (This line must be paste as is. Do not change it.)

            Note 2: In above AFTER you must replace the numbers:
            ```
123.123.123.123    ns1.YOURDOMAINNAMEHERE.com    ns1
```                (Change &#8220;123.123.123.123&#8221; to your remote Ubuntu server IP address.)

                  (Change &#8220;ns1.YOURDOMAINNAMEHERE.com&#8221; to your domain name. Keep the &#8220;ns1&#8221; at the beginning as is. 'ns1' is an industry standard. It stands for Name Server designator 1. Keep the &#8220;ns1&#8221; at the end as is.)

                For example if your domain name is virtualmin.com then your line would be: 
            ```
67.225.148.19    ns1.virtualmin.com    ns1
```Type in the following command in TERMINAL:
        ```
echo ns1.YOURDOMAINNAMEHERE.com > /etc/hostname
```If [COLOR=black]succes[/COLOR]sful TERMINAL will return nothing.

Type in the following command in TERMINAL:
    ```
/etc/init.d/hostname.sh start
```If [COLOR=black]succes[/COLOR]sful TERMINAL will return nothing.

Type in the following command in TERMINAL:
    ```
hostname
```If [COLOR=black]succes[/COLOR]sfull TERMINAL will output
    > ns1.YOURDOMAINNAME.comType in the following command in TERMINAL:
    ```
hostname -f
```If [COLOR=black]succes[/COLOR]sfull TERMINAL will output
    > ns1.YOURDOMAINNAME.comThe remote Ubuntu Server&#8217;s network is now configured.
The FQDN is now configured.

We are now going to change the remote Ubuntu Server Default Shell.

    If you don't do this, the ISPConfig installation will fail.

Note: A symlink is basically a shortcut to a file. Think of them like a shortcut in MS Windows, except the shortcut isn't a separate file, it's a "link" to the actual file.

Type in the following command in TERMINAL:
            ```
ln -sf /bin/bash /bin/sh
```If [COLOR=black]succes[/COLOR]sful TERMINAL will return nothing.

We are now going to disable then remove AppArmor on the remote Ubuntu Server.

Note: AppArmor is a security extension (similar to SELinux) that should provide extended security. In my opinion you don't need it to configure a secure system, and it usually causes more problems than advantages (think of it after you have done a week of trouble-shooting because some service wasn't working as expected, and then you find out that everything was ok, only AppArmor was causing the problem). Therefore I disable it (this is a must if you want to install ISPConfig later on). 

Type in the following command in TERMINAL:
```
/etc/init.d/apparmor stop
```If [COLOR=black]succes[/COLOR]sful TERMINAL will return:
        > /etc/init.d/apparmor stop Type in the following command in TERMINAL:
```
update-rc.d -f apparmor remove
```If [COLOR=black]succes[/COLOR]sful TERMINAL will output a few lines. The last 2 lines will look like this:
> Removing any system startup links for /etc/init.d/apparmor ... /etc/rcS.d/S37apparmorType in the following command in TERMINAL:
```
apt-get remove apparmor apparmor-utils
```In my case the package 'apparmor-utils' wasn't install so TERMINAL returns the following. That's normal.
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package apparmor is not installed, so not removed
Package apparmor-utils is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.Type in the following command in TERMINAL:
        ```
free -m
```TERMINAL will output the amount of RAM use on your remote Ubuntu Server before. Look at the second column titled 'used' and the first line titled 'Mem:'. All number are in MB. This is before installing Virtualmin. 
In my case TERMINAL output 65MB RAM used.

To make sure all changes we made are active reboot your remote Ubuntu Server.

We are now going to check the remote Ubuntu Server new fully qualified domain name (FQDN)
Open TERMINAL. 
Login your remote Ubuntu Server.
Type in the following command in TERMINAL:
    ```
hostname --fqd
```Note: Make sure it&#8217;s two dash before 'fqd' not one.

If [COLOR=black]succes[/COLOR]sful TERMINAL will output
> ns1.YOURDOMAINENAMEHERE.COMType in the following command in TERMINAL to update the apt-get packages repositories:
    ```
apt-get update
```Wait. This might take up to 5 minutes. If [COLOR=black]succes[/COLOR]sful TERMINAL output:
>      Reading package lists... Done Type in the following command in TERMINAL to update to the latest packages:
This will update your remote Ubuntu Server to the latest version. Currently 8.04.2 
        ```
apt-get upgrade
```TERMINAL will ask 'Do you want to continue [Y/n]?'.
Type in Y then press RETURN key.
Wait. This might take up to 15 minutes. If [COLOR=black]succes[/COLOR]sful TERMINAL output a lot of lines.

If TERMINAL returns the following error:
>          LANGUAGE = (unset),
LC_ALL = (unset),Then you must install another package. To do so type in the following command then press RETURN.
        ```
apt-get install language-pack-en
```TERMINAL will ask 'Do you want to continue [Y/n]?'.
Type in Y then press RETURN key.
If [COLOR=black]succes[/COLOR]sful TERMINAL will return lot of lines.

Type in the following command in TERMINAL to install 'screen' and 'wget'. Those will be use by the coming Virtualmin installation script 'install.sh'
        ```
apt-get install screen wget
```We are now going to download the free open source Virtualmin installation script. This script is going to do all the hard work for you.
Type in the following command in TERMINAL to download the installation script to your remote Ubuntu Server:
    ```
wget [http://software.virtualmin.com/gpl/scripts/install.sh](http://software.virtualmin.com/gpl/scripts/install.sh)
```Type in the following command in TERMINAL to set the permissions on the installation file:
```
chmod +x install.sh
```We are now going to make sure that there&#8217;s at least 2GB (2048MB) SWAP disk available for Virtualmin installation script (install.sh) otherwise the installer will run out of memory. You can reduce the SWAP to 512MB after installation. 

Type in the following command in TERMINAL to know the current size of your SWAP disk:
    ```
df -m
```TERMINAL will return the current size of you SWAP disk. Size is in MB. The number you're looking for in the first column titled '1M-blocks' and the first line. In my case my number is 2206. So I'm good to go to the next step.

Type in the following command in TERMINAL to install Virtualmin & Webmin & Usermin from within SCREEN:
    ```
sudo ./install.sh
```Terminal will ask 'Continue? (y/n)'.
    Type in y and press RETURN key.

Wait. The spinning bar means that the installation is in progress. It can take up to 30 minutes. Wait.

When the installation script is done the spinning bar will disappear.

Important note: Once Virtualmin is installed, you never need to run this script again.

Reboot your remote Ubuntu Server to make all the changes active.

Go to: [https://123.123.123.123:10000/](https://123.123.123.123:10000/)

    Note 1: You must replace above 123.123.123.123 by your remote Ubuntu Server IP address.
    Note 2: The link starts with https:// not http:// The 's' means secure connection.

If the script installation is [COLOR=black]succes[/COLOR]sful you should see Webmin control panel.

Note: If your internet browser is Firefox version 3 it will display the following message &#8220;Secure Connection Failed&#8221;. That's normal. You must let Firefox know that your remote Ubuntu Server is safe. To do so: 
Click on &#8221;Or you can add an exception&#8230;&#8221; link.
Click on ADD EXCEPTION link.
Click on GET CERTIFICATE button.
Click on CONFIRM SECURITY EXCEPTION button.

If working you'll see your Webmin log in page.
Type in your username & password. Your username & password are the same as your remote Ubuntu Server. Your username is usually 'root' unless you changed it. 

The first Webmin page is title &#8221;Post-Installation Wizard&#8221;
The following message is display under the title &#8221;This post-installation wizard allows you to configure Virtualmin optimally for your system. You can make selections depending on whether you want to host websites, email or databases, and based on your system's memory and CPU power.To continue, click the Next button below. To skip it and use the default settings, click Cancel.&#8221;

Click on NEXT button.
Set your preference to match your needs. You can change your settings later.

In my case I have a limited amount of RAM available so to use less RAM my settings are as follow:
        Preload Virtualmin libraries? NO
        Run email domain lookup server? NO
        Run ClamAV server scanner? NO
        Run SpamAssassin server filter? NO
        Run MySQL database server? YES because I'll add Drupal later.
        Run PostgreSQL database server? NO because I use MySQL instead.
        Set MySQL password? For security reason you should choose a different password than your remote Ubuntu Server. 6 to 16 alphanumeric and characters max. No symbol allowed.

After completing the WISARD Webmin will return the following message under the title at the top of your screen: &#8221;All done&#8221;
Click on NEXT button.

A yellow box will be display at the top of Webmin interface.
Click on RE-CHECK AND REFRESH CONFIGURATION button.

If [COLOR=black]succes[/COLOR]sful the following message will display close by the bottom:
> .. your system is ready for use by Virtualmin.We are now going to refresh the Webmin modules display.
Click on WEBMIN link located on the top left side of your screen.
Click on REFRESH MODULES link.  

If [COLOR=black]succes[/COLOR]sful Webmin returns a message like > &#8220;.. found 68 with installed applications, 43 not installed.&#8221;Click on VIRTUALMIN link located on the top left side of your screen.
Click on SYSTEM INFORMATION link located on the left side of your screen.
Find the line REAL MEMORY. This line provides information on your remote Ubuntu Server memory.
The first number is your total memory. And the second number is your used memory. In my case the used memory is around 150MB.

Important note 1: Once Virtualmin is installed, you never need to run this script again. This is a installation script NOT an updates script.

Important note 2: For now on Virtualmin, Webmin & Usermine upgrades and updates should be done within Virtualmin itself. Not TERMINAL.

That's it you're done. You have [COLOR=black]succes[/COLOR]sfully installed Virtualmin, Webmin & Usermine on a remote Ubuntu Server.

If you get any errors or have any concerns the first thing you should try is searching the free Virtualmin support forum at [http://www.virtualmin.com/search](http://www.virtualmin.com/search)

====================================================

You just installed the Virtualmin GPL free version. Virtualmin Pro offers extra features and support. [http://www.virtualmin.com/compare.html](http://www.virtualmin.com/compare.html) 

If you want to upgrade to Virtualmin Pro go to [http://www.virtualmin.com/catalog/19](http://www.virtualmin.com/catalog/19) and purchase a license for Virtualmin Pro.

Go to your Virtualmin: [https://123.123.123.123:10000/](https://123.123.123.123:10000/)

Note 1: You must replace above 123.123.123.123 by your remote Ubuntu Server IP address.
Note 2: The link starts with https:// not http:// The 's' means secure connection.

Navigate to VIRTUALMIN > SYSTEM SETTINGS > UPGRADE TO VIRTUALMIN PRO. This is the &#8216;Upgrade to Virtualmin Pro&#8217; page. 
Under the section VIRTUALMIN PRO LICENCE type in your SERIAL NUMBER and your LICENSE key.

Note: Your SERIAL NUMBER and your LICENSE key can be found on the following page. You must have a Virtualmin account to see this page and be login. [http://www.virtualmin.com/serial](http://www.virtualmin.com/serial)

Still in VIRTUALMIN &#8216;Upgrade to Virtualmin Pro&#8217; page click on UPGRADE NOW button. 

If successful Virtualmin will download all of the latest Virtualmin modules, and add them to your Webmin install. All of your existing settings will be left un-changed, and no other software installed.

Wait. The process might take up to 15 minutes.

If successful Virtualmin will output the following message at the bottom of the page. You must scroll down the page to see this message.
> Your system has been successfully upgraded to Virtualmin Pro!Virtualmin Pro contains new modules. So we are now going to refresh the Webmin modules display again.
Click on WEBMIN link located on the top left side of your screen.
Click on REFRESH MODULES link.  

If [COLOR=black]succes[/COLOR]sful Webmin returns a message like > &#8220;.. found 81 with installed applications, 43 not installed.&#8221;That's it you're done. You have successfully upgraded to Virtualmin Pro.

Enjoy

Onopoc

Source: [http://www.virtualmin.com/documentation/installation/automated](http://www.virtualmin.com/documentation/installation/automated)

---

### Post by Kolipoki on 2009-06-30
Excellent! Thanks a lot for sharing this info, highly appreciated!.

---

### Post by Nick Hill on 2009-08-24
I have spent about a week trying out the different control panels for web hosting. sysCp, ISPconfig, virtualmin, ebox. 

I have had past experience with Cpanel and Plesk6, which are both commercial offerings.

The free control panels are not close to the user friendliness and ease for end users compared to those two. However, those commercial panels I have tried are poor when you need custom apache configs. They tend to overwrite your custom config.

An ideal panel in my opinion would 

1 ) Each domain name must be attached to a control panel user. 

2 ) Each user can, depending on privileges given by the administrator, log into the control panel.

3 ) The administrator should be able to disable the user and by extension all services under that user.

4 ) For each domain name, it should be possible to enable and disable email, FTP, web service individually.

5 ) For each web host (under the user and domain name) it should be possible to enter custom apache configurations. Users should only be allowed to do this if granted by admin as these can prevent apache from restarting.

6 ) Users should be able to set up mail boxes, aliases and redirects according to limits set by administrator if the administrator has granted this privilege.

7 ) Mailbox username and passwords should not be mapped to POSIX usernames and passwords. It is completely nonsensical. It is very rare these days for a one email address per posix login account set-up. This relationship needs to be broken, as it just makes configs unnecessarily complicated and danger-prone. Most email is fetched either by webmail, Imap or POP3. POSIX user account mboxes are a broken implementation 99% of the time. Mail collection username should be [email]mailboxname@domainname.tld[/email] so that multiple users can share mailboxes of the same name, without messing with redirects. This could be implemented with a simple mapping file rather like /etc/shadow, with a standard layout, understood by both the MTA and by a POP/Imap daemon. This would be a simple piece of integration that will make a lot of difference. A patch by the distribution for the key supported MTA and pop/imap daemons would do the trick. This must be implemented at the distribution level, not the control panel vendor level.

8 ) The control panel and the daemons it controls should receive security updates through the package management system. There should not be any part of the standard system which requires the sysadmin to manually patch security flaws. 

Other things would be nice, but not important such as user configurable cron, per directory access configuration, file manager.

To achieve these goals, the user on the control panel should not link to a user on POSIX/PAM. There should be one POSIX username per domain name which Apache SUexecs in that virtualhost. FTP username/password on a per-domain name basis which matches the Apache SUexec POSIX user.

How close are the control panels?
SysCP offers much of the above, but with what appears to be a highly customised configuration system for mail and FTP. I have a copy running on Debian and an update sent the system Fubar. The config system is supported by SysCP but not by Debian. 

Ebox. Offers individual configuration of core linux services, but is clearly not designed for virtual host administration. Offers little to none of the above.

ISPconfig. I installed the system with some hesitation based on the fact that parts are compiled from source, not sourced via package management. Uses special configurations. I have spent an hour playing with it, but I find it frustrating. I have not yet been able to determine how much of the above it offers, as much of the language it uses is wrong. For example, fileserver - is that FTP? I am wary that given that the core of the system is not via package management, and given the custom configurations, believe it could break package management and updates, like syscp did for me.

Virtualmin - Misses many of the above functions. In particular, dos not allow creation of mailboxes not mapped to POSIX/PAM accounts. This is understandable given that Ubuntu don't appear to officially support this. Virtualmin appears to use standard configuration files as per usual Ubuntu system administration. The install was logical, and the user interface logical and consistent. I am leaning towards virtualmin in the hope that Ubuntu will one day introduce a *supported* method of full virtual mail. MTA -> pop/imap without needing a PAM/POSIX account as an intermediary.

I feel it is far less likely that updates to the Ubuntu system will break Virtualmin or the services it delivers.  I expect that if I stripped virtualmin from the system, services it supports will still operate with little or no re-configuration. Combined with it's more logical arrangement, I feel virtualmin is on the right lines. I have not made a final decision as I need to spend more time with ISPconfig to make sure, but Virtualmin is looking the best right now.

I'll re-iterate. Ubuntu, please deliver explicit support for integration of MTA (postfix or Exim) and POP/IMap in such a way that a POSIX PAM account is not necessary as an intermediary for the authentication and collection of mail. This isn't so much a coding but a management issue,

---

### Post by kemadruma on 2009-09-23
Hello,
When i click yellow button "Check confugiration",
It says

>      
BIND DNS server is installed, and the system is configured to use it.

Mail server Postfix is installed and configured.

 The Suexec command on your system is configured to only run scripts under /var/www, but the Virtualmin base directory is /home. CGI and PHP scripts run as domain owners will not be executed.

.. your system is not ready for use by Virtualmin.

Also, u have mentioned in your article,
> Reboot your remote Ubuntu Server to make all the changes active.

I havent done that yet, its remote server.

---

### Post by Francewhoa on 2009-10-16
@kemadruma: > When i click yellow button "Check confugiration", Solution at [http://www.virtualmin.com/node/8427](http://www.virtualmin.com/node/8427)

If that doesn't work have you tried searching the Virtualmin support forum? [http://www.virtualmin.com/search](http://www.virtualmin.com/search)

> I havent done that yet, its remote server.
One of the requirements is "Full root access and full SSH access." That means being able to remotely restart your remote server. If you don't restart your remote server it won't work properly.

---

### Post by Francewhoa on 2009-10-16
@Nick Hill: Thanks for your great suggestions in your comment #3. I posted a copy of your comment to Virtualmin forum for long-term feature goals. It's call the 'Blue Skies' at [http://www.virtualmin.com/forum/18](http://www.virtualmin.com/forum/18)

I'm sure the Virtualmin community would welcome your great suggestions to better match user' needs.

Direct link to the copy of your comment [https://www.virtualmin.com/node/11857](https://www.virtualmin.com/node/11857)

---

### Post by kemadruma on 2009-10-18
Had same problem after the restart.
( I had full root access, it was a dedicated server)

Unfortunatly, Didnt get the chance to check the solution you provided, server was expired by that time.

Btw. Thanks for the gr8 article and response, sure it will be helpful in future installations.

Cheers

---

### Post by jonnybradley on 2009-11-01
Many thanks for this guide - just thought i'd share my experiences in using it.

I found this a while ago but i had already messed about significantly with my server so installed Virtualmin mannually, but i was getting lots of trouble getting the mail to work properly, so i decided to start again.

This is running on an (incredibly good value) amd64 VPS with 256MB of RAM only, and 10GB of disc space (and setting it up from a Mac, but that's not really relavent).

My first attempt was on what my ISP describes as "Ubuntu 8.04.1 64 bit Minimal". I got some nasty errors about postgresql user and others (sorry, i didn't note them all down) so decided to re-reimage using just "Ubuntu 8.04.1 64"

That time it installed fine except when going through the Virtualmin wizard i had to 'chown -R postfix /var/spool/postfix' (although i'm not sure about the -R option) to get postfix happy.

All was well except the "The Suexec command on your system is configured to only run scripts under /var/www, but the Virtualmin base directory is /home" problem i had encountered before when installing manually. The only solution seems to be to rebuild apache with /home set as the --with-suexec-docroot.

Here is a quite short version of the process: [http://blog.chty.org/post/2008/08/12/Changing-suexec-root-directory](http://blog.chty.org/post/2008/08/12/Changing-suexec-root-directory) (there are others, and this one didn't install correctly for me first time - retrying...). Apparently this should have happened automatically - but didn't. There's more here: [http://www.virtualmin.com/documentation/installation/manual](http://www.virtualmin.com/documentation/installation/manual)

Anyway - apart from that hiccup, all was good in the end - and many thanks for this page!

---

### Post by finninasia on 2009-11-11
Question about using screen when starting install.sh

Should I use command

```
screen sudo ./install.sh
```

Instead of 

```
sudo ./install.sh
```

Original text in the howto.
Type in the following command in TERMINAL to install Virtualmin & Webmin & Usermin from within SCREEN:
Code:

sudo ./install.sh

---

### Post by mraza08 on 2009-12-11
Nice tutorial but i cant access 
#  /etc/network/interfaces
permission denid

if i enter
#  sudo /etc/network/interfaces
there is nothing to display. pleaes can you tell me how can i open interface file. i am new this.

---

### Post by mutucrystal on 2009-12-28
> **mraza08 said:**
> Nice tutorial but i cant access 
#  /etc/network/interfaces
permission denid

if i enter
#  sudo /etc/network/interfaces
there is nothing to display. pleaes can you tell me how can i open interface file. i am new this.

try         sudo vi /etc/network/interfaces

sudo comand give you admin privileages
vi comand for edit

after you finish to replace press ALT+d and the type :wq and press enter
:wq are 2 comands w- write, q- quit

---

### Post by milindras on 2010-03-02
This is an excellent documentation! No words to thanks.
i installed 02 web server according to the instructions & there is no problem at all.
 
many Thanks again:)

---

### Post by milindras on 2010-03-03
> **mraza08 said:**
> Nice tutorial but i cant access 
# /etc/network/interfaces
permission denid
 
if i enter
# sudo /etc/network/interfaces
there is nothing to display. pleaes can you tell me how can i open interface file. i am new this.
 
 
You are trying to access a directory here. interfaces is a file. try this
#su root (will promt for the root password)
#cd /etc/network/ (going to that directory first)
#vi interfaces (or use your favourite editor to edit that file - my favourite is vi editor)
 
Thanks
milindra

---

### Post by milindras on 2010-03-03
Hi,
Many thanks again for the clear instructions!
 
Have few questions?
 
1. The default installation of Spamassain with the virtualmin, Is that ready to use? I meant is that filter spams? Or Do i need to tune or configure anything on that?
This is mainly because of I have another web server which installed on 2008 nov (by somebody else) with virtualmin. We have like 100 domains hosted on that but I can't really see the spamassign do much work to filter emails to all domains. (basically all the domain receive spams!)
 
2. Do you have any documentation for Best Practise guide lines for Web server? Or know a place i can find in the internet?
This is because I install a new server last week for the first time. Its a live web server now. So I want to make sure all the security, performance & etc up to level/standards.
 
3. Is openwebmail also include in the virtualmin installation? Or do i have to install that seperately?
 
many Thanks
Mili

---

### Post by FatBoyNotSoSlim on 2010-03-04
Has anyone had any luck installing Virtualmin on Karmic?
 
I think I managed to get it to install correctly, but (unlike on Hardy) the login is for Webmin, and Virtualmin can only be used as a module from Webmin, not as it was previously.
 
If thats confusing, I'm trying to make Virtualmin and its laout/theme the default when I go to localhost:10000.
 
Backstory:
I had originally set up Virtualmin+Webmin on Hardy awhile back, and upgraded to Jaunty where it ran fine. However, after I migrated to Karmic, I had other issues, so decided to fresh install. Since then, Virtualmin isn't the same. I've installed from the script, fixing up minor problems as I went along, and when I go to log in, its only to Webmin, and I can acess Virtualmin with some errors and parts missing as a module, which is quite annoying. I'm wanting them seperated again.

---

### Post by zappal on 2010-04-25
im confused, in your tutorial you mentioned ISPconfig. is this a typo?

---

### Post by James78 on 2010-12-06
I want to clarify, that for your hostname, you don't need it to be a fqdn. All you need for a hostname is something like "ns1", then in your /etc/hosts an entry like "192.168.1.120    ns1 ns1.domain.com", and that way the hostnames short name will be ns1 and fqdn will be ns1.domain.com, the Virtualmin script and everything works with it. The ONLY problem is that Postfix is supposed to resolve the shortname to the fqdn, but doesn't, in which all you need to do is add ns1.domain.com to myhostname in the main.cf for Postfix.

It's much better to do it this way. ;)

---

### Post by duceduc on 2011-01-04
I've got webmin install and I also want to install virtualmin. However, the installation note says
>  The installation is quite stable and functional when run on a freshly installed supported Operating System, but upgrades from existing .wbm-based systems, or systems that already have Apache VirtualHost directives or mail users, will very likely run into numerous problems...


Would I really have problems if I install virtualmin over an existing server?

---

### Post by Cardale on 2011-01-14
hey is there a tutorial like this for 10.04 or 10.10?

---

### Post by James78 on 2011-01-20
The installer script isn't supported for 10.10, only on LTS releases, so I'm afraid you'd have to install it manually in that case.

---

### Post by jharris1993 on 2011-03-27
Question:
 
All of this dialog talks about installing webmin on a remote box.
 
I have a box on my LOCAL network running 10.04x LTS (server) that has no GUI because I don't need the dead weight on my box.  This box is primarly running as a Samba file server on my Windows network - and I use SWAT to configure and admin the SMB services.
 
I am looking for something that will provide a similar ability to perform simple admin tasks from a web client and webmin looks like a great choice.
 
Note that this box is **PRIMARILY** being used as a massive file server.  I don't have sendmail installed, postgres IS installed but not configured (as I don't really need it), no SQL stuff, etc.  The only things I have installed out-of-the-ordinary are screen and byobu to make console sessions friendlier.  I don't run LDAP, NFS, et. etc. etc. as (for all intents and purposes), this beastie is a multi-terabyte NAS box running Ubuntu on a dual-core amd-64 processor with handfulls of memory - as I want this box to be as lean-and-mean as possible, consistent with running multi-T raid arrays.
 
I deliberately trashed a 10.04 *desktop* install and replaced it with 10.04 *server* to eliminate a lot of the cruft that the GUI drags in its wake.
 
This brings me to two questions:
1.  Given the choice between running Webmin, or installing an X-client, which would be the better approach - while providing the ability to do at least limited remote admin, (using a Windows box on my network via a web browser or an X-server)
 
2.  How difficult will it be to install Webmin on a 10.04 (server) box on a local network?  Are there any hoops that I have to jump thorugh not detailed above?  Do I really have to go the LDAP or SQL server route to use it?
 
Thanks for any info you can give me.
 
Jim

---

