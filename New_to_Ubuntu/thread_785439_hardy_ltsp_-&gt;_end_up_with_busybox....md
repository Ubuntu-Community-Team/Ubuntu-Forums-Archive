---
title: "hardy ltsp -&gt; end up with busybox..."
date: 2008-05-07
forum: New to Ubuntu
---

### Post by byenary on 2008-05-07
Hello,

Just installed a hardy with the ltsp option, client's are connecting and booting but end up with just a commandline busybox while I was expecting a full gui... ?

What did i do wrong ?

---

### Post by YogiPaolo on 2008-05-13
I am having the same problem. Because I was kind of feverish and threw out a lot of "solutions", I'm not sure how I got things working.

Further, I should say that things are still not completely working. But, I did get past busybox and to a shell login (then broke things again).

Here are the things to look for. 
First, I noticed that /etc/exports was not set up to share /opt/ltsp/i386

Next, there was no lts.conf file (do a locate lts.conf to find an example file. There is an lts.conf place holder file that informs you of the proper location)

During boot, you can hold down ctrl + alt and press F1. This will allow you to see what is happening.

I noticed that the initrd kernel was getting the wrong IP. This was because my cable modem also had DHCP enabled. I thought that, because I created a subnet, that the DHCP servers would be ok. I was wrong, so I turned off the cable modem's DHCP server.

When I did that, the regular kernel would load, but give me a black screen with a blinky cursor for a couple minutes. When the cursor went away, I got a login prompt.

I have not been able to get this again, but I do have some thoughts.

First, I plan to chroot into the lts environment on the server and create a user. Then, I'm going to play with the settings in lts.conf.

Also, I'm not sure whether the x-server is set up to allow remote connections. It seems that some things that were supposed to be configured out of the box were not, so I'm studying the manual so that I can check everything out.

I'll post my results. I hope that helps.

Yogipaolo:popcorn:

---

### Post by 4leite on 2008-05-15
Not sure I can help much except to say that I am having similar problems. 

Trouble shooting is especially hard because hardy's config is different from debains and there is little to no good documentation.

If anyone has any good howto's or forums to link to that would be great. I have managed to boot to ubuntu (one step better than busybox) on the clients but cannont log in as anyone. Read somewhere that you need to chroot and change the root password, but this doesn't seem to have helped.

Any thoughts welcome...

---

### Post by YogiPaolo on 2008-05-18
Ok, I've gotten pretty far by obsessing all weekend, but I still don't have a working client. I may try getting rid of LDM and going with GDM using XDMCP

What happens now is that I get the LDM login screen. When I log in using my main account and/or a test user, my password goes through, the screen flashes from gray to black, then dumps me back to login.

I know that my password is being accepted because when I purposely type the incorrect password, i get red letters telling me "password incorrect". This is progress, because before, it would hang in "verifying password" for several minutes, then LDM would restart. I had to configure SSH and SSHD files to have a password accepted.

PARTIALLY SOLVED!!!!
I didn't want to erase what I typed up top, but I decided to try something before hitting post.

In the lts.conf file: /var/lib/tftproot/ltsp/i386/lts.conf
I added this line:

LDM_DIRECTX=True

this creates a direct, unencrypted TCP connection to the server. This implies that my issue is a problem with SSH and keys! I notice that when I run the ltsp-update-sshkeys, i get no output. No status messages, etc. That may have something to do with the issue. Perhaps the keys were never updated??!?!

This workaround got me to the desktop, but the problem is still there. This works for me, as I'm creating a multimedia kiosk situation around my apartment - picture frames, video mixing , etc. (sort of like the electric cool aid acid test without the drugs). Sorry for the digression.

The short story is that I have a thin client! 

Try messing with this setting and/or the ssh/sshd config to find out what's going on.....

Hope this helps!

---

### Post by ginjabunny on 2008-05-26
I have the same problem, this is my first try at LTSP which is on a fresh install on 8.04 desktop and I followed the instructions, but now I am stuck, clients PXE boot and I get the Ubuntu splash screen but after a couple of seconds I just get a busybox shell and initramfs prompt. I tried all day and gave up in the end, I just noticed this post so I'll try a few of the suggestions when I get time and report back if anything works.

I suppose I could install Edubuntu but I just wanted to see what LTSP is like and if I like it I may put it on my 8.04 server.

Is it a bug or something I've done or not done?

---

### Post by YogiPaolo on 2008-05-27
Hold down ctrl and press f2 (or f1) during boot so you can see what the scripts are doing. 

What is happening is that the pivot root hand-off is not succeeding. At this point, we don't know why.

My guess is that you have more than one DHCP server running. I'll assume that you have a cable or dsl router present on your network.

Get into the cable or dsl router and find the settings for DHCP server. Turn that setting to OFF. You can turn it back on again.

What I did was give my other computers static IP addresses and just let my LTSP box become my local dhcp server.

I hope this helps.

Yogipaolo

---

### Post by ginjabunny on 2008-06-02
I got it working, but I didn't fix it, I was trying to install from APT on a Desktop system which I gave up on, instead I downloaded the Alternate CD and installed as LTSP server and that works ok.

---

### Post by virilc on 2008-08-01
Experimented with LTSP Server 5 on Ubuntu Hardy Heron 8.04 i386

Problem:

Getting initramfs mount errors and just busybox when booting a client, no GUI, no joy :)

Solution:

1. Install nfs-kernel-server

   ```
$ sudo apt-get -y install nfs-kernel-server
```

2. Edit /etc/exports

   ```
$ sudo vim /etc/exports
```

3. Append the following on the bottom of /etc/exports and save it

   ***/opt/ltsp *(ro,no_root_squash,async)***

4. Restart nfs-kernel-server

   ```
$ sudo /etc/init.d/nfs-kernel-server restart
```

You may have to do: **sudo ltsp-build-client** again but maybe not.
After doing all this, I was able to get a GUI and everything works fine (flashdrive and cdrom/dvd/dvdrw drive and sound works!) except that I'm not sure why /opt/ltsp/i386/home is blank and I thought it would save everything in there instead of LTSP server's real /home/username directory. I may have to visit the manual again. ](*,)

Just try this and let me know if it works for you as well. Then just do me a favor and give me thanks by clicking on the :KS near the bottom-right corner of this box. Goodluck! :D

---

### Post by abg on 2008-08-07
I tried this then my problem was gone...
```
sudo ltsp-update-image
```

---

### Post by nimlc on 2008-09-11
> **abg said:**
> I tried this then my problem was gone...
```
sudo ltsp-update-image
```

Thanks a million abg. Its worked for me! :)

---

### Post by buntute on 2008-10-31
> Quote:
Originally Posted by abg View Post
I tried this then my problem was gone...

```

sudo ltsp-update-image
```

Thanks a million abg. Its worked for me!

Yes, me too. Thanks abg and nimlc.

---

### Post by wirelessben on 2009-09-17
sudo apt-get install openbsd-inetd

worked for me, as documented in [this thread]("http://ubuntuforums.org/showthread.php?t=686966"), comment #16. (Thanks to bobwdn.)

I had installed FOG after installing ltsp-server. Bad idea, as the FOG documentation warns. FOG uninstalled openbsd-inetd and replaced it with xinetd, but openbsd-inetd is what Ubuntu uses, so my LTSP broke.

---

### Post by coolnezz on 2012-08-13
Thank you!  I've been having this problem of getting stuck with the BusyBox screen.  Now I know why.  I disabled the DHCP on VMware's NAT adapter and it worked!


> **YogiPaolo said:**
> Hold down ctrl and press f2 (or f1) during boot so you can see what the scripts are doing. 

What is happening is that the pivot root hand-off is not succeeding. At this point, we don't know why.

[COLOR="Red"]**My guess is that you have more than one DHCP server running**[/COLOR]. I'll assume that you have a cable or dsl router present on your network.

Get into the cable or dsl router and find the settings for DHCP server. Turn that setting to OFF. You can turn it back on again.

What I did was give my other computers static IP addresses and just let my LTSP box become my local dhcp server.

I hope this helps.

Yogipaolo

---

