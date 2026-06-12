---
title: "Shells"
date: 2012-05-02
forum: New to Ubuntu
---

### Post by kabukiM0n0 on 2012-05-02
I was wondering. I've spent some time now playing around with Linux, grasping a better understand of the OS and learning - some times way too much . Anyway, 
Apart from the main Ubuntu interface and the obvious Gnome, I found Cinnamon which according to the reviews, worked really well, specially with the update. I personally find it runs rather jumpy and slow, but this could be due to the machine I am running. 
Either way. My initial curiosity was the following. 
Apart from the already mentioned, how many other interfaces/shells are there available to play around with?
or 
Where could I find somewhere that states them and I can look about.

I already did a search, but there was a huge mix of all the Linux interfaces, and in all honesty- I didn't really understand what I was reading. I'm not that Linux savvy as of yet. 

Kind thank you's

K.m

---

### Post by Immolatus on 2012-05-02
Bash is really solid but if you open the package manager and search "shell" you'll get a bunch. The most popular besides Bash might be the Korn shell. Also xterm is fun if you're a programer as it integrates well across to Mac. There is also an xterm extention for emacs(which also has a shell mode). I say it's best to learn Bash though cause if you lose your desktop for any reason TTY1 is a Bash terminal.:popcorn:

---

### Post by JKyleOKC on 2012-05-02
You probably have a small terminology problem, that may get you a few rather confusing responses.

In the Unix-oriented world, which includes Linux, "shell" has a very restricted meaning. Years ago, when helping write a couple of books about the internals of the Microsoft systems of that day (before Windows came on the scene; it was that long ago) I chose the phrase "command interpreter" to describe the class of system programs that are known as "shells" in the Linux world. These are programs that accept a limited number of text-input commands, and perform specific actions in response. In the Windows world, the class includes COMMAND.COM and CMD.EXE. No shell provides a graphic or desktop interface.

Only a small number of such programs exist; the *buntu distributions, like most others, use "bash" (an improved version of earlier shells) as their default shell, but others include the Bourne shell (from the original Unix systems) also known as "sh," the C shell "csh," "zsh," and "ash." However, from the context of your question, I suspect that you're really asking about the facilities known as "window managers" and "development environments" that provide a graphic interface and a desktop of some sort. These are what give rise to the various *buntu flavors, and dozens of them exist.

I don't know of any single place that contains a list of all of them, but I would start by googling for "window manager" and also for "development environment." A window manager is just one component of a complete development environment; it's the part that creates a blank desktop but does not include any facilities to populate it.

The original window manager was "twm" and it's still around. You can experiment with it by opening a text interface via Ctrl-Alt-F2 after installing the twm package, logging into the resulting console, then issuing the command "exec twm" to launch the manager. You will get a gray desktop with nothing on it but a menu. To escape, you can use Ctrl-C or work through the menu to its "quit" choice.

As you can see, such a window manager is rather primitive. However the Google search will show you that dozens if not hundreds of them exist, and some are more capable than others. I used IceWM for years on the system I ran before coming to Xubuntu, and it's still a mainstay of the Mint distribution.

As Linux distributions matured over the years, folk developed additions to basic window managers and collected them into what are now known as development environments. The two most popular DEs are GNOME and KDE, but XFCE is also well liked by many and many more are available.

When I began using Linux seriously, more than 10 years ago, I created a tiny shell script that helped me compare the leading window managers of that day. Unfortunately I can't find it at the moment; however it's what led me to choose IceWM at that time.

At this stage of your introduction to the subject, I'd say the first step into the next level of knowledge should be to become as familiar as you can with the specific jargon of the Linux world, so that you don't get as many not-quite-what-you-intended responses to your questions. To do so, the "jargon file" would be a good starting point. A Google search for it will turn up many copies; it seems to be almost everywhere!

Possibly the next most useful research resource is Wikipedia. It's not always accurate, but its attempt to provide comprehensive coverage of every subject under the sun makes it one of the best tools to put questions into context.

Have fun, and welcome to the endless search for more knowledge!

---

### Post by Derek Karpinski on 2012-05-02
Immolatus, the OP is talking about Desktop Environments.

Gnome (shell or classic)
Unity (built on top of gnome)
KDE (windows like aero glass looking)
LXDE (lightweight)
XFCE (lightweight, not as light as LXDE)
Mate (old classic gnome)
Cinnamon (same goal as above)

You can get crazy and install a dock (cairo, docky, or otherwise) on top of the above DE's.

Personally, I like Unity, but second for me would be gnome classic or whatever they're calling it these days with a cairo dock.

If you want to try them out, either install them in your existing install.  Or better, IMHO, download Kubuntu for KDE, Lubuntu for LXDE, Xubuntu for XFCE, etc and play in a virtual machine.  Installing these DE's will put a lot of extra packages and cruft on your machine.

[http://www.psychocats.net/ubuntu/whichbuntu](http://www.psychocats.net/ubuntu/whichbuntu)

Once you find one you like, do a clean install of the version you like best.

---

### Post by kabukiM0n0 on 2012-05-04
Yes, I was referring to Desktop Environments, My bad.

Thank you though for the information. It is hugely informative and opens new worlds within Linux.

Again, thank you ever so much - it shall be put to good use!

K.m

---

