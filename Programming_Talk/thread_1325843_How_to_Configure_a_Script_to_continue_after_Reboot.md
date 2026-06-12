---
title: "How to Configure a Script to continue after Reboot"
date: 2009-11-13
forum: Programming Talk
---

### Post by dr_latino999 on 2009-11-13
I'm currently trying to configure a set of NDT servers at work using Ubuntu 8.04LT and Web100 code and I've run into a bit of a situation. The install requires a reboot mid way through the setup and at which point I've had to split the script I've created for testing in half. Is there an easy way to immediately before the reboot command is given to tell the system to 'remember' where the script was and continue it once the system comes back on. 

Attached are my two configuration scripts, which I would like to make into one. Forgive any syntax or simplicity, I just started with bash this past week.

**Install-1.sh**
```
#!/bin/sh
###Begin Module 1
echo "Do you want to configure the system network interface? 1 = yes, 2 = no"
read answer
if [ "$answer" == 1 ]; then
    echo "Creating Network Interface File."
    echo "Stopping Network services"
    sudo /etc/init.d/networking stop

    echo "Location of the file to be stored."
    declare A=/etc/network/interfaces
    echo "Location file is to be saved: $A"
    echo "#The loopback network interface" > $A
    echo "auto lo" >> $A
    
    echo "What is the local IP address you wish to you?"
    read localipaddress
    echo "iface lo inet loopback" >> $A
    echo "#Primary Interface" >> $A
    echo "auto eth0" >> $A
    echo "iface eth0 inet static" >> $A
    echo "address $localipaddress" >> $A
    
    echo "What is the netmask?"
    read netmask
    echo "netmask $netmask" >> $A
    
    echo "What is the gateway?"
    read gateway
    echo "gateway $gateway" >> $A
    sudo /etc/init.d/networking restart
    echo "Networking settings are stored."
    sleep 15
else echo "Carrying on then."
fi
###End Module 1
#
#
#echo -n "Hold for image save"
#read z

echo "This will install Web100 NDT support to the Ubuntu 8.04 32 bit Server operating system."
###Begin Module 2
echo "Checking for and then installing system updates."
sleep 15
sudo apt-get update
echo Y|sudo apt-get upgrade
###End Module 2
#
#
#echo -n "Hold for image save after Mod 2"
#read z

echo "Installing the necessary packages to compile kernel."
###Begin Module 3
#Installing the necessary packages needed for the Web100 build
echo -n "IMPORTANT - Under absolutely no circumstances do you hit the TAB key when reading the Java user agreement, you will break the install. AVOID THE TAB KEY! [ENTER]"
read pppppp
echo Y|apt-get install autoconf automake1.9 csh bison build-essential flex g++ libarchive-zip-perl libauthen-pam-perl libdb4.4-dev libio-pty-perl libpcre3 libpopt-dev libnet-ssleay-perl libtool libmd5-perl libcap-dev libreadline5-dev libimlib2-dev kernel-package libncurses5-dev lynx fakeroot wget bzip2 ncftp nmap openssl rcconf sendmail sun-java5-bin sun-java5-jdk unzip zip zlib1g-dev python2.5-dev
###End Module 3
#
#
#echo -n "Hold for image save after Mod 3"
#read z

echo "Downloading 2.6.24 kernel."
###Begin Module 4
cd /usr/src
wget http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.24.tar.gz
###End Module 4
#
#
#echo -n "Hold for image save after Mod 4"
#read z

echo "Extracting the kernel."
###Begin Module 5
cd /usr/src
sudo tar -C /usr/src -xvf linux-2.6.24.tar.gz
sudo rm -rf /usr/src/linux
sudo ln -s /usr/src/linux-2.6.24 /usr/src/linux
###End Module 5
#
#
#echo -n "Hold for image save after Mod 5"
#read z

echo "Downloading Web100 patch."
###Begin Module 6
cd /usr/src/
sudo wget http://www.web100.org/download/kernel/2.5.19/web100-2.5.19-200802211940.tar.gz
sudo tar -xvzf /usr/src/web100-2.5.19-200802211940.tar.gz
###End Module 6
#
#
#echo -n "Hold for image save after Mod 6"
#read z

echo "Applying Web100 patch"
###Begin Module 7
cd /usr/src/linux
patch -p1 < /usr/src/web100/web100-2.6.24-2.5.19-200802211940.patch
###End Module 7
#
#
#echo -n "Hold for image save after Mod 7"
#read z

echo "Configuring the kernel and forcing a full rebuild."
###Begin Module 8
cd /usr/src/linux
sudo cp /boot/config-2.6.24-24-server ./.config
echo -n "IMPORTANT: When you enter the configuration for the kernel, the following items happen : [ENTER]"
read aaaaaa
echo -n "You must activate the Web100 Patch. It can be found under Networking -> Networking Options -> IP: Web100 networking enhancements. [ENTER}"
read bbbbbb
echo -n "All sections of Web100 must be selected. [ENTER]"
read cccccc
echo -n "Before you leave the menu, you must remove Xen support from the kernel. It can be located under Processor Type & Features -> Paravirtualized Guest Support. [ENTER]"
read dddddd
echo -n "If this is not removed, the build will fail. The cause of this is unknown at the time. [ENTER]"
read eeeeee
sudo make menuconfig
sudo make-kpkg clean
sudo fakeroot make-kpkg --initrd --append-to-version=-web100 kernel_image kernel_headers
###End Module 8
#
#
#echo -n "Hold for image save after Mod 8"
#read z

echo "Install new image and heades."
###Begin Module 9
cd /usr/src
sudo dpkg -i linux-image-2.6.24-web100-web100_2.6.24-web100-web100-10.00.Custom_i386.deb
sudo dpgk -i linux-headers-2.6.24-web-web100_2.6.24-web100-web100-10.00.Custom_i386.deb
sudo shutdown -r now
###End Module 9
#
#
#echo -n "Hold for image save after Mod 9"
#read z

```**Install-2.sh**
```
#!/bin/sh
echo "Continuing the install and setup of the Web100 packages."
cd /usr/src
echo "Downloading the Web100 Userland and then configuring it."
sudo wget http://www.web100.org/download/userland/version1.7/web100_userland-1.7.tar.gz
sudo tar -xvzf web100_userland-1.7.tar.gz
cd web100_userland-1.7
sudo apt-get install python2.5-dev
sudo ./configure --enable-python
sudo make
sudo make install
cd ..
sudo rm -Rf web100_userland-1.7
sudo rm web100_userland-1.7.tar.gz

echo "Configuring and installing NDT."
cd /usr/src
echo "Downloading NDT package from Internet2 website."
sudo wget http://software.internet2.edu/sources/ndt/ndt-3.5.6.tar.gz
sudo tar -xvzf ndt-3.5.6.tar.gz
cd ndt-3.5.6

echo "Installing NDT package."
sleep 15
sudo ./configure
sudo make
sudo make install

echo "Preparing to configure NDT."
#!/bin/sh
cd /usr/src/ndt-3.5.6/conf
sudo bash ./create-html.sh

echo "Housecleaning time."
sleep 15
cd /usr/src 
sudo rm -Rf ndt-3.5.6
sudo rm ndt-3.5.6.tar.gz
sudo rm web100-2.5.19-200802211940.tar.gz
sudo rm linux-image-2.6.24-web100-web100_2.6.24-web100-web100-10.00.Custom_i386.deb
sudo rm linux-headers-2.6.24-web100-web100_2.6.24-web100-web100-10.00.Custom_i386.deb

echo "Starting the server."
sudo /usr/local/sbin/fakewww >& /dev/null &
sudo /usr/local/sbin/web100srv -a --ip4 >& /dev/null &

```

---

### Post by dwhitney67 on 2009-11-13
There is a way to do this, but my knowledge on it is a bit rusty.

For your second script, remove the 'sudo' portions, because it will not be needed.

When the system is (re)booted, the scripts in /etc/rc#.d are invoked.  For systems that require networking and X11, this usually (almost always) involves /etc/rc5.d scripts being executed.

If you examine /etc/rc5.d directory, the script S99rc.local is called (that is, after S00policycoreutils, S01policykit, S05selinux, etc)... it is nearly one of the last to be called.

If you follow its link, you will notice that it is linked to /etc/rc.local.  It is within this file that you may specify (ie. call) your script.

Thus, adding your script to the /etc/rc.local would look something like:
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

if [ -x /path/to/Install-2.sh ]
then
     /path/to/Install-2.sh

     # comment-in the following IF required
     # unlink /path/to/Install-2.sh
fi

exit 0

```
Note the comment for the script to "commit suicide".  If your script is supposed to be a one-time only event, then something similar to what is shown above is necessary.  The alternative would be for your script to overwrite (ie restore) /etc/rc.local so that the statements shown above are not included.

---

### Post by dr_latino999 on 2009-11-13
> **dwhitney67 said:**
> There is a way to do this, but my knowledge on it is a bit rusty.

For your second script, remove the 'sudo' portions, because it will not be needed.

When the system is (re)booted, the scripts in /etc/rc#.d are invoked.  For systems that require networking and X11, this usually (almost always) involves /etc/rc5.d scripts being executed.

If you examine /etc/rc5.d directory, the script S99rc.local is called (that is, after S00policycoreutils, S01policykit, S05selinux, etc)... it is nearly one of the last to be called.

If you follow its link, you will notice that it is linked to /etc/rc.local.  It is within this file that you may specify (ie. call) your script.

Thus, adding your script to the /etc/rc.local would look something like:
**Code Block**
Note the comment for the script to "commit suicide".  If your script is supposed to be a one-time only event, then something similar to what is shown above is necessary.  The alternative would be for your script to overwrite (ie restore) /etc/rc.local so that the 

statements shown above are not included.

dwhitney, thank you for your informative response. I was almost literally banging my head on the desk trying to figure this out earlier and this is much simpler than anything I was thinking of. I will keep you informed of the outcome of my testing.

---

### Post by dr_latino999 on 2009-11-16
I tested out the code with a small pair of test scripts and on system reboot, the rc.local file is modified but the script it directs to does not run. Am I missing some minor thing?

**reboottest.sh**
```
#!/bin/sh
declare rc=/etc/rc.local
echo "#!/bin/sh -e" > $rc
echo "#" >> $rc
echo "# rc.local" >> $rc
echo "#" >> $rc
echo "# This script is executed at the end of each multiuser runlevel." >> $rc
echo "# Make sure that the script will "exit 0" on success or any other" >> $rc
echo "# value on error." >> $rc
echo "#" >> $rc
echo "# In order to enable or disable this script just change the execution" >> $rc
echo "# bits." >> $rc
echo "#" >> $rc
echo "# By default this script does nothing." >> $rc
echo "if [ -x /home/sysadmin/scripts/testingreboot.sh ]" >> $rc
echo "then" >> $rc
echo "/home/sysadmin/scripts/testingreboot.sh" >> $rc
echo "# comment-in the following IF required" >> $rc
echo "unlink /home/sysadmin/scripts/testingreboot.sh" >> $rc
echo "fi" >> $rc
echo "exit 0" >> $rc

```Which calls up.

**testingreboot.sh**
```

#!/bin/sh
echo "Testing reboot script"
mkdir /home/sysadmin/test1
mkdir /home/sysadmin/test2
mkdir /home/sysadmin/test3
echo "Done making test folders."

```

---

### Post by dwhitney67 on 2009-11-16
Since your 'reboottest.sh' script is re-creating /etc/rc.local, make sure that before the script exits, that it enables the execution bits of /etc/rc.local's properties.  In other words, add the following line:
```

...

chmod +x $rc

exit 0

```
Similarly, ensure that your script /home/sysadmin/scripts/testingreboot.sh is also executable; otherwise the if-condition in /etc/rc.local will fail, and your script will not be executed.

---

### Post by dr_latino999 on 2009-11-19
> **dwhitney67 said:**
> .  In other words, add the following line:
```

...

chmod +x $rc

exit 0

``` I followed your advice on the executable modifications and it worked flawlessly. I was able to to utilize this information and integrate it into a trio of scripts which takes a clean 8.04 LTS system and installs the Web100 and corresponding NDT software packages. If you want, you can see how much the scripts have changed since the initial presentation of the problem.

[B]Install1.sh
[/B]```
#!/bin/bash
#Begin Module 1
echo "Module 1: Do you want to configure the system network interface? [1: Yes][2: No]"
read answer
if [ "$answer" == 1 ]; then
    echo "Creating Network Interface File."
    echo "Stopping Network services"
    sudo /etc/init.d/networking stop
    echo "Location of the file to be stored."
    declare A=/etc/network/interfaces
    echo "Location file is to be saved: $A"
    echo "#The loopback network interface" > $A
    echo "auto lo" >> $A
    echo "What is the local IP address you wish to you?"
    read localipaddress
    echo "iface lo inet loopback" >> $A
    echo "#Primary Interface" >> $A
    echo "auto eth0" >> $A
    echo "iface eth0 inet static" >> $A
    echo "address $localipaddress" >> $A
    echo "What is the netmask?"
    read netmask
    echo "netmask $netmask" >> $A
    echo "What is the gateway?"
    read gateway
    echo "gateway $gateway" >> $A
    sudo /etc/init.d/networking restart
    echo "Networking settings are stored."
else echo "Carrying on then."
fi
#End Module 1
#
#Begin Module 2
echo "Module 2: This will install Web100 NDT support to the Ubuntu 8.04 32 bit Server operating system."
    echo "Checking for and then installing system updates."
    sudo apt-get update
    echo Y|sudo apt-get upgrade
#End Module 2
#
#Begin Module 3
echo "Module 3: Installing the necessary packages to compile kernel."
declare rc=/etc/rc.local
echo "#!/bin/sh -e" > $rc
echo "#" >> $rc
echo "# rc.local" >> $rc
echo "#" >> $rc
echo "# This script is executed at the end of each multiuser runlevel." >> $rc
echo "# Make sure that the script will "exit 0" on success or any other" >> $rc
echo "# value on error." >> $rc
echo "#" >> $rc
echo "# In order to enable or disable this script just change the execution" >> $rc
echo "# bits." >> $rc
echo "#" >> $rc
echo "# By default this script does nothing." >> $rc
echo "if [ -x /home/sysadmin/scripts/Install2.sh ]" >> $rc
echo "then" >> $rc
echo "/home/sysadmin/scripts/Install2.sh" >> $rc
echo "# comment-in the following IF required" >> $rc
echo "unlink /home/sysadmin/scripts/Install2.sh" >> $rc
echo "fi" >> $rc
sudo chmod +x /home/sysadmin/scripts/Install2.sh
sudo chmod +x $rc
echo "exit 0" >> $rc
echo "IMPORTANT - You will have to do a hard restart as the java screen likes to fail. [ENTER]"
read enter
    echo Y|apt-get install autoconf automake1.9 csh bison build-essential flex g++ libarchive-zip-perl libauthen-pam-perl libdb4.4-dev libio-pty-perl libpcre3 libpopt-dev libnet-ssleay-perl libtool libmd5-perl libcap-dev libreadline5-dev libimlib2-dev kernel-package libncurses5-dev lynx fakeroot wget bzip2 ncftp nmap openssl rcconf sun-java5-bin sun-java5-jdk unzip zip zlib1g-dev python2.5-dev libpcap0.8-dev traceroute
#End Module 3
```[B]Install2.sh
[/B]```
#!/bin/bash
#Setting up addition to be run after reboot after Java Crash
sudo dpkg --configure -a
sudo apt-get install -f -y
    echo Y|apt-get install autoconf automake1.9 csh bison build-essential flex g++ libarchive-zip-perl libauthen-pam-perl libdb4.4-dev libio-pty-perl libpcre3 libpopt-dev libnet-ssleay-perl libtool libmd5-perl libcap-dev libreadline5-dev libimlib2-dev kernel-package libncurses5-dev lynx fakeroot wget bzip2 ncftp nmap openssl rcconf sun-java5-bin sun-java5-jdk unzip zip zlib1g-dev python2.5-dev libpcap0.8-dev traceroute
#End Module 3
#
#Begin Module 4
majorminor=`uname -r | cut -f1,2 -d.`
KERNEL_VERSION=`uname -r`
MICROVERSION=`echo $KERNEL_VERSION | sed 's/^[^.]\+\.[^.]\+\.\([0-9]\+\).*/\1/'`
echo "Module 4: Installing new image and headers."
    cd /usr/src
    sudo dpkg -i linux-image-$majorminor.$MICROVERSION-web100-web100_$majorminor.$MICROVERSION-web100-web100-10.00.Custom_i386.deb
    sudo dpkg -i linux-headers-$majorminor.$MICROVERSION-web100-web100_$majorminor.$MICROVERSION-web100-web100-10.00.Custom_i386.deb
    #Setting up addition to be run after reboot
    declare rc=/etc/rc.local
echo "#!/bin/sh -e" > $rc
echo "#" >> $rc
echo "# rc.local" >> $rc
echo "#" >> $rc
echo "# This script is executed at the end of each multiuser runlevel." >> rc
echo "# Make sure that the script will "exit 0" on success or any other" >> $rc
echo "# value on error." >> $rc
echo "#" >> $rc
echo "# In order to enable or disable this script just change the execution" >> $rc
echo "# bits." >> $rc
echo "#" >> $rc
echo "# By default this script does nothing." >> $rc
echo "if [ -x /home/sysadmin/scripts/Install3.sh ]" >> $rc
echo "then" >> $rc
echo "/home/sysadmin/scripts/Install3.sh" >> $rc
echo "# comment-in the following IF required" >> $rc
echo "unlink /home/sysadmin/scripts/Install3.sh" >> $rc
echo "fi" >> $rc
sudo chmod +x /home/sysadmin/scripts/Install3.sh
sudo chmod +x $rc
echo "exit 0" >> $rc
#End Module 4
sudo shutdown -r now
```[B]Install3.sh
[/B]```
#!/bin/bash
#
#Begin Module 5
echo "Module 5: Continuing the install and setup of the Web100 packages."
    cd /usr/src
    echo "Downloading the Web100 Userland and then configuring it."
    wget http://www.web100.org/download/userland/version1.7/web100_userland-1.7.tar.gz
    tar -xvzf web100_userland-1.7.tar.gz
    cd web100_userland-1.7
    ./configure --enable-python
    make
    make install
    cd ..
    rm -Rf web100_userland-1.7
    rm web100_userland-1.7.tar.gz
#End Module 5
#
#Begin Module 6
echo "Module 6: Configuring and installing NDT."
    cd /usr/src
    echo "Downloading NDT package from Internet2 website."
    wget http://software.internet2.edu/sources/ndt/ndt-3.5.0.tar.gz
    tar -xvzf ndt-3.5.0.tar.gz
    cd ndt-3.5.0
    echo "Installing NDT package."
    ./configure
    make
    make install
    cd /usr/src/ndt-3.5.0/conf
    bash ./create-html.sh
#End Module 6
#
#Begin Module 7
echo "Module 7: Housecleaning time."
    cd /usr/src 
    rm ndt-3.5.0.tar.gz
    rm linux-image-2.6.24-web100-web100_2.6.24-web100-web100-10.00.Custom_i386.deb
    rm linux-headers-2.6.24-web100-web100_2.6.24-web100-web100-10.00.Custom_i386.deb
    echo "Starting the server."
    sudo /usr/local/sbin/fakewww -4 >& /dev/null &
    sudo /usr/local/sbin/web100srv -a --ipv4 >& /dev/null &
#End Module 7
#
#Begin Module 8
echo "Module 8: Do you want to setup FakeWWW to operate in Federated mode? [1: Yes][2: No]"
read answer
if [ "$answer" == 1 ]; then
    sudo bash /home/sysadmin/scripts/traceroute.sh
else echo "Very well then. If you choose to setup FakeWWW to operate in Federated mode at a later point you can find the setup script at /home/sysadmin/scripts/traceroute.sh"
fi
#End Module 8
#
#Begin Module 9
echo "Copying script for startup"
sudo cp /home/sysadmin/scripts/ndt /etc/init.d
cd /etc/init.d
sudo update-rc.d ndt defaults
sudo chmod +x ndt
#End Module 9
echo "Install completed."
```

---

### Post by dwhitney67 on 2009-11-19
I'm glad you got it working, however I must point out that you must be careful with liberal use of the 'chmod +x' statements.  I should have warned you in my earlier post that a regular user would be able to execute a script if the permission are set with the '+x'.

Don't get me wrong; this is great for the 'ndt' script, however for the install scripts you probably should set these such that only root can execute them.  For example, in Install1.sh:
```

chmod 700 /home/sysadmin/scripts/Install2.sh

```
Also, and on a different topic, you do not do anything significant (ie. exit) Install1.sh should the operator/user elect *not* to install.  You may want to revisit the else-block here:
```

...
else echo "Carrying on then."
fi

```

P.S.  On a 'virgin' Ubuntu system, /etc/rc.local has its permissions set to mode 755.  Note that the executable-privilege is set for all users.

---

### Post by dr_latino999 on 2009-11-19
> **dwhitney67 said:**
> I'm glad you got it working, however I must point out that you must be careful with liberal use of the 'chmod +x' statements.  I should have warned you in my earlier post that a regular user would be able to execute a script if the permission are set with the '+x'.

Also, and on a different topic, you do not do anything significant (ie. exit) Install1.sh should the operator/user elect *not* to install.  You may want to revisit the else-block here:

 Noted, but with user execution I am not so worried. Once these systems are in place, they will be headless only accessible through the administrative SSH account, or through a FakeWWW webpage as shown here -> [http://nitro.ucsc.edu](http://nitro.ucsc.edu). It will be something to look into but, trust me, the amount of time I've spent reloading snapshots of this box on my laptop makes me want to say "So be it, leave it up to the security team to place it behind umpteen million firewalls."

Install1 lacks an exit command, as those packages must be installed but everytime the Java User Agreement comes up the system does not respond till after a hard reboot. I haven't found a way around it yet unfortunately, so Install 2 automatically picks up where the hard lock occurs where the User Agreement reloads and you are able to correctly select "I Agree I will not use Java to make WMDs bla bla bla."

---

