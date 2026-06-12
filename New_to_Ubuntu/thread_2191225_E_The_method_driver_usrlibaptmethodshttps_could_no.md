---
title: "E: The method driver /usr/lib/apt/methods/https could not be found."
date: 2013-12-01
forum: New to Ubuntu
---

### Post by dryden-parker on 2013-12-01
Hey everyone! I realize this topic has already been posted several times and I have checked most that have been relevant to my problem and still no success so I need help!

I am a complete ubuntu noob running version 13.0.4 on a chromebook, everything worked fine for a couple weeks and then when I tried to install 
'Wine ' I was met with the code ' **Failed to download repository information **check your internet connection ' followed by ' E:The method driver /usr/lib/apt/methods/https could not be found ' Google produced many results, mostly telling me to run the command ' Sudo apt-get update ' then I was met with the same code ' E: The method driver /usr/lib/apt/methods/https could not be found. ' I have tried most of the fixes on google and the forums and none of them have produced any results, I have checked my /etc/apt/sources.list for typos and have come up with nothing. As of now my computer can not update, nor can it install anything from the Software Center. Any help would be extremely appreciated as I am extremely green when it comes to ubuntu, thank you so much :)

---

### Post by daslinkard on 2013-12-02
What happens when you run the following sudo command:
```
sudo apt-get install apt-transport-https
```

---

### Post by dryden-parker on 2013-12-05
This is the code:
$ sudo apt-get install apt-transport-https
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package apt-transport-https

---

### Post by abdrew on 2014-03-01
I'm having the exact same issue on my chrooted chromebook

---

### Post by abdrew on 2014-03-01
[COLOR=#333333][FONT=UbuntuRegular]I figured it out![/FONT][/COLOR]

[LIST=1]
[*]download the file from the link here: "[http://packages.ubuntu.com/precise/amd64/apt-transport-https/download](http://packages.ubuntu.com/precise/amd64/apt-transport-https/download)"

[*]click on the link labeled "security.ubuntu.com/ubuntu" on the webpage (that should download a file)

[*]Then, install that file with the "GDebi Package installer.
(finished)
[/LIST]

---

