---
title: "HOWTO: Share updates across multiple machines"
date: 2007-09-30
forum: Outdated Tutorials &amp; Tips
---

### Post by coolen on 2007-09-30
**NOTE:**
Apt-cacher does not seem to work with Lucid. This guide now use apt-cacher-ng. If you followed this guide before and are having troubles on Lucid, then run the following two commands:
```
sudo apt-get remove apt-cacher
sudo apt-get install apt-cacher-ng
```
If you have any troubles, check that configuration files are present and correct. They should remain intact, but you never know.



So, you have Ubuntu, you love Ubuntu, and you've spread the love throughout your home. Perhaps you have a few family members using it happily, or maybe you simply enjoy having a different computer in every room of the house.

Whatever the reason, you have multiple machines running this fine operating system. One problem, though: all those updates! You love getting upgraded software, but having to download it so many times really eats away at your bandwidth.

Luckily for you, you're using open source software. You're not alone in this concern, and a solution already exists.

This guide will get you setup with apt-cacher, a tool that caches Debian package files for your home network. When one of your machines requests a package, apt-cacher will check to see if it has it, and if it does, send it back to the client without downloading a single byte. If not, then it goes to the repository and grabs the package, streaming it back to the client as it does, and keeps it for future use.

Things to note:
1. A repository needn't be specified on the server machine for a client to access it. The server acts as a proxy which keeps a copy for itself.
2. This is not Ubuntu-specific. Any Debian-based distro should be able to act as both a server and a client, although you may have to adapt some of the steps for yourself.


**Part Zero: The Formalities**
This has been confirmed as working on very diverse networks, with machines running different distros (not merely Ubuntu derivative) with very different architectures. I've tested this myself on versions up to, but not including, Lucid. The use of apt-cacher-ng yields similar results according to other users.

Information for this guide was gathered primarily from the apt-cacher man page. I consulted this article ([http://www.linuxjournal.com/article/1058](http://www.linuxjournal.com/article/1058)) for help with inetd. It's rather dated, but quite useful.

Thanks to the following users:
omegamormegil, for providing a much easier method of redirecting APT.
bugmenot_user, for figuring out how to clean the regular APT cache.
mssever, for providing the workaround for upgrades.
Skip Da Shu, for being generally awesome and providing a lot of testing.


**Part One: The Server**
You'll need to select a server for this setup. It should have a fair bit of space to spare, particularly if the client machines belong to an eclectic group. For those with more advanced partitioning schemes, the cache is kept in /var/cache/apt-cacher by default, but this can be changed.

To get the ball rolling, we install the software in question:
```
sudo apt-get install apt-cacher-ng
```
With it successfully installed, we have to tell it how to start. There are two options for this. You can have it run in daemon mode (always on), or you can get inetd, which is a program to launch server applications on request. The obvious advantage is that you save memory and CPU power, but CPU usage will spike on startup when using inetd, and you may experience a delay.

If you're expecting a lot of traffic, go with the daemon mode. If you're a home user, chances are you'll want to go with inetd.

_Daemon Mode_
This is really quite easy. First, we'll need to edit our services file:
```
sudo nano /etc/services
```
The following lines can go anywhere really, but the end of the file is convenient, particularly if you're planning to have many services running from this machine:
```
apt-cacher           3142/tcp
apt-cacher           3142/udp
```
3142 is the default port. I see no reason to change it, but if you have one, you may. If so, you'll need to change the daemon_port option in /etc/apt-cacher/apt-cacher.conf

One more file to edit:
```
sudo nano /etc/default/apt-cacher
```
Set AUTOSTART to 1 to get the daemon to launch at boot time.

To launch it now, simply type the following:
```
sudo /etc/init.d/apt-cacher start
```
Now, we're all done for the server side of things. Skip down to Part Two :)

_Inetd Mode_
To kick things off, we'll need to install the service:
```
sudo apt-get install inetutils-inetd
```
Next, we edit a couple of files:
```
sudo nano /etc/services
```
Add these two lines to the end of the file:
```
apt-cacher           3142/tcp
apt-cacher           3142/udp
```
Now, we have to setup inetd:
```
sudo nano /etc/inetd.conf
```
Add this line:
```
apt-cacher stream tcp nowait www-data /usr/sbin/tcpd /usr/sbin/apt-cacher -i
```
Now, restart the inetd server:
```
sudo /etc/init.d/inetutils-inetd restart
```
You're done!


**Part Two: The Client**
To use apt-cacher, your clients need to redirect their requests to the server machine. APT has its own proxy configuration. Thanks to omegamormegil for this tip :)
Type the following in a terminal:
```
echo 'Acquire::http::Proxy "http://hostname:3142";' | sudo tee /etc/apt/apt.conf.d/01proxy
```
Where hostname is a valid identifier for your server (for home users, an IP address will probably be convenient).

For laptop users, this means that you'll be unable to update using this method while on the road (unless you have a global route to your server, although the speed will be greatly reduced). To switch back to direct updates, type the following command:
```
echo 'Acquire::http::Proxy "http://";' | sudo tee /etc/apt/apt.conf.d/01proxy
```
Then once you get home, the command given above will get you using shared updates again.

If you prefer, APT will look for the last line in the file. You can cut/paste them as needed, but the above commands can be easily written into a script to automate the process for you.

From ace214, the following command will tell apt-get to use direct fetching methods:
```
export http_proxy=http://
```
As far as I know, this will only work for apt-get until you end your session (by logging out, or exiting/closing the terminal). If you're not tied to the GUI, this may serve as a useful solution for you.

Now, update!
```
sudo apt-get update
```
If all goes well, you should download packages as usual. Try downloading some software, or getting some updates. It should work pretty much as before.

If you are upgrading, these steps *will not work*. This appears to be a bug in Update Manager.

To upgrade, you must edit the 01proxy file to use direct updates as described above. Now, run the following command:
```
sudo sed --in-place s_http://_http://hostname:3142/_ /etc/apt/sources.list
```
The syntax may seem a little daunting, but this simply replaces any occurance of http:// with ht****tp://hostname:3142/. Once again, hostname must be a valid identifier for your server.

Upgrades should now work normally through the Update Manager. Once you've finished the upgrade, run the following command:
```
sudo sed --in-place s_http://hostname:3142/_http://_ /etc/apt/sources.list
```
Now edit the 01proxy file to set yourself to shared updates as described above.

So far, this is the only workaround I know of. I apologise to anyone who may have suffered this bug. Once more, thank you mssever for bringing this to my attention and providing a fix.


**Part Three: The Transition**
Chances are your server's up to date,and has a fair package cache of its own. Why duplicate all of this fine work? Apt-cacher comes with a migration helper for pre-caching. Type the following in a terminal to copy your cache over:
```
sudo cp /var/cache/apt/archives/*.deb /var/cache/apt-cacher/import
sudo /usr/share/apt-cacher/apt-cacher-import.pl
```

At the moment, the server machine itself will go downloading its own packages, rather than reusing those in the cache. To fix this, use the same proxy setup as used above on the clients, using "localhost" as the hostname.

The final step is optional, but it will help you free up space. The server is currently maintaining two caches: the regular apt one, and the shared cache.

NOTE: If you omit this step, APT will keep building its own cache. This may be of benefit to you when you uninstall apt-cacher if have limited bandwidth, but APT's operation will not be affected.

If your server uses Synaptic at all, there's an option under Settings -> Preferences -> Files to delete packages after installation. Thanks to Skip Da Shu for pointing this out to me.

This will only apply (in Ubuntu and Xubuntu) to packages fetched through the GUI. It will not work in Kubuntu, and will not work from the command line. For a more universal solution, enter the following command:
```
echo 'DPkg::Post-Invoke {"/bin/rm -f /var/cache/apt/archives/*.deb || true";};' | sudo tee /etc/apt/apt.conf.d/clean
```
This command is carried out just before APT quits, and will clean the cache of any .deb files. Thanks to bugmenot_user for this command.


**Part Four: The Removal**
To undo the changes made in this guide, you must remove the proxy configuration lines. You must also remove the file /etc/apt/apt.conf.d/clean, or set the option in Synaptic back to its original value.

Purging inetutils-inetd, inetutils-tcpd, and apt-cacher-ng will undo most of the remaining changes. Remove the two lines from the end of /etc/services, and your system should be back to the way it was.

---

### Post by omegamormegil on 2007-10-25
Thanks for the info!  I have apt-cacher running on my network, now.  I figured out how to use a http proxy to make the clients update through the apt-cacher server, which might be easier than editing the sources.list file.  It is MUCH easier, IMO, if you are on a laptop.  I added the method I'm using to the end of this page: 

[https://help.ubuntu.com/community/Apt-Cacher-Server](https://help.ubuntu.com/community/Apt-Cacher-Server)

Hope it's helpful!

---

### Post by coolen on 2007-10-25
Thanks for that. Does seem easier, especially when you've got multiple sources files.

---

### Post by coolen on 2007-10-28
Seems that your method runs a fair bit faster, too.

---

### Post by bryceman on 2007-11-06
Wait, which was faster? The inetd proxy or the linked apache2 proxy?

---

### Post by spockrock on 2007-11-07
Ok sorry now if I put apt-cacher on my 'server' and then use a proxy for all my desktop clients, does this mean only cached packages are downloaded on the clients??

---

### Post by coolen on 2007-11-07
To bryceman, I haven't tried the apache2 method, I'm afraid. I don't currently have any need for a web server, and it seems more straightforward to me to set this up on its own. I'll add it in the future for those interested, or if anyone's interested in contributing, I can get it up sooner.
When I mentioned that in the post, I was referring to the old proxy method, in which you had to edit each line of your sources list. My download speeds were generally about 10-20% of the speed of a direct download, and are usually running pretty close to normal speeds using APT's proxy configuration.

To spockrock, this does not in any way limit your experience. You can still download any package you want, from any repository you want. Once you have this set up, you shouldn't need to think about it unless you're on a laptop moving between networks.
What happens is that the request goes to the server machine, where the apt-cacher service will pick it up. It'll download the package, streaming a copy of it to you (the client), and keeping one for itself. If another client requests the same package, the service will simply send them a copy of the cached package.

---

### Post by spockrock on 2007-11-07
ok cool so its fine then the servers sources.lst and clients sources.lst files are different, as well if the client upgrades or installs a package the server machine will then use the cached package as well right?

---

### Post by coolen on 2007-11-07
Yep. The next time the server requests the new package (uhh, from itself), it'll send itself the cached one without touching the 'net.

---

### Post by onegreenparker on 2008-01-29
All sounds good, but will this work if the server is running 6.06 and the desktops are running anything later?

---

### Post by coolen on 2008-01-29
You may have some trouble if your server uses the localhost method, but if not, I don't see that it'd cause any troubles.

I'll look into it and get back to you.

---

### Post by phynix on 2008-04-20
Is there anyway you can force cacher to automatically update them before you need them? For instance I have one computer that is 64 and another that is 32. Since it only updates when you need them, there is really no point. I would like the server to fetch the packages before I need them. Is that possible?

---

### Post by coolen on 2008-04-20
I'm not sure how apt-cacher would be useful in this case. The only way it would save you anything would be for no-arch packages (which, in the case of games, can actually represent the largest download), but either way, you're only saving yourself some time when you go to do the upgrade on the first client machine.

One solution would be pre-caching. If you place any package in /var/cache/apt-cacher/import and run
```
sudo /usr/share/apt-cacher/apt-cacher-import.pl
```
your packages will be available for direct dtreaming to clients.

As it is, I believe apt-cacher will onloy respond to requests from clients to actually fetch packages itself. If you're just looking to make the process more automatic, you could set the upgrade process to run daily.

---

### Post by phynix on 2008-04-21
Let me try to be more clear and see if it changes your answer. Lets say I only have on machine. I want the "server" to fetch the downloads ahead of time so that when my computer updates it uses those updates? Does that make more sense?

---

### Post by coolen on 2008-04-27
> **phynix said:**
> Let me try to be more clear and see if it changes your answer. Lets say I only have on machine. I want the "server" to fetch the downloads ahead of time so that when my computer updates it uses those updates? Does that make more sense?

Yeah, I got what you were asking. Apt-cacher cannot do this.

However, I do have a solution for you. It lies in APT itself.

```
sudo apt-get -d update
```

The -d tells it to fetch packages only. You may now optionally clear the cache as above, or do both with this command:

```
sudo apt-get -d update && sudo apt-get clean
```

I just tried this out, and it seems to be working.

---

### Post by coolen on 2008-04-27
> **onegreenparker said:**
> All sounds good, but will this work if the server is running 6.06 and the desktops are running anything later?

Wow, sorry I let this go. Life kind of caught up with me.

Anyway, I can now confirm that it works with different versions of Ubuntu. I have my server running Hardy, and my brother's desktop on Gutsy.

Apt-cacher should keep meta-information on different packages and should be able to deliver the requested version without conflict.

You probably either discovered this yourself or gave up. My bad. Anyway, it works, as far as I know.

---

### Post by phynix on 2008-04-28
Thanks, I don't know why i didn't think of that haha. Wow. Next question is can you make apt download packagaes not made for the architecture.

---

### Post by stanna on 2008-04-29
i just have a quick question before i do this. with very tight australian broadband access (completly homo). 

I have my computers here with ubuntu, setup to download from my ISP's ubuntu mirror as to not add the downloads to my monthly quota.. just curious as to where i would put my custom server.list settings, be it the normal /etc/apt/sources.list or somewhere with the apt-cacher?

just want to get a better understanding of this before i proceed, as i want my server to use this caching method along with the other 5 pcs i have here using various flavours of ubuntu.

cheers., (hope i make sense)

---

### Post by coolen on 2008-04-30
> **stanna said:**
> i just have a quick question before i do this. with very tight australian broadband access (completly homo). 

I have my computers here with ubuntu, setup to download from my ISP's ubuntu mirror as to not add the downloads to my monthly quota.. just curious as to where i would put my custom server.list settings, be it the normal /etc/apt/sources.list or somewhere with the apt-cacher?

just want to get a better understanding of this before i proceed, as i want my server to use this caching method along with the other 5 pcs i have here using various flavours of ubuntu.

cheers., (hope i make sense)

Hey, a fellow Aussie :)

If you mean the settings to use apt-cacher, they go in /etc/apt/apt.conf.d/01proxy

Simply add the line I mentioned in the post (with the appropriate hostname value) and APT will do the right thing from then on for all repositories.

I hope that answers your question.

---

### Post by stanna on 2008-04-30
so just to clarrigy, if im using internode mirror for my updates

```
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ gutsy universe main restricted multiverse
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ gutsy-updates universe main restricted multiverse
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ gutsy-proposed universe main restricted multiverse
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ gutsy-backports universe main restricted multiverse

deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ gutsy universe main restricted multiverse
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ gutsy-updates universe main restricted multiverse
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ gutsy-proposed universe main restricted multiverse
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ gutsy-backports universe main restricted multiverse

```

do i put that exact text into 01proxy file?

sorry to get you to basicly do it for me, im just very unsure of how all this works.. little slow :(

..and yes good old aussie. im a melbournite!! ;)  :guitar:

---

### Post by coolen on 2008-04-30
It's all in the howto. The line you need is this:

```
Acquire::http::Proxy "http://hostname:3142";
```

This instructs APT to use the proxy method through your server, and this will automatically apply to all requests.

I'm Waley Scum, I'm afraid ^_^

---

### Post by stanna on 2008-04-30
so its safe to assume its

Acquire::http::Proxy "http://mirror.internode.on.net/pub/:3142";

sorry you have to dumb it down soo much. but im trying soo hard lol. still quite new to all this and i feel this is a great opportunity to get something fun under my belt, even tho i have 5 pcs here runing different ubuntu's.. i still love it, soo much more satisfying when things work than with windows (which i fix all day).

---

### Post by coolen on 2008-04-30
Sorry, I misunderstood what you were trying to do.

Apt-cacher will not be able to do what you're trying to do unless the servers you're using have apt-cacher. Apt-cacher is a third-party service, so this is unlikely.

The setup here is done entirely on your own network. For example, in your case, it would mean that any packages common to all your PCs would be downloaded from the internet only once, and then any other machines that request it would get a copy direct from your chosen server machine.

To use the internode mirrors, you would need to put them in /etc/apt/sources.list

It may be possible to instruct APT to always look for those mirrors, but unofficial repositories (such as Medibuntu) would be a problem. I'll play around a bit and see if I can get that working, if that's what you want to do. If not, apt-cacher could still save you a fair bit of bandwidth, especially with 5 machines.

Don't worry about being new. We've all been there. Once you get into that mode of thinking, things make a lot more sense, and in doing so, you learn a lot. When I first started using Linux (Debian, four years ago) I spent hours looking through man pages and configuration files. It took me a week to match my screen resolution to my desktop size. It was fantastic.

---

### Post by coolen on 2008-05-01
I've looked into your problem a bit more.

Turns out it's ludicrously easy to set up APT to use the internode mirrors. System -> Administration -> Software Sources -> Download From -> Other...

Select Internode from that list.

Never occured to me to try the GUI way ^_^. I sometimes forget that Ubuntu is easy to use for the administrative stuff, too.

That should work for your official repos (Main, Restricted, Universe, and Multiverse). Not sure if it'll work for Security and Backports, but it's likely.

Anyway, if you're still interested, apt-cacher could save you bandwidth on third-party repos.

---

### Post by stanna on 2008-05-01
thanks coolen, i appreciate you going to the ultimate effort and giving it to me on a silver platter. i hope i have some time over the weekend to implement it..

cheers... ill come back and post if it works ;)

---

### Post by coolen on 2008-05-02
I just wish I hadn't spent so much time looking for the stone platter :P

Good luck in your endeavours. I hope this can help you in some way.

---

### Post by mssever on 2008-05-08
Thanks for this HOWTO. It should enable me to upgrade to Hardy without exceeding my bandwidth limit.

---

### Post by coolen on 2008-05-09
Glad to hear it ^_^

I've not upgraded using this method, although I maintain a Hardy and Gutsy machine using the same cache without issue. I see no reason why it shouldn't work, but if you do run into trouble, let me know.

---

### Post by Skip Da Shu on 2008-05-09
> **coolen said:**
> Wow, sorry I let this go. Life kind of caught up with me.

Anyway, I can now confirm that it works with different versions of Ubuntu. I have my server running Hardy, and my brother's desktop on Gutsy.

Apt-cacher should keep meta-information on different packages and should be able to deliver the requested version without conflict.

You probably either discovered this yourself or gave up. My bad. Anyway, it works, as far as I know.

Ditto, server is v8.04 64b Xubuntu, 1 client is(was) Xubuntu v7.10 32b (now 64b), 1 client v7.10 64b Xubuntu, 5 clients v8.04 64b Xubuntu, 1 client v8.04 64b (was 32b) Ubuntu.  Generally all working fine... fixin to post one warning error question.  Most on Gigabit LAN so the client "download" of HIT packages... well don't blink.

This is SOOOO much nicer than mucking about with the sources.list files.

---

### Post by Skip Da Shu on 2008-05-09
> **coolen said:**
> I've looked into your problem a bit more.

Turns out it's ludicrously easy to set up APT to use the internode mirrors. System -> Administration -> Software Sources -> Download From -> Other...

Select Internode from that list.

Never occured to me to try the GUI way ^_^. I sometimes forget that Ubuntu is easy to use for the administrative stuff, too.

That should work for your official repos (Main, Restricted, Universe, and Multiverse). Not sure if it'll work for Security and Backports, but it's likely.

Anyway, if you're still interested, apt-cacher could save you bandwidth on third-party repos.

Hmmmm... what I was thinking he'd want to do is to set the 01proxy on his CLIENTS ONLY to point to his apt-cache server (192.168.xxx.xxx:3142) and then point the apt-cache server to the internode thingie in sources.list as he has... but maybe as you describe above on but... on the SERVER ONLY.

Make any sense or am I missing the point?

PS: Hmmm guess it doesn't make any difference if the clients point to internode or not as long as they are proxied back to the server... never mind.

---

### Post by Skip Da Shu on 2008-05-09
Coolen,  First off excellent "how-to".  I had apt-cacher running when my machines were all v7.10 from a how-to on another site.  Went thru yours the other night and modified mine to the proxy method. MUCH nicer!

I really have two questions but I'll make two posts out of them so as not to muddy the waters.

Simple one first.

This is in my /var/log/apt-cacher file... I'm only posting the last few lines.  This was present back when I had the modified sources.list method and now with the proxy method (I deleted my log and access files when I changed to proxy method the other night).  I am assuming it is complaining that it's running in deamon mode.  I realize it's only a "warning" but I don't know why it's posting it all the time and don't know what to change to make it go away.  Any suggestions?


```
Fri May  9 07:45:09 2008|INETD|info [17141]: Warning: no running inetd server found
Fri May  9 07:45:09 2008|INETD|info [17143]: Warning: no running inetd server found
Fri May  9 07:45:10 2008|INETD|info [17146]: Warning: no running inetd server found
Fri May  9 07:45:11 2008|INETD|info [17149]: Warning: no running inetd server found
Fri May  9 07:45:12 2008|INETD|info [17152]: Warning: no running inetd server found
Fri May  9 07:45:13 2008|INETD|info [17154]: Warning: no running inetd server found
Fri May  9 07:45:14 2008|INETD|info [17157]: Warning: no running inetd server found
Fri May  9 07:45:14 2008|INETD|info [17160]: Warning: no running inetd server found
Fri May  9 07:45:15 2008|INETD|info [17163]: Warning: no running inetd server found
Fri May  9 07:45:16 2008|INETD|info [17165]: Warning: no running inetd server found
Fri May  9 07:45:16 2008|INETD|info [17167]: Warning: no running inetd server found
Fri May  9 07:45:17 2008|INETD|info [17169]: Warning: no running inetd server found
Fri May  9 07:45:17 2008|INETD|info [17171]: Warning: no running inetd server found
Fri May  9 07:45:18 2008|INETD|info [17173]: Warning: no running inetd server found
Fri May  9 07:45:18 2008|INETD|info [17175]: Warning: no running inetd server found
Fri May  9 07:45:19 2008|INETD|info [17177]: Warning: no running inetd server found
```

---

### Post by Skip Da Shu on 2008-05-09
The 2nd question...

In the 'how-to' you talk about "running apt-get clean" from a scheduler on the server (only?).  On my apt-cacher server (does run 24/7 as do most of the clients) I set this up to run twice a day (probably overkill) in CRON.

While mucking about with this I looked at some of the clients /var/cache/apt/archives directory to see if they were empty before and after running update-manager... I got a bit confused about when /var/cache/apt/archive will load up with packages and when it will not.  

So just now I'm back on a v8.04 Xubuntu   machine (c26).  I checked the /var/cache/apt/archives - nothing there - run update manager - 1 package to update - runs and updates.  Back to c26's /var/cache/apt/archives.  There sits "foomatic filters" package.  Back on c20 (the apt-cacher server) we have this in it's access log:
```
Fri May  9 10:21:12 2008|192.168.218.26|HIT|135864|foomatic-filters_3.0.2-20071204-0ubuntu2.1_all.deb
```

OK, this is what I had expected to happen.  C26's apt asks for foomatic, c20 got the request, had it in it's apt-cacher cache, sent it back to apt on c26 who stored it in it's cache. 

What I think this implies is that I really need to schedule "apt-get clean" on ALL the machines, not just the server.  Do you agree or did I miss a step to stop the client's 'apt-get' from doing local caching?

Thanx, Skip

PS: Uh... duh... maybe check "Delete downloaded packages after installation in Synaptic" in Settings -> Preferences -> Files tab?  So why not do this on client and server?  Wouldn't this eliminate the need for any scheduled "apt-get clean"?

---

### Post by mssever on 2008-05-09
> **Skip Da Shu said:**
> This was present back when I had the modified sources.list method and now with the proxy method (I deleted my log and access files when I changed to proxy method the other night).  I am assuming it is complaining that it's running in deamon mode.  I realize it's only a "warning" but I don't know why it's posting it all the time and don't know what to change to make it go away.  Any suggestions?
Have you checked your apt-cacher config? I'm running as a daemon and don't get those messages. Note that I don't use inetd; I run xinetd instead.
> **Skip Da Shu said:**
> What I think this implies is that I really need to schedule "apt-get clean" on ALL the machines, not just the server.  Do you agree or did I miss a step to stop the client's 'apt-get' from doing local caching?

Yes, you'll need to configure each client. Scheduling apt-get clean is certainly a fine way to do it. If you want to alter your APT config, it appears tat you can do that, as well. [quote=man apt.conf]Dir::Cache contains locations pertaining to local cache information, such as the two package       caches srcpkgcache and pkgcache as well as the location to place downloaded archives,       Dir::Cache::archives. Generation of caches can be turned off by setting their names to be       blank. This will slow down startup but save disk space. It is probably prefered to turn off       the pkgcache rather than the srcpkgcache. Like Dir::State the default directory is contained       in Dir::Cache[/quote]

---

### Post by Skip Da Shu on 2008-05-09
> **mssever said:**
> Have you checked your apt-cacher config? I'm running as a daemon and don't get those messages. Note that I don't use inetd; I run xinetd instead.


Yes, you'll need to configure each client. Scheduling apt-get clean is certainly a fine way to do it. If you want to alter your APT config, it appears tat you can do that, as well.

On the first... Ignorance... I don't know what either of these are and I think I'm running "stand alone" daemon mode.  What should I be looking for.  My apt-cacher.conf consists of:

```
cache_dir=/mnt/netshare2/apt-cacher
admin_email=skipatskipsjunkdotnet 
group=root
user=root
allowed_hosts=192.168.xxx.xxx-192.168.xxx.xxx, 127.0.1.1
denied_hosts=
generate_reports=1
clean_cache=1
offline_mode=0
logdir=/var/log/apt-cacher
expire_hours=0
use_proxy=0
http_proxy_auth=proxyuser:proxypass
use_proxy_auth=0
limit=0
debug=0
```


On the 2nd... I must have been adding my PS: about the time you responded.  For some reason right now I can't find apt.conf... what/where is the apt config file at?  

However, I'll guess the check box I referred to in my PS: does the same. ??

---

### Post by coolen on 2008-05-09
Ignore the original version of this comment. I didn't see that there was a fourth page *headdesk*

Anyway, in response to your first question, I'm not sure why it's expecting inetd to be running. The only thing I can think of is that something in your configuration file is telling it to expect inetd to wake it, although I see nothing there. What's in /etc/default/apt-cacher?

In response to your first question, I only directed people to schedule a cache clean on the server since I think the cache is generally a good idea. It's part of the "APT way", I guess you could say. If you take your laptop away from your network, for example, it would be good to have your cache still intact, but the server is unlikely to ever become disconnected from itself, and so will always have access to the server cache. For the sake of space, it's one or the other.

As for the option in Synaptic, well, I didn't know it existed. I do most of my specific APT work from the command line: I'll use Add/Remove to browse programs available, and Synaptic if I'm looking for specific packages I don't know the name of. Thanks for the tip. I'll add it as soon as I find the configuration file option. I'm getting errors using the method mentioned above.

---

### Post by mssever on 2008-05-09
> **Skip Da Shu said:**
> For some reason right now I can't find apt.conf... what/where is the apt config file at?
/etc/apt/apt.conf doesn't exist by default. But you can drop files in /etc/apt/apt.conf.d for the same effect.

---

### Post by Skip Da Shu on 2008-05-09
> **coolen said:**
> Ignore the original version of this comment. I didn't see that there was a fourth page *headdesk*Huh? 

> 
Anyway, in response to your first question, I'm not sure why it's expecting inetd to be running. The only thing I can think of is that something in your configuration file is telling it to expect inetd to wake it, although I see nothing there. What's in /etc/default/apt-cacher?

My /etc/default/apt-cacher only has the autostart turned on.  The entire file:
```
# apt-cacher startup configuration file
# IMPORTANT: check the apt-cacher.conf file before using apt-cacher as daemon.

# set to 1 to start the daemon at boot time
AUTOSTART=1

# extra settings to override the ones in apt-cacher.conf
# EXTRAOPT=" daemon_port=3142 limit=30 "
```

There is a file, /etc/apt-cacher/apache.conf.  I've never touched it and don't know what it's for.  What does this do?  Here it is:
```

Alias /apt-cacher /usr/share/apt-cacher/apt-cacher.pl

<DirectoryMatch /usr/share/apt-cacher/>
	Options ExecCGI
	AddHandler cgi-script .pl
	AllowOverride None
	order allow,deny
	allow from all
</DirectoryMatch>
```


> 
In response to your first question, I only directed people to schedule a cache clean on the server since I think the cache is generally a good idea. It's part of the "APT way", I guess you could say. If you take your laptop away from your network, for example, it would be good to have your cache still intact, but the server is unlikely to ever become disconnected from itself, and so will always have access to the server cache. For the sake of space, it's one or the other.

Oh yea, never thought about laptops and machines that might move.  Good point.  These things of mine tend to sit there until they become "replaceble", get taken apart, sold or become somebody's desktop upgrade and a new one comes it to take it's place.  

Anywho... I took the root CRON entries off of ALL the machines.  I wanna see if the Synaptic thing does what I think it's telling me it'll do.  That would be the simplest for me.  I'll keep in mind to not do this for anything portable (The wife's eeePC is still running Xandros and, btw, I guess they don't believe in updates.  Bought it in February and only 1 BIOS update has showed up.  The BIOS update will not apply anyway :-(  Thinking of converting it to Xubuntu).  

>  As for the option in Synaptic, well, I didn't know it existed. I do most of my specific APT work from the command line: I'll use Add/Remove to browse programs available, and Synaptic if I'm looking for specific packages I don't know the name of. Thanks for the tip. I'll add it as soon as I find the configuration file option. I'm getting errors using the method mentioned above. I didn't know about it until last night.

What "method mentioned above" is giving you errors?

PS: Got me wondering now if this thing could cache and handle Xandros packages also... oh wait, they don't do updates except annually.

---

### Post by mssever on 2008-05-10
> **Skip Da Shu said:**
> There is a file, /etc/apt-cacher/apache.conf.  I've never touched it and don't know what it's for.  What does this do?It appears to be Apache config in case you want to run apt-cacher as a CGI. 

> PS: Got me wondering now if this thing could cache and handle Xandros packages also... oh wait, they don't do updates except annually.
If Xandros uses APT, then this would probably work. That way, you'll be ready for their annual updates. :)

---

### Post by Skip Da Shu on 2008-05-10
> **mssever said:**
> It appears to be Apache config in case you want to run apt-cacher as a CGI. 


If Xandros uses APT, then this would probably work. That way, you'll be ready for their annual updates. :)

So nothing to do with my messages:
```
Fri May  9 07:45:19 2008|INETD|info [17177]: Warning: no running inetd server found

```

Can I deleted the file then?

---

### Post by coolen on 2008-05-10
The method mentioned above was leaving Dir::Cache variables blank. Every apt-get from then on complained about a missing partial/ directory. The only other solution I found was to tell APT to clean the cache as part of it's post-upgrade, but this failed since there was still a lock on the process.

I'm looking for a solution everyone can use, but for now, I've put the Synaptic option up as an alternative.

As for apache.conf, that's intended for a setup I didn't cover in this guide. I see no reason you couldn't remove it. It may be related to the warnings, but I doubt it. Just back it up before you remove it, kay?

---

### Post by Skip Da Shu on 2008-05-19
Here's some info that I am hoping might help on my error log messages.  I tied to match my access log entries to my error log entries by time/date stamp and here's what I found.

Access log:
```
Sun May 18 07:53:51 2008|CLEANUPREFRESH|HIT|60872|us.archive.ubuntu.com_ubuntu_dists_hardy_multiverse_source_Sources.bz2
Sun May 18 07:53:51 2008|CLEANUPREFRESH|HIT|6397|us.archive.ubuntu.com_ubuntu_dists_hardy_restricted_binary-amd64_Packages.bz2
Sun May 18 07:53:52 2008|CLEANUPREFRESH|HIT|1488|us.archive.ubuntu.com_ubuntu_dists_hardy_restricted_source_Sources.bz2
Sun May 18 07:53:52 2008|CLEANUPREFRESH|HIT|4257395|us.archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-amd64_Packages.bz2
Sun May 18 07:53:52 2008|CLEANUPREFRESH|HIT|1323029|us.archive.ubuntu.com_ubuntu_dists_hardy_universe_source_Sources.bz2
Sun May 18 07:54:33 2008|192.168.218.24|HIT|191|us.archive.ubuntu.com_ubuntu_dists_hardy_Release.gpg
Sun May 18 07:54:33 2008|192.168.218.24|HIT|191|security.ubuntu.com_ubuntu_dists_hardy-security_Release.gpg
Sun May 18 07:54:33 2008|192.168.218.24|HIT|191|archive.canonical.com_ubuntu_dists_hardy_Release.gpg
```

Error log:
```
Sun May 18 07:53:51 2008|INETD|info [6638]: Warning: no running inetd server found
Sun May 18 07:53:51 2008|INETD|info [6640]: Warning: no running inetd server found
Sun May 18 07:53:52 2008|INETD|info [6642]: Warning: no running inetd server found
Sun May 18 07:53:52 2008|INETD|info [6644]: Warning: no running inetd server found
Mon May 19 07:49:32 2008|INETD|info [25842]: Warning: no running inetd server found
Mon May 19 07:49:33 2008|INETD|info [25844]: Warning: no running inetd server found
Mon May 19 07:49:33 2008|INETD|info [25846]: Warning: no running inetd server found
Mon May 19 07:49:34 2008|INETD|info [25848]: Warning: no running inetd server found
```

Then next occurrences of the INETD error are later on the 19th when 

Access log:```
Mon May 19 07:50:07 2008|CLEANUPREFRESH|HIT|1488|us.archive.ubuntu.com_ubuntu_dists_hardy_restricted_source_Sources.bz2
Mon May 19 07:50:07 2008|CLEANUPREFRESH|HIT|4257395|us.archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-amd64_Packages.bz2
Mon May 19 07:50:08 2008|CLEANUPREFRESH|HIT|1323029|us.archive.ubuntu.com_ubuntu_dists_hardy_universe_source_Sources.bz2
Mon May 19 07:53:37 2008|192.168.218.22|HIT|191|us.archive.ubuntu.com_ubuntu_dists_hardy_Release.gpg
Mon May 19 07:53:37 2008|192.168.218.22|HIT|191|security.ubuntu.com_ubuntu_dists_hardy-security_Release.gpg
```

Error log (EOF):
```
Mon May 19 07:50:07 2008|INETD|info [25987]: Warning: no running inetd server found
Mon May 19 07:50:07 2008|INETD|info [25989]: Warning: no running inetd server found
Mon May 19 07:50:07 2008|INETD|info [25991]: Warning: no running inetd server found
```

Going to the oldest (top) entries in the files shows the same pattern... no error entries until...
Error log: 
```
Fri May  9 07:44:34 2008|INETD|info [17032]: Warning: no running inetd server found
Fri May  9 07:44:35 2008|INETD|info [17035]: Warning: no running inetd server found
```
Which coincides with...
Access log:
```
Fri May  9 07:44:32 2008|127.0.0.1|HIT|173749|us.archive.ubuntu.com_ubuntu_dists_hardy_multiverse_binary-amd64_Packages.bz2
Fri May  9 07:44:35 2008|CLEANUPREFRESH|EXPIRED|7874|security.ubuntu.com_ubuntu_dists_hardy-security_main_binary-amd64_Packages.gz
Fri May  9 07:44:36 2008|CLEANUPREFRESH|HIT|1512492|us.archive.ubuntu.com_ubuntu_dists_hardy_main_binary-amd64_Packages.gz

```
From this I'm concluding that it's the the execution of "CLEANUPREFRESH" generating the error.  Whatever "process" is triggering the error also seems to log it 1 second prior to the access log message.

Can anyone tell me a bit about what the "CLEANUPREFRESH" access log entry is about and what setting where triggers it?  Is it apt-cacher's clean-up or apt's clean-up...I'm guessing apt-cacher's.

Thanx, Skip

---

### Post by mssever on 2008-05-19
I've just now gotten time to upgrade from Gutsy to Hardy. But when I try to upgrade using apt-cacher (as a proxy), I get the following error: "Authenticating the upgrade failed. There may be a problem with the network or with the server."

Any ideas what might be causing this error and how to fix it?

NOTE: I'm upgrading via update-manager, which does a bit more than simply switching my sources.list to hardy would. The latter method is too risky for my tastes.

---

### Post by mssever on 2008-05-19
OK, my upgrade problem appears to be due to [bug 113658]("https://bugs.edge.launchpad.net/ubuntu/+source/update-manager/+bug/113658"). I'm using the workaround in that bug, and the packages for the upgrade are currently downloading. That workaround is to disable the Acquire::http::Proxy setting and modify sources.list instead. Here's an example line from my sources.list to illustrate this:
```
deb http://scott-desktop.mss:3142/archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
```

---

### Post by coolen on 2008-05-20
Thanks for that. Ironically, I scrapped that method a while back, thinking it was too messy :)

The guide has been updated with this workaround.

---

### Post by coolen on 2008-05-20
Skip, your warning messages baffle me. I'm getting nothing like that, although many CLEANUPREFRESHes. Thus, I can only conclude that CLEANUPREFRESH expects, at some point, that inetd be running (as it is on my machine). This could be something internal to apt-cacher. I can't seem to find any option that might relate to this behaviour.

---

### Post by mssever on 2008-05-21
> **coolen said:**
> Thanks for that. Ironically, I scrapped that method a while back, thinking it was too messy :)

The guide has been updated with this workaround.
Thanks. My upgrade was successful, and I immediately reverted the workaround, because I agree that that way is too messy. A few comments, though. First, my nick has nothing to do with MS servers. :) It's mssever, with only one *R*.

Second, I prefer to comment out the proxy config myself, instead of altering it. Maybe it's just personal preference...

Third, I'm glad I ran across your guide before you put all the sed commands in there. While I use regexps a lot, they're not particularly easy for humans to parse. And I actually prefer to operate from vim, instead of sed, which means I have to parse them before translating them to their vim equivalent. In fact, I'm wondering (and I don't know sed well enough to know the answer to this) if your sed command will fail in the case of a fresh install of apt-cacher. By default, /etc/apt/apt.conf.d/01proxy doesn't exist, so when sed tries to match [FONT=Courier New]http://[/FONT] it'll fail because it won't find a match. Unless sed does something odd.

---

### Post by Skip Da Shu on 2008-05-22
> **coolen said:**
> Skip, your warning messages baffle me. I'm getting nothing like that, although many CLEANUPREFRESHes. Thus, I can only conclude that CLEANUPREFRESH expects, at some point, that inetd be running (as it is on my machine). This could be something internal to apt-cacher. I can't seem to find any option that might relate to this behaviour.

Good, I don't feel so bad then.  As I've been over the options a couple of times or more.  I did find out one little more tidbit of information... but I think this would be expected.  By changing the "clean_cache=" parm from "1" to "0" I no longer get the error.  

I do have a questions.. not really related to the warning messages on inetd...

Do I understand that if I uncomment the 'daemon_addr=' line (with 'my.static.IP, localhost' in it) that apt-cacher will ONLY listen for requests coming to that IP?  Assuming so... what is it listing on w/o it?  So does it reduce some work apt-cacher otherwise has to do by "binding" it to nnn.nn?

```
# optional setting, binds the listening daemon to one specified IP. Use IP
# ranges for more advanced configuration, see below.
# daemon_addr=192.168.nnn.nn, localhost
```

Hmmm, the above uncommented gave me ```
skip@crunch20:~$ sudo /etc/init.d/apt-cacher start
Starting Apt-Cacher: apt-cacherUnable to bind socket (port 3142), trying again in 5 seconds.
Unable to bind socket (port 3142), trying again in 5 seconds.
```

---

### Post by coolen on 2008-05-22
> **mssever said:**
> Thanks. My upgrade was successful, and I immediately reverted the workaround, because I agree that that way is too messy. A few comments, though. First, my nick has nothing to do with MS servers. :) It's mssever, with only one *R*.

Second, I prefer to comment out the proxy config myself, instead of altering it. Maybe it's just personal preference...

Third, I'm glad I ran across your guide before you put all the sed commands in there. While I use regexps a lot, they're not particularly easy for humans to parse. And I actually prefer to operate from vim, instead of sed, which means I have to parse them before translating them to their vim equivalent. In fact, I'm wondering (and I don't know sed well enough to know the answer to this) if your sed command will fail in the case of a fresh install of apt-cacher. By default, /etc/apt/apt.conf.d/01proxy doesn't exist, so when sed tries to match [FONT=Courier New]http://[/FONT] it'll fail because it won't find a match. Unless sed does something odd.


Oh, sorry about the name. My bad. I'll fix it.

I put the sed commands in there because I prefer to give people commands they can just cut and paste. I feel it makes it easier, but it does look messy, and it's not as easy to read. I might give the sed commands as an alternative. It'd also helps those who use tools like whereami to auto-configure their laptop to have a command, rather than either swapping it out for another file or figuring the sed commands out themselves.

Also, you're right about 01proxy not being there. My bad.

---

### Post by bugmenot_user on 2008-05-26
add these line to /etc/apt/apt.conf.d/clean ; so apt cache will be automatically cleaned up after installation.
```

DPkg::Post-Invoke {"/bin/rm -f /var/cache/apt/archives/*.deb || true";};
```

This works well for my chroots. It should work well for desktop pcs and servers too. Note that you can't use apt-get clean instead of rm, because apt fails since it is already running.

---

### Post by greentree-sa on 2008-06-17
Hi guys,

Does anyone know how to create a local repo from DVD/CD's (Hardy 8.04) already downloaded?

Thanks for a great forum. I has "all" the answers for us newbies! 
(Has anyone found the questions yet? :smile:)

Christiaan.

---

### Post by Skip Da Shu on 2008-06-17
> **bugmenot_user said:**
> add these line to /etc/apt/apt.conf.d/clean ; so apt cache will be automatically cleaned up after installation.
```

DPkg::Post-Invoke {"/bin/rm -f /var/cache/apt/archives/*.deb || true";};
```

This works well for my chroots. It should work well for desktop pcs and servers too. Note that you can't use apt-get clean instead of rm, because apt fails since it is already running.

Would this be the same as setting Synaptic Package Manager -> Settings -> Prefs -> Files -> checkbox for "Deleted downloaded packages after installation"?

---

### Post by bugmenot_user on 2008-06-17
> **Skip Da Shu said:**
> Would this be the same as setting Synaptic Package Manager -> Settings -> Prefs -> Files -> checkbox for "Deleted downloaded packages after installation"?

Mostly it is. But Synaptic's setting only works with Synaptic, but this works wih apt-get and aptitude also.

---

### Post by Skip Da Shu on 2008-06-17
> **bugmenot_user said:**
> add these line to /etc/apt/apt.conf.d/clean ; so apt cache will be automatically cleaned up after installation.
```

DPkg::Post-Invoke {"/bin/rm -f /var/cache/apt/archives/*.deb || true";};
```

This works well for my chroots. It should work well for desktop pcs and servers too. Note that you can't use apt-get clean instead of rm, because apt fails since it is already running.

So, because I have lotsa practice... lemme ask the dumb question.  Since I don't have a "/etc/apt/apt.conf.d/clean" file. Can I assume I can create that file with only this 1 line entry in it?

---

### Post by bugmenot_user on 2008-06-17
> **Skip Da Shu said:**
> So, because I have lotsa practice... lemme ask the dumb question.  Since I don't have a "/etc/apt/apt.conf.d/clean" file. Can I assume I can create that file with only this 1 line entry in it?

Sorry! That was my bad. I wasn't clear enough. Just create a file and put that line into it. And create apt.conf.d directory, too, if your system doesn't have it.

---

### Post by Skip Da Shu on 2008-06-17
> **bugmenot_user said:**
> Sorry! That was my bad. I wasn't clear enough. Just create a file and put that line into it. And create apt.conf.d directory, too, if your system doesn't have it.

No, I think 99% of the folks would've known just to create it. I'm probably being overly cautious because I've got 11 machines running off of apt-cacher and it is working so nicely.  

I have as yet to figure out how Update-Manager decides what to keep in /var/cache/apt/archives and what to not keep.  I think the synaptic package manager setting I referred to has some influence on it because after setting that and clearing the package cache (with some apt command) I find very little in the cache after a fair amount of time... but not empty completely.

For example one of the machines serviced by apt-cacher is a Xubuntu 7.10 64b machine.  It has surely applied 10 or 20 updates and yet the only packages in it's local cache today were:

openssl-blacklist_0.3.3+0.4-0ubuntu0.7.10.1_all
and
xserver-xorg-core_2%3a1.3.0.0.dfsg-12ubuntu8.4_amd64

and the "8.4" in the 2nd one's name is a bit worrisome since this is a v7.10 machine.  

Anyway.  I created the clean file as you've outlined. Ran update-manager, picked up 5 updates, applied them and guess what... the cache is empty now!  :)

Thanx for the tip.

---

### Post by coolen on 2008-06-18
Hey, thanks for that. I'm erring on the side of caution with your suggestion. I'm not sure if APT keeps metadata on the cache, so I'm a little reluctant to simply remove them.

However, if this is what Synaptic essentially does, then it seems safe enough. I've been using it for a while without incident. I'll add it.

Thank you for your contribution.

---

### Post by Eladon on 2008-06-21
Great tutorial, worked like a charm.  Only one thing I'd like to request:

Part Four: Backing up and Restoring the apt-cache files

You know, in case you want to reload your server.  :)

---

### Post by bugmenot_user on 2008-06-21
eladon:
just copy /var/cache/apt-cache/packages to somewhere. and when you want to restore it, use
```
/usr/share/apt-cacher/apt-cacher-import.pl -r -R /your/backup/dir/
```

-r and -R is not so necessary, also consider other options. Look at them with --help argument.

---

### Post by Skip Da Shu on 2008-06-22
> **Eladon said:**
> Great tutorial, worked like a charm.  Only one thing I'd like to request:

Part Four: Backing up and Restoring the apt-cache files

You know, in case you want to reload your server.  :)

Hmmm, Is this worth the effort?  

Purge the cache and it'll rebuild as updates are needed by any machine serviced by the apt-cacher server.  

I would think that the odds are that 90% or more of what you would back up will not be used again unless you're in the middle of a doing updates.

---

### Post by coolen on 2008-06-22
For this, one could merely leave out the step to clean the cache (and use the cp command rather than mv). APT would keep updating its own cache, cleaning out outdated packages and storing new ones, but in the end, it'd still be there.

I've updated it with a note about keeping the cache around. I decided not to back up the cache, since there's no use case I can think of for restoring a cache with outdated packages.

---

### Post by egalvan on 2008-10-01
Thanks for a GREAT tutorial!

I would like to repeat the following question asked by 'greentree'
as I would like to do the same....
buy the DVD's (thus saving the download), then create a local repo on my harddive, and update automatically.



> **greentree-sa said:**
> Hi guys,
Does anyone know how to create a local repo from DVD/CD's (Hardy 8.04) already downloaded?
Christiaan.

ErnestG

---

### Post by coolen on 2008-10-01
Copy the .deb files in /media/cdrom/pool (these are further organised alphabetically in separate directories, so I don't know a command to accomplish this) to /var/cache/apt-cacher/import, then run this:

```
sudo /usr/share/apt-cacher/apt-cacher-import.pl
```

If the packages are the same version present in the repos, this should work. You'll need to follow the additional steps for upgrades on the client machines (unless this issue has been fixed somehow. I doubt it) and likely also on the server.

I hope that does what you want.

---

### Post by ad_267 on 2008-10-28
Just want to say thanks for the great tutorial! This is very useful and is working perfectly. I have one machine on Hardy and one on Intrepid at the moment, this should begin to pay off a lot when I upgrade the other one. 

(I couldn't thank your first post so thanked your most recent one)

---

### Post by damien_d on 2008-11-13
Hello,

Being an Aussie and just having just been throttled (again!) to 64k, this tutorial is very handy indeed.

One question though:  On the machine that you have the server, do you also have to configure it as a client?  

That is, on the machine that I have apt-cacher installed, must I also set the proxy on the same machine? (or, for those using the sources list, the sources file to localhost)

---

### Post by damien_d on 2008-11-13
Oh, and as a separate question, how does this program differ from apt-proxy?

[https://help.ubuntu.com/community/AptProxy](https://help.ubuntu.com/community/AptProxy)

---

### Post by coolen on 2008-11-13
I'd recommend it. If you don't, then any packages the server downloads will not be shared, unless you write a cron job to import the server's cache regularly (or do it yourself). Seems messy to me.

As for how this differs from Apt Proxy, this is what I decided to use when I wanted to do this. I considered Apt Proxy, but I can't remember why I didn't go with it. From what I've read, they're fairly similar in capabilities.

---

### Post by Skip Da Shu on 2008-11-13
> **damien_d said:**
> Hello,

Being an Aussie and just having just been throttled (again!) to 64k, this tutorial is very handy indeed.

One question though:  On the machine that you have the server, do you also have to configure it as a client?  

That is, on the machine that I have apt-cacher installed, must I also set the proxy on the same machine? (or, for those using the sources list, the sources file to localhost)

Short answer = Yes.

I'm assuming that you are using the "01Proxy" file in /etc/apt/apt.conf.d/ instead of modifying the sources.list on the client machines.  As such:

```
Acquire::http::Proxy "http://192.ip.of.aptcacher:3142";
```

I have the following file on my apt-cacher server(C20) as /etc/apt/apt.conf.d/01proxy:
```

Acquire::http::Proxy "http://localhost:3142";
```

---

### Post by ace214 on 2009-03-19
I know this thread is rather old, but figured this might be helpful. On the [Apt community wiki]("https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGetHowto#Temporary%20proxy%20session") page I found that you can temporarily set a variable for your proxy for use with a laptop with the command:
```
export http_proxy=http://
```
Works well for me as a temporary apt detour. I'm to the breaking point with updating three computers for Jaunty, so I will try this out later tonight. Thanks for posting the tutorial.

---

### Post by coolen on 2009-03-20
Thanks for that.

I'm not sure if it'd be useful as a complete solution, since it looks like it'll only work on the command line. Still, I'll put it up as a useful tip :)

---

### Post by ace214 on 2009-03-20
> **coolen said:**
> Thanks for that.

I'm not sure if it'd be useful as a complete solution, since it looks like it'll only work on the command line. Still, I'll put it up as a useful tip :)

Yes, you're right you have to use the terminal apt-get commands.

---

### Post by Skip Da Shu on 2009-05-27
Looking back thru this it seems I must have been installing apt-cacher in late April of 2008 thanks to the GREAT tutorial and follow-up discussions in this thread.

So, Apt-cacher has been running along just fine for over a year.  Today I logged onto the apt-cacher machine and got a notice that I had mail in /var/mail.

It seems somebody's not happy and I have no idea where to go with this.

> From root@crunch20 Wed May 27 07:57:50 2009
Return-path: <root@crunch20>
Envelope-to: root@crunch20
Delivery-date: Wed, 27 May 2009 07:57:50 -0500
Received: from root by crunch20 with local (Exim 4.69)
	(envelope-from <root@crunch20>)
	id 1M9IhZ-0000DB-Pr
	for root@crunch20; Wed, 27 May 2009 07:57:50 -0500
From: Anacron <root@crunch20>
To: root@crunch20
Subject: Anacron job 'cron.daily' on crunch20
Message-Id: <E1M9IhZ-0000DB-Pr@crunch20>
Date: Wed, 27 May 2009 07:57:49 -0500

/etc/cron.daily/apt-cacher:
Use of uninitialized value in concatenation (.) or string at /usr/share/apt-cacher//apt-cacher-lib.pl line 169, <$listpipe> line 17.
Use of uninitialized value in concatenation (.) or string at /usr/share/apt-cacher//apt-cacher-lib.pl line 169, <$listpipe> line 18.
Use of uninitialized value in concatenation (.) or string at /usr/share/apt-cacher//apt-cacher-lib.pl line 169, <$listpipe> line 41.
Use of uninitialized value in concatenation (.) or string at /usr/share/apt-cacher//apt-cacher-lib.pl line 169, <$listpipe> line 42.
Use of uninitialized value in concatenation (.) or string at /usr/share/apt-cacher//apt-cacher-lib.pl line 169, <$listpipe> line 64.
Use of uninitialized value in concatenation (.) or string at /usr/share/apt-cacher//apt-cacher-lib.pl line 169, <$listpipe> line 65.
Use of uninitialized value in concatenation (.) or string at /usr/share/apt-cacher//apt-cacher-lib.pl line 169, <$listpipe> line 87.
Use of uninitialized value in concatenation (.) or string at /usr/share/apt-cacher//apt-cacher-lib.pl line 169, <$listpipe> line 108.
Use of uninitialized value in concatenation (.) or string at /usr/share/apt-cacher//apt-cacher-lib.pl line 169, <$listpipe> line 109.
Use of uninitialized value in concatenation (.) or string at /usr/share/apt-cacher//apt-cacher-lib.pl line 169, <$listpipe> line 134.

This goes on for another 2K or so lines.

In /usr/share/apt-cacher/apt-cacher-lib.pl I see:

```

#! /usr/bin/perl
# This is a library file for Apt-cacher to allow code
# common to Apt-cacher itself plus its supporting scripts
# (apt-cacher-report.pl and apt-cacher-cleanup.pl) to be
# maintained in one location.

# This function reads the given config file into the
# given hash ref. The key and value are separated by
# a '=' and will have all the leading and trailing
# spaces removed.

```
```

sub extract_sums {
   my ($name, $hashref) = @_;
   my ($cat, $listpipe, $indexbase);

   $cat = ($name=~/bz2$/ ? "bzcat" : ($name=~/gz$/ ? "zcat" : "cat"));

   if($name=~/^(.*_)Index$/) {
       $indexbase=$1;
       $indexbase=~s!.*/!!g;
   }

   open($listpipe, "-|", $cat, $name);
   my $file;
   while(<$listpipe>) {
      if(/^\s(\w{40})\s+\d+\s(\S+)\n/) {
	 $sum=$1;
	 # Index format similar to Sources but filenames need to be corrected
	 # FIXME: this is sha1, not md5. Different format, can be detected by
	 # the length (40), though
	 $file=$indexbase.$2.".gz";
     }
     elsif(/^\s(\w{32})\s\d+\s(\S+)\n/) {
	 $sum=$1;
	 $file=$2;
      }
      elsif(/^MD5sum:\s+(.*)$/) {
	 $sum=$1;
      }
      elsif(/^Filename:\s+(.*)$/) {
	 $file=$1;
	 $file=~s/.*\///;
      }
      if(defined($file) && defined($sum)) {
	 $$hashref{$file}=$sum;
	 undef $file;
	 undef $sum;
      }
   };
   close($listpipe);
   my $ret = ! ($? >> 8);
   return $ret;
}
```
Line 169 is in the first if under the while:
```
 $file=$indexbase.$2.".gz";
```

So I'm sitting here thinking... 'OK goob, what did you change?'... recent changes included putting /mnt/netshare2 onto a RAID1 partition but that was over a week ago. 

I modified the /etc/logrotate.d/apt-cacher* entries to keep less logs.  Timestamps show that was done on the 5/22.
 
I moved where the logs are written back to /var/log instead of in the /mnt/netshare/apt-cacher directory... but that was done last Saturday (5/23). 

There's nothing in the error log except the same ol' entry I've had ever since I first started apt-cacher:
> Wed May 27 07:56:33 2009|INETD|info [32547]: Warning: no running inetd server found That appears to come from the CLEANREFRESH.  

What did I change YESTERDAY... I can't think of a thing I did directly to apt-cacher.

ONLY one thing.  I installed BackupPC onto this same machine last night.  I sure can't see the relationship but BackupPC does install Apache2 and a perl version of rsync and a couple perl libs.  Which is why I'm a bit suspicious of the perl parts.

Any body have any ideas?  Or where I could turn for help?\

**UPDATE:**  To test the perl conflict between backuppc and apt-cacher I installed "libfile-rsyncp-perl 0.68-1" one of the packages BackupPC installs that I was suspicious of.  I was expecting to get the concatenation error the next day.  I did not so back to square 1.  I will be re-installing BackupPC on the apt-cacher machine later this week to start over.

---

### Post by Skip Da Shu on 2009-05-29
Well I found the dpkg log and removed all packages that BackupPC installed, backed up my apt-cacher.conf file, did a synaptic reinstall of apt-cacher and all looked good.

This morning no nasty gram from cron.

However either with this OR more likely some prior change and I just didn't catch it... I can no longer browse the traffic report or the status page from anyplace but the apt-cacher server.

This works:  [http://localhost:3142/](http://localhost:3142/) on crunch20.

This, from my desktop on the same lan, does not:  [http://crunch20:3142/](http://crunch20:3142/)
nor does the same with the ip specified instead of the hostname.

> I get the The connection to the server was reset while the page was loading.
    
      
     
The network link was interrupted while negotiating a connection. Please try again.

Any ideas why Firefox on my desktop is being told no, no, no but it's functional from localhost?

**SOLVED:** Found a "," where a "." should've been in the deny_hosts= line.  Seems this also controls who can browse the stats page.

---

### Post by kevinguillorytraining on 2009-10-10
Thanks for sharing one of the main and best tip

---

### Post by Onesimus on 2010-05-14
I have been using this tutorial for a number of years.  However, I cannot get it to work on Lucid.

I get:
```
Unable to connect to localhost:3142: [IP: 127.0.0.1 3142]
```

Any thoughts on why this might be occurring ?

Edit:  I am using the inetd mode on the server.

---

### Post by coolen on 2010-05-14
I'm not running Lucid yet, so I can't say whether or not there are any issues specific to it...I find it difficult to imagine there would be, though.

Looks like the process is not responding. Are you sure you followed the setup correctly? Possible causes:

- If you're using daemon mode, you've not set autostart to 1;
- You've not restarted your machine, and either not started the apt-cacher process or not restarted inetd;
- If you're using inetd, you did not copy the command correctly.

Like I said, I can't imagine something changed to break this. This is server work, and we tend to like servers to keep running without having to update our setups with each new release.

Is anyone else having trouble with Lucid?

---

### Post by Marco Amans on 2010-05-15
> **coolen said:**
> 

Is anyone else having trouble with Lucid?

Hi! 
I found this thread by searching "unable to connect to localhost:3142". I was receiving this message when doing "sudo apt-get update" in Lucid Lynx. I don't have the faintest idea whether this is relevant to your problem, but I give the information just in case.

The solution was to rename 01proxy in /etc/apt/apt.conf.d to 01proxy.deactivated.

Warning: I am not a power user at all and I have no idea of what this change could break in your system.

---

### Post by ad_267 on 2010-05-15
That sounds like you just disabled accessing updates from apt-cacher, and are getting them over the internet. Not really much of a solution then...

I'm not using apt-cacher on Lucid either so can't be much help though.

---

### Post by coolen on 2010-05-15
Marco, thanks for taking the time to reply. I agree with ad_267. It sounds like you may have told APT to ignore that file, setting it back to direct updates. From the description of the problem, it didn't seem like there was anything wrong with the proxy setup.

How long have you been using apt-cacher successfully? Did you do an upgrade or a clean install?

If two people are experiencing this, it sounds as though something's broken in Lucid. I won't get a chance to look into it until later this week. In the meantime, I'll throw a warning up in the tutorial.

---

### Post by Onesimus on 2010-05-16
I created a script from the various commands that were given in the tutorial.  I have used the same script on previous versions of Ubuntu with no problems - so I don't think there is a problem following the commands.

I did reboot the machine.

Connection refused by the server to the clients and also to the server.

---

### Post by Onesimus on 2010-05-22
Following an update to apt this now is working once again :)

---

### Post by coolen on 2010-05-22
Thanks for that! Can others confirm? Could someone investigate whether this needs to be updated on all machines, or just the server? Sorry, but there's been a family emergency. I'm away from home for the next week.

---

### Post by zzztownsend on 2010-06-01
I've been trying to use apt-cacher today on Lucid before and after updates, but no luck. I tried apt-cacher-ng - almost identical installation/setup and works perfectly.

Cheers

Matt

---

### Post by Onesimus on 2010-08-21
This hasn't worked for me for some time on Lucid (if at all).

I tried zzztownsend's suggestion and can confirm that works.

Just uninstall apt-cacher on the server, and install apt-cacher-ng in its place - all other settings remain the same.

---

### Post by Skip Da Shu on 2010-08-22
I upgraded my apt-cacher machine a couple months ago (at most) from Xubuntu v8.04LTS to v10.04LTS.  

For at LEAST the last couple of weeks each time cron.daily runs the cleanup (apt-cacher-cleanup.pl) it appears to be going into a loop.  I THINK it's doing it because I have user and group in the .conf file set to root (as it's been since 4/2008).  Those of you running Lucid might want to run TOP or "ps aux | grep apt-cacher" to see if your cleanup has been running for days/weeks/months.  See bug [**_#622161_**](https://bugs.launchpad.net/ubuntu/+source/apt-cacher/+bug/622161) in launchpad for more detail.

---

### Post by karthick87 on 2011-07-09
I would like to import the CD caches. Is it possible? If yes? How to do it?

---

