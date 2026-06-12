---
title: "Dont know how to install tar.gz python file"
date: 2014-05-02
forum: New to Ubuntu
---

### Post by theway645 on 2014-05-02
Hello I am an absolute beginner to linux and and want to install a tar.gz file with with pythons files inside but have to idea how to do it. I ve looked at tutorials but they are all different and apparently anything can be inside a tar.gz file so you have to adapt accordingly. Here is the content of the tar file unarchived : 

emmanuel@emmanuel-MS-7850:~/Downloads/KindleComicConverter_linux_4.0.2$ ls
kcc  kcc-c2e  kcc-c2p  kcc.png  LICENSE.txt

There is no readme file nor config file. Also if you have a bitcoin wallet I might give a tip if it is a good answer with detailed explanation.

---

### Post by claracc on 2014-05-02
I have found this web page: [https://github.com/ciromattia/kcc](https://github.com/ciromattia/kcc) from which I supposse you have downloaded the software. 

It seems they are a set of phyton scripts in order to do the format conversion. 

As you can see in the link, you need to have some dependencies: See the paragraph "For running from source".

I would suggest you ask for help in the places addressed by the web page, in the part Issues/New features/Donations:

"If you have general questions about usage, feedback etc. please post it here. If you have some technical problems using KCC please file an issue here. If you can fix an open issue, fork & make a pull request.
If you want more chances an issue is fixes or your wanted feature added, consider placing a bounty! "

Or wait for the advice of python specialised members in the forum.

---

### Post by 3rdalbum on 2014-05-02
It looks like you just run the programs directly from that directory, or you can put them into /usr/local/bin if you want other users to be able to access them.

They are probably command-line only. To find out how to use them, drag the 'kcc' file to the terminal window and hit Enter.

You probably run them by dragging the kcc program to the terminal, and then the file you want to convert, and then press Enter.

I have a Bitcoin wallet, if my answer is helpful send me a PM.

---

### Post by sammykur on 2014-05-02
The file is executable ,just cd to the directory and run```
 ./kcc
```
It will give you and error saying **** not installed

Install this ppa
```
sudo apt-add-repository ppa:ubuntu-sdk-team/ppa
```

[http://packages.ubuntu.com/saucy/python/pyqt5-dev-tools](http://packages.ubuntu.com/saucy/python/pyqt5-dev-tools)
This is a site to download the dependency pyqt5 for the saucy and other  versions ,which i am not running(i couldnt find it for precise)
if not google pyqt5(or other errors) and the version you are running.
keep trying to run the file and look in synaptic and the Ubuntu software center firstto install the dependencies it give you errors on.

It looks like this thing has a ton of dependencies so you might be at it a while.

hope this helped, it should point you in the right direction.

---

### Post by theway645 on 2014-05-03
When I enter ./kcc on terminal I receive this : 

emmanuel@emmanuel-MS-7850:~/Downloads/KindleComicConverter_linux_4.0.2$ ./kcc
ERROR: PyQt5, python-slugify, Pillow 2.3.0+ is not installed!

---

### Post by oldos2er on 2014-05-03
According to the [README.md]("https://github.com/ciromattia/kcc/blob/master/README.md") you need 

[LIST]
[*]Python 3.3+
[*] [PyQt5]("http://www.riverbankcomputing.co.uk/software/pyqt/download5") 5.2.0+
[*] [Pillow]("http://pypi.python.org/pypi/Pillow/") 2.3.0+
[*] [psutil]("https://pypi.python.org/pypi/psutil") 2.0+
[*][python-slugify]("http://pypi.python.org/pypi/python-slugify")
[/LIST]

There's also a command given to install the dependencies on "Debian based distributions."

---

### Post by theway645 on 2014-05-04
Thank you, its working now! My source didnt have any readme.

---

### Post by claracc on 2014-05-04
Please, mark the thread as solved with thread tools button in the top right of the page.

---

