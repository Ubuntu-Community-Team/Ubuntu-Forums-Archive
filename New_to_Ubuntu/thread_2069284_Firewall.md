---
title: "Firewall?"
date: 2012-10-10
forum: New to Ubuntu
---

### Post by Yezinki on 2012-10-10
Hi,

Does Ubuntu have a firewall if yes how does one find & configure it?

Thanks.

---

### Post by albandy on 2012-10-10
Yes, ubuntu firewall.

[https://wiki.ubuntu.com/UncomplicatedFirewall](https://wiki.ubuntu.com/UncomplicatedFirewall)

---

### Post by agillator on 2012-10-10
Yes, several. To begin with, iptables is the basic command line firewall control system. All the firewalls for linux are actually just front ends for iptables. This gives you total control of the firewall rules.

The front end included with ubuntu is ufw. This is the one you will probably want to use. It should already be installed. If not, you can install it through apt-get, etc. There are others that are similar since they all do basically the same thing if you find you are not happy with ufw. A google search for 'linux firewall' should turn up a few. 

I would suggest you learn a bit about iptables itself, though, so you can be sure your firewall is doing what you want it to do and serving your specific needs. The command 'man iptables' in a terminal window will give you lots of good info, probably more than you can actually use at this point but it will give you a good idea of how firewalls on linux work.

---

### Post by oldos2er on 2012-10-10
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by DuckHook on 2012-10-10
Based on some of your previous postings, I am assuming that you are relatively new to Linux. If my assumption is false, then please accept my apologies and treat what follows as a review. However, based on that assumption, I am going to address what I perceive to be the larger question behind your question.

Firewalls are inherently complicated beasts, so anything to do with them is not going to be as easy as, say, learning a text editor. However, the tools that come with Ubuntu are as good and as straightforward as any, and the various responders on this thread have given you some good links to look into.

In particular, I encourage you to follow the link posted by *oldos2er*. This is a truly excellent primer for people new to Linux who are concerned about security.

At the risk of repeating what it already covers so well, I will just highlight and summarize what I think to be its most important point:

[I]The "Windows Mindset" is largely unneeded and often detrimental to Linux.
[/I]
While it is good to be concerned about security, Linux is far more hardened and secure "right out of the box" than Windows. For various reasons, you don't need a firewall on your personal computers (depending on where they are on your network). I know that this may sound crazy, but bear with me.

The overriding reason for a firewall is to protect you from baddies outside of your home network. Therefore, it is crucial to have a tough, battled-hardened firewall at the gateway that connects you to the Internet. For most users of the sort who visit this forum, this is their router. Almost all routers these days have built-in firewalls that do a passable job of protecting the home network from outside baddies. If you want to practice good security, then it is far more important to make sure that your router is doing its job than installing yet another layer of firewall on your PC.

Putting a firewall on a Linux computer that is not directly exposed to the outside world creates several disadvantages. Firstly, you are increasing complexity. This is never a good idea in any endeavor unless it is dictated by necessity. Secondly, you are adding another "thing" to remember and maintain. For new users already overwhelmed with the task of learning a new OS, you just don't need this additional distraction. Thirdly and most importantly, a firewall on your PC could prevent you from making connections to other machines within your home network that are important and/or useful. I have lost count of the times that users have come to me boiling with frustration because they couldn't connect to something at home, and the culprit has turned out to be the firewall on their PC.

Now for some comforting observations. Linux comes out of the box with all ports closed. In layman's terms, this roughly means that it is already, in a sense, "firewalled". Ubuntu also does not operate in root mode. This means that even if baddies gain access to your system, they will have a hard time changing critical system files (which is what most baddies want to get at). In summary, I would not install a firewall on my PC until I was thoroughly comfortable with Linux.

---

### Post by pqwoerituytrueiwoq on 2012-10-10
if you are just looking for a gui there is [gufw](apt:gufw)
if you are not using unity run this after installing it to get it in the menu
```
sudo sed -i 's/OnlyShowIn\=Unity/\#OnlyShowIn\=Unity/' /usr/share/applications/gufw.desktop
```
if you are using xubuntu also run this one, this will make it have a icon in the settings manager window
```
sudo sed -i 's/\.png//g' /usr/share/applications/gufw.desktop
```

---

