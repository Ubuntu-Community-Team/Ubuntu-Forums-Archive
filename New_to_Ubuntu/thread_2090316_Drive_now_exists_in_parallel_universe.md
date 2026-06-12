---
title: "Drive now exists in parallel universe"
date: 2012-12-01
forum: New to Ubuntu
---

### Post by Elect GMax on 2012-12-01
I successfully installed Ubuntu on a hard drive. That hard drive now exists in a parallel universe and cannot interact with storage devices from this one.

Allow me to explain. There are two identical 74GB WD Raptor hard drives connected to this computer. One has Ubuntu 12.04 and the other has Windows XP Professional with Service Pack 3. When I boot into Windows, it can see everything except the hard drive that Ubuntu is on. When boot into Ubuntu, I can't even figure out what it sees and what it can't see because I can't find a list of devices connected to the system. Can it see the windows drive? Can it see the DVD-ROM drive? Could it see an external drive if I plugged one in? I have no idea! The built-in Help menu isn't helping! Is there ANY way to get information onto this drive without going through a wired connection to the Internet?

---

### Post by ibjsb4 on 2012-12-01
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

sudo lshw

---

### Post by dli7319 on 2012-12-01
Ubuntu can see everything (cd, hdd). Windows can't see ubuntu because ubuntu uses ext4. Typically hdds are /dev/sda1

---

### Post by squakie on 2012-12-02
You can also just open disk manager and see what it says there.  Your Windows drive is probably listed as something like "x.x m/g/tb" when you just use the file manager to look.  If not, it just may not be getting mounted at boot.

---

### Post by grahammechanical on 2012-12-02
You do not say what version of Ubuntu you are using. So, it is not possible to give you accurate directions.

In Ubuntu the File Manager is called Nautilus. In Ubuntu 12.04 and 12.10 and even some earlier versions the File Manager is loaded by clicking the folder icon at the top of the Launcher - the panel on the left of the screen.

You need to open the View menu and make sure that there is a tick mark against Show side Panel. You should have a side panel that will list devices - hardisks. CD/DVDs.

In 12.04 drives/partitions are called File Systems and we are told the size of them.

Regards.

---

### Post by irv on 2012-12-02
> **Elect GMax said:**
> I successfully installed Ubuntu on a hard drive. That hard drive now exists in a parallel universe and cannot interact with storage devices from this one.

Allow me to explain. There are two identical 74GB WD Raptor hard drives connected to this computer. One has Ubuntu 12.04 and the other has Windows XP Professional with Service Pack 3. When I boot into Windows, it can see everything except the hard drive that Ubuntu is on. When boot into Ubuntu, I can't even figure out what it sees and what it can't see because I can't find a list of devices connected to the system. Can it see the windows drive? Can it see the DVD-ROM drive? Could it see an external drive if I plugged one in? I have no idea! The built-in Help menu isn't helping! Is there ANY way to get information onto this drive without going through a wired connection to the Internet?
Yes it would be nice to know what version of Ubuntu you are using. But most likely if you installed the base ubuntu with Unity you will have a File Manager that is called Nautilus.
[ATTACH]228083[/ATTACH]
If you look on the left side you will see your Bookmarks which are all your drives. Now on my screen shot I do not have any windows drivers because I do not have windows installed.
Now being new to Ubuntu you must remember that Linux does not use drive letters like windows. You won't have the "C" or "D" or any other drive letters. Your drive is set up like my screen shot from gparted.
[ATTACH]228084[/ATTACH]
If you have two drives then you might see sda and sdb. Also your formats might be NTFS for windows and Ext4 for Ubuntu. gparted is a tool for changing your hard drive so be careful with it if you do not know what you are doing. Do not chance things. It does not come installed on Ubuntu you need to install it. You can do it from the software center or from a terminal.by typing.
```
sudo apt-get install gparted
```
It will ask for your password because you are doing this as super user. The sudo means super user do. Then you are telling it to get the apt and install the gparted, which is the app you want to install. After you do this a few times it starts to make sense. 
Yes, Linux is different then Windows, but I find it easier now that I have been using it. By the way I don't use Windows any more because Linux is much better.
I hope this helps you in understanding the differences in the two OS'.

---

### Post by mcduck on 2012-12-02
> **Elect GMax said:**
> I successfully installed Ubuntu on a hard drive. That hard drive now exists in a parallel universe and cannot interact with storage devices from this one.

Allow me to explain. There are two identical 74GB WD Raptor hard drives connected to this computer. One has Ubuntu 12.04 and the other has Windows XP Professional with Service Pack 3. When I boot into Windows, it can see everything except the hard drive that Ubuntu is on. When boot into Ubuntu, I can't even figure out what it sees and what it can't see because I can't find a list of devices connected to the system. Can it see the windows drive? Can it see the DVD-ROM drive? Could it see an external drive if I plugged one in? I have no idea! The built-in Help menu isn't helping! Is there ANY way to get information onto this drive without going through a wired connection to the Internet?

Linux doesn't list hardd rives with drive letters like Windows does, which is probably what's causng your confusion. Instead all connected and accessible drives and partitons are simply added to one and the same filesystem hierarchy.

Ubuntu of course is able to see the drive it's installed on. Depending on the partitoning you used when installing, that drive appears as the root of your filesystem ("/") and the swap aprtition (which you don't need toa ccess yourself). And of course any other separate partition you might have created ("/home", for example).

And like already mentined, Windows is only able to see Microsoft's own filesystems, FAT and NTFS, so even though it will see the drive you used for UBuntu, it will not appear in the file manager in Windows.

Anyway, youc an use the Disk Management-tool in Ubuntu to check the connected drives, although any drives and partitions recognized should simply appear in the file manager in Ubuntu.

---

### Post by Bartender on 2012-12-02
If you're running 12.04, Windows partitions show up in a different way than before.  I attached a screenshot of my Windows partition on a "traditional" dual-boot.  Go to the Launcher (that vertical list of icons on the left-hand edge of the primary monitor) and click on Home Folder.

Once you're in Home Folder, devices that Ubuntu sees will be listed in the upper left corner.  Note that Ubuntu doesn't make a big deal over whether they're "devices" or just "partitions".  

If I pop a CD in, then the Home Folder pops up, showing that media in the same corner.

To go one step further, I plugged a HDD into the PC's hot-swap rack.  Within a few seconds it shows up in Home Folder too.  

In the attached screenshot, "Free Agent" is the HDD I plugged into the hot-swap rack.  The drive was pried out of a Seagate Free Agent external enclosure and still identifies itself as such.

Next is the CD.  I just grabbed the first thing I could find, which was a bootable GParted LiveCD.

At the bottom are the internal dual-boot HDD's two Windows partitions;  94GB Filesystem & OS_TOOLS.

As far as I know, that's textbook 12.04 behavior.  Are you getting something different?

---

