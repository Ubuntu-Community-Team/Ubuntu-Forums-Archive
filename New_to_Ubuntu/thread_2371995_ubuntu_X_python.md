---
title: "ubuntu X python"
date: 2017-09-20
forum: New to Ubuntu
---

### Post by sekerka on 2017-09-20
Hello, i'm recently following this article about how to prepare ubuntu laptop for programming in python( [https://www.digitalocean.com/community/tutorials/how-to-install-python-3-and-set-up-a-local-programming-environment-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-python-3-and-set-up-a-local-programming-environment-on-ubuntu-16-04) ). I've followed the instructions and this happend when i wanted to **install pip 9.0.1**:
[LIST]
[*][SIZE=2][FONT=book antiqua]python3 -V [/FONT][/SIZE]
[LIST]
[*]Python 3.6.2
[/LIST]

[*][FONT=book antiqua]sudo apt-get install -y python3-pip[/FONT]
[LIST]
[*]python3-pip is already the newest version(8.1.1-2ubuntu0.4)
[*]0 upgraded, 0 newly installed, 0 to remove and 0 to upgraded
[/LIST]

[*][FONT=book antiqua]pip3 install package_name[/FONT]
[LIST]
[*]Successfully installed package-name-0.1
[*][COLOR=#8b4513][B]You are using pip version 8.1.1, however version 9.0.1 is available.
[/B][/COLOR]
[*][COLOR=#8b4513]**You should consider upgrading via the 'pip install --upgrade pip'**[/COLOR]
[/LIST]

[*][FONT=book antiqua]pip install --upgrade pip[/FONT]
[LIST]
[*]**Downloading pip-9.0.1-py2.py33-none-any.whl (1.3mb)**
[*]Installing collected packages:pip
[*]**Succesfully installed pip-8.1.1**
[/LIST]
[/LIST]
Continuing in tutorial mentioned above:
[LIST]
[*]sudo apt-get install build-essential libssl-dev libffi-dev python-dev
[LIST]
[*]0 upgraded ...
[/LIST]

[*]sudo apt-get install -y python3-venv
[LIST]
[*]python3-venv is already the newest version [COLOR=#ff0000](3.5.1-3) [/COLOR]// ?shouldn't this be the same as[COLOR=#ff0000] *python3 -V*[/COLOR][I] ... Python3.6.2
[/I]
[/LIST]
[/LIST]
Continuing the tutorial when seeing this:
[LIST]
[*]mkdir environments
[*]cd environments
[*]python3 -m my_env
[LIST]
[*]/usr/local/bin/python3: No module named my_env.__main__; 'my_env' is a package and cannot be directly executed
[/LIST]
[/LIST]
**I'm trying this for the second time, i even restarted the laptop. [CENTER]Can someone help me install python, especially with option to run turtle commands in it?
[/CENTER]

---

### Post by Topsiho on 2017-09-20
It's not clear to me what you are trying to achieve.

After install you **already have what you need**: python2 and also python3.
All you need to do is in the terminal, after the $ prompt (if you can type you can use the terminal):

python

which starts python version 2, which will be obsolete before long, or you type:

python3

which starts python version 3. The new version, which is way better.

AFAIK you already can use the turtle too, but I'm not sure about that. Just google for that if necessary.

You should consult a good book for python, for python3 a good book is (to my opinion):

thinkpython2.pdf

The 2 in the title is for second edition!, not python2. It's a free download, just google for it.

If you hate the terminal, you could also try to program python within IDLE which is a graphical program.
(which I don't like, have to learn using the graphical program too, and if I change to another graphical program I need to learn to use that.
Using the terminal is knowledge that lasts.

Topsiho

---

