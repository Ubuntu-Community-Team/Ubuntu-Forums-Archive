---
title: "Update Manager"
date: 2013-04-16
forum: New to Ubuntu
---

### Post by iagowp on 2013-04-16
I was trying to fix my laptop not displaying the  battery status, and at some point i ran this commands:
sudo add-apt-repository ppa:iaz/battery-status && sudo apt-get update
sudo apt-get install battery-status


Now, whenever i try to run the Update Manager i get the following message:
"Failed to download repository information


Check your Internet connection.
W:Failed to fetch [http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead."

And commands like:
sudo apt-get remove battery-status

will return me this :
"E: Unable to locate package battery-status"

I'm not even sure battery-status is currently installed, as it doesnt work for my case (its a toshiba satellite l645, i found out i have to do some changes on the kernel, so i decided not to mess with that and keep without a battery indicator) so what i want is to either uninstall it, or make the UM stop asking for it

---

### Post by schragge on 2013-04-16
The PPA has no packages for releases newer than *natty* (Ubuntu 11.04), try to uncheck the PPA in your software sources. See [uhelp]community/Repositories/Ubuntu[/uhelp]

---

### Post by iagowp on 2013-04-16
Thanks for the help. but by software sources, you mean the software center? I tried typing software sources on the dash home, and its the only thing to come up

---

### Post by Cheesehead on 2013-04-16
Software Sources is accessible under "settings" in Software Center.
And several other ways.

---

### Post by ibjsb4 on 2013-04-16
If you cannot find it, [open a termina]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal")l and enter:

```
gksudo software-properties-gtk
```

And go here to either remove it or just uncheck it.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

---

### Post by iagowp on 2013-04-16
Thank you very much, i wasnt able to find it without the terminal.

Well, i cant see the option to show this thread as solved, but it is, thank you guys.

---

### Post by raja.genupula on 2013-04-16
you can do it from thread tools , thats in the menu of your 1st our thread.

---

### Post by iagowp on 2013-04-16
Yeah, but i get the exact same options as you, there should be a 'Mark this thread as closed' option, i suppose its because im a new user to the forums, and dont have yet all options.

---

### Post by ibjsb4 on 2013-04-16
Glad its fixed :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Iowan on 2013-04-16
> **iagowp said:**
> Well, i cant see the option to show this thread as solved, but it is, thank you guys.

I changed it for you but here's how:
[http://ubuntuforums.org/showthread.php?t=2121377](http://ubuntuforums.org/showthread.php?t=2121377)

---

### Post by iagowp on 2013-04-19
Ty, at first i tried to put solved using the link i received when i registered here

---

