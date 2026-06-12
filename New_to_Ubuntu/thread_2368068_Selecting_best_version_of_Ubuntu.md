---
title: "Selecting best version of Ubuntu"
date: 2017-08-06
forum: New to Ubuntu
---

### Post by tweetybirdbrain on 2017-08-06
Hello Everyone, 

i'm trying to figure out what the best flavor of ubuntu is right. I know it should be goal driven, but it seems that there's multiple goals. 

So, I'm trying to set up a test environment / learning environment that will eventually lead to a portfolio. 

So the experiment invovles 3 web sites, I'd like to create. they all will have either a) relational or b) non-relational database (mySQL / Mongoose), that will receive server calls (node.js / ruby on rails), from DOM (browser) javascript (react/angular - frameworks) / ruby / word press or php environments. 

Theoretiocally, these databases might also be copied to cloud servers mimic'd (test scenario - server loads increase)

So ... do I want ubuntu desktop? server? cloud? If I install desktop, can i install server ontop or is server the OS just not so pretty? can install cloud ontop of that?

Thanks a bunch

tbb.

---

### Post by vocx on 2017-08-06
> **tweetybirdbrain said:**
> ...

So ... do I want ubuntu desktop? server? cloud? If I install desktop, can i install server ontop or is **server the OS just not so pretty?** can install cloud ontop of that?

Thanks a bunch

tbb.
I think you are overthinking this. Essentially, a basic Linux system is just the Linux kernel and some basic programs, with no graphical interface, and you do everything from the command line. This is a Linux "server".

A desktop is the same as the server, but with the graphical user interface, or desktop environment, added on top. If you want to see the desktop, a file manager, and click on screens and windows, then you install the desktop.

Cloud? I've never heard of it, but I guess it's like some sort of virtualized server or desktop. Or who knows.

Anyways, since you are new to Linux, I suggest you install the desktop version and start doing whatever you want to do.

The "server" version basically means no user interface. That is, if you are very experienced with computers, and you know what you want to do, you can install email server, SQL, Apache, whatever, all from the command line. But for your case, I'd start with the normal desktop install, and see how it goes from there.

Linux systems are modular, meaning you can install all packages that you have in a "server" also in a "desktop". They use the same repositories. It's just pieces of puzzle. As long as your central figure is complete (basic Linux kernel and utilities), you can keep adding jigsaw pieces as you want.

---

### Post by mastablasta on 2017-08-07
you should install server and can install it in virtualbox (or similar) even with low ram on host machine:

here is a nice howto: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by ClickXT on 2017-08-07
I would install the Desktop if you are very fresh with Ubuntu. I think you could benefit from the UI. You can always switch later once you get some time under your belt.

---

### Post by The Cog on 2017-08-07
I too recommend installing the desktop version. You can always stop the GUI from starting at boot time if you want ([https://askubuntu.com/questions/16371/how-do-i-disable-x-at-boot-time-so-that-the-system-boots-in-text-mode](https://askubuntu.com/questions/16371/how-do-i-disable-x-at-boot-time-so-that-the-system-boots-in-text-mode)) but you might prefer to have the GUI available while you are learning your way round.

---

### Post by Bucky Ball on 2017-08-07
I agree with the majority of posters here, but with a caveat: go the desktop to start with until you know the system a little better, but I wouldn't recommend Ubuntu. I'd go for a Ubuntu flavour: a minimal install or Ubuntu Gnome or Xubuntu-core or a lighter spin along those lines. 

You don't need Ubuntu and all that comes with it for what you want to do. Possibly a lot of cruft you'll probably never use. Also, Ubuntu 16.04 LTS (you should use LTS releases for servers and production machines) uses the Unity desktop environment. You may just start getting 'second nature' with that when everything changes as the default DE is changing back to Gnome in 18.04 LTS. May as well start there, or with another DE than Unity, now. ;)

I generally install Xubuntu-core which gives me the Ubuntu kernel, xfce4 DE and not much else. I install the things I want/need from there (not a lot) and end up with a light and lightning fast, stripped back racehorse. :)

As mentioned, you can add things you might need later from the software repositories. There is no need to worry about installing a release that doesn't have an app you want. Just add apps as you need them. Easy.

---

