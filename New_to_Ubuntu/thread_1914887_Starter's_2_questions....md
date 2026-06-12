---
title: "Starter's 2 questions..."
date: 2012-01-25
forum: New to Ubuntu
---

### Post by Jan Erik on 2012-01-25
1. I suppose that there is an online support chat. Where do i find it?
2. I tried to download Kubuntu-Desktop (KDE) in my Ubuntu 11.10, but the CD/DVD was requested. I put the DVD in and it didn't find what it wanted. I then put a CD in (which also have) and it still didn't find what it wanted... How can I get KDE into my Ubuntu, as an additional choice for Gnome?

---

### Post by nothingspecial on 2012-01-25
Hi, welcome to the forums.

You can get real time help in #ubuntu or #ubuntu-beginners using an irc client

[https://help.ubuntu.com/community/InternetRelayChat](https://help.ubuntu.com/community/InternetRelayChat)
[http://www.ubuntu.com/support/community/chat](http://www.ubuntu.com/support/community/chat)

To install kde and a minimal set of kde applications install kde-plasma-desktop from the software center. To install the full kde based distribution install kubuntu-desktop although you will then have a mixture of kubuntu and ubuntu which some people find rather messy.

---

### Post by Lars Noodén on 2012-01-25
1) The general chat forum is #ubuntu on IRC freenode:

[http://www.ubuntu.com/support/community/chat](http://www.ubuntu.com/support/community/chat)

2) One way, if you want the full Kubuntu distro, would be to install the package 'kubuntu-desktop'  If you want only the KDE desktop, then you can install just the package 'kde-plasma-desktop'

---

### Post by Jan Erik on 2012-01-25
Thanks! (Eller kanske hellre: Tack!)
I did just that to install KDE, but - as I wrote - the DVD was requested and something wasn't found on it, and it stopped there ... so then what?

Please suggest an IRC client and tell me, what to do with #ubuntu or #ubuntu-beginners in it ...
As you see, I am a beginner with Ubuntu.

---

### Post by Lars Noodén on 2012-01-25
For an IRC client you can choose Pidgin or Telepathy, among many others.  Each client has strengths and weaknesses so you might want to try out two or three eventually and see which one suits your tastes best.

Here is some background material:

[https://help.ubuntu.com/community/InternetRelayChat](https://help.ubuntu.com/community/InternetRelayChat)

When you choose a nickname to use, you might want to register it to reserve it for future use:

[http://freenode.net/faq.shtml#registering](http://freenode.net/faq.shtml#registering)

---

### Post by nothingspecial on 2012-01-25
xchat is a nice easy irc client, install it launch it and (from memory), choose a nickname then in the server list choose **freenode** and connect. Then type ```
/j #ubuntu,#ubuntu-beginners
``` and ask a question in either or both channels.

#ubuntu is very busy
#ubuntu-beginners is some what quieter.

Can you post the exact error message you get when trying to install kde

---

### Post by haqking on 2012-01-25
If you are unfamiliar with IRC or chat interfaces use the web interface it is easy.

[http://webchat.freenode.net/](http://webchat.freenode.net/)

---

### Post by Jan Erik on 2012-01-25
I just tried again and a Ubunto 11.10 CD/DVD was requested that has "Oneiric Ocelot", but it seems that my DVD doesn't have that.

So what can I do if the DVD doesn't help?

---

### Post by Jan Erik on 2012-01-25
I found this:
"XChat is not installed by default. It is located in the *Universe* section of the Ubuntu repositories. Install XChat by opening Synaptic (*System, Administration, Synaptic Package Manager*) and highlighting *xchat*. XChat and it's associated packages will be installed when the user selects *Apply*. "

So where do I find Synaptic. i didn't find it in System Settings (no Administration etc,).
And how do I access Universe?

---

### Post by nothingspecial on 2012-01-25
Use the software center.

---

### Post by haqking on 2012-01-25
> **Jan Erik said:**
> I found this:
"XChat is not installed by default. It is located in the *Universe* section of the Ubuntu repositories. Install XChat by opening Synaptic (*System, Administration, Synaptic Package Manager*) and highlighting *xchat*. XChat and it's associated packages will be installed when the user selects *Apply*. "

So where do I find Synaptic. i didn't find it in System Settings (no Administration etc,).
And how do I access Universe?

just use the webchat interface i posted above if you are having issues

you have to install synaptic if you are running 11.10 or use software centre

```
sudo apt-get install synaptic
```

---

### Post by KdotJ on 2012-01-25
As for installing KDE... how are you doing it? Are you connected to the internet while doing so? It seems odd that it would ask you for the CD/DVD if you're installing from the software centre or terminal.

---

