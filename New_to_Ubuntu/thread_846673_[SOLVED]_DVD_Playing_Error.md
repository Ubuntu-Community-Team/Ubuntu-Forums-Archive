---
title: "[SOLVED] DVD Playing Error"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by AMC25114 on 2008-07-01
Hello,

Well so far this is the first problem ive run into since starting to use Ubuntu. Every time i try to play a DVD i get a error that says Could not read from resource. I had a friend help me and he said that he downloaded everything he could think of, restricted extras and codecs. Im not sure what to do from here so any help is appreciated. Thanks
  
  Aaron

---

### Post by bhadotia on 2008-07-01
Is the dvd running on windows? Well if its not the disk is damaged (or something like that).

---

### Post by silkstone on 2008-07-01
Have you installed libdvdcss2?

You can do it from Synaptic, or by...

```
sudo apt-get install libdvdcss2
```

---

### Post by AMC25114 on 2008-07-01
Yes, the DVD works on windows. I get this error with any DVD i try to play.

---

### Post by bhadotia on 2008-07-01
Well if don't have libdvdcss2 , install along with it libxine1 and libxine1-all-plugins  and xine-ui to play the dvds. You can also install vlc to play them but it needs a little configuration (sometimes); Xine always works for me.

---

### Post by bhadotia on 2008-07-01
To install those packages go to System>Administration>Synaptic Package Manager .
In window that opens ensure that the boxes beside them are green, if not check them and then click apply in the toolbar to install all of them simultaneously.

I detailed this much because it seemed to me you needed it.

---

### Post by AMC25114 on 2008-07-01
haha ya thx ill give that a shot

---

### Post by bhadotia on 2008-07-01
;-)

---

### Post by AMC25114 on 2008-07-01
ok, well i tried all of that and i still get the same error

---

### Post by bhadotia on 2008-07-01
Please, copy and paste the exact error you are getting and post it here.

---

### Post by AMC25114 on 2008-07-01
An Error Occurred

Could not read from resource

---

### Post by khr on 2008-07-01
I'm having the same problem.
I tried to install all the stuff you mentioned from synaptic, but it had no effect.

---

### Post by bhadotia on 2008-07-01
I think the error means , that there is some internal system problem or shortcoming. 
Is the DVD you are trying to play a UDF volume of the new type (v2.50) . If don't know that right-click on the DVD icon and open the properties window to find out . If so you might need to patch the kernel . But first let us know is this a UDF or an ISO volume.

---

### Post by AMC25114 on 2008-07-01
its a udf file

---

### Post by bhadotia on 2008-07-01
Yup, knew it look here [http://ubuntuforums.org/showthread.php?t=775775&highlight=udf+bhadotia](http://ubuntuforums.org/showthread.php?t=775775&highlight=udf+bhadotia).
Go to the last post on this page.
If you need help , post back.

---

### Post by mc4man on 2008-07-01
If these are commercial dvds then they're udf1.02 which is supported. 
Why don't you open vlc from the terminal, then file -> open disc. In the pop up -  note the default device and click play. Post error messages (if any)

---

### Post by AMC25114 on 2008-07-01
It all works now i added the Media Ubuntu Respitory that a friend gave me and it found new updates that once installed made it work.

---

### Post by bhadotia on 2008-07-01
What you mean you did not even have the medibuntu repos and were trying to play the disc? LOL
I thought you said a friend added all the extra stuff for you .
Well  here is another link to help you with the multimedia in ubuntu.[http://ubuntuforums.org/showthread.php?t=766683&highlight=comprehensive+multimedia](http://ubuntuforums.org/showthread.php?t=766683&highlight=comprehensive+multimedia)

---

### Post by AMC25114 on 2008-07-01
In his defense he is brain dead most of the time :p Anyways thanks for your help its much appreciated.

---

