---
title: "Having issues downloading ANYTHING. Issues with connection although i'm def connected"
date: 2019-10-01
forum: New to Ubuntu
---

### Post by verdae-geissler on 2019-10-01
I caanot download from ubuntu store, nor can I type it in a terminal.
I am not exactly new to ubuntu, as I used ubuntu several years ago, and I loved it, so I had a PC repair shop download it for me on my new PC.
Today is my first time attempting to use the PC.
I have connected to the wireless network at my house, but I continue to recieve error message stating that I am not connected.
Any thoughts?

---

### Post by guiverc on 2019-10-01
> **verdae-geissler said:**
> I caanot download from ubuntu store, nor can I type it in a terminal.

Downloading from Ubuntu store sounds like a networking issue, not being able to type in a terminal would imply a keyboard issue? which is something completely different.

Assuming it's not keyboard, I'd open a terminal and explore.
Is your network devices detected and look okay, ie. ```
ip link
```

Do your network devices get an IP address, ie. ```
ip addr
```

Assuming you have a network device recognize & a valid IP address, can you ping your router (I assume you know it's address, otherwise `ip route` may help if you're using DHCP. 

Next I'd try and ping an external address, ie. `ping -c 2 8.8.8.8`  (google's DNS)

If you can ping external, then I'd finally try pinging with a human addreess, ie. `ping -c 2google.com` , if this step fails it's a DNS issue; but you may have had failures earlier.

If I didn't see what looks like valid info to me with `ip link` or earlier commands, I'd go to other steps, eg. `sudo lshw -C network` to list-hardware of class=network, ie. is anything 'unclaimed'....

These are just random thoughts/steps - even if somewhat vague  (*hopefully few errors*)

---

### Post by Impavidus on 2019-10-01
If you cannot download from the ubuntu store, you may have a networking problem, a bad server or an old release. Can you access the internet in other programs? Can you, for example, get to this site using a web browser? What release was installed?

Normally I suggest a few terminal commands to investigate, but if you can't type in a terminal, that may be a bit hard. Can you open the file /etc/apt/sources.list in a text editor and show it to us?

If you try to use a terminal, what do you see? Can you open the terminal window, do you see a prompt? Does it not respond at all when you hit a key, or can you type, but the command isn't processed when you hit enter? Can you type in other applications? Can you switch to the console (ctrl+alt+F2), log in and use that command line? Use ctrl+alt+F7 to get back to the GUI.

Sorry for the many questions, but this may give us some leads.

---

