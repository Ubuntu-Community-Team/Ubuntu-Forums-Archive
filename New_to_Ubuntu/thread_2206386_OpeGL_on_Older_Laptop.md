---
title: "OpeGL on Older Laptop"
date: 2014-02-18
forum: New to Ubuntu
---

### Post by lance-uppercut on 2014-02-18
Hey all,

I am new to linux and I am having a problem playing Dota 2.

The computer is a Dell Vostro 1000 laptop running the most recent version of Xubuntu.

I have downloaded steam and Dota 2 but, when I click to play I get an OpenGL error. It says I might need to update my video card drivers.

Any advice is appreciated.

Thanks.

---

### Post by monkeybrain20122 on 2014-02-18
What is your opengl version?

In the terminal type
```
sudo apt-get install mesa-utils
```
Then when done
```
glxinfo | grep OpenGL
```

---

