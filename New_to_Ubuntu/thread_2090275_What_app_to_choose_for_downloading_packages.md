---
title: "What app to choose for downloading packages?"
date: 2012-12-01
forum: New to Ubuntu
---

### Post by stevetoops on 2012-12-01
I have Ubuntu installed on several computers. Initially, I installed gparted directly from Ubuntu Software Center. On the second machine, the software center assumed that the app was already installed, and only allowed me to remove it. So I removed what it thought was there, and then successfully installed it on the second machine. When I got to the third machine, gparted was no longer listed anywhere in the software center.

Now I'm trying to download from [https://apps.ubuntu.com/cat/applications/gparted/](https://apps.ubuntu.com/cat/applications/gparted/), but the site wants me to choose an application to open the download:
"This link needs to opened with an application."
What app should I choose?

thanks,
steve

---

### Post by Frogs Hair on 2012-12-01
Chrome found the application for me which is the software center.

---

### Post by Bartender on 2012-12-01
I don't get it.  What does it matter if you've installed gparted to the first or second PC?  Are they all on a network?  And you think that somehow the repositories are confusing one PC with another?

Have you tried installing Synaptic Package manager and using that instead of Software Center?  Numerous folks have mentioned that Synaptic is more reliable, and faster, than Software Ctr.

It only makes sense that the website would instruct you to use an app for downloading.  Because of dependencies, you can't just d/l something from the internet like you can with Windows and .exe

---

### Post by DukeOfMixture on 2012-12-01
You should try Synaptic and enter *gparted* in the search.

Or from the terminal:

```
sudo apt-get install gparted
```

---

### Post by Cheesemill on 2012-12-02
> **Bartender said:**
> It only makes sense that the website would instruct you to use an app for downloading.  Because of dependencies, you can't just d/l something from the internet like you can with Windows and .exe

The website wasn't asking what application to download the file with, it was asking what application to open the link with.

This is because the site was making use of apt URLs, these are in the form [apt://gparted](apt://gparted).
When you click on one it basically opens the software centre (or gdebi, or whichever app you've chosen) at the correct page for the named package. Try it and see.

I sometimes use these in posts when instructing someone to install a specific package.

---

### Post by stevetoops on 2012-12-03
Thanks to everyone for your advice. 

The final solution was that the server specified in /etc/apt/sources.list does not provide a reliable connection. I had problems downloading from it several weeks ago, but forgot about it. I'll see if I can add other servers to this list. 

I got it downloaded tonight just by entering "sudo apt-get install gparted". The same command that kept failing for the past several days. Next time I know to test the connection by pinging it.

Also, thanks for the reference to Synaptic Package manager. I'll look into this as well.

For now, that's an end to the query. I might have missed clicking on the right button to indicate query resolution status. This is my first forum query. Hope everyone will be willing to help again. 

thanks,
steve

---

### Post by oldos2er on 2012-12-03
> **stevetoops said:**
> I might have missed clicking on the right button to indicate query resolution status. 

Under the Thread Tools drop down menu at the top of the thread, tick 'Solved'.

---

