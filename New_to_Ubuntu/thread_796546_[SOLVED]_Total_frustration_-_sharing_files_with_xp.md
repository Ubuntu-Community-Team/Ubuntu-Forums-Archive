---
title: "[SOLVED] Total frustration - sharing files with xp"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by naggis on 2008-05-16
I am running Hardy on my laptop and want to see files on my xp laptop. Searches on the Internet and in this forum have not brought up any means of sorting out the problem. The laptop can ping the xp desktop but whatever I do, the desktop cannot be found. Samba has been installed and file sharing has been set up on the desktop.
There does not seem to be a simple Howto which applies to Hardy to setup file sharing
PLEASE - can anyone offer any help in this matter before I throw the lot through the window (or is that Window)
Thanks very much in anticipation

---

### Post by ZabiGG on 2008-05-16
Hi there ;)

There are many options, but I prefer to access my XP directly through a remote desktop tool.

Check out [TightVNC]("http://www.tightvnc.com/") and [FreeNX]("https://mail.kde.org/mailman/listinfo/freenx-knx").

In my opinion, and I'm no expert, this is WAY more convenient than sharing.

You'll have to make your system secure, though.

Cheers,

ZabiGG

---

### Post by ZabiGG on 2008-05-16
And I read your post wrong! lol

sorry, I hadn't realized you had partitioned and both were on the same computer!

Newbie mistake!! ;)

---

### Post by naggis on 2008-05-16
Now that is an idea that had not occurred to me before. So lets give it a try - I'll report back with the results.

---

### Post by naggis on 2008-05-16
Zabigg - you were right first time. The laptop is dual boot but the desktop is straight xp all the way.

---

### Post by alphaniner on 2008-05-16
Have you tried just opening 'My Computer' or something and typing the IP address into the browser bar?  It needs to be preceded by two back-slashes, ie:

```
\\XXX.XXX.XXX.XXX
```

---

### Post by ZabiGG on 2008-05-16
My honour (and -- very large -- ego) is saved ;) thanks!

---

### Post by naggis on 2008-05-16
Working through My Computer would effect the xp pc. What I really want to do is to see the desktop xp installation FROM the ubuntu laptop

---

### Post by alphaniner on 2008-05-16
My mistake, I got it backwards.  In this case try opening nautilus and typing

```
smb://XXX.XXX.XXX.XXX
```

in the location bar.

---

### Post by avtolle on 2008-05-16
If you have tried this, apologies in advance. Go to Places-->Network, click on Windows Network, select the workgroup name you gave it when setting Samba up; does the XP box show then? If it does, click on the icon with the machine name, and you should see the various folders you designated for sharing appear. If you've done this already without success, then there may be an issue with the setup of Samba on the Ubuntu laptop.

---

### Post by naggis on 2008-05-16
Yes, I did try typing the address into nautilus - but no luck.
Maybe the problem is due to the setup of samba. I can't see the xp box at all in the network window. 
I assume that setting up file sharing is normally a simple affair and that few people have any problems. Am I in a very small minority in having the problem?
How can I edit the setup of samba?

---

### Post by ZabiGG on 2008-05-16
sorry Naggis, my dual install is on a Vista comp :(

---

### Post by bodhi.zazen on 2008-05-16
You need to start on Windows and configure a folder for share (and give it a name).

Then, in Ubuntu, go to Network and navigate to the share. open it and enter your windows log in name and password.

If that fails, open nautilus and enter :

//xxx.yyy.zzz/share

where xxx.yyy.zzz = the ip address of your windows box
and share = the name of the share you assigned when you set it up on Windows.

Samba should work out of the box with no additional configuration required on Ubuntu.

---

### Post by alphaniner on 2008-05-16
I'm pretty sure Samba Client is installed by default.  In other words, you shouldn't need to install anything to be able to view shares on an XP PC.  I have actually heard many stories about people who could see other computers *until* they installed Samba Server (that's what you install to share *from* Ubuntu).  IOW, installing Samba Server can bork Samba Client.

---

### Post by naggis on 2008-05-16
Thanks bodhi.zazen. Windows is set up to share files and this is proven as the dual boot xp on the laptop can see the shared files and work with them.
Ubuntu Network shows - Windows Network which contains Workgroup but not the HOME group I set up in Windows. Could it be that the Workgroup is a group set up to be a server on Ubuntu when I need Ubuntu to be the searching client?
Inputting the address and group name in nautilus results in the error message that this information could not be found.
My attempt to solve the problem seem to have caused Synaptic to stop working - it will not load.
Perhaps I need to reinstall Hardy and samba. One of the pieces of information I did come across seemed to say that to do what I want to do, it is not necessary to install samba - just smbfs. Does that make any sense?

---

### Post by avtolle on 2008-05-16
As to your final question, yes, this does make sense. I think you looked at the same source I did when setting my sharing up, and that's the path I followed to be successful. I've proceeded to install samba as I need to be able to get to my Ubuntu files from my Vista box, and have had success with this, too; but to do what you want to do, installing smbfs should work for you.

---

### Post by naggis on 2008-05-16
Thanks for that. Maybe I will do a reinstall and try the smbfs route as you found it to be successful.

---

### Post by avtolle on 2008-05-16
If you are using the same source as I, be sure to use CIFS and not smbfs. Forgot this earlier :-( See [https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently) for an explanation, presuming this is what you wish to do.

---

### Post by naggis on 2008-05-17
Well folks, the sad story continues. I did a complete reinstall including deleting and reinstating partitions and then installed smbfs. But the result is the same - I CANNOT SEE THE XP BOX. I can't help feeling that there is some setup feature that has not been accessed and sorted. Places > Network gets me to Windows Network then - nothing.
There is this voice in the back of my head that is saying "Cut your losses and throw all this lot out of the window" But the other advantages of Ubuntu are very much worth struggling for.
But - I need help
Thanks for ANY points you can offer.

---

### Post by ZabiGG on 2008-05-17
Hi Naggis ;)

I wonder if your problem is not on the XP side... I had the same problem when I tried to set up a network linking my Vista and XP boxes (before trying linux), and I never managed to see my XP shares from Vista. I gave up after a number of attempts, and it's one of the reasons I researched Ubuntu ;)

---

### Post by tact on 2008-05-17
Hi there...

I had something similar problem-wise...  XP machine could see the ubuntu box but the ubuntu box could not see the XP machine.

That the XP box could see the ubuntu machine, access shared folders on the ubuntu machine, etc..  all said to me that sharing was working... the computers were communicating.

(To share folders on the hardy ubuntu machine all I did was "right click" > sharing...  etc)

Eventually I found the problem - or rather the problem evaporated and I found out why...

I had my log viewer open and after anywhere between 15 and 55 minutes I would see some action in the log saying that the ubuntu machine was now masterbrowser for network "workgroup_name"

AFTER that the ubuntu box could see the XP box.   

I tried a few more times.. it was repeatable.  Until the masterbrowser election was completed the ubuntu box could not see the XP box.

Seems that while your setup may be fine, unless you wait wait...wait...wait..  til windows networking does its thing... calling for and processing elections for masterbrowser...  the browse list is not available to the ubuntu machine.

Maybe give it a shot.  Set yourself up thinking all is well...  then go off for a coffee..  come back in 45 min.  Then see if the ubuntu box can see the XP box.

This waiting is not a linux or ubuntu problem.  It is how MSwin peer networking works ... sometimes it can be a while before elections are completed.

---

### Post by naggis on 2008-05-17
Hi Zabigg
I am certainly at the point where I do not have a clue where the problem may lie. I have unearthed another tutorial that may sort the matter. So far the xp setup has been tweaked - so here goes with the ubuntu bits.

---

### Post by naggis on 2008-05-17
The latest situation is that I have worked through the tutorial here - [https://help.ubuntu.com/community/ComprehensiveSambaGuide](https://help.ubuntu.com/community/ComprehensiveSambaGuide).
I carefully went through resetting the xp  box. The computer name is FREDDESK, workgroup = MSHOME and the shared folder is called "share"
When trying to mount the windows share, I got the following error message -  username=ubuntu,password=ShareAccessPassword,workgroup=MSHOME,gid=smb,uid=$USER,fmask=770,dmask=770,rw //FREDDESK/share /media/winshares
bash: //FREDDESK/share: No such file or directory
This confirms the findings from Places > Network, that the laptop cannot see workgroup never mind the xp box.
Can anyone suggest a way forward from here?
I have tried waiting the suggested 45 mins (the second half of the FA cup) but no joy.

---

### Post by bodhi.zazen on 2008-05-17
First, if you want to use the hostname rather then IP address you need to add it to /etc/hosts

```
gksu gedit /etc/hosts
```

Format is :

ip_address  hostname

Second, what happens when you try 

connect to server (form the menu at the top) and enter :

//windows_ip_address/share

Note: "share" may be "Share" ....

you should then get a box where you enter the username, workgroup, and password ...

Usually you can ignore the workgroup ...

---

### Post by naggis on 2008-05-17
Thanks for the suggestions - I'll certainly give them a try and report back later.

---

### Post by naggis on 2008-05-17
The host name of the xp box has been added to the hosts list. But when I go to "connect to server" a box appears in Hardy. If Windows share is selected in Service type and the ip address added to the Server box - the error message is -
Cannot display location "smb //192.168.0.2/" No application is registered to handle this file.
Another point: Synaptic manager and other Administration tasks will not now load. Does this indicate a deeper problem?

---

### Post by bodhi.zazen on 2008-05-17
What change did you make to /etc/hosts ?

I hope you did not delete the lines for localhost and hostname ...

---

### Post by naggis on 2008-05-17
I left all the existing entries as they were. The full list is -
127.0.0.1  localhost
127.0.1.1  roger-laptop-HOME
192.168.0.2  FREDDESK (I added this)
::1        ip6 - localhost ip6 - loopback
fe00::0    ip6 - localnet
ff00::0    ip6 - mcastprefix
ff02::1    ip6 - allnodes
ff02::2    ip6 - allroutes
ff02::3    ip6 - allhosts
I wonder if line 2 should end with MSHOME as this is the name of the workgroup

---

### Post by bodhi.zazen on 2008-05-17
line 2 needs to lit your hostname.

you can show your hostname with the command :

```
hostname
```

---

### Post by Victormd on 2008-05-17
1. I don't know if I understood correctly, but you are dual-booting and trying to access your XP using ubuntu + file sharing (this is what I got from the first few posts - ***"I am running Hardy on my laptop and want to see files on my xp laptop"***)? If that is what you're trying to do, then samba is NOT the way to go. For you to be able to access a shared folder in XP, XP has to be running, and in dual-boot, it's either XP or Ubuntu running at any given time. The best thing to do would be to mount your XP drive. 

2. However, from the posts on pages 2 and 3, it seems like you have 2 computers, one with XP and the other with Ubuntu, if that's the case, the you should be able to open nautilus and type smb://xxx.xxx.xxx.x (ip number).

Which is it, 1 or 2?

---

### Post by naggis on 2008-05-17
Line 2 does list the host name of the ubuntu laptop as confirmed by typing the script you suggested.
I have also changed the "HOME" to "MSHOME" as this is the name of the workgroup setup in the xp desktop.
I do have 2 computers. The desktop runs xp only and holds all the files I want to access from the laptop which is dual booted with xp and ubuntu. On the laptop I can easily see the xp files from ubuntu in "Places" - is this a new feature of Hardy?
When you say I should open nautilus, do you mean that I should go to Places and then Network and setup a search in which I can write the text you suggest? This is what I did and there was just no response of any kind.
I am really sorry to have to ask such basic questions - although I have been dealing with Windows for the last 15 years, I have only been Linuxing for the last few weeks and it is all very new.

---

### Post by Victormd on 2008-05-17
go to PLACES>HOMEFOLDER and when the window opens, click on the notepad icon on the left (toggle between button and text-based location bar) then type smb://yourdesktop'sipaddress

and it should look like the attached image

---

### Post by naggis on 2008-05-17
Did what you said but inputting the ip address of the xp desktop had little effect. The wheel turned for 20 seconds or so then stopped and nothing came up.
Although I have done it a number of times before, I will again check this ip address and check that it can be pinged

---

### Post by Victormd on 2008-05-17
I don't know how much fideling you did with your host files and such, but you may have to check to see if everything is right.
I do this and didn't edit any files, simply typing the above gets me to my XP machine...
This is what my etc/hosts looks like
> 127.0.0.1	localhost
127.0.1.1	victor-ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by naggis on 2008-05-17
Now there is a thing. The ip address of the laptop is 192.168.0.2 - and I cannot ping it now. The router finishes .1 and that pings. You would expect the laptop to ping ok (its what I am using now) and it does - it finishes .3
The desktop pinged ok earlier in the day - so what have I done to stop it I wonder?
As Terry Wogan says "Is it me?"

---

### Post by naggis on 2008-05-17
In line 2 - is your computer called "victor" or "victor-ubuntu"
Maybe I should try removing the "MSHOME" workgroup name following my computer name.
I have just noticed that your home town is Tampa fl, so the note about Terry Wogan would not have had any effect on you - I am sorry.

---

### Post by Victormd on 2008-05-17
my ubuntu box is called victor-ubuntu. Like I mentioned before, I didn't touch this file, this is the default setting

quick and dirty... reset your router and see what that does.

---

### Post by naggis on 2008-05-17
I tried again the access the desktop using your suggested method. Under Place > Network there seems to be the chance to search for the workgroup (network name). But it said that it couldn't find the location with the following error message - Error: DBus error org.freedesktop.DBus.Error.InvalidArgs: Mountpoint Already registered
Please select another viewer and try again.
Can you make any sense of this?
I really appreciate the help you have offered so far - I guess you are getting as frustrated as I am by now.

---

### Post by bodhi.zazen on 2008-05-17
> **naggis said:**
> In line 2 - is your computer called "victor" or "victor-ubuntu"
Maybe I should try removing the "MSHOME" workgroup name following my computer name.
I have just noticed that your home town is Tampa fl, so the note about Terry Wogan would not have had any effect on you - I am sorry.

your computer name should be == the output of

```
hostname
```

No adding windows domains, no adding or editing the name, just host name.

> bodhi@ubuntu:~$ hostname
ubuntu

bodhi@ubuntu:~$ grep ubuntu /etc/hosts
127.0.1.1       ubuntu

If you change this to something like

127.0.1.1       ubuntu-MSHOME

you will break things like sudo and administrative access

---

### Post by naggis on 2008-05-17
Router reset - no difference

---

### Post by Victormd on 2008-05-17
well, when you go through places>network, the title reads network:/// and your network group shows up, right (that's what happens in mine) but then you can't access the network group by double clicking it (that's what happens in mine). If this is the case, you'll have to properly configure samba. since I didn't want to do that and for me it works just fine entering the ip, then on the "Go To:" location, you can type either
> network://ipaddress
or
smb://ipaddress (like before)
I guess if you want it anyother way, you'll have to edit your samba configuration file
```
sudo gedit /etc/samba/smb.conf
```
but I can't help you much here since I decided not to edit this file.
You can get some more info [here]("https://help.ubuntu.com/7.10/server/C/configuring-samba.html")

---

### Post by naggis on 2008-05-17
Hi Victormd. When I use Place > Network< I get Windows Network which is empty when I click it. 
I think that you have probably reached the end of the help you can give me as there is obviously something fairly drastically wrong with my installation. I too don't want to edit the samba file but maybe I will have ago tomorrow - if I muck it up then I will reinstall Hardy and try again. 
In fact, I might just download the iso file again in case there was a problem with the original - though I doubt it.
One of the advantages in investigating ubuntu was to keep my aging (well retired) grey matter moving, so I can't complain too loudly when things need the attention that this problem does.
Anyway, thanks again for your input - I am now off to bed (its that time here in the uk) and will have another look at the situation tomorrow.

---

### Post by Victormd on 2008-05-17
> **naggis said:**
> Hi Victormd. When I use Place > Network< I get Windows Network which is empty when I click it.
This happens to me too. I can't get to the network that way. I have to access it via the IP address(I honestly don't know why), using the lines in the previous posts.

> **naggis said:**
> there is obviously something fairly drastically wrong with my installation.
I wouldn't be so quick to jump to this conclusion...

> **naggis said:**
> One of the advantages in investigating ubuntu was to keep my aging (well retired) grey matter moving, so I can't complain too loudly when things need the attention that this problem does.
Always a good thing to do, and I think you found a good way to do so...

Were you able to ping your XP comp. again? Can you ping ubuntu from XP?

---

### Post by stinger30au on 2008-05-17
not sure if it has been mentioned, but try turning off any firewalls in xp and try again

---

### Post by naggis on 2008-05-18
I have turned off the windows firewall and made sure that my normal firewall is set to allow file sharing.
Having checked the desktop xp again, I think there could be a problem with file sharing there. So maybe the best thing to do is to start all over again and to reset this feature - maybe, just maybe, this will sort things out!!!

---

### Post by Victormd on 2008-05-18
It's worth a shot... let us know how that worked.

---

### Post by naggis on 2008-05-18
Good morning (or is it good afternoon) Victormd. I am currently in the final stages of reinstalling xp on the laptop - the desktop has already been done using Acronis TrueImage. This latter wouldn't work with dual boot for some reason so it was back to the old fashioned method. So far the laptop has taken just short of 2 hours and I an still reinstalling all the drivers. Makes the 15 - 20 mins for Hardy look a snip.
I'll let you know later how things went - its about tea time now!

---

### Post by naggis on 2008-05-18
At this moment it seems that the problem was with the xp setup on both the desktop and the laptop. Each of them has now been clean reinstalled at significant time loss. But even that did not fix the problem which was that neither pc could see the shared files on the other. After much net searching, I came across a post which suggested that the TCPIP may be in need of repair and pointed at a download to fix it - which it appears to have done. At this moment, each xp setup can see shared files on the other but the fix has damaged my antivirus program (NOD) which is resisting being fixed on the laptop. Isn't it great not to have to worry about such matters in Ubuntu?
Anyway, enough for today. Tomorrow I'll fix NOD and reinstall Hardy - any bets that that will not go as smoothly as I'd like?

---

### Post by naggis on 2008-05-19
How unsmooth can you get. There appears to be a problem with NOD firewall effecting the xp TCPIP setup. So far the laptop can see the desktop and access shared files in xp but the Hardy os on the laptop cannot see the desktop.
I'm going to call a halt for a few days to let the dust settle and see what steps to take next. If you have any, and I mean ANY, suggestions please post.
Thanks

---

### Post by Victormd on 2008-05-19
Your XP-laptop can share with XP-desktop so that rules out any router issues. Hardy can access the internet but won't ping your XP-desktop? Just an observation, I don't know if you did this already, but I think you have to install samba (it doesn't come bundled with hardy). Eventhough you won't be editing the samba configuration file, you would still need it installed to access your XP-desktop.

---

### Post by naggis on 2008-05-22
The problem is solved - whooppee.
XP was the cause. There was a conflict between the antivirus software and the TCPIP system which needed a fix to be downloaded and applied. But there was also a sneaky problem with the Windows firewall. Although this had been turned off and checked many times, a deep search showed up a window indicating that it was still active on networks - well done Uncle Bill!
So a thorough reinstalling and much searching finally unearthed the culprit. How easy it was to reinstall Hardy and then smbfs and find that it all worked - virtually out of the box as someone said earlier. Its not surprising that there is not much information out there to help sort ubuntu network problems - it just works.
Just a small point - it took me about 35 minutes to install Hardy and get it safely working on the net. To achieve a similar situation with Windows took more than twice this time - 76 minutes!! And then all the software has to be found and loaded - again taking at least twice the time for Hardy. I guess I am becoming a convert!
At least I have learned a great deal - particularly about xp where I thought my knowledge was reasonable. Not regarding networks obviously.
All I can say is a big "thanks" to all of you who posted and helped keep the frustration down.

---

### Post by Victormd on 2008-05-27
Very nice!!!

Glad it's working... Just a note... I was checking my SAMBA installation... and it's not even installed!!! I have samba-common, smbclient, and smbfs, and that's it... :)

---

### Post by stinger30au on 2008-05-27
awesome work, glad you got it fixxed in the end

---

### Post by naggis on 2008-05-27
As you say Victormd, I only installed smbfs and that did all that was necessary - including sharing the printer attached to the xp desktop.
In retrospect, I am annoyed that Windows firewall should still be active on the network when it had been  disabled and checked many times. This was the main cause of the problems.

---

