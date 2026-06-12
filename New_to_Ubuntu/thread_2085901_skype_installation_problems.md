---
title: "skype installation problems"
date: 2012-11-19
forum: New to Ubuntu
---

### Post by sailashr on 2012-11-19
while installing i get messaeges
 sudo apt-get update && sudo apt-get install skype
"Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 skype : Depends: skype-bin but it is not installable
E: Unable to correct problems, you have held broken packages."

can any one help. iam using intel

---

### Post by dannyboy79 on 2012-11-19
it appears like it's telling you that you have some package "stickied" and it's broken. You sticky packages when you don't want them to upgrade. I believe this to be true from reading the following statement, 
"E: Unable to correct problems, you have held broken packages."

So, are there any packages that you installed that you have "held" at their current version?

---

### Post by jeremy on 2012-11-22
I have the same problem as sailashr, and do not have any sticky packages.

---

### Post by squakie on 2012-11-22
What I would try:

sudo apt-get remove skype

sudo apt-get purge skype

Then go to the software center and install it there.  Each time I've done a clean install with a new release that's all I've ever done (prior to software center I used synaptic package manager) and it's worked fine each time.

After you've done that if you still have problems please post back.

---

### Post by dniMretsaM on 2012-11-22
Make sure you have the partner repository enabled. You can open up [FONT=Courier New]/etc/apt/sources.list[/FONT] in a text editor and uncomment said repo. There is also a way to do through the USC, but I don't know since I'm not on Ubuntu.

---

### Post by Impavidus on 2012-11-22
Today I also had a problem updating skype-bin. It says: "Unable to update," altough a new version is available, it always worked out in the past and I haven't changed anything to the apt configuration lately. Synaptic tells me that to upgrade to the latest version of skype-bin I have to remove the package "skype", but according to the version numbers it should work fine (version 4.1.0.20-0ubuntu0.11.10.1).

It's not  security update, so I'll leave it for the moment. It sounds like some faulty dependencies. For the moment I'll assume it will be solved by a future update.

(The "skype" package doesn't really contain anything, so it should be fine to remove it and just install skype-bin.)

---

### Post by Paddy Landau on 2012-11-22
I am using the latest version from the official Skype website. To do this, you first have to remove existing Skype packages.

You need to remove all installed Skype packages, including (if installed) skype-bin and skype:i386.

You can do this from Ubuntu Software Centre, Synaptic, or from the terminal:
```
sudo apt-get remove skype*
```Then download the Linux deb from the [Skype Linux download page]("http://www.skype.com/intl/en-gb/get-skype/on-your-computer/linux/") and install it. It seems to work perfectly.

---

### Post by Impavidus on 2012-11-23
> **Impavidus said:**
> It's not  security update, so I'll leave it for the moment. It sounds like some faulty dependencies. For the moment I'll assume it will be solved by a future update.
The problem solved itself today with a new update. If you still haven't skype working, try again installing from the software centre.

---

### Post by NikTh on 2012-11-23
Anyone who has problem with the message > skype : Depends: skype-bin but it is not installable
E: Unable to correct problems, you have held broken packages." 

could try this 
```
sudo apt-get install skype-bin
```

Thanks

---

### Post by Paddy Landau on 2012-11-23
> **NikTh said:**
> ```
sudo apt-get install skype-bin
```
In my case, skype-bin is not in the repositories.

> **Impavidus said:**
> The problem solved itself today with a new  update. If you still haven't skype working, try again installing from  the software centre.
I also received the upgrade, even though I had installed from the Skype website.

As a test, I uninstalled Skype and installed the standard one from the repository, and it worked. It automatically installed both [FONT=Lucida Console]skype[/FONT] and [FONT=Lucida Console]skype-bin:i386[/FONT] (the latter was not visible before installing).

It is interesting that Canonical has approved an upgrade so quickly for Skype; that is quite unusual.

The OP (sailashr) has not responded, but this thread could probably be [marked as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

