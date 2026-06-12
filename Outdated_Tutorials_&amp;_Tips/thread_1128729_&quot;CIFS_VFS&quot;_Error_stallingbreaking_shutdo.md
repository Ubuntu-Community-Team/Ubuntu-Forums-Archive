---
title: "&quot;CIFS VFS&quot; Error stalling/breaking shutdown - simple fix!"
date: 2009-04-17
forum: Outdated Tutorials &amp; Tips
---

### Post by rhcm123 on 2009-04-17
There have been many threads on the forums/net about the CIFS shutdown bug, such as [this]("https://lists.ubuntu.com/archives/ubuntu-server-bugs/2008-April/001093.html") and [this]("http://ubuntuforums.org/archive/index.php/t-458518.html").This bug can be easily found with several Google searches [here]("http://www.google.com/search?q=ubuntu+shutdown+cifs+vfs+server+not+responding&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a") and [here]("http://www.google.com/search?q=samba+stalls+on+shutdown&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a").

This bug occours in permanently mounted samba/cifs shares, due to a bug in the packages, in all versions of Ubuntu. The way the bug works is a problem with old code. The way the shutdown pattern works is it brings down the networking before it unmounts all permanent drives. You see, linux and the /etc/fstab were made in the 1970's, where the idea of a non-local drive was not yet established. Therefore, the code (runlevel 0) assumes that it's OK to take down networking before it attempts to unmount all filesystems. That's the way it's been forever, and it's unlikley to change.

So, when cifs and samba roll along, and you permanently mount them in the fstab, you run into a snag, and that is this bug. Duh the cifs server is not responding to the disconnect command - networking is offline! :shock:(although some log output indicates otherwise!) This causes stalls and lock-ups on the shutdown, and can delay it by as much as 10 minutes! This is not good, obviously enough! :)

The old way of fixing this was use a script (see the above thread) that would be generally a pain to implement (lotta chmoding, copying, a reboot, etc.) It could be done in an hour or so, but I didn't want to waste an hour, so i let it be.

I was considering other options (such as a version of rc.local that would run at shutdown) while I looked through the Internet for ideas. I found one finally that suited my tastes for simplicity and workability. Heck, took two seconds to get working permanently. It's this command, that i found [here:]("http://whereofwecannotspeak.wordpress.com/2007/12/25/unmount-samba-filesystems-before-shutdown-or-reboot/")
```
sudo ln -s /etc/init.d/umountnfs.sh /etc/rc0.d/K15umountnfs.sh
&& sudo ln -s /etc/init.d/umountnfs.sh /etc/rc6.d/K15umountnfs.sh
```

Too simple, but brilliant. It links the unmount nfs init command to the shutdown and reboot runlevels, and the runlevel runs these commands when it starts!
**ITS BLOODY GENIOUS CHAPS**

Enjoy, and have lots of fun not having to manually unmount your server every shutdown!

---

### Post by dmizer on 2009-04-19
This fix is also here: [http://ubuntuforums.org/showthread.php?t=293513](http://ubuntuforums.org/showthread.php?t=293513) but it's a bit outdated. The current version is available in that thread, but it's buried.

I'm going to update my CIFS tutorial (2nd link in my sig), and link to this thread for the "CIFS VFS: Server not responding" fix.

Thanks.

---

### Post by rhcm123 on 2009-04-20
> **dmizer said:**
> This fix is also here: [http://ubuntuforums.org/showthread.php?t=293513](http://ubuntuforums.org/showthread.php?t=293513) but it's a bit outdated. The current version is available in that thread, but it's buried.


That's exactly why I made this thread. The first forum results on google are a bit outdated/buried in old threads, so i felt like making a new one so that when somebody googles their problem they don't get read only archive-results.

---

### Post by gcastell on 2009-06-15
> **rhcm123 said:**
> That's exactly why I made this thread. The first forum results on google are a bit outdated/buried in old threads, so i felt like making a new one so that when somebody googles their problem they don't get read only archive-results.

Well, even after this fix, I still get the error. Any other idea or at least how can I debug it? This is really annoying.

---

### Post by gcastell on 2009-06-15
> **gcastell said:**
> Well, even after this fix, I still get the error. Any other idea or at least how can I debug it? This is really annoying.

Well, I should know better, the reason why I still get this error is because I am using Jaunty. dmizer post the solution in his [tutorial]("http://ubuntuforums.org/showthread.php?t=288534")

---

### Post by michaelzap on 2009-06-22
I still get this error on my laptop running 64-bit Jaunty. I've tried the fix linked above (both in addition to the pre-Jaunty fix and also without those symbolic links, since the post isn't clear whether you need to do both). I've also tried using "S14" links in both places instead of "K15" (which is what works for me on my Jaunty desktop; the only difference that I can think of between my desktop and laptop is that the laptop is connected via wifi).

Does anyone else have trouble with this still, and better yet has anyone figured out another solution?

---

### Post by dmizer on 2009-06-22
> **michaelzap said:**
> I still get this error on my laptop running 64-bit Jaunty. I've tried the fix linked above (both in addition to the pre-Jaunty fix and also without those symbolic links, since the post isn't clear whether you need to do both). I've also tried using "S14" links in both places instead of "K15" (which is what works for me on my Jaunty desktop; the only difference that I can think of between my desktop and laptop is that the laptop is connected via wifi).

Does anyone else have trouble with this still, and better yet has anyone figured out another solution?

Edit /etc/gdm/PostSession/Default and add /etc/init.d/umountnfs.sh to the top of the file like so:

```
#!/bin/sh
[COLOR="Red"]/etc/init.d/umountnfs.sh[/COLOR]

PATH="/usr/bin/X11:/usr/X11R6/bin:/opt/X11R6/bin:$PATH:/bin:/usr/bin"
OLD_IFS=$IFS

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS
  echo "$OUTPUT"
}

exit 0
```

---

### Post by michaelzap on 2009-06-22
> **dmizer said:**
> Edit /etc/gdm/PostSession/Default and add /etc/init.d/umountnfs.sh to the top of the file...

Thanks, but that's the fix I've tried that isn't working.

---

### Post by dmizer on 2009-06-22
Are you using Kubuntu?

---

### Post by michaelzap on 2009-06-22
> **dmizer said:**
> Are you using Kubuntu?

Nope. Straight vanilla (64-bit) Gnome, freshly installed on a new laptop just a couple nights ago. I'm mounting my shared network drives using the same fstab commands that I use on my desktop system, and there they unmount without any problems.

---

### Post by dmizer on 2009-06-22
Please post your fstab mount lines.

---

### Post by michaelzap on 2009-06-22
> **dmizer said:**
> Please post your fstab mount lines.

Thanks for trying to help me with this.

There are four of them, all similar to this:
```
//192.168.0.120/archivos /mnt/tooga cifs credentials=/home/zap/.smbpasswd,iocharset=utf8,uid=1000,gid=1000 0 0
```

---

### Post by dmizer on 2009-06-22
> **michaelzap said:**
> Thanks for trying to help me with this.

There are four of them, all similar to this:
```
//192.168.0.120/archivos /mnt/tooga cifs credentials=/home/zap/.smbpasswd,iocharset=utf8,uid=1000,gid=1000 0 0
```

Okay, for testing purposes, manually unmount all the shares (sudo umount /mount/point) and then comment out all the shares except this one. See if you still get the error on shutdown then. If that fixes the problem, try uncommenting the shares one by one until it breaks again. Post the line that caused the failure.

If that does not fix the problem, then try this:

1) unmount the share:
```
sudo umount /mnt/tooga
```
2) edit the fstab line so it looks like this:
```
//192.168.0.120/archivos /mnt/tooga cifs [COLOR="Red"]users,[/COLOR]credentials=/home/zap/.smbpasswd,iocharset=utf8,uid=1000,gid=1000 0 0
```
3) reboot, access the share, and then try shutting down.

See if that fixes your problem.

---

### Post by michaelzap on 2009-06-22
Given that these shares mount fine on both my desktop and laptop and unmount fine on the desktop, I didn't think there was any reason to troubleshoot my fstab file carefully. Fortunately I long ago learned that there are plenty of things that I don't understand that nevertheless are true, so I did what you suggested anyway. You may be on to something...

Here are my fstab entries:
```
//192.168.0.120/archivos /mnt/tooga cifs users,credentials=/home/zap/.smbpasswd,iocharset=utf8,uid=1000,gid=1000 0 0
//192.168.0.121/media/mp3s /mnt/mp3s cifs users,credentials=/home/zap/.smbpasswd,iocharset=utf8,file_mode=0777,dir_mode=0777,uid=1000,gid=1000 0 0
#//192.168.0.121/media/videos /mnt/videos cifs users,credentials=/home/zap/.smbpasswd,iocharset=utf8,file_mode=0777,dir_mode=0777,uid=1000,gid=1000 0 0
#//192.168.0.121/programas /mnt/programas cifs users,credentials=/home/zap/.smbpasswd,iocharset=utf8,file_mode=0777,dir_mode=0777,uid=1000,gid=1000 0 0
#//192.168.0.121/respaldos /mnt/respaldos cifs users,credentials=/home/zap/.smbpasswd,iocharset=utf8,file_mode=0777,dir_mode=0777,uid=1000,gid=1000 0 0
```

The ones that are commented out cause the unmounting error. What seems very odd to me is that the mp3s mount doesn't cause this problem but the videos mount does, even though they're subfolders of the same network share (media). Is there perhaps an error in my syntax that's causing lines after the mp3s mount to not be mounted properly?

I hadn't noticed that I had file_mode and dir_mode values for some of these also; maybe those are problematic?

Thanks again for your help.

---

### Post by dmizer on 2009-06-23
Please post the /etc/samba/smb.conf file from //192.168.0.121, I think I see the problem. You're trying to mount a path, not a share. By that, I mean you're mounting /media/mp3s and /media/videos but it should probably look like this:
```
//192.168.0.121/media /mnt/media cifs credentials=/home/zap/.smbpasswd,iocharset=utf8,file_mode=0777,dir_mode=0777,uid=1000,gid=1000 0 0
```
Then you can access both mp3s and videos under media. I think that what's happening is that cifs is unmounting /media/mp3s and is hanging on /media/videos because "media" is common between both of them. I'm not sure though without taking a look at your smb.conf file.

---

### Post by michaelzap on 2009-06-23
You are absolutely right! When I mount those two directories as one share ("media"), it unmounts without a hitch using the Jaunty fix above. THANK YOU for figuring that out!

This share is an HP Media Vault drive, so although it probably has an smb.conf file it's not all that easy to get at and I'd be afraid to mess with it.

I'll just mount this share as media and be glad it works that way. I wonder why it works as individual directories on my desktop. I've been mounting these shares that way since Hardy, but I guess I won't be in Koala.

---

### Post by michaelzap on 2009-06-24
> **michaelzap said:**
> You are absolutely right! When I mount those two directories as one share ("media"), it unmounts without a hitch using the Jaunty fix above. THANK YOU for figuring that out!


Rats! It's no longer working for me now that I created two shares(mp3s and videos) on the network drive and I'm mounting them separately. What the heck?!?

---

### Post by michaelzap on 2009-06-24
Here are my fstab mount lines:```
//192.168.0.120/archivos /mnt/tooga cifs users,credentials=/home/zap/.smbpasswd,iocharset=utf8,uid=1000,gid=1000 0 0
//192.168.0.121/mp3s /mnt/mp3s cifs users,credentials=/home/zap/.smbpasswd,iocharset=utf8,file_mode=0777,dir_mode=0777,uid=1000,gid=1000 0 0
//192.168.0.121/videos /mnt/videos cifs users,credentials=/home/zap/.smbpasswd,iocharset=utf8,file_mode=0777,dir_mode=0777,uid=1000,gid=1000 0 0
//192.168.0.121/programas /mnt/programas cifs users,credentials=/home/zap/.smbpasswd,iocharset=utf8,file_mode=0777,dir_mode=0777,uid=1000,gid=1000 0 0
//192.168.0.121/respaldos /mnt/respaldos cifs users,credentials=/home/zap/.smbpasswd,iocharset=utf8,file_mode=0777,dir_mode=0777,uid=1000,gid=1000 0 0
//192.168.0.121/DVDs /mnt/DVDs cifs credentials=/home/zap/.smbpasswd,iocharset=utf8,file_mode=0777,dir_mode=0777,uid=1000,gid=1000 0 0
```
If I manually unmount the mp3s share before restarting, I get no error. The same is not true if I manually unmount the videos share. These are now separate shares on the network drive, so this is really strange.

---

### Post by dmizer on 2009-06-24
Okay, please post the smb.conf file from 192.168.0.121

---

### Post by michaelzap on 2009-06-24
Here it is:
```
# cat smb.conf 
[global]
        netbios name = Vicio
        server string = "Vicio"
        workgroup = COMPAS
        security = user
        guest account = guest
        log file = /var/log/samba.log
        socket options = TCP_NODELAY SO_RCVBUF=65536 SO_SNDBUF=65536
        encrypt passwords = yes
        use spnego = no
        client use spnego = no
        host msdfs = no
        interfaces = lo eth0 eth1 eth2 br0
        qos enable = no
        level1 file extensions = 
        level2 file extensions = 
        os level = 20
        preferred master = auto
        domain master = auto
        local master = no
        domain logons = no
        log level = 0
        max log size = 960
        null passwords = yes
        wins server = 
        passdb backend = tdbsam
        private dir = /shares/Volume1/__pdc
        map to guest = bad user

[programas]
       comment = 
       path = /shares/Volume1/programas
       writeable = yes
       browsable = yes
       inherit permissions = yes
       inherit acls = yes
       msdfs root = no
       invalid users = 
       read list = 
       write list = "zap", "xu", 

[mp3s]
       comment =  
       path = /shares/Volume1/mp3s
       writeable = yes
       browsable = yes
       inherit permissions = yes
       inherit acls = yes
       msdfs root = no
       invalid users = 
       read list = 
       write list = "zap", "xu", 

[videos]
       comment = 
       path = /shares/Volume1/videos
       writeable = yes
       browsable = yes
       inherit permissions = yes
       inherit acls = yes
       msdfs root = no
       invalid users = 
       read list = 
       write list = "zap", "xu", 

[DVDs]
       comment =  
       path = /shares/Volume2/DVDs
       writeable = yes
       browsable = yes
       inherit permissions = yes
       inherit acls = yes
       msdfs root = no
       invalid users = 
       read list = 
       write list = "zap", "xu", 

[respaldos]
       comment =  
       path = /shares/Volume2/respaldos
       writeable = yes
       browsable = yes
       inherit permissions = yes
       inherit acls = yes
       msdfs root = no
       invalid users = 
       read list = 
       write list = "zap", "xu", 
# 

```
See anything funny?

---

### Post by dmizer on 2009-06-24
Lots of unusual options, but I don't see anything that is glaringly wrong. Any of the options without an entry (level1 file extensions, wins server, etc) should probably be removed (make a backup first), but that probably won't affect your particular issue.

Try this. Edit /etc/gdm/PostSession/Default again and include an explicit unmount for the mp3s like this:
```
#!/bin/sh
[COLOR="Red"]umount /mnt/mp3s[/COLOR]
/etc/init.d/umountnfs.sh

PATH="/usr/bin/X11:/usr/X11R6/bin:/opt/X11R6/bin:$PATH:/bin:/usr/bin"
OLD_IFS=$IFS

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS
  echo "$OUTPUT"
}

exit 0
```

---

### Post by michaelzap on 2009-06-24
Adding an explicit unmount command does in fact work. So that's certainly good news for me (no more rough power-downs), but it still doesn't explain what's going on. The only obvious difference in this mount from the others is that it has a number in it; could the script somehow be broken when passed a mount point name with a number?

---

### Post by dmizer on 2009-06-24
> **michaelzap said:**
> Adding an explicit unmount command does in fact work. So that's certainly good news for me (no more rough power-downs), but it still doesn't explain what's going on. The only obvious difference in this mount from the others is that it has a number in it; could the script somehow be broken when passed a mount point name with a number?

Nope, a number won't make a bit of difference. The only other thing I can think of would be that perhaps the data volume in that or one of the other shares is causing the unmount to be too slow, so the rest of the logout script completes before the mp3 share is completely unmounted.

Complete guess though. I really have no idea why you would encounter that problem on that share only.

---

### Post by michaelzap on 2009-06-24
> **dmizer said:**
> Nope, a number won't make a bit of difference.
It certainly shouldn't...

> **dmizer said:**
> The only other thing I can think of would be that perhaps the data volume in that or one of the other shares is causing the unmount to be too slow, so the rest of the logout script completes before the mp3 share is completely unmounted.
I thought of that also, and I've tried reordering the shares in fstab to see if that matters (it doesn't). All but one of these shares is on the same drive, and this share's contents were in the media share before (combined with videos), so I can't figure it out.

> **dmizer said:**
> I really have no idea why you would encounter that problem on that share only.Me either!

---

### Post by dmizer on 2009-06-24
Is there something making use of the mp3s folder when you log off? If you have something like Amarok or Listen open or any kind of local database using the files, it will not unmount correctly.

That's the only other idea I have.

---

### Post by michaelzap on 2009-06-24
> **dmizer said:**
> Is there something making use of the mp3s folder when you log off? If you have something like Amarok or Listen open or any kind of local database using the files, it will not unmount correctly.

That's the only other idea I have.

Nope. I use Exaile to play mp3s, but this happens if I just boot up and then shut down, and it didn't happen when these same mp3s were in the media share with my videos. And of course mp3s does unmount if the command is manual or explicit, just not automatically...

---

### Post by measekite on 2009-06-26
> **rhcm123 said:**
> There have been many threads on the forums/net about the CIFS shutdown bug, such as [this]("https://lists.ubuntu.com/archives/ubuntu-server-bugs/2008-April/001093.html") and [this]("http://ubuntuforums.org/archive/index.php/t-458518.html").This bug can be easily found with several Google searches [here]("http://www.google.com/search?q=ubuntu+shutdown+cifs+vfs+server+not+responding&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a") and [here]("http://www.google.com/search?q=samba+stalls+on+shutdown&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a").

This bug occours in permanently mounted samba/cifs shares, due to a bug in the packages, in all versions of Ubuntu. The way the bug works is a problem with old code. The way the shutdown pattern works is it brings down the networking before it unmounts all permanent drives. You see, linux and the /etc/fstab were made in the 1970's, where the idea of a non-local drive was not yet established. Therefore, the code (runlevel 0) assumes that it's OK to take down networking before it attempts to unmount all filesystems. That's the way it's been forever, and it's unlikley to change.

So, when cifs and samba roll along, and you permanently mount them in the fstab, you run into a snag, and that is this bug. Duh the cifs server is not responding to the disconnect command - networking is offline! :shock:(although some log output indicates otherwise!) This causes stalls and lock-ups on the shutdown, and can delay it by as much as 10 minutes! This is not good, obviously enough! :)

The old way of fixing this was use a script (see the above thread) that would be generally a pain to implement (lotta chmoding, copying, a reboot, etc.) It could be done in an hour or so, but I didn't want to waste an hour, so i let it be.

I was considering other options (such as a version of rc.local that would run at shutdown) while I looked through the Internet for ideas. I found one finally that suited my tastes for simplicity and workability. Heck, took two seconds to get working permanently. It's this command, that i found [here:]("http://whereofwecannotspeak.wordpress.com/2007/12/25/unmount-samba-filesystems-before-shutdown-or-reboot/")
```
sudo ln -s /etc/init.d/umountnfs.sh /etc/rc0.d/K15umountnfs.sh
&& sudo ln -s /etc/init.d/umountnfs.sh /etc/rc6.d/K15umountnfs.sh
```Too simple, but brilliant. It links the unmount nfs init command to the shutdown and reboot runlevels, and the runlevel runs these commands when it starts!
**ITS BLOODY GENIOUS CHAPS**

Enjoy, and have lots of fun not having to manually unmount your server every shutdown!
I am really new at this so forgive me.

I did find out that the shutdown process drops the network and then tried to unmount the mounted network shares which causes it to hang for a couple of minutes.

I manage (stumbling a little) to write a script that umounts (in reverse order of the fstab mount lines) then went to terminal to excute it.

```
sudo /home/username/scripts/dismount.sh
```

**[COLOR=Red]This worked fine.  Now shutting down was fast and no errors.[/COLOR]**

Please (detailed step by step) what files and how do I need to put this working script in so it will go automatically.

Thanks in advance :popcorn:

---

### Post by dmizer on 2009-06-26
> **measekite said:**
> Please (detailed step by step) what files and how do I need to put this working script in so it will go automatically.

See post 7: [http://ubuntuforums.org/showpost.php?p=7500797&postcount=7](http://ubuntuforums.org/showpost.php?p=7500797&postcount=7)

---

### Post by rhcm123 on 2009-08-12
Also, i noticed that if you switch interfaces that the server is interfacing on, this fix fails, unless you have used the share,

For instance, if i mount the share over ethernet on my lappy (eth1) then unplug and go downstairs (eth0), this fix fails. However, if i go downstairs, then open a file on the server, this fix works. Hope this helps some of you.

---

### Post by AlexanderDGreat on 2009-09-11
Help, there's no K15umountnfs.sh in my /etc/rc0 and /etc/rc6

---

### Post by dmizer on 2009-09-11
> **AlexanderDGreat said:**
> Help, there's no K15umountnfs.sh in my /etc/rc0 and /etc/rc6

See post seven: [http://ubuntuforums.org/showpost.php?p=7500797&postcount=7](http://ubuntuforums.org/showpost.php?p=7500797&postcount=7)

---

### Post by AlexanderDGreat on 2009-09-11
Hey dmizer, thanks for that link, I solved my problem now.

My situation: Ubuntu 9.04 simple file server to Windows, Ubuntu, and Mac boxes, 10 cpus in our network.

I would just like to tell you to keep up your good work, helping average people solve problems in Ubuntu.

Your work is very much appreciated.

Thanks! =)

---

### Post by ubradford on 2009-12-06
I found a fix that works on Karmic and wireless (WPA). I posted the fix here:
[http://ubuntuforums.org/showthread.php?p=8449027#post8449027](http://ubuntuforums.org/showthread.php?p=8449027#post8449027)

---

### Post by a3101 on 2010-01-21
Hello

For me these fixes didn't work either. But I did find something strange.. at least imo...

I have 9.10 in both my desktop and media pc. In media pc for some reason there haven't been any freezes in shutdownt. For desktop I keep having this error and it's annoying. Only thing that basically is different with these pc's is the media pc has eth/wlan converter and the desktop pc has direct wlan.

So I switched the eth/wlan converter to my desktop pc and... the unmount problem disappeared! Ubuntu shuts down perfectly... But this isn't a long term solution... 

All my sources locate in linkstation nas. I have mounted them under home folder; Documents, Music, Pictures etc... (finnish names). So both pc's use same files.

I'm a noob, do you have any idea or fix for this...

My fstab:
```

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb6 :
UUID=c2008c0c-4bff-405b-b759-a228f7f3671e / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sdb7 :
UUID=70984964-1dc9-4936-a302-6260742740c0 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sdb1 /media/MEDIA ntfs-3g defaults,locale=fi_FI.UTF-8 0 0
/dev/sda2 /media/BACKUP ntfs-3g defaults,locale=fi_FI.UTF-8 0 0
//192.168.11.2/Kuvat      /home/kari/Kuvat      cifs credentials=/home/.smbcredentials,dir_mode=0777,file_mode=0777  0  0
//192.168.11.2/Mp3        /home/kari/Musiikki   cifs credentials=/home/.smbcredentials,dir_mode=0777,file_mode=0777  0  0
//192.168.11.2/Email      /home/kari/Email      cifs credentials=/home/.smbcredentials,dir_mode=0777,file_mode=0777  0  0
//192.168.11.2/Asiakirjat /home/kari/Asiakirjat cifs credentials=/home/.smbcredentials,dir_mode=0777,file_mode=0777  0  0
//192.168.11.2/Video      /home/kari/Videot     cifs credentials=/home/.smbcredentials,dir_mode=0777,file_mode=0777  0  0

```/etc/gdm/PostSession/Default file:
```

#!/bin/sh
/etc/init.d/umountnfs.sh

exit 0

```

---

### Post by a3101 on 2010-01-23
seems that no one's interested of this thread anymore... :/

---

### Post by Glasairman on 2010-01-25
I have been repairing this NM mess in every release since 8.04; every new release meant doing it all again.

And finally - the end solution is so simple:

***_Install WICD to replace NM_*** (gets dumped automatically)

That`s it !!!!

---

### Post by a3101 on 2010-01-28
> **Glasairman said:**
> I have been repairing this NM mess in every release since 8.04; every new release meant doing it all again.

And finally - the end solution is so simple:

***_Install WICD to replace NM_*** (gets dumped automatically)

That`s it !!!!


Well yes, WICD seems to help as you said. Now I just have a problem connecting to wlan with WICD. It was working for some time, but now it can't find network suddenly after switching pc on this morning.. I have ndiswrapper for buffalo g pci card (broadcomb43). Well, this is linux.. have to seek for wicd threads then... :)

---

### Post by a3101 on 2010-02-14
> **Glasairman said:**
> I have been repairing this NM mess in every release since 8.04; every new release meant doing it all again.

And finally - the end solution is so simple:

***_Install WICD to replace NM_*** (gets dumped automatically)

That`s it !!!!

I got it. I had to play a bit with packages, don't remember what it was exactly, but the shutdown goes ok now (1.6.1). Definetily the nm has a major bug init. How noob is that.

A new problem occurred with WICD though, and this is a bit funny I think. Now the startup doesn't work. I think the fstab mounts are done before the actual network connection to wlan host has been established. So I have to manually do sudo mount -a.

What to do? Somehow adjust the startup priorities or what? :D

---

### Post by tonywhelan on 2010-02-26
> **dmizer said:**
> Edit /etc/gdm/PostSession/Default and add /etc/init.d/umountnfs.sh to the top of the file like so:

```
#!/bin/sh
[COLOR="Red"]/etc/init.d/umountnfs.sh[/COLOR]
}
exit 0
```

The above fix worked for me with Karmic (9.10, i386 version). The commonly quoted fix of renumbering file K15umountnfs.sh had worked for me on earlier versions but not on Karmic.

Many thanks to dmizer for this.

---

### Post by a3101 on 2010-03-02
> **tonywhelan said:**
> The above fix worked for me with Karmic (9.10, i386 version). The commonly quoted fix of renumbering file K15umountnfs.sh had worked for me on earlier versions but not on Karmic.

Many thanks to dmizer for this.

Doesn't work for me. Sorry for yelling, BUT GETTING SO SICK'N TIRED for this...

1. Network manager hanging problem in shutdown when using wlan (with eth0 works like a charm) but when I disconnect eht/wlan converter cpu will hang with wlan...
2. WICD connecting to WLAN AFTER mount of network drives, so THIS ISN'T WORKING EITHER... This has been known and reported in 2008 already ([https://bugs.launchpad.net/wicd/+bug/179654](https://bugs.launchpad.net/wicd/+bug/179654)), but no fix for this in WICD... In that launchpad site, why not just run sudo mount -a instead of difficult looking and long script ???

[http://ubuntuforums.org/showthread.php?t=1072265](http://ubuntuforums.org/showthread.php?t=1072265) this might work, but first would have to learn what they mean by executables, and how to run that as root.. BUT, there's also some other problems in WICD, sometimes looses connection and only reboot helps.. don't want that either.

Loosing my head.

---

