---
title: "problem with fs-driver"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by siddharthshukla on 2008-11-19
I recently split my ext3 partition into /home and ubuntu sytem files.. to do this i used Gparted partition tool. However i am not able to access my /home from windows using fs-driver and i figured out it was because the Inode of my /home is larger than 128 bytes.. The only solution seems to be to reformat the /home to Inode of 128 bytes.. But i don't wanna loose my files on /home.. can anyone please suggest any solution to this problem , is there any other s/w tat can acess ext2/ext3 with inodes >128 bytes???

---

### Post by talsemgeest on 2008-11-19
I havent found any way to get any of the ext3 windows drivers to work with inodes of more than 128 bytes, so if you find a way, please let me know.

As for formatting, do you have anywhere big enough to put all of the files from your /home partition? If you can back up all of your files (remembering the hidden ones), it should be easy enough to copy them back after you format.

---

