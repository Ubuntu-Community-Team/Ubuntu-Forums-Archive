---
title: "how to install and run remastersys"
date: 2012-10-21
forum: New to Ubuntu
---

### Post by vegas89 on 2012-10-21
I have downloaded remastersys, and installed it to my system. Ubuntu 12.4
 How do I get to it to use it.](*,)

---

### Post by newb85 on 2012-10-21
I'm not familiar with remastersys, but there's this:
[http://www.geekconnection.org/remastersys/ubuntu.html]("http://www.geekconnection.org/remastersys/ubuntu.html")

Also, I'd imagine you could find out a few more details of use with
```
man remastersys
```

---

### Post by vegas89 on 2012-10-21
I have it downloaded and installed , I just can't get to it to use it](*,)

---

### Post by newb85 on 2012-10-21
Have you tried searching for it in the Dash?

---

### Post by vegas89 on 2012-10-22
Yes it is in the dash, but I need the terminal code scripts so I can copy and paste to pull it out and run it!!

---

### Post by newb85 on 2012-10-22
Are you saying the GUI isn't straight-forward?

You haven't yet said what you're trying to do.  Do you want to make a copy of your setup (without your personal files)?  Do you want to create a backup of your entire system that you can easily install on another HDD?

---

### Post by vegas89 on 2012-10-22
I have got my ubuntu 12.4 set up just as I want it and would like to make a reinstall disk that would just be for my own personal use. I would like to have the disk copy to have my OS with everything on it just as it is now so I could reload the OS without having to reset everything I have saved to it.

---

### Post by Cheesemill on 2012-10-22
Why do you need to use the terminal? Just run the GUI from the Dash.

---

### Post by vegas89 on 2012-10-22
When I click on the icon in the dash it just shows up as installed. How do I access the program to use it..](*,)

---

### Post by squakie on 2012-10-22
How did you install it?

---

### Post by vegas89 on 2012-10-22
Pulled it out of the download file and hit install#-o

---

### Post by ezsit on 2012-10-22
Have you tried following the instructions on their own website?

[www.remastersys.com](www.remastersys.com)

It is all laid out pretty clearly.

---

### Post by squakie on 2012-10-22
Have you tried:

sudo remastersys backup

and/or

sudo remastersys dist

?

These are the first to examples right at the top of "ubuntu" tab of the website pointed to by ezsit above.

If these come up with any type of error, post it back here so we can see it.

That same page says how to download and install.  Note that the GUI is a separate package - you have to install remastersys and the GUI if you want GUI'd access.  Be sure you have enabled the correct repository - if 12.04 then precise, if 12.10 look for quantal.

---

