---
title: "Moving Program in Ubuntu"
date: 2013-10-02
forum: New to Ubuntu
---

### Post by oli.kerr on 2013-10-02
Hello all,

I currently have Adobe Reader 9 downloaded and installed from my 'Downloads' folder in my home directory. As a matter of my OCD I would like this folder from which the program is dependant to run to be moved to a more sensible location such as 'file system/usr/lib'.

However, when I go to move the Adobe folder, for obvious reasons I get an error message saying I do not have permissions to move the folder. Also, if it were to be moved Adobe will stop working. What are your suggestions guys?

Thanks in advance

---

### Post by grahammechanical on 2013-10-02
I do not think that you have anything to worry about. You downloaded Adobe Reader 9 deb into the downloads folder. How did you install it? Did you use the File Manager to open it using the Software Centre? If so, then the Software Centre would have installed the libraries of this program in all the appropriate places that Linux programs reside in. I do not think that this program is running from the Downloads folder.

I would not be surprised if you can delete that Adode folder that is in the downloads folder but you cannot copy it into /usr/lib because it is a system folder and you need administrator permissions to paste anything into that folder. You will find that all you need to do it to create a folder to store the downloaded deb file into so that you can reinstall the program if you need to.

To use the File Manager with administrator permissions run

```
gksudo nautilus
```

if you are using 12.04. If it is 13.04 and onwards run this command first

```
sudo apt-get install gksu
```

But be careful how you use File Manager in administrator mode because we can do serious damage to the OS.

Regards

---

### Post by heir4c on 2013-10-02
Why use the second command? gksudo and gksu works fine in 13.04.

---

