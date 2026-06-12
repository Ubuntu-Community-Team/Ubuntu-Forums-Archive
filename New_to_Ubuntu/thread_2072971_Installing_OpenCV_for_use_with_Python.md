---
title: "Installing OpenCV for use with Python"
date: 2012-10-18
forum: New to Ubuntu
---

### Post by clum94 on 2012-10-18
So I am completely new with Linux, I don't know anything about it, so little in fact whats the difference between Linux and Ubuntu or are they the same? Not what my thread is about anyway.

What I want to know is how to install OpenCV to Ubuntu version 11.10 (had problems installing the latest version of Ubuntu)I don't understand the sudo codes? sudo apt-get install eclipse for example, so i have been watching youtube videos and what not but cannot seem to install OpenVC for use with Python, everytime I try to install it and think ive cracked it, i havent. I keep getting the no module "cv" in python shell. 

If anyone can help me with this it would be every so much appreciated and in anyway (other than telling me to give up) even if you can tell me how to uninstall what ever i have already installed to do with python, opencv and just start again from step 1. If you have any questions I will try to answer them, please help :)

---

### Post by audiomick on 2012-10-18
Firstly, Linux is the basic operating system, and ubuntu is a distribution based on Linux, and including over and above that a large number of additional programs.

Regarding sudo: A user logged on to a computer can be an administrator or have no administrator permissions. This is extremely simplified, but it will do for now. This also applies to windows. In the Linux world, the top administrator is called root. Root is allowed to do anything on the computer and access everything. Most Linux distributions have a root account and at least one normal user account. One normally does not log on as root for day to day business on the computer. One reason for this is that if a virus sneaks in an pretends to be the current user, if that user is not root then the virus can't do any damage on the computer. 

Ubuntu is set up such that the root account is locked. This is for security reasons. Sometimes, however, the user needs to have root permissions to do administration tasks on the computer. The sudo function is set up on ubuntu systems to provide root permissions to the user for that eventuality. Using apt-get to install programs requires root permission, so you have to issue the apt-get command with a sudo before it to enable it to work. If you try and install something via the software centre, you are also asked for your password. This is because, effectively, the software centre is invoking sudo apt-get behind the graphical interface.

I am not familiar with Open CV, but I searched for it in Synaptic and came across a package called libcv4, one called python-opencv, one called opencv-doc, one called libhighgui4, and a few others as well that look like the might be related. I reckon what you are missing is in there somewhere. Open the software centre, type in "Open CV" in the search box, and install what you reckon you need.

---

