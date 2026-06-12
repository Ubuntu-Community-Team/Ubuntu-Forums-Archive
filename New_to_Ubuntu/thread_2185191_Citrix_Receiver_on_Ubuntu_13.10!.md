---
title: "Citrix Receiver on Ubuntu 13.10!"
date: 2013-11-01
forum: New to Ubuntu
---

### Post by pbandjam on 2013-11-01
Hi,

I am relatively new to linux and am loving it so far! Everything works super smooth and fast. I've had issues with getting flash to work and detecting my sound driver but found work arounds to them.
A class I'm in requires me to use Citrix Receiver to access their network programs but whatever I do I can't seem to open the program. I am dual booting currently to both win8 and ubuntu at the moment and this is the only reason I am keeping Win8. Any help is appreciated!

---

### Post by Toz on 2013-11-01
There are a few other threads on this forum regarding Citrix and 13.10. See [here]("http://ubuntuforums.org/showthread.php?t=2181903&highlight=13.10+citrix") and [here]("http://ubuntuforums.org/showthread.php?t=2166020&highlight=13.10+citrix").

---

### Post by pbandjam on 2013-11-01
Ok, so I've already tried looking up this issue but keep running into errors. I used the first link you provided and when it asks for:
> dpkg-deb -x icaclient_12.1.0_amd64.deb foo

I get this in return:
> dpkg-deb: error: failed to read archive `icaclient_12.1.0_amd64.deb': No such file or directory

---

### Post by Toz on 2013-11-01
Did you download the file from the citrix website ([http://www.citrix.com/downloads/citrix-receiver/linux/receiver-for-linux-121.html]("http://www.citrix.com/downloads/citrix-receiver/linux/receiver-for-linux-121.html"))?

---

### Post by pbandjam on 2013-11-01
Yes, I downloaded it but when I try to install it I get:
"Dependency is not satisfiable: ia-32labs"

---

### Post by pbandjam on 2013-11-01
I tried this instead:
> dpkg-deb -x icaclient_12.1.0_amd64.deb

And got:
> dpkg-deb: error: --extract needs a target directory.
Perhaps you should be using dpkg --install ?

---

### Post by LkpPo on 2013-11-01
Try :  dpkg --install icaclient_12.1.0_amd64.deb

---

### Post by pbandjam on 2013-11-01
> **LkpPo said:**
> Try :  dpkg --install icaclient_12.1.0_amd64.deb

Now I'm getting:
> dpkg: error: requested operation requires superuser privilege


This isn't even making any sense. I'm the only person who uses this computer :(

---

### Post by pbandjam on 2013-11-01
Again tried installed with root 

> dpkg --install icaclient_12.1.0_amd64.deb
dpkg: error processing icaclient_12.1.0_amd64.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
icaclient_12.1.0_amd64.deb





---

### Post by Toz on 2013-11-02
Please follow the posted instructions carefully, you are missing some parameters to those commands. And run those commands from the same directory to which you downloaded the citrix deb file.

Instruction:
> dpkg-deb -x icaclient_12.1.0_amd64.deb foo

Your command:
>  dpkg-deb -x icaclient_12.1.0_amd64.deb 

---

### Post by Toz on 2013-11-02
> Again tried installed with root

[quote]dpkg --install icaclient_12.1.0_amd64.deb
dpkg: error processing icaclient_12.1.0_amd64.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
icaclient_12.1.0_amd64.deb
[/quote]
And now you've got a failed install. You'll need to run that first command to remedy this problem:
```
sudo dpkg -P icaclient
```

---

### Post by pbandjam on 2013-11-02
I already tried that command above thats when I got:

> dpkg-deb -x icaclient_12.1.0_amd64.deb foo 
dpkg-deb: error: failed to read archive `icaclient_12.1.0_amd64.deb': No such file or directory


---

### Post by pbandjam on 2013-11-02
> **Toz said:**
> And now you've got a failed install. You'll need to run that first command to remedy this problem:
```
sudo dpkg -P icaclient
```

Okay so now I'm getting:

> dpkg: warning: ignoring request to remove icaclient which isn't installed


---

### Post by Toz on 2013-11-02
> **pbandjam said:**
> Okay so now I'm getting:> dpkg-deb -x icaclient_12.1.0_amd64.deb foo
dpkg-deb: error: failed to read archive `icaclient_12.1.0_amd64.deb': No such file or directory 
The command is unable to find the file. In what directory is icaclient_12.1.0_amd64.deb? Where did you download it to? 

> **pbandjam said:**
> I already tried that command above thats when I got:> dpkg: warning: ignoring request to remove icaclient which isn't installed 
Okay, then you don't have to worry about it.

---

### Post by pbandjam on 2013-11-02
> **Toz said:**
> The command is unable to find the file. In what directory is icaclient_12.1.0_amd64.deb? Where did you download it to? 



I downloaded it to 'Downloads'  :(

---

### Post by Toz on 2013-11-02
Open a terminal window and go to the Downloads directory:
```
cd Downloads
```
...then start going through those instructions.

---

### Post by pbandjam on 2013-11-02
> ~/Downloads$ missing=$(cat ica_missing_packages | awk '{print $1}'); sudo apt-get -y install $missing
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 liboss4-salsa-asound2:i386 : Conflicts: libasound2
                              Conflicts: libasound2:i386


What does this mean?

---

### Post by Toz on 2013-11-02
The instructions worked for me. However, if you look at post #3 from that thread ([http://ubuntuforums.org/showthread.php?t=2181903&p=12821080&viewfull=1#post12821080]("http://ubuntuforums.org/showthread.php?t=2181903&p=12821080&viewfull=1#post12821080")), you'll see that their issue was similar to the one that you are having. They ended up solving the issue installing the beta version - instructions are included in that post.

---

### Post by pbandjam on 2013-11-02
I'm sorry but I really seem to be reading gibberish here. I don't understand a single word of these shell commands and even when I try to go through with them I have no idea what's going on. If their instructions were systematic to my issue I would have been able to solve it. But thanks for the help :)

I think I'll just stick to windows for now.

---

