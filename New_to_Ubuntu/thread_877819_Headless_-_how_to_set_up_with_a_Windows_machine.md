---
title: "Headless - how to set up with a Windows machine?"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by JustGus on 2008-08-02
Hi,

Long story short - I've been meaning to run my new, dedicated Ubuntu machine headless, but have had a monitor, which I've just learned I'll need to return in the next couple days.  So I need to quickly figure out how to install a solution that allows me to run it from a Vista laptop.
I'm just getting to grips with Ubuntu (if an app isn't packaged as a .deb file, installation is bewildering for me at this stage) so was wondering if anyone can point me to a step-by-step installation guide for a VNC app so I can take control of it through my other machine.  Something like RealVNC Free would be great, but can only find it as a tar file.  Any steps to walk me through installation would be hugely appreciated!
Cheers,
Gus

---

### Post by sharks on 2008-08-02
did you search for it in synaptic (system--administration). if u have downlaoded a tar file , extract it. open terminal , type **cd /the/location/of/the/folder/ **(eg: cd /home/user/realvnc). then type [B]make
[/B] and after that **make install**

note: if it tells you **permission denied **then type **sudo** in front of the command

---

### Post by UbuntuNerd on 2008-08-02
here is a link to install VNC in ubuntu

[http://www.ubuntu-unleashed.com/2007/10/setup-vnc-server-for-ubuntu-gutsy.html]("http://www.ubuntu-unleashed.com/2007/10/setup-vnc-server-for-ubuntu-gutsy.html")


also you can try OpenSSH provides secure remote access to your computer, allowing you to run command line and graphical programs, transfer files, and use a "port forwarding" capability to securely tunnel other protocols through firewalls and untrusted networks 

I use it in my own home server but im not 100 percent sure of how it works on windows?

---

### Post by UbuntuNerd on 2008-08-02
here is a link 

[https://help.ubuntu.com/community/SSHHowto]("https://help.ubuntu.com/community/SSHHowto")

also if you decide to use it download putty is a GUI to help you configure it

---

### Post by JustGus on 2008-08-02
Thanks,sharks. Yes, I did have a look in synaptic, but it wasn't there.
Just to ensure I've got what you're saying (as I know the terminal allows no room for error), if I've downloaded the file and extracted it to folder "realvncinstall"on my desktop and my user name is "user", i would type...
**cd /home/user/realvncinstall/realvnc make make install**

Not sure about the spaces and/or slashes between the "make" refererences you mentioned.

Thanks,
Gus

---

### Post by sharks on 2008-08-02
No. **cd /home/user/realvncinstall/** and press enter
then **make** press enter and once the process is completed type **make install**

---

### Post by JustGus on 2008-08-02
Thanks Ubuntu Nerd,
Is it right that these offer mainly a command line interface?  What I'm really trying to find is something that will display the Ubunu desktop in such a way that it mirrors what I would see if I had a monitor hooked up, so more graphical.  Does such an app exist?
Cheers,
Gus

---

### Post by JustGus on 2008-08-02
Thanks Sharks.  I get it now. To follow up on the comment I made referring to UbuntuNerd's post, do you know if installing RealVNC offers from another computer monitor, in effect a mirror of what I would see if I'd simply connected a monitor to the Ubuntu machine?  Cheers,
Gus

---

### Post by sharks on 2008-08-02
dont know about it. 

note:if a post has helped u , press the star button to think the person who helped under his post.(not must)

---

### Post by ByteJuggler on 2008-08-02
I would actually suggest you try out NX.  Currently running my server headless and using that for GUI desktop when needed. Download [here]("http://www.nomachine.com/download-package.php?Prod_Id=5").

Note, you have to install the client, then the node, then the server, in that order.

Download the packages then install with e.g.

```
sudo dpkg -i package.deb
```

Then download and install the NX Windows client, and connect to your server.  Sometimes some post install server configuration is neccesary, but I *think* the latest version should pretty much "just work"...  Post back if you have problems and I'll try to help.

---

### Post by ByteJuggler on 2008-08-02
> **JustGus said:**
> Thanks Ubuntu Nerd,
Is it right that these offer mainly a command line interface?  What I'm really trying to find is something that will display the Ubunu desktop in such a way that it mirrors what I would see if I had a monitor hooked up, so more graphical.  Does such an app exist?
Cheers,
Gus

No, VNC does not offer a command line (even if you can start it using the command line), it gives you a remote GUI desktop, whether a mirror of the acutal console, or whether a virtual one.  

For a command line interface you already have ssh, which is what I use in conjunction to NX.  (I *sometimes* use VNC as well but it's a little awkward to use, as you have to first ssh into the box then start an XVNC server, or you have to leave your console logged in first and start desktop sharing first, before you can connect.  With the setup I have, I can boot my box headless, then connect to it either using ssh or NX.  Job done. Aside, a nice ssh tool for Windows is "putty", [here]("http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html").)

---

### Post by JustGus on 2008-08-02
Thanks Sharks and ByteJuggler. You've been very helpful.  Didn't know that you had to click the ribbon buttons to post a "thanks", so thank you also for pointing it out.
Will try installing tomorrow. Fingers crossed!
Gus

---

