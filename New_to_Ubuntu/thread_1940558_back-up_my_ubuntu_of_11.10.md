---
title: "back-up my ubuntu of 11.10"
date: 2012-03-13
forum: New to Ubuntu
---

### Post by yangscofield on 2012-03-13
I have use fedora for several month for studying of C/C++! Last month, recommended by my friend, i like ubuntu much more now. But i don't know how to back-up the system in case of the collapse of the system  to lose the data. Besides, my English is not good enough,sorry for the expression wrong if any!
    It's my first time to post a thread and hope to make friends here!

---

### Post by zombifier25 on 2012-03-13
If you don't mind reinstalling the software packages, then you only need to backup your home folder, which contains all your personal files, settings, configs...

---

### Post by ubudog on 2012-03-13
Welcome to the forums!

The way I backup my data, is using rsync.

You can do something like this:
Plugin your backup drive.

Assuming it's mounted at /media/drive, this is what'd I'd do:
```
rsync -av --progress /home/username/ /media/drive/bak/
```

Also assuming you are backing up your home directory.

For more info on rsync, run: 
```
man rsync
```

Best of luck,
ubudog

---

### Post by jerrrys on 2012-03-13
maybe clonezilla

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by kazztan0325 on 2012-03-14
I use following tools for backing up my system.

***(NOTE: You should save the backup files in External media or Online Storage. In my case, I save them in USB External HDD.)***


- **'Y PPA Manager'** to back up Repositories.

**"WebUpd8" team > Y PPA Manager (in Launchpad)**
[https://launchpad.net/~webupd8team/+archive/y-ppa-manager]("https://launchpad.net/~webupd8team/+archive/y-ppa-manager")

**"Y PPA MANAGER 0.0.8.4 RELEASED, FINALLY WORKS IN KDE TOO"**
[http://www.webupd8.org/2011/11/y-ppa-manager-0084-released-finally.html]("http://www.webupd8.org/2011/11/y-ppa-manager-0084-released-finally.html")


- **'Synaptic Package Manager'** to back up a list of packages which are installed.

1. Click on File > Save Markings As...
2. 'Save Changes' dialog will appear.
3. Tick ON against 'Save full state, not only changes'
4. Select Place to save the file.
5. Input File Name (e.g. Packages-list.txt).
6. Click on 'Save' button.
(If you have not installed it yet, you can install it with 'Software Center'.)


- **'Deja Dup'** to back up Home folder.

1. Open 'System Settings'.
2. Click on 'Backup' icon.
3. 'Deja Dup Backup Tool' window will appear.
4. Click on 'Just show my back up settings' button if you opened 'Backup' for the first time.
5. Configure backup settings, and then click on 'Back Up Now' button.

---

### Post by Ghost_Mazal on 2012-03-14
Rsync rocks. I even use it to clone my HDD. Simple , effective and fast.

---

### Post by Rodney9 on 2012-03-14
Clone your full hard drive with Clonezilla, works perfectly.

[http://www.clonezilla.org/](http://www.clonezilla.org/)

Clonezilla Tutorial showing you both how to backup and restore an operating system

[http://www.dedoimedo.com/computers/clonezilla.html](http://www.dedoimedo.com/computers/clonezilla.html)

Rodney

---

