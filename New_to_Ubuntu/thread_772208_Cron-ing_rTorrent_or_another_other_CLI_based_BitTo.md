---
title: "Cron-ing rTorrent or another other CLI based BitTorrent"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by HornedBeast on 2008-04-28
[SIZE="3"][CENTER]***Note: The below has now been solved. Please check [this link]("http://ubuntuforums.org/showpost.php?p=4823787&postcount=11") for the guide to getting it all to work nicely.***[/CENTER][/SIZE]

Hi.

I have an 8mb Down and 1mb Up ADSL line and it doesn't get used between the hours of 4am and 4pm - I would like to get the most out of it! So, I have a stand-alone server configured with "podget" to download a host of video and audio podcasts automatically and place them inside folders and setup a transcode cluster for my home DVD's - all set to begin and end at 4am and 4pm respectively. I even have TwonkyMedia setup to stream all my media to Xbox 360s and Other Media devices around the house automatically. Its also all shared via Samba to Windows and Linux machines on the network.

However, I would like to get "rtorrent" doing the same thing. It has functions like watching a folder for new torrents and automatically begin them when they are found - all of which I have setup and got running absolutely fine - but it runs all the time and I have to be sitting at the server to stop it and start it at night (I dont wish to be using the connection too much outside of the specified hours because I have house mates that use it for gaming and the likes). 

Because it actually runs a front-end inside a GUI, it takes keyboard commands to stop and start. I have had a little run around, but found there to be no luck and no guide for doing this. I hear this kind of thing can be resolved using "screen" but I have no-idea what that is or how to use it?

Can someone point me in the right direction to get this working (only how to stop and start rtorrent using "crontab -e") - be-it inside "screen" or by any other method, or, is there a different BitTorrent client that has its own scheduler that can be set to do the same things?

Any help would be much apreciated.

Hit me back with a reply or email me [EMAIL="andrew.barlow@gmail.com"]here[/EMAIL].

Thank-you in advanced!

Horned!

---

### Post by hyper_ch on 2008-04-28
nil would result in no limit... so don't set it to "0" but to "1"... that should not hurt performance at all (1kb out of 1024 upload)

Another option would be to start/end rtorrent at given times with cron.

---

### Post by HornedBeast on 2008-04-28
Thank-you for your swift reply. This nearly does what i'm after - but after a little test I discovered the it still communicates with the tracker even with the bandwidth set to 0 - thus using bandwidth during the times I'm hoping to not use any.

If all else fails I'll have to go with this.

Anyone else got any ideas of how to perform the OP?

---

### Post by HornedBeast on 2008-04-28
You can't cron rtorrent in the usual way. 

I don't think rtorrent even worked when I added an entry in my crontab.

It also cannot be started via "rtorrent start" and "rtorrent stop" as it isn't a service. Problem being is that its got a front end for a console and requires keyboard commands to stop it.

The scheduler is pretty useless in rtorrent, I'd rather not use it. Cron seems to be the best way - I heard "screen" might help me... but I couldn't figure out how to use it.

Any others?

---

### Post by hyper_ch on 2008-04-28
there is an example script on how you would auto-start rtorrent in a screen.... however you can start rtorrent also in the background by issuing

```

rtorrent &

```
That should also be working.

Here's a quick guide for screen: [http://jmcpherson.org/screen.html](http://jmcpherson.org/screen.html)

---

### Post by HornedBeast on 2008-04-28
How do I stop it via cron after that though?

---

### Post by hyper_ch on 2008-04-28
why do you want to stop it at all? *g* You will have to kill the process...

---

### Post by Archmage on 2008-04-28
> **HornedBeast said:**
> How do I stop it via cron after that though?

Call me stupid, but should be a kill -15 or -9 do the trick?

---

### Post by HornedBeast on 2008-04-28
Rtorrent wont even start via cron. /usr/bin/rtorrent does absolutely nothing - it certainly doesn't begin my transfers and creating a log file shows NOTHING.

I've tried it a dozen times (I've used Cron for a long time). Its not as simple as everyone keeps suggesting - but I do appreciate your help.

I think I may have found the answer though using Screen.

```
00 4 * * * screen -d -m rtorrent
00 16 * * * screen -r -X quit
```

Going to dry run this tonight and see what happens.

Cheers again for your help.

---

### Post by HornedBeast on 2008-04-28
I have finally got it working absolutely fine.

For anyone else that might need it, see this below.

Install RTorrent via:

```
sudo apt-get install rtorrent
```

Copy and paste this into /home/<username>/.rtorrent.rc replacing <username> with your current username or the user you wish to download torrents with:

```

directory = /home/<username>/Torrents/Unfinished
session = /home/<username>/.rtorrentsession
schedule = watch_directory,10,10,load_start=/home/<username>/Torrents/Torrents/*.torrent
schedule = tied_directory,10,10,start_tied=
schedule = untied_directory,10,10,close_untied=
on_finished = rm_torrent,"execute=rm,$d.get_tied_to_file="
on_finished = move_complete,"execute=mv,-u,$d.get_base_path=,/home/<username>/Torrents/Finished/ ;d.set_directory=/home/<username>/Torrents/Finished/"
schedule = low_diskspace,5,60,close_low_diskspace=1000M
schedule = ratio,60,60,"stop_on_ratio=100"
check_hash = yes
encryption=allow_incoming,try_outgoing,enable_retry
```


This assumes you have the folders:

/home/<username>/Torrents/Torrents
/home/<username>/Torrents/Finished
/home/<username>/Torrents/Unfinished
/home/<username>/.rtorrentsession

If you do not have these folders, make them now using "mkdir" or simply make them using a GUI.

What this configuration does is check the folder "/home/<username>/Torrents/Torrents" for new .torrent files and starts them automatically and stops them if they are removed. Once the torrent has finished it is automatically moved to the Finished folder. If the torrent is still active it is found inside Unfinished. It is also set to use Encryption if it can, as this will hopefully navigate some of those nasty ISP who shape their bittorrent traffic.

You can now run this from a terminal by running simply "rtorrent". However, to make this only start at certain times, in my case 4am until 4pm, you need to do this:

Install "Screen" if you havn't got it already. Desktop Ubuntu does by default but Server users may need to install it:

```
sudo apt-get install screen
```

Now you need to edit your crontab. You can do this by typing this at a terminal:

```
crontab -e
```

Copy and paste this into it:

```
# m h  dom mon dow   command
00 **04** * * * screen -d -m rtorrent
00 **16** * * * screen -r -X quit
```

The bits in bold are the hours in the 24 hour clock. The bits before that are the minutes. Simply change these to the times that suit your needs.

What this does is start rtorrent in a "detached" screen session. Then, at 4pm, it makes screen quit any detached session. Thus giving you the desired effect.

I hope this helps someone as i've been stubling around for weeks now.

Horned.

---

### Post by defunkt on 2008-05-09
this actually answered my question on rtorrent...

im also looking to do something else similar.

im running moblock, and i would like to routinely use the moblock-nfq-control update command, though it needs root access.  does the cron run commands as root?

---

### Post by hyper_ch on 2008-05-09
the config file above is rather incomplete... it lacks a session (and watchfolder)...

---

### Post by jre on 2008-05-09
> **defunkt said:**
> this actually answered my question on rtorrent...

im also looking to do something else similar.

im running moblock, and i would like to routinely use the moblock-nfq-control update command, though it needs root access.  does the cron run commands as root?
Normally cronjobs run as root, yes. Although you can also make user cron jobs.
If you've installed the moblock debian package you will already have the daily "moblock-control update" in /etc/cron.daily/moblock

---

### Post by fwre01 on 2008-05-09
> **hyper_ch said:**
> the config file above is rather incomplete... it lacks a session (and watchfolder)...

are these not the commands for a watch and session directory??...the ones in the config above?

```
session = /home/<username>/.rtorrentsession
schedule = watch_directory,10,10,load_start=/home/<username>/Torrents/Torrents/*.torrent
```

---

### Post by hyper_ch on 2008-05-10
*sorry*

somehow I skipped them

---

### Post by HornedBeast on 2008-05-12
To set root cronjobs:

```
sudo crontab -e
```

And for user level cronjobs:

```
crontab -e
```

---

### Post by fwre01 on 2008-05-24
Is anybody getting the cron part of this to work?? i am using the commands in the example "screen -d -m rtorrent" in my crontab file and it doesnt start rtorrent!

if i tail the syslog i can see the command being executed, but if i "ps -ef | grep rtorrent" i see nothing!

BUT! if i run the command "screen -d -m rtorrent" it starts the dettached screen running rtorrent!! if i then "ps -ef | grep rtorrent" i can see rtorrent running! ARGH!!!

...anybody got any ideas, im at the end of my rope!! lol

---

### Post by defunkt on 2008-05-26
actually there is a script i found on the web page.  download this...

[http://libtorrent.rakshasa.no/attachment/wiki/RTorrentCommonTasks/rtorrentInit.sh](http://libtorrent.rakshasa.no/attachment/wiki/RTorrentCommonTasks/rtorrentInit.sh)

this is a script that you can put in your update-rc.d that will make this run at startup...  this fixed my issue...

if your looking to run this at different times of the day, gluck...  i run mine 24-7 and just limit it.  (could try using DHT too)

---

### Post by fwre01 on 2008-05-29
Thanks defunkt, i did take a look through that, but i persevered with rtorrent and finally got it working, it was a missing absolute path in my cron script 

**embarrassed look on my face**

...lesson of the day, make sure to use absolute paths when using cron!!

---

### Post by HornedBeast on 2008-05-30
Am I ok to say "I told you so!?"

---

### Post by fwre01 on 2008-05-30
haha....maybe?

---

### Post by HornedBeast on 2008-05-30
Lolz.

Just as a little note to all, I'm working on a script for Transmissioncli for watch folders, etc etc. I found Transmissioncli to be much faster than rTorrent in most cases.

Ill keep this thread updated.

---

### Post by sampe on 2009-01-17
Hello,

Interesting discussion here, however if you have more than one screeen which you would like to keep running I would instead ue the following in my crontab:

# m h  dom mon dow   command
00 04 * * * screen -d -m rtorrent
00 16 * * * pkill -U <user_id_running_the_cron> rtorrent

This way other screens with bitchx or irssi would keep running...

/S

---

### Post by larytet on 2013-03-13
I am using named sessions for rtorrent - this approach kills only screen session which runs rtorrent

```

0  5   *   *   *     /usr/bin/screen -r rtorrent -X quit
50 23  *   *   *     /usr/bin/screen -S rtorrent -d -m /usr/bin/rtorrent

```

---

### Post by ras123 on 2013-05-26
> **HornedBeast said:**
> 
```
# m h  dom mon dow   command
00 **04** * * * screen -d -m rtorrent
00 **16** * * * screen -r -X quit
```


Hi,
Is it possible to detach and attach with a session name in the above code?
Thanking You,
Ras

---

### Post by oldos2er on 2013-05-26
Please start a new thread, this one's really old.

---

