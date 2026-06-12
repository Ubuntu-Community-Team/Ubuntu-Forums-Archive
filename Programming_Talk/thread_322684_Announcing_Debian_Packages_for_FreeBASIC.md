---
title: "Announcing Debian Packages for FreeBASIC"
date: 2006-12-20
forum: Programming Talk
---

### Post by sir_mud on 2006-12-20
I've put together a couple Debian packages for FreeBASIC, a great BASIC compiler with the simplicity of BASIC and yet the power of C. There are currently packages for .16b and the Latest CVS version of the compiler. The .16b package is not Ubuntu specific and should work on almost any Debian derivative. The latest CVS version however is probably Ubuntu Dapper only but I haven't tested it on other distros. See the website for step by step installation instructions. At the moment I'm hosting the files on my home server and I don't have a lot of upstream bandwidth so if it's slow and starts killing my bandwidth I'll host it elsewhere.

Download [here]("http://tinyurl.com/yb335d")

---

### Post by coder_ on 2006-12-21
I've heard some good stuff about FreeBASIC at the (Used to be BlitzBASIC only) demoscene forums I used to visit.
[http://www.dbfinteractive.com](http://www.dbfinteractive.com)

They have some very knowledgeable FreeBASIC users there.  The leaders of the forums there are fantastic.  It was an awesome community.  An **awesome** community.

I'd recommend going there if you are into the oldschool demoscene and looking for a small community to join and help people in.

But anyway, back on topic:  Nice! :)  I'll be checking it out.

---

### Post by sir_mud on 2006-12-24
I just got a Repository set up the hard way. Has stable and CVS versions of the compiler available for Dapper and stable available for other Debian/Ubuntus. Follow the link in the first post for information.

---

### Post by yeehi on 2007-12-03
What is the latest on installing freebasic into ubuntu?

Is t

---

### Post by sir_mud on 2007-12-13
I haven't been able to host or update the package for quite sometime but its not very hard to install freebasic using the standard .tar.gz, here's some directions:

1. Download the latest (.18.2 at this time) release for linux from [http://sourceforge.net/projects/fbc/](http://sourceforge.net/projects/fbc/)

2. Open a Terminal window (Applications->Accessories->Terminal in Gnome and K->Run Command-> "konsole" in KDE)

3. Navigate to where you saved the file, if you saved the file to your desktop you would type: "cd ~/Desktop" without the quotes and push enter.

4. Extract the archive using this command: "tar zxf FreeBASIC-version.tar.gz (push TAB to autocomplete after FreeBASIC)

5. Enter the FreeBASIC directory: "cd FreeBASIC-version" (tab to autocomplete again)

6. And the final step to install is to run the provided install script: "sudo install.sh -i" then enter your password when prompted.

If you didn't recieve any errors FreeBASIC is now installed and nearly ready to use. You will need to install several development packages containing library headers. To do this run this command: 

```

sudo aptitude install build-essential libc6-dev libncurses-dev libgpmg1-dev libx11-dev libxpm-dev libxrandr-dev libglitz-glx1-dev 

```

That should install the very basic libraries necessary to get you started. If you get errors about missing libraries then you will need to install the development package for that library, usually liblibraryname-dev, you can search for packages using the command: aptitude search search terms

If you run into any trouble feel free to ask questions on the Linux sub-forum on [http://freebasic.net/forum/](http://freebasic.net/forum/)

---

