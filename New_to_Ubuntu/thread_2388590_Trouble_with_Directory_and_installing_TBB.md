---
title: "Trouble with Directory and installing TBB"
date: 2018-04-05
forum: New to Ubuntu
---

### Post by creamedcorn on 2018-04-05
I'm following a guide [https://askubuntu.com/questions/382394/how-do-i-install-the-tor-browser-bundle-in-ubuntu/420261](https://askubuntu.com/questions/382394/how-do-i-install-the-tor-browser-bundle-in-ubuntu/420261) (Second answer, jtd) on installing The Tor Browser Bundle on ubuntu, however on the verifying gpg signatures 2nd dot point I cannot seem to find the directory for the TBB, I tried dragging the TBB download from files but that doesn't seem to work i'm not sure what directories even are (4th day of using linux) these are the errors from my terminal:  user@Work:~$ cd ~/path/to/TBB_directory bash: cd: /home/user/path/to/TBB_directory: No such file or directory  user@Work:~$ cd '/home/user/Downloads/tor-browser-linux64-7.5.3_en-US.tar.xz' bash: cd: /home/user/Downloads/tor-browser-linux64-7.5.3_en-US.tar.xz: Not a directory,  I am using Ubuntu 16.04 LTS if that helps

---

### Post by deadflowr on 2018-04-05
Change directories to the Downloads folder instead of the non-existent path directory
like
```
cd Downloads
```
then run the gpg --verify command

Your prompt should look like this
```
user@Work:~/Downloads$ 
```
which will tell you that you are in the /home/user/Downloads directory (the ~ equals your current users home folder, top level)

tip: use ls (LS in small letters) when you enter the Downloads folder to see the names of the files in the directory.
```
ls
```

---

### Post by creamedcorn on 2018-04-05
Thank you so much, I cant believe it was that easy. however when i try validating it just gives me this info gpg: verify signatures failed: file open error, is the verification command wrong or something Edit: Fixed, on tor website you have to right click the (sig) link and choose save as to your downloads :)

---

