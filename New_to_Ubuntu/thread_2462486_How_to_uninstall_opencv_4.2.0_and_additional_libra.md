---
title: "How to uninstall opencv 4.2.0 and additional libraries (Ubuntu 20.04)"
date: 2021-05-21
forum: New to Ubuntu
---

### Post by ziadamr22 on 2021-05-21
I'm quite new to Ubuntu and I just installed opencv and some additional libraries using 

sudo apt update                              
sudo apt install libopencv-dev python3-opencv                                                                                                                                                                                                                                                                                                             
sudo apt install libjpeg-dev libpng-dev libtiff-dev

I'm now trying to downgrade from opencv 4.2.0 to opencv 4.1.1.26.

Can anyone help me with this?

---

### Post by guiverc on 2021-05-21
Also asked at [https://askubuntu.com/questions/1339866/uninstall-opencv-4-2-0-and-its-libraries](https://askubuntu.com/questions/1339866/uninstall-opencv-4-2-0-and-its-libraries)

---

### Post by ziadamr22 on 2021-05-21
I'm the one who asked that question as well.

---

### Post by monkeybrain20122 on 2021-05-21
So your question from the link is not how to install opencv-4.1.1.26 but how to cleanly uninstall what you have installed? That is easy, in the terminal type
```
sudo apt purge python3-opencv
sudo apt remove  libopencv-dev  libjpeg-dev libpng-dev libtiff-dev
sudo apt autoremove
```

You can use pip to install opencv as said in the link, but instead of using system python for development I would suggest setting up a separate python environment using something like [anaconda]("https://www.anaconda.com/products/individual").  That way you can upgrade or downgrade modules without affecting the systems and system updates won't interfere with your development environment. In the end of installing anaconda it will ask permission to alter your .bashrc. It will prepend the path to anaconda's bin to your $PATH, instead you should append it in the end so it won't mess up your system.

---

### Post by ziadamr22 on 2021-05-22
Thank you so much for your help. If possible, can you please give me an idea how to create a virtual environment and install packages in that environment? Also, can you tell me what you meant about Anaconda prepending the path to Anaconda's bin?

---

### Post by monkeybrain20122 on 2021-05-22
See this[ link]("http://ryan-leung.github.io/PHYS4650_Python_Tutorial/installing-on-linux.html"), but instead of "/home/XXXXX/anacondaX/bin:$PATH" in .bashrc, change it to '$PATH:/home/XXXXX/anacondaX/bin". This way the system can find anaconda's python but it won't override system's version when you are not using anaconda.

I don't use virtualenv, but there are many instructions online. Also you may want to take a look at my posts [here]("https://ubuntuforums.org/showthread.php?t=2444887&p=13963327#post13963327") and [here]("https://ubuntuforums.org/showthread.php?t=2449947").

---

