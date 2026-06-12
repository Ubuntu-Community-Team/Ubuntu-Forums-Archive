---
title: "NEED Sony Ericsson Phone Manager"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by balachandarlinks on 2008-06-07
****
Hai,
    i m using using **ubuntu 8.04**....in windows there is a software called **my phone explorer** is used to manage my **sony ericsson w700i**....
    I **_need a software for ubuntu to manage my phone sony ericsson w700i_**....
    Waiting for the reply........Help me.....

---

### Post by rraj.be on 2008-06-07
I am  too a big fan of My phone explorer an unforutnately there is no version of it in ubuntu.

But there is some other packages like  wammu gammu etc.

There are minimal support like downloading sms and contacts but not equal to my phone explorer.

you can install gammu and wammu by typing the following in terminal

```
sudo apt-get install wammu

sudo apt-get install gammu
```

---

### Post by balachandarlinks on 2008-06-07
I installed those two...But i open wamu the **error message** given below is shown in a pop up window....if i ignore it then the phone is identified and connected...but n**o information can be retrieved **from d phone...that time also a error message is show...

[B]Wammu configuration was not found and Gammu settings couldn't be read.

Do you want to configure phone connection now?[/B]
Help Me..

---

### Post by rraj.be on 2008-06-07
Yes similar to  my phone explorer  you should configure wammu and gammu.

when you start the wammu for the first tim eyou will be asked to configure.

If you havnt configured you can configure now by going to 

wammu -->setting's.

In settings chose connection tab and set the following

phone name : what you like or default sonny ericsson.

device :/dev/ttyACM1

and i think you can set others by your own.

I am not having my wammu nor my mobile now.

So i cant be much deepth.

If you have any doubt you can ask it specificaly.

---

### Post by balachandarlinks on 2008-06-07
By ignoring that pop up i connect the phone again....i can see my messages and contacts....
     But** cant see calls** (Error massage comes) and **cant look the contacts** in my sim...
     Moreover can i **message and call using wammu...???**

---

### Post by prabath_fun on 2008-11-07
Me too facing same problem.......

---

### Post by prabath_fun on 2008-12-15
any updates........

---

### Post by theaceoffire on 2009-02-12
I still haven't solved this completely, but I am currently looking at the following threads:

[http://ubuntuforums.org/showthread.php?t=861120&highlight=Sony+Ericsson+W580i&page=8](http://ubuntuforums.org/showthread.php?t=861120&highlight=Sony+Ericsson+W580i&page=8)

and testing out "Bitpim".

Also, the error you are getting is because of an older version of gammu. 

To get the newest version of wammu/gammu, go here:
[https://launchpad.net/~nijel/+archive/ppa](https://launchpad.net/~nijel/+archive/ppa)

---

### Post by prabath_fun on 2009-10-21
I can able to connect my W810I with Wammu using data cable. I am using Ubuntu 9.04 and Wammu0.29, Gammu 1.22.1. Even, I connected Nokia 3120 Classic using bluetooth to Wammu.

Prabath

---

