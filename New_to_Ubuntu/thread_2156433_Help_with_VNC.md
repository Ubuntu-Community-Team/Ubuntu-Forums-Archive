---
title: "Help with VNC?"
date: 2013-06-21
forum: New to Ubuntu
---

### Post by jumpycore on 2013-06-21
Ubuntu 12.04 LTS

[https://www.digitalocean.com/community/articles/how-to-setup-vnc-for-ubuntu-12](https://www.digitalocean.com/community/articles/how-to-setup-vnc-for-ubuntu-12)

I used this tutorial. I had a couple issues...

When I got to the point where you connect via TightVNC, my windows laptop connected once, but I had no access. I couldn't see anything, it was all grey. Mouse did nothing.

Then later every attempted connection was refused.

Not sure what I did wrong. Could someone help me troubleshoot, or start it over?

---

### Post by TheFu on 2013-06-21
That is a complex tutorial.
I'd break things down step by step.

Since that tutorial shows how to use ssh tunnels, I'd ask if you have ssh access working? That would be step 1. Forget VNC until that works.

If your client and server are on the same LAN, I wouldn't bother with ssh tunnels.  OTOH, if any traffic goes over an untrusted network ... internet, then there is no way I'd use VNC without a VPN or ssh tunnel.  Also, if you are going throw any routers (like a Linksys at home), you'll need to open some ports for this to work. There are how-tos for this all around.

I would also get VNC working locally - only using Linux systems before trying to get Windows involved.  You can connect to a VNC server running on the same machine locally. That should work fine.

In order to troubleshoot, we need log files. What do the log files show?   [http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files)

---

### Post by steeldriver on 2013-06-21
I agree, it seems needlessly complicated (at least for a starter setup) - do you really need to run VNC as a separate user / service? if not then all you should need to so is install the tightvncserver package, create a minimal ~/.vnc/xstartup file in your own user directory, and run vncserver in a normal user session. Typically I do it over SSH, and specify a display number corresponding to the port that I've already tunneled in the SSH session, e.g. 

```
ssh -p<port> -L 590**5**:<host>:590**5** <user>@<host>
```

(or the equivalent from Windows using a PuTTY SSH tunnel) then

```
vncserver -geometry 1440x900 **:5**
```

FWIW the 'all grey' desktop usually means it can't start your specified desktop session and has fallen back to a default X session

---

### Post by HiImTye on 2013-06-21
do you need VNC specifically, for a specific reason? there are two better alternatives, depending on your specific needs
&#8226;RDP
&#8226;SSH X forwarding
both are better options than VNC as VNC basically sends bitmaps of your desktop (which is very slow/data intensive), while the two others perform much more like a window manager. VNC will also garble up it's display over poor connections, making it very annoying.

RDP
[http://networkstatic.net/xrdp-an-easy-remote-desktop-setup-for-your-ubuntu-servers/](http://networkstatic.net/xrdp-an-easy-remote-desktop-setup-for-your-ubuntu-servers/)
note: if you use UFW with default deny you will need yo add an exception for xrdp to accept incoming connections

SSH X forwarding
[http://narnia.cs.ttu.edu/drupal/node/132](http://narnia.cs.ttu.edu/drupal/node/132)

so, what's the difference? RDP will log you into a desktop session, while X forwarding will display only the program(s) you launch. 

the only reason to use VNC is to view your currently logged in session.
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by TheFu on 2013-06-22
Actually, instead of RDP, VNC, or X/Windows, I prefer NX.  NX is based on ssh networking, feels 2-3x more efficient than RDP/VNC and has clients for the 3 main desktop OSes.  I use FreeNX on the "remote server" and the NoMachine NX-client for Linux or Windows.

The client-side setup is fairly easy.
The server-side has these instructions [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX) - there are a few manual steps to handle the keys (creating new keys on the server and manually providing those to each client), but it isn't much harder than apt-get install.  First time, it took me 15 minutes.  On every other machine I installed it, it was 5 minutes. I'm slow that way.

I've used NX from 5 different continents around the world - it works great for office-productivity apps.  Clearly, the multimedia performance is lacking. If you **need** that, check out **spice**. [http://blog.jdpfu.com/2013/01/12/of-spice-and-kvm](http://blog.jdpfu.com/2013/01/12/of-spice-and-kvm)

---

### Post by jumpycore on 2013-06-23
Hey guys, thanks for the replies. I just re-installed Ubuntu to start fresh. So no need to post the log file anymore. The reason I want remote access is because I have a media server that I intend to use the Ubuntu computer for downloading. I'll have the computer up next to my server in a high place and would like to access it from my Windows based laptop to add queues, organize, etc. I'm using SABnzbdplus, SickBeard, CouchPotato and the like. The server I currently use is FreeNAS but I'll be wiping it pretty soon to maybe install Ubuntu Server.

I don't need it for anything but using the WebUI's for these programs really. Maybe using Chrome and surfing IMDB to add files to the queue that way. Basically thats it I guess.

My thing is if I have remote access I have to have a GUI because I have virtually no knowledge on command line.

---

### Post by jumpycore on 2013-06-30
Okay I installed FreeNX. I looked for a Client to use from my Windows machine and found NoMachine. It connects but then comes up with an error saying "The NX service is not available or the NX access was disabled on host 192.168.1.X"

From what I've read I think I might have to have NoMachine installed on my Linux computer in order for it to work? Maybe I should try a different Client?

---

### Post by TheFu on 2013-06-30
> **jumpycore said:**
> Okay I installed FreeNX. I looked for a Client to use from my Windows machine and found NoMachine. It connects but then comes up with an error saying "The NX service is not available or the NX access was disabled on host 192.168.1.X"

From what I've read I think I might have to have NoMachine installed on my Linux computer in order for it to work? Maybe I should try a different Client?

FreeNX is the server. For that to work, you **must** have ssh-server installed and working. No NoMachine "server" is needed.

If you can ssh from the client machine to the server machine, then that is all the connectivity necessary. NX works through an ssh tunnel - it creates as part of the client to server connection.  Test ssh with putty from Windows or any ssh client .... android, OSX, Windows, Linux, UNIX, AIX, Solaris .... whatever. There must be 200 of them.

The NoMachine client is the best that I've found but there are other clients. I found them to be buggy.  Inside the client, you need to setup everything properly for your specific situation.  You can run a full desktop, single application or no GUI at all. Also the bandwith, screen size, colors are your choice too.  For WAN connections, I usually kick off an xterm, then manually start a pure WM environment. On the LAN, I use lxde, but anything except Unity/Gnome3 should be fine.

If you are still having ocnnection issues, revisit the "ubuntu FreeNX" page and check that you've setup everything manually correctly.  If you describe what you've done here, we might be able to point out a mistake.  If you didn't follow those steps and manually handle a few things, then you aren't configured yet.

---

### Post by jumpycore on 2013-06-30
I was able to connect to Ubuntu from Windows with no problems via PuTTY.

Here's the Details on the error.
```
[FONT=arial]NX> 203 NXSSH running with pid: 4332[/FONT][FONT=arial]NX> 285 Enabling check on switch command[/FONT]
[FONT=arial]NX> 285 Enabling skip of SSH config files[/FONT]
[FONT=arial]NX> 285 Setting the preferred NX options[/FONT]
[FONT=arial]NX> 200 Connected to address: 192.168.1.X on port: XXXX[/FONT]
[FONT=arial]NX> 202 Authenticating user: nx[/FONT]
[FONT=arial]NX> 208 Using auth method: publickey[/FONT]
[FONT=arial]NX> 204 Authentication failed.[/FONT]
```

Maybe it's something in the way I set up the key? I followed [these]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") instructions. I created the keys (without passphrase), saved it to .ssh/id_rsa.pub and then emailed it to Windows and imported the key.

I have also tried using the id_dsa, id_dsa.pub in case I was doing it wrong. I've tried it with a username/pass I've picked in the setup. I just now set "PasswordAuthentication No" and did a "sudo service ssh restart" then tried logging in as a guest user and nothing. And I added "AllowedUsers jumpy" at the end, as its my username on Windows. Just to see if it would help.

---

### Post by TheFu on 2013-07-02
I've never bothered with key-based auth for Windows/Putty. Can't help you there.  If password based works, then the ssh connection is fine.

The key to be entered into the nx-client is that from the NX userid on the server. The freenx setup instructions were clear about when I followed them.  Your personal ssh-key is NOT used for that part of the authentication.  Just like with putty, the userid and password used inside the nx-client is for your personal ID, not the NX server ID.  I hope that makes sense.  I do know of people that use Linux-based NX clients with their ssh-keys (both for nx and their userid) and get connected without any prompting.  I don't know if that is possible from Windows.

---

### Post by TheFu on 2013-07-02
I've never bothered with key-based auth for Windows/Putty. Can't help you there.  If password based works, then the ssh connection is fine.

The key to be entered into the nx-client is that from the NX userid on the server. The freenx setup instructions were clear about when I followed them.  Your personal ssh-key is NOT used for that part of the authentication.  Just like with putty, the userid and password used inside the nx-client is for your personal ID, not the NX server ID.  I hope that makes sense.  I do know of people that use Linux-based NX clients with their ssh-keys (both for nx and their userid) and get connected without any prompting.  I don't know if that is possible from Windows.

You need to allow password authentication until this is all working with keys. Disabling it before that point is counter productive.  If you have fail2ban loaded and don't use a bonehead password, I wouldn't worry too much about ssh security. It is covered.

---

### Post by jumpycore on 2013-07-02
this is so damn frustrating.

---

### Post by jumpycore on 2013-07-02
OK, so to disable the key auth, is this what I need to set as "No?"

RSAAuthentication
PubkeyAuthentication

---

### Post by jumpycore on 2013-07-02
fixed. did some detective work, some old posts from 2009 ended up helping me out.

added my local name, nx, and my windows name to AllowUsers and reset the port back to 22 (i changed it for security) and viola! it ****in works.

 thanks for the help!

---

### Post by TheFu on 2013-07-03
> **jumpycore said:**
> fixed. did some detective work, some old posts from 2009 ended up helping me out.

added my local name, nx, and my windows name to AllowUsers and reset the port back to 22 (i changed it for security) and viola! it ****in works.

 thanks for the help!

**Fantastic!**  As you've learned, key-based authentication is always enabled. It is just the password-based stuff that you might want to disable for non-LAN addresses.  With **Fail2Ban** loaded, that isn't so important, provided you configure it properly.  F2B assumes port 22, so if you changed it on the server-side, then that config needs to be updated. If just on the router for port translation (443 --> 22) - you are fine with the defaults.

Not certain I understand the "AllowUsers", but if you change the port on the server, then the clients need to talk to a different port.  On the server itself, I leave the ssh on 22 (default), only on the internet do I change it using the router's port translation.  

Then I modify the ~/.ssh/config file on each (and every) client machine with a specific stanza for each ssh server to have the alias I want, real-internet hostname (usually ugly), router high-port, and userid.  An example:

```
host lubuntur
  user thefu
  hostname d423423s.dyndns.org
  port 443 

```

So in most of my ssh connections from "this" client, I don't need to specify user, port and can call the remote machine "lubuntur".  **ssh lubuntur** is automatically converted into **ssh -p 443 [email]thefu@d423423s.dyndns.org[/email]** - nice. I use the real names and ports in the nx-client settings, not sure why - thick clients do that to me. But ssh, sftp, scp, rsync, rdiff-backup, which all use ssh libraries, definitely honor the ~/.ssh/config file settings.

Note the use of port 443 - when traveling, many/most hotels block non-standard internet ports, so only 80, 443, 25, 465, 993 are allowed. If ssh is not running on 443, there's about a 50/50 chance you will not be able to access it from a hotel.

Ah - I suppose this doesn't work for Windows clients. No idea of ~/.ssh/ anything? I dunno.

Anyway, NX is more secure and network efficient than VNC, IMHO.  I've used it to remote back home (Atlanta-based) from all around the world. Just the last year, from South Africa, Nepal, Korea, Spain, France, Italy, Austria, Czech Republic, and lots of places in the USA.  

It also works GREAT on a fast LAN.  Daily, I use a Win7 laptop to run my Ubuntu desktop in a full screen NX session. Doing that right now. The same session has been alive about 2 weeks.

I hope you find it works as well as I've found it to work.

---

### Post by jumpycore on 2013-07-03
I also neglected to mention - I returned the keys on the Client computer(Win) back to default(instead of copying the key from the server computer), and that's when it stopped getting refused altogether, logged in, then auth&pass was rejected. So thats when I googled around some more and added the AllowUsers.

I'm running the most recent Ubuntu on it, so it's a bit slow due to graphic reasons, but I think it might be something I can work on in the future. One step at a time. But I think I should do some backups before I screw with anything else.

I noticed, when accessing my friends computer he uses 443 on a lot of things, like his PLEX. So I may do that too. He & I access his PLEX from all over the world as well.

---

### Post by TheFu on 2013-07-03
For VPNs, it is very common to have a "server key" that needs to be installed on the client, plus something from the client side - often a PIN - but in this case your personal ssh credentials (either an ssh-key or userid/password), which are created on the client-side pushed back to the server.

There was a script that wasn't included with the freenx package that needed to be downloaded and run. If you didn't do that, then you are using the default server keys that everyone in the world knows. Anyone can access your NX server.  Please, please, please change those keys.

I've never touched the AllowUsers.  Which file/service is that for?  NX, ssh, what?

If you run Unity over NX or any remote desktop - your life will suck.  Load up something like LXDE and use it. When you are local, use Unity (if you must), when you are remote, use LXDE.

Port 443 ... without an ssl multiplexor program and the skill to set that up, you cannot have more than 1 program listening on a single port on a single IP address.  Your friend might have multiple public IPs.  I do, but most people do not.

I just got a Roku (forced by Amazon) and learned I can't access content on my own LAN without addons?  Crazy!!!!  For the last 10 yrs, I've been time shifting programs.  When Amazon broke access to all their VOD from Linux 2 months ago, the SO became pissed. The best solution was getting a Roku ... but that has added all sorts of other complexities that I won't go into besides to say that I'm looking in to loading Plex to replace my 3 yr old XBMC setup. **Damn you Amazon!!**

---

### Post by jumpycore on 2013-07-03
man, you have so much information about this stuff it's almost overwhelming haha.

I have no clue if I'm using the default nx server keys tbh. AllowedUsers via sshd_config. You have to put it on the bottom of the config file

How can I add LXDE and use it via the client? I really enjoyed Mint LXDE (was using a radeon card so i HAD to because there were no working drivers on ubuntu). 

My buddy who set his PLEX up is REALLY smart. Knows what he's doing. Has a Windows Server & NAS setup. I used to be pretty good at computer stuff, but I'm not as much anymore.

I bought a WDTV Live when I was deployed, and I love it. Watch movies/shows, listen to music off my server (it's running FreeNAS) as easy as connecting to my network. It even has apps like Netflix, which has WAY better resolution than my XBOX does (its always blurry I'm sure because of connection). Even supports MOST .mkv and subtitles unlike some. Although, it's not PLEX or XMBC compatible as far as I know.

---

### Post by TheFu on 2013-07-04
> **jumpycore said:**
> man, you have so much information about this stuff it's almost overwhelming haha.

We all know things that many other people do not.  **This** is the stuff I've learned in 20+ yrs doing programming, systems setup, architecture, corporate VPNs, and system admin stuff.  OTOH, I know very little or nothing about many topics.

> **jumpycore said:**
> I have no clue if I'm using the default nx server keys tbh. AllowedUsers via sshd_config. You have to put it on the bottom of the config file

There is no magic to the sshd_config.  Everything - - EVERYTHING --- is explained in the man page for it.  **man sshd_config**.  I doubt order matters unless there are 2 of the same entry.  If you didn't specifically generate an ssh key for the nx userid, then you are using the key that **everyone** in the world has. That means **anyone** in the world can access your system to that point ... bypassing fail2ban.  Google "ubuntu freenx" and check those instructions carefully. Follow them. If you can't - then you should remove FreeNX and find a different solution.

> **jumpycore said:**
> How can I add LXDE and use it via the client? I really enjoyed Mint LXDE (was using a radeon card so i HAD to because there were no working drivers on ubuntu). 

**sudo apt-get lxde**  Video drivers have ZERO to do with most desktop environments. I only know that Unity and Gnome3 demand it - none of the others do.  It was a design decision ... which I happen to disagree on.

> **jumpycore said:**
> My buddy who set his PLEX up is REALLY smart. Knows what he's doing. Has a Windows Server & NAS setup. I used to be pretty good at computer stuff, but I'm not as much anymore.

Often, being clever is not enough.  I've failed to install many complex Linux things over the years, but most things do install and work these days.  I don't think I'll bother with PLEX - seems limiting compared to XBMC and I already have multiple other ways to watch local media or stream it anywhere in the world. It was really just for the Roku and since Rokus don't play 90% of my content (all time shifted legal-like), I don't see the reason to switch.

> **jumpycore said:**
> I bought a WDTV Live when I was deployed, and I love it. Watch movies/shows, listen to music off my server (it's running FreeNAS) as easy as connecting to my network. It even has apps like Netflix, which has WAY better resolution than my XBOX does (its always blurry I'm sure because of connection). Even supports MOST .mkv and subtitles unlike some. Although, it's not PLEX or XMBC compatible as far as I know.

I have a WDTV Live HD, but the version that doesn't support Netflix.  I've had 3 other xvid/divx players before that.  The WDTV doesn't handle many older formats at all, so a real computer was needed in my environment. That's where XBMC comes in. Thanks to a low powered AMD CPU and ATI GPU, it handles the newest, 1080p stuff and the older, CPU-decode-only SD stuff.  I really miss the very first player I had compared to all these newer ones. It had all sorts of fantastic features that none of the new players deal with due to "big content" being involved these days.  Of course, I had to get it from overseas and when it broke, had to fix failed components myself. Eventually, after 5 yrs of use, it couldn't be fixed anymore. Sigh.

I can't believe people put up with the noise from Xbox-whatever or Playstations. Xbox360s that I've heard are like jet engines. Can't imagine trying to watch a quiet, scary, movie with either unit powered on.  My XBMC box is 100% silent, though I had to swap out the jet-engine-PSU for a pico-PSU for $50. Got mine here [http://www.mini-box.com/picoPSU-80](http://www.mini-box.com/picoPSU-80) - yes, it really is that small.

---

