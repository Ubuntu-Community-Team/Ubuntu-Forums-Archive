---
title: "[SOLVED] 3 compiz help"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by puleo1333774 on 2008-10-01
1.how can i get the flying windows in compiz?

2.the atlantis cube plug in

3.how to change the background of the cube into a picture?
because i only able to change color but not insert a picture 

thank you for your help

---

### Post by vantsochev on 2008-10-01
check in here:

[http://wiki.compiz-fusion.org/CompizFusionPlugins](http://wiki.compiz-fusion.org/CompizFusionPlugins)

:D

---

### Post by puleo1333774 on 2008-10-01
> **vantsochev said:**
> check in here:

[http://wiki.compiz-fusion.org/CompizFusionPlugins](http://wiki.compiz-fusion.org/CompizFusionPlugins)

:D

im not familiar of what command to use to install it sorry:(

---

### Post by vantsochev on 2008-10-01
try this:

```
sudo apt-get install compizconfig-settings-manager
```

and 

```
sudo apt-get install emerald
```

then press Alt+F2 and type “ccsm“

;)

---

### Post by puleo1333774 on 2008-10-01
> **vantsochev said:**
> try this:

```
sudo apt-get install compizconfig-settings-manager
```

and 

```
sudo apt-get install emerald
```

then press Alt+F2 and type “ccsm“

;)

i didnt get the flying windows effect nothing happens, i think i need to update my compiz, how will i do that to get the latest plugins???

---

### Post by vantsochev on 2008-10-01
The option is called "Wobbly Windows" in compiz settings.

press Alt + F2 type "compiz" and you will be able to find it...
;)

---

### Post by puleo1333774 on 2008-10-01
> **vantsochev said:**
> The option is called "Wobbly Windows" in compiz settings.

press Alt + F2 type "compiz" and you will be able to find it...
;)

how to install compiz fusion???

---

### Post by Terl on 2008-10-01
Go here for directions:  [http://ubuntuforums.org/showthread.php?t=809695 ]("http://ubuntuforums.org/showthread.php?t=809695")

---

### Post by vantsochev on 2008-10-01
open terminal and type:

```
sudo apt-get -y remove compiz-core desktop-effects
```

after that go to System -> Administration -> Software Sources, click on the second tab (Third-Party Software), then click on the "Add" button and paste the following code:

```
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
```

Click the "Add Source" button after you pasted the above code and do the same for the following code:

```
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```

In the terminal window, type:

```
wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg
```

```
sudo apt-key add DD800CD9.gpg
```

Now click the "Close" button on the Software Sources window and you will be asked if you want to reload the information about available software, so click the "Reload" button and wait for the window to disappear.

Copy/Paste the following lines in the terminal window:

```
sudo apt-get update

sudo apt-get -y upgrade
```

In case u are using gnome:

```
sudo apt-get -y install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf
```

For KDE:

```
sudo apt-get -y install compiz compiz-kde compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-kconfig
```

Now, if everything was correctly installed and you didn't encounter errors, press ALT F2 and type:

```
compiz --replace
```

thats it ;)

---

### Post by puleo1333774 on 2008-10-01
> **vantsochev said:**
> open terminal and type:

```
sudo apt-get -y remove compiz-core desktop-effects
```

after that go to System -> Administration -> Software Sources, click on the second tab (Third-Party Software), then click on the "Add" button and paste the following code:

```
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
```

Click the "Add Source" button after you pasted the above code and do the same for the following code:

```
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```

In the terminal window, type:

```
wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg
```

```
sudo apt-key add DD800CD9.gpg
```

Now click the "Close" button on the Software Sources window and you will be asked if you want to reload the information about available software, so click the "Reload" button and wait for the window to disappear.

Copy/Paste the following lines in the terminal window:

```
sudo apt-get update

sudo apt-get -y upgrade
```

In case u are using gnome:

```
sudo apt-get -y install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf
```

For KDE:

```
sudo apt-get -y install compiz compiz-kde compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-kconfig
```

Now, if everything was correctly installed and you didn't encounter errors, press ALT F2 and type:

```
compiz --replace
```

thats it ;)

this error occur when im doing the 2 address in system source
[ATTACH]86917[/ATTACH]

---

### Post by vantsochev on 2008-10-01
type in terminal:

```
sudo gedit /etc/apt/sources.list
```

and add in the source list:

```
deb http://download.tuxfamily.org/3v1deb/ gutsy eyecandy
deb-src http://download.tuxfamily.org/3v1deb/ gutsy eyecandy
```

and save the file then proceed with previous instructions.

;)

---

### Post by puleo1333774 on 2008-10-01
> **vantsochev said:**
> type in terminal:

```
sudo gedit /etc/apt/sources.list
```

and add in the source list:

```
deb http://download.tuxfamily.org/3v1deb/ gutsy eyecandy
deb-src http://download.tuxfamily.org/3v1deb/ gutsy eyecandy
```

and save the file then proceed with previous instructions.

;)

ok thanks

---

