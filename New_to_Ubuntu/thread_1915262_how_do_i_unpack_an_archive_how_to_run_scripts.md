---
title: "how do i unpack an archive? how to run scripts?"
date: 2012-01-25
forum: New to Ubuntu
---

### Post by arnicainthemembrane on 2012-01-25
Hello, I'm trying to install and run "Catan Online World". Thus far I've been instructed to download a file "onlineworld_3_909_eng_linux.tgz" (which I did) then: 

"Please unpack the archive into a folder where you have full write privileges at all times. You may use, for example, your home directory or also your desktop.
Inside the folder "COW-Client," please run the script "Create-Desktop-Icon.sh." This will create an icon called "Catan Online World" on your desktop"

My question, how do I do this? What does this all mean? How do I unpack an archive in a given folder, then how do I run scripts? I know these are very basic functions, but for a casual computer user it doesn't make much sense... any help appreciated. thanks.

---

### Post by oldos2er on 2012-01-25
Moved to Absolute Beginner Talk.

---

### Post by cortman on 2012-01-25
Very easy! The .tgz file you downloaded is a compressed file- just like a .zip in Windows. To unpack it, simply double click- it'll bring up the archive manager program, which will give you an "extract" option. Extract it to your home folder.
To run the script, open a terminal and copy/paste the code below:

```
cd ~/onlineworld_3_909_eng_linux/COW-Client
chmod +x Create-Desktop-Icon.sh
./Create-Desktop-Icon.sh
```

---

### Post by arnicainthemembrane on 2012-01-26
i appreciate your help! what exactly does

chmod +x Create-Desktop-Icon.sh

do? I understand that the other commands simply moved me to the file, "unpacked" it and then started up the Desktop Icon.

---

### Post by cortman on 2012-01-26
> **arnicainthemembrane said:**
> i appreciate your help! what exactly does

chmod +x Create-Desktop-Icon.sh

do? I understand that the other commands simply moved me to the file, "unpacked" it and then started up the Desktop Icon.

Sure! Sorry I didn't explain more fully last night; I was on my mobile.
chmod (you can look up the man page by typing "man chmod" in the terminal) modifies file permissions. All files in a Unix-like OS have three possible permissions: Read, Write, and Execute. "chmod +x" adds (+) the execute permission (x)  to the file, so you can run it as a program rather than just view it (read) or edit it (write).
If you're interested in learning more on the command line, we're compiling a master list of resources [here.]("http://ubuntuforums.org/showthread.php?t=1909108")

---

