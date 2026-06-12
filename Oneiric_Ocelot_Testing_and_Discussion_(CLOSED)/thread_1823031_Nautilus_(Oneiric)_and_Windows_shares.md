---
title: "Nautilus (Oneiric) and Windows shares"
date: 2011-08-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by coffeecat on 2011-08-11
Would someone who has set up "proper" Windows shares in a Windows machine or in a samba server please try this to see if they are getting the same as me. This is with my Western Digital MyBookWorld which works OK most of the time but I have had some odd glitches with its sharing in earlier versions of Ubuntu.

I open Nautilus and click on "Browse Network". I see only a folder called "Windows Network". No 'MybookWorld' which is what I see in Natty. If I double-click on the folder, I get "Unable to mount location - Failed to retrieve share list from server". In Natty, the Windows Network folder will open to show me MyBookWorld as well.

But if I ctrl-L to get the text address bar and type in smb://MYBOOKWORLD/ Nautilus connects just fine and shows me the shares. I can log into the password-protected one and copy files across.

File menu > Connect to server works just fine as well.

---

### Post by cariboo on 2011-08-11
I have a server that runs both Samba and NFS. When I open Nautilus and select Go->Network, I get the Windows Network icon, double clicking that takes me to the Workgroup Icon, double clicking that takes me to the icons of computers on the network, that share files via Samba

---

### Post by P-I H on 2011-08-11
When I use Browse Network, I can see two Window networks, one called "Hemma" and one called "Workgroup".
Hemma is a Vista computer which contains a share called "MULTIMEDIADATOR" and Workgroup is an Ubuntu NAS which contains a share called NAS.
Folders and files open OK on both shares and I can for example play music with Banshee.

---

### Post by coffeecat on 2011-08-11
@cariboo907 and @P-I H, thanks for that. It seems from what you say that Nautilus is working properly for Windows shares. I've been getting a few oddities with the WD mybookworld with every release of Ubuntu which I didn't get when I set up a Windows share in Vista. That's not available any more which is why I couldn't test this myself.

I think I'll write this off as another MyBookWorld glitch. I can work around them all but the firmware/OS in the Mybookworld must have a bug or three.

---

### Post by Morbius1 on 2011-08-11
I'm not using Oneiric but I wouldn't necessarily jump to the conclusion that something is wrong with the WD device.

If you go through Nautilus you get the dreaded "Failed to retrieve share list from server" error.

But if you use nautilus-connect-server ( i.e., Connect to Server ) or access it directly ( i.e., smb://server-name/share-name ) you don't get the error.

Without knowing any other information it sounds like  a problem with "Browse Network".

Do you get the same error when you do this from a terminal:
```
nautilus network://
```

---

### Post by coffeecat on 2011-08-11
> **Morbius1 said:**
> Do you get the same error when you do this from a terminal:
```
nautilus network://
```

Yes.

> **Morbius1 said:**
> I'm not using Oneiric but I wouldn't necessarily jump to the conclusion that something is wrong with the WD device.

I'm not saying that there's something wrong with the device - just that there's a bug in its implementation of smb. Although I suppose you could call that "something wrong". :) Apart from the minor issues I've experienced in earlier versions of Ubuntu I get something similar in MacOS. Going from memory here, but in the left pane of Finder is a network entry similar to that in Nautilus which also always errors with this WD device. But when I do the MacOS/Finder equivalent of File menu > Connect to server, I can connect just OK. If I set up a samba share in Ubuntu, MacOS can connect to it without issue. And when I've tried Windows accessing the WD device, I've had no problem at all. My guess is that it was only properly quality controlled with Windows.

My only reason for posting was to see whether this was an Oneiric bug that needed pursuing, or just an irritation with the WD device. The other two posts suggest that things are fine with Oneiric's Nautilus regarding Windows shares so I am happy to point the finger at the MyBookWorld and simply work around it.

Thanks for your thoughts anyway.

---

### Post by Morbius1 on 2011-08-12
OK, I'll admit I had an ulterior motive.

The situation you describe:
* "nautilus network://" does not work.
* "Connect to server" and "smb://hostname" does work.

Has been going on for some time - all the way back to at least 2009:

[http://www.linuxforums.org/forum/ubuntu-linux/173002-suddenly-cant-browse-windows-network-nautilus.html](http://www.linuxforums.org/forum/ubuntu-linux/173002-suddenly-cant-browse-windows-network-nautilus.html)
[http://ubuntuforums.org/showpost.php?p=7355261&postcount=5](http://ubuntuforums.org/showpost.php?p=7355261&postcount=5)


The "failed to retrieve share list" is aways interpreted as a name serves problem ( by me as well ) in which the network cannot convert a host name to an ip address. There are some out of left field fixes for this thing - winbind, nsswitch, personal geosynchronous communications satellite yet the the original poster says that he can access the remote machine by doing a "smb://host-name".

If it was a name services problem that command should not work. There's something wrong with "nautilus smb://network" or something that it invokes that predates Oneiric. I'm just not smart enough to know what that is and I was using your post to find the answer.

---

### Post by coffeecat on 2011-08-12
@morbius1, that's interesting and sorry if I appeared to be lacking in curiosity! :)

What you say bears out what I have been seeing. In earlier versions of Ubuntu (I can't remember which now), 'smb://MYBOOKWORLD/' wouldn't work, but 'smb://192.168.1.100/' would. But I could fix this with the Problem 3  workaround in this thread:

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

That most other people were probably not getting this issue, judging by the paucity of threads about it, and that I could browse Windows share hostnames in other devices without the fix, caused me to suspect the WD device. From what you say, it seems the issue is being seen elsewhere. Unfortunately, what I know and understand about Windows shares could probably fit comfortably on the back of an average postage stamp, so I took the pragmatic decision to do what I could to make the WD usable and not worry about exactly what is wrong.
 
By the way, I'm aware that I've been a little unfair to WD in my last post with the "My guess is that it was only properly quality controlled with Windows" comment. That should have read "Windows shares in Windows". The device also supports FTP, NFS and AFP, as well as CIFS, and my guess is that they would have assumed that most Apple users would use AFP.

---

### Post by cariboo on 2011-08-12
I have all the hostnames of the various computers I connect to on my network via nfs, ssh, and samba aliased in /etc/hosts:

> cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	alexis-oneiric
192.168.1.250	willy
192.168.1.240	likely
192.168.1.215	chilanko
192.168.1.235 	puntzi
192.168.1.218	mcleese

I've been using essentially the same smb.conf file for more years then I'd like to remember. My server currently consists of 4TiB of storage, but I have plans of upgrading to 8TiB once I refurbish the mini fridge server case I recently received.

---

### Post by capscrew on 2011-08-12
Just my 2 cents worth:  The "browse system" for SMB/CIFS relies on a master browser to hold the browse list.  It is possible to have erratic behavior if the machine holding that list is off line (even temporary) as the network (SMB) will elect a new master browser and populate the new list.  It usually takes 10-15 minutes for the process to complete.  The old master browser WILL NOT be brought back unless there is a new election and replacement browse list is made again.

Another problem with later Ubuntu releases is the failure of the nmbd daemon to launch leaving the Samba shares with now name services.  This is an Update problem.  At this point I just restart the daemon manually when needed.  I admit to some forms of laziness.  :-(

---

### Post by Morbius1 on 2011-08-12
The thing I can't get out of my mind is the description of the original post and many others like it:
> But if I ctrl-L to get the text address bar and type in  smb://MYBOOKWORLD/ Nautilus connects just fine and shows me the shares. I  can log into the password-protected one and copy files across.

File menu > Connect to server works just fine as well.It works under those conditions it just won't work if you open Nautilus and Select "Network".

It could very well be that there is a 10 - 15 minute interval between the original way and the smb://host-name way that explains it and if he had only waited a bit and tried it again it would work. Or there is some obscure bug somewhere in gvfs-backends or some other package that's contributing to this problem.

---

### Post by coffeecat on 2011-08-12
> **Morbius1 said:**
> It could very well be that there is a 10 - 15 minute interval between the original way and the smb://host-name way that explains it and if he had only waited a bit and tried it again it would work. Or there is some obscure bug somewhere in gvfs-backends or some other package that's contributing to this problem.

OK, I'm game! :) Posting from Oneiric that I booted up less than 5 minutes ago and again I'm getting "Failed to retrieve share list..." from Browse Network > Windows Network, but ctrl-L > "smb://mybookworld/" connects just fine. I'll leave it for twenty minutes, try it again and report back.

---

### Post by coffeecat on 2011-08-12
> **coffeecat said:**
> I'll leave it for twenty minutes, try it again and report back.

Bingo!

20 minutes later and Browse Network > Open Windows Network shows a folder called "WORKGROUP". Opening that shows MYBOOKWORLD and double-clicking on that shows me the shares which I can mount.

I believe not quite as you described, capscrew, because the Mybookworld was not off-line since I was able to see the shares with "smb://mybookworld/ within seconds of getting the "Failed to retrieve share list..." And when I went back to the Windows Network folder after success with the smb address, I got the failed message again. But 20 minutes later the Windows Network folder opens OK. All very interesting.

---

### Post by cariboo on 2011-08-12
I had to uncomment wins support = yes in my smb.conf a couple of weeks ago, as none of the computers on my network could see the server, this happened after a samba update.

---

### Post by capscrew on 2011-08-12
> **cariboo907 said:**
> I had to uncomment wins support = yes in my smb.conf a couple of weeks ago, as none of the computers on my network could see the server, this happened after a samba update.

This is not needed unless you want to run a WINS server for NetBIOS names.  Samba does not recommend using a WINS server unless you have multiple subnets.

---

### Post by coffeecat on 2011-08-12
Mmmm. My head is beginning to hurt. :| I offer these observations and then I'm going to bed.

Booting up my Mac Mini and enabling the smb share on it caused it to be seen within seconds in Oneiric's Nautilus and I was able to mount it. No "failed to retrieve" message.

After the mybookworld share eventually put in an appearance in Oneiric's Nautilus I decided to install the samba package in a vain hope that I would be able to enable nautilus shares in Oneiric (more of this in a moment). I logged out and in again and mybookworld then appeared as soon as I opened "Browse Network". I didn't have to open Windows Network > WORKGROUP. Seemingly installing samba helps. So I thought I would investigate the effect of uninstalling it. I uninstalled samba and rebooted. Mybookworld still appeared straight away. I removed the /etc/samba/smb.conf file that installing samba had created, and rebooted. Mybookworld appeared straight away again. I rebooted into Natty on another partition, did something else and then rebooted into Oneiric. Mybookworld still there.

Ho hum.

But there is still something definitely odd about Mybookworld. The MacOS finder shows it in the side pane but when I click on it I get "Connection failed". But when I go to Go > Connect to server and - you've guessed it - "smb://mybookworld/" - it connects OK. Moreover, as soon as I enabled a Nautilus share in Natty, it showed in MacOS's Finder and I was able to connect by clicking on it - no "connection failed".

One last thing. I couldn't set up a nautilus share in Oneiric. Even though the package nautilus-share is installed, there's no "sharing options" in a folder context menu as you get in Natty and before.

---

### Post by capscrew on 2011-08-12
> **coffeecat said:**
> Bingo!

20 minutes later and Browse Network > Open Windows Network shows a folder called "WORKGROUP". Opening that shows MYBOOKWORLD and double-clicking on that shows me the shares which I can mount.

I believe not quite as you described, capscrew, because the Mybookworld was not off-line since I was able to see the shares with "smb://mybookworld/ within seconds of getting the "Failed to retrieve share list..." And when I went back to the Windows Network folder after success with the smb address, I got the failed message again. But 20 minutes later the Windows Network folder opens OK. All very interesting.

This can be cured by giving election priority to a host that is alway (or mostly always) up.  This stops the election process you are experiencing.  You can also tune the setting for a second machine to win the election if the "server" goes down.

---

### Post by capscrew on 2011-08-12
> **coffeecat said:**
> Mmmm. My head is beginning to hurt. :| I offer these observations and then I'm going to bed.

Booting up my Mac Mini and enabling the smb share on it caused it to be seen within seconds in Oneiric's Nautilus and I was able to mount it. No "failed to retrieve" message.

After the mybookworld share eventually put in an appearance in Oneiric's Nautilus I decided to install the samba package in a vain hope that I would be able to enable nautilus shares in Oneiric (more of this in a moment). I logged out and in again and mybookworld then appeared as soon as I opened "Browse Network". I didn't have to open Windows Network > WORKGROUP. Seemingly installing samba helps. So I thought I would investigate the effect of uninstalling it. I uninstalled samba and rebooted. Mybookworld still appeared straight away. I removed the /etc/samba/smb.conf file that installing samba had created, and rebooted. Mybookworld appeared straight away again. I rebooted into Natty on another partition, did something else and then rebooted into Oneiric. Mybookworld still there.

Ho hum.

But there is still something definitely odd about Mybookworld. The MacOS finder shows it in the side pane but when I click on it I get "Connection failed". But when I go to Go > Connect to server and - you've guessed it - "smb://mybookworld/" - it connects OK. Moreover, as soon as I enabled a Nautilus share in Natty, it showed in MacOS's Finder and I was able to connect by clicking on it - no "connection failed".

One last thing. I couldn't set up a nautilus share in Oneiric. Even though the package nautilus-share is installed, there's no "sharing options" in a folder context menu as you get in Natty and before.

If you wish to dig into this with some logical diagnoses we can do that.  Let me know tomorrow (Saturday).

---

### Post by coffeecat on 2011-08-12
> **capscrew said:**
> This can be cured by giving election priority to a host that is alway (or mostly always) up.  This stops the election process you are experiencing.  You can also tune the setting for a second machine to win the election if the "server" goes down.

Sorry - could you explain that in words of one syllable? :) I think I follow what you are saying, but how do I set the priority?

---

### Post by capscrew on 2011-08-12
> **coffeecat said:**
> Sorry - could you explain that in words of one syllable? :) I think I follow what you are saying, but how do I set the priority?

In the /etc/samba/smb.conf file there is a setting in the [global] section called *os level*.  See either the man pages or [**_here_**]("http://samba.org/samba/docs/man/manpages-3/smb.conf.5.html") for an explanation of **os level (G)**.

If your Ubuntu host is up (online) most of the time you might want to make it win the election that happens every time the host with the master browser list goes down.  My desktop is always on but sometimes I leave the NAS off.  So I have my desktop act as the master browser.

Does that help?  

I don't know what hosts you keep running or which machine is that MB.  The command *findsmb* might help you find the MB.   

Here is what I get```

capscrew@malibu:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.3     MALIBU        +[BEACHBEES] [Unix] [Samba 3.4.7]
```

Note the +=LMB and the + after the host malibu.  
+=LMB denotes the Local Master Browser.


Edit:  When you change the question (or observation) as I am responding we loose the continuity of conversation.  How about you adding your edit to the bottom as I have done here.

---

### Post by Yes_It's_Me on 2011-08-12
I have had a similar issue on Oneiric since the very beginning that still hasn't improved. If I go to browse network I can see our media server share but I get the same errors as you guys if I try to open it. I can however type nautilus smb://ip-address and it works fine. There is clearly an issue with samba/nautilus. This was working OK in natty.

---

### Post by capscrew on 2011-08-13
> **Yes_It's_Me said:**
> I have had a similar issue on Oneiric since the very beginning that still hasn't improved. If I go to browse network I can see our media server share but I get the same errors as you guys if I try to open it. I can however type nautilus smb://ip-address and it works fine. There is clearly an issue with samba/nautilus. This was working OK in natty.

I disagree.  If you can see the share using *smb://ipaddress *then Samba has to be working without a doubt.  To successfully *browse the smb network* you must be able to build a Browse List.  This can only be done with NetBIOS name to IP address resolution.  

Samba uses the daemon *nmbd* to provide DNS to NetBIOS to IP address resolution.  You need to either a) have working LAN DNS working or b) setup Samba to broadcast it's NetBIOS name (which you can to define in the /etc/samba/smb.conf file).  I would check to make sure the *nmbd* and *smbd* daemons are running.  With the implementation of Upstart scripts to launch these daemons there have been problems with nmbd not starting. 

You can check this with ```
pgrep -l mbd
```

Here is what I get ```
$ pgrep -l mbd
938 smbd
1044 smbd
1715 nmbd

``` 

The only problem with that relates to Oneiric I see mentioned in this thread is the OP's inability to create Usershares (GUI share setup) with this version of Nautilus.

---

### Post by coffeecat on 2011-08-13
@capscrew, many thanks for all your suggestions which I will work on in due course. I really appreciate them. However, my intention when originally posting was to comment on an out-of-the-box installation of Oneiric, i.e. one that had not had its samba configs tweaked. I've started afresh this morning and have discovered something quite interesting.

This morning I started with the router-modem being the only thing switched on in my network. I then switched on the WD Mybookworld to let it boot up. Then I booted into my Oneiric testing installation on my main desktop machine. Yesterday I had removed the &#8220;samba&#8221; package I had installed, leaving the samba-common and samba-common-bin packages which come in a default install. This morning I restored the default /etc/samba/smb.conf file which, by the way, does not have an &#8220;os level&#8221; in the [global] section. Nautilus > Browse Network showed me only the Windows Network folder which gave me the &#8220;failed to retrieve...&#8221; message when I tried to open it.

Also:

```
$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.100   MYBOOKWORLD    [WORKGROUP] [Unix] [Samba 3.0.23c]

```

and:

```
$ pgrep -l mbd
$
```

Nothing.

I waited over half-an-hour but still I saw the &#8220;failed to retrieve...&#8221; message. Intriguing. I remembered that last evening I had complicated matters by booting my Mac, so I booted it now. Within seconds a network icon labelled &#8220;*my name's* Computer&#8221; appeared next to the Windows Network folder. This is the Mac's share and I am able to open it and connect. Then, after about 5-10 minutes I was able to open the Windows Network folder to reveal a Workgroup folder, and in that &#8220;MACINTOSH&#8221; and &#8220;MYBOOKWORLD&#8221;, both openable. &#8220;MACINTOSH&#8221; gives me the same as &#8220;*my name's* Computer&#8221; two folder levels up.

Now I get:

```
$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.9     MACINTOSH      [WORKGROUP] [Unix] [Samba 3.0.28a-apple]
192.168.1.100   MYBOOKWORLD    [WORKGROUP] [Unix] [Samba 3.0.23c]

```

And &#8220;pgrep -l mbd&#8221; still outputs nothing.

This is all very interesting. It seems that if Mybookworld is the only other smb server on the network, then I get the failed to retrieve message, but if another smb server is there, things work. Again, I emphasise, this is with the nearest I can get at the moment to an out-of-the-box experience. I will try your suggestions, but from what happened last night it seems that the most straightforward answer for me is the install the samba package &#8211; merely to get Mybookworld easily visible. IN fact, when I installed the samba package, all smb servers appeared in Browse Network - I didn't have to open the Windows Network folder at all.

The issue with not being able to set up nautilus shares rather than "proper" samba shares remains.

---

### Post by Morbius1 on 2011-08-13
I don't mean to be a pain in the butt ... but:
> because the Mybookworld was not off-line since I was able to see the  shares with "smb://mybookworld/ within seconds of getting the "Failed to  retrieve share list..." And when I went back to the Windows Network  folder after success with the smb address, I got the failed message  again. But 20 minutes later the Windows Network folder opens OK.I'm not disagreeing with anything capscrew is saying but it looks to me that name services are running just fine, thank you very much.

I think you all would have to admit there seems to be something peculiar with "Network" in Nautilus. If you're up for an experiment try bypassing "Network":

Do the Ctrl+L and type:
```
smb://
```No ip address - no host name - just "smb://"

Now bookmark it. What should happen is that you get a listing on the left side panel titled: Windows Network

Now Reboot and instead of going to "Network" select "Windows Network".

---

### Post by Morbius1 on 2011-08-13
> One last thing. I couldn't set up a nautilus share in Oneiric. Even  though the package nautilus-share is installed, there's no "sharing  options" in a folder context menu as you get in Natty and before.I don't know if this is fixed yet or how it relates to Oneiric: [https://groups.google.com/forum/#!topic/linux.debian.bugs.dist/0SpS9lUhr-g]("https://groups.google.com/forum/#%21topic/linux.debian.bugs.dist/0SpS9lUhr-g")

> Package: nautilus-share
Severity: important
Tags: experimentalnautilus-share depends on libnautilus-extension1, which conflicts with
libnautilus-extension1a. The latter is needed for nautilus, brasero,
evince, etc, etc on GNOME3. nautilus-share should depend on the newer
libnautilus-extension1a
Either that or you are not a member of the right group: sambashare.
If not add yourself:
```
sudo gpasswd -a user-name sambashare
```Then logoff and login again.

---

### Post by coffeecat on 2011-08-13
> **Morbius1 said:**
> I think you all would have to admit there seems to be something peculiar with "Network" in Nautilus.

No, I'm going to disagree for now. I booted into Oneiric, Nautilus > Browse Network showed me my Mac and Mybookworld shares, both openable, and the Windows Network folder. All fine and dandy. I shut the Oneiric system down and then shut the Mac Mini down. I restarted Oneiric and now Nautilus shows me only an unopenable Windows Network folder which gives me the "failed to..." message. If the only server online in my network is the Mybookworld, Nautilus fails. If there are other smb servers online, nautilus shows all the shares. I'd say - and have been saying - that there's something peculiar with Mybookworld.

I agree that I'm using a Mac to simulate a "proper" smb server. I haven't time now, but I will dust off Windows in one of my laptops, set up a share and see what's what.

> **Morbius1 said:**
>  If you're up for an experiment try bypassing "Network":

Do the Ctrl+L and type:
```
smb://
```No ip address - no host name - just "smb://"

I'm always up for an experiment! Tried it - failed. See screenshot. This with only Mybookworld apart from Oneiric on the network.

**EDIT**:

> **Morbius1 said:**
> Either that or you are not a member of the right group: sambashare.
If not add yourself:
```
sudo gpasswd -a user-name sambashare
```Then logoff and login again.

"id" shows that I am a member of sambashare already.

---

### Post by coffeecat on 2011-08-13
> **coffeecat said:**
> No, I'm going to disagree for now.

And now I'm going to contradict myself! :|

I'd been assuming that somehow the presence of the Mac share on the network makes the mybookworld share visible in "Browse Network". I was wrong. I tried the following.

I shut down the mybookworld and booted up the Mac. The Mac share became visible as “*my name's* Computer” (and was mountable) in Browse Network but the "Windows Network" folder next to it gave me "failed to retrieve..." when I tried to open it. Aha!

Then I restarted mybookworld and within a couple of minutes the "Windows Network" folder was openable and I could access the mybookworld shares.

Summary:

Only Mac on network: openable Mac share + unopenable Windows Network folder in "Browse Network".

Only Mybookworld on network: Only unopenable Windows Network folder in "Browse Network".

Both Mac and Mybookworld on network: openable Mac share + openable Windows Network folder in which I can access both the mybookworld and Mac shares.

@Morbius1, you're right - there's something peculiar with Nautilus. This is, I emphasise, without the samba package installed as per a default installation. Although the samba package solves all these problems for me and makes things more elegant by revealing all the shares in the "Browse Network" without having to open the Windows Network folder, I won't install samba just yet. I want to see what happens in a default installation.

---

### Post by Morbius1 on 2011-08-13
"could not display smb:///" ?

Do you have the following packages installed:

gvfs-backends
gvfs-fuse

---

### Post by coffeecat on 2011-08-13
> **Morbius1 said:**
> "could not display smb:///" ?

Do you have the following packages installed:

gvfs-backends
gvfs-fuse

Yes.

---

### Post by jerrylamos on 2011-08-13
Install Samba and enable home user sharing on Narwhal and Ocelot.

Narwhal can see Ocelot, browse, copy.

Ocelot gets: (Aspire-5253 is where Narwhal is)

```
Opening "Aspire-5253"

You can stop this operation by clicking cancel.

                                       Cancel
```

After some time, Ocelot gets:
```

Unable to mount location.

Failed to receive share list from server.

                                OK
```


I've never seen either of these messages from Ubuntu before.

Obviously Ocelot can't browse anything.

And yes I've submitted a launchpad bug which the developers were not interested in.  It's been a while so I forget the bug # at the moment.
Yes I've been checking from time to time.  The above instance is on Alpha 3.  So I use sneakernet or emails.

Jerry

---

### Post by capscrew on 2011-08-13
> **jerrylamos said:**
> Install Samba and enable home user sharing on Narwhal and Ocelot.

Narwhal can see Ocelot, browse, copy.

Ocelot gets: (Aspire-5253 is where Narwhal is)

```
Opening "Aspire-5253"

You can stop this operation by clicking cancel.

                                       Cancel
```

After some time, Ocelot gets:
```

Unable to mount location.

Failed to receive share list from server.

                                OK
```


I've never seen either of these messages from Ubuntu before.

This is a very common error message when attempting to browse shares that are not included in the Master Browse List.  > 

Obviously Ocelot can't browse anything.

And yes I've submitted a launchpad bug which the developers were not interested in.  It's been a while so I forget the bug # at the moment.
Yes I've been checking from time to time.  The above instance is on Alpha 3.  
I feel your pain, but I also understand the developers point of view.  At this point who knows if it is a bug or not.> 
So I use sneakernet or emails.

Jerry
What have you done to configure name service resolution (DNS or NetBIOS) for your LAN?  How have you configured Samba?  It has been pointed out this is a testing forum.  Do you wish to do some testing?

---

### Post by sparker256 on 2011-08-13
> **jerrylamos said:**
> Install Samba and enable home user sharing on Narwhal and Ocelot.

Narwhal can see Ocelot, browse, copy.

Ocelot gets: (Aspire-5253 is where Narwhal is)

```
Opening "Aspire-5253"

You can stop this operation by clicking cancel.

                                       Cancel
```

After some time, Ocelot gets:
```

Unable to mount location.

Failed to receive share list from server.

                                OK
```


I've never seen either of these messages from Ubuntu before.

Obviously Ocelot can't browse anything.

And yes I've submitted a launchpad bug which the developers were not interested in.  It's been a while so I forget the bug # at the moment.
Yes I've been checking from time to time.  The above instance is on Alpha 3.  So I use sneakernet or emails.

Jerry

Here is your bug report and not sure why this is not resolved yet. I did a me to.

[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/804588](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/804588)

Bill

---

### Post by capscrew on 2011-08-13
> **sparker256 said:**
> Here is your bug report and not sure why this is not resolved yet. I did a me to.

[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/804588](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/804588)

Bill

Bill,

Are you willing to do some testing to see if the *"Failed to receive share list from server" *is truly a bug or just a common misconfiguration.  I have solved this problem on many systems.  I want to see if something has been changed in the code (doubtful) or something you can add your basic setup scenario.

I have been using Samba on Ubuntu since Dapper (6.06 LTS) with no real changes.  The code is stable both in the kernel and with Samba.  Gnome can create problems and I haven't any experience with Gnome 3.

Up for a challenge?

---

### Post by Yes_It's_Me on 2011-08-13
The thing is, this configuration crap shouldn't be needed. It should just work. If you can see a share in the network using nautilus, clicking on it should open it up, quickly and without error. That's it. End of story. If Ubuntu is going to become a more mainstream OS, this just needs to happen.

---

### Post by cariboo on 2011-08-14
> **Yes_It's_Me said:**
> The thing is, this configuration crap shouldn't be needed. It should just work. If you can see a share in the network using nautilus, clicking on it should open it up, quickly and without error. That's it. End of story. If Ubuntu is going to become a more mainstream OS, this just needs to happen.

Sharing files, does pretty well just plain work, if you are sharing them with another system running linux. It's when you throw Windows into the mix that things become a bit of a mess. If Windows was open open source there wouldn't be the need for any extra software. By default Ubuntu sees windows shares without any extra configuration, it's Windows that can't see shares on a system running Linux that is the problem.

If Windows had native support for nfs and sshfs things would be a lot easier.

---

### Post by capscrew on 2011-08-14
> **Yes_It's_Me said:**
> The thing is, this configuration crap shouldn't be needed. It should just work. If you can see a share in the network using nautilus, clicking on it should open it up, quickly and without error. That's it. End of story.
You would think so.  But it doesn't.  That's just the way it is.  Too many folks with too may ideas of what the default configuration should be.  I like the options as they are.  I configure my LAN as I have for any network I have setup in the last 20 years and Samba just works for me.>  If Ubuntu is going to become a more mainstream OS, this just needs to happen.
I doubt Linux in general and Debian/Ubuntu will ever be *mainstream * as a desktop and that is fine by me.  That is a philosophical thought anyway and not really OT for this thread.

---

### Post by capscrew on 2011-08-14
> **cariboo907 said:**
> Sharing files, does pretty well just plain work, if you are sharing them with another system running linux. It's when you throw Windows into the mix that things become a bit of a mess. If Windows was open open source there wouldn't be the need for any extra software. By default Ubuntu sees windows shares without any extra configuration, it's Windows that can't see shares on a system running Linux that is the problem.

If Windows had native support for nfs and sshfs things would be a lot easier.
The question is not file sharing per se.  It is browsing for the shares that is the problem.  Samba is a suite of applications, not one monolithic application.  Parts of Samba can work while other parts do not (until proper configuration).  Windows has little to do with this multifaceted operation other than revealing misconfiguration of the system.

---

### Post by coffeecat on 2011-08-14
I've now managed to set up a Vista share and I can report that browsing Vista's network share works for me in an Oneiric installation that has not been reconfigured. 

In each case I've tested with only the share server and my Oneiric host online as my earlier experiments revealed that the presence of both the Mac and WD Mybookworld facilitated the opening of the Windows Network folder without error.

**VISTA** - With Vista as the only other device online on my network: I click on "Browse Network" and see only the "Windows Network" folder. I can open this and see the "WORKGROUP" folder. Attempting to open this soon after booting up Vista led to the "failed" message, but **when I waited a couple of minutes**, I was able to open this folder to see the icon for my Vista machine and was able to connect to the share and copy files across.

To recap:

**MAC** - With the Mac as the only other device online on my network: I click on "Browse Network" and see both a "*mynames*'s Computer" icon and the "Windows Network" folder. The first icon allows me to connect to my Mac share; trying to open the "Windows Network" folder leads to the "failed to retrieve" message.

**MYBOOKWORLD** - With the WD Mybookworld as the only other device online on my network: I click on "Browse Network" and see only the "Windows Network" folder. I cannot open this - it gives me the "failed to retrieve" message.

I have not yet tested with another Ubuntu machine. I shall do so.

Conclusion: Nautilus is behaving differently depending on what type the smb server is. It is working just fine for me browsing a Windows share from a Windows machine - this is with an untweaked Oneiric system samba-wise

@jerrylamos, I have read your bug report. You do not specify what your other "pc's" were running. It would seem this is fundamental. And I disagree with your assertion about Lucid. I had no end of trouble in Lucid and had to do extensive tweaking - it wouldn't even resolve server hostnames out of the box for me. It was only with the arrival of Maverick or Natty that my blood-pressure began to come down, although I still installed the samba package as a matter of course.

Can I remind everyone that the simple installation of the samba package (no re-configuration at all) completely resolved this issue for me in Oneiric? Perhaps the samba experts could explain why that should be

---

### Post by coffeecat on 2011-08-14
> **coffeecat said:**
> I have not yet tested with another Ubuntu machine. I shall do so.

And now I have, and the results are interesting. Folks, it seems that Windows share browsing is (mostly) just fine in Oneiric's Nautilus after all, but there are still one or two issues.

I set up a quick-'n'-easy nautilus share in Natty in another machine. With just the Oneiric and Natty machines on the network, in Oneiric's Nautilus the "Windows Network" folder opens > "WORKGROUP" folder which I can open to show the Natty machine's icon. Opening that accesses the share OK and I can copy files to and from it.

I set up a nautilus share in a third machine in Natty and was able to open it, and copy back and forth. As I type, I am in Oneiric with Nautilus logged into two Natty shares and one Vista share, and I am copying files around between the four machines like there's no tomorrow. 

One oddity - if I try to copy *.png screenshots to a share from Oneiric, I get "there was an error copying the file into smb://hostname/foldername/ - no such file or directory". All other file types (that I have tried) copy OK, including *.png wallpapers. :confused: :? :-k 

I have answered the question in my OP. Browsing, mounting and copying to and from Windows shares in Windows, Ubuntu and MacOS using Oneiric's Nautilus seems to be OK. There's a problem with the WD mybookworld but I can get round this by installing the samba package. And if I remember correctly, this is what I had to do in Natty anyway.

And now you can talk among yourselves. :)

---

### Post by jerrylamos on 2011-08-14
> **capscrew said:**
> This is a very common error message when attempting to browse shares that are not included in the Master Browse List.  I feel your pain, but I also understand the developers point of view.  At this point who knows if it is a bug or not.
What have you done to configure name service resolution (DNS or NetBIOS) for your LAN?  How have you configured Samba?  It has been pointed out this is a testing forum.  Do you wish to do some testing?

What is this "Master Browser List"?  I haven't seen that on any Ubuntu since Dapper Drake Beta.  Is it something that Oneiric Ocelot now needs that is not needed by Narwhal, Meerkat, Lynx, ... ?

I've set up Samba on all of the Ubuntu's since Dapper Drake the same way, this is the first one that complained about a "server list".  I don't find it in "The Official Ubuntu Book".  

The couple Windows pc's that my wife has were not even turned on.  Narwhal has no problems copying jpg's from Windows, but of course Oneiric Ocelot can't browse anything because of some "server list"?

Jerry

---

### Post by coffeecat on 2011-08-14
> **jerrylamos said:**
> I've set up Samba on all of the Ubuntu's since Dapper Drake the same way, this is the first one that complained about a "server list".

Perhaps it's the way that you are configuring samba? Perhaps something that you had to do in Dapper is no longer relevant in Oneiric. As you can see from my previous two posts, opening shares from Windows, Ubuntu and Mac boxes "just works" in Oneiric. I did no configuration at all.

---

### Post by capscrew on 2011-08-14
> **jerrylamos said:**
> What is this "Master Browser List"?  I haven't seen that on any Ubuntu since Dapper Drake Beta.  Is it something that Oneiric Ocelot now needs that is not needed by Narwhal, Meerkat, Lynx, ... ?

I've set up Samba on all of the Ubuntu's since Dapper Drake the same way, this is the first one that complained about a "server list".  I don't find it in "The Official Ubuntu Book".  

The couple Windows pc's that my wife has were not even turned on.  Narwhal has no problems copying jpg's from Windows, but of course Oneiric Ocelot can't browse anything because of some "server list"?

Jerry

From the *Official Samba Documentation*> What Is Browsing?

To most people, browsing means they can see the MS Windows and Samba servers in the Network Neighborhood, and when the computer icon for a particular server is clicked, it opens up and shows the shares and printers available on the target server.

What seems so simple is in fact a complex interaction of different technologies. The technologies (or methods) employed in making all of this work include:

    *

      MS Windows machines register their presence to the network.
    *

      Machines announce themselves to other machines on the network.
    *

      One or more machines on the network collate the local announcements.
    *

      The client machine finds the machine that has the collated list of machines.
    *

      The client machine is able to resolve the machine names to IP addresses.
    *

      The client machine is able to connect to a target machine.

The Samba application that controls browse list management and name resolution is called nmbd. The configuration parameters involved in nmbd's operation are:

Browsing options:

    * os level
    * lm announce
    * lm interval
    * preferred master(*)
    * local master(*)
    * domain master(*)
    * browse list

For more information you can see [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html").

I am interested in seeing what the default install configuration really is.  Not anecdotal observation.  Again, are you interested in testing?

---

### Post by Morbius1 on 2011-08-14
> I am interested in seeing what the default install configuration really is.It was against my natural instincts but I just installed Oneiric in a VBox VM and I can answer that question. Did a "testparm -v" on the new install:
> os level = 20
lm announce = Auto
lm interval = 60
browse list = Yes
domain master = Auto
local master = Yes
preferred master = NoIf I'm not mistaken it's the same as it's been for previous versions of Ubuntu.

BTW, I can immediately see the current menagerie of hosts and their shares from Nautilus on my lan as always.

---

### Post by capscrew on 2011-08-14
> **Morbius1 said:**
> It was against my natural instincts but I just installed Oneiric in a VBox VM and I can answer that question. Did a "testparm -v" on the new install:
If I'm not mistaken it's the same as it's been for previous versions of Ubuntu.

```
os level = 20
lm announce = Auto
lm interval = 60
browse list = Yes
domain master = Auto
local master = Yes
preferred master = No 
```

BTW, I can immediately see the current menagerie of hosts and their shares from Nautilus on my lan as always.

Hi @Morbius1,
Does this install include Samba +samba-common or just samba-common?  In other words; is it a Samba server as well as a client?  It appears that nothing has changed in the code (as I expected) on both the Linux kernel and Samba.

Thanks for the information.

---

### Post by Morbius1 on 2011-08-14
No samba package installed - just samba-common and samba-common-bin. I wanted to see this from only a samba client perspective.

BTW, I can confirm the "Sharing Option" is missing from the context menu so nautilus-share is installed but the mechanism to automatically install the samba package itself is missing.

---

### Post by Morbius1 on 2011-08-14
Just installed Samba and the above parameters did not change.

On the nautilus-share front it's still missing from the context menu but it's still possible to create a usershare - although you have to do it from the CLI. For example:
```
net usershare add documents /home/morbius/Documents "morbius documents" everyone:F guest_ok=y
```This will in fact create a usershare at documents that is accessible on the lan. Of course it's not writable until you do a "chmod 777" which nautilus-share does automatically as part of its process and the syntax is butt ugly but ....

It just confirms I guess that the problem is not Samba ( usershare itself ) but something with nautilus-share, nautilus, gnome or some dependency that seem to be getting in the way.

---

### Post by capscrew on 2011-08-14
> **Morbius1 said:**
> Just installed Samba and the above parameters did not change.

On the nautilus-share front it's still missing from the context menu but it's still possible to create a usershare - although you have to do it from the CLI. For example:
```
net usershare add documents /home/morbius/Documents "morbius documents" everyone:F guest_ok=y
```This will in fact create a usershare at documents that is accessible on the lan. Of course it's not writable until you do a "chmod 777" which nautilus-share does automatically as part of its process and the syntax is butt ugly but ....

It just confirms I guess that the problem is not Samba ( usershare itself ) but something with nautilus-share, nautilus, gnome or some dependency that seem to be getting in the way.

I thought that the lack of usershare functionality was a nautilus and/or nautilus-share problem.  Am I correct6 that we are refering to Gnome 3?

It is interesting that you would get output from *testparm -v*  from a samba *client*.  I believe the smbd and nmbd daemons are not installed let alone running.  But I guess the /etc/samba/smb.conf is installed with samba-common.  Testparm reads the file but there is no daemon to read the config upon startup.

---

### Post by Morbius1 on 2011-08-14
Since it's part of Samba, a usershare can be created on any OS that has samba installed if you are willing to use the terminal. XFCE for example used to have a nautilus-share look-alike called thunar-shares-plugin that has disappeared from the repository but you can still create a usershare.

It looses it's appeal though from the command line - it's more intuitive at that point just to create a share definition in smb.conf.
> Testparm reads the file but there is no daemon to read the config upon startup.I don't know ... is that true? I guess you're right. I just thought that since there are client level parameters in smb.conf that some mechanism was used to read it and act upon it.

---

### Post by capscrew on 2011-08-14
> **Morbius1 said:**
> Since it's part of Samba, a usershare can be created on any OS that has samba installed if you are willing to use the terminal. XFCE for example used to have a nautilus-share look-alike called thunar-shares-plugin that has disappeared from the repository but you can still create a usershare.

It looses it's appeal though from the command line - it's more intuitive at that point just to create a share definition in smb.conf.
i know how the mechanism works.  My comment was that the problem is with Nautilus's implementation of Samba usershares.  I'm well aware of how to configure usershares via the terminal.> 


I don't know ... is that true? I guess you're right. I just thought that since there are client level parameters in smb.conf that some mechanism was used to read it and act upon it.
What *client level parameters * are you referring to?  The /etc/samba/smb.conf file is how you configure the smbd and nmbd deamons.

---

### Post by Morbius1 on 2011-08-14
client lanman auth
client ntlmv2 auth
client plaintext auth

There may be others - only ones I can think of at the moment.

---

### Post by capscrew on 2011-08-14
> **Morbius1 said:**
> client lanman auth
client ntlmv2 auth
client plaintext auth

There may be others - only ones I can think of at the moment.

I believe all of the these are to configure the *smbd* daemon respond to various client responses rather than actually configuring a client.

---

### Post by Morbius1 on 2011-08-14
Let's take the first one:
> lanman auth (G) This parameter determines whether or not [smbd]("http://www.samba.org/samba/docs/man/manpages-3/smbd.8.html") will attempt to     authenticate users or permit password changes     using the LANMAN password hash.> client lanman auth (G) 
This parameter determines whether or not [smbclient]("http://www.samba.org/samba/docs/man/manpages-3/smbclient.8.html") and other samba client     tools will attempt to authenticate itself to servers using the     weaker LANMAN password hash.I've actually used the client lanman auth parameter on a linux client to solve a problem accessing a D-Link DNS-323 NAS that had a very old version of samba installed on it.

I hope it wasn't just a coincidence. That's a slippery slope :wink:

---

### Post by capscrew on 2011-08-14
> **Morbius1 said:**
> Let's take the first one:> lanman auth (G) ***This parameter determines whether or not smbd will attempt*** to authenticate users or permit password changes using the LANMAN password hash. 
The bold speaks for itself> 

I've actually used the client lanman auth parameter on a linux client to solve a problem accessing a D-Link DNS-323 NAS that had a very old version of samba installed on it.

I hope it wasn't just a coincidence. That's a slippery slope :wink:
One wonders which was the client and which was the server in those cases.  The lanman auth is a conversation between the two hosts.

On the other hand who really cares in this instance.  That stuff is really ancient history.  :-)

---

### Post by Morbius1 on 2011-08-14
Agreed, the bold speaks for itself:

> client lanman auth (G) 
**This parameter determines whether or not [smbclient]("http://www.samba.org/samba/docs/man/manpages-3/smbclient.8.html") and other samba client     tools will attempt** to authenticate itself to servers using the     weaker LANMAN password hash.                      

---

### Post by sparker256 on 2011-08-14
> **capscrew said:**
> Bill,

Are you willing to do some testing to see if the *"Failed to receive share list from server" *is truly a bug or just a common misconfiguration.  I have solved this problem on many systems.  I want to see if something has been changed in the code (doubtful) or something you can add your basic setup scenario.

I have been using Samba on Ubuntu since Dapper (6.06 LTS) with no real changes.  The code is stable both in the kernel and with Samba.  Gnome can create problems and I haven't any experience with Gnome 3.

Up for a challenge?
I had some other issues that I was looking at but I am sure up to a challenge. My system is as follows.


Machine one
Five installs
Natty 32 and 64
Oneiric 32 and 64
Windows XP 32

Machine two
Natty 32
Windows XP 32

Machine three
Natty 32
Windows XP 32

My Natty installs all work like I have seen from about 8.04 but not sure what is going on with Oneiric and at first thought it was gnome3 related but not sure now.

When I click on browse networks in nautilus it takes about a minute to display the Windows Network icon. Double clicking on the I get my WORKGROUP icon and double clicking on that after about same amount of time get the Unable to mount location.

I also have a D-Link DNS 320 that seems to be working correctly as I can browse to it.

Nautilus does not have the sharing options that has been there in past versions so I have wondered if that was my problem but sure want to know for sure.

Thanks for the offer Bill

---

### Post by jerrylamos on 2011-08-14
> **Morbius1 said:**
> It was against my natural instincts but I just installed Oneiric in a VBox VM and I can answer that question. Did a "testparm -v" on the new install:
If I'm not mistaken it's the same as it's been for previous versions of Ubuntu.

BTW, I can immediately see the current menagerie of hosts and their shares from Nautilus on my lan as always.

Hmmm.  Did testparm -v on installed in hardware Oneiric which doesn't look like yours:

jerry@Compaq:~$ testparm -v

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[jerry]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

The resulting dump is huge.  I'm not a Samba programmer so it doesn't make much sense to me.  

? 

Jerry

---

### Post by jerrylamos on 2011-08-14
> **coffeecat said:**
> Perhaps it's the way that you are configuring samba? Perhaps something that you had to do in Dapper is no longer relevant in Oneiric. As you can see from my previous two posts, opening shares from Windows, Ubuntu and Mac boxes "just works" in Oneiric. I did no configuration at all.
Think Dapper is too old?  How about Narwhal, Meerkat, Lynx, ... I've done network file browsing and copying on all of them, except Ocelot.  Narwhal can copy from Ocelot but Ocelot can't browse anything, and that's on my tower, my notebook, and my netbook.

Thanks for looking anyway.

Jerry

---

### Post by capscrew on 2011-08-14
> **Morbius1 said:**
> > lanman auth (G) This parameter determines whether or not smbd will attempt to authenticate users or permit password changes using the LANMAN password hash. Agreed, the bold speaks for itself:

Yes indeed.  I'd forgotten about smbclient reading the smb.conf file.  You can see this when you call it with the -d3 switch.  See below:
```
$ smbclient -d3 -L malibu
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() -[B][COLOR="Blue"] Processing configuration file "/etc/samba/smb.conf"
Processing section "[global][/COLOR][/B]"
added interface eth0 ip=fe80::223:54ff:fe52:1a6e%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.3 bcast=192.168.1.255 netmask=255.255.255.0
Client started (version 3.4.7).
```

Note that I am calling the Samba server by name, not the IP address. :D

---

### Post by capscrew on 2011-08-14
> **sparker256 said:**
> I had some other issues that I was looking at but I am sure up to a challenge. My system is as follows.


Machine one
Five installs
Natty 32 and 64
Oneiric 32 and 64
Windows XP 32

Machine two
Natty 32
Windows XP 32

Machine three
Natty 32
Windows XP 32

My Natty installs all work like I have seen from about 8.04 but not sure what is going on with Oneiric and at first thought it was gnome3 related but not sure now.

When I click on browse networks in nautilus it takes about a minute to display the Windows Network icon. Double clicking on the I get my WORKGROUP icon and double clicking on that after about same amount of time get the Unable to mount location.

I also have a D-Link DNS 320 that seems to be working correctly as I can browse to it.

Nautilus does not have the sharing options that has been there in past versions so I have wondered if that was my problem but sure want to know for sure.

Thanks for the offer Bill

Bill,

Before we delve into the mysteries of Samba/Gnome/Nautilus, tell me what *hosts/netbios* name resolution you use.  Can you ping each host by hostname?  Are all these machines on the same subnet?  Have you given any of the Samba servers netbios names?

---

### Post by capscrew on 2011-08-14
> **jerrylamos said:**
> Hmmm.  Did testparm -v on installed in hardware Oneiric which doesn't look like yours:

jerry@Compaq:~$ testparm -v

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[jerry]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

The resulting dump is huge.  I'm not a Samba programmer so it doesn't make much sense to me.  

? 

Jerry

I believe morbius1 pulled those parameters from the dump.  He knew what he was looking for.  You can parse the dump for specific terms if you like with *grep*.  Like this```
testparm -v | grep [COLOR="Red"]client[/COLOR]
```

This returns the following from the dump (everything else is suppressed).```
$ testparm -v|grep client
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[Public]"
Processing section "[ISO]"
Processing section "[Backup]"
Processing section "[homes]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

	[COLOR="Red"]client[/COLOR] schannel = Auto
	[COLOR="Red"]client[/COLOR] NTLMv2 auth = No
	[COLOR="Red"]client[/COLOR] lanman auth = No
	[COLOR="Red"]client[/COLOR] plaintext auth = No
	[COLOR="Red"]client[/COLOR] signing = auto
	[COLOR="Red"]client[/COLOR] use spnego = Yes
	[COLOR="Red"]client[/COLOR] ldap sasl wrapping = plain
	use [COLOR="Red"]client[/COLOR] driver = No

```

These do not have to be in the smb.conf file.  If not mentioned then Samba assumes the defaults.  To see all of the parameters and their defaults look [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://samba.org/samba/docs/man/manpages-3/smb.conf.5.html").  Every term you saw in the dump is listed here with a small discussion of the use.

---

### Post by jerrylamos on 2011-08-15
> **capscrew said:**
> I believe morbius1 pulled those parameters from the dump.  He knew what he was looking for.  You can parse the dump for specific terms if you like with *grep*.  Like this```
testparm -v | grep [COLOR="Red"]client[/COLOR]
```

This returns the following from the dump (everything else is suppressed).```
$ testparm -v|grep client
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[Public]"
Processing section "[ISO]"
Processing section "[Backup]"
Processing section "[homes]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

	[COLOR="Red"]client[/COLOR] schannel = Auto
	[COLOR="Red"]client[/COLOR] NTLMv2 auth = No
	[COLOR="Red"]client[/COLOR] lanman auth = No
	[COLOR="Red"]client[/COLOR] plaintext auth = No
	[COLOR="Red"]client[/COLOR] signing = auto
	[COLOR="Red"]client[/COLOR] use spnego = Yes
	[COLOR="Red"]client[/COLOR] ldap sasl wrapping = plain
	use [COLOR="Red"]client[/COLOR] driver = No

```

These do not have to be in the smb.conf file.  If not mentioned then Samba assumes the defaults.  To see all of the parameters and their defaults look [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://samba.org/samba/docs/man/manpages-3/smb.conf.5.html").  Every term you saw in the dump is listed here with a small discussion of the use.

On Oneiric here I got something different:

```
jerry@Compaq:~$ testparm -v | grep client
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Global parameter workgroup found in service section!
Processing section "[jerry]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions
	client schannel = Auto
	client NTLMv2 auth = No
	client lanman auth = No
	client plaintext auth = No
	client use spnego principal = No
	client signing = auto
	client use spnego = Yes
	client ldap sasl wrapping = plain
	use client driver = No

```

and on trying to browse local network I get
"Unable to mount location"

Anyone have anything to try?

Same hardware, same network, same Samba setup, Narwhal has no problem.

Jerry

---

### Post by capscrew on 2011-08-15
> **jerrylamos said:**
> On Oneiric here I got something different:

```
jerry@Compaq:~$ testparm -v | grep client
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
**[COLOR="Red"]Global parameter workgroup found in service section![/COLOR]**
Processing section "[jerry]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions
	client schannel = Auto
	client NTLMv2 auth = No
	client lanman auth = No
	client plaintext auth = No
	client use spnego principal = No
	client signing = auto
	client use spnego = Yes
	client ldap sasl wrapping = plain
	use client driver = No

```

and on trying to browse local network I get
"Unable to mount location"

Anyone have anything to try?

Same hardware, same network, same Samba setup, Narwhal has no problem.

Jerry

I highlighted an error that I see right off the bat (see red above).  post the output of ```
testparm -s
```  This should output the working smb.conf file.

What are you using in your LAN for host name resolution?  How about you posting the contents of your /etc/hosts file ```
cat /etc/hosts
```

---

### Post by Morbius1 on 2011-08-15
[1] A note on testparm.

You might want to actually do a find on /etc/samba/smb.conf and see if you have a "workgroup =" line in the [global] section as well. testparm will NOT show the workgroup if it's the default: "workgroup = workgroup" and in the correct section.

[2] This one's new:
> client use spnego principal = NoHad to go to google for this one: 
Samba 3.6 Features added/changed: [http://wiki.samba.org/index.php/Samba_3.6_Features_added/changed](http://wiki.samba.org/index.php/Samba_3.6_Features_added/changed)
> The impact of 'client use spnego principal = no' is that Samba will use  CIFS/hostname to obtain a kerberos ticket, acting more like Windows when  using Kerberos against a CIFS server in smbclient, winbind and other  Samba client tools.  This will change which servers we will successfully  negotiate kerberos connections to.  This is due to Samba no longer  trusting a server-provided hint which is not available from Windows 2008  or later.  For correct operation with all clients, all aliases for a  server should be recorded as a as a servicePrincipalName on the server's  record in AD.  ([COLOR=Blue]For this reason, this behavior change and parameter was  also made in Samba 3.5.9[/COLOR])Not sure what to make of that yet.

---

### Post by jerrylamos on 2011-08-15
Capscrew,

I did have two WORKGROUP lines, somehow when my wife's Windoze is on it shows up under WORKGROUP even though it thinks it has the same workgroup name as ubuntu, in this case LAUREL.

So I put in one WORKGROUP = LAUREL line in the expected place.

No help.

Still gets "Unable to mount location" even though Narwhal has no such trouble, same hardware, same network, same smb.conf.

Tried testparm -s and got:

```
[global]
        workgroup = LAUREL
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d

[homes]
        comment = Home Directories

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[jerry]
        path = /home/jerry
        guest ok = Yes

```

whatever that means, example "Bad User"  ?

Now /etc/hosts is:

```
127.0.0.1       localhost
127.0.1.1       Compaq

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

whatever all that means.  Compaq is the name of this pc.

?

Thanks, Jerry

---

### Post by Morbius1 on 2011-08-15
If you run the following command can you see your own share (jerry):
```
smbtree
```
And if it shows you errors post the entire output please.

---

### Post by jerrylamos on 2011-08-15
Morbius1,

Yeah, errors:

```
jerry@Compaq:~$ smbtree
Enter jerry's password: 
WORKGROUP
	\\ASPIRE-5253    		Aspire-5253 server (Samba, Ubuntu)
cli_start_connection: failed to connect to ASPIRE-5253<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
LAUREL
	\\IBM-1FE65896216		NetVista2
cli_start_connection: failed to connect to IBM-1FE65896216<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
	\\COMPAQ         		Compaq server (Samba, Ubuntu)
		\\COMPAQ\IPC$           	IPC Service (Compaq server (Samba, Ubuntu))
		\\COMPAQ\jerry          	
		\\COMPAQ\print$         	Printer Drivers
		\\COMPAQ\homes          	Home Directories

```
ASPIRE-5253 is another Oneiric on the network
Netvista2 is Windows which is set up to share photo's, documents, ...
COMPAQ is this pc

Usually this PC will show up as an icon on "Network" but it doesn't.
What shows up is "LAUREL" and "WORKGROUP"
selecting gets "Unable to mount location".

Any clue on what "NT_STATUS_UNSUCCESSFUL" is and what to try next?

Thanks, Jerry

---

### Post by Morbius1 on 2011-08-15
What I do when this comes up is 2 fold:

* Temporarily disable any firewall you have on the other box and run smbtree again to see if the error goes away.

* If not then change the order of name resolution samba uses:

Edit /etc/samba/smb.conf and add to the [global] section the following line:
```
name resolve order = bcast host lmhosts wins
```Then save smb.conf and restart samba:
```
sudo service smbd restart
```Wait a few minutes ( like the 10 - 15 minutes that capscrew talked about previously ) and run smbtree again and see if the errors go way.

---

### Post by capscrew on 2011-08-15
> **jerrylamos said:**
> Capscrew,

I did have two WORKGROUP lines, somehow when my wife's Windoze is on it shows up under WORKGROUP even though it thinks it has the same workgroup name as ubuntu, in this case LAUREL.

So I put in one WORKGROUP = LAUREL line in the expected place.

No help.

Still gets "Unable to mount location" even though Narwhal has no such trouble, same hardware, same network, same smb.conf.

Tried testparm -s and got:

```
[global]
        workgroup = LAUREL
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d

[homes]
        comment = Home Directories

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[jerry]
        path = /home/jerry
        guest ok = Yes

```

whatever that means, example "Bad User"  ?  
Paraphrasing -- ```
This tells smbd(8) what to do with user login requests that don't match a valid UNIX user in some way.

Bad User -A user with no username in the smbpasswd database (no samba user), in which case it is treated as a guest login and mapped into the guest account.

The default guest account is the user *nobody*

```
It is listed [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://samba.org/samba/docs/man/manpages-3/smb.conf.5.html") under *map to guest (G)*. >  

Now /etc/hosts is:

```
127.0.0.1       localhost
127.0.1.1       Compaq

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

whatever all that means.  Compaq is the name of this pc.?

Thanks, Jerry
To me it means you have not setup any name services for this host.

I'll let Morbius1 take the lead.  I feel it's not helpful to you for 2 people to try and diagnose the problem.

---

### Post by capscrew on 2011-08-15
> **Morbius1 said:**
> What I do when this comes up is 2 fold:

* Temporarily disable any firewall you have on the other box and run smbtree again to see if the error goes away.

* If not then change the order of name resolution samba uses:

Edit /etc/samba/smb.conf and add to the [global] section the following line:
```
name resolve order = bcast host lmhosts wins
```Then save smb.conf and restart samba:
```
sudo service smbd restart
```Wait a few minutes ( like the 10 - 15 minutes that capscrew talked about previously ) and run smbtree again and see if the errors go way.

If this host is to use netbios then Jerry needs to declare that in the [global] section of the smb.conf file.  Like this...```
netbios name = COMPAQ
```

Edit:  This should provide netbios naming for this host.  The combination of declaring the netbios name and the using bcast to resolve the name will allow this host to be visible when browsing.

---

### Post by jerrylamos on 2011-08-15
> **Morbius1 said:**
> What I do when this comes up is 2 fold:

* Temporarily disable any firewall you have on the other box and run smbtree again to see if the error goes away.

* If not then change the order of name resolution samba uses:

Edit /etc/samba/smb.conf and add to the [global] section the following line:
```
name resolve order = bcast host lmhosts wins
```Then save smb.conf and restart samba:
```
sudo service smbd restart
```Wait a few minutes ( like the 10 - 15 minutes that capscrew talked about previously ) and run smbtree again and see if the errors go way.

Morbius1, the 
```
name resolve order = bcast host lmhosts wins
```
fixed it.

Suits me.  Any idea what it does?

Thanks much, Jerry

---

### Post by Morbius1 on 2011-08-16
There is probably a more elegant ( and technically accurate ) way to describe this but I am not an elegant person :wink: :

"name resolve order" determines what naming services samba will use and in what order. The naming services is what converts the machine's name to an ip address. The default in samba is this:
> name resolve order = lmhosts wins host bcast* "lmhosts" and "host" have to be set up with what is essentially a lookup table that says this ip address belongs to this machine name. It's not set up by default - it's something you have to do and it requires that all machines have static ( or reserved ) ip addresses to work.

* "wins" refers to a WINS server which is a server specifically set up to provide name services to the lan. This is not set up by default either and it requires modifications to not only the machine you specify as the WINS server but also to all the clients.

* "bcast" refers to broadcast and it's just that. Every machine broadcasts it's presence on the lan. It's the only one that is enabled by default and unless you modify things is always a default functional option on Windows.

Linux will go through each option in the default order to try to resolve the name but you will notice that the only working mechanism "bcast" is listed last. Some of those options it can go through quickly - it tries lmhosts and host and finds nothing there so it moves on. But then it hits "wins"

[COLOR=Blue]Note: The following is based on my own experiences and is offered as such:[/COLOR]

What appears to happen is that it tries to find a wins server and cannot and times out, stops, and never gets to "bcast". Sometimes when a user does an smbtree instead of getting this:
>  failed to connect to ASPIRE-5253<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFULThey will get something like this:
>  failed to connect to ASPIRE-5253<20> (207.69.188.186). Error NT_STATUS_UNSUCCESSFULIt looks spooky at first since that's a public ip address not an internal ip address. But it turns out that ip address is the DNS server of their ISP and it appears that samba is leaving the lan to try to resolve the machine name ( I suspect "DNS redirection" by the ISP is the culprit here ).

Anyway, placing "bcast" first, or at least before "wins", sometimes resolves the issue as it places the only default functional mechanism first.

Sorry you asked ? :P

Getting to the original intent of this topic however is the still unanswered question: Why is Oneiric performing differently than earlier versions for some users. We've already determined that Samba itself is different but we don't know what else is different - and to be fair this is not a released OS yet either.

---

### Post by jerrylamos on 2011-08-16
Morbius1, > 
Sorry you asked ?

Getting to the original intent of this topic however is the still unanswered question: Why is Oneiric performing differently than earlier versions for some users. We've already determined that Samba itself is different but we don't know what else is different - and to be fair this is not a released OS yet either.


Not at all sorry!  For whatever reason the whole "network scenario" has grown up like Topsy with all sorts of appendixes and dead ends, my opinion.

Yes this isn't a released product yet, that's why us testers are looking for problems.  I'm just an ordinary user and don't know the intricate code, so all I can do is try to find situations where it's busted.  Sometimes the things we find are fixed in the released product, sometimes they aren't example Intrepid and Intel video.

Thanks for your insight and the fix.  I'll be interested to see whether the developers resolve this problem I and some others saw, or whether Oneiric will be released as is in this area.

Jerry

---

### Post by akand074 on 2011-08-17
I'm not sure if this is the right place to ask but seems to be on topic. Has anyone managed to set up shares in Ubuntu to be visible in Windows now that Ubuntu is using Gnome 3? I still haven't been able to set up a proper share which is why I dropped to Unity from Gnome-shell in 11.04. Does anyone know if Nautilus-share will be returning? I used to just right click a folder and press share and I'm done. Now I can't do it at all. Even using system-config-samba hasn't functioned properly but I mean just right clicking a folder is the most convenient way of doing it.

Basically, how is everyone setting up share folders now in Gnome 3? (or how have they always been doing it successfully).

---

### Post by Morbius1 on 2011-08-17
About 2 weeks ago in this thread ;)  I mentioned that nautilus-share for Gnome3 has a bug:

> I don't know if this is fixed yet or how it relates to Oneiric: [https://groups.google.com/forum/#!topic/linux.debian.bugs.dist/0SpS9lUhr-g]("https://groups.google.com/forum/#%21topic/linux.debian.bugs.dist/0SpS9lUhr-g")

     Quote:
                                                 Package: nautilus-share
Severity: important
Tags: experimentalnautilus-share depends on libnautilus-extension1, which conflicts with libnautilus-extension1a. The latter is needed for nautilus, brasero, evince, etc, etc on GNOME3. nautilus-share should depend on the newer libnautilus-extension1a                      I just looked at synaptic and libnautilus-extension1 is there but not 1a so I'm not sure what's going on here. It would be unfortunate if it ships without it.

---

### Post by akand074 on 2011-08-17
Thanks a lot! Finally got some information about this. Yes it would be very unfortunate if it ships without it. Though if I can get it to work via ppa or source or any other way that'd be fine by me.

---

### Post by madjr on 2011-08-21
i dont see an option to share folders over the network in nautilus 3...

this seems to be another important thing lacking...

this is a deal breaker for me, i can live for a while without changing themes, but no folder sharing? apart from being uglier, this is another con to the new nautilus.

anyone know a workaround?

thanks.

---

### Post by cbowman57 on 2011-08-21
Probably have to compile it yourself but I found this on the Arch AUR [http://ftp.gnome.org/pub/GNOME/sources/nautilus-share/0.7/](http://ftp.gnome.org/pub/GNOME/sources/nautilus-share/0.7/)

Here's a ppa [http://www.ubuntuupdates.org/packages/show/364261](http://www.ubuntuupdates.org/packages/show/364261)

Better link [https://launchpad.net/~gnome3-team/+archive/gnome3/+packages?field.name_filter=nautilus&field.status_filter=published&field.series_filter=natty](https://launchpad.net/~gnome3-team/+archive/gnome3/+packages?field.name_filter=nautilus&field.status_filter=published&field.series_filter=natty)  

Looks like you'll have to use the one built for natty, but it should work in Oneiric.

---

### Post by JRV on 2011-08-21
To share with another Ubuntu machine I use sftp.

I think you need to install openssh, instructions here:

  [https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html)

Then enter the command:

```

nautilus sftp://USER@HOSTNAME/home/USER

```

To access a Windows share:
```

nautilus smb://WINDOWS_HOSTNAME/SHARENAME

```

To access a shared folder on Ubuntu from Windows you need samba.  I can't help with that, I don't allow it on my network.

---

### Post by Morbius1 on 2011-08-21
"Sharing Option" in nautilus does not work at the moment. The package that makes that happen ( nautilus-share ) is installed but does nothing. There's a Debian bug report about this which I cannot find at the moment but it has to due with a dependency that if installed will break just about everything else so .....

There are Ubuntu bug reports here:
[https://bugs.launchpad.net/ubuntu/oneiric/+source/nautilus-share/+bug/829479](https://bugs.launchpad.net/ubuntu/oneiric/+source/nautilus-share/+bug/829479)
[https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/823937](https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/823937)

In the last bug it was reclassified from "Wishlist" ( you have to wonder who prioritizes things here ) to "Critical" so there may be reason for hope that this will get fixed.

---

### Post by portis on 2011-08-21
I packaged nautilus-share in my ppa. There are other packages in that ppa, so you may just manually download that package and install.

[https://launchpad.net/~portis25/+archive/test/+packages](https://launchpad.net/~portis25/+archive/test/+packages)

---

### Post by madjr on 2011-08-21
thanks guys for the responses, i see there's hope to get the feature back in one of the betas.

am sub to the bug reports, others might want to do as well.

---

### Post by sparker256 on 2011-08-21
> **portis said:**
> I packaged nautilus-share in my ppa. There are other packages in that ppa, so you may just manually download that package and install.

[https://launchpad.net/~portis25/+archive/test/+packages](https://launchpad.net/~portis25/+archive/test/+packages)

A little more info please. Are you saying that you have sharing options in your nautilus? I am waiting for the day when this works out of the box like with a live USB like natty does.

Thanks Bill

---

### Post by jbicha on 2011-08-21
The new version of nautilus-share is already in Debian; it just needs to get synced into Ubuntu.

---

### Post by cariboo on 2011-08-21
Merged two similar threads.

---

### Post by Morbius1 on 2011-08-22
> **cariboo907 said:**
> Merged two similar threads.
The original thread deals with a samba client.
The new thread deals with a samba server.

But I fully appreciate that you are the moderator and "He who must be obeyed" :P

---

### Post by akand074 on 2011-08-24
> **madjr said:**
> thanks guys for the responses, i see there's hope to get the feature back in one of the betas.

am sub to the bug reports, others might want to do as well.

IT'S BACK! I'm so ecstatic about this. Sharing options is working now. My one biggest issue I've had with gnome 3. Wow today has been nothing but good news for me.

---

### Post by jerrylamos on 2011-09-07
Beta 1 updated still busted for me on Network Browse Network.  
Other Ubuntu releases see Oneiric Ocelot, Beta 1 can't see anything not even itself on browse networks.

Is there a launchpad bug on browse networks not browsing networks?

Jerry

---

### Post by jerrylamos on 2011-09-07
> **Morbius1 said:**
> I don't mean to be a pain in the butt ... but:
I'm not disagreeing with anything capscrew is saying but it looks to me that name services are running just fine, thank you very much.

I think you all would have to admit there seems to be something peculiar with "Network" in Nautilus. If you're up for an experiment try bypassing "Network":

Do the Ctrl+L and type:
```
smb://
```No ip address - no host name - just "smb://"

Now bookmark it. What should happen is that you get a listing on the left side panel titled: Windows Network

Now Reboot and instead of going to "Network" select "Windows Network".
bash: smb://: No such file or directory

? 

Jerry

By the way, this is a multiboot, no problem with browse networks with Natty, Meerkat, Lucid, ...  Oneiric is busted.  Something about a "shares list"

Jerry

---

### Post by cariboo on 2011-09-07
> **jerrylamos said:**
> bash: smb://: No such file or directory

? 

Jerry

By the way, this is a multiboot, no problem with browse networks with Natty, Meerkat, Lucid, ...  Oneiric is busted.  Something about a "shares list"

Jerry

You're doing it wrong, open nautilus, press ctrl-l then type:

```
smb://
```

in the location box. You should see your workgroup in nautilus.

---

### Post by jerrylamos on 2011-09-08
cariboo907 thanks, I tried again:

in terminal session:
```

sudo nautilus
Ctrl-l
smb://
"Could not find /home/jerry/smb:".

```

Oops, shouldn't have used "sudo"?

Tried it without.  It found my local network icon.  Selected it.  After a while,  "Failed to retrieve share list from server."

In between, booted Narwhal using the "Home Folder" launcher and selecting "browse networks", gets the network and the running pc's on it almost instantly.

?

jerry

---

### Post by coffeecat on 2011-09-08
> **jerrylamos said:**
> ```

sudo nautilus
```

Why sudo?? :o

You don't need sudo. 

Simply open your home folder from the launcher, press ctrl-L to reveal the text address bar, and type "smb://".

---

