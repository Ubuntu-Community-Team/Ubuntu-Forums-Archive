---
title: "[SOLVED] permission problem? trying to extract to /opt"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by xdarkday on 2008-06-19
Trying to install xampp.
Downloaded XAMPP Linux 1.6.6 to my desktop
tried this command in terminal
```
richard@richard-desktop:~$ sudo tar xvfz xampp-linux-1.6.6.tar.gz -C /opt
[sudo] password for richard: 
tar: xampp-linux-1.6.6.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```
any ideas whats going wrong?

---

### Post by Dr Small on 2008-06-19
Please type:
```
ls ~ | grep xampp-linux-1.6.6.tar.gz
```

If you get no output, then it means the file does not exist, similar response to the tar error in your post.

Edit,
Anyhow, just run this:
```
sudo tar xvfz ~/Desktop/xampp-linux-1.6.6.tar.gz -C /opt
```

---

### Post by avtolle on 2008-06-19
First thought```
cd Desktop
sudo tar xvfz xampp-linux-1.6.6.tar.gz -C /opt
```
Give that a try

---

### Post by iaculallad on 2008-06-19
Try changing directory to your Desktop:

```
cd ~/Desktop
sudo tar xvfz xampp-linux-1.6.6.tar.gz -C /opt
```

---

### Post by xdarkday on 2008-06-19
> **Dr Small said:**
> Please type:
```
ls ~ | grep xampp-linux-1.6.6.tar.gz
```

If you get no output, then it means the file does not exist, similar response to the tar error in your post.

Edit,
Anyhow, just run this:
```
sudo tar xvfz ~/Desktop/xampp-linux-1.6.6.tar.gz -C /opt
```

Thank you for the quick response. I got no output after using that command. What does this mean? The file i downloaded really does not exist? How do I manage to further fix my problem?

---

### Post by Dr Small on 2008-06-19
The file exists in ~/Desktop/ just not in ~

---

### Post by xdarkday on 2008-06-20
You know what dudes? Sometimes its the smallest things you forget. Thank you so much.

---

