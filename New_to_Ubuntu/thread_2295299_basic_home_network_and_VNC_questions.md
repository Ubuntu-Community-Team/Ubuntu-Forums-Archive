---
title: "basic home network and VNC questions"
date: 2015-09-17
forum: New to Ubuntu
---

### Post by jrh74 on 2015-09-17
I am very new to linux and would like to learn ubuntu on my desktop using my windows labtop and VCN.  My simple system is as described below.  Could anyone help me with the following questions or recommend sources for further information.  I believe it is the windows/linux connection that is contributing to my confusion.

1.  I am able to get onto the internet from both computers.  Do I need to do anything else to be able to say I have a fully functioning network.
2.  Once I have a functioning network, what commands (or graphic interface procedure) will give me information (conformation) regarding the completeness of my network.
3.  Comment on VCN speed and security in view of the fact that the connection will not be over the internet.
4.  What is the best free VCN system or are there more recent methods that are better.

My system consists of desktop with ethernet connection to router.  The dektop is capable of being booted with ubuntu 14.04 on a 1000g hard drive or windows 7 on a seperate 500g hard drive.  The laptop is a lenovo yoga pro2 with windows 10 and is connected wirelessly to router.  I am also able to print wirelessly to a brother printer from the laptop and the desktop when in windows.  I have not yet been able to work out printing from the desktop with ubuntu.  I can connect to the internet with laptop and desktop with either or windows or ubuntu.


Thanks for you attenton, John

---

### Post by Geoffrey_Arndt on 2015-09-17
Basic instruction video here:   [URL="https://www.youtube.com/watch?v=gemAacoe78U"]https://www.youtube.com/watch?v=gemAacoe78U


[/URL]

---

### Post by DuckHook on 2015-09-18
Hi jrh74 and welcome to Ubuntu and the forums.

Though your questions may appear straightforward, you are actually asking complex questions requiring considerable in-depth knowledge.

To begin with, there's nothing simple about VNC and I'm wondering why you want to learn Ubuntu/Linux through such an awkward setup? If you are still intent on doing so, then [here]("https://help.ubuntu.com/community/VNC") is the official Ubuntu Community Help page for VNC. You may note that VNCs come with all sorts of setup and configuration requirements, and (more importantly to my mind) all sorts of security concerns that need proper and aggressive counter-insurgency measures. A relative of mine got owned through a combination of open VNC ports and weak passwords.

In my opinion, a better strategy would be to install Ubuntu in a Virtual Machine on your Windows laptop and run it as a VM. That way, it is available to you even when you are not connected by ethernet/WIFI to your home network. Nor would you need to leave ports open and risk the dark side of the Net with a VNC. VM instructions [here]("https://help.ubuntu.com/community/VirtualMachines").

I don't know your detailed needs, and maybe a VNC is necessary in your case. But based on what you have stated, and the fact that you want to *learn* Ubuntu (rather than use it in some production capacity), I believe that the VM route is the safest, easiest and simplest solution.

---

### Post by HermanAB on 2015-09-19
Also, VNC is the most common way in which new Ubuntu users get their computers compromized.  For some odd inexplicable reason, new users always want to use VNC.  Older users know better and use SSH instead.

---

### Post by DuckHook on 2015-09-19
> **HermanAB said:**
> Also, VNC is the most common way in which new Ubuntu users get their computers compromized.  For some odd inexplicable reason, new users always want to use VNC.  Older users know better and use SSH instead.+1

There is a place for VNC, but it's not what most people think (ie: remote interactive computer education). VNC tunneled through SSH is much safer. But I wouldn't even open SSH to the big bad Net these days without a port knocking setup. My old paranoia feels vindicated after Heartbleed.

---

### Post by fj401971 on 2015-09-19
1.  Yes, your network seems to be fully functioning.
2. Completeness?  I'm not sure what you mean.
3. The connection and speed will be the fastest they could ever be with your given setup.  The only way to get it faster is to hook both computers up via Ethernet, but the speed gain will most likely be negligible.  
4.  Google VNC for windows.  There's a lot out there.  

Your connections will not be available outside of your home network unless you make modifications to your router.  So your connections are safe and sound.  If you'd like to access your computers outside of your home, then that is a different story.

---

