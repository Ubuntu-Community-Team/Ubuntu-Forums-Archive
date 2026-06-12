---
title: "Skydrive"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by Line on 2008-08-19
Hi, Is there any way to mount MS skydrive as a regular harddisk?:)

---

### Post by cwsnyder on 2008-08-24
Try attaching the Skydrive as Network Attached Storage.  I haven't tried it, but that is the only way I can think might work.

cwsnyder

---

### Post by izar on 2009-03-31
and how do i do this?
or is there any other wey to upload many files quickly

---

### Post by bdaman80 on 2010-04-11
Yes I would like any available info on this too

---

### Post by marcio123 on 2010-05-20
I just created MS skydrive. It has nice 25 GB free space ... is there any software to sync folder ? (I don't care if it is windows or linux)

---

### Post by 3rdalbum on 2010-05-20
> **cwsnyder said:**
> Try attaching the Skydrive as Network Attached Storage.  I haven't tried it, but that is the only way I can think might work.

cwsnyder

Disregard this comment; cwsnyder doesn't seem to know what Skydrive is. (it's not a physical disk, it's online storage, similar to Ubuntu One).

As far as I'm aware there's no way to mount Skydrive on anything other than Windows. Can you use the web-based interface on Linux?

Honestly if I were you I wouldn't be surprised that Microsoft Skydrive is not Linux-friendly.

---

### Post by stmiller on 2010-05-23
[http://skydrivesimpleviewer.codeplex.com/releases/view/39728](http://skydrivesimpleviewer.codeplex.com/releases/view/39728)

There is a windows free utility that reveals a webdav unique url for your skydrive storage.

(As showcased here: [http://www.winsupersite.com/win7/totw/skydrive2.asp](http://www.winsupersite.com/win7/totw/skydrive2.asp) )

After using that above utility in a Windows VM to get my webdav URL, I cannot get it to connect with Gnome's 'connect to server...' dialog. Eh.

But if it's just webdav, it should be possible. Assuming there is nothing Windows specific involved.

---

### Post by mojo2012 on 2010-06-21
Unfortunately there seems to be some windows-specific requirements needed for accessing skydrive via webdav protocol. Normally on windows, connecting to webdav shares does show up the "normal" wndows login window but with skydrives a ".NET passport window" pops up. It seems that somehow skydrive bypasses the normal authentication and so it's not possible to use it with linux or mac os x (I only tried the latter).

---

### Post by marcio123 on 2010-08-08
The way I'm working with skydrive is using virtualbox (XP with Skydrive Explorer) with shared folder.

---

### Post by marcio123 on 2010-09-17
Try SMEStorage !! :)

---

### Post by bep7987 on 2010-09-21
I just installed moonlight libraries through synaptic, and now skydrive works fine.  :)

---

### Post by mkaut on 2010-09-24
> **bep7987 said:**
> I just installed moonlight libraries through synaptic, and now skydrive works fine.  :)

Hello, could you provide some more info about how to make it work, please?
I am sure I am not the only one that would appreciate it...

Thanks,

Michal

---

### Post by bep7987 on 2010-09-26
I don't really have much advice to give.  I realized that skydrive wasn't working.  The skydrive page had a message stating that I needed to have silverlight installed.

I opened the synaptic package manager and saw that I had some moonlight packages installed but not others.

I know one of the packages that was not installed was the libmoonlight-windows-desktop, so I installed that.

The packages that I have installed now are:
libmoon
libmoonlight-gtk3.0-cil
libmoonlight-system-windows3.0-cil
libmoonlight-windows-desktop3.0-cil
libmoonlight-system-windows-controls2.0-cil
moonlight-plugin-core
moonlight-plugin-mozilla

(See attached screenshot of synaptic package manager.)

I hope this information helps.

---

### Post by Danefae on 2010-10-21
> **bep7987 said:**
> I don't really have much advice to give.  I realized that skydrive wasn't working.  The skydrive page had a message stating that I needed to have silverlight installed.

I opened the synaptic package manager and saw that I had some moonlight packages installed but not others.

I know one of the packages that was not installed was the libmoonlight-windows-desktop, so I installed that.

The packages that I have installed now are:
libmoon
libmoonlight-gtk3.0-cil
libmoonlight-system-windows3.0-cil
libmoonlight-windows-desktop3.0-cil
libmoonlight-system-windows-controls2.0-cil
moonlight-plugin-core
moonlight-plugin-mozilla

(See attached screenshot of synaptic package manager.)

I hope this information helps.

Hi bep7987!

Did you also get the Silverlight upload tool to work - the one with drag and drop? (If you don't know what I mean, take a look at [http://www.liveside.net/2010/05/19/wave-4-windows-live-office-a-first-look/](http://www.liveside.net/2010/05/19/wave-4-windows-live-office-a-first-look/) and scroll down to "This means that the upload tool is now supported cross-platform and cross-browser, [...]")

---

### Post by flitbee on 2010-11-04
> **stmiller said:**
> [http://skydrivesimpleviewer.codeplex.com/releases/view/39728](http://skydrivesimpleviewer.codeplex.com/releases/view/39728)

There is a windows free utility that reveals a webdav unique url for your skydrive storage.

(As showcased here: [http://www.winsupersite.com/win7/totw/skydrive2.asp](http://www.winsupersite.com/win7/totw/skydrive2.asp) )

After using that above utility in a Windows VM to get my webdav URL, I cannot get it to connect with Gnome's 'connect to server...' dialog. Eh.

But if it's just webdav, it should be possible. Assuming there is nothing Windows specific involved.

I tried using webdav in ubuntu (i'm just a novice user anyway) but I couldn't get it to work. :(

---

### Post by jakobb on 2010-11-11
another thread is also running:
[http://ubuntuforums.org/showthread.php?t=1262705&page=2](http://ubuntuforums.org/showthread.php?t=1262705&page=2)

---

### Post by superprash2003 on 2010-11-16
any luck on getting skydrive to work with ubuntu?

---

### Post by flitbee on 2010-11-17
> **marcio123 said:**
> Try SMEStorage !! :)

 This is cool! I tried using this option and per [http://www.smestorage.com/?p=static&page=labs#Linux%20Sync](http://www.smestorage.com/?p=static&page=labs#Linux%20Sync) and [http://www.smestorage.com/?p=static&page=clients_and_tools](http://www.smestorage.com/?p=static&page=clients_and_tools) had it installed on my Ubuntu box.   I can copy files over and backup np! (but upload speeds suck). I tried then going one step further and using [rsync]("https://help.ubuntu.com/community/rsync") for incremental file updates (since SMEStorage has a limit of 1GB bandwidth per user per month). However haven't got rsync to work :(

```
rsync: ERROR: cannot stat destination 
```

---

### Post by superprash2003 on 2010-11-17
but doesn't SMEstorage have a 1GB monthly bandiwdth??which i think is a very serious limitation considering skydrive provides 25gb...

---

### Post by flitbee on 2010-11-17
> **superprash2003 said:**
> but doesn't SMEstorage have a 1GB monthly bandiwdth??which i think is a very serious limitation considering skydrive provides 25gb...

Yes it is. That is the downside :( But it's the closest I came to a 25GB backup (barring the Silverlight solution mentioned above)

---

### Post by izar on 2010-11-20
> **superprash2003 said:**
> any luck on getting skydrive to work with ubuntu?

):P here's a summery of this thread:

there are 3 methods that work:

1. the most simple method - you can simply use skydrive on firefox (or another browser). the main drawback is that you need to upload every file singularly.

2. SMEStorage- they provide a platform by which you can upload files to many locations.   > **flitbee said:**
> This is cool! I tried using this option and per [http://www.smestorage.com/?p=static&page=labs#Linux%20Sync](http://www.smestorage.com/?p=static&page=labs#Linux%20Sync) and [http://www.smestorage.com/?p=static&page=clients_and_tools](http://www.smestorage.com/?p=static&page=clients_and_tools) had it installed on my Ubuntu box.   I can copy files over and backup np! (but upload speeds suck)

3. virtualbox- vbox allows you to have a virtual machine that can contain ms windows inside ubuntu. this way you can use any tools that work for windows.

---

### Post by inlovewithu on 2011-05-02
You can use the dropbox prvided by dropbox. It integrates very well into Gnome Ubuntu. And provides very good features.

---

### Post by inlovewithu on 2011-05-02
But still i am waiting for the Ubuntu One to Support operation behind proxy.   :neutral::neutral::neutral:

---

### Post by izar on 2011-05-03
as you said there are many alternatives to skydrive such as ubuntu one and dropbox.
nevertheless they can't compete with skydrive's 25 GB.

---

### Post by flitbee on 2011-05-03
> **izar said:**
> as you said there are many alternatives to skydrive such as ubuntu one and dropbox.
nevertheless they can't compete with skydrive's 25 GB.

 yup the 25GB's the clincher!

---

### Post by I2k4 on 2011-05-03
I switched from MS Skydrive to Amazon's new cloud storage even though the free limit is less (5GB) because Skydrive has a little 50mb upload limit per file, while Amazon's is 2GB.

[https://www.amazon.com/clouddrive/learnmore](https://www.amazon.com/clouddrive/learnmore)

(Everything I keep on it is independently encrypted, since I'm still leery of these Cloud services.)

No automatic backup as far as I know.  I'm a user and big advocate of DropBox for active file sync with automatic 30 day recovery.  But it is not "backup" in the strict sense, and needs a secure backup - every month is good is enough for me.

---

### Post by mmoalem on 2011-05-04
hi there all - tried many and now i am using both dropbox and sugarsync. sugarsync has 5gb free plus extra upon referrals and its application runs under wine.
Adrive gives you 50gb free but for the application to keep everything in sync you will need the paid premium membership.
my android phone has the app sorami which mounts skydrive storage - now if android is a nix system at heart there must be a way for someone to convert sorami to linux...

---

### Post by Dragonbite on 2011-12-23
Sorry to reanimate a thread (but thought it might be better than creating yet another one).

I've been fooling around with SkyDrive on my wife's new Windows 7 system and would really like to see it work in Linux.

I did run across a codeplex entry though it looks unsupported, [URL="http://skydrivesync.codeplex.com/"][U]SkyDrive Synchronizer
[/U][/URL].

Between the newer Ubuntu version (11.10), and Online Accounts (adding Live Account possible, it seems, according to this OMG! Ubuntu article [_Install Empathy with MSN XMPP Support in Ubuntu 11.10_]("http://www.omgubuntu.co.uk/2011/12/how-to-install-empathy-with-msn-xmpp-support-in-ubuntu-11-10/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29&utm_content=Google+Reader")

Is SMEStorage still the best solution at this point?

EDIT: I see according to here [_SkyDrive Client for Linux openSuse_]("http://www.linuxquestions.org/questions/linux-newbie-8/skydrive-client-for-linux-opensuse-877054/") Dolphin (the file manager for KDE) is able to handle WebDAV plus it has some commands for mounting the SkyDrive in fstab.

---

### Post by izar on 2011-12-24
> **Dragonbite said:**
> 

EDIT: I see according to here [_SkyDrive Client for Linux openSuse_]("http://www.linuxquestions.org/questions/linux-newbie-8/skydrive-client-for-linux-opensuse-877054/") Dolphin (the file manager for KDE) is able to handle WebDAV plus it has some commands for mounting the SkyDrive in fstab.
apparently this topic still interests me. thanks for your update.

---

### Post by krabunski on 2012-01-03
If you look at the bottom of [http://skydrivesimpleviewer.codeplex.com/](http://skydrivesimpleviewer.codeplex.com/)
> Note: Passport1.4 authentication is used by the services, so WebDAV access will only work in Windows (even though the WebDAV part is standard).

So Passport 1.4 for Linux seems to be the missing link...

---

### Post by I_ated_it on 2013-01-15
So I guess the short of it is there is still not a solution other than the limited SMEstorage solution.

Also, not sure if anyone else has experienced anything similar but my system sometimes crashes when I go to skydrive using firefox.  Im running XUbuntu 12.10.

---

### Post by oldos2er on 2013-01-15
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

