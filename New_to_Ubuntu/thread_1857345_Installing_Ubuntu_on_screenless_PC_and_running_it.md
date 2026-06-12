---
title: "Installing Ubuntu on screenless PC and running it"
date: 2011-10-10
forum: New to Ubuntu
---

### Post by vmsda on 2011-10-10
I have an Ubuntu laptop (L) from which I run everything. But would like to install a screenless music box (M), connected via USB to my home hi-fi setup and via Ethernet cable to L.

On M I need:
1. To install Ubuntu without a display
2. Run Music Player Deamon (MPD, a music server)
3. The music file used by MPD
4. M communicates with L and L only, for security and performance reasons.
5. On power-on, MPD starts automatically.

On L:
1. A way of installing Ubuntu on M
2. Run an MPD client (in my case, Sonata)
3. Run normal Ubuntu maintenance for L (including backup of the all important MPD music file).

Is this too much of a mouthful for a largely non-tech user? What is the minimum set of software and procedures to achieve those objectives?

Thank you for your ideas.

---

### Post by ezramorris on 2011-10-10
Hi,
The complicated part of this is actually installing Ubuntu. I've set up a few headless machines running Debian (another Linux distribution), but have always plugged a keyboard and monitor in to install it.

> **vmsda said:**
> On M I need:
1. To install Ubuntu without a display
There are ways and means but it's probably easiest to take the hard disk out of M and connect it to L (via a USB adaptor or something). Then remove L's hard disk to make sure you don't overwrite anything on that, and boot an Ubuntu Server CD and install as usual.


> **vmsda said:**
> 
On L:
...snip...
3. Run normal Ubuntu maintenance for L (including backup of the all important MPD music file).

This can be done easily enough with SSH (Secure SHell). When you install Ubuntu Server, you may get an option to install the SSH server, if not, you can do:
```
apt-get install openssh-server
```

Then you can get in to M from L with something like:
```
ssh server-username@server-ip-or-hostname
```

Copying files can be done with SCP (Secure CoPy), which works very similarly to the cp command:
```
scp server-username@server-ip-or-hostname:/path/to/remote/file destination
```

> **vmsda said:**
> 4. M communicates with L and L only, for security and performance reasons.

If a crossover cable is used between M and L, and M is connected to nothing else, then the only thing that should be able to access M is L. Obviously, anyone else connecting via the crossover to M would be able to access it, if, say, they knew your login password. There are various ways to prevent this, although perhaps a little OTT.

As for installing MPD, the server package, as well as a number of clients are available in the ubuntu repositories, so that should be easy enough.

Hope this helps. If I've been unclear about anything, let me know.

---

### Post by vmsda on 2011-10-10
> **ezramorris said:**
> Hi,
... Hope this helps. If I've been unclear about anything, let me know.

Thank you, ezramorris, for your prompt and comprehensive reply, which has been of great help, naturally.

In order not to overcomplicate matters, I am going to borrow a screen and a keyboard and do a normal Ubuntu installation on M. Since I have already had my classical music collection running for some time on L, all that remains is for me to concentrate on getting SSH to do the rest; from your description, it does not look like an insurmountable job.

Thank you once again.

---

