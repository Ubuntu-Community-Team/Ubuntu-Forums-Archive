---
title: "HowTo: Backup Passworded Windows Accounts"
date: 2007-03-01
forum: Outdated Tutorials &amp; Tips
---

### Post by radiohead on 2007-03-01
[http://thresholdofthought.com/?p=4](http://thresholdofthought.com/?p=4)

In computer repair, data backup is obligatory. You may ask a customer if there is data to be backed up and they will say no, not knowing what they are saying exactly. To them, data isn’t the Word documents or speadsheets in their My Docs. Those are “objects” of a sort. Any competent computer tech knows this and will at least make sure there is nothing in the My Docs or on the desktop that could possibly cause a problem if lost. Then they realise that they can’t get into the account that needs backing up, whether in the computer itself, or with the HDD in a server meant for backing up data. There are two possible ways that I know of to get the data without asking the customer for the password. Firstly, the Administrator account, which should be basic knowledge to a computer tech. The second deals with a more hands on way of getting the data backed up. This is also the reason my boss has the servers at my shop dual-booting Ubuntu Linux. You don’t have to install Ubuntu to your server for this to work, their LiveCD works scrumptrulescently with this, and if you aren’t comfortable with Linux, then it is right up your alley.

First off, you need to have an ISO burner and a blank CD. Preferably a Sharpie also, because you will want to label it. It will become a part of your toolkit after this. For an ISO burner, I would recommend Alex Feinman’s ISO Recorder. It is free and has never failed me, it even creates ISOs. I am assuming you are working on PCs here, so you will want to download the i386 ISO for Ubuntu here. Burn the ISO to the disc and you are ready to go.

Next, you need to understand how Linux depicts hard drives. There is no C:, D:, etc… You have devices, which are kept in the /dev folder of your root, or / (the equivalent of C:). Your master drive will almost always be /dev/hdax, x being the partition number. Generally speaking, /dev/hda1 will be where your master hard drive’s OS will be installed to. Your slave drive will be /dev/hdbx. Now if you keep your hard drives on your secondary channel, which isn’t a smart move in the first place, /dev/hda turns into /dev/hdc and /dev/hdb turns into /dev/hdd. Hopefully, you catch the gist of this and will realise that because your CD drives are on your secondary channel, your master and slave CD drives will be /dev/hdc and /dev/hdd, respectively. After that, you probably have a RAID going. That starts at /dev/hdex, and continues along the alphabet. Now this is all for IDE.

SATA is a bit different, but nothing major. SATA is referred to as /dev/sdax, given this is the first SATA channel. You should still hook your CD drives up in your secondary IDE channel, even if your master/slave drives are on SATA, that’s just good practice. All the rules for IDE apply to SATA after that. The more you add to SATA, the higher up in the alphabet the drive gets.

Now, you should know enough about how Linux detects and refers to hard drives, so lets get started with backing this puppy up. Put the drive to be backed up in the server/computer however you want, I will cover most of the ways you can put it in, be it master backing up to slave, slave to master, RAID to master, etc… Take that Ubuntu CD you just burned and put it in your CD drive and make sure your computer will boot to it. Restart your computer and when the Ubuntu screen pops up, select “Start or Install Ubuntu”. This will start the LiveCD. Now, because it is running completely from your RAM, it will take a bit longer than if actually installed on a HDD, so don’t think that that is the actual boot time.

Once booted fully, you will have a pretty GNOME desktop going on. First, we need to fire up the terminal. To do that, you need to look up in the top left corner and click Applications > Accessories > Terminal. A text box similar to cmd will come up. This serves a lot more function than Windows’ cmd as it is far more developer-oriented. Next, we will create to directories in your home folder (which is very much like your My Docs folder on Windows). Copy and paste (or type if you are into that kind of thing) these commands in to the terminal.

mkdir master_mount backup_mount

This creates two directories in your home folder, master_mount, which we will mount the hard drive that we copy the backups to, and backup_mount, which we will mount the hard drive that is to be backed up.

Now, this section is if your hard drive is formatted NTFS.

Sadly, Ubuntu doesn’t come with NTFS read/write support right out of the box, so you will need to install a 3rd party program called NTFS-3G. You can get it after editing a simple text file, so lets do that. We will open up the sources.list file which contains the repositories of the programs that Ubuntu can download. I won’t get into that, so just trust me. ;-)


sudo gedit /etc/apt/sources.list

At the end of the file, copy and paste this line to the end.


deb [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) edgy main main-all

Then, copy and paste this set of commands and you will be good to go.


wget [http://flomertens.keo.in/ubuntu/givre_key.asc](http://flomertens.keo.in/ubuntu/givre_key.asc) -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install ntfs-3g
sudo modprobe fuse

Now mount your hard drive with the mount command.

sudo mount -t ntfs-3g /dev/hda1 ./master_mount

You need to remember that I am only assuming your hard drive is at /dev/hda1. You will have to edit that command yourself if you are using a different drive.

If your hard drive is FAT32, you are in luck. FAT is native in Linux and is automatically mountable. Just run the following command,

sudo mount -t vfat /dev/hda1 ./master_mount

Now you need to mount the drive to be backed up. If it is NTFS, you do not need NTFS-3G unless you plan on editing some of your customer’s files, which you wouldn’t do, I am sure. ;-) This is where it gets a bit cloudy. I don’t know where you have setyour drive up in your computer, so I will give you a general command, and you will have to edit it accordingly. If you read above about how Linux treats hard drives, you should be fine.

If the customer’s hard drive is NTFS, use this command.

sudo mount -t ntfs /dev/x ./backup_mount
sudo chmod -R 777 ./backup_mount

If it is a FAT drive, use this command.

sudo mount -t vfat /dev/x ./backup_mount
sudo chmod -R 777 ./backup_mount

You have now mounted everything and you can now start to transfer the data from the customer’s hard drive to your drive without worrying about passworded accounts. This doesn’t mean that their files won’t be passworded, you just have access to the files in the passworded account.

Type

nautilus

to browse the folders and to copy them from one to another. It will be a slow process, again, because it is running straight from the RAM, but I find that not asking the customer for their password brings a sense of trust from the customer and they will be more loyal to you.

---

