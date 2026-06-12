---
title: "how install skype in lubuntu 12.10"
date: 2012-11-04
forum: New to Ubuntu
---

### Post by ninos on 2012-11-04
can this be done
through terminal commands?

---

### Post by monkeybrain2012 on 2012-11-04
Open Synaptic, go to Settings > Repositories in the drop down menu on the top and check the box Canonical Partners, reload synaptic and search for Skype to install it.

Oh, the search function in Synaptic doesn't work in Lubuntu because they don't install it by default for some strange reasons, so, before you do all this use Synaptic to install apt-xapian-index just by scrolling down, close Synaptic and restart it then do the steps above.

EDITED: to use the command line

```
sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"

sudo apt-get update

sudo apt-get install skype
```

---

### Post by amjjawad on 2012-11-05
> **ninos said:**
> can this be done
through terminal commands?

[https://help.ubuntu.com/community/Lubuntu/3rdParty#How_to_install_Skype](https://help.ubuntu.com/community/Lubuntu/3rdParty#How_to_install_Skype)

---

### Post by SBMN7 on 2012-11-05
Bro, open Ubuntu Software Center then sreach for skype then start download, when your download will complete it will automatically start installing on your system.

---

### Post by amjjawad on 2012-11-05
> **SBMN7 said:**
> Bro, open Ubuntu Software Center then sreach for skype then start download, when your download will complete it will automatically start installing on your system.

Lubuntu does not have Ubuntu Software Center ;)

---

### Post by SBMN7 on 2012-11-05
Try this:
1. Download the Ubuntu version of Skype
2. Use the Archive manager to uncompress it. Alternatively, right click on the deb package and select "extract here"
3. Rename the uncompressed folder, by changing the ending from i386 to lpia. (the folder should be now named: skype-debian_2.0.0.72-1_lpia)
4. Open the folder
5. There are 3 files. remove the "debian-binary" file
6. Decompress "control.tar.gz". There are tree files in it.
7. Make a folder "DEBIAN" in the main folder, and placed the 3 files you just decompressed inside it.
8. Open one of the files inside DEBIAN,"control". Change the line "Architecture: i386"into "Architecture: lpia"
9. Open the other archive "data.tar.gz". There is a folder "." inside. Open it (double click). Select both the folders (usr and etc) and select uncompress.
10. Remove the files "control.tar.gz" and"data.tar.gz"
11. You should now have your main folder with the following inside:
DEBIAN folder with tree text files in it (conffiles, control, md5sums); a "usr" folder and a "etc" folder.
12. You are now ready to prepare your lpia deb folder.
13. From the command line, go to the folder that contains your main skype folder you just prepared (most likely named: skype-debian_2.0.0.72-1_lpia).
14. type: dpkg --build skype-debian_2.0.0.72-1_lpia
15. Your deb package is ready. Double click on it and follow instruction. After installation it should appear in Synaptic, and from there you can remove it at any time.
16. Enjoy!!!

---

### Post by amjjawad on 2012-11-05
> **SBMN7 said:**
> Try this:
1. Download the Ubuntu version of Skype
2. Use the Archive manager to uncompress it. Alternatively, right click on the deb package and select "extract here"
3. Rename the uncompressed folder, by changing the ending from i386 to lpia. (the folder should be now named: skype-debian_2.0.0.72-1_lpia)
4. Open the folder
5. There are 3 files. remove the "debian-binary" file
6. Decompress "control.tar.gz". There are tree files in it.
7. Make a folder "DEBIAN" in the main folder, and placed the 3 files you just decompressed inside it.
8. Open one of the files inside DEBIAN,"control". Change the line "Architecture: i386"into "Architecture: lpia"
9. Open the other archive "data.tar.gz". There is a folder "." inside. Open it (double click). Select both the folders (usr and etc) and select uncompress.
10. Remove the files "control.tar.gz" and"data.tar.gz"
11. You should now have your main folder with the following inside:
DEBIAN folder with tree text files in it (conffiles, control, md5sums); a "usr" folder and a "etc" folder.
12. You are now ready to prepare your lpia deb folder.
13. From the command line, go to the folder that contains your main skype folder you just prepared (most likely named: skype-debian_2.0.0.72-1_lpia).
14. type: dpkg --build skype-debian_2.0.0.72-1_lpia
15. Your deb package is ready. Double click on it and follow instruction. After installation it should appear in Synaptic, and from there you can remove it at any time.
16. Enjoy!!!

I'm sorry but why to make life more complicated? 
Obviously, the OP is a new user and we usually must take this into consideration and guide them with the easiest ways.

I'm not saying this is wrong but it's too long :) way too long!

---

### Post by Lyfang on 2012-11-05
> **ninos said:**
> can this be done
through terminal commands?
Open terminal:
```
sudo nano /etc/apt/sources.list
```

Uncomment these hashes (#)
```
deb http://archive.canonical.com/ubuntu quantal partner
deb-src http://archive.canonical.com/ubuntu quantal partner
```

```
sudo apt-get update && sudo apt-get install skype
```

---

