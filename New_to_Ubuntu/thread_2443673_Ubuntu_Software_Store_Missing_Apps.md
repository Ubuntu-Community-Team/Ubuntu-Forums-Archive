---
title: "Ubuntu Software Store Missing Apps?"
date: 2020-05-18
forum: New to Ubuntu
---

### Post by jay56547 on 2020-05-18
So this is how the store looks: 
[https://imgur.com/a/uJY9zgV](https://imgur.com/a/uJY9zgV)
Which is fine, but when I click a category, this is all the apps that show up: (this is editors pick, happens to all)
[https://imgur.com/a/B1DQDWe](https://imgur.com/a/B1DQDWe)
There's supposed to be more, I've tried reinstalling gnome software and that doesn't work 
I'm using Ubuntu 20.04 (external live persistence hard drive, "Try Ubuntu" selected) 


Also problems with chrome remote desktop: 
[https://imgur.com/a/879urQa](https://imgur.com/a/879urQa) (I click turn on, set up a name and password, and this shows up)

---

### Post by daniewicz on 2020-05-18
Install the Synaptic Package manager and use it to install software. IMHO a better choice.

---

### Post by jay56547 on 2020-05-18
Dumb question, is it like the ubuntu store where it's a graphical interface?

---

### Post by Perfect Storm on 2020-05-19
> **jay56547 said:**
> Dumb question, is it like the ubuntu store where it's a graphical interface?

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=285923&stc=1&d=1589871603[/IMG]

---

### Post by ActionParsnip on 2020-05-19
If you run:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

Does it work OK?

---

### Post by jay56547 on 2020-05-19
Yes. Also I had to reinstall all of Linux cause it out me in an infinite log in loop. Now "editors pick" is the only thing showing up. (I did minimal install)

Edit, I only see a square with 3 dots in it under categories, installed tab also shows nothing

---

### Post by Dennis N on 2020-05-19
If the icon for the application is named "Ubuntu Software" it's a snap package. You might have better luck with the Ubuntu repository package instead (named "Software").

First, remove "Ubuntu Software" using your terminal:
```
snap remove snap-store
```
Then install "Software" from the Ubuntu repository using your terminal:
```
sudo apt install gnome-software
```

The icon is labeled "Software".

---

### Post by jay56547 on 2020-05-19
What's the point of a snap package


Also everything works now. But I still need help with chrome remote desktop. Now it doesn't even give the option to turn it on. And chrome keeps asking for a default keyring. Idk what that is

---

### Post by monkeybrain20122 on 2020-05-20
> **jay56547 said:**
> What's the point of a snap package


snap is supposed to provide up to date software while the repo version (from synaptic) may get old after a while. Personally I prefer to use ppa or compile from source to keep up to date. The snap store also provides some proprietary software not available in the normal repo.

---

