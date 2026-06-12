---
title: "the shut down problem"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-12-01
i am using hardy heron.when i click on shut down button in my panel,the system instead of presenting me with choices as to whether the system should restart,shut-down,log out,etc.,the system simply hangs up,everything gets stuck and i can't do anything.how do i fix this?

---

### Post by cmnorton on 2008-12-01
Right click on the shutdown icon and select Configure Session Manager.

What are the settings?

Also, can you shutdown properly from a x-term?

---

### Post by linux_tech on 2008-12-01
Try turning off your network connection before you turn off your PC. The icon is in right corner of your screen, right click and uncheck the box “Enable Networking”.  Then try shutdown button.

---

### Post by stonecoldjha on 2008-12-01
the same thing happens even on disabling networking.

---

### Post by linux_tech on 2008-12-01
Can the computer shutdown by terminal?
```
 sudo shutdown -h
```

Is this a laptop or desktop?  what is system config? 

It likely could be how it handles power management so
try changing the power management settings 
System-->Preferences-->Sessions-->Power Manager
Is it enabled or disabled?
What is selection for Action (General tab), "when power button is pressed"? Try "ask me" or "shutdown"

---

### Post by jakupl on 2008-12-01
> **linux_tech said:**
> Can the computer shutdown by terminal?
```
 sudo shutdown -h
```

Is this a laptop or desktop?  what is system config? 

It likely could be how it handles power management so
try changing the power management settings 
System-->Preferences-->Sessions-->Power Manager
Is it enabled or disabled?
What is selection for Action (General tab), "when power button is pressed"? Try "ask me" or "shutdown"

I think that command should be:

```
sudo shutdown -P now
```

---

