---
title: "What is the difference in commands between Ubuntu &amp; CentOS?"
date: 2019-03-11
forum: New to Ubuntu
---

### Post by likewise2 on 2019-03-11
I am new to Linux in a overall way. But I know some CentOS commands (which are essential to run a simple server with LAMP).

Now, presently I am having thoughts of migrating from Windows to Ubuntu for my personal computer. So, I was just wondering which commands are different in Ubuntu? One thing I know that unlike CentOS Ubuntu doesn't use the 'yum' command but what else should I have to learn?

If I see good support from Ubuntu then I might migrate my server from CentOS to Ubuntu too. And also one more thing CentOS has the minimal install option which is without GUI, does Ubuntu gives that option too?

---

### Post by jdeca57 on 2019-03-11
So these are two questions. Let's start with the desktop.
Liike Fedora, Ubuntu uses Gnome as a GUI and as a Centos user I'm convinced you know Fedora. On the surface, there is little difference. Unless you have reasons to avoid Gnome that transition will be easy.You can manage most things from the GUI and under the text terminal the difference is that you use apt, deb and repositories and that's a bit different but nothing very strange there.
If you go for the server, well, then you should be aware that the places where the OS stores data like your web data are different. It's nothing serious, it's simply other directories. php is the same, databases are the same, apache is the same. Data are in other places. And yes, the server comes in text-only so that is not a problem.

---

### Post by likewise2 on 2019-03-11
Can you provide me an article or list where I can see the difference in code between Ubuntu and CentOS?

No Sir, I don't know Fedora. I only that its the version from which RHEL has been derived and CentOS is the non-paid (without logo & subscription or support) version of RHEL.

As, I stated earlier I only know the basic commands to run and update a LAMP server.

---

### Post by yancek on 2019-03-11
The primary differences will be the method of installation of software with CentOS using yum and Ubuuntu/Debian using apt/apt-get.  THe last time I used CentOS it didn't use sudo so that may also be a difference.

Fedora is the the test release version of Red Hat and has all the newest software and has very short support periods and is not stable (although an experienced user can make it so) while CentOS is basically a stable version of Red Hat without the trademarks and support.  Other than what is mentioned in the post above, there should not really be many differences in commands, they both use a Linux kernel.

---

### Post by oldrocker99 on 2019-03-11
The biggest difference between different distributions is how software is installed. Debian derivatives all use apt, Fedora derivatives all use yum, Arch derivatives all use pacman. Aside from that, they all act like Linux systems. Install the desktop you like best, and you're off and running. 

Jump right on in!

As said, don't start out with a bleeding-edge system for now. The LTS (Long-Term Support) versions of Ubuntu are stable and supported for 5 years.  Stay with  one of them for now. Do NOT upgrade 18.04 to 18.10 in place if it's suggested. There be dragons down that road. ;-)

When you have a bit of experience, you need to set up a separate partition for your /home folder. Here's exactly how to do it:[https://www.howtogeek.com/116742/how-to-create-a-separate-home-partition-after-installing-ubuntu/](https://www.howtogeek.com/116742/how-to-create-a-separate-home-partition-after-installing-ubuntu/). Don't make the system partition bigger than 64GB, and even 32GB; your /home folder can never be too big.

Then, if you want to change the version, you can select "Something Else" when installing, format /, and mount the big partition as /home. Easy-peasy.\

I personally, by the way, love the MATE desktop, which is lightweight, attractive, and extremely configurable. Give it a try:```
sudo apt install mate-desktop-environment
```
Log out, select the MATE desktop (or any other desktop installed), and log back in. See what you think. The MATE Tweak utility allows the desktop to look like Windows (Redmond), Mac (Cupertino), and even Unity (Mutiny(!)). I like the top-down menus, so it's a perfect match for me. It's the greatly-improved version of GNOME 2.3, which I fell in love with when I started out with Ubuntu 8.04.

---

