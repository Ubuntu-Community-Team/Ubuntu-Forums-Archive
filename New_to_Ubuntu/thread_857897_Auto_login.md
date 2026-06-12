---
title: "Auto login?"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by BluePlum on 2008-07-13
Hello ,I hope someone can help me with my problem. It isn't to easy so beginners to Ubuntu save your time and don't read this.

**[SIZE="4"]The story so far[/SIZE]**: I have a certain download cap which is 12gb. Which i can only download 1 to 3 Game demos a month before i hit dial up. So i have to stay up to midnight ( When my off cap starts ) start the download Wake up and stop it before the Off cap ends. This is frustrating and tiering.

So i had an idea! I downloaded Deluge and set it to download my torrents In my off cap and no other time. This was all good but the bad part was my laptop was constantly on Decreasing it's life span and Eating up the power bill. So i changed my BIOS to automatically start my laptop at 11.59 PM. And it did start at 11.59 PM. Only to be Foiled by the login screen. Is there a way to make it auto login at that certain time? I would like to keep the password security on but if i can't i won't. I have also forgot how to start a program on startup ( deluge ).

**[SIZE="4"]If we can do the above then how do [/SIZE]****[SIZE="4"]I[/SIZE]**: Shutdown my computer automatically. 

Thank you VERY much in advance.

---

### Post by Jim! on 2008-07-13
> **BluePlum said:**
> Hello ,I hope someone can help me with my problem. It isn't to easy so beginners to Ubuntu save your time and don't read this.

**[SIZE="4"]The story so far[/SIZE]**: I have a certain download cap which is 12gb. Which i can only download 1 to 3 Game demos a month before i hit dial up. So i have to stay up to midnight ( When my off cap starts ) start the download Wake up and stop it before the Off cap ends. This is frustrating and tiering.

So i had an idea! I downloaded Deluge and set it to download my torrents In my off cap and no other time. This was all good but the bad part was my laptop was constantly on Decreasing it's life span and Eating up the power bill. So i changed my BIOS to automatically start my laptop at 11.59 PM. And it did start at 11.59 PM. Only to be Foiled by the login screen. Is there a way to make it auto login at that certain time? I would like to keep the password security on but if i can't i won't. I have also forgot how to start a program on startup ( deluge ).

**[SIZE="4"]If we can do the above then how do [/SIZE]****[SIZE="4"]I[/SIZE]**: Shutdown my computer automatically. 

Thank you VERY much in advance.

Another Australian, Sorry I don't know how to solve your problem - But can you tell me what ISP you use because I'm also on a 12GB Cap (Bigpond) but I don't have off-peak:( Australia really is a third world Country when it comes to Internet:(

---

### Post by aktiwers on 2008-07-13
System = Preferences = Sessions
and add:
```
deluge-torrent
```

To make it start on startup.

Also look into cron to make it shutdown at a specific time. 

I guess you already no about the "autologin" feature in System = Administration = Login Window
under the "security" tab. But that would off cause be at all times = no solution.

---

### Post by BluePlum on 2008-07-13
im on Optus ADSL ( connection speeds up to 8mbs )  which is like $63 a month with 12gb Downloads and Off-peak 
But i've recently found a way better plan. Its ADSL 2. ( connection speeds up to 24 MB'S )  30gb A month + 20 Gb Off-peak for $59.99. Which is way better then my current plane in every way and seems to be $3 cheaper. Also has a static IP for hosting servers. www,tpg.com.au . That's the best ISP plan for me in my price range. If it is for you to, Check it out im switching soon!

---

### Post by Tim Sharitt on 2008-07-13
From the main menu or menu bar:
System --> Administration and select Login Window. Select the Security tab on the login preferences window. Check "Enable Automatic Login" at the top of the screen and select a user from the list. I hope that helps.
I guess I type too slow :)

---

### Post by fenian on 2008-07-13
Go to the menu System>Administration>Login Window
Click the security tab 
check the box next to enable automatic login

---

### Post by BluePlum on 2008-07-13
Ok guys it now auto logs in and everything is going good! But Every problem solved leads to another, Now when i log in it says " user/***/nm-aplet is trying to access the keyring "

Thats the notification bar on the panel which connects to the net. And it cant automatically download when it doesn't connect to the net automatically anymore. When we solve this, How to auto shutdown?

---

### Post by doorknob60 on 2008-07-13
I've never gotten gnome network manager and auto login working at the same time... You could either use Knetworkmanager or Wicd. Or I think you could go into the gnome keyring settings and set a blank password (it works in KDE with Kwallet, don't know about gnome).

---

### Post by Jim! on 2008-07-13
> **BluePlum said:**
> im on Optus ADSL ( connection speeds up to 8mbs )  which is like $63 a month with 12gb Downloads and Off-peak 
But i've recently found a way better plan. Its ADSL 2. ( connection speeds up to 24 MB'S )  30gb A month + 20 Gb Off-peak for $59.99. Which is way better then my current plane in every way and seems to be $3 cheaper. Also has a static IP for hosting servers. www,tpg.com.au . That's the best ISP plan for me in my price range. If it is for you to, Check it out im switching soon!

Hey cool! A similar plan is available in my area (36GB) at $59.95. Thats way better then my current plan ($60 12GB No Off peak). Looks like I'll be changing. Thanks!:)

---

### Post by BluePlum on 2008-07-13
> **Jim! said:**
> Hey cool! A similar plan is available in my area (36GB) at $59.95. Thats way better then my current plan ($60 12GB No Off peak). Looks like I'll be changing. Thanks!:)

what company?

---

### Post by Canis familiaris on 2008-07-13
> **Jim! said:**
> Another Australian, Sorry I don't know how to solve your problem - But can you tell me what ISP you use because I'm also on a 12GB Cap (Bigpond) but I don't have off-peak:( Australia really is a third world Country when it comes to Internet:(

At least your situation is better than the situation in India.

---

### Post by BluePlum on 2008-07-13
> **Anurag_panda said:**
> At least your situation is better than the situation in India.

theres a simple solution for your problem, Move to australia! lol.

Back on topic. I was looking around keyring and took out the password but it just asked for a password next time :P. Any other idears? I need to solve this problem before[COLOR="Red"] MIDNIGHT[/COLOR]! ( plays spooky horror music )

---

### Post by aktiwers on 2008-07-13
I did something else the other day that fixed that thing.. now I cant find it.
Anyways it did screw something up, like networkmanager completely disconnecting from the internet when the PC went to sleep. However, I just found this guide for you (which is not the same thing I did), maybe it will work for you?
[http://ubuntuforums.org/showthread.php?t=187874](http://ubuntuforums.org/showthread.php?t=187874)

---

### Post by Canis familiaris on 2008-07-13
> **BluePlum said:**
> theres a simple solution for your problem, Move to australia! lol.

Even a better solution is to move to Finland/Denmark/Sweden. hundreds of Mbps to 2Gbps :faint: :lolflag:

---

### Post by lisati on 2008-07-13
> **BluePlum said:**
> im on Optus ADSL ( connection speeds up to 8mbs )  which is like $63 a month with 12gb Downloads and Off-peak 
But i've recently found a way better plan. Its ADSL 2. ( connection speeds up to 24 MB'S )  30gb A month + 20 Gb Off-peak for $59.99. Which is way better then my current plane in every way and seems to be $3 cheaper. Also has a static IP for hosting servers. www,tpg.com.au . That's the best ISP plan for me in my price range. If it is for you to, Check it out im switching soon!
Aaargh! I'm on $NZ50 with a 6Gb cap, and snails-pace connection by comparison......

Should I start swimming across the ditch? If so, how best do I waterproof my gear?

---

### Post by aktiwers on 2008-07-13
I have unlimited 100mbit/s in Denmark - and it is included in my rent. :P

---

### Post by BluePlum on 2008-07-13
> **lisati said:**
> Aaargh! I'm on $NZ50 with a 6Gb cap, and snails-pace connection by comparison......

Should I start swimming across the ditch? If so, how best do I waterproof my gear?

Don't worry bout swimming, Just dangle some tuna in the water and wait for a dolphin to come. When it does Jump on it and grab it's fin and steer to the big land mass! Then enjoy your slightly faster INTERNET!

---

### Post by billynomates on 2008-07-13
A friend of mine wrote [this]("http://sat2000.sourceforge.net/") program. Maybe it could help you.
Also, There are a unch of online torrent clients, which download and seed your file for you, so that you can turn your computer off while it downloads. Then once it's done you just go to the site and download the file. Photobucket has one.

---

### Post by billynomates on 2008-07-13
Oh and by the way, I have my computer set to auto-login, but I have *gnome-screensaver-command -l* in my sessions so that whoever turns my computer on still has to enter a password, but the desktop loads in the background.

---

### Post by BluePlum on 2008-07-13
I read the whole 16 page thread and only the last post helped :P.

[http://ubuntuforums.org/showpost.php?p=5177343&postcount=195](http://ubuntuforums.org/showpost.php?p=5177343&postcount=195)

Solved that new issue. Now How to make it shutdown Automatically?

Thankyou

---

### Post by lisati on 2008-07-13
> **BluePlum said:**
> Don't worry bout swimming, Just dangle some tuna in the water and wait for a dolphin to come. When it does Jump on it and grab it's fin and steer to the big land mass! Then enjoy your slightly faster INTERNET!
:)

---

### Post by BluePlum on 2008-07-13
> **lisati said:**
> :)

Well should take you bout 20 hours to get here, When you do give me a ring!

---

### Post by BluePlum on 2008-07-13
So how exactly do i auto shutdown?

---

### Post by todlangweilig on 2008-07-13
I'm not sure I can help you; unfortunately I have no experience with Deluge. Let me make sure I understand the situation. The computer will start up automatically, log itself in, run deluge, exit deluge and shutdown? 

1. Does deluge exit when the torrents are finished downloading? 
2. If not, is there a way for the computer to know that the torrent is done?
3. Or do you want the computer to shutdown after some amount of time, when it is likely the torrent(s) have finished downloaded?

I think 1 and 3 would have an easy solution using cron, 2 would require a more complex solution. 

I'm curious as to the solution that will be found, since I have wanted to do something similar for my server. (automatically turn off when a task is completed)

---

### Post by BluePlum on 2008-07-13
> **todlangweilig said:**
> I'm not sure I can help you; unfortunately I have no experience with Deluge. Let me make sure I understand the situation. The computer will start up automatically, log itself in, run deluge, exit deluge and shutdown? 

1. Does deluge exit when the torrents are finished downloading? 
2. If not, is there a way for the computer to know that the torrent is done?
3. Or do you want the computer to shutdown after some amount of time, when it is likely the torrent(s) have finished downloaded?

I think 1 and 3 would have an easy solution using cron, 2 would require a more complex solution. 

I'm curious as to the solution that will be found, since I have wanted to do something similar for my server. (automatically turn off when a task is completed)

1. I i don't think deluge exits when torrent is done but it can remove torrents when done, may theres an add on to do it.

2. Nop the only way for you to shutdown the torrent when it's done is to look at the ETA in deluge and set it at the ETA, But that would require you to set all the time and torrents speed up, Slow down and cut out all the time.

3. i just want my computer to shutdown at a certain time Everyday.

```
assasin@Invisible-Assasin:~$ cron
cron: can't open or create /var/run/crond.pid: Permission denied

```

---

### Post by todlangweilig on 2008-07-14
It took me a little while to figure out, but I think I have it finally.

These explain how to set up a cron task
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
[http://ubuntuforums.org/showthread.php?t=102626](http://ubuntuforums.org/showthread.php?t=102626)

For this example, I'm going to have the computer shutdown at 3am everyday. Read the links I listed to change the time to the value you would like. 

Run the following command in the terminal
```
sudo crontab -e
```

edit the file to look like this:
```

PATH=/usr/sbin:/usr/bin:/sbin:/bin
# m h  dom mon dow   command
00 03 * * * shutdown -P now

```

The path line is there so the shutdown command can be found by the root user, it doesn't seem to work without it. The -P argument for shutdown tells the computer to power off. The now argument specifies when the computer will turn off after shutdown has been run. 

You might want to set it to a time other than now to give yourself a chance to cancel the shutdown if you happen to be using the computer at the time. Read the man shutdown page for information on how to cancel a shutdown.

---

