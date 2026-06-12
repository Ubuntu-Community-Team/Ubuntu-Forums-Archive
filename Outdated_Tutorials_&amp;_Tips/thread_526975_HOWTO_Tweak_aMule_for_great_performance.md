---
title: "HOWTO: Tweak aMule for great performance"
date: 2007-08-16
forum: Outdated Tutorials &amp; Tips
---

### Post by Hallvor on 2007-08-16
**1. What is aMule **
aMule is a p2p, or peer-to-peer, client for the eD2k network, commonly known as eDonkey network or eD2k network (eDonkey2000). 
[B]
2. Sharing Files with aMule [/B]
First off, note the eDonkey2000 network is not meant to share small files such as audio clips and small mp3s, but instead is optimized for distribution of larger files. The current stable version of aMule is 2.2.x, and has a lot of exciting features, like large file support, UPnP and protocol encryption. If aMule for some reason doesn`t work properly or you like the most popular client on Windows better, aMule`s Windows "cousin" eMule runs well in Wine. It is however recommended to use native applications when possible.

The ed2k-network is huge and with an enormous amount of users and shared files. The typical user shares hundreds of files and have queue sizes from a few hundred users to several thousand. The ed2k-network is excellent for finding rare content and for sharing many large files. If you are patient, you will be rewarded with material not found anywhere else.

**3. Installing aMule. **
If you haven't installed aMule yet, do so by launching a terminal (Applications-> Accessories->Terminal and type 

```
sudo apt-get install amule
```

If you can`t find it, you may need to enable the universe and multiverse repositories. (Click Applications->Add/Remove in the main menu of Ubuntu and tick «Show unsupported applications» and «Show commercial applications»)
(You may also install aMule from Applications ->Add/remove. enter amule in the search box, tick aMule and click apply).

**4. Running aMule for the first time **
First, launch aMule. This can be done by executing the command amule in the terminal or by launching aMule from the main menu. You should find aMule in Applications->Internet. Running aMule from a terminal can be useful in cases of crashes to find out what is wrong.
Once started, aMule will display a notification telling you that you are running it for the first time.
Please note that aMule makes extensive use of right-click menus, so if you can't find a function, try right-clicking on the item you wish to manipulate. 

**5. Configuring aMule **
Before you begin file sharing, you will need to properly configure aMule. This includes connection speeds and limits, directories to be used, proxies, port settings and other settings. You can access aMule preferences by clicking on the Preferences icon at the top of the aMule window. 
Here are some settings under *Preferences* you might want to look at::

*General*: -Type a nickname in the box if you want to. This will be visible to all users downloading from or uploading to you.

*Connection*: This is important. You don`t want to set the upload limit too high or too low. Setting it too high will choke your connections and decrease performance, and setting it too low will make you lose credits from other filesharers. Other clients will remember the clients who upload data to them, and will give them a better position in their queue. Therefore, high upload means faster download. I recommend setting the upload limit to something like 60-80% of your upload capacity.

Slot allocation means how fast aMule should upload to each client. I recommend dividing the upload bandwidth by a factor of 5-6, so that an upload of 100 kB/s gives some 16-20kB/s per client. Too many open connections may also decrease performance (slightly). (Bear in mind that the values for speed given by ISPs are usually given in kilo Bits per second [kb/s] but the values to be entered in the text fields 'Download', 'Upload' and 'Slot Allocation' contained in "Bandwith Limits" are in kilo Bytes per second [kB/s]. To convert to kilo Bytes simply divide the kilo Bits value by 8. 

As for TCP and UDP ports, just use the standard ports unless you have trouble. Some ISPs will throttle certain common P2P ports, so changing them might work in some cases. Try any non-standard p2p port first. If that doesn`t work, use a port usually restricted for "important" traffic, like 554, 443 or 1755.

The TCP and UDP port will have to be open from aMule to the internet. The first obstacle is iptables in Ubuntu. Iptables will cause aMule to receive firewalled status &#8211; or low id. Being firewalled will drastically decrease performance. To open the ports you can either install Firestarter, the GUI for iptables by typing the following in the terminal:

```
sudo apt-get install firestarter
```

From Firestarter, open the ports in Preferences->Connection in aMule.
Or, you can just open the ports using the terminal. Type, e,g, 

```
sudo iptables -A INPUT -p tcp --dport 4711 -j ACCEPT
```

to open tcp port 4711, and 

```
sudo iptables -A INPUT -p udp --dport 4712 -j ACCEPT
```

to open udp port 4712. (To close the ports again, use the same parameters, except replace «ACCEPT» with «DROP».)

To acieve maximim performance, it is also a good idea to open a UDP-port for extended server requests. This means the port through which all non-core packets are sent to the server. That is data such as file rates, extended file descriptions (encoding, audio length, video resolution, etc), and other trivial but very handy data. The UDP port for extended server requests is always TCP-port +3, so in this case we open it with

```
sudo iptables -A INPUT -p udp --dport 4714 -j ACCEPT
```

If you have a router, you also need to open the above mentioned ports and forward them to your computer. If you open the ports but don`t forward them to the right device, you will be firewalled.

If you don`t know how to open and forward your ports, enter this page: [http://portforward.com/routers.htm](http://portforward.com/routers.htm) From this page, select your router. You will now enter a new image with a lot of application names. aMule is unfortunately not on the list, but select eMule instead. You should now get a guide for your router on how to open and forward the ports. (Remember that eMule and aMule uses different default ports.) 

Max sources per file: This all depends on how much your router and modem can handle. The more connections they can handle without problems, the better. I have mine at 500 and 700 respectively. You may want to experiment with these values. If you put the limit too high, you may choke your router and internet becomes unresponsive.

Networks: Make sure you have both ed2k and Kad ticked.
Message Filter. This is where you can fill in common spam-messages. Just copy and paste the spam message into the box and separate messages with a «,» (without the «s) and you`ll never see the message again. 

*Server*. This is important. Some servers are fakes, mainly run by the entertainment industy, and will not give any results. To avoid the bad ones, untick the «update serverlist» boxes, and tick «autoconnect to servers in static list only».

*Directories*. Incoming directory is where your finished downloads will be saved. Keep in mind that the default setting is within the hidden .aMule folder, so if you don`t change it you will have to use Ctrl+h to make it visible. I recommend making a folder in your home directory for incoming files, and point towards it from aMule. Tempfiles is reserved for non-complete files, and may well be hidden. Shared directories is the files you share using aMule. (Please be generous. Filesharing is after all about sharing, and not about using aMule as a download machine. Whatever you download has to be uploaded by someone else. Roughly speaking: Total network upload speed = Total network download speed.) By default, you only share your incoming folder, and you can`t unshare it. Double click on a folder to share the contents. This will not share subdirectories! If you have one or more subdirectory within that folder you want to share, right click the folder! Any shared directory will be marked in bold letters.

*Security*. Tick «Enable IP-filtering.» The purpose of using an IP-filter is to block the bad guys, mainly the entertainment industry and their lackeys, who are sabotaging the ed2k network. Clients on your ipfilter will not be able to establish a connection to your computer. I use the ipfilter from Bluetack, so you can insert this url [http://www.bluetack.co.uk/config/nipfilter.dat.gz](http://www.bluetack.co.uk/config/nipfilter.dat.gz) and then click «Update now». The ipfilter should then download and install. (A known bug in Feisty may cause aMule to crash while updating the IPfilter.) If you can`t do without an IPfilter, try Moblock. [http://ubuntuforums.org/showthread.php?t=192559](http://ubuntuforums.org/showthread.php?t=192559)

*Gui-tweaks* contains a few useful settings, like percentage, progress bar and fast ed2k-links handler. You can use the latter for ed2k links found on the internet and click apply, and the file shoud be on your download list.
That`s it for the Preferences box! Click ok to save the changes.

The last thing you have to do before starting to use aMule is to add servers. There are no servers by default. Select the Networks icon between the Disconnect and Search button in the main menu.  Add this line in the top box and press enter: [http://peerates.net/peerates/certifiedservers.met](http://peerates.net/peerates/certifiedservers.met)
You can also add servers manually from e.g. [http://gruk.org/list.php](http://gruk.org/list.php) and enter name, IP and portnumber in the boxes below. (Avoid servers marked in pink.) Once you have a few servers, right click a couple of large servers with low responsetime (ping) and right click. Select add to static server list. (If you chose to autoconnect only to servers in static serverlist, aMule will only try reconnecting to one of these safe servers if disconnected.) Remember: Do not connect to servers located in the USA, since they almost certainly are fakes.

**6. Using aMule for the first time**
Now, if you are done with all the steps above, it is time to test aMule. You will have to restart aMule to make all the new settings work properly. (All settings are saved in a file called amule.conf in your .aMule directory. Do not change these settings unless you know what you are doing.) 

Once aMule is restarted, you need to connect to a server. Select the Servers-icon on the top menu and try a relatively large one with a low ping number and connect by double clicking it. If everything is normal, the left arrow on the little globe on the bottom right of the screen should turn green instantly. This means you are not firewalled and will enjoy good performance. If you also want to connect to Kad, select Kad right below the disconnect icon on the top of the main menu. Select bootstrap from known clients. (If you have never downloaded a file with aMule before, you will not have any known clients, and the right arrow on the little globe on the bottom right may be yellow. If your left arrow (ed2k) is green, the right arrow should turn green once you have put a few popular files on your download list and Kad is properly bootstrapped.  
[B]
7. Searching.[/B] 
Click the Searches icon on the main menu. Type allows you to select where to search. On a local server, on all servers or on the serverless Kad network. (Do not use Kad for the first search on a fresh install, since it needs to bootstrap properly first.) Choosing global search will give more results than a single server search. However, for a very popular file, it does not really matter. (Note: Some servers have been forced to filter certain words, if they are identical to names of polular movies, like "king". If you don`t believe me, try searching for "king" on a donkeyserver. Fortunately there is a way around this - just use the Kad search!)
 
Click the Extended Parameters box. This is important to narrow down your search and find what you are looking for. Under File Type, select if you want to download a video, archive, cd-image or something else. Specifying a minimum and maximum filesize is also useful to filter out files you are not looking for. If you don`t do this, the file you are looking for may (in a worst case scenario) not show up on your search list. Preferably find a file with plenty of sources. A large file with just a couple of sources may take weeks to download. A file with 200+ sources is very popular and should fly if you upload fast enough.
When you find something you want to download, right click and select download. Click the Transfers icon in the top menu, and the file should be there.

**8. Fake files and how to avoid them **
Some files out there are misnamed or corrupted. In most cases they are porn files with wrong names and even wrong extensions. To avoid getting these files always check if the file is commented. If other users have commented the file, an icon will turn up next to it. Right click the file and select Show All Comments. You will also see what file name the other user has for the file. This is important if it differs from yours. If you are looking for a movie, and you see someone has marked it as ok, it is a good idea to see if the other user has the same filename as yours or if it is something you were not looking for.
The second check you can do to avoid fake files is to right click the file on your download list and click Show File Details. In this box you can see what the other users are naming their files. The majority is usually right if there are different names/extensions.

Thirdly, use the preview function once you have downloaded a few chunks. Select the  Preferences icon->Files and tick the box Try to download first and last chunks first. This will make the movie previewable sooner. (Preview only works on movie files in aMule.) Click on to Directories in the Preferences menu and type mplayer or vlc (if you have it installed) in the box. You should now be able to preview a partially downloaded file in Transfers with a right click ->select preview part. If you can`t make it work, you can also enter the tempfiles directory and open it there with a video player.

(Some files are just garbage made to poison or spread spam to the network, and that goes for most relatively small files with wmv, wma and a few with exe extension.)
[B]
9. Make Firefox accept eD2k links[/B]
eD2k links are available on the web and function pretty much the same way as torrentfiles. It is possible to copy the links, paste them into aMule`s eD2k link handler on the bottom of the screen. But a much easier way is to associate eD2k-links to aMule through Firefox. eD2k links will then be added directly to aMule with a click of a button.

eD2k links will not launch in a browser of you haven`t got amule-utils installed. Install it with 

 ```
sudo apt-get install amule-utils
```

(1.) Launch Firefox.

(2.) Then, insert about:config in the address bar. Right click on the list, select *New*, then *Boolean*; insert *network.protocol-handler.external.ed2k* as Preference Name and *true *as Value.

(3.) Now another right click, select *New* and *String*; insert *network.protocol-handler.app.ed2k* as Preference Name and */usr/bin/ed2k* (or path to where the file is installed on you system) as Value.

(4.) Restart Firefox.

Now eD2k links will be captured by aMule

**10. FAQ: **
Just read this: [http://www.amule.org/wiki/index.php/FAQ_aMule](http://www.amule.org/wiki/index.php/FAQ_aMule)

**11. Filesharing ethics **
I just have to mention this again, filesharing is about giving and receiving, with emphasis on giving. Always upload at least as much data as you download, since downloading more data than uploading will slow down the network because users with big pipes will have to use their bandwidth to feed the leechers.

Secondly, share rare files. Especially if you are the only source among millions of users, sharing such a file is a valuable contribution to the ed2k network.
Click the Statistics icon on the top menu to see how much you have downloaded/uploaded, and always try to keep at least a 1:1 ratio. (Mine is 2:1, meaning that for every GB i have downloaded, I have uploaded two. I even upload when I have no files on my download list, 24/7.)
[B]
12.Reinstalling or removing aMule[/B]
If you want to reset all settings, the easiest is to remove and reinstall amule. Do this with
```

sudo apt-get remove amule
```

From the desktop, press Alt+Home and Ctrl+h and delete the .aMule folder (containing the config file). Then reinstall aMule with 

```
sudo apt-get install amule
```

or do these operations from Applications->Add/remove

Credits: A lot of the text is based on the following:
[http://www.amule.org/wiki/index.php/Getting_Started](http://www.amule.org/wiki/index.php/Getting_Started)
[http://www.amule.org/wiki/index.php/Extended_server_requests_UDP_port](http://www.amule.org/wiki/index.php/Extended_server_requests_UDP_port)
Opening ports from the commandline    is from this  Howto: [http://ubuntuforums.org/showthread.php?t=331161&highlight=open+ports](http://ubuntuforums.org/showthread.php?t=331161&highlight=open+ports)
Associate eD2k links with different browsers: [http://www.amule.org/wiki/index.php?title=Ed2k_links_handling](http://www.amule.org/wiki/index.php?title=Ed2k_links_handling)

Happy sharing!


Edits:

18.08.07: Included info about large file support in CVS version of aMule. Thanks to KubuntuKilledMe.
23.08.07: Included info about last resort ports.
30.08.07: Included extra info about fake servers and blocked search terms on server searches.
08.09.07: Included extra info about extended server requests, eD2k links handling, plus crash in Feisty while updating IPfilter. Thanks to KCPokes.
18.09.07: Removed recommendation of donkeyservers because of suspicious behavior (no search results).
05.02.08: Included URL for compiled aMule 2.2.0 CVS version.
06.08.08: Minor edit because of released stable aMule 2.2.x.

---

### Post by KubuntuKilledMe on 2007-08-18
The cvs version of amule handles files > 4gb.

---

### Post by Hallvor on 2007-08-18
Thank you. I will update it.The CVS does also supports UPnP, I heard. Do you know if it supports protocol obfuscation?

---

### Post by KubuntuKilledMe on 2007-08-18
I don't know, sorry.

---

### Post by Hallvor on 2007-08-18
Searched the web a little and found this: 

[http://en.wikipedia.org/wiki/Comparison_of_eDonkey_software](http://en.wikipedia.org/wiki/Comparison_of_eDonkey_software)

The upcoming version will also have protocol obfuscation.

---

### Post by benevolent on 2007-08-27
Very helpful thread!!! thak you very much!!!!! i'm downloading now :)

---

### Post by mindtrick on 2007-08-28
Thaks for the guide Hallvor, you make us love linux

---

### Post by Hallvor on 2007-08-28
Thank you! :popcorn:

---

### Post by elinav on 2007-09-05
Hi,

Hope this is the right forum for this question - if not just ignore...

I installed Ubuntu on an old PC thinking to use it mainly for P2P. Installation went ok for aMule, but I cannot see any text. It is there (search for example brings up white-on-white text, and I can choose files for download which actually runs) but cannot be seen.

I would guess the problem is OS related, not application, since aMule probably uses default font colors. 

Any suggestions?

Doron

---

### Post by Hallvor on 2007-09-06
> **elinav said:**
> Hi,

Hope this is the right forum for this question - if not just ignore...

I installed Ubuntu on an old PC thinking to use it mainly for P2P. Installation went ok for aMule, but I cannot see any text. It is there (search for example brings up white-on-white text, and I can choose files for download which actually runs) but cannot be seen.

I would guess the problem is OS related, not application, since aMule probably uses default font colors. 

Any suggestions?

Doron

Never heard of that problem before. What version of Ubuntu are you using?

You could try changing the colours though GTK. But I have never done it before and can`t offer any other help than what I found here: 

[http://www.amule.org/wiki/index.php/Skins](http://www.amule.org/wiki/index.php/Skins)

Hope it works.

---

### Post by KCPokes on 2007-09-07
> **Hallvor said:**
> *Security*. Tick «Enable IP-filtering.» The purpose of using an IP-filter is to block the bad guys, mainly the entertainment industry and their lackeys, who are sabotaging the ed2k network. Clients on your ipfilter will not be able to establish a connection to your computer. I use the ipfilter from Bluetack, so you can insert this url [http://www.bluetack.co.uk/config/nipfilter.dat.gz](http://www.bluetack.co.uk/config/nipfilter.dat.gz) and then click «Update now». The ipfilter should then download and install. 


Nice HOW-TO. 

Just wanted to add a note, regarding a known issue, in case others are having issues with IP Security.  Essentially, it appears for some, the functionality just doesn't work.  You can read more about the bug at [https://bugs.launchpad.net/ubuntu/+source/amule/+bug/99917](https://bugs.launchpad.net/ubuntu/+source/amule/+bug/99917)

---

### Post by Hallvor on 2007-09-08
Thanks.  Updated.

It seems this bug is present in Feisty only. No problem in Dapper. Let`s hope everything will be OK in the upcoming aMule 2.2.0 version. The aMule developers are at least aware of the problem.

---

### Post by sledhead45 on 2007-09-14
very nice how-to. Much appreciated. Thanks,

--travis

---

### Post by Baby Boy on 2007-09-15
Explains a lot, very good howto. Thanks ;).

---

### Post by opossumjack on 2007-11-10
Very good guide!!! 
Thanks a  lot....

:)

---

### Post by linux noooob on 2007-11-22
ok so i did everything you said opened all the ports in my router and firewall *even others that other guides told me to open* but still my top arrow is red and my bottom one is yellow

HELP!

---

### Post by Hallvor on 2007-11-23
You will get a low id if your IP ends with a zero. If that is the case, wait until you get a new one. Also, use the serverlist from peerates.

Check that you not only have opened the ports in your router, but also that you have forwarded them correctly.

---

### Post by Tsume on 2007-11-24
I don't know if this belongs here or the aMule forum, so I posted in both.
(Original post [http://forum.amule.org/index.php?topic=13825.0](http://forum.amule.org/index.php?topic=13825.0) )

Okay, here's the deal.  I've gotten my eMule on Vista x64 running on the same ports on the same computer with the same IP address as aMule on my Linux Mint 4.0.  I've even taken the liberty of forwarding and opening the +3 UDP port that eMule doesn't use.

My problem:  In windows, with the same exact configuration, I get HighID on KAD and ED2K.

On Linux with aMule, however, I *ALWAYS* get LowID with KAD.  I could connect to a billion KAD sources and it's ALWAYS LowID "Firewalled".  I have protocol Obfuscation enabled and forced on both my Windows eMule and Linux aMule.

I've added the entries to IPTABLES just like this:
sudo iptables -A INPUT -p tcp --dport 64975 -j ACCEPT
sudo iptables -A INPUT -p udp --dport 64978 -j ACCEPT
sudo iptables -A INPUT -p udp --dport 55918 -j ACCEPT

Why oh WHY can I not achieve a HighID with KAD like I can on the same exact machine with (what I can see is) the same exact configuration in eMule?  I am using the latest aMule build for Gutsy posted on the aMule forum as of now.  I don't have anything like firestarter installed.

Thank you :)

---

### Post by c-m on 2007-11-25
I have opened the ports in i want to amule to use in my router and using firestarter but still i aways recieve a low id.

If i boot into windows and use the same ports i recieve a high id, so somewhere ubuntu must be blocking my ports. 

Can anyone help at all?

---

### Post by Hallvor on 2007-11-25
> **Tsume said:**
> 
On Linux with aMule, however, I *ALWAYS* get LowID with KAD.  I could connect to a billion KAD sources and it's ALWAYS LowID "Firewalled".  I have protocol Obfuscation enabled and forced on both my Windows eMule and Linux aMule.

I've added the entries to IPTABLES just like this:
sudo iptables -A INPUT -p tcp --dport 64975 -j ACCEPT
sudo iptables -A INPUT -p udp --dport 64978 -j ACCEPT
sudo iptables -A INPUT -p udp --dport 55918 -j ACCEPT


Kad needs a valid server and quite a few sources to bootstrap propely. You did not write if you also got a low ID on ED2K servers in aMule. If only KAD appears to be firewalled while you get a high ID on servers, I would not worry about it.

KAD does not support protocol obfuscation. This is only a feature for servers.

Read this:
[http://forum.emule-project.net/index.php?showtopic=48127](http://forum.emule-project.net/index.php?showtopic=48127)

Hope it helps!

---

### Post by myle on 2008-01-31
I have two problems:
First, Failed to download the server list from [http://peerates.net/peerates/certifiedservers.met](http://peerates.net/peerates/certifiedservers.met)
Second, I put manually a server (Razorback 3.1) and I can find a file I am looking for, but the download never starts.
I have already executed the commands about the firewall.
What's wrong?


I can download files via &#956;Torrent (I run wine-server) or FrostWire. The problem is that amule doesn't seem to work properly.

---

### Post by Hallvor on 2008-02-01
As long as you have a working server in your serverlist you should be fine. (Kad will also work in such a case.) As long as there are sources for the file the download will start sooner or later. Some users share thousands of files, so getting a chunk from them can take quite some time.

If you double click your file you have in your download list, you will get a list of sources and something called QR. QR means what rank you are in the other queue. Obviously a low number is best.

---

### Post by pagadama on 2008-02-02
&#51339;&#51008;&#51221;&#48372; &#44048;&#49324;&#54633;&#45768;&#45796; :)

---

### Post by GamingMazter on 2008-02-02
:D Thanks Matey :D

---

### Post by elinav on 2008-04-22
Took me a while - but finally figured out the solution:
Change the language - for me it was set to Hebrew. Once I set it to English, everything worked great.

Doron

---

### Post by fangorn on 2008-05-08
Hi,

I have problems getting ports accessible to normal user.

I am a user quite used to Linux, but this is the first Ubuntu machine I am using (have mainly Gentoo and Debian Machines running). 

The machine we are talking about is a dedicated router for a small home network. On it shall run aMule, a squid/frox proxy, and maybe later a email server. The squid proxy is working great. 

The problem is aMule, which is run by a normal user with as low as possible privileges. The amule ports are open in the firewall (rules have worked perfectly on the gentoo installation the new machine replaced). Test says port 4662 is accessible. But aMule run as normal user cannot access it!

Is there some kind of permission problem? What group does the amule user have to be part of to access network ports? I think amule needs exclusive access to the port, which is the problem. 

I hope someone can help me with this. 

Tnanks in advance,
fangorn

---

### Post by XanderNor on 2008-06-08
Hi,

Excellent post. Helped me a lot to set up amule, took me three days. Haha

I have one question. First some background info.

I run Mac OS X 10.4.10 and amule 2.0.3. I did not do any port forwarding or firewall disconnecting. But I have a stable connection. Green stripes on the earth thing on the lower, right side, 23 servers, and I can download things when I search for them. Don't know if my kad is working though.

The only reason I have amule is to download stuff from this side [www.verycd.com](www.verycd.com)
it&#8217;s in Chinese. I bought my Mac in Norway, and I know that other foreigners are able to download from this site. Read:  Can&#8217;t be a problem with the Chinese site. 

I am not really interested in the search function of amule. I want to use the ed2 links I find on this website [www.verycd.com](www.verycd.com) to paste into the ed2 link finder on amule, and start downloading. The only problem is I get this message after pasting in the ed2 link, and hitting the commit button.  Invalid ed2 link! Error: Not a ed2k &#8211; URI. 

For example this ed2 link didn&#8217;t work: 

ed2k://|file|[YYTvO]06.11.13_06&#36229;&#22899;·&#25105;&#30340;&#23547;&#26790;&#25925;&#20107;(4)&#21385;&#23068;·&#35768;&#39134;·&#21016;&#21147;&#25196;.rmvb|162480168|058b2eb3efab659dc7a34c247074907f|h=E7XL2JT7NBRDJXKMA63W7G3B2L4MMFKK|/

This is where I got the ed2k link from: [http://www.verycd.com/topics/114791/](http://www.verycd.com/topics/114791/)

What am I doing wrong? I pasted in the entire thing, and hit the commit button?

Thank you very much in advance. Would be really nice if somebody would take the time to answer this, even if this probably is a real newbie question. 

Btw: Verycd.com is a great site for finding not only Asian movies, but also European and American ones. Just type in the name of the movie you are looking for into the red barren in the middle of the site.

---

### Post by jjgomera on 2008-06-08
if you delete chinese letters, it may work:

ed2k://|file|[YYTvO]06.11.13_06.rmvb|162480168|058B2EB3EFAB659DC7A34C247074907F|/|/

dont your browser support ed2k protocol? I can click ed2k there and it add automatically to amule without problem

---

### Post by XanderNor on 2008-06-08
Hi jjgomera,

Thank you very much for your answer. It doesn&#8217;t work when I take away the Chinese characters. It says. Invalid ed2k link! Error: I&#8217;ll-formed hash. Any other suggestions?

Before I installed and got the current amule running, I had downloaded the 2.1.3 version (I am currently running the 2.0.3 version). Running the 2.1.3 version I was not able to connect to any client or download anything, but when I clicked on the things I wanted to download, they got automatically redirected to amule. They showed up in red, and nothing happened. This time I got amule up and running, but I somehow can&#8217;t make the ed2k links show up in amule. 

I would think my browser supports ed2k protocol, because as previously mentioned it used to show up/be automatically directed to amule? 

I would really appreciate any tips or help?

---

### Post by jjgomera on 2008-06-08
excuse me, for any reason this forums add a "space" if it dont use ```
, and really thats was the problem, dont the kanjis.
do this work?:

[code]ed2k://|file|[YYTvO]06.11.13_06&#36229;&#22899;·&#25105;&#30340;&#23547;&#26790;&#25925;&#20107;(4)&#21385;&#23068;·&#35768;&#39134;·&#21016;&#21147;&#25196;.rmvb|162480168|058B2EB3EFAB659DC7A34C247074907F|/|/
```


I dont know in mac, how amule bin locates, but in linux i think bin changed in version 2.1.3, from /usr/bin/amule to /usr/bin/ed2k to handle ed2k protocol.

Which browser do you use?

---

### Post by XanderNor on 2008-06-09
Hi,

thank you again for your help. I didn't help so, I think there was some mess up with the two versions I downloaded. I just deleted the old version, and re installed the version I had in the first place. I am sorry for creating such a mess.I have however made some progress.

I can now copy and paste ed2k links, and they show up in amule, which is great. But now I have one red and one green stripe on the globe, which means I can still not download the files I want to. amule also says kad off. I think I need to do some portforwarding right? 

Any help is greatly appreciated. Please ask if the information I give is not sufficient.


Btw: I have tried to do portforwarding, but I am not able to complete all the steps because it is written for emule. If I need to do any portforwarding please point me to a link, whick is suitable for amule. Thank you very much

---

### Post by Hallvor on 2008-06-09
> **XanderNor said:**
> Hi,

thank you again for your help. I didn't help so, I think there was some mess up with the two versions I downloaded. I just deleted the old version, and re installed the version I had in the first place. I am sorry for creating such a mess.I have however made some progress.

I can now copy and paste ed2k links, and they show up in amule, which is great. But now I have one red and one green stripe on the globe, which means I can still not download the files I want to. amule also says kad off. I think I need to do some portforwarding right? 

Any help is greatly appreciated. Please ask if the information I give is not sufficient.


Btw: I have tried to do portforwarding, but I am not able to complete all the steps because it is written for emule. If I need to do any portforwarding please point me to a link, whick is suitable for amule. Thank you very much

If you have a green arrow and Kad is off, you are connected with a high id to the ed2k servers. To activate Kad, click on Kad in "Networks" in the main menu, and click on the button called "Bootstrap from known clients". The red arrow should now turn yellow and then green. If you have two green arrows, all is well.

Btw: The new aMule 2.2.1 is going to be released this wednesday.

---

### Post by XanderNor on 2008-06-09
Hi Hallvor,

thank you very much it acutally helped. The stripe turned from red to yellow, and it says I am still firewalled. I looked through the forums, and found this written by you:

It is probably because KAD needs to bootstrap properly. This means that KAD needs to find enough sources from the eD2k network to run optimally. Just put a few popular files on your download list, and the light should turn green in a while.

Is this what I need to do? Any help is appreciated.

Btw: The stripe justed turned red again. I will not download the new version, if I can get the current one up and running.

---

### Post by Hallvor on 2008-06-10
> **XanderNor said:**
> Hi Hallvor,

thank you very much it acutally helped. The stripe turned from red to yellow, and it says I am still firewalled. I looked through the forums, and found this written by you:

It is probably because KAD needs to bootstrap properly. This means that KAD needs to find enough sources from the eD2k network to run optimally. Just put a few popular files on your download list, and the light should turn green in a while.

Is this what I need to do? Any help is appreciated.

Btw: The stripe justed turned red again. I will not download the new version, if I can get the current one up and running.

Hello again!

If KAD turns yellow, it could be that your router is remapping the outgoing UDP port:

[http://www.amule.org/wiki/index.php/FAQ_eD2k-Kademlia#Why_does_Kademlia_still_say_it_is_.22firewalled.3F.22](http://www.amule.org/wiki/index.php/FAQ_eD2k-Kademlia#Why_does_Kademlia_still_say_it_is_.22firewalled.3F.22)

Kad also turns yellow if it can`t find enough sources from the ed2k network to bootstrap properly. Try to download a popular file and press "bootstrap from known sources" again. If not, check your router. I`m afraid I can`t help you with router problems, but you could always ask dr. Google for help on that. :)

---

### Post by XanderNor on 2008-06-10
Hi,

thank you. At least it works, and I download with 10kbs. I will wait till I get out of China, which is going to be in 2 weeks, and see if I connect my Mac back in Europa if there are going to be any changes. I will try looking up the stuff on the internett, but its not very Mac specific.

Thank you two guys very much!

---

### Post by actarus000 on 2008-08-05
Hi,

Very useful thread, thanks.
I think this is a stupid question but I'll ask it anyway.

You say that the upload limit should be set at 60% to 80% of capacity. Amule (by default on my machine) shows 3ko/s UL capacity and 0ko/s limit (the 0 limit looks suspect because loads of users are uploading my files at rates obviously higher than 0).
So, is my UL capacity really just 3ko/s ? And should I change my limit to 80% of that, ie 2ko/s (rounded).

---

### Post by Hallvor on 2008-08-06
> **actarus000 said:**
> Hi,

Very useful thread, thanks.
I think this is a stupid question but I'll ask it anyway.

You say that the upload limit should be set at 60% to 80% of capacity. Amule (by default on my machine) shows 3ko/s UL capacity and 0ko/s limit (the 0 limit looks suspect because loads of users are uploading my files at rates obviously higher than 0).
So, is my UL capacity really just 3ko/s ? And should I change my limit to 80% of that, ie 2ko/s (rounded).

I`m not in front of aMule now, but I think the UL/DL *capacity* settings are just for statistics. Don`t even bother changing them. There are several places on the internet where you can [test your upload speed]("http://www.google.no/search?hl=no&q=internet+test+upload+speed&meta="). Your upload speed should be much higher than 3 kB/s. A different way to do it is to set upload speed to unlimited and see how fast data can be transfered; when you have the numbers, then reduce to 60-80% of that.

---

### Post by thynamite on 2008-10-21
Hi all,
  Thanks for the excellent tutorial.  I have recently update to intrepid and aMule v2.2.1.
  Now aMule no long able to handle ED2K links with foreign characters from firefox.
  Here is an example:
```
ed2k://|file|%E5%91%A8%E6%9D%B0%E4%BC%A6.-.%5B%E9%AD%94%E6%9D%B0%E5%BA%A7%5D.%E4%B8%93%E8%BE%91.%28MP3%29.rar|100041658|a86f1cf829ce6ab5ff100119c18fb74c|h=V4IUD2M5QR5PTGZF6T7TJADNNYDNKXAT|/
```

  You could also retrieve link from link - [http://www.verycd.com/topics/405249/](http://www.verycd.com/topics/405249/).

  I really appreciate your help!  Thanks.

Andy

---

### Post by Jota37 on 2008-11-30
Thanks a lot for the great tutorial.

I also have noticed that the link to the server list mentioned is not working. Going to peerates.net, I found this working link:
[http://peerates.net/servers.php]("http://peerates.net/servers.php")

It does then download the list of servers.

---

### Post by johnlocke2342 on 2009-01-11
Hi.
Ihad low ID issues, so I followed your tutorial to get rid of these. I don't know what I did, but since I finished, it doesn't download anything, and doesn't connect either.
If you can help me...

---

### Post by Hallvor on 2009-01-12
> **johnlocke2342 said:**
> Hi.
Ihad low ID issues, so I followed your tutorial to get rid of these. I don't know what I did, but since I finished, it doesn't download anything, and doesn't connect either.
If you can help me...

That is just weird.

Perhaps it is this issue: [http://www.amule.org/amule/index.php?topic=16037.0](http://www.amule.org/amule/index.php?topic=16037.0)

---

