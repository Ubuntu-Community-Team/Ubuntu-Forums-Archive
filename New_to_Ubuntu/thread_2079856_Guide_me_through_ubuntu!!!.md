---
title: "Guide me through ubuntu!!!"
date: 2012-11-02
forum: New to Ubuntu
---

### Post by Ububtuser44 on 2012-11-02
I am a new user to ubuntu. Was using windows for the past 6yrs. Now I want to get into linux to learn it and use it. But I feel lost when I get into the interface. I just can't know what to do. I installed Ubuntu 12.10 and currently using Xubuntu 12.10 due to my old computer hardware. In both the OS's I get lost on the basics like installing software, using terminal, using the interface as I wish etc. So my questions are:

1- How is Xubuntu different from Ubuntu and can I be fluent in Ubuntu if I am good at handling Xubuntu? 

2- Can the softwares that Ubuntu support be installed in other Ubuntu lightweights (X ,L) ? All software in Ubuntu software centre are not found in Xubuntu software centre.

3- I want to begin learning to handle Ubuntu and sisters. From where to start and lay the foundations? And what can I do to absolutely master the OS? (any websites, books, ebooks, or any material link)

4- Is virtualbox in windows a good idea to learn the OS. What are the advantages/disadvantages associated with it? Using Oracle VM with Pentium G630 2.7Ghz processor, 2gb Ram.


Any advice is greatly appreciated.

---

### Post by ibjsb4 on 2012-11-02
Ill do #1

The big difference is Xubuntu uses the xfce desktop and Ubuntu uses the unity desktop.  I think you will find that the software center in both are identical.  Could be wrong on that, but think not.  You can install all the different desktops (lfxe; xfce; gnome) on one install and try them all out.  Just pick the one you want to use at login.

---

### Post by pkadeel on 2012-11-02
Yes virtualbox is no doubt a very good tool to install linux in it and learn without affecting your day to  day computer requirements.

I have not used Xubuntu and Lubuntu but my guess is that you should be able to use most of the softwares easily in any of the buntu family member.

For people shifting from windows, like me shifting to linux recently, yes there is initially a problem of dis-orientation & finding things even the close, minimize and maximise buttons get lost in the global menu LOL but in a couple of days you will adjust. I without any exaggeration tried 5 different distros within 2 days just to find that no matter which distro I use, it will not be windows.

Spend an hour or  two exploring the menus and applications and soon you will be quite familiar with locations where to find things.

---

### Post by Ububtuser44 on 2012-11-02
> **pkadeel said:**
> Yes virtualbox is no doubt a very good tool to install linux in it and learn without affecting your day to  day computer requirements.

I have not used Xubuntu and Lubuntu but my guess is that you should be able to use most of the softwares easily in any of the buntu family member.

For people shifting from windows, like me shifting to linux recently, yes there is initially a problem of dis-orientation & finding things even the close, minimize and maximise buttons get lost in the global menu LOL but in a couple of days you will adjust. I without any exaggeration tried 5 different distros within 2 days just to find that no matter which distro I use, it will not be windows.

Spend an hour or  two exploring the menus and applications and soon you will be quite familiar with locations where to find things.

The GUI menus are okay, but the main problem I face is installing software, updates, finding drivers etc. Like the adobe flash layer isn't available on the software center. So i downloaded the tar file. And I have no idea how to execute it, then look the internet and the terminal etc. The sudo get command goes just overhead. Is there a general procedure for software installation or it varies by software.

---

### Post by techvish81 on 2012-11-02
> **Ububtuser44 said:**
> The GUI menus are okay, but the main problem I face is installing software, updates, finding drivers etc. Like the adobe flash layer isn't available on the software center. So i downloaded the tar file. And I have no idea how to execute it, then look the internet and the terminal etc. The sudo get command goes just overhead. Is there a general procedure for software installation or it varies by software.





just install 'xubuntu restricted extras ' from the software centre/ synaptic package manager,  it will be a big download but you will not have to worry about installing  several media codecs.  it will install flash and all major codecs.  the package to be installed would be 'ubuntu restricted extras' if you are running ubuntu.  


and do keep in mind that linux is not windows,  keep reading things and try google for your problems, you will be fine in a week and will certainly start enjoying linux. 

cheers!

---

### Post by mike555 on 2012-11-02
You should ONLY install from the package manager , Flash is having lots of problems lately, you should not use it unless you absolutely need it..

---

### Post by snowpine on 2012-11-02
The secret to Linux is that the things that are easy in Linux are INCREDIBLY EASY if you do them the right way.

Example: "How do I install Flash in Ubuntu?"
Incredibly Easy Way: 
1. google "flash site:ubuntu.com"
2. this page is the first hit, notice the link is from ubuntu.com so it can be trusted: [https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)
3. follow the easy instructions
4. if you have any problems/errors then post back here and **copy & paste the errors so we can help you**

Linux is only difficult if you choose to do things that are difficult in Linux, or if you choose to do things that are incredibly easy (but then don't do them the incredibly easy way). Examples of common mistakes beginners often make instead of doing things the incredibly easy way: following a how-to from some random guy's blog, downloading software from some random guy's website, trying to use hardware/software not supported by Ubuntu, using an old Ubuntu release that is obsolete, etc.

---

### Post by evilsoup on 2012-11-02
Flash is in the repositories (that's the servers the Ubuntu Software Centre downloads software from), you should be able to find it in the software centre by searching for 'flash'. You'd probably be best off installing the ubuntu-restricted-extras package (this includes flash, MP3 support, and some other things). See [these](http://www.psychocats.net/ubuntu/nonfree) instructions.

---

### Post by pkadeel on 2012-11-02
> **Ububtuser44 said:**
> The GUI menus are okay, but the main problem I face is installing software, updates, finding drivers etc. Like the adobe flash layer isn't available on the software center. So i downloaded the tar file. And I have no idea how to execute it, then look the internet and the terminal etc. The sudo get command goes just overhead. Is there a general procedure for software installation or it varies by software.

General procedure for installing softwares is through "Software Centre" application present on all buntu family OSs. Alternately many people install "Synaptic Package Manager" which is more detailed but I don't recommend using it even if you have it on your computer just because I now windows users are familiar with double clicking setup.exe file and it handles every thing where as in Synaptic Package Manager you will get lost easily.

I had specific software needs but found 80% softwares preinstalled and found the another 18% in the Software Centre. Had to download only only 2% manually and again just because I needed latest version of those softwares otherwise old versions were present in the Software centre.

---

### Post by ibjsb4 on 2012-11-02
> **mike555 said:**
> You should ONLY install from the package manager , Flash is having lots of problems lately, you should not use it unless you absolutely need it..

The flash package is no longer offered.  Interesting though that the flash installer is still there.

[http://packages.ubuntu.com/quantal/xubuntu-restricted-addons](http://packages.ubuntu.com/quantal/xubuntu-restricted-addons)

---

### Post by Abhinav Kumar on 2012-11-02
**Installing software**: Use Ubuntu Software center to install softwares but you can also do this by using terminal. 
For manually downloaded packages first go to the desired folder using cd command and then execute the following commands according to the package
1.For deb packages, type
```
sudo dpkg -i packageName
```2.For shell scripts, type 
```
sudo chmod +x fileName.sh
./fileName.sh

```[B]
Updates :[/B] Ubuntu - Linux for Human Beings! Ubuntu is purely an open source philosophy and so its updates are absolutely free ....:P So a simple best way to update is to type in terminal```
sudo apt-get update
``` and then give root password. Remember sudo stands for Super User DO.

**Finding Drivers: **Just type drivers in your unity dash and ubuntu will automatically tell you what hardware drivers you need.

**Install Flash**- A simple procedure would be 
Go to adobe site 
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
and download flash player as tar file. (tar is a compressed file format like rar)
Now extract the contents of tar file using archive manager.
say you extracted and you created folder named install_flash at the Desktop.
You can see there will be a file named libflashplayer.so in install_flash folder.
execute the following command in terminal
```

sudo cp ~/Desktop/install_flash/libflashplayer.so /usr/lib/mozilla/plugins/

```and then give the password.
restart firefox

**Learning commands **: Say you want to know about a command
Type in terminal ```
man commandName
```. Search the net and you will get to know a lot of commands Remember linux is much more powerful. You will definitely love it once you start using it:P

---

### Post by snowpine on 2012-11-02
Be careful, **Ububtuser44**--there is no test or requirement to post here on UbuntuForums. Don't just blindly follow instructions that someone posts! If you aren't sure what a command does, then always double-check it at help.ubuntu.com or wiki.ubuntu.com. I usually don't recommend non-Ubuntu sites, but this one is good too: [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Personally I wouldn't even dream of following some other random website how-to until I had researched my question at the three sites above plus ubuntuforums.org. :)

---

### Post by ajgreeny on 2012-11-02
> **mike555 said:**
> You should ONLY install from the package manager , Flash is having lots of problems lately, you should not use it unless you absolutely need it..
That is a very oversimplified reply to the question.

So many websites require flash in to see or hear them fully that it is almost pointless saying don't use it unless you really need it, and  html5 is not yet universal and therefore as an alternative is of little use.

In my opinion, for what it's worth, flash is still an absolute necessity for web use.

---

### Post by snowpine on 2012-11-02
It's funny, I installed Debian yesterday, and I haven't installed Flash yet, and still I have no problem reading Gmail, posting on Facebook, watching Youtube, etc... interesting that Debian has this capability and its child Ubuntu does not.

---

