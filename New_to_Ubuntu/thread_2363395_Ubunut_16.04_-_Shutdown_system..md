---
title: "Ubunut 16.04 - Shutdown system."
date: 2017-06-09
forum: New to Ubuntu
---

### Post by antero00 on 2017-06-09
Hi everyone, 

I'm new user Ubuntu, and I've a problem. When I click shutdown my laptop reboots instead of shutdown.

I'm tried edit /etc/default/grub 

with: 
GRUB_CMDLINE_LINUX_DEFAULT = "quiet splash" 

to: 
GRUB_CMDLINE_LINUX_DEFAULT = "quiet splash acpi = force"  but nothing.  

Please help me. 

I know that my English isn't perfect but I still learn.

---

### Post by mr.v. on 2017-06-10
What is the brand and model of your laptop?

Also see if you directly issue a system shutdown command from the terminal and see if it shuts down the system correctly. You can do that by going into the terminal (press the "Super" button or Windows key and type "Terminal" in the search box and run  it)
Next in the terminal issue the following command:
> sudo shutdown -h now
and enter your sudo password
(note you can actually also use > sudo poweroff or > sudo systemctl poweroff
This command will shutdown the system. Let's see if that has the proper behavior.

---

### Post by antero00 on 2017-06-10
I checked these 3 commands, but they don't work.
My laptop is HP Probook 450 G0 

When I click the wi-fi button and I shutdown the system, it's all ok. 

There is another way to get it work correct ?

---

