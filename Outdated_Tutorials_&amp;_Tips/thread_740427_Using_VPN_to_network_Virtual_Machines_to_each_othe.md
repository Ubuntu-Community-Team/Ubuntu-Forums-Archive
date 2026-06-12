---
title: "Using VPN to network Virtual Machines to each other and to the Guest OS"
date: 2008-03-30
forum: Outdated Tutorials &amp; Tips
---

### Post by arronf on 2008-03-30
Using VPN to network Virtual Machines to each other and to the Guest OS

I find this to be one of the easiest and securest ways of networking virtual machines (VM) to each other, and to the host OS (operating system).  It uses Virtual Private Network software (VPN) called hamachi, which is free to download, however it is freeware not free software (for more information about free software visit this web site [http://www.fsf.org](http://www.fsf.org))


I in my day-to-day studies, use a lot of virtual machines and i found bridging the VM sometimes to be a little complicated and maybe not the best solution.  I came across this free solution and i have used ever since, for the purposes of this guide if will setup a virtual LAMP server, however your limited to your own imagination for other uses of this.  The reason i have chosen to use a virtual LAMP server, is that i can load the VM, it is only accessible via the VPN software, i can work on it from my host OS, when i'm finished i close the VM down and i the server by default is no longer accessible.  I have also used it to network Linux Host OS, to Windows XP Guest OS for my course, which means i can run a number of tools against the XP from Ubuntu as though i was on the same network (the actuality of this is that i am actually on the same network).  The great benefit in my mind for doing this with the LAMP test servers and for networking test Guest OS, is when the VPN software is off then and your Virtualisation software is turned off then the server is no longer there, your system in essence doesn't have a server installed, and any routes to that server are closed down.  I have also used the VirtualBox software from Innotek, there is a free software version licensed under the GPL (GNU Public License) more information about the GPL can be found at the web address [http://www.gnu.org](http://www.gnu.org).  However this process should work on any virtualisation software such as VMWare.  You can find out more about VirtaulBox from this web address [http://www.virtualbox.org](http://www.virtualbox.org) 

If you have VirtualBox installed, then just skip this step and move to the next ine

Step 1 installing VirtualBox Ubuntu 7.10

Installing VirtualBox is pretty easy and i'll not go into detail on howto install it, you kind find how to install with a quick search about with your favourite search engine.  I tend to use the Linux version of Google and that can be found here [http://www.google.com/linux](http://www.google.com/linux), however for the purposes of this guide i've added instructions on install VirtualBox on Ubuntu 7.10, you will need to make sure you have universal repository is setup in your software sources, this can be done by editing your source.list file (sudo gedit /etc/apt/source.list) or by going to System > Administration > Software Sources and clicking on the Community-maintained Open Source software (universe) option in the application window that comes up.  Make sure to update your system by placing this code in your command line terminal 

sudo aptitude update

once that is done place the following code into the command line terminal

sudo aptitude install virtualbox-ose virtualbox-ose-source

This will install VirtualBox's community open source edition on to your system, the we need to install the VirtualBox OSE kernel modules this can be done by placing the following code into the command line terminal

sudo aptitude install module-assistant
sudo m-a prepare
sudo m-a a-i virtualbox-ose
sudo modprobe vboxdrv

(if you get an error similar to this one FATAL: Error inserting vboxdrv (/lib/modules/2.6.22-14-generic/misc/vboxdrv.ko): Invalid argument
 then please visit this site [http://ubuntuforums.org/showthread.php?p=4589941](http://ubuntuforums.org/showthread.php?p=4589941) for the fix )

To load the VirtualBox OSE Kernel module permanently at boot up time, you will need to edit your /etc/modules file.  I have used gedit but you can use any text editor you wish

sudo gedit /etc/modules 

and add the following code to the bottom of the list of modules in the text file that appears

vboxdrv
tun

Save and close the text file, you have added two modules, vboxdrv for virtual box and tun is needed for a later step, now you will need to add your self to the vboxusers group.  Place the following code into the command line terminal, remembering to change [your username] with your one

sudo adduser [your username] vboxusers

There is also a very nice howto guide at this web address for installing VirtualBox [http://linuxmint.com/forum/viewtopic.php?f=42&t=8453](http://linuxmint.com/forum/viewtopic.php?f=42&t=8453) seems a little more comprehensive than mine

You may need to reboot for all of that installation and configuration to take affect.

Once you have VirtualBox installed you can then install an OS of your choice, by creating a new virtual imagine and mounting your install media iso as a CD-Rom.  I used Debian netinstall for my LAMP more information about debian can be found at this web address [http://www.debian.org](http://www.debian.org) and you can download a copy of the netinstall iso from this web address [http://www.debian.org/CD/netinst/](http://www.debian.org/CD/netinst/)

Once your install is complete you will now need to install Hamachi on both your Guest OS and your Host OS, if you haven't installed SSH (Secure Shell) on your host OS then my advice would be to do so but it's not strictly necessary, just makes it easier later on to be able to SSH into your Guest OS from your Host OS whenever you choose.  (sudo aptitude install ssh)

Installing Hamachi can seem difficult on a Linux System (It's an.exe file and does nearly everything in Windows, grrrrr) but i have come across this script to install Hamachi with everything on Ubuntu/Debian systems, you can find more information about install Hamachi manual from their forums, which can be found at this web address [https://forums.hamachi.cc/](https://forums.hamachi.cc/)

If you search about on their forums you should be able to find some instruction for installing it on different distro's and architecture if yours differs to mine.

Step Two Installing Hamachi on Ubuntu/Debain

One of the first steps is to set up tunneling in your kernel this can be done by placing the following code into your command line terminal

sudo modprobe tun

Then you will need to make sure you edit your your /etc/modules to make sure tunneling module is loaded at boot up time, by placing the following code into the command lone terminal.  As i've stated i've used gedit but feel free to use whatever text editor you want, if you've followed my instructions for installing virtualbox then you will not need to do the next step 

sudo gedit /etc/modules

In the file that opens add the following line

tun

We will also make sure that we have set up valid tunneling node, you can do this by issuing the following code into command line terminal

ls /dev/net/tun

If you get an error message similar to this “No Such File or Directory” then you will need to create the tunnel by issuing the following code into the command line terminal 

sudo mkdir /dev/net
sudo mknod /dev/net/tun c 10 200

Then we need to install the hamachi you can find the latest version for all platforms from this web address [https://secure.logmein.com/products/hamachi/list.asp](https://secure.logmein.com/products/hamachi/list.asp)

In your command line terminal then and cd in to the directory that you downloaded hamachi into then you will need to extract the file by issuing the following code into the command line terminal.  Remember if you've downloaded a different version of hamachi than hamachi-0.9.9.9-20-lnx.tar.gz change the codes to the match yours

tar -zxvf hamachi-0.9.9.9-20-lnx.tar.gz
cd hamachi-0.9.9.9-20-lnx

Then you will need to install the decompression software

sudo aptitude install upx-ucl-beta

Then we'll install hamachi 

sudo make install
sudo upx-ucl-beta -d /usr/bin/hamachi
sudo tuncfg/tuncfg

Then we'll configure hamachi group so that anyone that is a member of that group can start hamachi, place the following codes into your command line terminal.  First like set up the group, issue the following codes into the command line terminal

sudo groupadd hamachi

then let's add your username to the the group

sudo gpasswd -a YOURUSERNAME hamachi

and then we'll add root to the group as well

sudo gpasswd -a root hamachi

Then we need to configure the socket so it has the right user permissions 

sudo chmod 760 /var/run/tuncfg.sock

and then change the group of the socket to hamachi

sudo chgrp hamachi /var/run/tuncfg.sock

Then let's setup your nickname, and your VPN network

So let's set up a initial hamachi configuration by issuing the following code into a command line terminal

sudo hamachi-init -c /etc/hamachi

you should see something like this

// begin example screen

Initializing Hamachi configuration (/etc/hamachi). Please wait ..

  generating 2048-bit RSA keypair .. ok
  making /etc/hamachi directory .. ok
  saving /etc/hamachi/client.pub .. ok
  saving /etc/hamachi/client.pri .. ok
  saving /etc/hamachi/state .. ok

Authentication information has been created. Hamachi can now be started with
"hamachi start" command and then brought online with "hamachi login".

// end example screen

Then it's time to start hamachi by issuing the following code into the command line terminal

sudo hamachi -c /etc/hamachi start

Then we need to setup a nickname, this can be anything you choose but i tend to set up the nickname as the host name of the machine

sudo hamachi -c /etc/hamachi set-nick "YourChosenNickname"

then we need to login into hamachi this can be done by issuing the following code into the command line terminal

sudo hamachi -c /etc/hamachi login

Then we can create a new VPN by issuing the following code into the command line terminal

sudo hamachi -c /etc/hamachi create [desirednetworkname-withoutbrackets] [desiredpassword-withoutbrackets]

You can connect to a desired network by issuing the following code into a command line terminal 

sudo hamachi -c /etc/hamachi join [networkname-withoutbrackets] [networkpassword-withoutbrackets]

Lastly you will need to go online to be able to interact with the VPN, you can do this by issuing the following code into the command line terminal

sudo hamachi -c /etc/hamachi go-online [networkname-withoutbrackets]

I would certainly suggest doing the above on your host OS, but you can use this lovely script for your VM's works very quickly and takes most of the hassle away.  It can be found at this web address [https://forums.hamachi.cc/viewtopic.php?t=16590&highlight=ubuntu](https://forums.hamachi.cc/viewtopic.php?t=16590&highlight=ubuntu) i have this script saved and it a most have in my tools arsenal.  It also makes it very easy to install the GUI's, the reason that i have not used the script on the host, is that the script doesn't configure the permissions part, and i like to be able to run it as a normal user.  I'm not so bothered about that on a VM because once i'm done i turn it off.  If you want to set the guest OS by hand then follow the above instructions, and instead of creating a network, join your network.

Once your virtualmachine or in my case my virtual lamp server is connected to the VPN, issue the following code into the host OS's command line terminal 

hamachi get-nicks

followed by 

hamachi list

you should get a similar output as this

// begin example screen

 * [finux-LAMP]
     * 5.192.165.195    finux-box-VitrualDebianLA  192.168.0.2:32984
       5.193.7.208      finux-box-virtualUbuntuSe
       5.193.42.74      finux-box-virtual-ubuntu 
     * 5.193.152.113    finux-box-one              192.168.0.2:32798

// end example screen

you can point your web browser to the virtual lamp either directly by typing in the ip address in my case 5.192.165.195, but i edited my /etc/hosts by issuing the following code into the command line terminal

sudo gedit /etc/hosts

and add the IP address to your host file with name you want so in my case

5.192.165.195	vlamp

save and exit, now i just type vlamp into the url var and i get the web server.  You can also ssh into it if you installed ssh 

Once you have done this you can follow the above on each VM and have them connect to your newly created VPN, if your using Windows then you can download hamachi from this web address [http://hamachi.en.softonic.com/](http://hamachi.en.softonic.com/) .

If you setup a telnet server on your Windows VM and then you can telnet from your bash to your Windows box.

This is just something i use every day, it may or may not be of use to you, i would treat it as a proof of concept and nothing more.  Please feel free to add, change, manipulate it.  I'll apologies for any typo's now, and all that it looks complicated now once hamachi is installed on your Host, and with the script you can connect to your VM's without much work at all, you don't need to worry about bridging, or change any of your connection parameters.  If your type ifconfig you will see the dummy network interface alongside your other network devices.

Hope this helps someone, and like i say you can use the above to do whatever you want.

---

