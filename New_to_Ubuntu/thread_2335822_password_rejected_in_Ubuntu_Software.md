---
title: "password rejected in Ubuntu Software"
date: 2016-09-01
forum: New to Ubuntu
---

### Post by glatt on 2016-09-01
Hello!
I tried to download ejabbered via "Ubuntu Software" (vers. 16.04) and this requires my email address and password of Ubuntu One. But the password is rejected although it works and opens Ubuntu One in the browser. How can I solve this problem?  Thanks for advice!

---

### Post by howefield on 2016-09-01
> **glatt said:**
> Hello!
I tried to download ejabbered via "Ubuntu Software" (vers. 16.04) and this requires my email address and password of Ubuntu One. But the password is rejected although it works and opens Ubuntu One in the browser. How can I solve this problem?  Thanks for advice!

You shouldn't need an email address nor Ubuntu One password to download from the Ubuntu Software application. Can you post a screenshot of what you are trying to do ? The password should be the one that you used when setting up your user account during the Ubuntu installation.

---

### Post by glatt on 2016-09-01
I have tried all Ubuntu-related passwords unsuccessfully. Attached a screenshot of what I'm tying to do.[IMG]/Home/Pictures/Screenshot.png[/IMG]

---

### Post by howefield on 2016-09-01
> **glatt said:**
> I have tried all Ubuntu-related passwords unsuccessfully. Attached a screenshot of what I'm tying to do.[IMG]/Home/Pictures/Screenshot.png[/IMG]

Use the paperclip icon to attach your image to the posting. Not available in the Quick Reply window, so click Go Advanced or Reply to Thread buttons.

---

### Post by glatt on 2016-09-01
As you can see I'm really new to ubuntu...
Hope the screenshot is ok by now.

---

### Post by howefield on 2016-09-01
OK, so it is a snap that you are trying in to install which would mean an Ubuntu One sign on details.

There is also a .deb package for ejabberd available although it is version 16.01-2 as opposed to the snap version which is 16.08, so slightly more up to date, if 16.01-2 isn't an issue, install with..

```
sudo apt install ejabberd
```

I mention this in case you are unaware given that you are new to Ubuntu, if you really want the snap package try installing via the command line, see if it accepts your login details.. (obviously use the correct email address)

```
sudo snap login xxxxxxxxx@xxxxxx.com
```

Type your password when prompted, you won't see the characters being typed.
 
Then, when you get the "*Login successful*" message, use the following to install..

```
snap install ejabberd
```

Example
```
hugh@xenial-laptop:~$ sudo snap login xxxxxxxxx@xxxxxx.com
Password: 
Login successful
hugh@xenial-laptop:~$ snap install ejabberd
22.39 MB / 22.39 MB [==================================================================================================] 100.00 % 2.01 MB/s 

ejabberd (stable) 16.08 from 'wyrddreams' installed
hugh@xenial-laptop:~$ 
```

---

### Post by glatt on 2016-09-01
I followed your suggestions, here is the result:

```
:~$ sudo apt install ejabbered
[sudo] password for marco: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ejabbered

:~$ sudo snap login [email]xxxxx@xxxxxxx.xx[/email]
Password: 
Login successful
:~$ snap install ejabbered
error: cannot install "ejabbered": snap not found
:~$ 
```
The screenshot shows an anomaly: ejabbered is listed among installed packages but with an install button instead of a remove button.

---

### Post by howefield on 2016-09-02
Have you updated since installing Ubuntu ?

```
sudo apt update
```
```
sudo apt upgrade
```
```
sudo apt install ejabberd
```

PS. You misspelt ejabberd in your attempt to install the snap package, you could try again with the correct name....

---

### Post by glatt on 2016-09-02
Now it works. Thanks a lot for help and hints!

---

### Post by howefield on 2016-09-02
Cool, thanks for the update and feel free to mark the thread as solved :)

---

