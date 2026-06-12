---
title: "Prey installed but not working"
date: 2016-02-06
forum: New to Ubuntu
---

### Post by brian106 on 2016-02-06
I downloaded and installed the Prey Ubuntu client software today as an addition to my existing account. The first three attempts at installation failed but the 4th one seems to have installed correctly. According to Synaptics it looks OK. However, it has not registered on the Prey Panel. I have already written to Prey Project about this but I wondered if any other Ubuntu users have had a similar experience.

---

### Post by Vladlenin5000 on 2016-02-06
How exactly have you "downloaded and installed" it? And why?
It's available in the official repositories therefore it can be installed like any other software with Ubuntu Software Center, any other fronted, or simply
```
sudo apt-get install **prey**
```

Source: [https://preyproject.com/blog/2011/04/its-official-prey-is-now-on-ubuntu](https://preyproject.com/blog/2011/04/its-official-prey-is-now-on-ubuntu)

---

### Post by brian106 on 2016-02-06
> **Vladlenin5000 said:**
> How exactly have you "downloaded and installed" it? And why?
It's available in the official repositories therefore it can be installed like any other software with Ubuntu Software Center, any other fronted, or simply
```
sudo apt-get install **prey**
```

Source: [https://preyproject.com/blog/2011/04/its-official-prey-is-now-on-ubuntu](https://preyproject.com/blog/2011/04/its-official-prey-is-now-on-ubuntu)

Precisely. It is a laptop.

---

### Post by monkeybrain20122 on 2016-02-06
Prey has a .deb for [download]("https://preyproject.com/blog/page/4?lang=es%2Fdownload") and the version is 1.5.0, the version in Ubuntu's repository is 0.6.2??!! Not sure how it is versioned in the repo but if the version reported is as is then the repo's version is very outdated.

---

### Post by brian106 on 2016-02-06
The version installed is 1.5.0. It just doesn't seem to be logging in with Prey.

---

### Post by howefield on 2016-02-06
Anything look interesting in these threads ?

[http://ubuntuforums.org/showthread.php?t=2285276](http://ubuntuforums.org/showthread.php?t=2285276)
[http://ubuntuforums.org/showthread.php?t=2276081](http://ubuntuforums.org/showthread.php?t=2276081)

---

### Post by brian106 on 2016-02-06
> **howefield said:**
> Anything look interesting in these threads ?

[http://ubuntuforums.org/showthread.php?t=2285276](http://ubuntuforums.org/showthread.php?t=2285276)
[http://ubuntuforums.org/showthread.php?t=2276081](http://ubuntuforums.org/showthread.php?t=2276081)

I just entered the prey account config intruction in the second link (ignoring all the preceding items) and it worked. Thank you so much!

---

### Post by howefield on 2016-02-06
Cool, glad you sussed it :)

---

### Post by brian106 on 2016-02-06
Silly me to think it would set itself up as happens in Windows.

---

### Post by howefield on 2016-02-06
The silly bit was not searching the forums 4 hours ago ;)

---

### Post by brian106 on 2016-02-06
> **howefield said:**
> The silly bit was not searching the forums 4 hours ago :wink:

Cute  observation but there was no discernable error, just a package that was  installed but not working. I did search the forum but nothing relevant  resulted so that's why I raised the question.
I had done the same thing with my PC after installing Win 10 and then Prey without any problem. 
I am new to Ubuntu so I'm still in the learning phase.

---

### Post by brian106 on 2016-02-07
Well, it appeared to be solved but today, Prey cannot contact the device (Ubuntu laptop). I have tried re-entering the config command but I get the response 'already configured'.

Now I've damaged (emptied) the prey.postinst file due to my unfamiliarity with nano.
 
cd /var/lib/dpkg/info
sudo nano prey.postinst

Somehow, I got confused with the exit command and I seem to have wiped the file and saved it.

I tried the command 'sudo apt-get install prey' again and this appears to work but does not repair the damaged file. Is this a major problem or is there a way to fix it?

I reinstalled the Prey client and that seems to have resolved the situation, even after a reboot. Even so, the installer said it had failed.

---

### Post by brian106 on 2016-02-08
It presumably doesn't matter that the prey.postinst file is now empty (location: /var/lib/dpkg/info) but I would have liked to return the system to its original state. Is there a way to do this without re-installing 15.10? Alternatively, is it likely to be repaired (overwritten) in a subsequent upgrade?

---

### Post by brian106 on 2016-03-14
This is driving me crazy. It has worked but it keeps reverting to the 'Unable to reach device.' condition despite the fact that all the usual searches show that Prey 1.5.0 is installed and configured. I have been through the previous routines that restored functionality but they don't work any more.
Does anyone have any ideas on how to resolve this. I guess maybe cleaning all traces of Prey and starting again would be the most likely course to follow.

If I type 'whereis prey' I get 'prey: /usr/lib/prey /etc/prey'. Is this correct?

---

### Post by brian106 on 2016-03-16
It would be appreciated if a moderator could please remove the [Solved] statement as there is as yet no lasting solution.

---

### Post by brian106 on 2016-03-17
I don't understand why I am getting no responses to my calls for help.  There is evidently something wrong but the package seems to be installed  and configured correctly. However, Prey responds 'Unable to reach  device'. I suspect no-one is looking at this thread because it is marked  as solved. I am therefore appealing for an administrator to please  remove that statement.

Thank you.

---

### Post by oldos2er on 2016-03-17
I've removed the 'Solved' tag; were you not able to do so yourself?

In the future please use the 'Report Post' icon to message staff if you need help with your thread. I only happened to stumble on it randomly.

---

### Post by brian106 on 2016-03-18
> **oldos2er said:**
> I've removed the 'Solved' tag; were you not able to do so yourself?

In the future please use the 'Report Post' icon to message staff if you need help with your thread. I only happened to stumble on it randomly.

Thanks for your help and for drawing my attention to the fact that I could have done it myself. Put it down to the novice user (me) making the assumption that, as it was marked 'Solved' by an admin, that action could only be reversed by an admin. I have now seen that 'Thread tools' is the place to go.

---

### Post by oldos2er on 2016-03-18
You're welcome. Feel free to "bump" your thread once a day or so if you still need help.

---

### Post by brian106 on 2016-03-20
Well, at last I found the time to pursue my own idea of a complete uninstall (using Synaptics Package Manager), re-downloading the Prey 1.5.0 package from the Prey website and re-installing (using the dpkg -i command) and configuring the package via my Prey account. Voila! It works.

What a load of hassle! It seems indeed that the original installation of Prey 1.5.0, although appearing to be correctly installed and configured, was, in some inexplicable way, broken and unable to communicate with the Prey server. It functioned initially so I can only hope that this new installation will be more reliable than the first.

The main obstacle that I found with the new installation was finding a way to access the downloaded file with any of the installation facilities. For instance, Synaptics denied all existence of the downloaded file, using any of the search methods available. It is very frustrating to repeatedly receive the 'No such file' message when you know that it is there in the Downloads folder. Accessing the Downloads folder through Terminal was also difficult. No doubt the Ubuntu afficionados will scoff at this but I found it very difficult to obtain instructions that worked. Just for the record, one command that did work was:

[COLOR=#ff0000]cd /home/(user name)/Downloads[/COLOR]  Note that Downloads has a capital D, in this case.

So, I am provisionally marking this thread as 'Solved' and hope that it will stay that way.

---

