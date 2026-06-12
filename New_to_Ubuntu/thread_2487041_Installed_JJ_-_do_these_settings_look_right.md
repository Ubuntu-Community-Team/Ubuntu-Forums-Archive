---
title: "Installed JJ - do these settings look right?"
date: 2023-05-21
forum: New to Ubuntu
---

### Post by nowindows2 on 2023-05-21
I removed Windows 10 and installed Ubuntu Jammin' Jellyfish on an old laptop and the install seems to be successful, but I'm not familiar with Linux and some things look odd.  I'm hoping someone might let me know everything's okay, especially the FF settings. I haven't hooked up to the Internet yet.

**First screenshot:**
The " C Drive" tmp folder. I didn't try all the folders but the ones I tried, I was able to access the folders with my password. It's the whole red X/private verbiage that looked odd.

**Second screenshot(s)**
The Firefox browser settings are a bigger concern. Only certain toggles are able to be turned off, and some toggle back on with 10-15 seconds.  The last 5 toggles in the second screenshot won't toggle off at all.

**Third screenshot:**
I'm not able to "unset" any of the options. Is this normal?

As always, thanks for your time!!

---

### Post by aljames2 on 2023-05-21
Hi and welcome to Ubuntu

The snap version of Firefox is more locked down (sandboxed), from what you are likely used to.  The snap version is the default on new Ununtu installations.  Snap FF is good &#8220;out of the box&#8221; for casual users who just want a secure browser to do browser stuff, but not so much for a power user, without some customizations.  The snap version does not allow access to other folders on your system, by design.  Some users are fine with this, while others choose to replace the snap version with a repository version, or a manually executable version.  There are lots of posts in these forums and elsewhere on the pros and cons of snap firefox and how to use other versions of it.

---

### Post by nowindows2 on 2023-05-21
Thanks for the welcome :cool:

Which is the best option for a newb?  I'm not lazy - just a bit lost. Well, maybe more than just a bit.  

I'm leaning towards the manual FF download, but will it override the default Snap version? If not, what's the best way to remove snap?

I'll look around for the other threads now that you've pointed me in the right direction. Your advice is greatly appreciated! Thanks!

---

### Post by tea for one on 2023-05-21
> **nowindows2 said:**
>  I haven't hooked up to the Internet yet.
Rather than worry about any Firefox settings at the moment, why not hook up to the internet and see if there is a problem?
You may be pleasantly surprised?

---

### Post by Impavidus on 2023-05-22
Good that you put "C Drive" in quotes. Linux doesn't use drive letters. That thing is known in Linux as the root directory (when viewing it as the base of your filesystem) or root partition (when viewing it as a chunk of your hard drive).

Linux is designed from the very start as a multi user system. I use a different file manager (I'm on Xubuntu), but I think those locks in the directories indicate that you can't edit the directories (add, remove or rename files or directories), the crosses indicate that you can't view the contents. In this case, only the owner of the directories can, and that is the root user. You're not the root user, but, being the admin of your system, you have the right to act as the root user. You have to type your password and the permission only lasts 15 minutes. (Processes you start as root user will continue as such until they terminate, even after those 15 minutes.)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Firefox is normally installed as a snap package instead or the normal deb packages. Programs from deb packages normally have permissions identical to those of the user starting them, but snap packages can be more limited. The packager can decide what permissions the program has, what permissions it hasn't and what permissions are for the user to decide. You were looking at the tool to configure snap packages.

I used the Firefox snap for about 7 months before I decided to revert to the deb. The main reason was that some official Ubuntu packages come with documentation in html format stored in /usr/share/doc/, which the snap Firefox cannot access, making the official documentation unreadable with the official browser. I switched to Firefox from the Mozilla Team PPA.
[https://ubuntuhandbook.org/index.php/2022/04/install-firefox-deb-ubuntu-22-04/](https://ubuntuhandbook.org/index.php/2022/04/install-firefox-deb-ubuntu-22-04/)

---

### Post by nowindows2 on 2023-05-22
I made the screenshot too small, butoOne of the toggle  options in the first screenshot is  "allow access to personal files or directories". That didn't sound right. I've never installed Linux before, and if there were a problem, once I'm on the Net it's too late.

---

### Post by nowindows2 on 2023-05-22
Thanks for the info and thanks for the links - esp the FF link. Bookmarked them both and will try replacing the snap version later today.

Thanks again!

---

### Post by deadflowr on 2023-05-22
> **nowindows2 said:**
> I made the screenshot too small, butoOne of the toggle  options in the first screenshot is  "allow access to personal files or directories". That didn't sound right. I've never installed Linux before, and if there were a problem, once I'm on the Net it's too late.

How else would you expect to download and save files from the internet without giving Firefox proper access to save said files?
That is what that means. it's gives Firefox the access it might need to either download and save files, or upload files from your home folder.
You, of course, are free to turn that off if you feel you will never need it. As you are free to turn off any of the settings listed.

---

### Post by Impavidus on 2023-05-22
To emphasise this: the snap version of Firefox is more secure than other versions, but less convenient. Wherever the snap version has access, the other versions have access too.

---

### Post by nowindows2 on 2023-05-23
Thanks, but the reason for the post was that I'm _not_ able to toggle off some of the settings. I just wanted to check that I did the downolad/install correctly and didn't end up with a virus.

---

### Post by nowindows2 on 2023-05-23
> **Impavidus said:**
> To emphasise this: the snap version of Firefox is more secure than other versions, but less convenient. Wherever the snap version has access, the other versions have access too.


So much to learn, so few brain cells. I don't mind some inconvenience if it improves security. I'll leave the snap version.

Thanks for all your help!

---

