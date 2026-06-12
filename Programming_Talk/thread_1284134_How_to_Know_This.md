---
title: "How to Know This?"
date: 2009-10-06
forum: Programming Talk
---

### Post by huangyingw on 2009-10-06
Hello,
     Some Ubuntu operation must be completed within  a series of UI based operation. For example, searching for the best software source, or, launching GUI-based Kdiff3.
    I want to know, the background triggering event handler script/codes, with every mouse click, or mouse navigation through screen.
    If I could know the background better, so, I could simulate the similiar action with the GUI show.
    For example, the Kdiff3 could not launch in NX's text command mode. But, it could launch from GUI-base operation. So, I need to know, what the exact code/script actions for the UI operation.
    How could I know this?

---

### Post by Tony Flury on 2009-10-06
You may well find that many GUI operations launch the equivalent of command lines (using things like systems calls, or calls to other libraries), rather than actually launching the commands themselves - but then again I guess that some GUIs do actually launch the commands (i think Synaptic package manager does this but i might be wrong).

The only way to know for sure is to get the source code for your favourite GUI application, and read through the source code to understand actually what it does - what systems calls or commands are launched when the GUI buttons are clicked etc.

You will need to understand a range of languages to achieve this task - for instance C, C++, Python, Java, C# and many others, it all depends on which application are you interested in, and which language it is written in.

---

### Post by huangyingw on 2009-10-08
> **Tony Flury said:**
> The only way to know for sure is to get the source code for your favourite GUI application, and read through the source code to understand actually what it does - what systems calls or commands are launched when the GUI buttons are clicked etc.

Well, get the source code, is something like bellowing:
```

test@test-desktop:~$ type ifconfig
    ifconfig is /sbin/ifconfig
    test@test-desktop:~$ sudo dpkg -S /sbin/ifconfig
    net-tools: /sbin/ifconfig
    test@test-desktop:~$ sudo apt-get source net-tools

```

---

### Post by Tony Flury on 2009-10-08
Looks right, but having said that i have never attempted to get the source code of any package, as I have never been that motivated to delve into the inner workings of stuff that already works.

If I was going to grab the source code for something - as a cure for insomnia maybe - I would enable the sources repositories in Synaptic and download it from there.

---

### Post by nvteighen on 2009-10-08
Just something: **Don't** do "apt-get source" with root privileges... 1) You don't need to be root and 2) you'll get into a permissions issue as the downloaded directory will be owned by root... by not using su(do) you will be the owner.

---

### Post by huangyingw on 2009-10-09
> **nvteighen said:**
> Just something: **Don't** do "apt-get source" with root privileges... 1) You don't need to be root and 2) you'll get into a permissions issue as the downloaded directory will be owned by root... by not using su(do) you will be the owner.
Yes, while, I don't care about the root privilege. For this PC is used only by me....

---

### Post by huangyingw on 2009-10-09
> **Tony Flury said:**
> Looks right, but having said that i have never attempted to get the source code of any package, as I have never been that motivated to delve into the inner workings of stuff that already works.

If I was going to grab the source code for something - as a cure for insomnia maybe - I would enable the sources repositories in Synaptic and download it from there.
Yes, I am also seldom motivated to delve into that degree..But, if this could enable me more convenient usage, let take it as a learning tour:(:(

---

### Post by Reiger on 2009-10-09
Quite a few applications register themselves as a D-BUS service. The idea is that you can call the underlying D-BUS service to do something; rather than directly prodding applications.

You may want to check if, say, kdiff3 registers itself as D-BUS service too.

Link to D-BUS tutorial: [http://dbus.freedesktop.org/doc/dbus-tutorial.html](http://dbus.freedesktop.org/doc/dbus-tutorial.html)

---

### Post by huangyingw on 2009-10-10
> **Reiger said:**
> Quite a few applications register themselves as a D-BUS service. The idea is that you can call the underlying D-BUS service to do something; rather than directly prodding applications.

You may want to check if, say, kdiff3 registers itself as D-BUS service too.

Link to D-BUS tutorial: [http://dbus.freedesktop.org/doc/dbus-tutorial.html](http://dbus.freedesktop.org/doc/dbus-tutorial.html)
Yes, thanks to your guide. I will save this in my favorite link.

---

