---
title: "problems installing bin file"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-08-31
I have been trying to install a bin file but I don't know what I am doing wrong.

allan@allanlaptop:~$ chmod +x RealPlayer11GOLD.bin
chmod: cannot access `RealPlayer11GOLD.bin': No such file or directory
allan@allanlaptop:~$

---

### Post by tuxxy on 2008-08-31
Make sure you have changed to the current ddirectory of the .bin file, for example if you downloaded it to your Desktop then type

```
cd Desktop
```

Now try your original command again.

---

### Post by SuperSonic4 on 2008-08-31
have you went to the folder with real player in using cd (if its on the desktop you'd type cd ~/Desktop

---

### Post by halitech on 2008-08-31
where did you download the file to?

do an ls -l if your current directory and see if the file is there. if not you need to cd to where the file actually is

---

### Post by saskatchewan on 2008-08-31
When I switch to the desktop this is what I get.

allan@allanlaptop:~$ chmod +x RealPlayer11GOLD.bin
chmod: cannot access `RealPlayer11GOLD.bin': No such file or directory
allan@allanlaptop:~$ cd Desktop
allan@allanlaptop:~/Desktop$ chmod +x RealPlayer11GOLD.bin
allan@allanlaptop:~/Desktop$

---

### Post by saskatchewan on 2008-08-31
I downloaded the file to the desktop.

Here is what I get from chmod.

allan@allanlaptop:~$ cd ~/Desktop
allan@allanlaptop:~/Desktop$ chmod +x RealPlayer11GOLD.bin
allan@allanlaptop:~/Desktop$

---

### Post by ice2921 on 2008-08-31
After the chmod command run the following (in the same directory):

```
./RealPlayer11GOLD.bin
```

You may want to try this as well if the latter does not work:

```
chmod a+x RealPlayer11GOLD.bin

./RealPlayer11GOLD.bin
```

---

### Post by oldos2er on 2008-08-31
> **saskatchewan said:**
> I downloaded the file to the desktop.

Here is what I get from chmod.

allan@allanlaptop:~$ cd ~/Desktop
allan@allanlaptop:~/Desktop$ chmod +x RealPlayer11GOLD.bin
allan@allanlaptop:~/Desktop$

 So chmod worked. Next run "sudo ./RealPlayer11GOLD.bin"

---

### Post by saskatchewan on 2008-09-01
I have RealPlayer installed and there is an icon but when I click on it, nothing happens.

Any suggestions?

---

### Post by oldos2er on 2008-09-01
> **saskatchewan said:**
> I have RealPlayer installed and there is an icon but when I click on it, nothing happens.

Any suggestions?

 Can you type "realplay" in a terminal, and post the output here?

---

### Post by saskatchewan on 2008-09-01
allan@allanlaptop:~$ realplay
bash: realplay: command not found
allan@allanlaptop:~$

---

### Post by oldos2er on 2008-09-01
Try "realplayer"

---

