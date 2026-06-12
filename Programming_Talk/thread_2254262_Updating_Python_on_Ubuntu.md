---
title: "Updating Python on Ubuntu?"
date: 2014-11-26
forum: Programming Talk
---

### Post by baudrillard on 2014-11-26
I want to teach myself python and just recently started using Ubuntu as my main OS recently.

I just found out that Ubuntu has Python pre-installed on some level because it is largely coded in Python. However, as a result, this apparently makes it a special exception when it comes to updating, given that Python 2.7(the current version my pc has) is much different from Python 3.4.

So my question is as follows: Is it possible to install Python 3.4 seperately, and then use that version of Python in a compiler of my choice (Preferably Pycharm)?

If so, how could I do it? 

Thank you all for your time, I'm really new to this.

---

### Post by baudrillard on 2014-11-26
Update:

I managed to figure out how to install (I believe) python 3.4.1, but I have no clue how to specifically access it, or make it show in unity search. What I did was follow the directions in the extracted files (obvious, I know), but I'm still kind of left clueless as to how I use this version of python over the preinstalled version, and then how do I tell pycharm to use it?

---

### Post by steeldriver on 2014-11-26
What Ubuntu version are you using?

Typically Python 2.xand Python 3.y can coexist, with the latter being invoked explicitly as "python3". On Ubuntu 14.04 the default version of "python3" should already be 3.4 I think - there should be no need to manually install anything.

---

### Post by baudrillard on 2014-11-26
I'm running Ubuntu 14.04, and yeah, I'm starting to catch onto that. I realized I can evoke Python3 by just typing that out in terminal, which will give me access to it rather than the python the system was coded in.

Lol, I hope installing python 3.4.1 won't mess anything up then.

Any idea how to make sure that's the python version I use for a compiler tho? I'm still confused in regards to that.

---

### Post by baudrillard on 2014-11-26
Also, if anyone knows how to install pycharm in of itself, I'd appreciate a point in the right direction. No apt-get I've tried works so far, and I don't know how to run the shell files provided in the tar.gz file from the official website.

---

### Post by baudrillard on 2014-11-26
Answered my own problem. For anyone who wants to know how to install Pycharm on Ubuntu 14.04, go [here]("http://linuxg.net/how-to-install-pycharm-3-4-on-ubuntu-14-04-linux-mint-17-pinguy-os-14-04-and-other-ubuntu-14-04-derivatives/").

Additionally, using Pycharm, you're capable of choosing which version of Python to use with the compiler, so you're free to install python 3.4.1 and still be able to use Python 2.7, etc.

---

### Post by flaymond on 2014-11-27
You can open the Python 3 by typing this into your Terminal -

```
python3
``` * without any space



If you want to use Python 3 Interpreter (text-editor like, but rich features and simple)


Open Ubuntu Software Center > Type Python 3 > Install > Done.


or If you want use Python IDE (contain everythig you need, apparently)

Open Ubuntu Software Center > Type Ninja IDE > Install >Done.


** Type this into your Python Interpreter"

```
print ("Welcome to the forum\r\nThanks for choosing Ubuntu!")
```

---

