---
title: "How to create a USB flash drive without the spyware?"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by susanne260 on 2013-02-24
I tried to create an Ubuntu USB flash drive with the “persistence” option turned on with the Universal-USB-Installer, because I wanted to remove the spyware feature and not have to do it every single time I boot from the USB drive, but Ubuntu was incredibly slow with the persistence file.

So, I re-created the USB drive without the persistence file. But now I have to manually remove the spyware every time I use it. :(

Is there a modified ISO image I could download that doesn't have the spyware? Any other solutions?

---

### Post by axel668 on 2013-02-24
You can try another version that doesn't include the spyware, like Lubuntu, Xubuntu or Ubuntu Gnome Remix, or you can switch to Linux Mint (which is 99% Ubuntu, too, under the hood).

Or you can create a custom LiveCD as described here: [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

---

### Post by Sealbhach on 2013-02-24
I'm using Debian with XFCE on a USB stick right now. I started up the Debian CD in a Virtualbox machine and installed it directly onto the USB as if it were a regular hard drive. I never found the persistent option installs to be satisfactory, but this Debian install is working great.  It takes a little more effort to get Debian up and running OK, but it's worth it. Very quick and efficient and low memory usage.

.

---

### Post by sudodus on 2013-02-24
> **axel668 said:**
> You can try another version that doesn't include the spyware, like Lubuntu, Xubuntu or Ubuntu Gnome Remix, or you can switch to Linux Mint (which is 99% Ubuntu, too, under the hood).

Or you can create a custom LiveCD as described here: [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
+1
Not only that, they are faster to boot and to run too, particularly Lubuntu with the ultra light-weight desktop environment LXDE :-)

---

### Post by susanne260 on 2013-02-24
I had almost forgotten about Xubuntu and Lubuntu, thanks for reminding me. :)

I'll try them. It looks like they aren't as bloated as Ubuntu, which is another bonus. I'll also give Debian a try later.

---

### Post by prodigy_ on 2013-02-24
Low performance with persistence is a result of frequent writes. Mounting / with noatime and removing journal with ```
tune2fs -O ^has_journal $(mount -l|grep " on / "|cut -d' ' -f1)
``` could help a lot.

---

### Post by n4pgw on 2013-02-24
Pardon my ignorance, but what is the spyware on the USB stick?

It sounds like something Ubuntu is installing when formatting....

A little scary here.

---

### Post by 3rdalbum on 2013-02-24
> **n4pgw said:**
> Pardon my ignorance, but what is the spyware on the USB stick?

It sounds like something Ubuntu is installing when formatting....

A little scary here.

Don't be scared, it's just a search engine. People spreading FUD have called it "spyware" but it's no more spyware than Google.com.

---

### Post by mick222 on 2013-02-24
It annoys me people using Ubuntu and being  so down on it for trying to make it support itself. If the price of free software is an easily removed link to Amazon why complain. There are plenty of distros out there that you could use instead.

---

### Post by susanne260 on 2013-02-24
> **3rdalbum said:**
> Don't be scared, it's just a search engine. People spreading FUD have called it "spyware" but it's no more spyware than Google.com.

Ubuntu should NOT send users' personal information to anyone **by default** if they search for their own files! This is unbelievable.

New users might not even know how to disable it right away. And if you go to google.com you know that you are searching the web, not from your own files.

And to make it even worse, the results are sent back over plain HTTP, so that anyone could easily listen in between. Why don't you fetch the images over HTTPS at the very least?

---

### Post by prodigy_ on 2013-02-24
> **3rdalbum said:**
> Don't be scared, it's just a search engine. People spreading FUD have called it "spyware" but it's no more spyware than Google.com.
Nice try. But Google.com is opt-in. Every time you use it you explicitly choose to do so. Amazon search in Ubuntu 12.10, however, is opt-out. IIRC, Ubuntu installer doesn't even warn you that you're going to have it installed. Therefore it's a typical spyware/adware.

---

### Post by sudodus on 2013-02-24
> **susanne260 said:**
> Ubuntu should NOT send users' personal information to anyone **by default** if they search for their own files! This is unbelievable.

New users might not even know how to disable it right away. And if you go to google.com you know that you are searching the web, not from your own files.

And to make it even worse, the results are sent back over plain HTTP, so that anyone could easily listen in between. Why don't you fetch the images over HTTPS at the very least?
We, at the Ubuntu Forums are not the programmers 'the devs', and we are not the company behind Ubuntu 'Canonical'. So don't blame us. We are only here to help. By the way Mr Shuttleworth has posted a message, that people will be made aware of this feature of the dash.

[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=2117985&highlight=Mark+Shuttleworth+Amazon+Dash[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2117985&highlight=Mark+Shuttleworth+Amazon+Dash")

---

### Post by 3rdalbum on 2013-02-24
> **prodigy_ said:**
> Nice try. But Google.com is opt-in. Every time you use it you explicitly choose to do so. Amazon search in Ubuntu 12.10, however, is opt-out. IIRC, Ubuntu installer doesn't even warn you that you're going to have it installed. Therefore it's a typical spyware/adware.

It. Is. Not.

Stop trying to scare people.

Spyware collects as much useful information as it can, and sends it back to base for malicious purpose. It attempts to evade detection by the user.

Ubuntu's Shopping lens is not malicious. It sends one search query when you type it - nothing more. That search query is stripped of identifying information at Canonical and sent on to do the actual search. Anybody with half a brain will notice Amazon search results in the Dash.

It doesn't fit any accepted definition of spyware as it is not malicious, does not evade detection, is not meant to collect data and only sends user queries.

It is indeed like Google.com in that any Google search will also send the search query to YouTube - even if you didn't intend this - and also to advertisers. If you click on any search results, your search query and IP address get sent to the destination website.

But nobody cares about that. As soon as you start bringing a large and successful business like Amazon into the equation, people start losing perspective. Heck, the Ubuntu Video lens sends your video search queries to China, but nobody seems to care if a corrupt and militaristic dictatorship gets your search queries. A shopping website though, that's a total breach of trust!

---

### Post by oldos2er on 2013-02-24
Please don't use the term "spyware" when asking about the Amazon search/shopping lens; it is inaccurate FUD and borderline trolling.

From the Code of Conduct:

Trolling, Attacks and Flaming: These are always forbidden.
Trolling is posting in a way that provokes emotional responses.
Attacks and derogatory terms of any kind are not welcome. This includes references to other operating systems and the companies that produce them.
Flames are messages that personally attack or call any people names or otherwise harass. These, along with any generally condescending posts will be edited or removed at the moderators discretion.
If a thread is flame-bait (appears to be intended to start an argument or is likely to cause an argument rather than enhance discussion, as in trolling), it will be locked or removed without notice. Individual flame-bait comments in a post may be deleted or edited at the moderators' discretion.
If the thread turns into an argument, it can be closed to further comment or removed without notice. Sometimes a moderator may split the thread or delete certain portions in order to keep the discussion going, but that is not always possible since we are a staff of volunteers with limited time and numbers.

---

### Post by Elfy on 2013-02-24
Thread closed. 

There is a thread in the cafe you can argue about the definition of spyware.

---

