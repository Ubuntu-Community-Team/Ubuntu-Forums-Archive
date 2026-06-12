---
title: "Help setting up Unity Mail"
date: 2017-02-11
forum: New to Ubuntu
---

### Post by DOHCme on 2017-02-11
I've been trying to setup Unity Mail, but when I input my account user-name/password it wont let me press Apply and save it, only cancel. Any idea what I'm doing wrong? Using 16.04LTS and kinda new at this...

---

### Post by Frogs Hair on 2017-02-11
Is it the linked Unity Mail ?
[http://www.omgubuntu.co.uk/2016/09/install-unity-mail-ubuntu-16-04-ppa](http://www.omgubuntu.co.uk/2016/09/install-unity-mail-ubuntu-16-04-ppa)

---

### Post by DOHCme on 2017-02-11
Yes, thats the one.

---

### Post by DOHCme on 2017-02-11
[ATTACH=CONFIG]273651[/ATTACH]

I can't advance from this screen. When I press the Apply button, nothing happens.

---

### Post by mc4man on 2017-02-11
The build is broken. Maybe wait till next build or if you really want then this is last build to work - 
[https://launchpad.net/~robert-tari/+archive/ubuntu/main/+build/11971063](https://launchpad.net/~robert-tari/+archive/ubuntu/main/+build/11971063)
You'd download &  install it with apt, first run 
```
sudo apt purge unity-mail
```
 then like example - 
> sudo apt install ./Downloads/unity-mail_1.6.4.44~ubuntu16.04.1_all.deb

---

### Post by TariBuntu on 2017-02-12
Hello, Unity Mail here.

I have stumbled here by chance, so I thought I'd comment...
I am not aware of anything I may have broken recently, but should that be the case, report it immediately:

[https://bugs.launchpad.net/unity-mail/+filebug](https://bugs.launchpad.net/unity-mail/+filebug)

Another thing: downloading .deb packages from the internet is never a wise practice (as I used to tell my kid, "Spit it out you have no idea where it's been"). Add a repository, thus you'll have regular updates and safety above all. Here's where Unity Mail lives:
```

sudo add-apt-repository ppa:robert-tari/main
sudo apt-get update && sudo apt-get install unity-mail
```

---

### Post by mc4man on 2017-02-12
> **TariBuntu said:**
> Hello, Unity Mail here.

I have stumbled here by chance, so I thought I'd comment...
I am not aware of anything I may have broken recently, but should that be the case, report it immediately:

[https://bugs.launchpad.net/unity-mail/+filebug](https://bugs.launchpad.net/unity-mail/+filebug)

Another thing: downloading .deb packages from the internet is never a wise practice (as I used to tell my kid, "Spit it out you have no idea where it's been"). Add a repository, thus you'll have regular updates and safety above all. Here's where Unity Mail lives:
```

sudo add-apt-repository ppa:robert-tari/main
sudo apt-get update && sudo apt-get install unity-mail
```

here - [https://bugs.launchpad.net/unity-mail/+bug/1664098](https://bugs.launchpad.net/unity-mail/+bug/1664098)

Just to make clear, there is nothing wrong with latest 2 packages as far as running, they work fine.
It's only if unity-mail had never been setup before, then the current & previous both fail to allow a setup.
If one used the package I mentioned then the setup would work, at that point the 2 latest versions/packages would be ok..

(- it would be nice to know how to totally clear account info & where or how does unity-mail store that info.

---

### Post by lisati on 2017-02-12
Have you tried **imap.googlemail.com** instead of **imap.gmail.com**? I think googlemail/gmail also likes to have your complete email address as "myusername."

---

### Post by TariBuntu on 2017-02-12
> **lisati said:**
> Have you tried **imap.googlemail.com** instead of **imap.gmail.com**?

No, the settings are correct, there is a bug in the app. I am working on it right now.

---

### Post by lisati on 2017-02-12
> **TariBuntu said:**
> No, the settings are correct, there is a bug in the app. I am working on it right now.

That's ok, just checking....I was going by what Thunderbird uses for one of my gmail accounts, sometimes email providers have aliases and the like for their servers.

---

### Post by DOHCme on 2017-02-13
> **TariBuntu said:**
> No, the settings are correct, there is a bug in the app. I am working on it right now.

Thanks - looking forward to testing this out

---

### Post by TariBuntu on 2017-02-13
> **DOHCme said:**
> Thanks - looking forward to testing this out

Fixed. There have been a lot of changes recently, and there is a lot planned for the near future. I am a one person development team, so I am bound to overlook something once in a while. You just make a bug report on Launchpad if anything should seem off.

---

### Post by DOHCme on 2017-02-13
Reinstalled it and had a crash when I tried to apply account settings, but gave it another shot and now its working! Thanks again.

---

### Post by lisati on 2017-02-13
Kudos to you guys for making good progress.

If you're happy that things are working as they should, and believe the issue to be solved, feel free to mark the thread "solved" with "Mark the thread solved" option on the "Thread tools" drop down menu near the top of the page.

---

