---
title: "Failed To Install HandBrake"
date: 2013-02-18
forum: New to Ubuntu
---

### Post by Melita on 2013-02-18
I tried to install the file converter HandBrake but failed. Please see the screen shot of Terminal that is attached. What can I do about this?

Thank you.

---

### Post by coldraven on 2013-02-18
I just looked at the package in Synaptic, it seems that there is only a 32bit version.
You could use the Software centre or try this --
```
sudo apt-get install handbrake-gtk:i386
```

---

### Post by Melita on 2013-02-19
> **coldraven said:**
> I just looked at the package in Synaptic, it seems that there is only a 32bit version.
You could use the Software centre or try this --
```
sudo apt-get install handbrake-gtk:i386
```

 I am using Ubuntu 12.04 Is this compatible with that?  Regards.

---

### Post by coldraven on 2013-02-19
> **Melita said:**
> I am using Ubuntu 12.04 Is this compatible with that?  Regards.
Sorry, I should have checked before I posted.

Go to the Handbrake downloads page and click on the link for Ubuntu
[http://handbrake.fr/downloads.php](http://handbrake.fr/downloads.php)


Then add the PPA to your software sources 
```
sudo add-apt-repository deb [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu) precise main 
sudo apt-get update
sudo apt-get install handbrake
```I hope that works this time ;)


Sorry again, it is too early in the morning for my brain to work :(
I have to go out now, hopefully someone will help.

---

