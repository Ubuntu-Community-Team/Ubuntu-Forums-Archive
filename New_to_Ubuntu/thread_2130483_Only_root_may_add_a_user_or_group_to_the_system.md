---
title: "Only root may add a user or group to the system"
date: 2013-03-29
forum: New to Ubuntu
---

### Post by toadinapintglass on 2013-03-29
Hi
I'm trying to install Samba using this guide [http://www.unixmen.com/howto-install-and-configure-samba-share-in-ubuntu/](http://www.unixmen.com/howto-install-and-configure-samba-share-in-ubuntu/)

and at step 4 I'm getting this message "Only root may add a user or group to the system"

all i'm typing in terminal is "adduser home-server" as thats the name i gave to this comp

thanks in advance

---

### Post by Kopkins on 2013-03-29
To do certian things (commands) you need to be root, or have root priveledges. The root user is the administrative account. On ubuntu the root user has no set password. So to access root priveledges, a user can use the command `sudo' Super User DO. You will be prompted for your own password, and the command will be executed as root. Usually it is system commands you need sudo for.

Here is the wiki page. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
Try this: ```
sudo adduser home-server
```

Often times in tutorials, they give the command you need to use but don't say you need to be root.

Good luck,
Kopkins

---

### Post by toadinapintglass on 2013-03-29
I am root  but wont add my name so I can choose password and share files

---

### Post by coldcritter64 on 2013-03-29
> **toadinapintglass said:**
> I am root... The root account is locked by default in Ubuntu, **unless you specifically enabled it** you are using your user account. 

Edit: It is possible the terminal is remembering your password for a limited time when repeatedly using "sudo". The elevated privileges are only for the individual terminal in use **(and only for commands preceded by "sudo")**, that is you are still operating as a normal user, with elevated privileges only applying to the commands preceded by sudo issued in the terminal itself.

To gain root privileges for the adduser command, alter the 4th command in the instructions to,
```
sudo adduser <your-username>
```Replacing <your-username> with the actual username you want added to the system.

Raising the privileges during this command is necessary (adding a user is an administrative task), this is done simply by adding "sudo" before the command; the password to use when asked is your user password and it **will not** show as it is entered in a terminal, another security feature. 

If the terminal shows nothing but a new prompt, then the command worked OK, any errors will trigger a terminal response/warning.

---

### Post by gordintoronto on 2013-03-30
The guide you are using may be excessively complex. If you just want to share a folder, step one is all you need to do. Then, in the File Manager, right-click on the folder and select sharing options. Issue 60 of Full Circle Magazine has details.

By the way, it's generally a good idea to mention what version of Ubuntu you are using. File sharing is an example where Xubuntu is slightly different from Ubuntu, and there have been minor changes over the years.

---

### Post by toadinapintglass on 2013-03-30
I'm using ubuntu 12.10
Just trying to make a home server that i can store all my films on and download torrents
Also want to connect HDMI lead from server onto my TV, (Tv has no internet it isnt a smart TV)
Need to be able to steam films to  another computer and laptop
Also want to be able to have remote excess to the server via laptop and computer
so that i can add torrents and unrar them ect
My server and my main computer will be connectted by ethernet cable and laptop
via wireless...all be on same router and wont need to excess server outside of the router
Also need to portition my harddrive so can av OS and space seperate

What would the best Ubuntu to use as I've been trying to set up the server for last 3 days and seem to be going round in circles

server specs
Aspire-x3300
memory : 2.7 GiB
Processor : AMD Athlon (tm) II X3 
OS type : 32-bit
Disk : 500GB

Is there a better guide i can use?

---

### Post by gordintoronto on 2013-03-30
You said "server" several times. Please confirm that you are actually running Ubuntu Desktop, which can do everything Ubuntu Server can do. It has a tiny bit of overhead, and about 10% of the learning curve. And it can't do at least one of the things you want to do.

I have no experience with Steam. Oh, you probably meant "stream," did you mean as a DLNA Server, or just playing a video that happens to reside on a different computer? The second option, and everything else, is simple using Ubuntu Desktop. (Or Mint. Xubuntu or Lubuntu have a bit less overhead, but might require more work to do some of the things you want to do.)

If it were my system, I would use Ubuntu Desktop 12.04 LTS, 64-bit version. Constant upgrades are a pain in the butt; by the time support for 12.04 ends, there won't be much happening in the 32-bit world. I've been running 64-bit for almost four years, and it only needed a little extra work once.

You might find that the computer struggles to play 1080P video. It was low-spec three years ago, most particularly the Nvidia 9200 video adpater. If the TV is 720P, the computer should be OK. The "green" hard drive might also cause stuttering, especially across the network.
[http://compreviews.about.com/od/sff/gr/Acer-Aspire-X3300.htm](http://compreviews.about.com/od/sff/gr/Acer-Aspire-X3300.htm)

---

### Post by toadinapintglass on 2013-03-31
I am running Ubuntu Desktop  12.10 But now going to format the computer and put on  Ubuntu Desktop 12.04 LTS, 64-bit version
How much space will I need for this OS and programs so that i can portition it off?
I'm planning on having all my media files on this machine so I can Stream it to another PC and Laptop...So will have to learn more about DLNA..whats the best way or program to use to be able to do this?
My TV is only 720p and only planning on playing 720p or less on it
Hopefully after This is up and running I'll Take out the dvd rom and add a better harddrive and make sure it isnt a green one
Thanks for your advice

forgot to mention I dont want no mouse or keyboard attached to this machine after set up

---

### Post by gordintoronto on 2013-03-31
I have never set up a DLNA server, but this article looks like it has some answers:
[http://www.linux-magazine.com/Online/Blogs/Productivity-Sauce/Set-up-a-DLNA-Server-in-a-Minute](http://www.linux-magazine.com/Online/Blogs/Productivity-Sauce/Set-up-a-DLNA-Server-in-a-Minute)

If your root partition runs out of space, it's a disaster, so I tend to make mine twice as large as it needs to be. 12 GB should be lots, if you don't expect to play around with the program of the week. You still need to keep an eye on it; I have heard of runaway log files chomping up space at an alarming rate.

You will want to learn about SSH, which is the usual approach to a remote server. Maybe Remote Desktop as well.

---

### Post by 3rdalbum on 2013-04-01
I can't help you with your Deluge problem, sorry; it's been years and years since I've used Deluge.

12 gigs should be a fine amount of space to put as your / partition.

For streaming videos to PCs and laptops, **you don't need DLNA**. Just use Samba. You'd only need DLNA if you were streaming to a PS3 or something else that can use DLNA but not Samba.

I notice you didn't follow Coldstream's advice about using 'sudo'; instead of "adduser", use "sudo adduser". This is because the user account you log into is not root, but the 'sudo' command allows you to run a command as root. It's a security measure that your user account is not all-powerful.

You don't even need to do "sudo adduser" and "sudo passwd" - why not use the User Accounts program that comes with Ubuntu in the System Settings? You can easily create a user there.

You're on the right track about using system-config-samba, that's what I use. Just remember that you need to use system-config-samba to create a user account in Samba for every ordinary user account you create in User Accounts. In other words, if you have a user on one of the laptops called "greg" who will be accessing the server, you need to use User Accounts or 'adduser' to create a user account for Greg, and also create a Samba account for Greg in system-config-samba.

---

### Post by toadinapintglass on 2013-04-05
Thanks for the help guys
I've just done a fresh install of Ubuntu 12.04LTS 64bit desktop
25gb for operating system
2.5gb for swap
439gb for media
I managed to share files in home using samba but having trouble sharing
/dev/sda3  /media/New Volume  type fuseblk
I did format it as NTFS[I]
W7 just keeps coming up with a error that i dont have permission to excess it[/I]

---

