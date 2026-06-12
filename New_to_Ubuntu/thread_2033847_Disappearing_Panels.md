---
title: "Disappearing Panels"
date: 2012-07-27
forum: New to Ubuntu
---

### Post by SEECo on 2012-07-27
I have Ubuntu Netbook Remix 10.04 on y Dell Laptop and it's been months I have it installed on it. But for the couple of days there's been a problem that my panel keeps disappearing just like in the photo in the attachments and then I run the command "metacity --replace" but after sometime it disappears again. How can I solve this? Any would be appreciated.

---

### Post by Bufeu on 2012-07-27
Try to re-install Gnome Shell (I suppose that's what you are using).```
sudo apt-get purge gnome-shell
sudo apt-get install gnome-shell
```

---

### Post by SEECo on 2012-07-28
> **Bufeu said:**
> Try to re-install Gnome Shell (I suppose that's what you are using).```
sudo apt-get purge gnome-shell
sudo apt-get install gnome-shell
```

Thanks for your early reply I really appreciate it. but the commands you gave me I ran them in terminal. When I ran the first command it said that "Not installed so not removed" And when I installed the other command it installed successfully but things gone way worse now the delay is even more shorter now i have to run the command every 5 - 10 minutes.

---

### Post by kabukiM0n0 on 2012-07-28
Even though I don't know the answer. The same thing happens to me on 12.04 with Gnome fallback. I notice it starts playing up after the system has been on for some time. Restarting from terminal at least for my system seems to sort it out - until the next time of course.

---

### Post by NikTh on 2012-07-28
Hi , 

different things , different Desktop Environments. 
There is nothing to do gnome-shell with ubuntu-netbook-remix. 

Ubuntu-netbook-remix and ubuntu-netbook are both optional meta-packages and not installed by default on Ubuntu 10.04 . 

OP , when the first command you ran returns "Not installed so not removed" should not run the next command. 
Now you have installed a new desktop environment Gnome-shell. Beautiful environment (IMO) but heavy for netbooks.

Try to purge this environment and reistall your ubuntu-netbook-remix with below commands
```
sudo apt-get purge gnome-shell
sudo apt-get install --reinstall ubuntu-netbook-remix
```I never used this environment , so i cannot help you with settings (maybe launcher settings are responsible for your problem).
Thanks

---

