---
title: "Installing GSconnect on Ubuntu 18.04"
date: 2020-04-06
forum: New to Ubuntu
---

### Post by navido on 2020-04-06
Hi guys. I really need help. I come from Windows so i am new to Linux.

I am trying to install the GSConnect from zip

[https://github.com/andyholmes/gnome-shell-extension-gsconnect/wiki/Installation#install-from-zip](https://github.com/andyholmes/gnome-shell-extension-gsconnect/wiki/Installation#install-from-zip)

I use the 3.28 gnome version. So i downll0aded the V28.

I have read the installation, but Im not sure if i did it right.but this is what i have done through the GUI 


I created the folder 


[email]gsconnect@andyholmes.github.io[/email] in 


/usr/local/share/gnome-shell/extensions


And unzipped the V28 version into that folder.


So that it looks like this


[https://ibb.co/9y990Yj](https://ibb.co/9y990Yj)


The zip file still is there though as you can see but i dont hink it makes any different


Then i ran the command to restart the gnomeshell


DISPLAY=:0 gnome-shell -r &


I get a bunch of errors. 

Before i paste the error. Is this correct?

Appreciate help.

---

### Post by CelticWarrior on 2020-04-06
Why don't you try installing it with Gnome extensions, the [recommended method]("https://www.omgubuntu.co.uk/2019/09/gsconnect-android-media-controls-update")?

---

### Post by navido on 2020-04-06
Not sure what you mean.

You mean from the ubuntu sofware gui? Just search for gsconnect and download it?

---

### Post by CelticWarrior on 2020-04-06
What I meant was entirely explained in the linked OMGUbuntu! article.

---

### Post by tea for one on 2020-04-06
> **navido said:**
> Not sure what you mean.

You mean from the ubuntu sofware gui? Just search for gsconnect and download it?

Try this:-

You first of all need a package to integrate with the extensions website.
Open a terminal and enter

```
sudo apt install chrome-gnome-shell
```

Assuming the package is installed correctly, then using Firefox, navigate to 

[https://extensions.gnome.org/extension/1319/gsconnect/](https://extensions.gnome.org/extension/1319/gsconnect/)

Download from the official site.

---

### Post by Dennis N on 2020-04-06
> You mean from the ubuntu sofware gui? Just search for gsconnect and download it? 
Correct, except that instead of downloading, you just click the 'Install' button (see screenshot) and Ubuntu Software does the rest. If you use Ubuntu Software to install it, you don't need to install chrome-gnome-shell.

---

### Post by navido on 2020-04-06
YES..thanks..i managd to install it throught the GUI and it runs perfect now

---

### Post by tea for one on 2020-04-07
> **navido said:**
> YES..thanks..i managd to install it throught the GUI and it runs perfect now

Splendid - please mark the thread as solved so that others can use the solution in the future.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

