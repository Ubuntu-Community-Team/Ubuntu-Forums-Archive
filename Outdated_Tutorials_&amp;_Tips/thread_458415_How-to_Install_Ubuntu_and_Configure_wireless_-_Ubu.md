---
title: "How-to: Install Ubuntu and Configure wireless - Ubuntu 7.04 on a Dell C610 Laptop"
date: 2007-05-29
forum: Outdated Tutorials &amp; Tips
---

### Post by adampyre on 2007-05-29
Hello:

I decided to make this how to because this is the third time I have had to re-install Ubuntu on my laptop for various reasons and I would like to also have a guide in the future for myself if I have to do it again. I also thought others could benefit from this, especially newbies like me.

In this guide, I will walk you through how I:

Prepare the partitions
Install Ubuntu
Configure Ubuntu for my particular wireless card, a Linksys Wireless-G WPC54G ver. 3


First, I used the GParted live CD to set up my partitions. I have had random luck with Ubuntu's built in partitioner (who knows, it could be the same as GParted for all I know..) but the last 2 times I've gotten it to work if I created a primary partition and a swap partition. I am not quite certain about Linux, but I know with Windows, they say to make your swap partition as follows: you amount of ram * 1.5. So, I created a primary Linux filesystem partition and a swap that is 1.5X my memory.

After that, I boot into the Ubuntu 7.04 live CD and click the install icon on the desktop. I go through the settings and get to the partitioner. Take the manual settings as the partitions are set up, but here is where you will want to mark your primary partition as root ("/"). I also clicked the format check box. I think this is redundant but I am paranoid. Note you can't format the swap partition.

So let the installer run and there you go. Ubuntu is installed. But there is still work to do.
upon logging into Ubuntu, the first thing I will want to do is set up my internet access. This is the hardest as my network card is a PCMCIA Linksys Wireless-G Notebook Adapter, WPC54G ver. 3. The Ubuntu Kernel doesn't automatically set it up, but I have had success getting it to work using the proprietary drivers from Linksys w/NDISWRAPPER. But before we can go here, we need build-essentials installed for NDISWRAPPER to work. Luckily, build-essentials is on the CD 
(but now installed by default? I'm new to Linux so I don't understand.)

So, how to get the WPC54G ver. 3 to work:

log in to Ubuntu. open up a terminal. make sure your ubuntu live CD is in the drive. type:
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential

it'll want you to confirm, press yes and install.

So now build-essential is installed, we can move on to ndiswrapper. Since ndiswrapper isn't on the CD and we don't have net access we have to get it on to the computer. I use my pen drive to move files between a computer that had net access and my laptop we are setting this up on. 

So, get NDISWRAPPER from here: [http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

download it to your pen drive.

while we're at it, we might as well get the driver for our PCMCIA card as well. For my particular model, the WPC54G ver. 3.    I got it from Linksys here: [http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859842300&packedargs=sku%3DWPC54G&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4230042300B01&displaypage=download#versiondetail](http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859842300&packedargs=sku%3DWPC54G&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4230042300B01&displaypage=download#versiondetail)

Ok, so we need to take the pendrive over to Ubuntu and install NDISWRAPPER and then the drivers.

First, I copy the ndiswrapper tar and the linksys zip over to my desktop. Leave a copy on your pendrive or backed up to an easily accessible area as you may find yourself re-installing ubuntu one day and will want to shorten the process.....

ok, right click the icon for ndiswrapper and hit extract here. then go to a terminal and point your present working directory to the desktop. (cd Desktop) the cd to the ndiswrapper directory.

type:
sudo make uninstall
sudo make (this may take a minute or so)
sudo make install

now ndiswrapper should be installed. test it by typing ndiswrapper at the prompt. If it gives you a list of options for the command you're set. Now to install the drivers with ndiswrapper.

right click the icon for the WPC54G driver on the desktop and hit extract here. We need the .inf file that is located in the same folder as the .cat and .sys file in the NT folder. Change to this folder from the file you just unzipped. Now to use NDISWRAPPER to install the drivers:

type:
sudo ndiswrapper -i LSBCMNDS.inf
you should see several messages stacked about forcing parameter etc etc from 0 to 2. I got 5 of them myself. Then I check to see if ndiswrapper took by typing:
sudo ndiswrapper -l
it should show the driver now installed and device present. it should also show something about the bcm43xx alternate driver. We need to blacklist this driver to keep the system from using it so it uses the driver we just
 installed. To do this, type:
sudo nano /etc/modprobe.d/blacklist
scroll to the bottom, you can add a comment (#) to note what this is for future reference if you wish. You'll probably never look here again anyway.

at the bottom, type:
# get rid of fallback wireless driver
blacklist bcm43xx

hit ctrl + o to save and ctrl + x to exit. 

finally, in the terminal, type:

sudo modprobe ndiswrapper

your wireless should be working. Left click the network icon in the notification area and you should see your wireless network listed. Connect to it. If you don't see anything, reboot the computer. boot to the hd if the live cd is still in. Hopefully it is there when you start back up.

Update! I forgot to mention, if everything works and you want it to automatically load your configuration on each startup, remember to type "ndiswrapper -m" in a terminal to write the configuration for modprobe as this will ensure your configuration is loaded upon each boot.

So all that and we have Ubuntu installed and networking going. I hope this was some help.

---

### Post by mentar on 2007-06-17
Thanks a lot for the how-to adampyre!
I got mine working except the "sudo modprobe -m" doesn't seem to have cause the module to be loadaded on restart (or at least I still have to run "sudo modprobe ndiswrapper" to get the connection to work)
Any suggestion on how to get it working?
Thanks a tonne!
Mentar

---

### Post by TheEmb3rEgg on 2007-06-26
Ithink the OP forgot to mention you'll need administrative privileges to do that last command. Type the following in terminal:
sudo ndiswrapper -m

It should work now.

---

### Post by alabasterjones on 2007-07-03
You are like unto a GOD. This worked perfectly the first time and for a NETGEAR WG511v2 at that. Thank you

---

### Post by daMacroGuy on 2007-11-30
THANK YOU, THANK YOU, THANK YOU! I'm a newbie to Ubuntu and your instructions were PERFECT. I got my Linksys wireless card working after a reboot.

For the record, my wireless card was version 1.2 and I'm running Ubuntu 7.04 (Fiesty Fawn) on a Dell Inspiron 1100.

---

### Post by janosp on 2008-07-14
THANK YOU! This worked like a charm!!
I had trouble getting a zip file for the driver, they were all .exe files.
I ended up using the drivers for the Marvel mrv8335 card, and it worked beautifully!
j

---

