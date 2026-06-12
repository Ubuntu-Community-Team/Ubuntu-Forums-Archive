---
title: "Why can't I add a repository"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by SIStem_shock on 2008-07-17
I tried to post this hours ago but can't find it even with search, so I'm very sorry if it ends up being a double post. I want to add another repository to software services, but when I try to do that the Add Source button is greyed out. What am I doing wrong?

---

### Post by hyper_ch on 2008-07-17
```

gksudo gedit /etc/apt/sources.list

```

---

### Post by oldos2er on 2008-07-17
> **SIStem_shock said:**
> I tried to post this hours ago but can't find it even with search, so I'm very sorry if it ends up being a double post. I want to add another repository to software services, but when I try to do that the Add Source button is greyed out. What am I doing wrong?

 The repository location must be preceded by "deb" or "deb-src."

---

### Post by SIStem_shock on 2008-07-17
I did try preceding it with deb before I posted but it didn't work. Does it matter if it is deb or deb-src? I'll try using the terminal. Thanks!

---

### Post by SunnyRabbiera on 2008-07-17
> **SIStem_shock said:**
> I did try preceding it with deb before I posted but it didn't work. Does it matter if it is deb or deb-src? I'll try using the terminal. Thanks!

yes as deb and deb src are different... deb is regular debian packages and deb src are source packages.
are you getting errors might I ask by typing in a terminal apt-get update

---

### Post by SIStem_shock on 2008-07-17
> **SunnyRabbiera said:**
> yes as deb and deb src are different... deb is regular debian packages and deb src are source packages.
are you getting errors might I ask by typing in a terminal apt-get update

Hmm, I'm not sure which one I need then. I was only given the URL and I don't have it handy on this computer right now. I haven't tried apt-get update though I have used the update in synaptic without errors. That computer is tied up with a big download right now, but I'll try it as soon as it is free.

---

### Post by Vivaldi Gloria on 2008-07-17
> **SIStem_shock said:**
> I tried to post this hours ago but can't find it even with search, so I'm very sorry if it ends up being a double post. I want to add another repository to software services, but when I try to do that the Add Source button is greyed out. What am I doing wrong?

If you tell which repo or program you are trying to add then we can give more spesific help.

If it is a deb file then you can download and double click on it.

---

### Post by SIStem_shock on 2008-07-17
> **Vivaldi Gloria said:**
> If you tell which repo or program you are trying to add then we can give more spesific help.

If it is a deb file then you can download and double click on it.


Yeah, I know. Sorry. I didn't have that info on this computer and couldn't get to the other one at the time to find out. This is it, though - 
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
or at least, that is the link I was given.

---

### Post by Vivaldi Gloria on 2008-07-17
> **SIStem_shock said:**
> Yeah, I know. Sorry. I didn't have that info on this computer and couldn't get to the other one at the time to find out. This is it, though - 
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
or at least, that is the link I was given.

It's explained here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Open a terminal from applications > access. menu and give the commands in that page. If you are using ubuntu 8.04 then the commands are as follows:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by SIStem_shock on 2008-07-21
> **Vivaldi Gloria said:**
> It's explained here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Open a terminal from applications > access. menu and give the commands in that page. If you are using ubuntu 8.04 then the commands are as follows:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```


Thanks. Can I ask why it has to be done in the terminal? Why can't I ever get the GUI interface to do what I want?

---

### Post by Tomosaur on 2008-07-21
> **SIStem_shock said:**
> Thanks. Can I ask why it has to be done in the terminal? Why can't I ever get the GUI interface to do what I want?

Well, you could use the GUI, but it's a lot easier to help people with a few simple commands than it is to walk somebody through a GUI, telling them which buttons to click etc :)

---

### Post by SIStem_shock on 2008-07-21
> **Tomosaur said:**
> Well, you could use the GUI, but it's a lot easier to help people with a few simple commands than it is to walk somebody through a GUI, telling them which buttons to click etc :)

But I know where you are supposed to add it in the GUI, I just don't know why the Add button is always grayed out and what to do about that. I don't want to have to use the terminal for everything because I can't remember the commands. Some things should just be easier than that.

---

