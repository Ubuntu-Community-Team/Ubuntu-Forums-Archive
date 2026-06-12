---
title: "E: unable to locate package ros fuerte"
date: 2014-05-06
forum: New to Ubuntu
---

### Post by kevin82 on 2014-05-06
so i'm trying to install ros-fuerte, but everytime i tried, this error comes up:
E: unable to locate package ros-fuerte-desktop-full

Code:
$ sudo sh -c 'echo "deb [http://packages.ros.org/ros/ubuntu](http://packages.ros.org/ros/ubuntu) lucid main" > /etc/apt/sources.list.d/ros-latest.list'
$ sudo sh -c 'echo "deb [http://packages.ros.org/ros/ubuntu](http://packages.ros.org/ros/ubuntu) `lsb_release -cs` main" > /etc/apt/sources.list.d/ros-latest.list'
$ wget [http://packages.ros.org/ros.key](http://packages.ros.org/ros.key) -O - | sudo apt-key add –
$ sudo apt-get update
$ sudo apt-get install ros-electric-desktop-full
   Reading package lists... Done
   Building dependency tree
   Reading state information... Done
   E: Unable to locate package ros-fuerte-desktop-full

Can anybody help? Thanks...

---

### Post by bapoumba on 2014-05-06
First off, I have no idea about the package in question..
Second, are you on Lucid ? The desktop version has reached end of life in May last year although the server version is supported until next year.

That said, the package you are looking for is here : [http://packages.ros.org/ros/ubuntu/dists/lucid/main/binary-i386/Packages](http://packages.ros.org/ros/ubuntu/dists/lucid/main/binary-i386/Packages) and there [http://packages.ros.org/ros/ubuntu/dists/lucid/main/binary-amd64/Packages](http://packages.ros.org/ros/ubuntu/dists/lucid/main/binary-amd64/Packages), not sure which architecture you are using.

Please post the output to 
```
cat /etc/apt/sources.list.d/ros-latest.list
```
Would the line be commented out ?

---

### Post by grumblebum2 on 2014-05-06
The first command sets the ros repo to **lucid**
 ```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu **lucid** main" > /etc/apt/sources.list.d/ros-latest.list'
```
Where I see **ros-fuerte*** packages.


The second command you ran changes the ros repo to the **current release** you're using.
```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu `**lsb_release -cs**` main" > /etc/apt/sources.list.d/ros-latest.list'
```
Where I don't see any **ros-fuerte*** packages.

---

