---
title: "Wired but no Wireless internet"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by mjmark223 on 2008-10-17
Hi

I'm an absolute beginner and I need help connecting to my wireless home network.

I had no problem connecting to my router with a network cable. That is how I am on the internet right now.

I have tried tutorials and other posts but I can't seem to figure it out.

I tried to do System/Preferences/Hardware Options but I don't have the icon to check my hardware. Also "hardware options" isn't the exact term, but hardware is in the title.

Anyway, I am using Ubuntu 8.04 and I have a Linksys router.

I took 3 screen shots. ifconfig. iwconfig, and route.

I'm not really sure what I'm looking for after I type those in.

Hopefully those will help.

Thanks

Mark

---

### Post by chuckyp on 2008-10-17
You can click on the little network icon by the clock and configure wireless or you can go to System > Preferences > Network Configuration

---

### Post by shabs on 2008-10-17
Do you see a list of wireless networks or do you see you home network listed when you click on the network manager icon on your panel?
First try this command "sudo ifconfig wlan0 up"
If you still have trouble could you please post the output of "lspci".

---

### Post by beno1990 on 2008-10-17
Try typing lspci into the console and see what model wireless adapter you have. You may be able to get native wireless drivers for Linux (many drivers for such things are found in the Hardy backports), but if not, you will probably be able to get it working by installing ndiswrapper.

For each:

Open System -> Administration -> Software Sources -> Updates tab and check the "hardy-backports" box.

Then the following command lines:

```

sudo apt-get update

```

And then:

```

sudo apt-get install linux-backports-modules-hardy-generic

```

Reboot, and see if your wireless works.

If that doesn't work, type lspci into the console and find your wireless adapter in there. Download the Windows driver for it, and then type the following into the console:

```

sudo apt-get install ndisgtk

```

After that, there should be a new application in System -> Administration for Windows drivers. Open it, and point it to the respective file for your Windows wireless driver.

---

### Post by mjmark223 on 2008-10-18
Thanks Beno. I am now currently on my wireless network.

Mark

---

