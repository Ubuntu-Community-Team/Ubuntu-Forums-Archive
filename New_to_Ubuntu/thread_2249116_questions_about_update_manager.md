---
title: "questions about update manager"
date: 2014-10-19
forum: New to Ubuntu
---

### Post by chopra on 2014-10-19
Hi Guys,

I recently changed the settings on my update manager package to check for updates weekly instead of daily.  However, recently, it offered some thunderbird updates.  Because I don't use thunderbird, I unchecked them.  Then, it kept bugging me about them every time I signed on.

I noticed that these were listed as "important security updates", and apparently, the ordinary weekly setting doesn't apply to them.  The settings for the updates have:

Automatically check for updates: (daily, weekly, never, etc)

When there are security updates: (display immediately, download automatically, download and install automatically)

When there are other updates: (display immediately, display every two weeks, etc)

First, how are the first and last of these related?  If I have autocheck weekly, how is it possible to display updates immediately?  Those two seem to be redundant.

Second, there seems to be no way to control the frequency of security updates.  So, for updates, (security or otherwise), if I don't need them, they're just going to keep showing up indefinitely?
There've been updates on other systems that I've declined, only to see them appear the next time update check occurs, and I've sometimes just accepted them out of exasperation, even if they don't apply to me.

So, is there a way to decline an update, and just have the information stored that you've declined it?  Otherwise, I'll be promped for thunderbird updates every time I log on, and I don't use thunderbird, so why fill up my hard drive with them?

Thanks, Chopra

---

### Post by Vladlenin5000 on 2014-10-19
Updates are displayed for any software you have installed whether you use it or not. And you should apply those anyway because you may want to use that software later. If not, why keep that software anyway? Better to uninstall, don't you think?

---

### Post by grahammechanical on 2014-10-19
"Displayed" = giving the user notification of the security fix instead of waiting until the user runs Update Manager. With security fixes it make sense to not allow the user to turn off Display Immediately as that would make the machine vulnerable. So, then the question becomes, does the user want the update at that moment, or does the user want to postpone it to some more convenient time? But the security update cannot be forgotten. This kind of thing makes Linux a very secure OS. 

There is a difference between "checking for updates" and being notified that there are updates. With stable releases of Ubuntu a daily or weekly check for updates will often come up blank. The user does not need to be notified that there is nothing to report. But what if there is some package that can be updated, when does the user want to know about it? Immediately? Or at a regular time, say, every two weeks?

By the way, our hard drive is not filled with updates because it is the package that is updated. The existing Thunderbird application will be replaced with an updated version. Just use the software centre to remove Thunderbird. You do not use it. You do not want it. So, remove it. No more security updates for Thunderbird because it is no longer on your system.

Regards.

---

### Post by craig10x on 2014-10-19
In the Software Updates section, the way i have the 3 buttons (regarding updates) is:
Automatically Check For Updates: Daily
When There Are Security Updates: Display Immediately
When There Are Other Updates:    Display Immediately

That way, the updater automatically checks about 30 minutes or so after i boot up ubuntu in the morning, and if there are any, the Software Updater icon appears on the unity dock bar and i install them...
If the Updater Icon doesn't appear, it meant no updates to display...

Notify Me of Any New Ubuntu Version refers to it notifying you of an UPGRADE... which you can set to notify you of LTS Versions only or Any New Version (which means the 6 month ones)...
I was just let it install everything if i were you (doesn't matter whether you use the particular item or not)...This is not windows..these things don't hog up your hard drive...;)

---

### Post by ian-weisser on 2014-10-19
> **chopra said:**
>  So, for updates, (security or otherwise), if I don't need them, they're just going to keep showing up indefinitely?
[...]
So, is there a way to decline an update, and just have the information stored that you've declined it?

Keeping your system secure and updated is not really a choice, you know.
Ubuntu is built on the assumption that you want to install security and other important updates.

The purpose of the checkboxes is to *temporarily delay* an update because it you need to do more research, test it, or ask a question about it.

Declined updates will keep showing up forever.
The only way to stop prompting for updates you don't want is to uninstall the package.

---

### Post by vasa1 on 2014-10-19
> **chopra said:**
> ....  However, recently, it offered some thunderbird updates.  Because I don't use thunderbird, I unchecked them. ...

... Second, there seems to be no way to control the frequency of security updates.  So, for updates, (security or otherwise), if I don't need them, they're just going to keep showing up indefinitely?
There've been updates on other systems that I've declined, only to see them appear the next time update check occurs, and I've sometimes just accepted them out of exasperation, even if they don't apply to me.

So, is there a way to decline an update, and just have the information stored that you've declined it?  Otherwise, I'll be promped for thunderbird updates every time I log on, and I don't use thunderbird, so why fill up my hard drive with them?
...
Whether you use or don't use Thunderbird, you will still get updates to Thunderbird if it is installed on your system.

Please run```
dpkg --get-selections | grep "thunderbird"
```and post the output here.

I don't mean to sound rude, but if you're knowledgeable enough to decide that a **security** update isn't needed right away perhaps Ubuntu is the wrong distro for you: Ubuntu is/was designed to be (somewhat) friendly to people new to Linux. 

Re. "There've been updates on other systems that I've declined", it isn't at all clear what you're talking about. Could you please clarify?

Re. "so why fill up my hard drive with them"? Recent (or all?) components of any update you **accept** and install are stored in /var/cache/apt/archives. There are command-line tools (*sudo apt-get autoclean* or *sudo apt-get autoclean*) to clean up that folder. I'm sure there's some GUI-way as well.

Oh, and if your questions are largely due to concerns over internet usage caps, I'd strongly suggest going for an "unlimited" plan.

---

### Post by chopra on 2014-10-20
Okay, thanks to everyone who posted quick replies. Each one gave usefull information.  I'm used to a windows mentality, so I didn't realize that it wouldn't bug you about stuff that's not on your system, or overcrowd your harddrive.


> **vasa1 said:**
> Whether you use or don't use Thunderbird, you will still get updates to Thunderbird if it is installed on your system.

Please run```
dpkg --get-selections | grep "thunderbird"
```and post the output here.

Here's the output:
```
thunderbird                    install
thunderbird-gnome-support            install
thunderbird-locale-en                install
thunderbird-locale-en-us            install
```

> **vasa1 said:**
> 
I don't mean to sound rude, but if you're knowledgeable enough to decide that a **security** update isn't needed right away perhaps Ubuntu is the wrong distro for you: Ubuntu is/was designed to be (somewhat) friendly to people new to Linux.

Re. "There've been updates on other systems that I've declined", it isn't at all clear what you're talking about. Could you please clarify? 

To clarify, I was referring to windows.  My computer would keep asking me to install facebook and other social media  "optional" applications (explicitly stated not to be security), and as I don't use facebook, I saw no need for them, so I didn't accept them.  But it kept bugging me until I finally relented.  There've also been updates windows tries to make that it can't because they apply to programs I don't have installed, and so it just keeps attempting the same update, failing, and then sending error messages, continually.

Chopra

---

### Post by craig10x on 2014-10-20
It's quite understandable, coming from windows, that you might have a cautious view about what you should or shouldn't let it install...but it is different (much different) here...it's fine to go ahead and let it install everything...won't cause any problems, overload your drive or install all kinds of junk stuff like can often happen in windows...this is linux (and ubuntu) as the aussies would say "no worries mate!" :D

---

### Post by vasa1 on 2014-10-20
Okay, so you do have Thunderbird installed and you'll keep getting offered updates. If you want to remove it, use the Software Center itself or use the command line --- whichever you're more comfortable with.

Re. your Windows experience, **and I could be wrong here**, you *may* see something similar here too if you're using the Unity DE. This has to do with the whole "integrated experience" Unity tries to offer. Anyway, people will help you sort things out: just be sure to provide the details they ask for and all will be well :)

Here's an oldish example of what could happen: [Chromium nags me to install Unity Webapps]("http://ubuntuforums.org/showthread.php?t=2128645"). I don't know if that situation still persists, but I remember seeing related issues.

---

### Post by sotiris2 on 2014-10-20
As far as I know you wil only be asked if you want to install the facebook/gmail/amazon/x webapp if you visit the corresponding website. However I don't think that windows updates (the windows OS part) would nag that kind of apps. Third party updaters (which every little program likes to stick to startup...) perhaps.  Ofcourse this may have changed with win8 and it's attempt to pretend it's a smartphone os.

---

### Post by chopra on 2014-10-25
Thanks guys.  Thread finally marked as solved, even though there was never really a problem to begin with.

---

