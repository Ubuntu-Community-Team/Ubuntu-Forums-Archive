---
title: "Old PC project"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by 5nak3 on 2008-09-12
Hi all, this is more a project of my own as a means to get me to learn linux but given lack of time i would want to avoid as many mistakes as possible in getting the project off the ground, so here we go with some details.

PC spec:
Model: Compaq Presario notebook 700 (734EA to be exact)
AMD athalon 1.2ghz
256 ram, although 240mb showing up so i assume 16mb shared gfx
GFX card S3 twister K (probably Compaq own brand)
20gb HDD (possibly going to change this due to possible HDD warp)

Ok the PC has nothing of value on the HDD so scrapping the HDD makes no difference to me.
At one time the HDD was making a lot of loud clicks while in operation which led me to believe it was a warped HDD. However after 1 year of no use i decided to fix the PC, having had it running now for about 3 hours there have not been any signs of clicks or odd sounds so i am not sure what to expect from the HDD.

My questions and the reason as to why i am posting is basically with the current listed spec would i be able to run ubuntu on this PC (talking about ubuntu 8.04). I think the limitation will no doubt be the ram and gfx, i will look into upgrading the ram (should be very cheap), but gfx being shared and internal i cant change this, additionally i have heard this model can only go up to 384mb of ram, long shot here but could anyone confirm that point?

Anyways, due to this limitation i thought of installing xubuntu instead now while i read a number of things on the internet i am really none the wiser as to the difference between ubuntu and xubuntu. From what i read the base system is the same just the GUI is less intensive with xubuntu. If this is the case can i access and download programs on xubuntu the same way as i can on ubuntu i.e. through the download manager.

I am still new to the linux world and so am not too sure about the inputting of code within the terminal environment and will look into that at a later date.

Ideally the most simple install would be ubuntu live cd, erase entire windows image and start fresh with ubuntu. However, considering there is a chance the HDD is warped i come to the next set of questions.

Say i replace the HDD with a brand new notebook HDD from the store, could i simply install the HDD. Stick the ubuntu live cd into the cd drive, reboot and install my new OS just like that. I was told that this is not possible and that XP needs to be installed first due to the fact the brand new HDD is not formatted and XP is needed to format it. However this surely cannot be right, so can someone please clarify if a new HDD is bought and put into the HDD bay on the notebook all i need to then do is run the ubuntu (or xubuntu) live cd and install the OS to have a fully functional PC.

I'm sure there was more to my questions but they are not coming to me at the moment. Anyway, i hope someone could shed some light on matters. Also if anyone has any tips as to how to approach matters differently i'm open to suggestions.

Thanks a lot

---

### Post by alzie on 2008-09-12
I don't think you'll have any problems other than you may need to use the text based or alt install.  I think that's on the live cd as an option.

If you replace the hard drive, you shouldn't need to format with an XP disk.

You might burn a copy of the **ultimate boot cd** to check the hard drive for errors.  You can find that here: [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

Good luck with the install.

---

### Post by cwsnyder on 2008-09-12
1) Normally, if you can boot the Ubuntu live disk without extra options, you don't have to worry about drivers for your display card.  It will work with the default settings.  If you have to set the options for Frame Buffers, etc. just to get a display, you will need the same options set to install.

2) Your Ubuntu (or Xubuntu) live CD (using Gparted or another partition manager) is fully capable of partitioning and formatting a totally blank hard drive.

3) Xubuntu uses a different display manager (Xfce) which uses less RAM than the Ubuntu default Gnome or Kubuntu default KDE.  Other lightweight display managers which can be installed in place of Xfce are Fluxbox, Enlightenment, and JWM, for example, and others from the Ubuntu program repository.  Xubuntu also does not come standard with the full OpenOffice.org office suite and makes other compromises on the installed programs to save hard drive space.  As you have space, and the application will run in your RAM space, you can load applications from the Ubuntu repositories.

256 M of RAM is light for running Ubuntu, but I would not hesitate to install either Xubuntu or one of the other lightweight distributions on the laptop.  I was trying to shoehorn a Linux install on a Compaq laptop with only 64M RAM and a 3G HDD! (No, I went with Damn Small Linux, not Xubuntu).

Anybody else want to weigh in?

---

### Post by handydan918 on 2008-09-12
Emphatically agree on the issue of not needeing XP. XP is only capable of two file formats, fat32 and ntfs. Linux is capable of those and many more. Whoever told you that should be filed away under "doesn't know squat".

---

### Post by FrostDust on 2008-09-12
Ubuntu's install sequence has it's own disk formatter/partition, so you can use your old hard drive, or a new blank one just the same. During install you'll be prompted to chose how to format it so Ubuntu can install itself to the drive. In your case, you could just pick the "Format the whole disc for Ubuntu" option, as it seems like you don't want to save anything from your Windows install.

---

### Post by cariboo on 2008-09-12
You won't have to install xp first to partition  the disk properly. Any of the cd's include all the tools you need to setup Ubuntu on a new hdd. The only difference between Ubuntu, Kubuntu, and the rest of the *bunutus is the gui interface. You have access to the same repositories and can install any program that you would on a full Ubuntu installation.

You can install ubuntu on your laptop, but it will take an unreasonable amount of time to get to the desktop on the livecd. I would suggest using the alternate installation cd, as it would take a lot less time.

Jim

---

### Post by 5nak3 on 2008-09-12
Wow, really suprised by the responses :D Thanks a lot too everyone that has had a say so far!

Right well just to give a quick update, i tried the ubuntu liveCD which was painfully slow to load up and shut down, so as you guys suggested it is the alternate install for me, which through back ground reading I have come to understand it is text based rather than a GUI install.

I dont have a major problem with that, but are there any snags i should watch out for? When playing with the Ubuntu live cd on my primary machine i messed around with the install feature it was a simple answer the questions and press "next" is the alternative install the same just text based?

Since i can access the ubuntu repositories via xubuntu, i think i might settle with xubuntu given the lighter GUI which should work much better on the system if i cant upgrade the ram and then from what i understood i can choose to download the likes of open office (which i prefer it to Abi word) as well as any other programs which take my fancy onto the xubuntu OS, and given the fact access to the repositories exists and the fact the buntu's are based off the same OS "base" (probably not the correct word but nevermind) in theory this should be possible with no need for any sort of messing around in the terminal?

One other thing which came up while i was browsing other forums was the fact ubuntu seems to be picky when running off an external HDD, i assume this is not the case with an internal drive and any drive i choose to buy will simply need to be put into the bay, formatted by the Linux install process and be ready with my new OS to be used regardless of brand

---

### Post by alzie on 2008-09-13
My first installation was a dual boot using an alt disk,  It was pretty straight forward.  

I'd recommend you bookmark psychocat's tutorials here: [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

This will help you getting things set up.

Good luck.

---

### Post by Zzl1xndd on 2008-09-13
I would also Advocate using Xubuntu in this case, it will run a lot smoother for you then Ubuntu.

---

