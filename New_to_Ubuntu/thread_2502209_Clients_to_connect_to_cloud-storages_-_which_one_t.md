---
title: "Clients to connect to cloud-storages - which one to choose?!"
date: 2024-11-05
forum: New to Ubuntu
---

### Post by ursinusbaer on 2024-11-05
dear community - good day dear Ubuntu-experts


well at the moment i am thinking about the connection to a cloud -- how to do this via linux!?



Google Drive provides 20 GB. Among the multitude of providers - still an offer that looks somehow interesting (- among the cloud storage services for Linux ). It now even offers 20 GB (previously only 15) free storage space, which can be shared via the Gmail account, Google Photos and various Google and Android services. The space could also be expanded. But how do you connect: there have actually been official Google Drive clients for Windows, macOS, Android and iOS since 2012.
But I have not yet seen an official Linux client. 

Of course - one thing always works: connect to the browser on the Internet or use it; so far so good - but this does not yet establish data synchronization.
And no automatic uploading. 


What options are there in the Linux world!? i have heard about RKlone and Insync - but i am not sure which one to choose!?



1. Insync
2. RKlone 

look forward to hear from you 


rgards

---

### Post by TheFu on 2024-11-07
As Linux people, we can easily host our own "Cloud", especially for storage.  How?   Setup **ssh** using **ssh-keys** (never passwords!) and run a brute force attack dynamic blocking tool like fail2ban.  This enabled an **sftp-server** automatically.  Most Linux file managers support sftp out of the box.  The URL they need changes, but sometimes it is sftp:// and sometimes it is ssh:// and sometimes it is something else. Just depends on the file manager. Try sftp:// first, after you setup ssh between the client and server.

With just this, you'll have access to storage connected to YOUR computer, on YOUR network, from anywhere in the world, using the secure **sftp** protocol.  20GB?  How about 25**TB** - or whatever size you need.

I struggle to trust any 3rd party "cloudy" services.  None that I know are actually trustworthy.  They've all been caught doing something nefarious with the data we give them.  They certainly scan it all for information, unless we go to the extra effort of pre-encrypting it before pushing it into the cloud.

So, you'll need to decide how much "*convenience*" OR *"privacy"* are actually worth for you.  Google is great at convenience, but terrible at privacy. Same for almost all cloudy providers.  Just something to consider.

There are great **sftp** clients for every networked OS.  Plus, you'll have ssh access so there are 50+ other things you gain access just by setting up remote ssh access into your home LAN using ssh-keys.  ssh connectivity is well understood and how to secure it is also well-known.

I use ssh as a SOCKS proxy to connect into my home **NextCloud** server, so if you want a fancy web interface, Nextcloud being accessible just to you, but not to anyone outside your LAN is possible from anywhere in the world too.  Thanks to snap packages, nextcloud is a 1 command install on Ubuntu, if that interests you.  I ran a carefully installed Nextcloud server for a few years. Manually downloading each required package, getting the Nextcloud source code, patching it every month.  Then there was a major upgrade and it wanted newer versions of the 50+ dependencies.  It was a hassle to get working again, but after an hour, I got it working.  About a year later, the next major update causes similar issues.  3 hrs to get it working again.  And another year later and another major upgrade.  After screwing with it for 2 hrs, I got frustrated.  The base Ubuntu OS could use an upgrade too, so I decided to do that first.  Then I found the nextcloud snap package.  Ran the 1 command install and had a look around.  It was nextcloud, just like I had before, but as a snap.  Snaps get updates automatically.  That was 3-4 yrs ago.  There have been a number of major upgrades of that snap.  Backups of any snap are pretty easy.  There's a way to snag everything and put it into a tgz file, if that's your desire.  The Nextcloud snap also has an "export" command that does just the data for all users.  Anyway, running a server like nextcloud isn't hard anymore.  FWIW, I installed the nextcloud snap on the system with version 18.x .... just checked and it is running _Nextcloud Hub 6 (27.1.10)_ now.  I didn't do any upgrades. They were all automatic.  Of course, I do patch the server running the nextcloud snap every week. Takes about 5 minutes;  **sudo apt update && sudo apt upgrade** . Pretty easy.  It basically "just works."

If you have a Raspberry Pi v3, putting nextcloud on it can be your "server".  It would be silent and very low power use.  More than fast enough for running a webapp like nextcloud.

But sftp is much easier.

---

