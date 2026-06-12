---
title: "I need step by step instructions to install scilab-6.0.0.bin.linux-x86_64.tar.gz"
date: 2017-02-25
forum: New to Ubuntu
---

### Post by afz12 on 2017-02-25
Hi

I've been using SciLab5.5.2 for modeling various physical systems and would like to try the latest version from [http://www.scilab.org/](http://www.scilab.org/). I have the file

scilab-6.0.0.bin.linux-x86_64.tar.gz

downloaded but have had very little past success installing tar files. First, where should this file be copied? Many directories have permission issues but I assume there must be a preferred directory to start the procedure from. Also I've read various posts on installing tar files before but they either assume prior knowledge that I do not possess and are therefore unhelpful, or I find that the commands presented fail half way through (e.g. needing some prerequisite files or other), or don't end up with a proper launch icon that can go in a panel like other installed software. Therefore I would appreciate if someone can list simple step by step instructions that I can copy into a terminal and see if it works OK.

At first I'd like to test SciLab's latest recommended version 6.0.0 on this notebook using Ubuntu 17.04 alpha 2. If this works I'd like to repeat the procedure for Ubuntu 16.10 and Mint 18.1 (this is not an OS related issue of course). This notebook is an hp Envy 4-core with 8 GB RAM and has no difficulty running SciLab5.2.2. However I now would like to upgrade to the recommended SciLab6.0.0 version but don't know how to install the file without unexpected hiccups along the way. Any suggestions for this task are appreciated in advance:D

---

### Post by cariboo on 2017-02-26
Assuming the downloaded file is in your Downloads directory in a terminal:

```
cd Downloads
sudo cp scilab-6.0.0.bin.linux-x86_64.tar.gz /opt
cd /opt
sudo tar zxvf scilab-6.0.0.bin.linux-x86_64.tar.gz
```

press enter after each command. 

to run scilab:

```
cd scilab-6.0.0/bin
./scilab
```

---

### Post by afz12 on 2017-02-26
Hi caraboo

Thanks for the code - this was exactly what I wanted. SciLab installed, starts and runs well - opens quite fast. However I would like to make an icon to start SciLab as so with other s/w. It doesn't show up in the dash panel - only SciLab5.2.2 is there. How do I accomplish this? 

Also is it possible to convert the tar file to a deb file or is this complex?

---

### Post by RobGoss on 2017-02-26
This might be of use for what you want to accomplish there might be someone else that has better understanding on how this method is used

Checkinstall

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by HermanAB on 2017-02-26
Well, you could have installed it from the repos with apt.

---

### Post by afz12 on 2017-02-26
Thank you RobGoss and HermanAB for your replies. I would like to mark this thread as "solved" but if you re-read my first post, I thought I had been clear to have wanted a launch icon for SciLab6.0.0. This version is only available as a tar file and I specifically did not want any older version. Launch icons are an expected standard by most people that use computers and these forums use them - I doubt that many people would participate in these forums if everything had to be accomplished through a terminal. Anyway, there must be a simple way to install SciLab6.0.0 (not any previous version) and have it launched by clicking an icon just as is done with proper software installations. Again, step by step instructions would be appreciated, higher level concepts such as "could have installed ... with apt" are not all that helpful, or if I guess the meaning, would not have installed the tar file - properly at version 6.0.0 with a standard launch icon as requested.

---

### Post by oldos2er on 2017-02-26
You would need to [create a *.desktop file]("https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles") as a GUI launcher.

---

### Post by afz12 on 2017-02-26
Thank you Oldos2er

I tried your link and both methods drew blanks. I prefer clear and simple instructions to make a proper launch icon - the examples are far too esoteric and assume knowledge I don't have on the subject matter. I had hoped for a complete solution for installing SciLab with a proper launch icon with clear step by step instructions on how to accomplish this, without assuming prior knowledge - just like programming a robot if you like. So far I have a partial solution, if anyone can provide terminal commands to complete the task entirely then I would appreciate this. I am sure I am not alone in this - tar files are always problematic and no-one ever provides _**complete**_ solutions it seems.

---

### Post by cariboo on 2017-02-26
the *.desktop files are located in /opt/scilab-6.0.0/share/applications, just copy them using sudo to /usr/share/applications.

You may have to change the Exec= line to:

```
Exec=/opt/scilab-6.0.0/bin/scilab -f
```

---

