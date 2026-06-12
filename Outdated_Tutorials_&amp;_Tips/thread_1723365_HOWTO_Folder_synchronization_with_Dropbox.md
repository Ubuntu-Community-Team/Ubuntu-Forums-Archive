---
title: "HOWTO: Folder synchronization with Dropbox"
date: 2011-04-07
forum: Outdated Tutorials &amp; Tips
---

### Post by orodoni_le on 2011-04-07
Probably some of you already knows Dropbox. A proprietary application to synchronize and share your files. Is a non-free software, but it's quite powerful and useful, specially in Linux, although it can be used to share data with Windows, Mac-OS, and even with mobile phones.

Dropbox is both, the name of the application, and the name given to your "sharing box", which is a folder or directory where you copy all of the information that you want to share. This tutorial will show you how to install Dropbox, and set up to synchronize folders outside your "dropbox" directory. I write with capital D the _Dropbox_ software, while I use _dropbox_ for the sharing folder. This avoid having multiple copies of the same files.

For example, I have a Desktop at work and a netbook for my personal use. At work I use Fedora, while my netbook uses Linux Mint Debian Edition. With my setup, I can modify a file at work, and then continue the edition with my netbook, on a local copy that is exactly the same as the latest version generated at work. It also works in the opposite direction. Changes made in the netbook will be forwarded to the Desktop. You can achieve similar functionality with VPN access to your work server, bu you have to keep track of the changes by yourself. Dropbox manages this function, keeping the latest version, and avoids the configuration of VPN clients, which can be troublesome, and not always available (I went to an airport, and the VPN access was blocked by the firewall).

Dropbox is initially free, with a Dropbox size starting at 2GB. The size increases if you invite people to join. Each new member will give you 250MB, or 500MB if you are an academic user.

Here's the procedure:

[size=4]**1. Create a Dropbox account**[/size]
Go to [this link and create your Dropbox account](http://db.tt/NUAZODH). Basic information, just email and password. The above it's my referral link. If you use it, it will increase the size of my online space. Thanks!

After you register, if you are an academic user, go to [http://www.dropbox.com/edu]("http://www.dropbox.com/edu") and put you academic email address. It will send you a confirmation email, and after that, you increase your referral bonus from 250MB to 500MB.

[size=4]**2. Install Dropbox**[/size]
You can go to [this site](https://www.dropbox.com/downloading?os=lnx) to download Dropbox. They provides binaries for Ubuntu and Fedora, in both 32 and 64 bits. Depending of your active software source, it could also be downloaded from the repositories.
In Ubuntu, Debian, LMDE, type in the terminal
```
sudo aptitude search dropbox
```
It should list two packages: *dropbox* and *nautiuls-dropbox*. In this case, install them both with
```
sudo apt-get install dropbox nautilus-dropbox
```
If this packages are not listed in the search (as it was in my case), do the following. As root, create a file *dropbox.list* inside your */etc/apt/sources.list.d/* directory
```
su
cd /etc/apt/sources.list.d
touch dropbox.list
```
Open this file with your favorite text editor (vim, emacs, gedit, etc, ) and paste the following line
```
deb http://linux.dropbox.com/ubuntu maverick main
```
Yes, I'm using LMDE and installing and Ubuntu repo. It works. Then, we should add the key to this repo. Still as root, type
```
apt-key adv --keyserver pgp.mit.edu --recv-keys 5044912E
```
Finally, update your packages list, and install Dropbox
```
apt-get update
apt-get install dropbox nautilus-dropbox
```

[size=4]**3. Run and configure Dropbox**[/size]
Run Dropbox from the menu, and a GUI will guide you through th basic setup. It will download and install the Dropbox daemon, ask your account information, your subscription level: Basic(free 2GB), Pro 50 ($100/yr 50GB) or Pro 100($200/yr 100GB), and the the placement of your *dropbox* directory, by default in $HOME/Dropbox. If you select a different folder, the installer will create automatically the corresponding /Dropbox directory.

Now your Dropbox will be ready to use. Just drag your files into your dropbox, and it will be available for you in any other machine that you configure Dropbox, or you can access them through the web interface, or share it with someone else. The sharing options appears with right click on the file or folder, thanks to the nautilus-extension

[size=4]**4. Synchronize folder outside your dropbox**[/size]
Let's suppose that your dropbox directory is $HOME/Dropbox, and that you want to synchronize the folder $HOME/Pictures/Vacations.
Using the Nautilus file manager, search the desired folder ($HOME/Pictures/Vacations). Right click on it and create a link (Make Link). Rename the newly created link file to a meaningful name (Vacations-synch), cut the file and paste it into your Dropbox.

I your other computer, with Dropbox running and configured, you should see inside the dropbox directory a Vacations-synch folder. Create a link to this folder, cut it from the dropbox, and paste it in the desired location (i.e. $HOME/Desktop). You can rename this link file (i.e Share-Vacations)

Then, in the Desktop of the 2nd computer should have a Share-Vacations folder with the same files than in the $HOME/Pictures/Vacations of the first machine. Any changes to the file structure in any of these folders (add/delete files, file edition, etc..) should be forwarded shortly (sometimes immediately) to the other folder.

From the dropbox directory of any of the computers, you can even share this folder with someone else, allowing them to add files to your $HOME/Pictures/Vacations and $HOME/Desktop/Share-Vacations folder. Excellent function to share pictures with the family and create an album with pictures taken by different people. Or it can be used in collaborative work, allowing multiple users to edit a document, project, report, article, book, thesis, etc...

I hope this has been helpful.

---

### Post by rMatey on 2011-04-07
Just a note to let you guys know that I really like Dropbox.  It syncs everything between my Linux netbook for tech school, Linux on my laptop, and my Linux and Windows Desktops.
  If you try and like it, how about clicking on my link for extra space for me, too.
[http://db.tt/VOuIT5R](http://db.tt/VOuIT5R)
 I would appreciate it a lot!!

---

### Post by fooey on 2011-04-07
> **rMatey said:**
> Just a note to let you guys know that I really like Dropbox.  It syncs everything between my Linux netbook for tech school, Linux on my laptop, and my Linux and Windows Desktops.
  If you try and like it, how about clicking on my link for extra space for me, too.
[http://db.tt/VOuIT5R](http://db.tt/VOuIT5R)
 I would appreciate it a lot!!

hah. you just couldn't resist! 

[http://db.tt/yCQkF32](http://db.tt/yCQkF32)
^thanks to anyone who signs up via my referral link

remember, it's free & an amazing service

---

