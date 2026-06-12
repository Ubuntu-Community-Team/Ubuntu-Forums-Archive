---
title: "Uninstalling a sudo get-apt install?"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by moose4204l on 2008-05-19
quick question, i just sudo apt-get install sox but now i want to unistall it because it wasnt what i was looking for.

also, how do i play a .wav or .mpg from the command terminal or do i need to downlaod some tool for it?

thanks

the moose

---

### Post by Cypher on 2008-05-19
Use
```

sudo apt-get remove sox

```
to remove the application.

Install mplayer with
```

sudo apt-get install mplayer

```
for a command line util to play audio/video files..

---

### Post by stchman on 2008-05-19
> **moose4204l said:**
> quick question, i just sudo apt-get install sox but now i want to unistall it because it wasnt what i was looking for.

also, how do i play a .wav or .mpg from the command terminal or do i need to downlaod some tool for it?

thanks

the moose

Use the auotremove command.

```
sudo apt-get autoremove sox
```

Autoremove removes unused dependencies.

---

### Post by moose4204l on 2008-05-19
thank you!

---

### Post by Skeet on 2008-05-19
VLC (Video LAN Client)

---

### Post by Skeet on 2008-05-19
Whoops, clicked submit before I finished.

```
sudo apt-get install vlc
```

VLC plays everything you throw at it.

---

### Post by Paqman on 2008-05-19
You can also use Synaptic to remove anything installed through apt-get.

---

### Post by vikikamath on 2012-05-02
> **stchman said:**
> Use the auotremove command.

```
sudo apt-get autoremove sox
```

Autoremove removes unused dependencies.

Thanks worked for me!

---

### Post by coffeecat on 2012-05-02
Old thread - closed.

---

