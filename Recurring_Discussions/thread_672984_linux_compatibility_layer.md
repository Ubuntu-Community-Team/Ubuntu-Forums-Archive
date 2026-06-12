---
title: "linux compatibility layer"
date: 2008-01-20
forum: Recurring Discussions
---

### Post by zbog on 2008-01-20
Please do not refer me to Wine, which is a different dish!

I am thinking of a layer/API that ensures that if an application runs on Ubuntu, and also runs on Fedora without major changes. A counter-example: some linux distros have devices mounted on /mnt others on /media. Also I had installed the Apache HTTPD 2.0 web server on its default location and Eclipse still had problems finding it.

It would have been useful if Linux had a common settings repository where programs could share there settings. What if, in my case above, Apache had published its home path and configuration file to a common repository? Eclipse could then find Apache automatically and everything would run smoothly, without my intervention.

I know that the fact that Linux has no common repository for its settings has been driving malware writers away from it, but it has also had driven away a lot of good, beginning programmers.

This lack of compatibility between distros, desktop enviroments, and free platforms (BSD, Java, Linux) is what drives away most new developers and users following them. I would like to see this as one of the top priorities of all major Linux distros.

---

### Post by zbog on 2008-01-20
Some more examples that I could not fit in the first post:
I have configured my mail accounts in KMail, I got my mails everything fine.
Then I wanted to use Thunderbird, but whoa, I have to configure it again, since Thunderbird and KMail can not share a common setting.
Another example:
to exchange bookmarks between Konqueror and Firefox one has to use an application called "Bookmark bridge", that I have to run manually every time I want synchronization. This is a major inconvenience for an end user of a computer.

Now to extend the talk about the application developer that wants to make a platform independent application the major inconvenience at the user level now becomes a huge problem:
the developer will stick to her/his statement that the application is platform independent and will test it on the myriad of Linux distros and derivatives, or will drop the 'platform independence' out, and will join the people maintaining the dominance of non-free platforms.

The proprietary developer of the OS, being the sole developer of the core platform, offers a strong, 'de facto' standard to other applications. So the proprietary OS developers are ahead of us by nothing more than standards for third party developers (be they freedom developers or not). 

Integration is the key to our success.

---

### Post by Sef on 2008-01-20
Moved to Recurring Discussions.

---

### Post by popch on 2008-01-20
> **zbog said:**
> The proprietary developer of the OS, being the sole developer of the core platform, offers a strong, 'de facto' standard to other applications. So the proprietary OS developers are ahead of us by nothing more than standards for third party developers (be they freedom developers or not). 

If that were true, then the problems stated in this and the previous post would not exist in the unnamed proprietary OS.

In at least one of the proprietary OSs in my home, the very same problems can be observed, such as incompatible settings for mail applications, mutually incompatible bookmarks and so on.

---

### Post by zbog on 2008-01-20
Here is an example of what I mean: 
> Elektra is a universal hierarchical configuration store, with related goals like GConf and the Windows Registry. It allows programs to read and save their configurations with a consistent API, and allows them to be aware of other applications' configurations, leveraging easy application integration. The whole point of it is to tie applications together, so that they can co-operate and share their user-preferences. [http://www.libelektra.org/]("http://www.libelektra.org/")

I don't know the project well enough to say how well it works, but at least they have high goals.

KConfig-XT and GConf are good, but limited only to applications part of their respective desktop enviroment (KDE or Gnome). They do not include Firefox or Eclipse. And other desktop enviroments ( XFCE or E17 and countless others) are not even included!

---

### Post by Darkhack on 2008-01-21
Already been done and improvements are being worked on...

[http://en.wikipedia.org/wiki/Linux_Standard_Base](http://en.wikipedia.org/wiki/Linux_Standard_Base)

---

