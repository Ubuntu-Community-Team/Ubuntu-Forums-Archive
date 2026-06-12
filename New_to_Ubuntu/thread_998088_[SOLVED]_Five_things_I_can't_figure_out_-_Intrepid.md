---
title: "[SOLVED] Five things I can't figure out - Intrepid"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by wc4r on 2008-11-30
I'm an advanced Windows users but new to Ubuntu 8.10. I hate the necessity to work with terminal but I like Linux so much so far that I'll deal with it.

There are 5 things I don't like and I bet there is a way to change them. Unfortunately, I can't come up with the answer by poking around or doing a search.

1. System sounds. I went to System > Preference > Sound to change some defaults using some wav files I have. They test fine but they do not run when they should (ie new mail or OS boot).

2. Keyring password. I find this annoying. Everytime I open Evolution, it asks for the password. I'd like this to go away. I tried some posted suggestions but they did not work.

3. Admin password. Like # 2 above, when running an administrator task, I need to enter the password. I'd like this to go away.

4. 3/4 GB RAM. I have 4 GB RAM installed. The BIOS and Win VISTA recognize it fine. Ubuntu does not. Why? Is this disto of Linux limited to using 3 GB of memory? Can I make it use the 4 GB available?

5. Dual boot screen. The initial dual boot screen to choose the OS is not in my preferred order. I know I can edit the lines but I wish to edit the order of the choices; maybe even delete a choice too. I can't locate the file for this.

Oh, I run Linux and Vista on a Dell 8400, 3.0 dual core, dual 320 GB HD (one for each OS), & two DVR-RW drives.

Thanks all for the support!
Joe

---

### Post by CatKiller on 2008-11-30
> **wc4r said:**
> I'm an advanced Windows users but new to Ubuntu 8.10. I hate the necessity to work with terminal but I like Linux so much so far that I'll deal with it.

You don't need to use the Terminal that much. As you'll come to find, Ubuntu is extremely customisable. Which means that the "click on this, click on that, press the blue thing..." style of instruction is ambiguous as well as unnecessarily lengthy.

Terminal commands are both quick to give, and quick to paste onto the command line, are unambiguous, and are applicable no matter which Desktop Environment the user uses. And you'll get feedback on what's happening should things go wrong.

Some things **are** just quicker on the command line, though.

> 5. Dual boot screen. The initial dual boot screen to choose the OS is not in my preferred order. I know I can edit the lines but I wish to edit the order of the choices; maybe even delete a choice too. I can't locate the file for this.

```
sudo nano /boot/grub/menu.lst
``` The file itself has information on how it can be edited, but there is also a host of information on this forum and the Internet generally about how to edit your menu.lst.

---

### Post by madsmeg on 2008-11-30
Not wanting to step on your toes CatKiller, but i think gedit would be easier to work from if he is coming from a windows background

so it would be ```
sudo gedit /boot/grub/menu.lst
```

As regards to removing the fact it asks for your password all the time... there are many debates about this, short answer is its far safer the way it is, and coming from Vista, you should be used to this anyway :)

---

### Post by nothingspecial on 2008-11-30
> 3. Admin password. Like # 2 above, when running an administrator task, I need to enter the password. I'd like this to go away.

So would a hacker or some piece of malicious software trying to install itself on your system.

Seriously,  this forums code of conduct prevents anyone from telling you. And if you need to ask, well maybe you shouldn`t know the answer.

Don`t know about your Ram, I only have 1gig.

As for the others, what have you tried. A little more info would help. This is why it is the done thing to use a different thread for a different question. That way someone who knows the answer is more likely to see it and help.

Good luck by the way.:)

---

### Post by nhasian on 2008-11-30
Windows may tell you that you *have* 4 gigs of ram, but it can only use 3 gigs.  its a limitation of the 32bit OS.  only 64 bit Operating systems can use all 4 gigs like Windows Vista Ultimate 64 or Ubuntu 8.10 64bit version.

I know your used to windows, but its really in your best interest to have to use a super user password when making a change that affects the system.  it remembers the password for 10 or 15 minutes so you dont have to keep entering it over and over.  

> **wc4r said:**
> 

3. Admin password. Like # 2 above, when running an administrator task, I need to enter the password. I'd like this to go away.

4. 3/4 GB RAM. I have 4 GB RAM installed. The BIOS and Win VISTA recognize it fine. Ubuntu does not. Why? Is this disto of Linux limited to using 3 GB of memory? Can I make it use the 4 GB available?


---

### Post by CatKiller on 2008-11-30
> **madsmeg said:**
> Not wanting to step on your toes CatKiller, but i think gedit would be easier to work from if he is coming from a windows background

Ah, but only if he's using Gnome. If he were using KDE (Kubuntu) he'd use ```
kdesu kate /boot/grub/menu.lst
``` If he were using Xfce (Xubuntu) he'd use something else - is it mousepad in Xubuntu? It's not just this person we're trying to help, but also all the other people who find this thread because they have a similar problem. Hence my comments about the Terminal above. It would be **[gksudo]("http://www.psychocats.net/ubuntu/graphicalsudo")**, btw, if he were to use GEdit.

---

### Post by gandaran on 2008-11-30
> 2. Keyring password. I find this annoying. Everytime I open Evolution, it asks for the password. I'd like this to go away. I tried some posted suggestions but they did not work.

this one is easy
open passwords  and keys (applications » accessories) go to edit » preferences, delete/remove the current keyring (could be default) profile and close the application 
next time you open evolution and it asks for you to set password don't enter any, just hit okay or use the unsecured option, it'll never ask you again for keyring password!

---

### Post by nothingspecial on 2008-11-30
> 1. System sounds. I went to System > Preference > Sound to change some defaults using some wav files I have. They test fine but they do not run when they should (ie new mail or OS boot).


See this bug, it seems to be related to your problem.

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/176898](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/176898)

Don`t know if there`s a definitive answer yet.

---

### Post by gandaran on 2008-11-30
> 5. Dual boot screen. The initial dual boot screen to choose the OS is not in my preferred order. I know I can edit the lines but I wish to edit the order of the choices; maybe even delete a choice too. I can't locate the file for this.
for this one install startup-manager in synaptic, it makes choosing which operating system to boot first easy
don't delete anything in boot grub menu list, if you want to get rid of some old kernels in the boot grub list just remove them using synaptic package manager

---

### Post by kansasnoob on 2008-11-30
> **wc4r said:**
> I'm an advanced Windows users but new to Ubuntu 8.10. I hate the necessity to work with terminal but I like Linux so much so far that I'll deal with it.

There are 5 things I don't like and I bet there is a way to change them. Unfortunately, I can't come up with the answer by poking around or doing a search.

1. System sounds. I went to System > Preference > Sound to change some defaults using some wav files I have. They test fine but they do not run when they should (ie new mail or OS boot).

2. Keyring password. I find this annoying. Everytime I open Evolution, it asks for the password. I'd like this to go away. I tried some posted suggestions but they did not work.

3. Admin password. Like # 2 above, when running an administrator task, I need to enter the password. I'd like this to go away.

4. 3/4 GB RAM. I have 4 GB RAM installed. The BIOS and Win VISTA recognize it fine. Ubuntu does not. Why? Is this disto of Linux limited to using 3 GB of memory? Can I make it use the 4 GB available?

5. Dual boot screen. The initial dual boot screen to choose the OS is not in my preferred order. I know I can edit the lines but I wish to edit the order of the choices; maybe even delete a choice too. I can't locate the file for this.

Oh, I run Linux and Vista on a Dell 8400, 3.0 dual core, dual 320 GB HD (one for each OS), & two DVR-RW drives.

Thanks all for the support!
Joe

#1. Unfortunately the transition to pulse audio has NOT been flawless, but it can be dealt with. Look here: 

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

#2 & #3. Annoying? I select a fairly easy password for myself based on fig 27 fat here:

[http://users.bigpond.net.au/hermanzone/p2.htm](http://users.bigpond.net.au/hermanzone/p2.htm)

It's a little better than halway down the page.

But if you should decide to do so you can change things by editing sudoers. Basic info here:

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

NOTE: I strongly recommend NOT doing this!

#4. I'm clueless!

#5. Install Startup Manager. It's in Synaptic so you can go to System > Administration > Synaptic Package Manager and then in the Search tool type startupmanager (as you use Synaptic you'll find there are never upper case letters or spaces but the normal search tool does quite well with "partial" descriptions, like in this case you could type manager and then scroll down to the s's).

Or if you want to use the terminal just:

```
sudo apt-get install startupmanager
```

You'll then find it in System > Administration > StartUp-Manager. On this screen you can see I clicked on the toggle to select default OS:

[ATTACH]94728[/ATTACH]

Just a note, and since you're an experienced Win user you already know, make limited changes at one time and keep track of what you've done. That way it's easily reversed!

As far as deleting a choice, if the choice is an older Linux Kernel you can click on the Advanced tab and select how many Kernels to "keep". I set mine on "1" but anytime I have a Kernel update I de-select that option or change it to "2" until I'm sure the new Kernel works well with my hardware.

Otherwise you can edit the Menu List, but it's seldom necessary.

---

### Post by kansasnoob on 2008-11-30
Just a note: 

This post was just fine, so don't take it as criticism, but in the future it's good practice to post separate threads regarding separate problems.

Most of us have extensive knowledge in certain areas, while limited or no knowledge in others so it's nice to see a thread titled in a manner that draws the interest of the right folks.

Also this is a great (and very dependable) link:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Welcome, and enjoy!

---

### Post by SunnyRabbiera on 2008-11-30
> 1. System sounds. I went to System > Preference > Sound to change some defaults using some wav files I have. They test fine but they do not run when they should (ie new mail or OS boot).
Here I cannot help you with, but you may want to double check your .wav's are coded properly, I know there are some .wav files that wont work with system sounds unless you edit them.
You can try audacity for this, and you can use it to properly compress your .wav's

> 2. Keyring password. I find this annoying. Everytime I open Evolution, it asks for the password. I'd like this to go away. I tried some posted suggestions but they did not work.
I never been a big fan of evolution, so I dont use it...
You can install Mozilla thunderbird if you wish though.
> 
3. Admin password. Like # 2 above, when running an administrator task, I need to enter the password. I'd like this to go away.
Now this here is where you are totally on your own, the administration passwords are there FOR A REASON.
Want to know why windows is so insecure?
Because it does allow root access by default, it leaves itself wide open to attacks by not having a main password or does it requite one to be enabled.
Sure this makes windows easier, but it makes it unsecure and vulnerable.
Ubuntu and Linux in general are secure BY DEFAULT, by keeping the root user and the normal user seperate or by eliminating the root account entirely like in Ubuntu the sucurity factor goes up.
It might be annoying to type in your password all the time especially if you are the only user...
But it is SAFE.

> 4. 3/4 GB RAM. I have 4 GB RAM installed. The BIOS and Win VISTA recognize it fine. Ubuntu does not. Why? Is this disto of Linux limited to using 3 GB of memory? Can I make it use the 4 GB available?
Well this depends on what version of Ubuntu you are running and how high your memory is.
There is a limitation in the 32bit version of Ubuntu and if you use it it can explain why you are not reading your full memory.
But you can remedy this by installing the 64bit version of ubuntu, but depending on your processor you may wish to ignore it.
But in your case with your dual core setup you may wish to try out the 64bit kernel version of ubuntu.
Really Ubuntu is no hog like Vista, it doesnt need insane amounts of memory to run a single app like vista.

> 5. Dual boot screen. The initial dual boot screen to choose the OS is not in my preferred order. I know I can edit the lines but I wish to edit the order of the choices; maybe even delete a choice too. I can't locate the file for this.
Not my area of expertise again, so sorry.

---

### Post by Ripfox on 2008-11-30
> **kansasnoob said:**
> Just a note: 

This post was just fine, so don't take it as criticism, but in the future it's good practice to post separate threads regarding separate problems.

Most of us have extensive knowledge in certain areas, while limited or no knowledge in others so it's nice to see a thread titled in a manner that draws the interest of the right folks.

Also this is a great (and very dependable) link:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Welcome, and enjoy!

Since when?

---

### Post by oldos2er on 2008-11-30
"sudo gedit /boot/grub/menu.lst" should be "gksu gedit /boot/grub/menu.lst" since gedit is a graphical program.

---

### Post by oldos2er on 2008-11-30
"Can I make it use the 4 GB available?"

 Use 64-bit Ubuntu.

---

### Post by wc4r on 2008-11-30
Thanks all. All items are taken care of except the Sound issue. Still trying to work that one out.

---

### Post by CatKiller on 2008-11-30
> **wc4r said:**
> Thanks all. All items are taken care of except the Sound issue. Still trying to work that one out.

The login window (GDM) uses **gdmplay** to play sounds. I haven't been able to find out much about it, but it's possible that it's a restricted wrapper around **aplay**, the native ALSA player. **man aplay** has this to say about the formats that it supports; >               Recognized sample formats are: S8 U8 S16_LE S16_BE U16_LE U16_BE
              S24_LE S24_BE U24_LE U24_BE S32_LE S32_BE U32_LE U32_BE FLOAT_LE
              FLOAT_BE  FLOAT64_LE  FLOAT64_BE  IEC958_SUBFRAME_LE IEC958_SUB&#8208;
              FRAME_BE MU_LAW A_LAW IMA_ADPCM MPEG GSM
              Some of these may not be available on selected hardware
 I don't know how these correspond to the files you're trying to use.

Programs that run before anyone's logged in are a bit tricky. Obviously there are no users, which limits the types of daemon that can be assumed to be running. Also, they need to be restricted in scope so that a vulnerability in them can't be used to gain unauthorised access.

Using Audacity to save your .wav files as Unsigned 8-bit might be the most compatible option. Then you can try stepping up the quality from there to see which combinations work, and which ones don't. Having said that, the default login window sound is mono 16-bit at 44100 Hz. I don't know if it's signed, or if it's little-endian or big-endian.

Good luck!

---

### Post by Lamont Cranston on 2008-12-20
startupmanager worked magic for me...thank you

---

