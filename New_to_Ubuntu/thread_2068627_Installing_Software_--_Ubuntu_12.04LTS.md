---
title: "Installing Software -- Ubuntu 12.04LTS"
date: 2012-10-09
forum: New to Ubuntu
---

### Post by Curt Carpenter on 2012-10-09
Hi.
I've downloaded a few programs, and they appear as files in my Downloads folder -- but I can't understand how to install them properly (or at all:().  

For example:  I just downloaded Adobe Reader.  When I open the file AdbeRdr9.5.1-1_i486linux_enu.bin using the Archive Mounter, there is a flicker on the Nautilus window -- but nothing seems to happen otherwise.  

Any clues as to what I need to do would be appreciated.  I need the PDF markup tools that Adobe Reader provides (highlighter & notes) or I'd just use the built-in PDF reader.

(Part of my difficulty is from just not really understanding the file system.  If I click on an icon for an executable file, for example, that appears in a folder in my Home directory, nothing happens.)

Help/suggestions/pointers to docs I should read appreciated!

---

### Post by audiomick on 2012-10-09
I believe you can get Adobe Reader from the software center. Open the software center and go to the "package sources" entry at the bottom of the edit menu. Make sure the box is ticked for the "multiverse" sources.

Having done that, type "adobe reader" in the search box. I think you will find Adobe Reader 9 will show up.

As far as other things go, you should try and get a .deb file of anything you want to install. Having done that, you should be able to right click on the file and choose to install it with the software center. 

If you can only get a .tar.gz file, there is very often a read-me file in there that tells you what to do with it.

Other than that, post what it is exactly that you are trying to install. Hopefully someone will be able to tell you how to go about it.

Generally speaking, it is a good idea to stick to what is available through the software centre. Nearly everything you need is there.

---

### Post by raja.genupula on 2012-10-09
> For example:  I just downloaded Adobe Reader.  When I open the file  AdbeRdr9.5.1-1_i486linux_enu.bin using the Archive Mounter, there is a  flicker on the Nautilus window -- but nothing seems to happen otherwise.   

one more thing  you can install a .bin file by using this command 

```
chmod +x <filename>.bin
./<filename>.bin
```

---

### Post by grahammechanical on 2012-10-09
My guess is that the Archive Manager cannot do anything with that file because it is a program executable and not an archive file.

It is usually best to install programs through the Ubuntu Software Centre. Then all the bits of the program will be put in all the right places in the file system.

Ubuntu is based upon Debian Linux and so Ubuntu uses the deb packaging format for program files. If this program had the extension of deb and not bin then installing it would be as simple as right clicking the file and selecting Open with Ubuntu Software Centre.

The deb extension tells us that the program is packaged to work on Debian based operating systems (which Ubuntu is).

I do not know if selecting Open with Ubuntu Software Centre will work with bin files. You might need to do something else with that file first.

Regards.

---

### Post by newb85 on 2012-10-09
To give an answer more targeted at your immediate need, Adobe Reader 9 is not in the multiverse repository; it's in the main repostitory.  The actual package name is acroread.

FYI, for a file to actually be executable in Ubuntu there are two requirements.  First, the file permissions must allow its execution.  This was the purpose of the first line of code given by raja.genupula.  In Ubuntu, when you download a file, the permissions are automatically set to prevent execution.  Second, it must be a file type your system knows how to execute.  (For example, your system won't know how to execute a .exe unless you install an abstraction layer like Wine, and even then, it must be executed a specific way.  In general, abstraction layers are a sub-optimal approach.)

---

### Post by sumancs on 2012-10-09
The best way to install a software in Ubuntu, in my view, is to install it via terminal by:
sudo apt-get install packageName[.extension]

---

### Post by audiomick on 2012-10-09
> **newb85 said:**
> To give an answer more targeted at your immediate need, Adobe Reader 9 is not in the multiverse repository; it's in the main repostitory.  The actual package name is acroread.

OK. I assumed it would be multiverse because it is proprietary. Wont argue, though.

---

### Post by Curt Carpenter on 2012-10-09
Thank you all for the quick help.

I downloaded the Adobe Reader file from the Adobe site using Firefox, and will try your suggestions for making it work.  The instructions from Adobe said to open the file with Archive Mounter, but that clearly doesn't work -- so I'll try the other approaches you've suggested.   Many thanks!

I did download the reader from the Software Center and it works fine.   I'll try the other tactics (using chmod for example) though,  just as a way to try to learn how to use Ubuntu and Linux.

---

### Post by Cheesemill on 2012-10-09
Take a look at this page, it explains all about installing software in Ubuntu:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by newb85 on 2012-10-09
> **audiomick said:**
> OK. I assumed it would be multiverse because it is proprietary. Wont argue, though.

Oh, actually, we were both wrong.  It's in the Canonical Partners repo.  (Which, for some reason, Synaptic labels "main"...)

---

### Post by audiomick on 2012-10-09
> **newb85 said:**
>  It's in the Canonical Partners repo.

Ah, that makes sense. Thanks for checking.

---

### Post by oldos2er on 2012-10-10
In addition to the link Cheesemill posted, see [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

Downloading programs from websites is last on the list of methods to install programs.

---

