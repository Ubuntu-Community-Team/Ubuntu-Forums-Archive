---
title: "Ubuntu server 12.04 random re-boots?"
date: 2014-03-23
forum: New to Ubuntu
---

### Post by Craig71 on 2014-03-23
Hi Guys, thanks to some very helpful people on here, I have managed to setup a home meida server, and shared stuff across the network.

However, just lately, the server has started rebooting when I'm watching something streamed from it. What logs should I check to help pinpoint a problem?

I also have Webmin installed, but no idea what to check!

Any input is greatly appreciated.

---

### Post by 7sbaV8Kt5PTh on 2014-03-24
Craig,  I would start by checking /var/log/syslog and kern.log.  
What kind of hardware are you running on?  There could be something to that as well.

---

### Post by Craig71 on 2014-03-24
Thanks for your reply mate. I've tried looking at those logs, but I don't really know what I'm looking for!

The logs seem very big, and if I wanted to check what happened when it rebooted yesterday, how would I do that?

---

### Post by 7sbaV8Kt5PTh on 2014-03-24
There is a program called logrotate that takes a logfile, like syslog and copies them to syslog.1 on reboot.  after that, it compresses them to syslog.2.gz or some such.  The easiest way to look at the logs is to "grep" an errorfrom it:

grep -i error syslog

this means to "look in the file for the word "error" without case sensitivity from the file called syslog, and display the line".

You can also grep by date:  grep "Mar 23" syslog

Or even string them if you like:

grep "Mar 23" syslog | grep -i error

While this will help you look through a file, the simple truth is that it might not even have time to write the file before it locks up.  That can make finding the problem that much harder; this detective work requires patience, and tenacity.  And a fair amount of beer.

---

### Post by Craig71 on 2014-03-24
Thanks for that mate, this seems to be this issue (said like I know what I'm talking about)

```
Feb 21 19:45:41 server kernel: [   10.125200] EXT4-fs (sda1): re-mounted. Opts: errors=remount-roFeb 22 16:22:36 server kernel: [    9.297273] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 22 16:42:46 server kernel: [   10.473693] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 22 20:15:53 server kernel: [    9.005419] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 22 20:22:33 server kernel: [   12.571230] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 23 16:07:33 server kernel: [    9.774769] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 23 20:08:57 server kernel: [   12.492293] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 23 20:25:21 server kernel: [   12.209285] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 23 20:49:53 server kernel: [   11.845478] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 23 22:29:33 server kernel: [   11.289737] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 24 17:57:04 server kernel: [   10.641675] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 24 20:02:18 server kernel: [   11.431652] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 24 20:24:24 server kernel: [   11.745378] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 24 20:30:13 server kernel: [   11.961212] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 24 21:02:38 server kernel: [   11.220401] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 25 17:11:13 server kernel: [   11.024726] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 25 18:43:44 server kernel: [    9.657938] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 25 19:09:04 server kernel: [   12.717410] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 25 20:51:46 server kernel: [   12.568831] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 26 19:53:22 server kernel: [   11.103687] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 26 20:21:50 server kernel: [   11.727545] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 26 20:59:10 server kernel: [   11.206850] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 26 21:27:55 server kernel: [   13.590366] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 26 21:39:11 server kernel: [   10.582991] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 26 22:12:36 server kernel: [   10.699245] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 27 17:30:41 server kernel: [    9.490778] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 27 17:34:40 server kernel: [   10.592843] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 27 18:23:46 server kernel: [   10.672031] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 27 19:24:35 server kernel: [   10.699198] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 27 20:44:14 server kernel: [   10.077788] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 27 22:24:30 server kernel: [   11.527809] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 28 17:34:30 server kernel: [    9.614743] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 28 17:53:39 server kernel: [   12.365503] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 28 20:22:37 server kernel: [   10.893924] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 28 20:36:35 server kernel: [   11.772733] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 28 20:45:33 server kernel: [   10.051792] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 28 21:20:10 server kernel: [   12.425787] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar  1 12:31:58 server kernel: [    9.687779] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar  1 13:28:37 server kernel: [   11.440208] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar  1 14:01:43 server kernel: [   11.927278] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar  1 17:00:08 server kernel: [   10.631953] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar  2 19:14:30 server kernel: [   10.443159] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar  2 19:31:36 server kernel: [   12.899843] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar  2 19:35:02 server kernel: [    9.993547] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar  2 19:39:22 server kernel: [   10.897929] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar  2 20:24:29 server kernel: [    8.638166] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar  2 20:26:26 server kernel: [    9.647644] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar  2 21:12:13 server kernel: [   10.883254] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar  2 21:57:39 server kernel: [   10.196259] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar  3 19:45:42 server kernel: [   11.343575] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar  3 20:05:26 server kernel: [   11.865701] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar  4 20:12:12 server kernel: [    9.961682] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar  4 20:21:38 server kernel: [   11.759935] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar  5 20:30:40 server kernel: [    9.710639] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar  5 21:02:58 server kernel: [   12.845393] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar  6 19:32:46 server kernel: [    9.509647] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar  6 20:21:31 server kernel: [   10.844924] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar  6 20:41:27 server kernel: [   11.105607] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar  9 06:43:13 server kernel: [   10.256817] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar  9 07:29:00 server kernel: [   12.040812] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar  9 07:44:32 server kernel: [   10.682066] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar  9 07:52:27 server kernel: [   11.107388] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar  9 19:02:03 server kernel: [    9.943183] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar  9 19:08:56 server kernel: [    9.998771] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar  9 19:46:53 server kernel: [   10.057163] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar  9 20:12:48 server kernel: [   10.946195] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 10 20:37:29 server kernel: [    8.613840] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 10 20:50:44 server kernel: [    9.593317] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 11 12:02:40 server kernel: [    9.167021] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 11 19:29:37 server kernel: [    9.552651] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 11 20:00:09 server kernel: [    9.860708] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 11 21:12:40 server kernel: [   12.911542] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 11 21:36:39 server kernel: [   11.756674] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 12 08:06:05 server kernel: [   10.076257] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 12 08:28:26 server kernel: [   11.501057] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 12 08:33:22 server kernel: [   11.693811] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 12 08:57:45 server kernel: [   10.654341] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 12 09:46:14 server kernel: [   10.318217] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 12 12:55:10 server kernel: [    9.276527] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 12 13:08:30 server kernel: [   11.464757] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 12 13:14:28 server kernel: [   10.835640] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 12 13:43:26 server kernel: [   10.033685] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 12 19:56:14 server kernel: [   10.330550] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 12 20:31:20 server kernel: [    9.863574] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 12 20:32:36 server kernel: [    9.494686] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 12 20:36:55 server kernel: [   10.121144] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 12 20:39:52 server kernel: [    9.636684] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 13 19:21:26 server kernel: [    9.853600] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 13 19:53:11 server kernel: [   10.490566] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 14 19:46:29 server kernel: [   10.055939] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 15 19:54:17 server kernel: [    9.658792] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 15 21:52:24 server kernel: [   11.937799] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 16 19:13:12 server kernel: [    9.907020] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 16 19:29:06 server kernel: [    9.508300] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 16 19:52:48 server kernel: [    9.890015] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 16 20:41:37 server kernel: [    9.554132] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 16 21:22:46 server kernel: [   10.257066] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 17 20:06:59 server kernel: [   10.764396] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 18 19:24:17 server kernel: [    9.597767] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 18 20:01:13 server kernel: [   11.723755] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 20 19:56:12 server kernel: [   10.560474] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 20 20:13:08 server kernel: [   11.982369] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 20 20:36:34 server kernel: [   12.155563] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 22 15:14:55 server kernel: [    9.676397] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 22 15:29:16 server kernel: [   12.722668] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 22 19:22:09 server kernel: [   10.713911] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 22 20:37:37 server kernel: [   11.029974] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 22 20:55:01 server kernel: [   10.403805] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 23 06:59:43 server kernel: [   10.322143] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 23 08:40:48 server kernel: [   12.238527] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 23 09:19:06 server kernel: [   10.631750] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 23 15:38:33 server kernel: [    9.581583] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 23 17:38:47 server kernel: [   10.227311] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 23 19:15:51 server kernel: [   10.709428] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 23 19:26:42 server kernel: [   10.804600] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 23 20:02:27 server kernel: [   10.048972] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 24 14:30:57 server kernel: [    9.933040] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 24 19:08:55 server kernel: [   10.205449] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro



```

---

### Post by Craig71 on 2014-03-24
Would this point to sda1 (the Hd that ubuntu server is running from) having problems? 

It was an old drive I've  used to build my server. The one with all the media on is a new 2TB drive.

---

### Post by Craig71 on 2014-03-26
Anyone? I have checked the drive using 'badblocks' but this didn't show any errors.

---

### Post by 7sbaV8Kt5PTh on 2014-03-26
Craig,  I'm sorry, but I got nothing.  I don't know why it would be mounting and remounting.  
Can you boot from a Live CD and run fsck on /dev/sda1?  It might show something corrupt at the data level.

---

### Post by Craig71 on 2014-03-26
I'll give that a go mate, thanks. I'm guessing it's not a good idea to run the fsck command from the server directly?

---

### Post by bab1 on 2014-03-27
> **Craig71 said:**
> I'll give that a go mate, thanks. I'm guessing it's not a good idea to run the fsck command from the server directly?
You should always fsck an UNMOUNTED partition.  since this is the partition with the OS on it you need to start Ubuntu from the LiveCD so the /dev/sd1 will not be used.  Then you have to find the partiton's NEW NAME.  It will change.  Maybe it will be sdc1 or it could be scb1.  Then run  ```
sudo fsck <partition>
```

When it's all said and done, it looks like you will need to replace that hard drive.  It appears that the partition is mounting ***read only***.  This is usually do to the hard drive failing.

---

### Post by Craig71 on 2014-03-27
Yep, I'd thought from researching that the hard drive could be on the way out.

I'm thinking if putting a small SSD drive in, but I understand I can't use clonezilla for that, because the new drive will be smaller.

Is there any idiot-proof way of copying or cloning to a smaller drive? I really don't want to mess anything up!

---

### Post by bab1 on 2014-03-27
> **Craig71 said:**
> Yep, I'd thought from researching that the hard drive could be on the way out.

I'm thinking if putting a small SSD drive in, but I understand I can't use clonezilla for that, because the new drive will be smaller.

Is there any idiot-proof way of copying or cloning to a smaller drive? I really don't want to mess anything up!

I do a new install.  The configuration is really the only the hard part.  I normally just save the /etc directory since all the configuration files are there.  You should always document your configuration so you can review them in situations like this.  Take the time to write this out before the drive fails completely.  Isn't all the data on the other drive.

---

### Post by Craig71 on 2014-03-27
Cheers mate. I'll go HD shopping!

Yes, all the data is on the other drive.

---

