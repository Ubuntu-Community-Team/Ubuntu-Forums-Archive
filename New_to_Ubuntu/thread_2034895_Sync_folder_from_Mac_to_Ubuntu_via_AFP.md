---
title: "Sync folder from Mac to Ubuntu via AFP?"
date: 2012-07-29
forum: New to Ubuntu
---

### Post by EtherealSky77 on 2012-07-29
Hi people - this is my problem: I've got PC1 (Mac) and PC2 (Ubuntu). I shared a folder on the mac... I can read and copy from this folder - no problem (AFP). But what If I would like to sync the two folders? I mean, sync all content from the PC1-folder to my PC2-folder? How should I do this? And can this be done automatically? Cheers and thank you :D

---

### Post by TheFu on 2012-07-29
"Automatically" can mean different things.  
For example, you can use rsync every 5 minutes via cron to push changes from A to B or B to A based on which has the newer file(s). I think most people would avoid this by just mounting the other file system on the opposite machine and access the files directly.  I'd do it with NFS [http://mactechnotes.blogspot.com/2005/09/mac-os-x-as-nfs-server.html](http://mactechnotes.blogspot.com/2005/09/mac-os-x-as-nfs-server.html) myself since both systems definitely support that.

There are lots of programs like rsync out there and lots of 3rd party  tools (dropbox, crashplan, etc) will handle sync between PCs on a LAN without eating WAN bandwidth.

I don't know anything about OSX network file systems, but Linux has a few different ways to sync disks at the block level using glusterFS and similar solutions that probably have OSX versions too. There's something called Netatalk that seems to be specifically for AFP.
[http://techpp.com/2010/07/05/dropbox-alternatives-sync-files-online/](http://techpp.com/2010/07/05/dropbox-alternatives-sync-files-online/) and 
[http://www.readwriteweb.com/cloud/2011/05/4-ways-to-build-your-own-dropbox.php](http://www.readwriteweb.com/cloud/2011/05/4-ways-to-build-your-own-dropbox.php) might help with some ideas too.

I don't mean to over simplify.  What have you looked at already?

---

### Post by EtherealSky77 on 2012-07-29
Well, Dropbox and Crashplan are not really an option (I think). My folder is packed with big and heavy video-files (movies), not really online material I think. They do LAN-sync without going online? I've heard good things about Rsync though. Does it do AFP also? :)

---

### Post by EtherealSky77 on 2012-07-29
Oh no. I can see that Samba is involved. I just can't deal with Samba. It's difficult and what not. Really, I've tried to share my folder on the Ubuntu machine - but it's nowhere to be found on the network. My share Mac-folder though can be seen and read from the Ubuntu (no problem there). I guess that I have to a working shared folder from PC2 also, in order to get Rsync to work - right? Sigh.

---

### Post by Lars Noodén on 2012-07-29
> **EtherealSky77 said:**
> Hi people - this is my problem: I've got PC1 (Mac) and PC2 (Ubuntu). I shared a folder on the mac... I can read and copy from this folder - no problem (AFP). But what If I would like to sync the two folders? I mean, sync all content from the PC1-folder to my PC2-folder? How should I do this? And can this be done automatically? Cheers and thank you :D

You could mount the remote system with [SSHFS](http://www.linuxjournal.com/article/8904).  That's fairly simple to use and needs only OpenSSH-server for set up.  The Ubuntu documentation is here:

[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

Or you could use rsync directly with SSH.  If you use a key and load it into an agent, then you only need to enter the passphrase once.  Using rsync with SSH is the normal way of operating.

Using rsync with SSH keys requires a little modification.  Something like this:

```

rsync -e "ssh -i ~/.ssh/key -t -l someuser" \
-av someuser@remote.example.org:/home/someuser/www/ /home/someuser/www/

```

---

### Post by stmiller on 2012-07-29
You may be interested in netatalk:

[http://netatalk.sourceforge.net/](http://netatalk.sourceforge.net/)

---

### Post by TheFu on 2012-07-29
> **EtherealSky77 said:**
> Oh no. I can see that Samba is involved. I just can't deal with Samba. It's difficult and what not. Really, I've tried to share my folder on the Ubuntu machine - but it's nowhere to be found on the network. My share Mac-folder though can be seen and read from the Ubuntu (no problem there). I guess that I have to a working shared folder from PC2 also, in order to get Rsync to work - right? Sigh.

Why would Samba be involved?  NFS is different from samba.  OSX had an issue seeing samba shares for in in Feb 2012. I think Apple patched that, but don't know. I gave back the Mac after a week. It felt too limiting to me, but I can see how many people would love it.  The copy/paste drove me nuts. I'm addicted to the built-in X/windows select/paste. Sorry, I digress.

Using rsync doesn't require any file sharing, just an ssh server needs to be running on one or both machines. ssh rocks.  rsync doesn't care about AFP either.  From my reading about AFP today, seems that NFS is a better, more stable file system sharing answer.

I saw that someone else recommended sshfs. sshfs is a FUSE (read really slow) file system. It is neato for special uses and I've used it lots, but **rsync over ssh** is a better answer.  [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync) explains all.  For the OSX side, you'll have to find a howto elsewhere, I guess. Apple probably calls it something else to make it easier for some, but more confusing to people like me. The main thing is there is a client and a server for ssh.  rsync runs through that tunnel by default, so you don't need an rsync-server (though that is possible too). In all my years, I've never setup an rsync server. Never needed one. I have used ssh and rsync almost every day for the last 15 yrs.

I'm a little confused. I do everything I can to avoid having multiple copies of large files on multiple machines, outside the backups.   Why not stream the content directly from the machine that hosts the files?   A 6 hour 1080i Olympics file recorded OTA is about 45G and streaming it to a network player works just fine. Smaller files aren't any issue either.   I must be missing something.

---

### Post by asmoore82 on 2012-07-30
> **EtherealSky77 said:**
> I've heard good things about Rsync though. Does it do AFP also? :)

Once you understand rsync, you will see that this is an impossible question.

You could use rsync to sync files from a local folder to a mounted remote folder, but this does not fulfil the purpose of rsync which is _remote_ sync. In other words, the act of mounting a network share is a convenient twisting of reality so that you can use it as if it were local.

Rsync works much better when something is _not_ local. It provides its own special way to communicate directly with the remote location. Even better, all modern versions of rsync default to using secure SSH transport to initialize this communication, so you typically put no extra requirements or open ports on the server that you are syncing with. In other words, most servers will have some form of SSH already open.

Rsync actually launches a process on each end of the remote sync to analyse the files locally and then the 2 processes communicate with each other to decide how to sync the files most efficiently. This is why no other form of rsync, such as on a mounted share of any kind, will be effective at minimizing network traffic.

---

### Post by EtherealSky77 on 2012-07-30
> **TheFu said:**
> I'm a little confused. I do everything I can to avoid having multiple copies of large files on multiple machines, outside the backups.   Why not stream the content directly from the machine that hosts the files?   A 6 hour 1080i Olympics file recorded OTA is about 45G and streaming it to a network player works just fine. Smaller files aren't any issue either.   I must be missing something.

Hi again and thank you for all the answers. Will look into it right now, but until then: Why? Well, I would prefer to stream the files - no question. But I use XBMC and it doesn't add the video files to the Library, when it's through for example UPNP. Streaming instead of synching? I would love that, but I need the Library (complete with folder art and everything) on PC2 :D

On second thought though: No streaming after all. I need PC2 to work on it's own if it has to. Mirror, mirror on the LAN - Willing or not, I'm your man :P

---

### Post by TheFu on 2012-07-30
> **EtherealSky77 said:**
> Hi again and thank you for all the answers. Will look into it right now, but until then: Why? Well, I would prefer to stream the files - no question. But I use XBMC and it doesn't add the video files to the Library, when it's through for example UPNP. Streaming instead of synching? I would love that, but I need the Library (complete with folder art and everything) on PC2 :D

On second thought though: No streaming after all. I need PC2 to work on it's own if it has to. Mirror, mirror on the LAN - Willing or not, I'm your man :P

I use XMBC and stream over NFS from an Ubuntu file server without any issues. The library DB (not any files) is located on the XBMC box.
I've also streamed over CIFS.  
I've never gotten DLNA streaming (UPnP) to work well on any platforms. Attempted it on windows, android, WD-TV-Live, XBMC, and straight Ubuntu. The issues for me were that series and movies were never current, always out of date.  Files deleted 4 months earlier would still show up and files recorded yesterday didn't.  That [B]plus the fact that UPNP is a huge security risk makes me stay away from it.

[/B]By now I hope you understand that I'm pushing NFS for your answer.You'll be happier.

---

