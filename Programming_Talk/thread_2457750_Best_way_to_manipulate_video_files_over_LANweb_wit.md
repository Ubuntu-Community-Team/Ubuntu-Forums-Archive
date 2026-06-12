---
title: "Best way to manipulate video files over LAN/web with Linux"
date: 2021-02-08
forum: Programming Talk
---

### Post by rainerfeyer on 2021-02-08
Being newish to Linux, recently successfully installed Surveillance camera program: Motion. Now researching to make myself a little GUI which I can use over my local network (i.e.: same GUI accessed by multiple PC's on LAN). The GUI is very simple: Display a listbox or similar with filenames of video files (sometimes over 100 in a folder) saved by Motion. Listbox should have multi-select option. I then need 3 buttons: 1-Play selected files 2-Move selected files to another folder 3-delete the files.

I was able to produce this using Python and tkinter (which I never heard of past last week). Then I realized that the tkinter GUI has to be played on the local PC. It is able to play the mkv files in succession as selected via MPlayer Current research points toward Python/ Flask/ PHP.

Would Python/ Flask/ PHP be the best way to go to keep it secure but simple for my simple mind?

Any help would be appreciated.

---

### Post by TheFu on 2021-02-08
Webapps are a security nightmare.
I'd use remote X11 or just mount the remote storage over NFS or sshfs to my local workstation.

ssh -X  thefu@ip command

ssh has all the connectivity needed to connect between Unix systems. It really is sad that Windows hasn't prepared people with that type of security tools. So sad.

I certainly wouldn't bother creating a menu. Any file manager can support right-click options, if you want a GUI.  A little bash would create a TUI that is easy, simple, in perhaps 30 minutes. Don't get me wrong,  if the bash becomes longer than 1 pg of code, I'd switch to perl/ruby/python too. Doubt this would.  xenity can make little TUIs, BTW.

But if you want a webapp, flask/python isn't the wore idea - besides the security parts.

---

### Post by rainerfeyer on 2021-02-08
Hey TheFu,
TY tons for answering. 
I do have ssh set up on the local machines and that works. I can easily view the files over the LAN with it, though, my wife is NOT happy about needing to get to the files this way.
We currently use BlueIris which simply shows the recorded video clips and click on the clip, and it shows. Etc Etc .
So, switching over to Linux (Mint), the only program option is a command line program (Motion - which I love), but I need to write something to view the recorded files with simple left right clicks, hopefully speedup slow down, that kind of stuff.
Again, already concocted something with Python and tKinter, but with all the research online, it does not appear possible to view the program over LAN (or Web).
Also, eventually I would like to see the cameras (with button options/ viewing options) when we are traveling.
I have some experience with Python, some Flask, but nothing to create listboxes supporting population of folder content. I have not found Flask can create multi select listboxes to be placed on an HTML form?)
Would PHP/ Flask/ Python be a bad combo? What I wish to create would, BTW, not be listed somewhere on the web, only for my access.

---

### Post by TheFu on 2021-02-08
Ah - the wife.  In that case, setup a DLNA server and let her use a DLNA client to view all the files.  There are many, free, F/LOSS, options.  And the bonus is that these can be limited if you pick the right server software.

For access when traveling, you'll want to run a VPN at home to provide remote access. This isn't THAT hard.  OpenVPN or wireguard really do work.  For you, you can use an ssh tunnel as a SOCKS proxy and access the DLNA server's web interface from anywhere.  I've posted a SOCKS ssh script here a few times.

>  Would PHP/ Flask/ Python be a bad combo? What I wish to create would, BTW, not be listed somewhere on the web, only for my access. 
It completely depends on your ability to create secure code.  I've been programming for 30+ yrs - all sorts.  I've written a commercial video server for clients.  For my needs at home, I'd never bother. The wheel has already been invented.  Rygel, JellyFin, DLNA, VLC, Kodi, are just a few ways for access to be provided.  There is plex too, if you want to have every button and file accessed reported to someone else (not you).

Anything you can access on the web without using an encrypted, key-based authentication, will be found by others, no matter what you do.  I had a private photo gallery just for family decades ago.  Within a few weeks, google was indexing all those photos. I was pissed.  Once google found it, all the other web indexers found it too. Google honors the robots.txt but almost none of the the others do.  Some were abusive to my bandwidth ($$$), re-indexing the full site 6 times daily.  In short, if it can be found, it will. Obscurity doesn't work.

---

### Post by rainerfeyer on 2021-02-08
Ouch,
that sounds as bleak as one should imagine nowadays - privacy is certainly gone (hence my need to change all my PC-OS's).
TY tons for your suggestions and your input - I will read up on the above mentioned tomorrow!
Nothing is simple, yes? :)

---

### Post by SeijiSensei on 2021-02-09
```
sudo apt install minidlna
```

Edit /etc/minidlna.conf with "sudo nano /etc/minidlna.conf" and set the "V=" line to point to the directory where the video files are stored.

```
sudo systemctl start minidlna
sudo systemctl enable minidlna
```

Wait a bit while minidlna indexes the files. This can take awhile if there are a lot of them. You can follow the process with
```
tail -f /var/log/minidlna.log
```

Now you can see the files from any DLNA-compliant device. I use BubbleUPnP on my Android phone with MXPlayer to view the files. My LG TV has a DLNA client built in; so does my Roku device. On Linux or Android, you can use VLC which has a built-in DLNA client. Don't know anything about iThings.

For access from outside you can probably forward a port back through your router to the DLNA server's port 8200 where minidlna is listening. You'll want to consider the security implications of this first.  At a minimum don't use port 8200 on the router. Choose some arbitrary number between 10000 and 60000 and forward that back to the server's port 8200.

---

### Post by TheFu on 2021-02-09
MiniDLNA is great, unless you need transcoded video per device.  If the created videos are all h.264/aac in an mp4 container, then transcoding probably isn't needed.

BubbleUPnP isn't bad; used it for a few years. I switched to VLC as my android client. Sometimes use Kodi on Android too. Both do DNLA fine and both play anything.

DLNA is a LAN broadcast protocol, so you won't be able to use DLNA over the internet. At least it never worked for me. For that, you'll need some media streaming server ... like Jellyfin or Plex with a web interface that you connect into when away.  If you start with Jellyfin, you won't feel the need to use plex. It isn't hard to setup jellyfin - took me about 10 minutes last week. Jellyfin is 100% F/LOSS and won't do anything anti-privacy unless you setup those connections. MiniDLNA won't either.
There is also Rygel - the DLNA server that Ubuntu has advertised.  Rygel is a little flaky in my testing, but eventually I got it working. Minidlna was much easier.  Plex and Jellyfin are more massive, but those systems really want to be media servers for clients that like to see Movie and TV metadata as you browse what to playback.  The last week or so, I've been maintaining both Plex and Jellyfin servers here. There are just a few annoying issues with Jellyfin to me, but the privacy aspects and built-in transcoding as-each-client-requires is very nice.  

Jellyfin allows multiple users, so different content can be seen by different users.  Perhaps you don't want the kids to have access to the security videos?  Most DLNA servers don't have any logins. Anyone on the network with a DLNA client can access all the content.

---

### Post by ajgreeny on 2021-02-09
I use minidlna on my laptop to stream music, videos and photographs mainly to my LG smart TV, and it works brilliantly for what I need from it.  I have also tried rygel but like TheFu I find it a bit lacking and flaky so I no longer use it; it is not a default installed package in Xubuntu but is now included as default I believe in Ubuntu so probably wirth trying. I generally use VLC on all client devices for viewing the DLNA media, whether it's another computer, or Android tablet or phone; the LG TV just sees the laptop in its smartshare utility with no additional app being necessary.

There are a few filetypes that are seen but will not play, for example I record TV programmes onto a USB external drive. 
They are recorded as .ts files, (mpeg2 transport stream) and will not play in any way and as TheFu says, minidlna can not transcode on the fly, so I use thunar's custom actions system to convert them using ffmpeg in a few seconds to .mkv or .mp4 files, both of which play very well. I have no idea whether other Ubuntu DE versions have similar custom actions from right clicking files but it is incredibly useful to me for this and the many other uses to which I put it.

In the past I used plexmedia-server on my main desktop machine to stream media again mainly to the same LG smart TV but about a year ago I moved to Emby-Mediaserver and found it better than Plex; you may find Plex better but each to their own!  I have also tried jellyfin the open-source fork developed from Emby when that moved to closed-source and whilst it is pretty good it is not yet as polished as Emby (or Plex), and does not yet have an app for the LG TV, so for now I stay with Emby which does have an app, but I will keep trying jellyfin.  Plex, Emby and Jellyfin will all transcode on the fly but I usually convert any of those recorded .ts files to mkv (or mp4) as they are both usually smaller files than the original.

Sorry if this is a long winded post but I thought it worth pointing out the possibilities, and how many different ways there are, many of which have been mentioned already by others but which I have never used.
I have never needed to use, nor set up any of my systems to stream media over remote connections so can not add anything more about that.

---

### Post by SeijiSensei on 2021-02-09
A web server like Apache is probably the easiest and safest way to go for external access. Make sure you use at least [Basic authentication]("https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-apache-on-ubuntu-18-04-quickstart") so a username and pasword will be required. You can force the Apache server to list the available files in any order you choose. For descending by timesamp you would use:
```

<VirtualHost *:80>
ServerName     myvideos.example.com
[etc.]

Alias /Videos/ /path/to/the/Videos/directory/
Directory <"/path/to/the/Videos/directory/">
  AuthType Basic
  AuthName "Authentication Required"
  AuthUserFile "/path/to/.htpasswd"
  Require valid-user

  Order allow,deny
  Allow from all

  IndexOrderDefault Descending Date
</Directory>

</VirtualHost>

```

I recommend using [certbot](https://certbot.eff.org/lets-encrypt/ubuntufocal-apache) with [Let's Encrypt]("https://letsencrypt.org/") to provide SSL encryption as well. certbot will create a configuration file based on what you have for port 80, and replace 80 with 443 in the <VirtualHost> declaration.

Once again hide the service from snooping eyes by forwarding a high-numbered port back to port 443 on the web server (80 if you don't use SSL).

If you go this route, you can view the videos while on your local network with only a web browser. The most recent recording will be at the top of the list.

---

### Post by rainerfeyer on 2021-02-09
Doing a quick search on miniDLNA, it looks like a great little streaming app.
Though I do not see how it is programmable? 
I am looking more for a program language which allows me to control the functions of buttons, have a multi-select file list etc etc.
Again, would like to use Python, and, possibly with Flask if I can figure out security and the ability to populate a list box with file name references contained in a single folder.

---

### Post by TheFu on 2021-02-10
We are trying to say - don't reinvent the wheel. There are lots of streaming systems already. Using one of those will be faster and more secure than building your own, especially if you plan to make it available over the internet.

Most media streaming servers see when files arrive and leave the directories they are watching.  You can program all you want to put the files in the specific directories watched by the streaming server and to remove them when done.  I don't remember clearly, but thought miniDLNA required running an "update" task to rescan the directories.  Plex, Jellyfin have watches already setup and do the rescans automatically.  Both have "Delete Media" built into the webGUI.  No need to reinvent that wheel.  But you can, if you like.  The problem will become setting up the permissions to allow the streaming server and the userid running your program control over the files to be managed. Not hard, assuming you understand Unix file and directory permissions.

miniDLNA has CLI options. Use those from your program, if you choose to use that tool.

Of course, if you WANT to use python mainly to learn to use python and build a streaming app, perhaps seeking python specific experts would be a good idea?  There are all sorts of complexities in building a streaming server. It isn't just about sending bits over a network stream based on a client request. Web servers really don't want to do that for long running streams, support fwd, rewind, pause, restart, or jump to timecode.

But this is your itch. Scratch away. ;)

---

### Post by ajgreeny on 2021-02-10
Minidlna has text in its config file at /etc/minidlna.conf which enable autodetection of changes and how often it does so making things much faster than rescanning the whole system with a forced reload.
```
# Automatic discovery of new files in the media_dir directory.
inotify=yes
# Notify interval, in seconds.
notify_interval=900
```

---

### Post by rainerfeyer on 2021-02-10
TY both for hanging in there with me!

I truly have the BUG/ itch to learn more python, and add a little 'other language' to it, like flask etc.
Unfortunate tkinter does not work over network.

As for other sites to help: I have asked on several and since I did not have specific code to talk about, I was either not answered or given a 'your thread has been deactivated since you are not asking specific questions (Stack OF). Once I know which python addition to attack, I will study that and then I can start asking specific coding questions.
I am still stuck a little on Flask, but if I can not come up with a good multi-select list box for recorded files, I will look at ruby next which you (theFU) have suggested :)

Again, thanx both - any other suggestions would certainly be appreciated!

---

### Post by TheFu on 2021-02-10
Are you using remote X11 through an ssh connection?  All x11 programs should work that way - including tkintee.

I suggested ruby?  Really?  When it comes to languages, python is fine. Stick with that for at least 6 months of daily coding.  Don't mix too many languages when learning.

---

### Post by rainerfeyer on 2021-02-10
Hey,
I am using x11vnc and ssh for remote desktop.
Is that what you are thinking, or is there actually a way to remote activate the tkinter/ python program?
That would sound like a great idea!

---

### Post by rainerfeyer on 2021-02-10
Wow! theFu,
how good are you!
I just gave it a try via ssh (withoutx11) and it worked. Probably should create a .sh file to simply this - over the LAN, this is a GREAT breakthrough!
TY for that!
Will deviate from the Flask HTML trials and move into this avenue for now.
Again, tons of thanx!

---

### Post by TheFu on 2021-02-10
x11vnc - uh, no. Use remote x11.
```
ssh -X  feyer@IP  "command options"
```
Simple. The network needs to be fast enough. With ssh-keys setup, it is really convenient. Any LAN should be these days.

VNC would be my last choice. I haven't used that in about a decade. x2go is much faster and easier to use, IME. Any NX-based tool would be better than vnc or rdp. I only use a full remote desktop when away. Sure, for testng, I'll e it on the LAN, but in my world, here's the preferred order for GUI stuff:
[LIST=1]
[*]remote x11
[*]SPICE
[*]x2go
[/LIST]
I run both my web browser and email program over remote X11 almost 24/7.  Using remote X11 is a standard part of my workflow and a been about 25 years.  My desktop is actually a virtual machine running on a different system. I do this for many reasons, but mainly for flexibility.

SPICE is crazy fast.

x2go is for when I need to do desktop productivity apps from a different continent or the local coffee shop down the street.

An old article about some options: [https://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](https://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications)
It doesn't say anything about spice. sorry.

---

### Post by rainerfeyer on 2021-02-11
yup - found out how to call the tkinter script over LAN last night - so, this morning I tried a batch file but it's having problems with display and hanging.
Don't give me the answer yet, once I am done with my current portion of the 'to-do-list' (home, not computer related) I will keep playing with it. Think I found an answer, but will have to do trial and error.
This is a great route to take - again, TY - and I am sure I will be back soon!

---

### Post by rainerfeyer on 2021-02-11
OK,
so, I got the tkinter GUI running over SSH and LAN! 
Initially I would get - nothing - after calling the bash script - then, after some research added this to the py3/tkinter code:
   if os.environ.get('DISPLAY','')=='':
       os.environ.__setitem('DISPLAY',':0.0')

and that worked! I would have thought about DISPLAY :0 if it was a headless target, but it is not. And, the same script did not cause this directly from terminal, only bash. 
The bash script (tMotion.sh)

#!/bin/bash

ssh -X rainer@192.168.0.26 "python3 /home/rainer/Projects/tkinter/MultiSelectCopy-current.py"
## /tmp/mylogfile 2>&1 &"

But, it works, I am glad you got me there. Now I will work a little more on the actual video streaming script and then try to get a little understanding of x11 :)
TY again

---

### Post by TheFu on 2021-02-11
Don't set the DISPLAY variable inside your script.
BTW, if the userid on the client and the server are the same, you don't need to specify it.
And if you setup the ~/.ssh/config file, you don't need the IP address either.
And if the script is setup correctly with the #! line, you shouldn't need python3 in the ssh command at all.
And the directory doesn't need to be so long ... 

```
ssh -X {remote} ~/Projects/tkinter/MultiSelectCopy-current.py
```
would be fine. If it were me, I'd put the script into my ~/bin/ and have that in the PATH for that userid, set in the ~/.bashrc. The {remote} would relate back to the stanza in the ~/.ssh/config file.  This is handy so you don't need to memorize IPs, usernames, alternate ports for ssh, alternate ssh-keys for different systems and a bunch of connection settings that can become useful for more complex setups.

---

### Post by rainerfeyer on 2021-02-12
Hey,
where should the if os ...DISPLAY... go? 
Good to know about the ssh and config suggestions! So much to learn!
Currently having a problem with tkinter GUI crash by activating askforfilenames(). Works great first time, but crashes when trying a second time without leaving GUI.
Tried asking this question on StackOF, but apparently question again not accepted (I am not smart enough, I guess).
Would you tell me where to turn for these questions? Of course, I am more than happy with your help but at some point someone may complain that I am on the wrong forum for these questions?

---

### Post by TheFu on 2021-02-12
ssh -X controls the DISPLAY setting automatically. Don't do anything.

ssh is a very mature tool.  If something seems hard, you probably aren't doing it the easy way or didn't setup something to make it easy.

Python questions are best asked in python groups. I've only played with that language.  Earned my living for 15 yrs programming in other languages (most that you've never hear named).

---

### Post by rainerfeyer on 2021-02-12
I will remove the DISPLAY section again as trial. The program over SSH would not display without the above, however, when I tried it before. Weired.
I did find a python forum and will register there as well.
As always, your help and thoughts are greatly appreciated! Especially your insight on the larger scale of things!

---

### Post by TheFu on 2021-02-12
Maybe you should join a local python meetup group?  Use google - search by the city name, local universities, computer clubs, and other, similar groups.  There might be a LUG nearby too. Some of those people will know about other tech groups.  For smaller cities, perhaps there's a regional term for the area that the groups all take.  "South-Alabama LUG" or "North Georgia LUG" .... or "Gotham City Python"

My metro area has a python group with over 7200 members.  [https://www.meetup.com/python-atlanta](https://www.meetup.com/python-atlanta)  They have weekly coding meetings.
With COVID, many of these groups have gone virtual with online meetings.

---

### Post by rainerfeyer on 2021-02-12
I actually did at one point look for user groups in this area, but... the closest group is 1.75 hours away, about the same distance than Atlanta! (Atlnata may be a bit more). I am in Jonesborough TN :)
I will sign up for the Python user group (python-forum.io) now!
:)

---

### Post by TheFu on 2021-02-12
> **rainerfeyer said:**
> I actually did at one point look for user groups in this area, but... the closest group is 1.75 hours away, about the same distance than Atlanta! (Atlnata may be a bit more). I am in Jonesborough TN :)
I will sign up for the Python user group (python-forum.io) now!
:)

You have internet, right?  Join their meetings using whatever video-chat tool they use.  You aren't limited by physical location.

---

### Post by rainerfeyer on 2021-02-13
That is probably a great idea - for the future.
Right now, I am trying to research as much as I can about what I don't know - that is a lot.
Then I will try Python forum. Once I feel a tad comfortable, I will see about joining the LUG online.
With this python and tkinter, I feel the 1 step forward .....
:)

---

