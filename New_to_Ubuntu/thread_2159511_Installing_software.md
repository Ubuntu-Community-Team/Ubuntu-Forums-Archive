---
title: "Installing software"
date: 2013-07-03
forum: New to Ubuntu
---

### Post by lawrencegan on 2013-07-03
Hi all,
I am a totally new to linux, while spending few days getting used to it, that I always see some installation tutorial or videos typing [COLOR="#FF0000"]codes[/COLOR] in some software, I don't know which software that I can use and where to download or already installed? 
such as if I want to install spotify. 
Thanks for you all

---

### Post by newb85 on 2013-07-03
Welcome to Ubuntu and the forums!

It's usually best to install software from repositories, using the built-in package management software on your system. (This includes the Software Center and apt-get from the command line.)  That way, the package manager can automatically update the software, and dependencies can be automatically handled.

Ubuntu comes with default repositories, and you can add more.

Spotify isn't in the Ubuntu repos, but they have their own.  There are good instructions for adding it at [http://www.omgubuntu.co.uk/2013/01/how-to-install-spotify-in-ubuntu-12-04-12-10](http://www.omgubuntu.co.uk/2013/01/how-to-install-spotify-in-ubuntu-12-04-12-10).

It might be more painless to add the repository thus:

```
sudo add-apt-repository 'deb http://repository.spotify.com stable non-free'
sudo apt-get update
```

Addendum:
For future reference, [www.omgubuntu.co.uk]("http://www.omgubuntu.co.uk") and [www.webupd8.org]("http://www.webupd8.org") are great places to look for software not in the main repos.  I find them indispensable.

---

### Post by oldos2er on 2013-07-03
Changed thread title to something more appropriate.

---

### Post by Peptid on 2013-07-03
Welcome,

You can use, as @newb85 says, `software center` to search fro and install programs. Further, you can choose to download .deb files from internet sources, like from skype.com or any other, and then install them using the command 
----code----
sudo dpkg -i `.deb package name`
----code----
through terminal.

---

### Post by newb85 on 2013-07-03
Yes, you can install a manually downloaded .deb file, but you won't automatically receive updates that way. That can also cause dependency difficulties down the road when your system updates. 

In some rare cases (I think Skype is one), installing the .deb will add the repository. But that's not typically the case.

---

### Post by cub on 2013-07-04
Are you using 12.04 or 13.04?

---

### Post by Dozy Van on 2013-07-04
> **lawrencegan said:**
> Hi all,
I am a totally new to linux, while spending few days getting used to it, that I always see some installation tutorial or videos typing [COLOR=#FF0000]codes[/COLOR] in some software, I don't know which software that I can use and where to download or already installed? 
such as if I want to install spotify. 
Thanks for you all

Sorry us Ubuntu people are not the best at explaining for people new to it. Here is my attempt to work through it with you.


That software is known as a Terminal. As you are new to Ubuntu so while writing this I am assuming you are running the standard download from Ubuntu.com. 


Ok so Step 1:

You need to click on the ubuntu logo in the top left of the screen and type in the word Terminal. 



Step 2:

When that appears type the commands that people have posted here. So for exaple to quote newb85. When you have the terminal open type these commands one line at a time. (You can coppy paste but need to use the mouse)


     Code:
     

sudo add-apt-repository 'deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free' 
sudo apt-get update








 
 

Step 3.

Then go click on that ubuntu logo on the top left hand corner of the screen again and type "Ubuntu Software Center". There you will find all the programs you need.

---

### Post by newb85 on 2013-07-04
Right-o.  Something else we often forget to mention: when you run commands and it asks for a password, it's the password you log in with, and it won't give you any feedback as you type it.

---

### Post by Rob Sayer on 2013-07-04
+1 on using the ubuntu repositories unless you really need to do something that you can't get a program for from the repos.  Particularly for a beginner.  Ubuntu linux does a pretty good  job of maintaining itself, but introducing bad dependencies from repos that can't be trusted means you can bugger up your system somewhat.

Actually, I'd recommend installing and using synaptic package manager to install software.  It may seem a little confusing when you first try it but it's really the best way to install programs I know.  It comes highly recommended on this board.  It clearly shows you what has to be installed or removed, and it has very good history.

---

