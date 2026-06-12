---
title: "General Question"
date: 2013-01-22
forum: New to Ubuntu
---

### Post by thehim on 2013-01-22
This may be a stupid question, but here goes.
Is the server edition only available as a command prompt version, there is no Graphical User Interface for the server version?

I'm asking as I'm completely new to linux systems, people recommended me to take up Ubuntu, as it's dummy-proof.
Bad thing is I have zero knowledge regards to command prompts.

I'm now running Desktop version, but hope to get to be able to know about Server edition, and use it, lesser resource hogging.

And what happens if I want to add a new Hard disk onto my current system?

It's a single boot Ubuntu.

---

### Post by Bucky Ball on 2013-01-22
Welcome to the forums.

For less resource hogging use a different desktop environment. Xfce or Lxde are a start. You can install either from Software Centre, log out, choose from 'Sessions' and log in. 

For Xfce, install xfce4; for Lxde install lxde. Or you could install Xubuntu or Lubuntu or any other number of flavours and variations instead of straight Ubuntu with Unity desktop enviroment.

If you want to add another hard drive just go ahead and add one. Format it using Gparted.

(PS: Many use xfce for a simple, lightweight server GUI if they need one. Common. You can practice using the CLI only by attempting to do as much as you can in Ubuntu just using the terminal. You could even uninstall all your desktop environments and run Ubuntu from a terminal.)

---

### Post by sudodus on 2013-01-22
> **thehim said:**
> This may be a stupid question, but here goes.
Is the server edition only available as a command prompt version, there is no Graphical User Interface for the server version?

I'm asking as I'm completely new to linux systems, people recommended me to take up Ubuntu, as it's dummy-proof.
Bad thing is I have zero knowledge regards to command prompts.

Yes, Ubuntu Server has a text user interface. It is possible to add a graphical desktop environment (for example light-weight LXDE), but it is not recommended.
> 
I'm now running Desktop version, but hope to get to be able to know about Server edition, and use it, lesser resource hogging.

And what happens if I want to add a new Hard disk onto my current system?

It's a single boot Ubuntu.

But there are several ways to get a less resource-hungry system:

1. Install Lubuntu or Xubuntu

- Lubuntu with the ultra light-weight desktop environment LXDE
- Xubuntu with the light-weight desktop environment XFCE

2. Install those desktop environments into your vanilla Ubuntu. You can select desktop at the login screen.

```
sudo apt-get install lubuntu-desktop
sudo apt-get install xubuntu-desktop
```
or only the plain desktops
```
sudo apt-get install lxde
sudo apt-get install xfce4

```
3. or run a text session with the hotkey combination

***ctrl + alt + F1***
***ctrl + alt + F2***
...
***ctrl + alt + F6***
and 
***ctrl + alt + F7***
to get back to the graphical screen

4. enter the boot option [FONT="Courier New"][SIZE="3"]text[/SIZE][/FONT] into the grub menu

[[COLOR="Red"]https://help.ubuntu.com/community/BootOptions[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

---

### Post by ibjsb4 on 2013-01-22
In order to use the server edition you must understand the command line and that takes time.  Like BuckyBall said, use a lighter desktop if you find Ubuntu too heavy.

[http://xubuntu.org/](http://xubuntu.org/)

[http://lubuntu.net/](http://lubuntu.net/)

---

### Post by thehim on 2013-01-22
I use the terminal function and type in the sudo commands right?
then after setting up, I just boot and select the lubuntu?

installing lubuntu via terminal now

---

### Post by Bucky Ball on 2013-01-22
```
sudo apt-get install lubuntu-desktop
sudo apt-get install xubuntu-desktop
```

Don't do this! You will create even more bloat as that will drag in all default apps from the flavour so you will end up with all Ubuntu default apps and default apps dragged in by installing *buntu-desktop. You don't want that. More resource heavy ...

You only want the desktop environment. One or the other:

```
sudo apt-get install lxde
sudo apt-get install xfce

```

... as suggested. But the xfce one is wrong. It is, as I mentioned:

```
sudo apt-get install xfce4
```

---

### Post by Bucky Ball on 2013-01-22
> **thehim said:**
> I use the terminal function and type in the sudo commands right?
then after setting up, I just boot and select the lubuntu?

installing lubuntu via terminal now

You only want the desktop environment, lxde, not lubuntu-desktop.

---

### Post by thehim on 2013-01-22
Is there a way to clear out the previous installations?
I closed the terminal half way through lubuntu desktop installation.

---

### Post by sudodus on 2013-01-22
> **Bucky Ball said:**
> You only want the desktop environment, lxde, not lubuntu-desktop.
Let her/him try any of the desktop environments, and later on clear out what is not wanted according to this link

[[COLOR="Red"]http://www.psychocats.net/ubuntu/index[/COLOR]]("http://www.psychocats.net/ubuntu/index")

---

### Post by thehim on 2013-01-22
I'm now on Xfce environment, will try it out tomorrow when I have the time.
It's time to sleep, and it does looks alot lighter compared to the default ubuntu desktop.

Thanks.

EDIT,
Any place to do read ups before attempting to do up the server on the Xfce environment?
I'd do it tomorrow.
Or a step-step guide on setting up servers would be good.

---

### Post by Paqman on 2013-01-22
You've not been 100% clear about what you're trying to achieve. Do you want to set up:
[LIST=1]
[*]A server?
[*]A lightweight desktop?
[/LIST]

If you just want a desktop then there's no point installing the server edition. The server edition with desktop packages added isn't any more lightweight than the desktop edition running those same packages.

---

### Post by sudodus on 2013-01-22
Continue testing and select what is best for you :KS
And we would be happy to share your experiences.

Good luck :-)

*Edit*: And a comment to Bucky Ball's post: If you tell us more about what you want to do with the computer, it will be easier to help you.

---

### Post by thehim on 2013-01-22
> **Paqman said:**
> You've not been 100% clear about what you're trying to achieve. Do you want to set up:
[LIST=1]
[*]A server?
[*]A lightweight desktop?
[/LIST]

If you just want a desktop then there's no point installing the server edition. The server edition with desktop packages added isn't any more lightweight than the desktop edition running those same packages.

I like to get a server, small sized for home usage.
But I have zero experience with linux systems, thus trying out desktop version.
I need GUI as I am a complete blur with line prompts.

Which is why I appear so fickle minded.


EDIT,
I'm too used to Windows, just connecting to the same Workgroup and I can treat it as a server.
Thus I need to learn about Linux.

---

### Post by ibjsb4 on 2013-01-22
The command line is already installed on Xubuntu.

---

### Post by grahammechanical on 2013-01-22
I think you will find that the Desktop and Server editions have different default programs/applications. Depending on what you mean by 'lightweight' you may find that the Server edition takes up more space on the hard disk than the desktop edition.

The Server edition is lightweight in the sense that it does not come with a Graphical User Interface and so can be installed on hardware without needing a video adapter installed. They are then administered over the network.

Those Server Edition programs can be installed on the Desktop Edition. So, if your interest is in studying Network Administration, then it is the server programs that should be studied.

The issue of so-called lightweight verses so-called heavy weight GUIs only applies if the hardware you are experimenting with is of a low specification.

You may find that some server applications can have a GUI installed for them. Others may only be administered through the terminal.

Regards.

---

### Post by Paqman on 2013-01-22
> **thehim said:**
> I like to get a server, small sized for home usage.
But I have zero experience with linux systems, thus trying out desktop version.
I need GUI as I am a complete blur with line prompts.


Depending on what you want to do with the server you might find a pre-configured appliacance from something like [Turnkey Linux]("http://www.turnkeylinux.org/") might be suitable. You can get a ready made machine that is already set up for whatever task you want to do. For example, if you wanted a file server you could just download [this image]("http://www.turnkeylinux.org/fileserver").

However, a lot of home servers function as several different things (file server, web server, torrent server, print server, etc) so if that's the case starting with a generic Ubuntu server is fine.

As for GUIs, you might want to look at something designed specifically for servers, such as [Webmin]("www.webmin.com"). You install Webmin onto your server, and it can run headless. You control it through a browser interface on any other machine (any OS). Webmin is significantly lighter and less fuss than installing desktop packages onto your server and then remoting into it.

You'll need to pick up some basic proficiency with the command line though, as most server packages are configured through text files. You'll need to be able to find and edit those files, and you'll need to understand and be able to change file permissions.

---

### Post by sudodus on 2013-01-22
> **thehim said:**
> I like to get a server, small sized for home usage
...
EDIT,
I'm too used to Windows, just connecting to the same Workgroup and I can treat it as a server.
Thus I need to learn about Linux.

If I understand this *edit* sentence, you want a file server: to read and write files on this computer from other computers.

If this is the case, it is easy to set it up as an ssh or samba server. This can be done easily with a desktop version of Ubuntu (Lubuntu or Xubuntu if you want light-weight desktop environments). And there will be a minimum of command line work, not zero, but less than starting with Ubuntu Server.

You can also log in via the network from other computers and run programs in the server with ssh.

But if you know that you want more than that, go ahead with Ubuntu Server. With some help from us at the Ubuntu Forums and some tutorials from the internet you will soon learn a lot of command line stuff.

*Edit*: Or choose some specialised server distro suggested by Paqman. Look forward to an interesting journey. You can change direction and install something different after some time. You gain experience and the next installation will be much easier, when you know more about linux.

---

### Post by thehim on 2013-01-23
I guess I'll go for what Paqman suggested, as I'd like this system to be a file server at first.

Only after studying more into Linux, will I upgrade to Server editions, learn more commands and do more things with it.

Thanks.

---

### Post by ibjsb4 on 2013-01-23
Sounds like you found your answer.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Bucky Ball on 2013-01-23
> **thehim said:**
> I guess I'll go for what Paqman suggested, as I'd like this system to be a file server at first.

Only after studying more into Linux, will I upgrade to Server editions, learn more commands and do more things with it.

Thanks.

Solved? Please mark as such from Thread Tools at top right. This does non stop the conversation.

If you have any further issues, please don't hesitate to post a new thread in the appropriate sub-form.

---

