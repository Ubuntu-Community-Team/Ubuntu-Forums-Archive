---
title: "Installing stuff"
date: 2014-08-26
forum: New to Ubuntu
---

### Post by AleksaK on 2014-08-26
I'm completely new to Ubuntu, installed it few hours ago and I find it hard to realize how..well.. installing stuff works. On windows I'd just open up a file and everything would go smooth. But from what I hear everything works with Terminal here? I mean I downloaded Google Chrome .deb file and double clicked it, asked me if I wanted to install it via Software Center, I said yes, and it said 'this package cannot be opened'.
And another thing, probably stupid question. I installed qBittorrent from Software Center and when I click on it, it well.. doesn't get opened. It has that '>' by it's name but I can't see it anywhere... 
For the first question, some basic tutorial would do, preferably video tutorial.
Thanks in advance!

---

### Post by grahammechanical on 2014-08-26
> [COLOR=#000000] But from what I hear everything works with Terminal here?[/COLOR]

No. We have the Ubuntu Software Centre which will download and install applications and will remove them. Choose the applications from the Software Centre.  Applications available in the software Centre are code audited to make sure that they do not contain any malicious code.

I installed Chrome the other day and I used the software centre. I found that Chrome had to be launched by running a command in the terminal and could only be removed by running a command in the terminal. But that is what we get when we download proprietary software which the Ubuntu developers cannot modify to put an icon in the Launcher.

Regards.

---

### Post by deadflowr on 2014-08-26
> I mean I downloaded Google Chrome .deb file and double clicked it,  asked me if I wanted to install it via Software Center, I said yes, and  it said 'this package cannot be opened'.

That sounds like you might have had a second instance of apt running. Perhaps the updater was running.
Sometimes all it takes it for you to wait a moment.
I usually install chrome via the software center without issue.
It's been well over two years since I've needed to start chrome through a command in the terminal. The icon works for me as expected.

However to install via the command-line(terminal), if you want
You can run
```
sudo dpkg -i <filenamehere>
```
replace <filenamehere> with the the file name.
Typically downloads are in the Downloads folder so the file name path would be
/home/yourname/Downloads/packagename.deb

Hope this helps, if even a little.

---

### Post by mastablasta on 2014-08-27
and to install programs outside of software center you would add a personal repository to software sources in software center, update the center and then the programs you want to install appear in the software center.

---

### Post by Rob Sayer on 2014-08-27
> **mastablasta said:**
> and to install programs outside of software center you would add a personal repository to software sources in software center, update the center and then the programs you want to install appear in the software center.

However, you should generally avoid installing through 3rd party ppa's if you're new to linux.  These are not beta tested or supported by ubuntu and can cause hard to diagnose problems, even causing failure when you update e.g.  I *never* use them unless I damn well know what it is and it does something I can't do without.  That's not very many programs in my case.  Some ppas have malware too.

BAsically, Linux is extremely stable but you can destabilize a linux installation, and 3rd party ppas are a pretty good way to do it.  Lots of blogs recommend them and lots of linux blogs aren't very good.  Newbies can't tell the difference so it's better to stick to the standard ubuntu repos.

However, I have to disagree with "On windows I'd just open up a file and everything would go smooth".  It does until it doesn't, and you have malware or adware.  Or your Windows registry gets buggered up when some app install also installs a bunch of crappy 3rd party codecs.  Fixing the registry is a swine and there aren't any reg edit tools I trust.

Note that this all happens *with no warning*, which doesn't happen in linux.  Windows permission levels suck.  Before I installed ubuntu I was using mostly Linux ports in Windows 7 because I was sick of badly behaved programs.

It's not so much that Linux is more complicated than WIndows but more that Linux doesn't hide what it's doing from you.

I highly recommend installing Synaptic Package Manager from the repos for installing programs.  There is a small learning curve but it's definitely worth the effort.  Synaptic is one of the most recommended Linux programs by the really serious geeks here.  I always use either that or the terminal to install.  It's been a while since I used software center.

---

