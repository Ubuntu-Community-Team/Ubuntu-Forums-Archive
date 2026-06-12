---
title: "backent server issues"
date: 2013-08-24
forum: New to Ubuntu
---

### Post by jim_collins2 on 2013-08-24
Installed mythbuntu.  Setup the backend and restarted.  Now I get this error: Could not connect to the master backend server.  Is it running?  Is the IP address set for it in mythtv-setup correct?  I am running the front end and back end on the same machine, I didn't change the default IP address in the backend setup.  I followed the installation manual exactly and finally got this far.  Any suggestions?

---

### Post by steeldriver on 2013-08-24
Are you running off an SSD? I've seen problems where the backend launches so fast it fails due to network services not being ready - see [http://code.mythtv.org/trac/ticket/11160](http://code.mythtv.org/trac/ticket/11160) for example. Not sure what the recommended fix is though.

---

### Post by jim_collins2 on 2013-08-24
In a terminal I typed the following that I found on another thread - NOW what is my problem???

jccubs@jccubs-A15G:~$ sudo mythbackend
2013-08-24 12:23:47.546582 C  mythbackend version: fixes/0.25 [v0.25.2-15-g46cab93] [www.mythtv.org](www.mythtv.org)
2013-08-24 12:23:47.546654 C  Qt version: compile: 4.8.1, runtime: 4.8.1
2013-08-24 12:23:47.546663 N  Enabled verbose msgs:  general
2013-08-24 12:23:47.546735 N  Setting Log Level to LOG_INFO
2013-08-24 12:23:47.546873 I  Added logging to the console
2013-08-24 12:23:47.546889 I  Added database logging to table logging
2013-08-24 12:23:47.547121 N  Setting up SIGHUP handler
2013-08-24 12:23:47.547425 N  Using runtime prefix = /usr
2013-08-24 12:23:47.547666 N  Using configuration directory = /home/jccubs/.mythtv
2013-08-24 12:23:47.548121 I  Assumed character encoding: en_US.UTF-8
2013-08-24 12:23:47.564171 N  Empty LocalHostName.
2013-08-24 12:23:47.564221 I  Using localhost value of jccubs-A15G
2013-08-24 12:23:47.646811 N  Setting QT default locale to EN_US
2013-08-24 12:23:47.646975 I  Current locale EN_US
2013-08-24 12:23:47.647098 N  Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2013-08-24 12:23:47.693448 I  Current MythTV Schema Version (DBSchemaVer): 1299
2013-08-24 12:23:47.694566 I  Loading en_us translation for module mythfrontend
2013-08-24 12:23:47.696660 N  MythBackend: Starting up as the master server.
2013-08-24 12:23:47.771075 E  TVRec(1): Problem finding starting channel, setting to default of '3'.
2013-08-24 12:23:47.878615 E  InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2013-08-24 12:23:47.881223 E  ChannelBase: CreateChannel() Error: Failed to open device 192.168.2.2-0
2013-08-24 12:23:47.881295 E  Problem with capture cardsCard 1failed init
2013-08-24 12:23:47.886046 E  TVRec(2): Problem finding starting channel, setting to default of '3'.
2013-08-24 12:23:47.904589 E  InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2013-08-24 12:23:47.904931 E  ChannelBase: CreateChannel() Error: Failed to open device 192.168.2.2-0
2013-08-24 12:23:47.904996 E  Problem with capture cardsCard 2failed init
2013-08-24 12:23:47.908933 E  TVRec(3): Problem finding starting channel, setting to default of '3'.
2013-08-24 12:23:47.927617 E  InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2013-08-24 12:23:47.927969 E  ChannelBase: CreateChannel() Error: Failed to open device 192.168.2.2-1
2013-08-24 12:23:47.928037 E  Problem with capture cardsCard 3failed init
2013-08-24 12:23:47.931013 E  TVRec(4): Problem finding starting channel, setting to default of '3'.
2013-08-24 12:23:47.949401 E  InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2013-08-24 12:23:47.949958 E  ChannelBase: CreateChannel() Error: Failed to open device 192.168.2.2-1
2013-08-24 12:23:47.950010 E  Problem with capture cardsCard 4failed init
2013-08-24 12:23:47.950038 W  MythBackend: No valid capture cards are defined in the database.
2013-08-24 12:23:47.981579 W  Scheduler: Listings source 'Antenna' is defined, but is not attached to a card input.
2013-08-24 12:23:47.981608 E  Scheduler: No channel sources defined in the database
jccubs@jccubs-A15G:~$

---

### Post by steeldriver on 2013-08-25
What were you hoping that command would do? If you just want to start/stop the backend, then afaik the correct way to do that is via the myth-backend upstart job (note the hyphen!)

To see the current backend status

```
service mythtv-backend status
```

To stop a current instance

```
sudo service mythtv-backend stop
```

To start an instance

```
sudo service mythtv-backend start
```

You can see if it's actually running either using the 'ps' command, or by looking at the open ports using netstat

```
sudo netstat -nltp | grep myth
```

My guess is that all the errors you're seeing when stating mythbackend independently just indicate that you haven't finished configuring the backend?

---

### Post by jim_collins2 on 2013-08-26
I thought I had completed the configuration of the backend.  Obviously I have not.  What exactly is still not set up (if you can get that from the information I posted)?

---

### Post by steeldriver on 2013-08-26
Well is anything actually broken? can you record / watch stuff?

The error messages *may* just be because you tried to start the backend in a nonstandard way (perhaps it was already running so the new instance couldn't access the resources?) - I would suggest firing up the GUI mythbackend setup program (on my system it is in the Applications menu --> System --> MythTV backend setup) and having a quick run through all the menus

---

### Post by jim_collins2 on 2013-08-26
I tried to just watch tv and got a tuner error.  When I get home tonight I will document the exact error as I know troubleshooting is a pain with limited information (like, can you fix my car - it makes a funny noise).  I have HD Homerun set to my two tuners and am getting over the air signal.  I know the signal is good as I can watch the tv directly without myth.

---

### Post by jim_collins2 on 2013-08-27
Ok, went through each step in the backend setup and believe that everything is correct.  When I exit the backend setup it asks if I want to start backend and I click yes and enter my password.  Then it asks if I want to run mythfill database.  I click yes and it runs.  Then when I click to start the frontend I get the same message as the original post. "[COLOR=#000000]Could not connect to the master backend server. Is it running? Is the IP address set for it in mythtv-setup correct?"  I am willing to try anything, but I am a newbie to Linux so please spell it all out for me!! Thanks in advance for the help.[/COLOR]

---

### Post by steeldriver on 2013-08-27
Let's start by seeing what's running

```

ps -ef | grep myth

sudo netstat -nlpt4 | grep myth

```

---

### Post by jim_collins2 on 2013-08-27
jccubs    1776  1747  0 Aug26 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/share/mythbuntu/session.sh
jccubs    1779     1  0 Aug26 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session /usr/share/mythbuntu/session.sh
jccubs   26048 25982  0 07:09 pts/0    00:00:00 grep --color=auto myth
jccubs@jccubs-A15G:~$ 

Then when I typed the second line it just went back to the prompt - nothing appeared, actually it asked for my password, then nothing appeared.

---

### Post by steeldriver on 2013-08-27
OK let's try

```
sudo service mythtv-backend start
```

and then have a look at the log

```
tail /var/log/mythtv/mythbackend.log
```

---

### Post by jim_collins2 on 2013-08-27
jccubs@jccubs-A15G:~$ sudo service mythtv-backend start
mythtv-backend start/running, process 26133
jccubs@jccubs-A15G:~$ tail /var/log/mythtv/mythbackend.log
Aug 27 07:24:57 jccubs-A15G mythbackend[26156]: E CoreContext channelbase.cpp:940 (InitializeInputs) InitializeInputs(): #012#011#011#011Could not get inputs for the capturecard.#012#011#011#011Perhaps you have forgotten to bind video#012#011#011#011sources to your card's inputs?
Aug 27 07:24:57 jccubs-A15G mythbackend[26156]: E CoreContext channelbase.cpp:1229 (CreateChannel) ChannelBase: CreateChannel() Error: Failed to open device 10167AD4-1
Aug 27 07:24:57 jccubs-A15G mythbackend[26156]: E CoreContext main_helpers.cpp:196 (setupTVs) Problem with capture cardsCard 3failed init
Aug 27 07:24:57 jccubs-A15G mythbackend[26156]: E CoreContext tv_rec.cpp:1715 (GetStartChannel) TVRec(4): Problem finding starting channel, setting to default of '3'.
Aug 27 07:24:57 jccubs-A15G mythbackend[26156]: E CoreContext channelbase.cpp:940 (InitializeInputs) InitializeInputs(): #012#011#011#011Could not get inputs for the capturecard.#012#011#011#011Perhaps you have forgotten to bind video#012#011#011#011sources to your card's inputs?
Aug 27 07:24:57 jccubs-A15G mythbackend[26156]: E CoreContext channelbase.cpp:1229 (CreateChannel) ChannelBase: CreateChannel() Error: Failed to open device 10167AD4-1
Aug 27 07:24:57 jccubs-A15G mythbackend[26156]: E CoreContext main_helpers.cpp:196 (setupTVs) Problem with capture cardsCard 4failed init
Aug 27 07:24:57 jccubs-A15G mythbackend[26156]: W CoreContext main_helpers.cpp:211 (setupTVs) MythBackend: No valid capture cards are defined in the database.
Aug 27 07:24:57 jccubs-A15G mythbackend[26156]: W CoreContext scheduler.cpp:207 (VerifyCards) Scheduler: Listings source '' is defined, but is not attached to a card input.
Aug 27 07:24:57 jccubs-A15G mythbackend[26156]: E CoreContext scheduler.cpp:218 (VerifyCards) Scheduler: No channel sources defined in the database
jccubs@jccubs-A15G:~$ jccubs@jccubs-A15G:~$ sudo service mythtv-backend start
jccubs@jccubs-A15G:~$: command not found
jccubs@jccubs-A15G:~$ mythtv-backend start/running, process 26133
mythtv-backend: command not found
jccubs@jccubs-A15G:~$ jccubs@jccubs-A15G:~$

---

### Post by jim_collins2 on 2013-08-27
I just tried to go to the video portion of the backend setup.  I get to the part where I enter my schedules direct name and password.  It downloads the info, I clicked the perform EIN scan (not sure if it is EIN). and then click finish, but it does not appear that the video part saved.

---

### Post by jim_collins2 on 2013-08-27
tried to watch tv through the frontend again.  got the same error message, then it said all tuners are busy if that helps any.

---

### Post by jim_collins2 on 2013-08-27
Sorry - I have to go to work now.  I will try any suggestions tonight. Thanks again.

---

### Post by jim_collins2 on 2013-08-27
After looking at other posts it must have something to do with my HD HomeRun and getting my channels set up.  I followed every online guide I could find.  I entered my schedules direct information and it grabbed the information (I could see the progress bar as it downloaded).  What tests can I run to check for the problem?  Anybody live near chicago that wants to do this for me for some $$$.  I'm desperate and the wife is not happy about this!

---

### Post by steeldriver on 2013-08-27
Have you run the HDHomeRun config GUI? can you detect both tuners and view channels that way?

I don't really know what else to suggest - short of diving into your mythconverg database

---

### Post by jim_collins2 on 2013-08-27
I ran it from the applications menu.  I can have it scan and it detects the channels, but don't see a way to "save" the channels.  It looks like I can only close the program.  There is a rescan button, but tried that also.  So the HD HomeRun sees the channels, but it isn't telling the backend what they are??

---

### Post by steeldriver on 2013-08-27
Well as far as I know the mythbuntu backend doesn't actively scan for devices like the HDHR - on my setup, I have assigned a reserved LAN IP for it which I then type into the backend setup.

If your HDHR is getting a variable DHCP-assigned address, then your backend setup will lose sight of it if the IP changes.

Do you remember the details of how you set it up?

---

### Post by jim_collins2 on 2013-08-27
I don't think I understand your question.  I used the defaults for 99% of everything on the setup.  I chose the HD HomeRun video and since it has 2 tuners built in it assigned them -0 and -1.  I took notes of everything I did, but I'm still at work.  What specifically do you want to know?

---

### Post by jim_collins2 on 2013-08-27
OK, in HDHomeRun Config I can Scan and then view the channels.  It uses VLC Media player on a window that I can close.  So, obviously the HDHomerun can access the channels.  I guess the question is how do I get mythbuntu to recognize the channels from HD HomeRun?

---

### Post by jim_collins2 on 2013-08-27
OK, I at least have something new.  I got to the point where I can scan for channels through myth.  running mythfilldatabase now.  Will update very soon.  I went through the Video source again and made sure I names the source antenna this time.  Then wenth through the input connections and told HD HomeRun to look for antenna - THAT WAS THE PROBLEM - IT WAS NOT LOOKING FOR ANTENNA (THE NAME I GAVE IT).  Huge weight off my shoulders!!!  Thank you all for helping me - as it turns out it was me - not the program (I'm sure that is the case 99% of the time).  It would be helpful in the installation guide to instruct the user to name the source so they can direct the tuners to it later.  Thanks again!!!

---

### Post by steeldriver on 2013-08-27
OK sounds like you're making good progress - fwiw I found the backend setup process very non-intuitive, I think I blew it away and re-started 3 or 4 times before I got it working right

---

### Post by jim_collins2 on 2013-08-27
One more thing.  I have my old drive in the computer now.  I found the location of the recordings.  I would like to transfer them to the new drive.  The old recordings are in /mnt/sdb6/mythtv/recordings.  I cannot locate the four recordings that I have recorded since I got the system back up and running.  I cannot find a location for recordings to move the old ones into.  I have he following folders on the drive:
bin
boot
cdrom
dev
etc
home
lib
lib64
lost+found
media
mnt
opt
proc
root
run
sbin
selinux
srv
sys
tmp
usr
var
and the following files:
initrd.img
initrd.img.old
vmlinuz
vmniluz.ols
I have looked for another directory labeled recordings so I can move them, but I cannot locate it!!!

---

### Post by steeldriver on 2013-08-27
The default location is /var/lib/mythtv/recordings HOWEVER just moving the files there WILL NOT make them available for watching via the front end, since everything goes via the database - there are some perl scripts to rebuild the DB and pull in the relocated files, I think

---

### Post by jim_collins2 on 2013-08-27
that sucks - I don't even know what perl scripts means!!!

---

