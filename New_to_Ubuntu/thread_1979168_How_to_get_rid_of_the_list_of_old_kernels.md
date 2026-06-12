---
title: "How to get rid of the list of old kernels"
date: 2012-05-12
forum: New to Ubuntu
---

### Post by Hwalker1 on 2012-05-12
I loaded Ubuntu some years ago on my laptop, thinking that it was a serious operating system, even though it was free. Now I have a list of what appears to be garbage all over my screen, and if I want to boot in windows to update my system, I have to scroll through about 30 entries. I made a complaint about it some time ago, and now and again, when anyone adds to the post, I get emails about what they are saying.
Unfortunately they talk in gobbledegook like "i did sudo add-apt-repository ppa:bugs-launchpad-net-falkensweb/remove-old-kernels"
This may mean something to a geek, but its meaningless to me. I just want to get rid of all the rubbish on my screen at startup and also, get rid of the large amount of software that is now being stored but not used on my hard disk. 
How does one edit a grub list? Indeed, what is a grub list?
How do you delete old kernals?
If these procedures were to be exxplained in a little detail then I might start to use Ubuntu for things that matter, rather than just playing games and reading the news, before I start serious work in Windows 7 on my main machine.

---

### Post by oldos2er on 2012-05-12
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

---

### Post by wilee-nilee on 2012-05-12
Install ubuntu-tweak it has a kernel cleaner.

[http://ubuntu-tweak.com/source/ubuntu-tweak-stable/](http://ubuntu-tweak.com/source/ubuntu-tweak-stable/)

You can remove them quite easily in synaptic, but if you are sketchy on that use the tweak.

I assume you are running Ubuntu or a release from canonical.

---

### Post by Hwalker1 on 2012-05-15
Well all that looks promising. However I still have not figured out what to do with what you call code - like sudo ....... etc.
What program do I use to enter the code into the computer and how do I run the code once its entered.
Like I said - I am just a user, not a programmer.:confused:

---

### Post by David Andersson on 2012-05-15
> **Hwalker1 said:**
> However I still have not figured out what to do with what you call code - like sudo ....... etc.

In the first post of [http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462) you have *two* choices and the instructions how to perform them: 1) "An Easy GUI Method - Ubuntu-Tweak" and 2) "Removing Kernels via Synaptic". (We forget about the third "Hiding Kernels via Grub Customizer".) 

Both instructions at some point ask you to enter a *command* into a *Terminal*. You can open a terminal with *Program>Accessories>Terminal* or press Ctrl-Alt-T (not sure if the same in Ubuntu 12.04).

Or you can avoid the terminal completely. The commands in the instructions for 2) "Removing Kernels via Synaptic" can be replaced with GUI tools. The first command "Code: uname -r" can be replaced with "Open System>Administration>System Monitor, go to tab System, note the version number in 'Kernel Linux x.x.xx-xx'." The other commands are optional (the GUI equivalent is mentioned before them).

(You may need to go to *Ubuntu Software Center* and install Synaptic, if it is not installed yet.)

---

### Post by Lisiano on 2012-05-15
Go ahead and download Ubuntu Tweak ([http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)), once it's done downloading, just double-click the file and Ubuntu Software Center will help you install it.
Then once you installed it, open it and go to a tab called Janitor, now just tick System -> Old Kernel and tick the kernels you don't want (Don't worry, the one you are currently using is not shown), I'd recomend you always leave 1 old kernel, for example if your previous kernel is 3.2.0-23 then you'd want to keep these 3 files
[LIST]
[*]linux-headers-3.2.0-23
[*]linux-headers-3.2.0-23-generic
[*]linux-image-3.2.0-23-generic
[/LIST]
After you are done picking, just press clean, type in your password, wait while it removes them and you are done.

---

### Post by Cavsfan on 2012-05-15
I keep a list of my kernels on a text (gedit) record [COLOR=Red]and just keep the 2 most recent kernels[/COLOR] along with the commands to remove and install them.

```
sudo apt-get purge linux-headers-2.6.32-37 linux-headers-2.6.32-37-generic linux-image-2.6.32-37-generic    - deleted
sudo apt-get install linux-headers-2.6.32-37 linux-headers-2.6.32-37-generic linux-image-2.6.32-37-generic 

sudo apt-get purge linux-headers-2.6.32-38 linux-headers-2.6.32-38-generic linux-image-2.6.32-38-generic    - deleted
sudo apt-get install linux-headers-2.6.32-38 linux-headers-2.6.32-38-generic linux-image-2.6.32-38-generic 

sudo apt-get purge linux-headers-2.6.32-39 linux-headers-2.6.32-39-generic linux-image-2.6.32-39-generic    - deleted
sudo apt-get install linux-headers-2.6.32-39 linux-headers-2.6.32-39-generic linux-image-2.6.32-39-generic

sudo apt-get purge linux-headers-2.6.32-40 linux-headers-2.6.32-40-generic linux-image-2.6.32-40-generic
sudo apt-get install linux-headers-2.6.32-40 linux-headers-2.6.32-40-generic linux-image-2.6.32-40-generic

sudo apt-get purge linux-headers-2.6.32-41 linux-headers-2.6.32-41-generic linux-image-2.6.32-41-generic
sudo apt-get install linux-headers-2.6.32-41 linux-headers-2.6.32-41-generic linux-image-2.6.32-41-generic linux-headers-generic linux-image-generic
```Notice that linux-headers-generic linux-image-generic also get deleted if you remove the most recent kernel. 
So, I am sure to add those back too if I remove it.

After going through the How To in my signature, This entered in terminal
```
grep menuentry /boot/grub/grub.cfg | cut -b 1-11 --complement | cut -d "'" -f1 | cut -d "\"" -f 1 | nl --starting-line-number=0
```yields this on my Grub menu:

```
     0    Ubuntu Lucid Lynx
     1    Ubuntu Lucid Lynx (Recovery Mode)
     2    Windows 7
```The top one will always boot into the latest installed kernel. If I would ever have to use the 2nd kernel, which I have never had to do, I would enter this into a terminal
**sudo chmod +x /etc/grub.d/10_linux && sudo update-grub**
Which changes my grub menu to display like this:
```
     0    Ubuntu Lucid Lynx
     1    Ubuntu Lucid Lynx (Recovery Mode)
     2    Windows 7
     3    Ubuntu, with Linux 2.6.32-41-generic
     4    Ubuntu, with Linux 2.6.32-41-generic (recovery mode)
     5    Ubuntu, with Linux 2.6.32-40-generic
     6    Ubuntu, with Linux 2.6.32-40-generic (recovery mode)
```

---

### Post by Paqman on 2012-05-15
> **Lisiano said:**
> I'd recomend you always leave 1 old kernel, 

A lot of people recommend this, and it's a good (if very conservative) line of thinking. In practice I've never, ever had a major kernel regression running a stable version of Ubuntu that meant I had to fall back on an old kernel.

Excess kernels are fairly large, so if you're at all squeezed for space I'd delete all but your current kernel. If you're running an alpha or beta I'd advise keeping at least one spare, as you're going to need it.

---

### Post by NikTh on 2012-05-15
Hi , 
just install Synaptic Package Manager . Open terminal (ctrl+alt+t) and write ```
sudo apt-get install synaptic
``` when installation complete find Synaptic and open it. 
Then in Search Box write "linux-image" and click at left the installed section. You will see all installed kernels. Right click and complete remove anyone you want EXCEPT that kernel that you are now. 
Do the same thing for linux-headers. 

Ubuntu tweak its a good automated tool for kernel remove but as Lisiano said > **Lisiano said:**
>  I'd recomend you always leave 1 old kernel, and i am not sure if Ubuntu tweak lets you choose your kernels you remove.. check it out.

---

### Post by grahammechanical on 2012-05-15
You play games in Ubuntu?

A lot of people who use Ubuntu for serious computer work say that they keep Windows just to play games.

Regards.

---

### Post by Lisiano on 2012-05-15
I personally keep at least 1 old kernel simply due to my nvidia driver not properly installing in the new kernel once (I think back in 9.10), so the only way I knew to get back and fix it was to use the old kernel. Exotic situation but better safe than sorry.

---

### Post by Cavsfan on 2012-05-15
> **Lisiano said:**
> I personally keep at least 1 old kernel simply due to my nvidia driver not properly installing in the new kernel once (I think back in 9.10), so the only way I knew to get back and fix it was to use the old kernel. Exotic situation but better safe than sorry.

I keep 2 also as you can tell from my previous post. I dual boot windows 7 so although I have the 2 
kernels, I can use windows 7 when needed.

One time my nVidia driver did bomb on me. It just made cairo-dock look like a useless rectangular block.
I just reinstalled the driver.

---

### Post by Face-Ache on 2012-05-15
> **David Andersson said:**
>  (We forget about the third "Hiding Kernels via Grub Customizer".) 

This is what i would personally recommend, and what i used to do the same thing as you'd like to do.

Synaptic would work, but it's a bit intimidating for a novice user, don't you think? Same with the command-line terminal advice.

Anyway, to install Grub Customizer, open the Ubuntu Software Centre, type in Grub, and Grub Customizer will come up as an option, click on it, and then click the Install button. Once it's installed, open the Dash (by either clicking on it in the top of the left-hand-side launcher menu, or hitting the 'Windows' key on your keyboard) and type in Grub, then click it.

It uses simple tick boxes that you can either tick or untick to determine which OS's show as boot options.

You can also rename these by clicking on the entry, so you don't get all the "...generic-19.0-PAE" stuff. My boot menu just says "Ubuntu 11.10" and "Windows XP Professional".

There's also another section of Grub Customizer, under Preferences and then the Appearances tab, where you can specify the font colours and a set whatever background picture you want to show at the 'choose OS' screen.

:)

---

### Post by Cavsfan on 2012-05-15
I don't think "hiding" as many kernels as Hwalker1 has installed is the correct answer. 
Each kernel takes up approximately 214MB and that can total up quickly.

What can be more simpler than typing this command into a terminal? 

**sudo apt-get purge linux-headers-2.6.32-37 linux-headers-2.6.32-37-generic linux-image-2.6.32-37-generic**

I would use Synaptic Package Manager to find the name of the kernel and then I would change 
the above commands as needed to delete each one.

I doubt if there are any special PAE kernels.

Myself, I use recovery once in a while to install a new nVidia driver.

The How to in my signature is intimidating at first but, it gets less the more you look at it.
I know not all the people that have viewed it have done it but, 24,000+ views means a lot of people have used it.

---

### Post by Face-Ache on 2012-05-15
As i say, some people find the whole Terminal Command Line Interface method to be quite intimidating.

The OP has said "I loaded Ubuntu some years ago on my laptop" - so if these kernels haven not been a problem for 'some years' i don't see how the space that they take up would suddenly be an issue now.

Remember, they are asking on how to get rid of the *_**list**_* of old kernels, not the kernels themselves. I believe i'm suggesting the easiest and most user-friendly way in which to do that.

Your opinion differs, and i'm totally okay with that :)

---

