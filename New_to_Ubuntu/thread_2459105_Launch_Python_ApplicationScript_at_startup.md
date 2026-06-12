---
title: "Launch Python Application/Script at startup"
date: 2021-03-10
forum: New to Ubuntu
---

### Post by dbs179 on 2021-03-10
Hi all,

I'm very new to Linux, Ubuntu and Python, and have a question I can't sort out.  I have an Ubuntu VM spun up to connect with and automate my home alarm system.  I have everything working like it should, except when I need to reboot the VM or the host it is on goes down.  When either of those happen, I have to manually launch the python application/script that connects to my alarm system for my automations.  I'm using the Concord232 application from here [https://github.com/JasonCarter80/concord232](https://github.com/JasonCarter80/concord232)  

At the bottom of the page, it talks about and links to a different URL to start the project on boot, that article is here:  [https://www.raspberrypi-spy.co.uk/2015/10/how-to-autorun-a-python-script-on-boot-using-systemd/](https://www.raspberrypi-spy.co.uk/2015/10/how-to-autorun-a-python-script-on-boot-using-systemd/)

That link talks about using systemd and configuring the script to run as a service, but I haven't been able to get it to work and to make things less clear for me, it is also for Raspbian.

To launch the Concord232 application, I run this command from terminal:  sudo concord232_server --serial /dev/ttyUSB0  

After entering the command, I get a prompt for my sudo password and then everything runs as it should.

The concord232_server.py script the command above refers to is located at /usr/local/bin and is a pretty short script.

```

#!/usr/bin/python3
from concord232 import main
main.main()

```

The rest of the concord232 package is located at /usr/local/lib/python3.8/dist-packages/concord232 including the main.py script the the concord232_server.py script references.

I've beaten my head against the wall all day on this and am not any closer than when I started.  I'm sure it is a simple solution if you know what you are doing, but I don't, so any help would be greatly, greatly appreciated.

Thanks!!!

---

