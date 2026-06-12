---
title: "Does synaptic package manager have a larger software database than USC"
date: 2015-02-15
forum: New to Ubuntu
---

### Post by remmas-sido on 2015-02-15
USC: Ubuntu Software Center
Because a lot of users prefer it, so I was wondering if that was the reason?

---

### Post by TheFu on 2015-02-15
Software Center was designed to be simpler and to show the most popular software. This is good for people new to Linux/Ubuntu.

Synaptic shows all the packages available in the same repositories that get filtered by SC.  Packages for developers, libraries - basically seeing all those packages can be confusing and scary to the uninitiated.

Underneath both use APT, so the dependency checks are the same ... the packages are loaded from the same sources with the same gpg validations, etc.  I actually use aptitude - since most of my systems are pure servers (no GUI). It works fine on desktops too.

So, there are times to use SC, other times to use Synaptic and still other times to use aptitude or apt-get ... they are virtually just a different interface over APT. Preference, that's all .... er ... mostly. There are times when aptitude **is** better, but most normal users won't run into those situations.

---

### Post by PhilGil on 2015-02-15
> **remmas-sido said:**
> USC: Ubuntu Software Center
Because a lot of users prefer it, so I was wondering if that was the reason?
The USC hides system files and libraries, so all you see when you search is the user-facing package. Of course, all the dependencies are installed when using the Software Center to install a package.

I'm one of those users who prefer Synaptic to the USC, primarily because it is faster and because I'm old school enough to want to see all the packages that I'm installing.

---

### Post by monkeybrain20122 on 2015-02-15
I don't think synaptic is that difficult to use. I started with 10.04  and learned to use it in no time. The USC is too dumbed down IMO it would be very frustrating to use if one tries to do anything beyond 'absolute beginner' tasks. It is also terribly slow.

But the USC does have things that you don't find in synaptic like paid apps. I never use those though.

---

### Post by gifford on 2015-02-15
Synaptic is also a great tool. You can use it to fix broken packages, find upgradable packages, change or add repositories, etc. As indicated previously, it is much faster for installation and lets you know
all of the packages and dependencies needed for installation. Synaptic really is your friend when using Ubuntu.

---

### Post by newb85 on 2015-02-15
Direct answer is no.  The packages available are exactly the same. *Edit: see note below*  USC does hide what it calls "Technical Packages", but tells you it's doing so and allows you to view them.

I generally use USC or apt-get, and haven't had synaptic installed in some time.  I find USC more helpful than synaptic when I'm browsing and don't know exactly what I'm looking for.  I find apt-get faster than synaptic when I know exactly what I want to do.  But that's just me.

*Note: Yes, I forgot to mention that USC by default runs slightly behind because of phased updates.*

---

### Post by ajgreeny on 2015-02-15
> **monkeybrain20122 said:**
> I don't think synaptic is that difficult to use. I started with 10.04  and learned to use it in no time. The USC is too dumbed down IMO it would be very frustrating to use if one tries to do anything beyond 'absolute beginner' tasks. It is also terribly slow.

But the USC does have things that you don't find in synaptic like paid apps. I never use those though.
^^^
This is absolutely right.

I started using Ubuntu with version 5.04 or 5.10, I can't remember which, when USC was not even available, maybe not even thought of, and when USC arrived, I looked at it and quickly decided it was of no use to me.

In those 10 years of using Ubuntu I have never once actually used USC; it is supposed to be simpler than synaptic but I find it much more cumbersome when searching for packages.  It also is not nearly as flexible when dealing with problems like broken packages, etc etc. nor does it use the phased updates that USC does, so you get everything that is available if you use it for updating your system.

---

### Post by newb85 on 2015-02-16
USC often gets a bad rap from veteran Ubuntu users.  Simply put, it doesn't really fit into their software management workflow.  But a growing number of users come with app-store/play-store style experience, and respond well to that kind of interface.

Phased updates, meanwhile, are an intentional part of the Ubuntu experience.  Many of the aforementioned users also prefer a more well-tested set of applications, and phased updates is one way of achieving that.  Regardless of whether they care if they receive phased updates, it's hardly a reason to tell them not to use USC/Software Updater.  Phased updates can easily be defeated with a single switch in the /etc/apt/apt.conf file.  See [https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)

---

### Post by oldrocker99 on 2015-02-16
When I started using Ubuntu, back in the day (8.04), Synaptic came preinstalled (!), and I had zero difficulty learning how to use it. 

USC is nice if you're installing or buying paid-for software, but (1) written in Python, it's somewhat slower, and only installs one program at a time, and (2) its search function is a lot less efficient than Synaptic's search and quick filter options.

USC is the only option for installing pre-purchased software (Torchlight,and many others which were in Humble Bundles), and some I purchased directly from USC, like the Libre Office manuals, which DO get updated with new versions. However, Synaptic is my go-to installer.

---

### Post by Bucky Ball on 2015-02-16
I've never used the Software Centre. I have only ever used Synaptic and 'apt-get install' in the terminal. Matter of personal preference, I guess. Synpatic gives you a lot more info, though, as has been mentioned.

---

