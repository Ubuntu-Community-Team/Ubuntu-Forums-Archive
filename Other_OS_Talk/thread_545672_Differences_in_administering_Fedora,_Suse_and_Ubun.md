---
title: "Differences in administering Fedora, Suse and Ubuntu"
date: 2007-09-07
forum: Other OS Talk
---

### Post by sicofante on 2007-09-07
Is there any book or reference material that will highlight the differences in administering these three distros?

I'm not trying to choose. I WILL have to deal with the three of them shortly and I just want to get an overview of what will be the common procedures and the differences.

Thanks for any info.

(Guess I'll post this same post at Fedora's and Suse's forums.)

---

### Post by afonic on 2007-09-10
I haven't used Suse for a server so I cannot know how you use Yast in the command line (I think it has an ncurses interface).

In my experience Ubuntu Server is a solid base, keeping the system up to date is easy and security is up to par with older and most trusted solutions. And if you get a LTS release you have support for 5 years which is very important if you don't want to spend your time updating boxes and solving problems.

And that exactly is the weekness of Fedora. The support cycle is too small causing you to update between releases which is NOT trouble free. If you have a mission critical server stay away from Fedora, it can cause you serious headaches.

Last but not least, CentOS is an excellent solution for every server scenario. :)

---

### Post by sicofante on 2007-09-10
Sorry I don't think I expressed myself correctly. I was talking about the differences in the location of configuration files and procedures for a number of things.

For example, there's a huge difference on how to enable ethernet bonding (aggregate two or more ethernet ports) in Ubuntu/Debian and Fedora/Centos. I would like to know if this type of differences are summarized anywhere in a book or in the web. I can't find it, but then I might just being using the wrong keywords in Google...

Thanks again.

---

### Post by afonic on 2007-09-11
I think your best choice would be to read through the documentation of each distro and right down the differences you are talking about.

I haven't found a page that summarizes them, and yes as you say they are quite different from the location of config files to a simple httpd restart.

---

