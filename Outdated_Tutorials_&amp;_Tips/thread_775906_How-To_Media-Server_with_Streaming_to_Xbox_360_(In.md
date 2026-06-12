---
title: "How-To: Media-Server with Streaming to Xbox 360 (Includes Torrents and Podcasts)"
date: 2008-04-30
forum: Outdated Tutorials &amp; Tips
---

### Post by HornedBeast on 2008-04-30
**Synopsis: **

Guide to setting up a media server which streams to most media capable hardware (including PS3 and Xbox 360) with automatic Podcast downloading and scheduled BitTorrenting. This creates a perfect setup where you can get to all your media via any computer on your network, start torrents from any computer on the network and use all your untapped bandwidth during the night!


**Equipment List:**

[LIST]
[*]Computer with at least:
[*]500mhz CPU
[*]256mb of RAM
[*]CD-Rom Drive
[*]Harddrive with at least 2gb free. (More storage the better for media and downloads)
[*]Network card (Wireless will do, cables are better)
[*]PC-Monitor and Keyboard  (For installing server, everything else can be done remotely)
[*]One Ubuntu Server 8.04 32bit Edition CD.
[*]An internet connection (For downloading podcasts and BitTorrent)
[/LIST]

**Pre-face:**

I do not take any responsibility for any damages to hardware made by this guide! All software used is open-source and free with the exception of TwonkyMedia server. This is a proprietary piece of Linux software which I could not find such a feature rich, open-source alternative. TwonkyMedia can be installed as a free 30 day trial, which at the end of you, can purchase via their website for only $30. Its worth it! All code in this guide has been fully tested to be working with Ubuntu server 8.04 32bit LTS (Aka. Hardy Heron). 

This may not be the best way to do any of this, but its the way I know works! If you have any suggestions of changes, please let me know by PM'ing me or reply to this post. If you do not have a second computer at home and wish to do all this on the server as a client machine, or perform this guide on a desktop installation (Untested), just ignore all the parts about logging in via SSH, and just login locally and follow the exact same steps.

***This guide only works with the 32bit version of Ubuntu Server 8.04 because there are no versions of TwonkyMedia in 64bit. The rest of the guide will in 64bit work absolutely fine except steps 7 and 8. So, if you do not need media streaming, are using the 64bit version of Ubuntu Server and only wish for the automated downloads part of this guide, read on!***


[B]Step One:
_Installing Ubuntu-Server 8.04 from CD._[/B]

*Notes: This is by no means a comprehensive guide to installing Ubuntu-Server 8.04. For full instructions please visit Ubuntu.com*

Ill assume at this point you already know how to download the Ubuntu-Server 8.04 ISO file and have burnt it to a blank CD-R &#8211; or you have used Ubuntu's handy &#8220;Ship-It&#8221; service and have had a disk sent to you. If not, there are plenty of guides on Ubuntu.com about how to do this.

Drop the disk into the drive of the server and see if it boots into the Ubuntu install screen. If it doesn't you may have to change the boot order of your BIOS to make it do so. This varies from motherboard to motherboard so I cannot help too much here.

Once you have booted into the the menu, choose your language of choice and hit &#8220;Install&#8221;.

Follow all of the instructions on the screen. The trickiest part is how to partition your drive. If you are unsure when you get to the partition section, just choose &#8220;Completely remove partitions and use all available space&#8221;.

When the installer asks you for a hostname, type &#8220;media-server&#8221; or a name for your computer on the network. This will appear to any computer viewing this server remotely.

When it asks you for a username, I used &#8220;sysadmin&#8221;. I shall assume you have done the same for this entire guide and as the configuration files included in this guide use this username inside them, I suggest you do the same too. If for any reason you decide not to use &#8220;sysadmin&#8221;, please substitute it inside all of the configuration files where ever you may see it.

Give this username any password you wish!

When you get near the end of the installation it will ask you what packages you wish to install. I only choose the OpenSSHd server option. This will allow you to access the server remotely via SSH once you have setup the network address on the server.

Once all this is complete, remove the CD, flip it over and put it back in your CD-Drive for safe keeping (or put it somewhere safe) and reboot the server. If it starts up ok, then onto step two! If not, you may wish to check out &#8220;Ubuntu.Com&#8221; for a full fledged guide on installing the Server Edition.


[B]Step Two:
_Updating Software and Setting Up The Network Address On The Server_[/B]

Before you remove the monitor and keyboard from the server, your going to want to update all the packages on the server and give it a static IP address. Firstly login by typing your username (&#8220;sysadmin&#8221; if you following this guide exactly) and type your chosen password. Once logged in, run the following commands and type your password when you get asked for it.

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ntp
```

This will automatically update all your packages with the latest version of all the software currently installed on the system. The final comand installs NTP, which keeps your system clock in sync with a remote server. Depending on where you chose your location to be in the server install stage, it will keep your clock accurate. This is useful due to files being accessed over a network where file modification dates might need to be monitored. It is also useful for logging and security.

Once this is finished, its time to setup the network address of this machine. All network card settings are stored inside a simple text file in Linux, which can be edited with your favorite Linux text editor. I use 'nano' as its a little simpler, but you can use 'vim' if you prefer.

```
sudo nano /etc/network/interfaces
```

This will open up 'nano' with your current network settings. Look to the bottom and change the settings to the following.

```
# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.2
gateway 192.168.1.2
netmask 255.255.255.0
```

Change the address and gateway settings to suite your current network settings. The ones I provided worked with my network happily as I knew my router was 192.168.1.1, and that the IP address 192.168.1.2 was available for my server to use. You may have to check what IPs are available on your network. Once this has been done and you are using 'nano', you can save the file by press &#8220;Ctrl + O&#8221;. This writes the file (&#8220;out&#8221;) back to the hard drive. Then press &#8220;Crtl + X&#8221; to quit the program.

Once saved, type this command at the terminal to restart the network. 

```
sudo /etc/init.d/networking restart
```

This should bring the network card back up with your new settings. Once this is done your all set to remove all your devices from the server, such as the keyboard and monitor. Hit the reset button and make sure the server boots up with nothing plugged into it. If you hear any beeping you may wish to plug the monitor back in and see whats going on. Otherwise, your ready to crack on!

[B]Step Three:
_Logging In Remotely_[/B]

One of the luscious things about Linux is the ability to administrate everything remotely from any SSH terminal, which thankfully, Linux has built in and Windows has the awesome Putty software. In this guide I will assume you have a Linux variant installed on a client machine somewhere else on the network. If you are running Windows of some variety, then download Putty and perform all the commands using that.

In a Linux terminal, type the following to login remotely to your server:

```
ssh sysadmin@192.168.1.2
```

If you didn't use &#8220;sysadmin&#8221; as your username, change it above. You will then be prompted for the password for your username. Type it and press enter. You will now be logged in and residing in your home folder. On the filesystem, the location will be &#8220;/home/sysadmin/&#8221;. From here, you can do anything you like to your server. Including installing new software and various other tasks &#8211; all of which will be covered in the next few steps.

The default folder you are now in we will only use to download a few installable files and keep our configuration files. All data will be stored in some new folders we shall make in the next steps.


[B]Step Four:
_Create Media and Storage Directories and Share Them Via Samba_[/B]

Now were going to create some folders to put all your music, videos and torrents inside. Then were going to share them via Samba so Windows, Mac and Linux clients can see them on the network.

Firstly, you need to create the directories to put all your new data into. You can change these locations, but I chose the following setup as its clean and tidy.

Login via SSH (or perform this locally), then do the following.

```
cd /
sudo mkdir mediaserver
cd mediaserver
sudo mkdir -m 777 music
sudo mkdir -m 777 video
sudo mkdir -m 777 torrents
cd torrents
sudo mkdir -m 777 Finished
sudo mkdir -m 777 Unfinished
sudo mkdir -m 777 Torrents
sudo mkdir -m 777 Session
```

This will make the following directory tree at the root of your filesystem:

[INDENT]/mediaserver
[INDENT]/music
/video
/torrents[/INDENT]
[INDENT]/Finished
/Unfinished
/Torrents
/Session[/INDENT][/INDENT]

The reason for the &#8220;-m 777&#8221; is so that Samba can read and write to these folders, which is necessary for copying files to these folders over a network. You don't need the original &#8220;/mediaserver&#8221; folder to have this access though, as you wont be sharing that folder explicitly.

Now you have this tree in place, you can install Samba and set it up to share these folders.

```
sudo apt-get install samba smbfs
```

This installs Samba along with any dependencies. To configure these shares we must do the following. First we backup the configuration in case something goes wrong (always good practice) and then we open 'nano' to edit the file.

```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf_backup
sudo nano /etc/samba/smb.conf
```

Find this line:

```
...
;  security = user
...
```

And replace it with:

```
security = share
```

Then scroll to the bottom of the file and append the following:

```
[music]
  comment = Music Folder
  path = /mediaserver/music
  public = yes
  writable = yes
  create mask = 0777
  directory mask = 0777
  force user = nobody
  force group = nogroup

[video]
  comment = Video Folder
  path = /mediaserver/video
  public = yes
  writable = yes
  create mask = 0777
  directory mask = 0777
  force user = nobody
  force group = nogroup

[torrents]
  comment = BitTorrent Folder (Put .torrent files inside the 'Torrents' folder)
  path = /mediaserver/torrents
  public = yes
  writable = yes
  create mask = 0777
  directory mask = 0777
  force user = nobody
  force group = nogroup
```

To make any of the folders &#8220;read-only&#8221; simple change the &#8220;writeable&#8221; variable to &#8220;no&#8221;. This will lock anyone from putting and files inside that folder. Now we need to restart Samba.

```
sudo testparm
sudo /etc/init.d/samba restart
```

This should all go smoothly. If you are at your client machine, go to the network folder and you should find a computer called &#8220;media-server&#8221; (or whatever hostname you gave it) and it should now have the 3 shares available. Feel free to put anything you wish inside the Music and Video folders, but ignore the Torrents share for the time being. Onto setting up automatic Podcast automatic downloading!


[B]Step Five:
_Installing and Configuring Podget for Automatic Podcast Downloading_[/B]

Install Podget via:

```
sudo apt-get install podget
```

This will install Podget with some base settings. However, we're going to change them to suit our new setup!

```
sudo nano /home/sysadmin/.podget/podgetrc
```

Now copy and paste the following into this file, erasing first anything that was there:

```
# Name of Server List configuration file 
config_serverlist=serverlist 

# Directory where to store downloaded files 
dir_library=/mediaserver 

# Directory to store logs in 
dir_log=/home/sysadmin/.podget

# Set logging files 
log_fail=errors 
log_comp=done 

# Wget base options 
wget_baseopts=-c -nH 

# Most Recent 
# 0  == download all new items. 
# 1+ == download only the <count> most recent 
most_recent=0 

# Force 
# 0 == Only download new material. 
# 1 == Force download all items even those you've downloaded before. 
force=0 
 
# Autocleanup. 
# 0 == disabled 
# 1 == delete any old content 
cleanup=0 

# Number of days to keep files.   Cleanup will remove anything 
# older than this. 
cleanup_days=14 

# Filename Cleanup: For FAT32 filename compatability (Feature Request #1378956) 
# Tested with the following characters: !@#$%^&*()_-+=||{[}]:;"'<,>.?/ 
# filename_badchars=!#$^&=+{}[]:;"'<>?|\ 

# Filename Cleanup: For FAT32 filename compatability (Feature Request #1378956) 
# Tested with the following characters: !@#$%^&*()_-+=||{[}]:;"'<,>.?/ 
# filename_badchars=!#$^&=+{}[]:;"'<>?|\ 

# Filename Replace Character: Character to use to replace any/all 
# bad characters found. 
filename_replacechar=_ 

# Filename Cleanup 2:  Some RSS Feeds (like the BBC World News Bulletin) download files with names like filename.mp3?1234567. 
# Enable this mode to fix the format to filename1234567.mp3. 
# 0 == disabled 
# 1 == enabled (default) 
filename_formatfix=1 

# Stop downloading if available space on the partition drops below value (in KB) 
# default:  1843200 (1800MB) 
min_space=1843200 

# ASX Playlists for Windows Media Player 
# 0 == do not create 
# 1 == create 
asx_playlist=0 
```

&#8220;Ctrl + O&#8221; again to write the file and &#8220;Ctrl + X&#8221; to quit 'nano'. You don't really need to know what most of this does. Just make note of the directory at the top. If you changed this directory in the previous step, change it here. You may also want to fiddle with the AutoClean settings and how much space should be left before stopping downloading.

Now lets configure some servers.

```
sudo nano /home/sysadmin/.podget/serverlist
```

This will open up the list of servers to download from. PodGet automatically downloads any RSS or XML feeds with Encapsulated tags. I have included some basic feed URLs in my server list. Copy the following into this file, erasing anything that was once there.

```
# Default Server List for podget 
# FORMAT:    <url> <category> <name> 
# NOTES: 
#    1. The Category must be one word without spaces.  You may use underscores. 
#    2. Any spaces in the urls needs to be converted to %20 
#    3. Disable the downloading of any feed by commenting it out with a #. 
#    4. If you are creating ASX playlists, make sure the feed name does not 
#       have any spaces in it. 
# Find more servers at: http://www.ipodder.org/directory/4/podcasts 
http://feeds.ziffdavis.com/ziffdavis/dltvwmvvideo video DL.TV 
http://feeds.feedburner.com/TrailercastHd720p?format=xml video HD Film Trailers 
http://feeds.feedburner.com/MajorNelsonblogcast music Xbox Live Podcast 
http://www.linuxbasement.com/mp3-full/feed music Linux Basement Podcasts
```

As you can see, this file has a few instructions inside it already. I have also included some feeds for your pleasure and set them up for you. You can include new feeds with Encapsulated media by using this syntax. Take this example below:

```
**http://feeds.feedburner.com/TrailercastHd720p?format=xml [COLOR="RoyalBlue"]video[/COLOR] [COLOR="Red"]HD Film Trailers[/COLOR] **
```

The bit in black is the feed URL itself. Copy this from anywhere you can find podcast addresses. A few good places to look are: 

[Digital Podcast]("http://www.digitalpodcast.com")
[Download Radio]("http://downloadradio.org")
[IndiePodder.org]("http://indiepodder.org")
[Podcast.net]("http://podcast.net")
[Podcast Alley]("http://www.podcastalley.com")
[The Podcast Bunker]("http://www.podcastbunker.com")
[The Podcast Network]("http://www.thepodcastnetwork.com")
[Podcasting News Podcast Directory]("http://www.podcastingnews.com/forum/links.php")

The bit in blue is the folder name to put the content into. If your feed contains video, type &#8220;video&#8221;, if its music, type &#8220;music&#8221;. These names are the folders you created earlier inside /mediaserver. If you called them anything different, make the changes here.

The part in red is the folder name to create to put the content inside from that feed. So, for the example above. Because its a feed containing HD Movie Trailers, ive put it inside the Video directory inside its own folder called HD Film Trailers. Simple as that! Tailor this list to your needs!

Now the fun part! You can make 'Podget' run by simply typing &#8220;Podget&#8221; at the terminal. Its not a bad idea to run it quickly to make sure your servers are working correctly and its all setup properly. However, what you really want is for it to run in the night or at a time you arn't using your connection very much. To do this you want to setup a &#8220;cron job&#8221;. This is done via the following command.

```
crontab -e
```

Paste this inside. This will make 'Podget' run at 3am every day of the week. Change this to your needs. The -s option makes 'Podget' run in silent mode which simply suppresses all the output which you don't really need!

```
# m h  dom mon dow   command 
0 3 * * * /usr/bin/podget -s
```

That's all setup and done! You'll now have podcasts automatically downloading every night at 3am to your shared folders. You can see all the data if you view the shares from any client machine over the network.


[B]Step Six:
_Install Rtorrent and Schedule It For Overnight Downloads_[/B]

'Rtorrent' is a command line based BitTorrent client. Its nice and small and has some neat features, such as folder watching so you can start and stop torrents by simply dropping .torrent files into a folder of your choosing. If you made the directory tree as suggested in step 3, those folders should now become apparent in their usage!

Firstly, install Rtorrent via this command:

```
sudo apt-get install rtorrent
```

Now you need to create a configuration file for 'Rtorrent'. 'Rtorrent' does not make this automatically so I will supply one for you pre-set up for all the previous configuration in this guide.

```
sudo nano /home/sysadmin/.rtorrent.rc
```

Now copy and paste the following into the file:

```
# Default directory to save the downloaded torrents. 
directory = /mediaserver/torrents/Unfinished 

# Default session directory. Make sure you don't run multiple instance 
# of rtorrent using the same session directory. Perhaps using a 
# relative path? 
session = /mediaserver/torrents/Session

# Watch a directory for new torrents, and stop those that have been deleted
schedule = watch_directory,10,10,load_start=/mediaserver/torrents/Torrents/*.torrent 
schedule = tied_directory,10,10,start_tied= 
schedule = untied_directory,10,10,close_untied= 

# Move completed downloads 
on_finished = rm_torrent,"execute=rm,$d.get_tied_to_file=" 
on_finished = move_complete,"execute=mv,-u,$d.get_base_path=,/mediaserver/torrents/Finished/ ;d.set_directory=/mediaserver/torrents/Finished/" 

# Close torrents when diskspace is low. 
schedule = low_diskspace,5,60,close_low_diskspace=1024M 

# Stop torrents when reaching upload ratio in percent.
schedule = ratio,60,60,"stop_on_ratio=100" 

# Check hash for finished torrents.
check_hash = yes 

# Encryption options. This can be useful when using an ISP that uses traffic shaping.
encryption=allow_incoming,try_outgoing,enable_retry
``` 

This will setup 'Rtorrent' so that any .torrent files moved into the &#8220;Torrents&#8221; folder of the &#8220;Torrents&#8221; share will automatically begin downloading. It will automatically stop downloading if your disk space goes below 1gb. It will stop and remove .torrent files once a download is complete and move the file to the Finished folder. It will also use encrypted traffic where possible to stop ISP traffic shaping. 

All currently downloading torrents can be found inside the &#8220;Unfinished&#8221; folder. Generally you want to leave everything alone except the &#8220;Torrents&#8221; folder which should only contain .torrent files and the Finished folder, which you can copy your finished torrents from when they are complete.

Now, to make this only run at certain times you will need to install Screen. I wont go into what this does, but its a useful app for running this sort of program without you being there (as 'Rtorrent' uses a front-end inside a CLI, it inst appropriate to run as a 'cron job' by itself, this is what Screen is for!).

```
sudo apt-get install screen
```

Now to make it run and stop at certain times do the following. Open up cron again.

```
crontab -e
```

And append this underneath the previous 'Podget' entry:

```
# Start rtorrent at 4am every day 
0 4 * * * screen -d -m rtorrent 

# Stop rtorrent at 4pm every day
0 16 * * * screen -r -X quit 
```

As the comments suggest, it will only run 'Rtorrent' at 4am when your connection might be quiet and stop it at 4pm when you may want to use your connection for other things. Simply change the values to whatever you need!


[B]Step Seven:
_Install TwonkyMedia to Stream Media to Various Devices_[/B]

Now lets go ahead and install TwonkyMedia.

TwonkyMedia server is the software that allows you to share various folders containing music, videos and pictures and have them stream to different media enabled devices. Specifically I use it to stream music and video to my Xbox 360 on the network.

To download it, make sure your in the default directory that you started in after logging in via SSH then type the following command.
```

wget http://www.twonkymedia.com/Download/4.4/twonkymedia-i386-glibc-2.2.5.sh
```

This invokes the &#8220;Web Get&#8221; command which downloads the address after the &#8220;wget&#8221; bit. This should only take a second. There may be a new version of the software available at a later date. To check this visit [http://www.twonkymedia.com/Download/TwonkyMedia/index.html](http://www.twonkymedia.com/Download/TwonkyMedia/index.html). Then copy and paste the link for the &#8220;Linux Setup Script&#8221; and &#8220;wget&#8221; that instead.

Now to install the server itself.

```
sudo chmod 777 twonkymedia-i386-glibc-2.2.5.sh
sudo ./twonkymedia-i386-glibc-2.2.5.sh
```

Ignore any errors about not starting properly or permissions denied &#8211; we'll fix this ourselves. This will automatically install the software to '/usr/lib/TwonkyMedia' and attempt to make it start at boot time. However, because TwonkyMedia hasn't been correctly setup to install to Ubuntu or Debian properly we shall have to do some fiddling to fix this.

```
cd /etc/init.d/
sudo chmod 755 twonkyserver
sudo nano twonkyserver
```

Look for this line inside the file:

```
echo -n "Starting $TWONKYSRV ... "
$TWONKYSRV -D -inifile "${INIFILE}"
rc_status -v
```

And replace it with:

```
echo -n "Starting $TWONKYSRV ... "
$TWONKYSRV -D -ip 192.168.1.2 -inifile "${INIFILE}"
rc_status -v
```

Changing the IP according to the setup you did in step two.

Then you need to run the following command.

```
sudo update-rc.d twonkyserver defaults
```

Now you can restart the server via:

```
sudo reboot
```

And once it has restarted you should be able to visit [http://192.168.1.2:9000/](http://192.168.1.2:9000/) and see your new media server running! Onto the next step to configure it!


[B]Step Eight:
_Configure TwonkyMedia Server_[/B]

Now we can finally configure TwonkyMedia to periodically scan your newly made media directories full of automatically downloaded podcasts so you can stream it all to media devices like the Xbox 360 and PS3.

In an internet browser, on a machine on your network, go to: [http://192.168.1.2:9000/config](http://192.168.1.2:9000/config)

Now click on &#8220;First Steps&#8221;.

Rename the media server to anything you want to. This will be the name displayed on your media devices.

Now click on &#8220;Sharing&#8221;.

From here you can setup any shares you like. The top one I set as:

```
/mediaserver/music
```

And set the type to: 

```
&#8220;Audio Only&#8221;
```

And a second one as:
```

/mediaserver/video
```

And set the type to:

```
&#8220;Video Only&#8221;
```

Set the re-scan time to anything you like. I have mine set to 60 which means once an hour. You can set it to anything you wish in minutes. Then hit &#8220;Save&#8221;, wait a moment, then hit &#8220;Restart Server&#8221; at the top.

You can also setup &#8220;Internet Radio&#8221; streams. Just follow the links on the right and enjoy tweaking it to your desire. As I say in my notes at the top of this guide though, this is only a trail version of the software and purchasing it after the 30 day trial is a must if you wish to keep using it.

Every things now setup! Go ahead and test everything just incase, but it should all work smoothly!

Let me know if you have any problems or if you would like more information on any of the software used above.

HornedBeast

*Note: I have also attached a .zip to this post with the guide in a nice PDF format for easy printing and reading. Its difficult setting up a server whilst looking at this forum sometimes, so, printing this guide could be useful to some. Hope it helps!*

---

### Post by bbarrons on 2008-06-13
Thank you so much for this tutorial. I used it a month ago to setup twonky. I had been looking for a way to stream video to our xbox. Other solutions did not work as well as twonky out of the box (with your config)
I have a question about rtorrent. I have been using ktorrent but it is a memory HOG! How is rtorrent in this regard?
thanks again.
 Bill B

---

### Post by HornedBeast on 2008-06-13
Hi!

No worries about the guide! I plan on updating it soon to use TransmissionCLI instead of RTorrent. 

However, I can vouch for RTorrent being awesome. Its really solid and doesn't take up much resource at all! Just wish it had UPnP support really (please devs make it happen!)

You should be fine on Rtorrent!

Hope that helps.

HB

---

### Post by dhughes on 2008-06-15
Thanks HornedBeast for the tutorial.

 I'm about 80% finished, I got stuck at the Twonky install since the wget link in your tutorial wasn't any good so I tried to get around it by downloading the file from the website to my desktop (not my server) but now I can't copy it over to my server since ssh freaks out since it's "not a regular file". I'm researching how to move directories using ssh or whatever it is you need to do it.

 Oh and the host name being media-server (with a hypen) and the directory storing the files called mediaserver (no hypen) was a bit confusing, I can see you were trying to use generic names but they are a bit too similar.

 I'm using my own host name but use your directory naming structure. Although I had to really watch it using your config files and use the path on my server and with mediaserver (the directory) and not media-server. A bit confusing but once I saw what was going on  I was OK...or I'll see when I get Twonky downloaded and set up.

---

### Post by Twiggy794 on 2008-06-16
Thanks for the tutorial, worked great for me.  I'm using Twonky 5 beta 1 now (just for kicks).  Looks like to get my Xbox to stream my H.264's correctly I need to rename all the mp4's to m4v's.  Otherwise, working perfectly!  It's great to have all the load of streaming off of my PC and onto another machine.

---

### Post by HornedBeast on 2008-06-16
Re: dhughes

Yea, I thought of that after I posted the tutorial - it is a little confusing. I'm currently re-writing the tutorial with a few changes and have decided I will change the hostname and other various things.

Re: Twiggy794

No problem at all - Twonky usually gets a fair few updates a year, so its worth checking back. Its also worth purchasing if you use it alot as the open-source alternatives seem a little lacking right now. If I can get the same functionality out of an OSS peice of software I shall update my guide with that!

Cheers for all the useful replies! Keep checking back!

Regards, HB!

---

### Post by nunki on 2008-06-19
Im having problems with the rtorrent setup. I followed the directions, and rtorrent will not move any completed torrent to the specified directory. Nothing is ever removed from the unfinished directory. Ive checked the syntax of the .rc file, and made sure there are no permissions issues.

Has anyone had any issues like this? Any recommendations on what to check?

---

### Post by bbjc on 2008-06-24
hey,
i'm really new to the whole linux thing and i've got a pure noob situation here.  once i input the following:

# Name of Server List configuration file 
config_serverlist=serverlist 

# Directory where to store downloaded files 
dir_library=/mediaserver 

# Directory to store logs in 
dir_log=/home/sysadmin/.podget

# Set logging files 
log_fail=errors 
log_comp=done 

# Wget base options 
wget_baseopts=-c -nH 

# Most Recent 
# 0  == download all new items. 
# 1+ == download only the <count> most recent 
most_recent=0 

# Force 
# 0 == Only download new material. 
# 1 == Force download all items even those you've downloaded before. 
force=0 
 
# Autocleanup. 
# 0 == disabled 
# 1 == delete any old content 
cleanup=0 

# Number of days to keep files.   Cleanup will remove anything 
# older than this. 
cleanup_days=14 

# Filename Cleanup: For FAT32 filename compatability (Feature Request #1378956) 
# Tested with the following characters: !@#$%^&*()_-+=||{[}]:;"'<,>.?/ 
# filename_badchars=!#$^&=+{}[]:;"'<>?|\ 

# Filename Cleanup: For FAT32 filename compatability (Feature Request #1378956) 
# Tested with the following characters: !@#$%^&*()_-+=||{[}]:;"'<,>.?/ 
# filename_badchars=!#$^&=+{}[]:;"'<>?|\ 

# Filename Replace Character: Character to use to replace any/all 
# bad characters found. 
filename_replacechar=_ 

# Filename Cleanup 2:  Some RSS Feeds (like the BBC World News Bulletin) download files with names like filename.mp3?1234567. 
# Enable this mode to fix the format to filename1234567.mp3. 
# 0 == disabled 
# 1 == enabled (default) 
filename_formatfix=1 

# Stop downloading if available space on the partition drops below value (in KB) 
# default:  1843200 (1800MB) 
min_space=1843200 

# ASX Playlists for Windows Media Player 
# 0 == do not create 
# 1 == create 
asx_playlist=0

and try to save it in nano, i get an error message saying that there is no such file or directory.

tips?

---

### Post by arrrghhh on 2008-06-30
have you tried mediatomb?  i haven't tried twonky, so i'll see if it's worth the $30.  but i prefer mediatomb, it's GPL...

---

### Post by trying_least on 2008-07-03
I've got an old pc that is just gathering dust, its a celeron 733, with 515mb of ram. 

Would that be sufficient to stream movies through the 360?

I have speed issues running on p4 2.8 in XP so I'm curious to know if the above will cut it. 


Also is it possible to use an external usb drive for storage of movies on the server?

thanks

---

### Post by HornedBeast on 2008-07-04
@ trying_least:

As the machine will only be transmitting the data it should be fine to stream to the Xbox 360. It is the Xbox 360 that actually does all the video decoding, so you should be ok.

My box isn't much faster and I can watch full 1080p WMV's via my 100mb ethernet.

You should be ok for this setup.

Oh... and yes... you can use an external USB drive. Infact, I mount a 500gb USB drive to /mediaserver instead of creating the folders. Seems to work a treat :).

HB

---

### Post by HornedBeast on 2008-07-04
@ BBJC:

Are you sure you've installed PodGet?

Also, the file may not exist at all on boot... you may have to create it and fill it with that information. If you ran a "sudo nano" then it should just create it when you save it.

Then just continue with the guide.

HB

---

### Post by bossco on 2009-10-07
[SIZE=2]I'm having an issue with this as well. The error is something like can't save filename..


[SIZE=2]This part through a clue to I was in the wrong dir, or I may not of installed the podget. So I did a [/SIZE][/SIZE][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]find / -name 'podget' 2>/dev/null[/SIZE][/FONT][SIZE=2] to see if it was installed, and found it under /usr. 

So on to the clue you suggested that "If you changed this directory in the previous step, change it here". Well following the steps you provided, we should be in the mediaserver dir. I'm just asking if this is the dir that I should be in.??

I also tried the nano to create edit, also tried a vi editor and was still getting the same results. 

maybe I missed something not sure. I do understand that this post is old, so if I don't get a reply thats cool, or if you can help or point me in the right direction as well would be helpful.

thanks
 [/SIZE]

---

### Post by BLOODHOUND11245 on 2009-10-07
Would TVersity work to stream files?

---

### Post by ccphilly1984 on 2010-02-13
so this streams to both at the same time?

---

### Post by johnycage on 2010-02-24
Very comprehensive how-to indeed. I am going to be doing something similar in my home network. I would keep a headless server, will use keyboard, monitor only for intial-setup. Also, in my setup LAMP installed (webmaster testing)

Laptop= windows
headless CPU= Ubuntu Server
[IMG]http://s3.amazonaws.com/twitpic/photos/full/37197503.jpg?AWSAccessKeyId=0ZRYP5X5F6FSMBCCSE82&Expires=1267066294&Signature=oUwDymQk74G5%2FfsZusC5J8kxM8Y%3D[/IMG]
 I really liked your idea of managing torrents remotely & automatically.

---

### Post by Bone Down on 2010-11-21
Alright I am running a headless server at this point I am utilizing:
Torrentflux
transmission cli
sortTV
MiniDLNA

Currently TorrentFlux is running RSSad via (ShowRSS) I am currently downloading all the television shows that I like to watch, sortTV sorts them, renames them, places them in their appropriate folder for viewing later, miniDLNA serves it up to my network for viewing via wifi bluray. The next step is for me to get my favorite video podcasts downloading automatically then sort them to their appropriate folders.

podget is an old bash file in Maverick the file installs to /usr/bin the file has to be copied and saved as .sh then executed once then it will creat the POD/LOG & .podcast directories containing the before mentioned files requiring modification. 

After sorting this out and making the above listed changes I attempt to run the file and I receive a few errors, and being of linux newb status I am not certain what I need to do to navigate past these errors.

```
:~$ podget -l
podget

Session file not found.  Creating.
/usr/bin/podget: line 450: [: too many arguments
/usr/bin/podget: line 481: [: /home/maverick/.podget/serverlist: binary operator expected
/usr/bin/podget: line 457: $current_serverlist: ambiguous redirect
/usr/bin/podget: line 481: [: /home/maverick/.podget/serverlist: binary operator expected
/usr/bin/podget: line 457: $current_serverlist: ambiguous redirect
/usr/bin/podget: line 658: [: too many arguments

Closing session and removing lock file. 
```

Can anyone point me in the right direction, there is not much in regard to help on the internet for podget so I am turning to the Ubuntu forums.. 

Thanks in advance.

---

### Post by Bone Down on 2010-11-23
bump
Anyone have any idea how to or can assist with this?

---

