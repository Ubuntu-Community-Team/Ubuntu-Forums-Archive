---
title: "no view of hardware drivers"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by danny138 on 2008-08-01
Hello, I read a forum post that led me to definetly think that hardware devices and even more importantly drivers should be shown from the Hardy desktop. This isn't the case in " Hardware Drivers ". Am I missing an installation from add/remove or Synaptic. I'm new and am not very comfortable with Terminal yet. Thanks for any help, danny

---

### Post by phidia on 2008-08-01
What hardware exactly are you needing drivers for? 
Hardware that you would configure with a initial windows install is already done for you with linux. Exceptions would be unsupported wireless cards and proprietary video drivers. There is a menu selection from the System > Administration menu for enabling some drivers.

---

### Post by danny138 on 2008-08-01
I don't need any drivers, thats not what I'm getting at. In order to know what hardware is on the computer as well as installed drivers it needs to be visable. I briefly had Ubuntu 6 installed and in that version all hardware/drivers were listed in a hardware manager. What if one was to need to change or update or do anything regarding drivers, at my current level I have no resources to access this information. If none of this makes any sense then perhaps it's just that I'm so unfamiliar with this OS but I want to understand, Thanks

---

### Post by phidia on 2008-08-01
I'm using Intrepid Ibex (testing) right now but if you check your System> Administration menu there is a selection there I believe that provides some of that. 

Most system drivers are in the linux kernel so there isn't as much of a need for what you're asking. That is most of the drivers in the kernel will be updated using update manager. The exceptions to that are as I noted before.

For general System Administration you might want to [check this]("https://help.ubuntu.com/community/SystemAdministration") out.

---

### Post by danny138 on 2008-08-01
Thanks for the info. I was reading the Begginer to Pro book it occured to me that they called it "Device Manager" imagine that! Went to Synaptic and there it was. I guess I like to dig into things at times, maybe I'm just wierd , Thanks, danny

---

### Post by AndrewTheArt on 2008-08-01
I think you're looking for something like gnome-device-manager. For some reason the Device Manager (gnome-device-manager) isn't included by default in Hardy.

```
sudo apt-get install gnome-device-manager
```

Now look in Applications -> System Tools and find the entry "Device Manager".

Alternatively, run it from the command line - 

```
gnome-device-manager&
```

---

