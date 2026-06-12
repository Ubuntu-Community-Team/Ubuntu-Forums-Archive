---
title: "Dropbox system-tray silencer"
date: 2009-11-10
forum: Outdated Tutorials &amp; Tips
---

### Post by QwUo173Hy on 2009-11-10
**[SIZE="1"][COLOR="Red"]Important! : If you're a linux newbie[/COLOR], or unsure about the methods I'm using, then wait until someone replies with a post saying that it all worked for them. I've tested all this out on Ubuntu 9.10 (Karmic Koala) running Dropbox version 0.6.571. This tutorial assumes you have dropbox already installed from [https://www.dropbox.com/install](https://www.dropbox.com/install)[/SIZE]**

I use dropbox to keep synced with my colleagues on projects we are working on. But I really don't like having the icon in the system-tray all the time. At the moment, there is no option to hide it - so I've written a script that starts dropbox and performs any syncing that needs to be done. Then it exits leaving your system-tray nice and tidy again!

I have this happen automatically at login, because I boot my machine regularly enough. But you can also have it happen more regularaly using cron. Below, I will describe how to install the script and set it to run at login as well as optional intervals using cron.

**_Installation_**
Just download the script attached at the end of this post and place it wherever you like. First of all, we need to make it executable:

```
chmod +x check-dropbox.sh
```
I like to keep the file 'hidden' in my home folder so I saved it there and renamed it with this command:
```
  mv check-dropbox.sh .check-dropbox.sh

```
The dot in front of the name makes it hidden. So now the file is called .check-dropbox.sh


[B][U]Making it run at login
[/U][/B] Go to System -> Preferences -> Startup Applications.
 Click the Add button.
 Type in any name for this, and click Browse...
 In the new dialog that appears, click the right mouse button and select 'Show Hidden Files' so that you can find the file if you used the Installation method I described earlier.
 Then just click Add and also Close in the main window.


**_Making it run every fifteen minutes_** 
 Open a new terminal and backup the file /etc/crontab before we continue. We will be editing this file.

```
 cp /etc/crontab ~

```
 Next we want to add a single line to the correct location in this file to make our script run regularly. In the terminal type:

```
 sudo gedit /etc/crontab

```
 The file will look very like this in Ubuntu Karmic:
```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#
```

We want to add this line, replacing the two instances of <username> with your username:
```
*/15 * * * * <username> /home/<username>/.check-dropbox.sh

```
Copy that line above and paste it just under where it says: "# m h dom mon dow user	command". On my computer that portion of the file looks like this:     (our new part is highlighted in red)

```
# m h dom mon dow user	command
[COLOR="Red"]*/15 * * * * jarlath /home/jarlath/.check-dropbox.sh
[/COLOR]17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#
```
Save and close. Enjoy!

**_Credits_**

Thanks to diesch for helping me with a coding problem I had.
The commands I use in this script can be found in the following:
Dropbox man page - type 'man dropbox' in a terminal (for the 'dropbox status' command)
[Newbies intro to cron]("http://unixgeeks.org/security/newbie/unix/cron-1.html") -  (for information on editing the crontab file to automate script or command execution)
And [Advanced Bash Scripting guide]("http://tldp.org/LDP/abs/html/") - (for all the rest! script programming in general is covered here.)

---

### Post by raktarok on 2009-11-24
thank you very much for this tip, I was looking for something like this.

---

### Post by QwUo173Hy on 2009-11-25
You're very welcome raktarok.

---

### Post by liangzzzzzzz on 2009-11-26
thank you very much,it's helpful to me.

---

### Post by lpfan076 on 2009-12-05
Thanks mate. This is well needed on a netbook.

---

### Post by QwUo173Hy on 2009-12-05
liangzzzzzzz, lpfan076 - you're very welcome. I'm glad you find it useful.

---

### Post by slughappy1 on 2009-12-20
Just heard about this and must say thanks! I don't like having a lot of icons up there, especially when dropbox's icon stays the same size no matter the size of the gnome-panel with no way to hide it.

---

### Post by chontler on 2010-02-02
thanks for this great script and for giving a noob like me a heads up about the cron :D

---

### Post by QwUo173Hy on 2010-02-09
Thank you for the feedback. I've discovered a bug with the behavior of the script. Today the script exited without updating my files - so I need to investigate.

In the mean-time, anyone using this script should run dropbox normally:
```
dropbox start
```
until I fix it.

---

### Post by QwUo173Hy on 2010-02-23
The problem seems to have been with dropbox - the native application was also misbehaving and now both are fine. The problem manifests when your bandwith is blocked up - for example, someone on the network filesharing heavily.

---

### Post by Zyonin on 2010-03-22
A wee bit late but thanks for this little script.   I so hate that icon in my system tray but I love having my files synced with Dropbox.

---

### Post by QwUo173Hy on 2010-04-10
Thanks Zyonin, and it's never too late to leave good news in someones inbox :)

---

### Post by techunit on 2010-05-02
While this is just me thinking this over but wouldn't it just be easier to create a special icon pack for it or something. I don't like it but it seems that really all you would need to do is replace the Taskbar icons with wire frame icons. I understand that there would be the problem with the icon animation but it was just a thought.

---

### Post by QwUo173Hy on 2010-05-02
> **techunit said:**
> While this is just me thinking this over but wouldn't it just be easier to create a special icon pack for it or something. I don't like it but it seems that really all you would need to do is replace the Taskbar icons with wire frame icons. I understand that there would be the problem with the icon animation but it was just a thought. Unfortunately, the icon is hard-coded into the binaries and cannot be modified. It is not stored in the gtk-client. I'm sure that they do this to maintain their brand identity. The dropbox forums are littered with requests for an option to disable or change the icon but they go unanswered - unlike most other posts in the forums there.

I am using Ubuntu One at the moment though, and it seems to be working better than ever. If it maintains it's stability over the next few months, I might consider using it for personal use (my colleagues use other operating systems so dropbox is a must for now).

---

### Post by muadibmt on 2010-05-03
Hi! thanks for this script :)

---

### Post by QwUo173Hy on 2010-05-04
> **muadibmt said:**
> Hi! thanks for this script :)
You're welcome muadibmt :)

---

### Post by __elvis__ on 2010-05-08
I'm using Lubuntu 10.04. How could I change the script to run this:
```
~/.dropbox-dist/dropboxd
```

Maybe only replace "dropbox" with "~/.dropbox-dist/dropboxd" in your's file?

P.S. Sorry for my English

---

### Post by QwUo173Hy on 2010-05-08
Hi Elvis,
I would leave the script alone, and make a dropbox 'link' where the script expects it. Linkink to whatever you want. For example.
```
sudo ln -s /usr/bin/dropbox ~/.dropbox-dist/dropboxd 
```This creates a dropbox file in /usr/bin, where my script expects it - but it's really a pointer to your dropboxd. Then you can install my script as described.

I have no idea if that would work for you or why you would want to do it though.

---

### Post by QwUo173Hy on 2010-05-08
It seems we have been saved :)
[http://www.omgubuntu.co.uk/2010/05/dropbox-adds-indicator-applet.html](http://www.omgubuntu.co.uk/2010/05/dropbox-adds-indicator-applet.html)

---

### Post by __elvis__ on 2010-05-08
This is the reason for me:
```
How to install Dropbox in Lubuntu

Open up a terminal session and type the following lines separately, hitting return after each.

cd
wget -O dropbox.tar.gz http://www.dropbox.com/download\?plat=lnx.x86
tar -zxof dropbox.tar.gz
wget -nd http://dl.dropbox.com/u/6995/dbmakefakelib.py
wget -nd http://dl.dropbox.com/u/6995/dbreadconfig.py
python dbmakefakelib.py
Let DropBox complete its' initial sync and then, in future, start Dropbox using the following command (either via the terminal or by making a launcher for it)
~/.dropbox-dist/dropboxd
```

SOURCE: [http://www.omgubuntu.co.uk/2010/04/how-to-install-dropbox-in-lubuntu.html](http://www.omgubuntu.co.uk/2010/04/how-to-install-dropbox-in-lubuntu.html)

---

### Post by QwUo173Hy on 2010-05-08
Ah, okay. Well, hopefully my idea above should do the business for you.

---

### Post by Gaba_p on 2011-02-20
Hi jarlath,

thank you very much for sharing this fine script. In my case I use it for a very different reason than the one that made you write it. I use Dropbox to sync my Google Chrome folder. When I'm using Chrome some files are changing all the time (like 'cookies', 'History', etc..) and so Dropbox is constantly uploading. This takes its toll not only on my bandwidth but on my CPU also. Since Dropbox has no option to schedule how often it runs (I don't really get why), I use your script to have it run every x hours.
What I would REALLY like is to be able to actually **see** the Dropbox icon pop-up every time it runs. This way I can see what's happening (since Dropbox has no 'offline' log option, I don't really get why...) and I can be sure that it is actually doing what it's supposed to do.
Since you wrote this script specifically NOT to see the Dropbox icon on the system tray, I realize that what I'm asking may be odd, but to me the script has MUCH more value filling a very big lack of feature in Dropbox: schedule.

I've even modified your script to write a simple log to a file that looks like this:

Mon Feb 21 00:40:03 ART 2011
Connecting...
Waiting on Idle status
Idle again.. exiting.
Mon Feb 21 00:41:44 ART 2011

but this doesn't show what Dropbox is actually doing, so I would still like to see the icon pop-up. Is there any way to achieve this?

Anyway, thanks a lot for taking the time to write the script and sharing it with the rest of us.

Cheers,
Gabriel

---

### Post by QwUo173Hy on 2011-02-21
Hi Gabriel. Thanks for your feedback.

Well, the truth is that I didn't design the script to completely hide the icon - only to keep Dropboxes presence to a minimum while still doing it's job.

I haven't written any code since this script and my ability to modify isn't what it used to be :)

But I do remember that when I was putting it together, increasing the time before the 'dropbox stop' command was issued meant that the icon appeared for longer. There might even be a clever way to use the return values of the dropbox execution to send a message to the notifications.

I hope thats some help.

Best,
Jarlath

---

### Post by Gaba_p on 2011-02-21
Hi,

well after investigating a little I found that Cron jobs are always run in the background, that's why I can't see the Dropbox icon pop-up. I'll keep on trying but in the meantime I followed your advice and modified your script to create a simple log to be extra sure that Dropbox is running and working ok. Here's an example of the log's output:

[I]Mon Feb 21 18:00:03 ART 2011
Connecting...
Starting...
Waiting on Idle status
Uploading 4 files...
Indexing 236 files...
Indexing 17 files...
Uploading 11 files...
Indexing 2 files...
Uploading 10 files...
Uploading 10 files...
Uploading 4 files (139.7 KB/sec, 7 min left)
Uploading 4 files (123.0 KB/sec, 7 min left)
Uploading 4 files (96.4 KB/sec, 7 min left)
Uploading 4 files (74.0 KB/sec, 9 min left)
Uploading 4 files (67.8 KB/sec, 10 min left)
Uploading 4 files (57.1 KB/sec, 11 min left)
Uploading 4 files (47.8 KB/sec, 13 min left)
Uploading 3 files (76.1 KB/sec, 11 min left)
Uploading 3 files (181.6 KB/sec, 4 min left)
Uploading 3 files (110.7 KB/sec, 6 min left)
Uploading 2 files (110.7 KB/sec, 5 min left)
Uploading 2 files (110.7 KB/sec, 4 min left)
Uploading 2 files (675.4 KB/sec, 35 sec left)
Uploading 2 files (675.4 KB/sec, 24 sec left)
Uploading 1 file (675.4 KB/sec, 18 sec left)
Uploading 1 file (675.4 KB/sec, 6 sec left)
Uploading 1 file (675.4 KB/sec, 6 sec left)
.dropbox:       up to date
.dropbox.cache: unwatched
FOLDER1:        up to date
google-chrome:  up to date
Photos:         up to date
Public:         up to date
Idle again.. exiting.
Mon Feb 21 18:01:59 ART 2011[/I]

(the amount of lines displayed can be edited)

I attach the script in case somebody may want it. You just have to change '/home/gabriel/Dropbox' to your Dropbox folder location and '/home/gabriel//dropbox-crontab.log' to the location (and name) you want the log file stored to.

Sadly Dropbox doesn't provide a way to store a more detailed log of it's actions (one is forced to log in  to see your account's 'Events')

Cheers,
Gabriel

---

