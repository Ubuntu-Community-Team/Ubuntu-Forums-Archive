---
title: "after 24 years with MS, its time to move on?"
date: 2012-11-17
forum: New to Ubuntu
---

### Post by DeathByDigital on 2012-11-17
Hello.

Ive been trying a few distros during last 4-5 years, on different computers.
(all have worked just well out of the box, for most of my needs, exept high end games)

Now i have a idea of setting up linux all around the house, including a server for my media.
And here i really are going to need alot of help......

Lets start with what i have.

The server is an older [Intel Core 2 Duo E6600 2.4GHz ]("https://www.komplett.no/k/ki.aspx?sku=322633") but it should do just fine for server use. 
ive got a IDE 250gig system disk, a 500Gb media HD (ntfs atm.. so im not certain how to move data from NTFS disk) to the last HD on server, who is a 1TB disc, that is unused atm. Guessing i can install ubuntu, get ntfs file support, format 1tb disc, move data to that one and reformat 500 gig HD.

The two other computers in the network (one in bedroom and one in livingroom)
Are both              [Gigabyte GA-990FXA-UD3, Socket-AM3 ]("https://www.komplett.no/k/ki.aspx?sku=637650")
The livingroom computer is a FX4100 prosessor, 8gb of 1600mhz ram, and Nvidia GF560TI 
(this is the one i am using for music and movies) so im hoping my hw is working decent with any distro. (thinking of XBMC)

I also have a few laptops and a good old Galaxy P1000 Tab, and both my gf and i have Galaxy SII phones......

Now.. thats what i have...  what i want is to be able to have a easy way to set up my server, and get a decent media setup for my livingroom.
Pref i want to be able to controll my media from my adroid based phones/tab.
(this worked pretty decent in windows.)

At least i will be dual booting my bedroom computer to be able to play BF3 once in a while...... (reading something about steam+linux..som there might be hope one day)

Now here is the hard part.....
Ive used Microsoft since the days you did write your own autoexec.bat files, and have no clue about linux. yes ive tried a few distros, but they all worked just out of the box.
(have to google to figure how to open console...) so im not familiar with none MS.....
Trouble on moust guides for linux, is that they say... open "somethig" or start "something", but i have no clue what or how to  start... so i really need basic step by step guides for kids..... 

Therefore i need some help for what distro to use on the server, and what to use on my media senter. it might work great with same distro on both... but i dont know...

it would be great if i could reach my media on server from android phones/tab, and if i did boot one computer in windows7.

so what do ppl suggest i install on server and mediapc? what should i do with my media on the NTFS disk? (dont want to loose my history with pictures.... 
All help is needed and appritiated.
sorry abotu syntax error and alot of questions... more will follow.

---

### Post by The Cog on 2012-11-17
> Trouble on moust guides for linux, is that they say... open "somethig" or start "something", but i have no clue what or how to start... Starting programs should be easy in any distro (although I wouldn't know how to start a program in Unity - I hear that they have removed the start menu, so I would have to use a command prompt). 

The difficult part is knowing which programs you need to run to achieve different tasks. There is no easy way round this. You have learned over the years which programs you would use in windows, but they all have different names (and sometimes different capabilities) in Linux. Your best bet is to use these forums when you need to know how to do a new task.

You should try the live CDs of the different distros to get an idea which one feels most comfortable.

AS for your pictures, Linux can read NTFS, but by the sound of it, you don't have a backup. Make one now. Today. Before the hard disk fails. I lost all mine once because I didn't keep backups, and the disk gave no warning that it was going to fail.

---

### Post by Beardedturtle on 2012-11-17
SSD Solid State Drive  or SSD is awesome I will only use these as my main drive due to high reliability and they are getting cheaper each year. Also if they reach there end of life they will go to read only so you can get all your important data off of them.

---

### Post by Gone fishing on 2012-11-17
Sorry I've never done a home server but servers I've used FreeBSD, Opensuse, Ubuntu, Debian and CentOS. They all work I would suggest using the one your most comfortable with, as your probably setting up from the commandline if you use ssh then you can set from any other box useand  Google as needed even Windows if you must.

Of the distro's above I'd probably go for Ubuntu, FreeBSD or CentOS here,s a link that might be useful [http://www.server-world.info/en/note?os=Ubuntu_12.04&p=download](http://www.server-world.info/en/note?os=Ubuntu_12.04&p=download) there centOS howto were good and here's a link to the Linux action show [http://www.jupiterbroadcasting.com/26306/perfect-linux-server-las-s24e02/](http://www.jupiterbroadcasting.com/26306/perfect-linux-server-las-s24e02/)

---

### Post by DeathByDigital on 2012-11-17
thank you for replies....

just a thought, but setting up server in command promt... is ..hmm...scary...
I might just use regular ubuntu on server, and share from there...
I kinda feel safer with point and click as far as that is possible....

---

### Post by LuigiAntoniol on 2012-11-17
> **Gone fishing said:**
> Sorry I've never done a home server but servers I've used FreeBSD, Opensuse, Ubuntu, Debian and CentOS. They all work I would suggest using the one your most comfortable with, as your probably setting up from the commandline if you use ssh then you can set from any other box useand  Google as needed even Windows if you must.


Hi, DeathByDigital

Personally, I'd agree that Debian is probably your best OS for a server.  
It has many high end admin tools that will suite the tasks you need done.

As for your desktops, I'd go for Lubuntu (LXDE) or Xubuntu (XFCE) as they're very lightweight GUI's with minimum graphics that won't slow your computers down.

But don't let that fool you, they carry all the same codecs and media players you'd need to look at pictures and play movies.

I'm not a fan of KDE or Unity as, in my opinion, they hog too many resources.

As suggested by others, do a bit more research and find what you feel most comfortable with.

Good luck!!

---

### Post by DeathByDigital on 2012-11-17
ive tried the smaller distros on a asus eee pc once, and they worked fine.
(as long as i didnt touch anything :) hehe )

But i think my systems should be able to run most distros? 

best feel i got from kubuntu, but well... changing parameters/resolution did kill my fun with that...

Ubuntu is what ive spent most time with, and its working great out of the box...
So i probably should stick to that...

downloading 64bit as i write....

---

### Post by Lars Noodén on 2012-11-17
+1 for Debian on the server

If you're used to Ubuntu, then it's a smaller adjustment to get used to Debian.

As far as graphical environments go, you might go even lighter weight and run just a window manager instead of a full desktop environment.  You can run FVWM, Openbox or Enlightenment without needing to also add in a heavy desktop environment.  Also with a light WM, it reminds you that you are on the server.  However, the shell is so flexible and powerful, the sooner you find your way around with it, the better. But it's ok to get used to it gradually.

---

### Post by coldraven on 2012-11-17
As I don't have a TV I have never had a use for a media sever but is XBMC or Mythbuntu what you are after?
[http://en.wikipedia.org/wiki/XBMC](http://en.wikipedia.org/wiki/XBMC)
[http://en.wikipedia.org/wiki/Mythbuntu](http://en.wikipedia.org/wiki/Mythbuntu)

---

### Post by QIII on 2012-11-17
> **DeathByDigital said:**
> just a thought, but setting up server in command promt... is ..hmm...scary...

New things often are.  But once you get used to them, they aren't "new" any more and you often wonder how you ever made do without them.

---

### Post by DeathByDigital on 2012-11-17
well.. now ive got Ubuntu 12.10 on this server and the media PC...
Thought id try to fiddle around a bit, see if i can get these connected over the network... and start small and easy.

First bugger.... ive got a disk attatched... 1tb disk, formatted in fat32ex file...

how do i format this?

the system is reading my 500gig media disk in NTFS (by defalut)
But thought id backup to the other disk also..so if one fails.. i have a spare one.
So how do i format the fat32ex disk?

Other tips for EASY network is appritiated.

---

### Post by audiomick on 2012-11-17
Whilst all the above advice is good, I think you would do well to settle on one Distribution for a start. There is an Ubuntu Server version. I don't know exactly how it is different from standard Ubuntu, but I know you can install a Desktop Environment onto it without a problem. This might be an option for you until you learn what you need.

On the other hand, just using the machine as a media server doesn't warrant, I think, a "hard core" server install. From your descriptions, I assume that the usual work it will be doing is having maybe 2 or 3 computers pulling films or music off it. That should not be too much of a bother for a standard Ubuntu install, I imagine. If there is anything missing there that the server edition would have had, it can be installed from the software center. In short, I'm inclined to suggest a standard Ubuntu on all of the machines, and take it from there. You chances of getting the entire set-up exactly right and never wanting to do anything different are pretty minimal, so don't bother your head about doing things wrong too much. Just go at it, and see how it developes. )

As far as your data goes, you are on the right track. If you install Ubuntu on the machine, you will be able to copy your data across to the new drive without a bother. Incidentally, the advice from an earlier poster about doing a backup immediately is good. Having valuable stuff on only one drive is always risky. I don't have a good backup habit, but I do keep stuff I can't replace spread around on several drives and machines. Anyway, Ubuntu can read ntfs. You don't need to install anything extra.

Now that I think about it, I would be inclined to boot the machine into the live environment and work from there. You could use gparted from there to partition the new 1TB drive as you want it, and copy your files across once you have that done. While you are at it, you might like to get a hold of an external drive and make a copy of them to there too, just for safe keeping. Once all that is done, you can install, format the ntfs drive during the install, and mount the 1TB to the install during the install. 

As far as the difficulties with the various guides go, I know exactly what you mean, It is hard to give general advice, but you can nearly always get help hear. Post a question with an approriate title, a link to the guide you are trying to follow, and what it is you don't understand. A lot of the time someone will even chime in with an easier way... ;)

---

### Post by nothingspecial on 2012-11-17
Open up the software centre and install gparted. You can format the disc with that.

Easy networking. Press Ctrl-Alt-T to open a terminal.

```
sudo apt-get install openssh-server
``` on both machines. 

Then on machine A

```
ssh-keygen
ssh-copy-id user@host
```

user@host would be the user name of your account on the other machine @ it's ipaddress

eg bob@192.168.0.2

accept the connection

Type the password from your account on the other machine

Then open your file browser and in the menu go File > Connect to server

Choose ssh, fill in the boxes (no password needed because you just did that bit)

You can now add the other machine as a bookmark in the file browser.

Go to machine B and do the same thing.

---

### Post by DeathByDigital on 2012-11-17
heh..did search from dashboard and "disks" did randomly appear... 
And that did the desired job, so the fat32ex is now formatted to ntfs, and up and running.
Copying pictures now....

Ive got a question:
On the computer set for livingroom, the Plasma starts to "flicker". 
It turns black for a half sec, then normal a sec or 3.... 
anyone know what this is?
I tried to install Nvidia drivers for it, but ended up loosing my desctop.
(just had the background, but no icons or anything)
if i right click, i get the desktop adjustment. so i ended up with reinstalling  : P

But anyone know what is the easiest way to fix this problem? Dunno if it is the Nvidia GF560TI causing it, but think i had similar problem with a earlier install with another computer.
(might be my old hitachi plasma....)

Thank you for all replies btw.

---

### Post by holiday on 2012-11-17
You are not using Linux unless you learn the command line. All this GUI fluff? Might as well be Windows or Apple. 

Well no. I don't know why, but Ubuntu graphics are better than Windows graphics on the same machine. Even using a VM. 

But yes. As others have suggested, learn the command line. It is often much faster than clicking through some 'wizard' that often restricts your choices more tightly than the command line. GUI developers don't have the time to cover all of the options so they give you what they think are going to be the most popular. 

Get into the command line!

---

### Post by Paqman on 2012-11-17
> **DeathByDigital said:**
> 
Trouble on moust guides for linux, is that they say... open "somethig" or start "something", but i have no clue what or how to  start... so i really need basic step by step guides for kids..... 

On Ubuntu you can launch apps or open files the same way you'd search for them. Click on the Ubuntu icon on the launcher, or hit the Windows key. The you can either start typing the name of what you want, or navigate through the icons.

> Therefore i need some help for what distro to use on the server, and what to use on my media senter. it might work great with same distro on both... but i dont know...

Ubuntu has a server version, and is well documented. If it's just serving up some files though any Linux distro will work fine. 

For the media centre I would recommend XBMC. There's a release of it called XBMCbuntu that is the XBMC media centre software prepackaged with the underlying Ubuntu OS, which makes setup pretty straightforward.

> it would be great if i could reach my media on server from android phones/tab, and if i did boot one computer in windows7.

No probs. If the server runs SAMBA then you can serve your files up in the Windows networking protocol (SMB/CIFS), which is understood by a wide variety of stuff. There are plenty of SMB browsers for Android

---

### Post by DeathByDigital on 2012-11-17
im so new to this, that im still unshure if commandline is the same as terminal?
its like driving a car... its easy if you know how, but if you never have seen one before, its hard to know what the shifter, or break pedal is.......even the easiest basics have to be learned......

and for me... i have copied alot of lines into terminal..but still dont understand what...
im starting to thinking i know what a few words are... but still i dont think i can manage to intuitive set up a sambashare from command line yet :)


still- anyone know what the flicker on my tv is?
IS it my tv, graphics card, or sw that makes the picture go black.. its just off  for 0,25 secs. every 10 sec. still annoying

---

### Post by stinkeye on 2012-11-17
> **The Cog said:**
> Starting programs should be easy in any distro (although I wouldn't know how to start a program in Unity - I hear that they have removed the start menu, so I would have to use a command prompt). 

The difficult part is knowing which programs you need to run to achieve different tasks. There is no easy way round this. You have learned over the years which programs you would use in windows, but they all have different names (and sometimes different capabilities) in Linux. Your best bet is to use these forums when you need to know how to do a new task.

You should try the live CDs of the different distros to get an idea which one feels most comfortable.

AS for your pictures, Linux can read NTFS, but by the sound of it, you don't have a backup. Make one now. Today. Before the hard disk fails. I lost all mine once because I didn't keep backups, and the disk gave no warning that it was going to fail.

...and there's the beauty of unity dash.
You don't have to know the actual name of the application.
You can type in something related to the task you want to perform.
I find it strange that someone on the ubuntu forums staff hasn't even looked at unity out of curiosity.
:confused:

---

### Post by Paqman on 2012-11-17
> **DeathByDigital said:**
> im so new to this, that im still unshure if commandline is the same as terminal?


A terminal is something that can display the command line. The terminology goes back to mainframe days, these days the actual terminal is software instead of an actual box with a monitor and keyboard.

However the distinction is unimportant, essentially they're the same thing.

---

### Post by Calinou on 2012-11-17
> Ubuntu forums
> Asks people whether they should move on
...seems legit. :)

[quote=DeathByDigital]At least i will be dual booting my bedroom computer to be able to play BF3 once in a while...... (reading something about steam+linux..som there might be hope one day)[/quote]

Don't play DRM'd/commercial/proprietary games (BF3 isn't even natively available for Linux anyway, and while we're at it BF3 sucks).

---

### Post by audiomick on 2012-11-17
> **DeathByDigital said:**
> im so new to this, that im still unshure if commandline is the same as terminal?
its like driving a car... its easy if you know how, but if you never have seen one before, its hard to know what the shifter, or break pedal is.......even the easiest basics have to be learned....
Yes. It is a good thing to learn how to use the command line to do things in the terminal. You want to get your setup happening, though. If that works quicker for you using a GUI, then do it that way. You will know doubt pick up a grounding in command line stuff as time goes by. I use a mixture of terminal commands and GUI. To each his own.


> 
still- anyone know what the flicker on my tv is?
IS it my tv, graphics card, or sw that makes the picture go black.. its just off  for 0,25 secs. every 10 sec. still annoying

Why don't you try running the TV off another computer for an hour or so. That will soon tell you if it is the computer or the TV that is causing trouble.

---

### Post by DeathByDigital on 2012-11-17
my 42" plasma works great on windows...
I did try to install xorg, but either i just get a empty desktop background, with no icons- then i have no flicker... :P
have to ctr+alt+del to get to logoff screen...and i can rightclick to get into change desktop, and get further to system.. but still no icons on desktop... 
I do see the "startbutton" in the logON meny, but logging on, just returns me to the blank desktop. ><

Im downloading the 32bit version to see if that helps...

---

### Post by DeathByDigital on 2012-11-17
:( still flicker.... GRRR

---

### Post by Gone fishing on 2012-11-17
You can build a server with a GUI for example the first server I built was Opensuse with Gnome GUI and Yast (Opensuse's config tool) was very helpful It was a damn good server lasted some years and was hardly ever rebooted (P4 with 2 Gig RAM). You could build a server based on CentOS for example and install gnome. However, whatever server you are going to use the command-line and edit text files - with a GUI you could use an editor like gedit but nano in the command-line is not to scary.

If you put a GUI on your server you will need more power as some of it your wasting running the GUI - but if this your first go why not. I would suggest Webmin [http://www.webmin.com/](http://www.webmin.com/) a web based graphical config tool for Linux and Unix servers (very good in my opinion). I would also consider RAID 1 where the data is written to 2 drives simultaneously drives are quite cheap and a software raid easy to set-up.

---

