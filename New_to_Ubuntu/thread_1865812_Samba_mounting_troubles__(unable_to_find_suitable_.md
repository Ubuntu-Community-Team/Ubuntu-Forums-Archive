---
title: "Samba mounting troubles  (unable to find suitable address etc.)"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by rockstar1009 on 2011-10-20
I'm attempting to stream mp3s from my Windows HTPC (Vista Ultimate) to my 11.10 Kubuntu laptop.  I do have access to the HTPC, but VLC refuses to play networked files and Amarok downloads them before playing them.  Searching around the Google indicates that mounting samba shares is the way around these issues.

However, about a dozen different walkthroughs later, I'm still lost.  Part of the problem is each one says to enter the same basic info in fstab, but with each with slightly different parameters (IE some reference a config file, others don't).  I'm running into constant terminal errors (unable to resolve host, unable to find suitable address etc.) when attempting to mount via CLI.  I'm also unable to mount whether using using the server file path or the IP address.

I'm presently set up as per the "official" ubuntu guide [here]("https://wiki.ubuntu.com/MountWindowsSharesPermanently").  I can usually get through the guide without error, but even if I edit fstab without terminal errors, I get errors at the mount -a command.  Usually *mount error(13): Permission denied* but once I *received mount error(115): Operation now in progress* as well.  If I don't get those ones, it's *mount error: could not resolve address for ROCKSTAR-HTPC: Unknown error*.

Here's my present fstab entry:

```
//ROCKSTAR-HTPC/i /mnt/HTPC cifs credentials=/home/rockstar/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```or as an alternate

```
//192.168.1.110/i /mnt/HTPC cifs credentials=/home/rockstar/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```The HTPC name is in all caps as it appears in Windows, but initial cap as it appears in KDE.  I've tried all variations of capitalisation, and none really seem to matter, but an uppercase I: drive leads to *X error: BadWindow* while a lowercase i: drive lets me close kate without terminal errors.  (I've set the entire drive to be shared - is this causing issues?  Should I do separate content mounts like i/Music & i/Television etc. instead?)

Windows can't see the Linux laptop (it does see an unknown device, which I suspect to be the laptop), but I'm not sure if that matters, but I'm trying to list EVERYTHING here in an effort to be thorough.  :)  (And yes, I've adjusted all the security policy settings in Windows needed for Linux access, but like I said, I'm only interested in Doze via Nix access; Nix via Doze access isn't my concern).

All that said, I am now here to humbly kneel before you Linux gods and ask your assistance in helping me sort out this mess.  I fully expect it to be a simple n00b oversight (that's the way it always works for me :(), and I am ready to be publicly shamed.  Please, please PLEASE help me to either A) get VLC/Amarok to play networked files without downloading them or B) help me mount my networked drives without issue.  (Or C - advise an alternative that can work cross platform - I've used PS3 media server for my HTPC > PS3, and wished there was an equally simple, lightweight option to stream to Linux, but if one exists, I haven't found it yet).  Thanks!

---

### Post by rockstar1009 on 2011-10-26
BUMP

I still can't figure this one out, but I have managed to manually mount the drive using the command

```
sudo mount -t cifs -o username=samba,password=P455W0RD //192.168.1.110/i /mnt/HTPC
```

However, I still get errors when trying to mount the same Windows share (192.168.1.110/i) to mnt/HTPC through fstab.  I'm here on Absolute Beginners because I'm still new to this, and I can't figure out why mount -t works but mount -a gives errors.  I'm sure I'm making some simple syntax error in my fstab setup I pasted in the first post, but I can't find it.  However, I'm also unsure if it may be worth scrapping the fstab route and using the command pasted in this post as a startup script, but I've never done a startup script before.  I'm hoping one of the experts here could give me some pointers on start scripts, or tell me why running this command as a start script would be a bad idea.

Thanks!  :)

---

### Post by audiomick on 2011-10-26
Hi. I don't know if this will help, but you could have a look here
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

Hope it helps. ;)

---

### Post by rockstar1009 on 2011-10-29
@audiomick - Thanks for the link, but that was one of the sites I visited.

I finally found my issue though - I knew it would be something simple and n00bish.  I changed my fstab entry from this

```

//ROCKSTAR-HTPC/i /mnt/HTPC cifs credentials=/home/rockstar/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```to this

```
//ROCKSTAR-HTPC/i /mnt/HTPC cifs username=samba,password=P455W0RD  0 0
```which worked.  Suddenly I realised the problem had to lie within my credentials file, and sure enough I found an extra space in the password line.  Deleting the space solved everything.  On the one hand I feel great having solved this mystery, but on the other hand I feel like giving myself a painful atomic facepalm for getting stuck up on something so simple.  :)

I'm updating the title as solved, and hoping that further searches for these mounting error codes might be solved by fixes as simple as taking care of whitespace issues, too.

---

