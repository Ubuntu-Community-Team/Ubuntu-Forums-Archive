---
title: "Best method to remote desktop to Ubuntu 12.10 from Win 7?"
date: 2013-01-02
forum: New to Ubuntu
---

### Post by g0nz0uk on 2013-01-02
Hello,

I have just installed Ubuntu 12.10 and need to remote desktop to it from my Windows 7 PC, how can I do this?  Is Xrdp any good?

Thanks

---

### Post by The Spectre on 2013-01-02
TeamViewer Work's Great...

[http://www.teamviewer.com/](http://www.teamviewer.com/)

---

### Post by g0nz0uk on 2013-01-02
Hi, I meant to say locally on the LAN not over the Internet.

---

### Post by siddharth007 on 2013-01-02
You can work on the console(terminal) remotely using the puTTy tool from Win7 and logging in through ssh.

---

### Post by g0nz0uk on 2013-01-02
I'm already using SSH, but the Ubuntu laptop is in a secure DMZ and I'd  like to use the internet via it too, hence the remote desktop.  Is it something that is is difficult to get working then?

---

### Post by TheFu on 2013-01-02
> **g0nz0uk said:**
> Hello,

I have just installed Ubuntu 12.10 and need to remote desktop to it from my Windows 7 PC, how can I do this?  Is Xrdp any good?

Thanks

The best way is with NX.  On Linux, run FreeNX and on Windows run the NoMachine NX client.  The NX protocol is 2x or 3x more efficient than either RDP or VNC AND it includes ssh, so you can use it to remote back from anywhere in the world safely.

BTW, I run my main desktop this way.  I've used it from 6,000 miles away or from inside the same room. It works fairly well.  I'm actually connected to my Linux desktop from a Win7 laptop right now writing this post.

You'll need to find an NX setup page and follow it - it is not the bonehead install due to the added pre-shared ssh keys for security. There are a few manual steps.  Shouldn't take more than 15 minutes to setup - 5 if you know what you are doing. ;)

---

### Post by Fahim Abdun-Nur on 2013-01-02
Any disadvantage of running the NomachineNX server?

---

### Post by TheFu on 2013-01-02
> **Fahim Abdun-Nur said:**
> Any disadvantage of running the NomachineNX server?

It isn't F/LOSS. The codebase is closed. I think there is a limited number of concurrent connections, so if you need more, open your wallet.  But I must admit I've never tried it either.  **I always choose F/LOSS over other options**, and with F/LOSS I choose MIT/Apache/BSD followed by LGPL over GPL.  Call it personal preference. I suppose it shows my business-friendly leanings.

I would prefer the F/LOSS client as well, but when I was looking for a good client, qtnx just wasn't working for me on the platform I had then. I've used qtnx in the last  month. It worked fine from Linux.  On Windows, I never got it working.

I should also point out that I do not run 12.10.  I'm strictly an LTS guy. I know this setup works on 12.04 perfectly ... er ... besides the audio and video stuff.  Another option is to get **spice** remote desktop [https://wiki.ubuntu.com/spice](https://wiki.ubuntu.com/spice) working, but I haven't been able to make that happen either. THAT will be really impressive, since it provides almost native graphics and audio performance to remote desktops.

---

### Post by g0nz0uk on 2013-01-04
Sorry for the delay guys,  I am very new to Ubuntu/Linux but am keen to learn.  I've installed many tools using sudo apt-get can I install FreeNX this way?

---

### Post by mlentink on 2013-01-04
Why not simply use vnc? Remote desktop is built in standard in ubuntu (open the dash and start typing remote...). Enable remote desktop, note the IP of the ubuntu machine, fire up a vnc viewer on your windows-box and get cracking.
Since you're within the same local network, the lack of security won't be of much concern, and i would guess this is by far the easiest method.

---

### Post by g0nz0uk on 2013-01-04
Hi, all I get when I do that is remote desktop client, not server?

---

### Post by TheFu on 2013-01-04
> **mlentink said:**
> Why not simply use vnc? Remote desktop is built in standard in ubuntu (open the dash and start typing remote...). Enable remote desktop, note the IP of the ubuntu machine, fire up a vnc viewer on your windows-box and get cracking.
Since you're within the same local network, the lack of security won't be of much concern, and i would guess this is by far the easiest method.

If you are within the same LAN, I agree, this is the easiest way and 99.999% of Linux users find this acceptable.  VNC has many more clients across more platforms and much better acceptance even if it is 2x-3x less efficient than NX. On a LAN, that probably will not matter at all. You should use VNC if this is your purpose.

If you would like to have a remote - as in* **over the internet*** - desktop, then with VNC, you need to add a VPN. VNC doesn't have much real security, no encrypted tunnel and just a port/password. All traffic can be captured and scene by the network provider, including the unencrypted password.  NX uses proven ssh tunnels and keys, so all the traffic has strong encryption.  VNC should be 2 minutes to setup.  NX is about 15 if you don't know what you are doing and less than 5 if you do. 
[B]
Over a trusted LAN connection, there is little to be gained using NX, VNC would be an easier choice.[/B]

Can you install freenx using apt-get - yes, but there are additional steps required to set it up to work. The packages, at least recent ones, didn't do or include everything necessary to create a working NX server.

---

### Post by g0nz0uk on 2013-01-04
You guys are very informative.  Where do I go to install VNC then, sorry to ask but when I search in Ubuntu all I see is Remote Desktop Client?

Kind Regards

---

### Post by zombifier25 on 2013-01-04
> **g0nz0uk said:**
> You guys are very informative.  Where do I go to install VNC then, sorry to ask but when I search in Ubuntu all I see is Remote Desktop Client?

Kind Regards

Looks like you found the remote desktop client. Ubuntu also has a preinstalled remote desktop server, and it's called "Desktop Sharing". Open it and the settings should be straightforward.

After that, get your Ubuntu machine's local IP address (if you don't know, click the network icon, choose "Connection Information" of something like that (I'm not using the English locale), open your VNC client installed on your Windows box and connect to your Ubuntu machine using the IP address (authenticate if necessary)

---

### Post by The Spectre on 2013-01-06
> **g0nz0uk said:**
> Hi, I meant to say locally on the LAN not over the Internet.

TeamViewer also has the ability to connect over a Local Area Network using IP Adresses (See Attached Screenshot).

---

### Post by mysteriousdarren on 2013-01-07
+1 for teamviewer. I've used it at work extensively and it just works.

---

### Post by TheFu on 2013-01-07
> **mysteriousdarren said:**
> +1 for teamviewer. I've used it at work extensively and it just works.

The only issues I have with Teamviewer are:
* Can I have the source code please? No?
* Does it work on the LAN when the Internet connection is broken? No?
* Trusting a 3rd party to provide access inside my LAN just seems **so very wrong.**

Besides that, I suppose it is a great tool to help access Grandma's PC over the internet, assuming grandma doesn't run Linux.

Sorry, but I'm extremely jaded from trusting any free service like this. Each of us has to determine who to trust.  While the teamviewer company hasn't made any well-known mistakes, they probably will.  Heck, RSA Security screwed up their FOBs and that was their MAIN business.  It is just a matter of time before a hack/hijack happens against teamviewer users.

---

### Post by AtariBaby on 2013-02-25
> **TheFu said:**
> The only issues I have with Teamviewer are:
* Does it work on the LAN when the Internet connection is broken? No?

Other points aside, I'm pretty sure this answer is yes.

---

### Post by AtariBaby on 2013-02-25
> **mlentink said:**
> Why not simply use vnc? Remote desktop is built in standard in ubuntu (open the dash and start typing remote...). Enable remote desktop, note the IP of the ubuntu machine, fire up a vnc viewer on your windows-box and get cracking.
Since you're within the same local network, the lack of security won't be of much concern, and i would guess this is by far the easiest method.

The built-in version lacks copy and paste, which I found pretty disappointing.

---

