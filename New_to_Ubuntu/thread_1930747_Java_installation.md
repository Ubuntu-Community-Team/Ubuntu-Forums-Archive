---
title: "Java installation"
date: 2012-02-24
forum: New to Ubuntu
---

### Post by kp00274 on 2012-02-24
I am an absolute newbie and i wanted to know the correct way to install java on ubuntu 10.04 LTS. I downloaded a Linux RPM file and when i read the instructions for its installation it said to open the terminal and type 'su' (without the ' and ' sign) and when asked for the root user password type the password. But, when i tried it and typed the password when prompted to do so it said "Authentication Failure". I dont know what the problem is cause I am the solo user for it, although i have installed the ubuntu inside the windows but i dont know if that is the problem. Can it be issue that it might not be working because it is installed inside windows? I would really appreciate any help.

Thanks in advance.

---

### Post by Paqman on 2012-02-24
On Linux you generally don't get your software by downloading it from websites and installing it manually. You have a package manager on your computer that can automatically find, download, install, update and cleanly remove almost any kind of software you'll ever need.

Open up Ubuntu Software Centre and search for "java", then click to install.

---

### Post by kp00274 on 2012-02-24
I did that, but it seems that it is not working cause when i tried to download youtube videos using keepvid it still says that I don't have java installed. I just want to be able to download videos using keepvid, and also I want to know why my password was not working when I tried to do so. Can you tell something about that too.

---

### Post by link307 on 2012-02-24
First, you should know that the password `su` required is unique. It's the root password and it's not set normally.
If you want to install Java, I recommend two ways:
1.  deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
2.  sudo add-apt-repository ppa:ferramroberto/java

---

