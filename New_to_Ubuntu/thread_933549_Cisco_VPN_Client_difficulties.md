---
title: "Cisco VPN Client difficulties"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by drumnmachn19 on 2008-09-29
So I've been using Ubuntu for about a month now, and my college requires that we use a Cisco VPN Client to connect to the wireless network.  I managed to install it using a patch that I found off a website, but everytime that I use the vpn after about 20 minutes of surfing the internet it crashes my computer.  I will be opening a link, and since i always have num-lock on, the caps and scroll-lock lights on my keyboard start flashing, and the only thing I can do is manually turn the power off to my computer.  If anyone can help me it would be greatly appreciated.

-Bruce

---

### Post by timcredible on 2008-09-29
you should just be able to download the linux client off cisco.com.  if the site requires a login, then ask your school's it department to download the client for you.  it shouldn't require any patch or anything, and should work fine.  i installed a cisco 3015 vpn a couple years ago at work and tested their linux client, it worked fine.  however, my workplace has since made a policy that only windows machines may connect to the network remotely, so i haven't used it in a while, but it worked before without issue, so it should do so now also, and if not, ask your school for help.

---

### Post by boghead on 2008-10-07
I am having the same symptoms running the latest patched Cisco client for x86_64 Hardy Heron (Cisco Client x86_64-4.8.01.0640-k9, Kernel 2.6.24-19-generic).  The patch was necessary to get the client to run on newer kernels, but it seems like it needs some more work.

My coworker is using the same client on an older Kernel, unpatched, and having no problems.

The hang seems to only happen when I have more than one simultaneous connection through the VPN tunnel.  I am able to browse/connect to multiple non-tunneled sites fine.  However, whenever I run two different network services through the tunnel, or open a web page that does a lot of simultaneous connections, the system hangs.

I saw the thread and wanted to contribute, but I have been using Linux for around 10 years (not a beginner).  If not here, where do you recommend I post to get this resolved (or at least reported as a bug to someone)?

---

### Post by boghead on 2008-10-08
According to this thread

[http://ubuntuforums.org/showpost.php?p=4488540&postcount=1](http://ubuntuforums.org/showpost.php?p=4488540&postcount=1)

the issue has to do with Intel wireless driver and the Cisco VPN Client.  I have done a few minutes of testing on a wired connection and it seems a lot more stable.  Hopefully this is a solid workaround.

---

### Post by Warren MacEvoy on 2009-06-22
I am having similar problems with Ubuntu 9.04:

Linux linux-stage 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009 i686 GNU/Linux

I have a wired network, but after roughly an hour of vpn connection, the systems hangs hard.

I can't use vpnc, because it does not support certificate authentification, which I must have for the connection.

---

