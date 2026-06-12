---
title: "TP-Link WN821 wifi problems on Precise Pangolin 12.04"
date: 2013-04-28
forum: New to Ubuntu
---

### Post by UncleAsriel on 2013-04-28
I've encountered a similar problem to [nns2006]("http://ubuntuforums.org/showthread.php?t=2139990"), but I'm using a TP-Link TL-WN821N wireless adapter on Ubuntu v12.04. 

The system is unning on machine with 64-bit AMD Phenom 8450 Triple-Core processor x3 and a nvidia graphics card.

The device is detected when inserted into my machine, but when I go to connect to the wifi network, I get stuck at the network authentification stage. I type in the network's password, but the same prompt shows up after a minute of attempting.

I know there were some problems with [Ubuntu 10.04]("http://ubuntuforums.org/showthread.php?t=951683"), but those involved outright non-detection of the hardware. 

In this machine's location, wireless is the only internet I have. The same computer running Windows Vista was able to connect to the internet. Currently the notebook I'm using has a full connection.

Can someone please advise?

Here is the netinfo.txt file.
[ATTACH]241919[/ATTACH]

---

### Post by UncleAsriel on 2013-04-28
Update: after restarting the router, I appear to have a connection. This shall be treated as solved.

---

### Post by UncleAsriel on 2013-04-28
After my system froze (I believe this is borne of the problems discussed [here]("http://ubuntuforums.org/showthread.php?t=2018276"), [here]("http://askubuntu.com/questions/56645/ui-elements-become-completely-unresponsive") and [here]("http://askubuntu.com/questions/126773/ubuntu-become-very-slow-and-unresponsive-after-upgrade-to-12-04"), but that's another topic), the wireless adapter stopped working. The same problem described in my first post arose. 

I'm searching for alternative problems like this, but I'm so far still stuck on finding a consistent cause.

Does anyone have an idea of what's happening?

---

### Post by varunendra on 2013-04-29
Welcome to the forums UncleAsriel :)
> **UncleAsriel said:**
> Does anyone have an idea of what's happening?
The netinfo.txt file could give us some idea. Unfortunately, the attachment seems to be missing. Please re-attach the file..

---

### Post by kurt18947 on 2013-04-29
There are different versions of that adapter.  V1. V2 & v3 use some form of Atheros chipset which generally work. An Atheros fix which is sometimes required is to disable hardware encryption.   It looks like V4 switched to Realtek.

[TABLE="class: sortable wikitable smwtable jquery-tablesorter"]
[TR]
[TH="class: headerSort"][/TH]
[TH="class: Chip1-brand headerSort"][Chip1 brand]("http://wikidevi.com/wiki/Property:Chip1_brand")[/TH]
[TH="class: Chip2-brand headerSort"][Chip2 brand]("http://wikidevi.com/wiki/Property:Chip2_brand")[/TH]
[/TR]
[TR="class: row-odd"]
[TD][TP-LINK TL-WN821N v1]("http://wikidevi.com/wiki/TP-LINK_TL-WN821N_v1")[/TD]
[TD="class: Chip1-brand"]Atheros[/TD]
[TD="class: Chip2-brand"]Atheros[/TD]
[/TR]
[TR="class: row-even"]
[TD][TP-LINK TL-WN821N v2]("http://wikidevi.com/wiki/TP-LINK_TL-WN821N_v2")[/TD]
[TD="class: Chip1-brand"]Atheros[/TD]
[TD="class: Chip2-brand"]Atheros[/TD]
[/TR]
[TR="class: row-odd"]
[TD]**TP-LINK TL-WN821N v3**[/TD]
[TD="class: Chip1-brand"]Atheros[/TD]
[TD="class: Chip2-brand"]Atheros[/TD]
[/TR]
[TR="class: row-even"]
[TD][TP-LINK TL-WN821N v4]("http://wikidevi.com/wiki/TP-LINK_TL-WN821N_v4")[/TD]
[TD="class: Chip1-brand"]Realtek[/TD]
[TD][/TD]
[/TR]
[/TABLE]

[http://wikidevi.com/wiki/TP-LINK_TL-WN821N_v1](http://wikidevi.com/wiki/TP-LINK_TL-WN821N_v1)
[http://wikidevi.com/wiki/TP-LINK_TL-WN821N_v3](http://wikidevi.com/wiki/TP-LINK_TL-WN821N_v3)

---

### Post by UncleAsriel on 2013-04-29
Added the netinfo.txt as requested.
[ATTACH]241953[/ATTACH]


Last night I did some diagnostics a friend walked me through.
Into the terminal we typed the following

```
sudo rmmod ar9170usb 
```

The attempt saw us recieve this error: 

```
ERROR: module ar9170usb does not exist in /proc/modules
```

We then used the lsmod command. It gave us [these results]("http://pastebin.com/HFNfZXSm").

Having determined that the name of the device we were looking for was rtl8192cu, we then tried the rmmod command on it.

```
sudo rmmod rtl8192cu
```
We then tried 
```
sudo modprobe rtl8192cu
```

The wireless tried re-checking itself but the same problem kept re-occurring.

We then tried to change the wireless so that the network no longer required a password, but that turned out sour when it took out the internet for the entire house.

After struggling for an hour to get the internet set up again, we decided to call it quits for the night.



What does that mean for my system, kurt18947? Realtek vs Altehros refers to the type of physical unit they chose to store this on, correct?

How does the this affect the problem at hand? Do I have to install a different patch/module/thingy to fix this?

---

### Post by kurt18947 on 2013-04-30
> **UncleAsriel said:**
> 
....................

What does that mean for my system, kurt18947? Realtek vs Altehros refers to the type of physical unit they chose to store this on, correct?

How does the this affect the problem at hand? Do I have to install a different patch/module/thingy to fix this?

It appears you have v.4 of this adapter using the RealTek chipset.  If you have v.1-v3 the module in use would most likely be ath9k, not rtl8192cu.  A module is sort of like a driver in Windows.  This forum has wizards when it comes to wireless problems, I am not one.  Here is a thread about the same RealTek chipset in a different device:

[http://ubuntuforums.org/showthread.php?t=2119378&highlight=rtl8192cu](http://ubuntuforums.org/showthread.php?t=2119378&highlight=rtl8192cu)

I have used driver-from-RealTek solution on another realtek chipset and it worked a treat on 12.04 and 12.10.  You appear to be running 12.04 so it should work for you as well.  I prefer to avoid NDISwrapper unless there is no other choice.  Be aware that the Realtek driver may fail after an update to the linux image/kernel.  My solution is to leave the extracted download from RealTek on the desktop of my SUDO account user.  If the adapter fails after an update, simply re-run the script.  The adapter will function again.

---

### Post by varunendra on 2013-04-30
First, a few notes :-
[LIST=1]
[*]I don't know about ar9170usb, but ar9170 has been replaced by carl9170 driver long ago (since 10.04 I guess). Not that it is relevant to your problem, just a note :)
[*]NEVER use '**rmmod**' unless you are absolutely sure what you are doing and what all it will affect. Instead, use **modprobe -r** command. Short description of 'why' is that rmmod doesn't care for dependencies or load/unload sequence and may even crash system due to this. On the other hand, **modprobe -r** is just a smart way of handling rmmod. It also unloads the dependencies in correct sequence, and returns error message if there is any problem in removing a module or any of its dependencies.
[/LIST]


> **UncleAsriel said:**
> What does that mean for my system, kurt18947? Realtek vs Altehros refers to the type of physical unit they chose to store this on, correct?

How does the this affect the problem at hand? Do I have to install a different patch/module/thingy to fix this?

While kurt may be able to elaborate on this, the short answer to your questions is that Realtek/Atheros are chip manufacturers and the name indicates which manufacturer's chip has been used on the wireless (or any card for that matter) module. It changes the whole thing about a problem and its solution, including applicable driver, available options that can be applied and methods to solve pertinent problems, if any.

That said, please try a small parameter to your driver first, and let us know if it makes any difference -
```
sudo modprobe -rfv rtl8192cu
sudo modprobe -v rtl8192cu swenc=Y
```
Try to connect after running the above commands and post back the result. This is a temporary change that will be lost at reboot. If it seems to help, we can make it permanent.

**EDIT:** Beaten by kurt :)

---

### Post by UncleAsriel on 2013-04-30
I tried the modprobe commands like you suggested.

The wireless icon flickered but no long-term effect was noticed.

How do I go about making these additions to the blacklist. I believe it involves loading things via the [commands discussed here]("https://wiki.archlinux.org/index.php/Kernel_modules#Loading").

I'm unsure of the exact syntax, though. (still very green with Linux, all-in-all). What should I type?

[COLOR=#000000]I'm assuming the following should not suffice

```
blacklist [/COLOR][COLOR=#417394]rtl8192cu[/COLOR][COLOR=#000000] in /etc/modprobe.d/blacklist.conf[/COLOR]
```

Installing the driver should be easier (just extract the executable from the webtsite (found [here]("http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU")) and follow the instructions on the auto-extraction. (I'm assuming that - like w Windows executable file - one of these conpressed drivers know which directory to install themselves into. I have a feeling this is incorrect, though).

Could you please advise before I take this last step (which I believe will fix this issue)?

---

### Post by kurt18947 on 2013-04-30
You're most likely correct, you need to blacklist the default realtek drivers in order for the module to created from Realtek to not conflict.  Arch looks substantially different though the idea is the same.  First, you're modifying system files so you need **S**uper**U**ser**DO** privileges.  You'll need to be using the account you first set up when you installed.  That account has SUDO privileges by default, other accounts do not.  Once logged into that account, open a terminal and type the following:
```
gksu gedit /etc/modprobe.d/blacklist.conf.
```

You'll need to enter your SUDO password again.  A file should open in gedit, the default text editor.  You can scroll to the bottom of the file and add the entries necessary to prevent the default realtek drivers loading.  Save, exit and reboot.  I do not have your particular adapter but I have one similar, rtl-8188CUs.  I have blacklisted 
[LIST]
[*]rtl8192cu 
[*]rtl8192c_common 
[*]rtlwifi 
[/LIST]
Yours may not be the same.  You can run the command "lsmod" and note any rtl*entries.  Those will likely have to be blacklisted.  The module from RealTek on my machine  doesn't begin with rtl, it's only 8192cu.  Hopefully this will be your last step.  

You could run into one other problem though I'm not certain which adapters are affected.  If I put a machine with an rtl8192SU adapter in suspend then resume, the wifi adapter will not come online.  Unplug, reinsert and it works.  There is a fairly simple fix if you have an issue with your adapter waking up after suspend.  We can cross than bridge if and when we get there.

---

### Post by UncleAsriel on 2013-04-30
I'm glad I read XKCD, then. sudo make me a sandwich!

I encountered the same three files under my configuration as well. [COLOR=#000000]rtl8192cu, rtl8192c_common, and rtlwifi seemed to be the same troublemakers. They were blacklisted and the problem was dealt with.
[/COLOR]
I then extracted the drivers from Realtek's website (porting them over from a USB, extracting them onto the desktop, opening the folder, then right clicking on install.sh, and selecting the 'Allow executing as program" under the Permissions tab.

I then restarted the computer.

Upon logging in, the wireless icon did its light-up animation. The problem persists.

I intend to attach the new netinfo.txt to demonstrate the appropriate changes made.

What else could I consider?

---

### Post by UncleAsriel on 2013-04-30
[ATTACH]242019[/ATTACH]

Here is the new netinfo.txt file

---

### Post by varunendra on 2013-04-30
> **UncleAsriel said:**
> I then extracted the drivers from Realtek's website (porting them over from a USB, extracting them onto the desktop, opening the folder, then right clicking on install.sh, and selecting the 'Allow executing as program" under the Permissions tab.

I then restarted the computer.

The good part is - you gave us a very good description of what all you did.
The not-so-good part is - 1) what you have done so far is not enough, and 2) Your method of black listing is 'slightly' incorrect.

Before you proceed to replace the native driver with the downloaded one (you haven't done it so far), I'd recommend you try the "swenc=Y" parameter I suggested in my previous post. It won't hurt anything even if didn't work, and will be a better choice if it did work.

ONLY If that option doesn't help, go ahead with installation of the downloaded one as follows -
[LIST=1]
[*]Open a terminal.
[*]Go into the directory in which you have extracted the downloaded driver package. For example, if it is RTL_DRIVER folder on the Desktop, then enter the command ```
cd ~/Desktop/RTL_DRIVER
```
[*]Once in, run - ```
sudo ./install.sh
```
[*]Enter your password when asked by sudo, and let the process finish. Watch out for any errors. Post back if there are.
[/LIST]


Now to correct the blacklisting of the native drivers (obviously don't do it if the swenc=Y trick works for the native one) -
[LIST=1]
[*]Open the blacklist.conf file as root - gksu gedit /etc/modprobe.d/blacklist.conf
[*]Now change the last three lines (that you have added) such that -
[/LIST]
```
rtl8192cu
rtl8192c_common
rtlwifi
```
become-
```
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi
```
Proofread, save and close. Reboot and check -
```
lsmod
```
You shouldn't see any of the blacklisted drivers in the output. Instead, you should see the 8192cu driver loaded as Kurt mentioned.

Let us know of the outcome.

---

### Post by UncleAsriel on 2013-05-01
Ha ha!

Thank you, doing the Blacklist the right way was what did it! (I tried the sweck=Y method and it failed).

Thank you so much! I'm going to close this topic now.  Now I'm off to learn the basic primers of proper command line commands!  Thank you all for your patience and continued support!

---

### Post by varunendra on 2013-05-01
> **UncleAsriel said:**
> Thank you, doing the Blacklist the right way was what did it!

Glad it worked. Please consider marking the thread as [Solved] now. Follow the 'See how' link in my signature to see how to do that. Thanks!

---

### Post by UncleAsriel on 2013-05-01
Thanks, Varunendra.

This is embarassing, I can't seem to get the prefix option available. Like coffeecat discussed in the link in your signature, my display when I go advanced on the editing feature looks different (it resembles [this]("http://ubuntuforums.org/attachment.php?attachmentid=239689&d=1362300481") more than [this]("http://ubuntuforums.org/attachment.php?attachmentid=239665&d=1362279530"))

Last night I changed the threat title to [SOLVED], and put in the editing reason for it, too. Unfortunately, I'm experiencing the same issue a number of users discussed. By putting [Solved] into the title, it shows that the title of the post in-thread has my changes, but when viewed from the Absolute Beginners section, it show these changes.  Sorry, mod team! I tried my best!

---

### Post by varunendra on 2013-05-01
> **UncleAsriel said:**
> This is embarassing, I can't seem to get the prefix option available.

No prob., I requested the mod team to do that for you. You can always communicate with the mods/admins directly by using the "Report Post" button at the bottom of each post. It is there to communicate with mods where necessary, that's all :)

---

### Post by papibe on 2013-05-01
Hi  UncleAsriel.

[This]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") describe how to mark the thread as solved on the current (new) forums.

Let us know if you have any problem with that.
Regards.

P.S.: thanks for the heads up varunendra :)

---

### Post by UncleAsriel on 2013-05-02
Thank you, varunendra. I figured that would be the next step, but I wasn't sure about the mods attitudes towards that. (Some forums I've been on have had mods extremely displeased with the use of reports for anything other than dealing with problem users).

papibe, I'm afraid I'm still encountering the same problem as before. I click the Edit Post button at the very first post of the thread, click Go Advanced, but there is no Prefix dropdown button for me to manipulate. I must say, I'm stymied.


Thanks all the same for your help!

---

