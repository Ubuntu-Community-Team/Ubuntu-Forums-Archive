---
title: "Ubuntu &amp; iPhone"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by planetzpmq on 2008-10-31
I just purchased a Dell Mini 9 with Ubuntu but I have an iPhone.  Is this bad?  I'm obviously going to need to sync my music if you get my drift.

---

### Post by talsemgeest on 2008-10-31
It shouldn't be too bad. As far as I know, even though there is no iTunes, you should still be able to sync it with some other problems. I'm afraid I can't help you too much with it, since I don't have an ipod, but this forum is full of people who should be able to help you out.

---

### Post by UbuWu on 2008-10-31
Yes, that is problematic. So far even impossible. You could use vmware to run windows and itunes, that will work.

---

### Post by talsemgeest on 2008-10-31
> **UbuWu said:**
> Yes, that is problematic. So far even impossible. You could use vmware to run windows and itunes, that will work.
Ok then, I take it back...

---

### Post by uidb4056 on 2008-10-31
I've not tested because I don't have Ipod but there is an application that could do it [http://gtkpod.org]("http://gtkpod.org/") this applicattion you can install from Synaptic Package Manager if you have enabled the Universe repository.

---

### Post by Kobalt on 2008-10-31
As fas as I know iPod Touch and iPhones are a "no go" using Linux, either with amaroK or Gtkpod...

---

### Post by thomasyen on 2008-10-31
But can't Rhythmbox support the iPhone?

---

### Post by Nepherte on 2008-10-31
> **Kobalt said:**
> As fas as I know iPod Touch and iPhones are a "no go" using Linux, either with amaroK or Gtkpod...
Not if you jailbraik them and don't use 2.x firmware.

---

### Post by Kobalt on 2008-10-31
I did forget this option, right.

---

### Post by Paqman on 2008-10-31
> **UbuWu said:**
> You could use vmware to run windows and itunes, that will work.

The Mini9 is a netbook isn't it? I doubt you'd be able to run a VM well, if at all. Maybe if you logged into a lighter desktop than Gnome and ran a lightweight version of Windows like TinyXP (which is illegal) you might be ok.

Tbh, if you've got the storage space for it a dual-boot would be best. A clean install of XP isn't *that* big, especially since if you're only using it to sync an iPhone you might not need to connect to the net, and therefore could forgo antivirus/firewall etc.

---

### Post by Nepherte on 2008-10-31
> **Kobalt said:**
> I did forget this option, right.
You're correct when you are talking about 3g iphones, which is the case here :) Only a virtual machine might help here.

---

### Post by ginbuntu on 2008-11-13
I am using my iphone with Vmware on Ubuntu amd64. Works fine :)

---

### Post by grimdeath on 2008-11-14
I would recommend keeping an eye on [Songbird]("http://getsongbird.com/features/"). They do not support iphone, ipod touch or zunes yet but hopefully this will come in the future. That app rocks!

---

### Post by jpoRS on 2008-11-14
The reason why iPhones, iPod Touch, and the like don't work is that they require the newest iTunes to work; and for various reasons we can't get the latest iTunes to work in Ubuntu (yet).  The only way to get around that is Jailbreak, which has been mentioned, but (I believe) that voids your warranty.

On another note though, if you have a Mini9, how much music do you have?  I believe the largest "hard drive" for them is 16 gigs, and that is before you install the OS and other software.  Do you have access to another computer (parents, friends with exceptional musical taste) that you could use as your music-machine?

Good Luck,
jim

---

### Post by AlanR8 on 2008-11-14
My son has an IPod Touch and recently I Linuxed his laptop! All was well until he wanted to synch his Touch with Amarok. (We run Kubuntu).

After much searching around I found this tutorial and followed it to the letter. It works. He can now synch his music.

I can't take credit for this tutorial, when I find a post I can use I copy it into a WP document and save it for a rainy day.

Here goes!

> The following guide allows you to wirelessly sync an iPhone with Amarok in Ubuntu 7.10, including adding, editing and playing songs and playlists. 
Note :- it requires a jailbroken iPhone.
Step1 :- Set up the iPhone
On your iPhone:
Click Settings &#8594; General and set Auto-lock to Never. This will ensure the iPhone keeps the WiFi connection open.
Click Settings &#8594; WiFi and select your WiFi network. Click the Static button and change the IP Address to something outside the dynamically assigned range of your network. For example, if your wireless router normally assigns 192.168.1.1 - 192.168.1.5, try 192.168.1.10. This will ensure your iPhone is always contactable at the same address for syncing.
Open Installer.
Click on All Packages &#8594; OpenSSH &#8594; Install.
Click All Packages &#8594; BSD Subsystem &#8594; Install
Step2 :- Set up Ubuntu
A third party source provides the ipod convenience package needed to properly mount and unmount an iPhone or iPod Touch, and for gtkpod users, a newer gtkpod that’s required for the iPhone and iPod Touch.
First you need to edit the /etc/apt/sources.list file
sudo gedit /etc/apt/sources.list
add the following line
deb [http://ppa.launchpad.net/ipod-touch/ubuntu](http://ppa.launchpad.net/ipod-touch/ubuntu) gutsy main
Save and exit the file
Update the source list
sudo aptitude update
Install the ipod-convenience and amarok packages
sudo aptitude install ipod-convenience amarok
When asked, enter the IP address of your iPod Touch or iPhone that you selected earlier. When asked for a folder to mount your iPod Touch or iPhone, either leave the default of /media/ipod or another folder if you prefer - just remember to use that folder name for rest of this guide. The package will make the folder for you.
Step3 :- Set up Amarok
Click Applications &#8594; Sound and Video &#8594; Amarok
When you first open up Amarok:
Click Settings &#8594; Configure Amarok.
Choose Media Devices.
Hit Add Device.
Select Apple iPod Media Device for the plugin type.
Point it at your mount point, /media/ipod.
Back in the main app, click the blue cog icon called Configure Device just above the iPhone or iPod Touch. For Pre-Connect Command, add iphone-mount, for the Post-Disconnect Command, add iphone-umount
Click Connect. After entering your password, your iPhone or iPod touch should now appear in Amarok.
You can now add, edit, and delete music to the iPhone like any other device. Just drag the music files into Amarok, and hit Transfer to move them to your iPhone. When you’re done, stop any music playing from the iPhone and click Disconnect.
Music should show now up in the iPhone immediately.
Note: If music doesn’t show up immediately this may be due to a bug recent BSD Subsystem packages missing the killall command. If so, you can download killall for iPhone, move the ‘killall’ file to /usr/bin/on your iPhone, and enable the execute permission.



---

### Post by jpoRS on 2008-11-14
Like it has been said, Jailbreaking the iPhone will work, but I *think* it voids your warranty.  Does anyone know for sure?

jim

---

### Post by iaskedalice09 on 2008-11-14
@jpoRS, I'd bet money that it breaks your warranty.

---

### Post by jbrown96 on 2008-11-14
You can easily revert it back to the official software very easily. With Ziphone, its just one click. If you needed to get service you can do this, or if it's too messed up to restore, then it's unlikely apple will be able to do anything with it either, so they would never know. I've had an Iphone for a year, and Apple usually takes the restore it and if that doesn't work replace it ideology, so its not much of an issue.

---

