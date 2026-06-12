---
title: "Installing Netbeans on Ubuntu 11.10"
date: 2011-11-01
forum: Programming Talk
---

### Post by NattyLight on 2011-11-01
How do you do this? On 8.04 you were able to install Netbeans on the Ubuntu Software center, but disappointed to see that its not in 11.10, does anyone know if they may add in to the software center in the future? I prefer DLing things from there cause it just seems safer to me, plus I don't really know how to install things on the Linux side.

---

### Post by Liiiim on 2011-11-01
It looks like it was removed because the version in the repos was out of date and there wasn't enough resources to update it.  However, NetBeans seems to have an install script which should make it relatively painless to install.  You can download it here - [http://netbeans.org/downloads/index.html](http://netbeans.org/downloads/index.html)

---

### Post by 11jmb on 2011-11-01
[http://netbeans.org/downloads/index.html](http://netbeans.org/downloads/index.html)

IIRC you will download a shell script that gets everything installed for you

---

### Post by NattyLight on 2011-11-01
> **11jmb said:**
> [http://netbeans.org/downloads/index.html](http://netbeans.org/downloads/index.html)

IIRC you will download a shell script that gets everything installed for you

  I was looking at the website and it looks like most of the DL files for Linux anyways is in a tar format? Do I just unzip it like if it were on windows? Thanks both of you guys and/or girls.

---

### Post by 11jmb on 2011-11-01
Yes, if its in .tar or .tar.gz format, you can extract the files, then it should be just 

```
./configure
make
sudo make install
```

---

### Post by NattyLight on 2011-11-01
> **11jmb said:**
> Yes, if its in .tar or .tar.gz format, you can extract the files, then it should be just 

```
./configure
make
sudo make install
```

 Awesome, thank you so much! Now for another unrelated question... is there some kind of source where I can learn about all the Ubuntu command line commands?

---

### Post by NattyLight on 2011-11-01
OK so the files have the .sh extension, when I tried to do the chmod +x  it doesnt work? Whats the syntax to make the .sh file executable in Ubuntu?

---

### Post by ibutho on 2011-11-01
Just run the installer by doing something like
```
sh netbeans-7.0.1-ml-javase-linux.sh
```

---

### Post by NattyLight on 2011-11-01
> **ibutho said:**
> Just run the installer by doing something like
```
sh netbeans-7.0.1-ml-javase-linux.sh
```

 It says it can't open it

---

### Post by ibutho on 2011-11-01
Do you have a JDK installed preferably Oracle Java? The commands work fine for me in Mint 11 with the latest Oracle JDK.

---

### Post by DarkAmbient on 2011-11-01
Anyone knows if Netbeans will be back in the repos? I've was thinking about upgrading to 11.10 tomorrow actually, but things like this makes me not wanna upgrade. It's not that I dont know how to install otherwise, I'm just lazy.

Sorry for being slightly off-topic.

---

### Post by 11jmb on 2011-11-01
> **DarkAmbient said:**
> Anyone knows if Netbeans will be back in the repos? I've was thinking about upgrading to 11.10 tomorrow actually, but things like this makes me not wanna upgrade. It's not that I dont know how to install otherwise, I'm just lazy.

Sorry for being slightly off-topic.

It is not.


> **NattyLight said:**
> OK so the files have the .sh extension, when I tried to do the chmod +x  it doesnt work? Whats the syntax to make the .sh file executable in Ubuntu?

```
chmod 777 install.sh
``` will give read/write/execute privlages to all users

---

### Post by NattyLight on 2011-11-01
> **ibutho said:**
> Do you have a JDK installed preferably Oracle Java? The commands work fine for me in Mint 11 with the latest Oracle JDK.

 I have OpenJDK 6

---

### Post by NattyLight on 2011-11-01
> **11jmb said:**
> It is not.




```
chmod 777 install.sh
``` will give read/write/execute privlages to all users

 Ok, I will try this.

---

### Post by NattyLight on 2011-11-01
Ok guys I figured it out, I right clicked on the sh file and made it executable via the permissions tab, now Im trying to decide if I should install JUnit or not?

---

### Post by NattyLight on 2011-11-01
Yes it does, :)

---

### Post by 11jmb on 2011-11-02
> **NattyLight said:**
> Im trying to decide if I should install JUnit or not?

Is this for fun/learning or big-time development? If you ever get into developing large applications, unit testing will become vital, so it may be worth your while to learn how to use the unit test suite that is pretty much the standard.

If you are just messing around and learning how to make simple apps, you might not want to waste your time.

---

### Post by NattyLight on 2011-11-02
> **11jmb said:**
> Is this for fun/learning or big-time development? If you ever get into developing large applications, unit testing will become vital, so it may be worth your while to learn how to use the unit test suite that is pretty much the standard.

If you are just messing around and learning how to make simple apps, you might not want to waste your time.

 I just installed it anyways, figured what the heck its not gonna hurt anything, it can only benefit me you know? I appreciate your help me :)

---

### Post by aneslin85 on 2011-12-20
> **ibutho said:**
> Just run the installer by doing something like
```
sh netbeans-7.0.1-ml-javase-linux.sh
```

It works, Thanks a lot.
I install jre 7 from ubuntu software center, and then i oved the downloaded file to my home directory, then run this command in terminal,
Perfect. thanks a lot

---

