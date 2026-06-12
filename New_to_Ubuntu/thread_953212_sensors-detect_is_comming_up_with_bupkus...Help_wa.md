---
title: "sensors-detect is comming up with bupkus...Help want to monitor CPU and MoBo Temps!"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by The MAX on 2008-10-19
So I've gone through a couple of different ways to instal lm-sensros to get my vidard, cpu, and mobo temps. and so far have only been able to get my Nvidia 8800GT's temp and thats it.

this is what I've done.
```
sudo apt-get install lm-sensors

```
made the mkdev.sh script
```
sudo ./mkdev.sh
```
that returns
```
/dev/i2c-0
mknod: `/dev/i2c-0': File exists

```
have no idea what that means.
ran sensors detect and its final return is
```
#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# Chip drivers
# no driver for Analog Devices ADT7473 yet
#----cut here----

```

so basically it just wants to add comments to my file...

anyways...done a bit of other fiddling but nothing is working.

Running 8.04 and have a P5Q-Pro and an E8400 if that helps...

---

### Post by Elfy on 2008-10-20
Does it not say similar to this, with your adapter drivers. Say yes 

> I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
w83627hf
#----cut here----

Do you want to add these lines automatically? (yes/NO)


Once you've let it add the lines to the /etc/modules reboot and they should be there for you.

---

### Post by The MAX on 2008-10-20
No it doesn't have anything like that.
It says (and I've thrown in the cpu section as well where it shows no cpu sensor detected)
```

Some CPUs or memory controllers may also contain embedded sensors.
Do you want to scan for them? (YES/no): yes
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `to-be-written' (should be inserted):
  Detects correctly:
  * Bus `NVIDIA i2c adapter '
    Busdriver `UNKNOWN', I2C address 0x2e
    Chip `Analog Devices ADT7473' (confidence: 5)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# Chip drivers
# no driver for Analog Devices ADT7473 yet
#----cut here----

Do you want to add these lines automatically? (yes/NO)

```

the code it wants to add is just comments. It doesn't detect a CPU or mobo sensor, but I know they are there cause I monitor the temps in windows.

---

### Post by Elfy on 2008-10-20
Sorry didn't see that, apparently it is supported - the lm-sensors shows it, though not sure about the version in hardy though. 

[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices)
[http://www.lm-sensors.org/wiki/Download](http://www.lm-sensors.org/wiki/Download)
There is a wizard - [http://www.lm-sensors.org/wiki/iwizard/1](http://www.lm-sensors.org/wiki/iwizard/1)

---

