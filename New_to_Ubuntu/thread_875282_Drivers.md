---
title: "Drivers"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by djzalzer on 2008-07-30
When I downloaded my nVidia driver from nvidia's website, and ran their little program thing, it tells me that I am running an X server.  What is an X server, and why on earth is this thing telling me it can't install graphics drivers because I have one?

I tried to go into system> administration > hardware drivers and install from there, but it gets me a 404.

What to do, what to do?!

---

### Post by tuxxy on 2008-07-30
You should of jsut enabled the driver from the system> administration > hardware drivers

Maybe you need to uninstall the first driver you installed then try and enable the supported one again.

---

### Post by djzalzer on 2008-07-30
okay, thanks; but I haven't installed anything, everything i've tried to install has failed. :[

---

### Post by Unanimated on 2008-07-30
Get EnvyNG. It's way easier.

[http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

---

### Post by a0u on 2008-07-30
> **Unanimated said:**
> Get EnvyNG. It's way easier.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

EnvyNG is available in the Ubuntu repositories for Hardy (8.04).
```
sudo apt-get install [envyng-gtk](http://packages.ubuntu.com/hardy/envyng-gtk)
```
which installs both the GUI frontend and the core program.

> **djzalzer said:**
> What is an X server

Ubuntu (and GNU/Linux in general) uses the X Window System to support the implementation of window managers and provide basic support for graphics hardware, pointing devices such as mice, and keyboards (see [Wikipedia]("http://en.wikipedia.org/wiki/X_Window_System")).  The X Window System uses a client-server model; "the server accepts requests for graphical output (windows) and sends back user input (from keyboard, mouse, or touchscreen)."

Just so you know.

---

### Post by djzalzer on 2008-07-30
Thanks, It'll work once I plug my cd drive back in. >.> If not I can always mae a new thread, eh?

---

### Post by steveneddy on 2008-07-30
If you are running Hardy, then the OS will detect the hardware for you.

Go to

System --> Administration --> Hardware Drivers

put in your password

and click the Nvidia driver install - yes - let it install - restart

---

### Post by CatKiller on 2008-07-30
> **djzalzer said:**
> I tried to go into system> administration > hardware drivers and install from there, but it gets me a 404.

This tool will download and install the restricted nvidia driver for you. I've not seen the repositories down except when they are being hammered by people after a new release, but I'd imagine that it's only temporary. My advice would be to just try again later.

---

