---
title: "[SOLVED] Flashplayer and security stuff"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by Waqsione on 2008-06-08
Hello, everyone. I'm pretty new to Ubuntu, and is wondering if a few small questions of mine can be answered. For the sake of convenience, I'm asking three of them here (That's okay, right?).

1. I've installed the flashplayer some days ago, and at one point in the installation, it told me to get an administrator to remove a file (I don't remember it's name, but I think it was a dat file- whatever that is). I haven't done so yet (because I'm not sure how), but didn't see any problems that might have arose because of it. Should I do something about it, or am I worrying too much?

2. I read that announcement about the security vulnerability on the top of the forums, and ran that code that's suppose to test if my system's vulnerable or not (on the terminal). It didn't gave a response, and just went to the next line waiting for a new command. Does this mean my computer's okay, or did I do something incorrectly?

3. Can anyone recommend some reliable security softwares for Ubuntu? Or are the security updates that it gets enough for general users?

Thank you for reading through the questions, and I would appreciate it if you can answer any one of them.

---

### Post by ibuclaw on 2008-06-08
Hello Waqsione.

Sure, you can ask all the questions you like. We won't mind :)
We are here to help aid the transition and hassles of learning to administer a completely new Operating System.

To reply to your questions.

1) Did you install flashplayer via the repository/when Firefox asked you to install it?
Or did you download it from Adobe's Site and installed it yourself?

2) If you are referring to the OpenSSL fiasco. Then you should be alright.
If nothing gets outputted, that means that you are not using/haven't yet used ssh to connect to anywhere yet. So you shouldn't worry about that for now.

3) Ubuntu is pretty safe as is out of the box. Although it does help to be cautious.
One great example is to use ufw. (Ubuntu FireWall) :D

To set it up for everyday use. copy and paste this line by line into a terminal.
```

sudo apt-get install ufw
sudo ufw default deny
sudo ufw allow 80
sudo ufw allow 22
sudo ufw enable

```
Basically, you install the app and setup the default settings of it to deny all ports.
Then you tell ufw to allow port 80 (allows internet browsing) and port 22 (allows ssh protocols). And the last command enables the daemon to start for next time your PC boots up.

Regards
Iain

---

### Post by Waqsione on 2008-06-08
...

---

### Post by Waqsione on 2008-06-08
Wow, thank you! Those questions were bugging me for a while.
As for question 1, I downloaded it off Adobe's site and followed the instructions. Flash contents seem to display just fine.

---

### Post by ibuclaw on 2008-06-08
Oh, OK.

Ubuntu has it's own script to install adobe flashplayer itself for you. (It also gets added to the indexed list of installed apps on your PC.)

It's not that much different to how you did it. It's just automated, that's all.

But to get it the proper way. You'd have to make sure the multiverse repository is enabled. And then install it using Ubuntu's built-in package manager.
```

sudo sed -i '/hardy multiverse/s/#//' /etc/apt/sources.list
sudo apt-get update
sudo apt-get install flashplugin-nonfree

```
Although, if it is up and working fine. There may be no need to do this (Unless you'd rather have the option to uninstall it in the future).


Regards
Iain

---

### Post by Waqsione on 2008-06-08
Thanks again, tinivole! Your suggestions are great and easy to follow.
(And yeah, I probably never needed to worry about the Flashplayer)

---

