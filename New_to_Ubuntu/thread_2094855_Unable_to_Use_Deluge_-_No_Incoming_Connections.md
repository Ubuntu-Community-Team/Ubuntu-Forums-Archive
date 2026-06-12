---
title: "Unable to Use Deluge - No Incoming Connections"
date: 2012-12-15
forum: New to Ubuntu
---

### Post by eleutherian on 2012-12-15
I am posting this in the beginners forum because this is my first real experience with Linux and Ubuntu.

I have two Windows laptops connected to a newly built server running Ubuntu 12.04.1 LTS. I installed Deluge on the server and activated the Web UI on one of the laptops. I set Deluge to automatically connect to any torrent added to one of the shared folders on the server.

When I attempt to add a torrent, either directly through either the client on the server or the Web UI or by adding the torrent to the designated shared folder, the torrent appears in Deluge, but it won't connect. I can download the same torrent using utorrent on my Windows laptop, so that is not the problem. The status bar states "No Incoming Connections!". I searched for as much information as I could online before posting, but most of what was mentioned did not apply. For instance, UPnP has been enabled on both Deluge and my router.

I've been working on this for several hours now, but I admit, I'm wandering in the dark here. I am also posting this on the Deluge forum, but similar posts seem to be directed away to forums such as this. Thank you for your assistance. I will be happy to provide any additional information you might find useful.

---

### Post by pompel9 on 2012-12-15
Try to flush the IP tables. I don't remember the code. That was the only way I could manage to download on torrent software in Ubuntu.

PS: Don't do this if you have set up rules.

---

### Post by eleutherian on 2012-12-15
I flushed the IP tables, but there was no change.

---

### Post by monkeybrain2012 on 2012-12-15
I see the warning sometimes, but it never actually impedes downloading or uploading, everything works fine so I kind of ignore it. Moreover, it only happens from time to time.

---

### Post by r2ramos on 2012-12-18
I have a very similar problem: can't download anything since i updated from ubuntu 12.04 32b to ubuntu 12.10 64b. I've tried installing, reinstalling, purging, (you name it) with deluge. Back in 12.04 i had no problem, but now it just wont work.

Triyng stuff, i installed transmission (had it unistalled when updated), but it wont download either.

Checked iptables, but there is no rule established, and the policies are set to ACCEPT.

Then i began thinking that my internet provider was blocking torrents, so i took the 3G modem (all i have for internet connection) and placed it in a laptop (borrowed) with ubuntu 12.04 32b, started deluge with the same torrents and it began downloading: so ruled out blocking by provider. Furthermore, i connected the modem to my PC (the one with 12.10 64b), and used ICS config for my LAN, then connected the laptop to it, and deluge in laptop is still able to download torrents (note that internet traffic goes trough the main PC, which confirms that there is no firewall blocking anything).

I made the same settings in both deluge's, since the one in the laptop worked, and still nothing.

So, i ran out of options and still cant get deluge to download anything. 

So please, i really need your help to solve this.


PS: i went from 12.04 to 12.10 before going from 32b to 64b, and can't say for sure but i think that deluge wasn't working in 12.10 32b either.

---

### Post by 420trvlr on 2012-12-27
I have installed/uninstalled/reinstalled Deluge and can not get it to work. The problem is I can't get it to connect to the internet. I have tried numerous things in that area with no success. 
It says no incoming connections at the bottom of the GUI, and going into preferences/network/test active port, and nothing... When I have tried to start a download, it doesn't show up as an option for download. 
I have it installed on another computer and it does a great job. Transmission is okay, but I would rather have Deluge.
I don't know if processor has anything to do with it, but this computer is 64x and the other computer is a very old 32x.

---

### Post by eleutherian on 2012-12-29
As an update, my Internet connection is fine. I also tried using qBitTorrent, but I can't get any torrent to connect with that program either. All of the torrents I have tested download just fine on my Windows computer. It seems that I can't get any torrent application to work in Ubuntu. Any thoughts?

---

### Post by hortstu on 2013-01-05
I'm having the same exact problem.  If anyone has come across a solution can you point me in the right direction?

---

### Post by kpheasey on 2013-01-16
Also having this problem.

Can't use any bittorrent client to download torrents.  However, my other computers, (windows 8, osx) can use clients.

Tried three clients, with nothing.

Using 12.04 LTS

---

