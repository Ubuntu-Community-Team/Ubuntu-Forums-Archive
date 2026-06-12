---
title: "Is there a way to install JRE(or any other program) with only clicks (i.e no typing)?"
date: 2015-12-08
forum: New to Ubuntu
---

### Post by waitaminute2 on 2015-12-08
Hi,

So I was told to try Ubuntu as it was suppose to be as user friendly as Windows, but so far I can see quite a difference.
I'm on Lubuntu now, trying to install Java runtime and all the instructions I see online (whether by Oracle or by regular users) involve either manipulations with the console (inputting all sorts of commands) or using the Download Center . Isn't there some user friendly way in which I can download executables from the internet and by performing some minimal manipulation making those files run (with password authorization for security's sake)?  


Thank you!

---

### Post by TheFu on 2015-12-08
Welcome to the forums.

Linux is not Windows.  Expecting it to behave like windows will only lead to frustration. There is a learning curve and whether you realize it or not, that 5, 10, 15, 20 years you've used Windows taught you much, of the Windows-way. The Linux-way is different.

I suspect you don't actually need to install java/jre and just need to find the program (or equivalent program) that you'd like to run in the **Package Manager** and install that. If java is a dependency, it will be installed automatically for you.  In most Linux versions, including Ubuntu, software packages know what other packages they depend upon and automatically install any dependencies for you. Give that a try first.

How is Linux Different?

For example, downloading programs with a "setup" isn't how Linux works best.  We use "package managers" to install and patch all software on our systems. There are trade-offs, because the repository maintainers don't always have the latest version/release of any specific package.  For newer versions of some packages, there are PPAs. These are like the Canonical repositories, but anyone, including you, can have a PPA where we place packaged software for others to be able to install through their package manager.  I don't use Java, but know that Oracle has a habit of NOT supporting PPAs, thus making it some 3rd party (someone like you?) who might create one for Java.

Because there are so many different versions of Linux (over 200 distros and counting), there are many different compatibility considerations. The Ubuntu repositories and/or PPAs should address that for you and make it easy.  You just need to pick the repo for your specific release of Ubuntu (14.04 hopefully), then whether it is 32-bit or 64-bit - this isn't any different than Windows (though I haven't installed any new programs on Windows in a few years, so I really don't remember). The 32/64-bit stuff should be automatic for the major repos and qualify PPAs.

Plus, there are 2 different major versions of Java - the proprietary, closed, version, from Oracle and the 100% F/LOSS version (openjdk?) that is from a consortium of companies trying to ensure Oracle doesn't screw the world with their version, their licenses, their mistakes or their API lawsuits. Yes, Oracle sued to have an API fall under copy-write laws. [https://www.eff.org/deeplinks/2015/06/bad-news-supreme-court-refuses-review-oracle-v-google-api-copyright-decision](https://www.eff.org/deeplinks/2015/06/bad-news-supreme-court-refuses-review-oracle-v-google-api-copyright-decision)

Because I don't use the GUI much, I can only provide very high-level instructions. Sorry.  If you open up **synaptic**, that is a package manager, then search for JRE, you should be able to select the package, right-click on it, select "Mark for Installation".  JRE might not work, so be read with "openjdk" or "java", but know that "java" will probably find hundreds of packages. There are other Package Manager GUIs available, I'm just not familiar with them enough to know what is or isn't pre-installed on Lubuntu. You can install any of them on Lubuntu, if you like. Then there's an "Apply" button at the top. Press it.  This will probably be the openjdk version. I suspect Oracle doesn't allow redistribution, but I don't know, but Oracle has a history of killing off F/LOSS projects they acquired with the Sun Microsystems buyout. You might get lucky, assuming oracle allows this.

If you are a Java programmer, getting used to the shell and CLI commands is mandatory. Don't fear the shell. There are many ways to learn it, since every Unix user since 1972 had to go through the same learning curve. There are books, online training, youtube videos, blog posts ... but they all will take effort. Learning a new way of thinking takes effort.  OTOH, my 80+ yr old mother used Linux for the last 4 yrs of her life and never needed to touch the shell/CLI/terminal (because I did all that stuff for her from 4 states away). She happily used the mount, email, web browser, printer to do the things she wanted daily.

Here's a Linux for Windows Users article that will explain many things [http://blog.jdpfu.com/Lin_4_Win_Users](http://blog.jdpfu.com/Lin_4_Win_Users) written by a professional writer. The 5 minutes reading it will really open your eyes, plus he is funny while conveying the most important differences. ;)  He does cover package managers.

---

### Post by QIII on 2015-12-08
User friendly?  Maybe for those of us who have been using it for years.

You "grew up" speaking Windows.  Linux is a foreign language to you.  New languages take time and a great deal of effort to learn.  The first thing one should do when trying Linux is to disabuse themselves of any notion that it will be like Windows and leave that all at the door.

It is generally the case that "downloading executables from the web and installing them" is not popular in the Linux community.  In the Windows community, careless installation of applications found on the web is a prime factor in compromised systems.

Most Linux distributions have software package managers that are as easy as a click.  But you won't often find proprietary software.

One such thing you won't find is Oracle Java:  It is not open source and Oracle will simply not let anyone keep the binaries in their repositories.  That is their decision, not the decision of the Linux community.

So, you have to install it another way.

The very easiest way to do that is by following the instructions [here]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html").

But to make this ***really*** easy:
If you want to install OpenJDK, the open source reference for Oracle Java, you can do so by searching for OpenJDK in your package manager and clicking install.  As the open source reference for Oracle Java, that means that Oracle Java itself must conform to OpenJDK -- that is what Oracle has decreed.  So it's not like you'll be missing anything.

However, if you don't install Oracle Java as described in the link above, you will also have to install the IcedTea browser plugin.  Again, just search for it in your package manager and click to install.

---

### Post by buzzingrobot on 2015-12-08
You might also install and try Synaptic, which, like the Lubuntu's software installer, is a GUI front end to the package manager. 

Installing packages is either going to be via the command line or a GUI.  There's no third alternative, on any OS.

Your best, and first, resort when looking for software to install should always be the official Ubuntu repositories.  If you need something that is not in them, then look for an unofficial source, like a PPA, that has packaged the software for Ubuntu.  That will allow the package manager to install it and track updates.  Installing software from unofficial and unsupported third-parties that is not packaged for installation by the package manager should be a last resort. You'll be responsible for updates and for dealing with problems, incompatiblities, etc.

The web is chocked full of little "howto" articles about installing this, that, or the other and they always use boilerplate terminal commands:  "sudo apt-get install AmazingPackage".   Sites do this because it  is quicker and easier to write "sudo apt-get ....." than it is to explain how to use a GUI tool to do the same thing. It's an wasy way to generate some clicks.

---

### Post by grahammechanical on 2015-12-08
Typing the letters jre in the Software Centre search panel gives as results:

Open JDK Java 8 runtime
Open JDK Java 7 runtime
Open JDK Java 6 runtime

From there on installing is just 2 clicks away.

---

### Post by TheFu on 2015-12-08
OP is running Lubuntu - does Software Centre exist? Don't think so for Lubuntu. Synaptic is a little busier than "Software Center" and many people prefer to see all the available packages, not just the most popular ones.

buzzingrobot - brilliant.  100% agree on the repo --> PPA --> then all other methods order.

**sudo apt-get install AmazingPackage** is easier than point here, click there, then there, then there, then there and including all those screen shots.  Plus apt-get is concise, but results in the desired outcome 98% of the time.  All the package manager front-ends are like that - doesn't usually matter which one is used. The back-end database will still maintain the true states for packages.  It is completely safe to use apt-get or aptitude or synaptic or software-center or ..... whatever else package manager someone decides to release (provided it works with Ubuntu and APT).  Of course, blindly copy/pasting commands into any Linux system can be extremely dangerous, so it is best if every command and every option is researched before hitting <enter>.  Learn a little every day, just like how to learn a foreign language or how to eat an elephant, one bite at a time.

For people really new to Linux, google searches are NOT their friend. Sure, the search is important, but the results may not lead to a good answer.  There's no way to know whether the advice applies to all systems or how much of an "expert" the author may or may not be.  I'd guess that 80+% of those articles were written by relative noobs who think they figured out something and their method will work for others. That usually is not the situation. For how-tos, try to stay with reputable sources. A few:
*    Ubuntu Desktop Guide
*    Ubuntu Server Guide
*    Help.ubuntu.com &#8211; semi-official ubuntu help.
Sorry, the links where lost in the copy/paste, but these search terms will find the correct locations.

Of course, asking for help here and on AskUbuntu.com is a good way too.  We are almost all volunteers, just trying to help others navigate Ubuntu.  I've found it is best to assume I'm doing something wrong or missed a subtle point when things don't work the way I expect.  That tone will get more help, since we all make mistakes or don't know how to do everything. Ubuntu, GNU, and Linux are huge topics. After over 20 yrs, I think, maybe, I've grasped 10%. ;)  Plus there is always someone smarter than I, in some topic. Always.

---

### Post by mastablasta on 2015-12-09
> **TheFu said:**
> OP is running Lubuntu - does Software Centre exist? Don't think so for Lubuntu.
.
it has Lubutnu software center : [https://apps.ubuntu.com/cat/applications/lubuntu-software-center/](https://apps.ubuntu.com/cat/applications/lubuntu-software-center/)

---

### Post by stalkingwolf on 2015-12-09
not user friendly?  i just gave a computer to a 4 yr old with mint on it and all the educational packages.  from what his Mom says he is having a blast with it.  I  suspect Mom is to .
Ive given several to kids in the 10 - 12 yr range none of them have had any problems.

---

