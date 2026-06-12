---
title: "Desktop Effects Help"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by pepaman on 2008-08-12
Hi 
I'm trying to get me Desktop Effects to work
but the problem that i have is. 
When i go to change it it wont let me( comes up with an error)
I think its something to do with my nvidia drivers. 
I Have a 9500 gs card. cant figure out how to get into the nvidia settings to?
Help

---

### Post by tuxxy on 2008-08-12
Did you install the nvidia drivers at system > admin > hardware drivers?

If so you need to run nvidia-settings to configure, type this into terminal

```
nvidia-settings

```
If its not installed yet, search for it and install through synaptic or type in terminal

```
sudo apt-get install nvidia-settings
```

---

### Post by pepaman on 2008-08-12
came up with couldnt find pakage

---

### Post by glennric on 2008-08-12
You need to make sure you have the universe repositories enabled.  To do this go to System->Administration->Software Sources and under the "Ubuntu Software" tab make sure that "Community-maintained Open Source software (universe)" is checked.  Then do 
```
sudo apt-get update
sudo apt-get install nvidia-settings
```

---

