---
title: "difficulty in tunneling VNC through SSH"
date: 2016-06-24
forum: New to Ubuntu
---

### Post by devlin3 on 2016-06-24
Hello,

I'm attempting to set up a VNC tunnel through VNC so i can access my lubuntu desktop remotely. I'm following the directions found here:

[https://wiki.ubuntu.com/Lubuntu/RemoteDesktop](https://wiki.ubuntu.com/Lubuntu/RemoteDesktop)

deviating only from the instructions by tunneling the VNC through my local network, as it would currently be inconvenient to go to a remote location.

Everything goes fine until I run the ```
vncviewer localhost:12345
``` from my local pc under the command prompt of the Lubuntu pc. This gives me the output ```
Error: Can't open display:
```

Can anyone help? thank you in advance for taking he time.

---

### Post by HermanAB on 2016-06-24
Tunneling VNC through SSH is a form of recursion and is bound to be awfully slow. 

Assuming that you have ssh working already, try this:
$ ssh -C -c blowfish -X user@serveraddress "gedit filename"

---

### Post by steeldriver on 2016-06-24
What do you mean by
> 
from my local pc **under the command prompt of the Lubuntu pc**


? The **viewer** needs to be run on the **local** system

---

### Post by devlin3 on 2016-06-24
> **HermanAB said:**
> Tunneling VNC through SSH is a form of recursion and is bound to be awfully slow. 

Assuming that you have ssh working already, try this:
$ ssh -C -c blowfish -X user@serveraddress "gedit filename"

I was hoping that Lubuntu would be light enough that I could tunnel VNC through SSH without too much slowdown. would the slowness cause the "could not display" error I mentioned in my first post? Would having faster internet help?

Also, I tried typing ```
ssh -C -c blowfish
``` (exactly as you typed it only substituting my Lubuntu's name@serveraddress) and it gave me this output ```
Unknown cipher type 'blowfish'
```

> **steeldriver said:**
> What do you mean by


? The **viewer** needs to be run on the **local** system

I ran the command from my ubuntu laptop, after I connected to the lubuntuserver via SSH, so instead of the command prompt being ```
user@ubuntulaptop
``` it was ```
user@lubuntuserver
```

---

### Post by steeldriver on 2016-06-24
No... don't do that

The whole point of a tunnel (think about a real tunnel) is that the traffic goes in one end and comes out the other - so you connect your vncviewer to the local end of the tunnel (in your case, port 12345 on your laptop)

---

### Post by devlin3 on 2016-06-24
I see. Could you show me what the terminal commands should look like? I'm pretty new to this.

I went to the physical lubuntu server laptop and ran the command ```
vncviewer localhost:12345 &
``` and got ```
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server
``` as an output. Was this the action you meant for me to take in your post? Thanks again for taking the time.

---

### Post by steeldriver on 2016-06-24
The commands are not wrong - you just need to execute the last one on the **local** machine

```

vncviewer localhost:12345

```

(You will also need to have **installed** the vncviewer on the local machine, not the remote one)

---

### Post by devlin3 on 2016-06-24
ok I have tried executing the "vncviewer localhost:12345" command on both computers, and on my ubuntu laptop I get ```
connected to RFB server, using protocol version 3.7
Server did not offer supported security type
``` on my lubuntu laptop I get ```
ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server
``` and when I execute the command on my ubuntu laptop using my lubuntu command prompt via SSH I get ```
error: Can't open display
```

I installed the vncviewer on both machines just to be sure...

---

### Post by steeldriver on 2016-06-24
If you're using vino-server, you *may* need to mess with the encryption settings - see [http://ubuntuforums.org/showthread.php?t=2291106&p=13340526#post13340526](http://ubuntuforums.org/showthread.php?t=2291106&p=13340526#post13340526)

---

### Post by devlin3 on 2016-06-24
I performed the terminal prompt to change the encryption setting in vino, rebooted both laptops, ran the ssh vnc tunnel command on the remote, then ran the vncviewer localhost:12345 & prompt and  was able to remote into the lubuntu server. Thank you very much for your help. In the future, would you recommend that I search the ubuntu forums in a particular way? Despite all my googling, I never came across the page that you linked to in your previous post.

And just out of curiosity, do you think the method of VNC tunneling in the article I initially posted is safe? I have read before that there are things one can do to increase the security of an SSH. Are they necessary?

---

### Post by HermanAB on 2016-06-24
If you would type 'man ssh' in your browser search box, then you would find a list of supported ciphers which nowadays includes blowfish-cbc.  Long ago, just typing blowfish was enough.  Things changed a little though.

$ ssh -C -c blowfish-cbc -X user@server "gedit filename"

You can also try arcfour.  It is a little faster than blowfish, but its security is now in doubt due to a bad implementation on Windows.

Tunneling VNC over SSH is secure, but sending the whole flippen desktop graphic over the wire, when your local machine already has a perfectly working desktop is redundant.  Using only SSH, without VNC, you only tunnel the application itself, which is much more efficient.

---

