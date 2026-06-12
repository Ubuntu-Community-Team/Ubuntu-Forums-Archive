---
title: "photo management"
date: 2014-04-05
forum: New to Ubuntu
---

### Post by bazza57 on 2014-04-05
Hi, I have just had linux mint installed and I need to be able to email photos to friends.
I read Shotwell was ok so I went to the website and hit the Download button.....I presume it loaded but I see no sign of it, how do i access it or put it on my desktop for easy access?
Its all new to me so please use detailed instuctions and simple terms please, regards Barry.

---

### Post by PartisanEntity on 2014-04-05
I am not sure what the DE looks like on Linux Mint, but you could open up the terminal and simply type: shotwell

---

### Post by sikander3786 on 2014-04-05
Hi. Welcome to the Ubuntu Forums! :D

I am not using Linux Mint currently so can't say if Shotwell is present there by default or not. It is present in Ubuntu's official variants though.

For installing software in Ubuntu and its derivatives, you should preferably use the Software Manager included in the installation which in Ubuntu's case is Ubuntu Software Center. For Linux Mint, I guess it is Software Manager. Again, I can't be sure as I have never used Linux Mint.

Anyhow, the global method across all Debian based Linux distros is to use "apt-get" for installing software. To use it you will need to open up a "Terminal" window and run this command:

```
sudo apt-get install shotwell
```

It will ask for your password. Just type your password and hit <Enter> as the Terminal won't return any feedback as you type the password.

Once installed, the software will appear in your application menu which you can drag and drop to your desktop for easy access.

You should be using the repositories (both apt-get and software manager download from the repos) for installing new software instead of downloading the software from developer websites. This way, you won't need to install it manually after downloading and you will always be updated to new versions automatically.

---

### Post by Rob Sayer on 2014-04-06
So I guess you're another Mint user posting here because mint tech support forum is so bad.  I sympathize ... I've been DE and distro hopping on my netbook, on which ubuntu 12.04 doesn't work as well as later versions, until 14.04 comes out.

I had Mint 16  with the MATE desktop(ubuntu 13.10 based) for a while not long ago.  The pesky wireless was working OK but still iffy sometimes.  I needed a backport.  Found it by searching here ... good luck with that stuff on the Mint forums.

Which is why I'm running Lubuntu 13.10 on it now ...

First, "linux mint" isn't enough info.  The release matters too, and if you want to search/ask here you'll need to know which ubuntu version your mint is based upon.

Generally if you go to a site and just download something all it'll do is dl a tar file.  This isn't noob friendly and there should be an easier way.  The developer's site generally has the latest release.  This is only really a good idea if you're using the latest ubuntu release.

Try looking in mint software centre or synaptic package manager.

---

### Post by bazza57 on 2014-04-07
...thanks for your  replys...I got a computer shop to install Linux so I may have to go back to them to get some software installed to enable me to email pics.
I should say the Linux program is smooth to use and apart from the photo emailing issue, I like it,  Barry.

---

