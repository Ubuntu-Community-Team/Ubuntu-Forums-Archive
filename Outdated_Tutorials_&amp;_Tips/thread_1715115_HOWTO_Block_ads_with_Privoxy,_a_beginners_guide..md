---
title: "HOWTO: Block ads with Privoxy, a beginners guide."
date: 2011-03-26
forum: Outdated Tutorials &amp; Tips
---

### Post by goldaryn on 2011-03-26
Hello all,

Today here's a tutorial on how to get up and running with [SIZE="3"][Privoxy]("http://www.privoxy.org/")[/SIZE], a privacy-enhacing HTTP proxy that can block adverts. This tutorial is about getting the most of Privoxy in isolation; if you are interested in Privoxy and Tor together, there are several articles on these forums that can help you - do a search.

**Why use Privoxy?**

These days there are a few different ways to block ads. One way is web browser extensions, such as AdBlock and co. for Firefox. The second way is through  [hosts files]("http://ubuntuforums.org/showthread.php?t=241460"). Both ways lack power at times, and hosts files can be fiddly.

Privoxy is an HTTP proxy. This means it is a service which sits between your internet connection and any programs that use the internet. It can be turned on or off easily, and acts as a middleman, eating any nasties such as adverts or privacy-intrusive cookies, so that your web browser or other program never sees them. 

This can save your bandwidth, is flexible and powerful, and easily turned off or uninstalled if you don't need or like it.

Privoxy is available in the Ubuntu Software Centre.

**How do I install it?**

these instructions are for Ubuntu 10.10, others should be similar

[LIST=1]
[*]Click on Applications -> Ubuntu Software Centre.
[*]Click on "Get software", then click on the search box.
[*]Type in Privoxy, and press enter.
[*]The package "privoxy: Privacy enhancing HTTP Proxy" should come up.
[*]Select it and press install. That was easy :-)[/LIST]

**How do I set it up?**

Privoxy is now installed on your system, and defaults to localhost:8118. If you want to start using it, you will have to tell your web browser to use it.

An example of how to do this, with Firefox:

[LIST=2]
[*]Open Firefox
[*]Go to Edit -> Preferences
[*]Click "Advanced", press the "Network" tab and then look for Connections -> Settings. Press that.
[*]You should now see the proxies set up page. Your current setting should be "No proxy". If it isn't, stop here! WRITE DOWN what it is!
[*]So now we need to tick "Manual proxy configuration". Edit HTTP Proxy to be "localhost" and port to be "8118. (This is where Privoxy defaults to.) Save and restart Firefox. All done.[/LIST]

If you find it doesn't work or you don't want it, switch it back to "No proxy" (or whatever it was before that you WROTE DOWN).

**It works! This is pretty cool :P How do I block things from [www.xyxlol.com?](www.xyxlol.com?) **

[LIST=3]
[*]To add an additional site to the block list easily, first open the user.action file. 
```
$ sudo gedit /etc/privoxy/user.action
```
[*]You're going to make a backup, aren't you! Yes, good idea! Do that! Give yourself a pat on the back.
[*]Read the readme.
[*]Scroll to the very bottom of the file
[*]Add 

```
{+block}
.xyxlol.com
```

to the bottom of the file.

[*]In future, you can add others like so

```
{+block}
.xyxlol.com
.anotherannoyingsite.net
.so-many-adverts-argh.org
```[/LiST]

**It seems that site X has stopped working properly.**

If a site seems particularly sensitive to Privoxy, you can tell Privoxy that it's fragile and please leave it alone. Add

```
{fragile}
video.google.com
.yahoo.co.uk
```

to the bottom of the file above. These need to be AFTER any blocks that you have said. So at the very, very, VERY bottom of the file.

**How do I edit the other Privoxy files?**

They should all be in /etc/privoxy, so have a look there. The main ones to look at are **default.filter** and **user.action**. Read the readmes.

**I want to uninstall!**

[LIST=4]
[*]Turn off the proxy in your browsers.
[*]Uninstall it in Ubuntu Software Centre (you will find it in "Installed" this time, obviously).[/LIST]

**I want to do more advanced things!**

[LIST]
[*]Back stuff up first :)
[*]See the Privoxy FAQ and tutorials on their site
[*]Look at the .filter and .action files in /etc/privoxy and read the helpful tutorials.
[*]See my [blog]("http://goldaryn.blogspot.com/").
[*]Ask in this thread
[*]Wait for my next tutorial :-)[/LIST]

**It'd be good if someone consolidated some good HOSTS files into Privoxy format..**

I agree. Try [here]("http://sites.google.com/a/goldaryn.org.uk/www/user.action"). A **warning** though: I filter things as {+block-as-image} instead of plain old {+block} as the big white Privoxy panels get on my nerves sometimes. If you want these back, change the {+block-as-image}s back to plain old {+blocks}.

---

