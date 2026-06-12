---
title: "Basic Question about Ubuntu"
date: 2013-10-05
forum: New to Ubuntu
---

### Post by adithya2 on 2013-10-05
I am new to Ubuntu and I have installed Ubuntu 11.10 version on my PC.
Is there anything similar to control panel in Ubuntu.If not,how to know what all applications are working in the background and how to detect and stop them if some of the applications are not required.
Thanks and regards in Advance.

---

### Post by Prime624 on 2013-10-05
You're thinking of the system manager. While there is a system manager in Ubuntu, it's not nearly as powerful as in Windows. If your computer freezes, it's frozen.

System Monitor manages tasks in Ubuntu. You can search for it in the dash.

You can also set a shortcut for it to open (command: "gnome-system-monitor"). XKill turns your mouse into a task killing tool, click and gone. It's command (can also set shortcut) is just "xkill".

---

### Post by whitesmith on 2013-10-05
> **Prime624 said:**
> You're thinking of the system manager. While there is a system manager in Ubuntu, it's not nearly as powerful as in Windows.System manager? There's a System Monitor that does everything Microsoft's Task Manager does. Or at the command line you can simply run ```
top
``` and then```
kill xxxx
```Simple, elegant & powerful.
> **Prime624 said:**
> If your computer freezes, it's frozen.Sometimes Ubuntu, a shell wrapping Linux, will freeze. The Linux kernel remains active, and can be safely restarted by holding down Alt+SysRq and slowly typing the initialism formed by this mnemonic: Raising skinny elephants is utterly boring.
> **Prime624 said:**
> You can also set a shortcutShortcut is a Windows term; we call them Launchers.

[edit]**adithya2 ** you are running an old version of Ubuntu. Code past EOL is unsupported. Consider upgrading to 12.04 LTS, which is probably the best for you at this stage.

---

### Post by SeijiSensei on 2013-10-05
You should be running 12.04LTS, not 11.10.  That release has already reached its "[end-of-life]("https://wiki.ubuntu.com/Releases")" and is no longer supported.  Since you just installed Ubuntu, I recommend reinstalling with 12.04 which will be supported until 2017.  If you installed 11.10 to avoid the Unity desktop, consider one of the alternative "flavors" of Ubuntu like Kubuntu with the KDE desktop environment, Lubuntu with LXDE, or Xubuntu with XFCE.

---

### Post by Prime624 on 2013-10-05
> **whitesmith said:**
> Sometimes Ubuntu, a shell wrapping Linux, will freeze. The Linux kernel remains active, and can be safely restarted by holding down Alt+SysRq and slowly typing the initialism formed by this mnemonic: Raising skinny elephants is utterly boring.

Shortcut is a Windows term; we call them Launchers.

Thank you for the sys restart method. I will definitely try that. When I said that the Ubuntu system manager isn't as powerful, I meant as powerful as Ctrl+Alt+Del is, not just the manager.

Please stop trying to be superior with your terminology. Straight from Ubuntu:

[IMG]http://i.imgur.com/iDTmKsB.png[/IMG]

---

### Post by whitesmith on 2013-10-05
No "superiority" was intended. One problem we have in the Linux world is the necessity of accommodating people who know more about Windows than Linux. Take the Super key. We *could* call it the Windows key, but that's a hat tip to Redmond. Shortcut falls into the same category. Unfortunately, the community is not always consistent, as your screenshot demonstrates. Have a pleasant weekend.

---

### Post by Barsoom88 on 2013-10-05
Great post and replies!
Thanks!

---

### Post by DuckHook on 2013-10-05
> **Prime624 said:**
> Please stop trying to be superior with your terminology.With all due respect, I don't think *whitesmith* was trying to be superior.  I've often run into this dilemma myself: if Linux refers to certain things using a different term, then using the Windows term tends to confuse new users rather than help. A different example is the Linux use of "module" for what roughly in the DOS/Windows world is "driver". Commands like *lsmod* and *modprobe* derive from "module". Therefore, new users often get confused if we use "driver" although the terms are roughly interchangeable.

EDIT:

*whitesmith* already replied on his own behalf.

/EDIT

---

### Post by grahammechanical on 2013-10-05
Linux does not have the same issues as Microsoft Windows does. You will find in Ubuntu 11.10 there is a utility called Startup applications that lists the applications that start when the OS is booted. Be warned. It is very easy to remove important components by removing things from Startup Applications. This is why in Ubuntu 13.04 Startup applications only lists applications that we choose to install and need to be loaded automatically at boot time. I have installed two utilities for monitoring various temperatures and fan speeds. These are the only two items that I have in Startup Applications in Ubuntu 13.10.

It is not easy in Ubuntu to stop system services from working and it should not be easy to do that either. Open a terminal and run this command

```
top
```

That will show you all the processes that are running and how much system resources are being used by each. You close the terminal to closed down top. A lot of effort has been done in Ubuntu over the past year to make Ubuntu more efficient. I have seen a 15% to 20% reduction in memory usage from 12.04 to 13.04. And I have read about ongoing work to identify which processes can be automatically shutdown if not needed and then restarted when needed. This is part of the development work for Ubuntu phones/tablets but it will also benefit us on the desktop.

Regards.

---

### Post by DuckHook on 2013-10-05
To expand on whitesmith's suggestions, as a rule, Linux is far more stable than Windows because the GUI is just another app running on top of the base Linux OS, unlike Windows where the GUI is so heavily integrated into the kernel that a misbehaved app will bring down the entire Windows session.

Because the GUI and the entire desktop environment (DE) in Linux is basically just another app, there are many ways to show, suspend and even kill misbehaved apps, but the most powerful methods require the command line. Therefore, open a terminal and, to see running processes, do:```
ps -ef
```To search for a specific process:```
ps -ef | grep -i <process name>
```...and replace <process name> with the actual name of the process. Note the process ID (PID) beside the process name of interest.

To terminate a frozen or misbehaving app, find the corresponding (PID) from the command just given and:```
kill -s 15 <PID>
```...where <PID> is replaced with the actual numerical PID you noted earlier. A stronger version is ```
kill -s 9 <PID>
```...but try "15" first and use "9' only if necessary. To learn some of the basic commands that are actually at the heart of Linux, [this]("https://help.ubuntu.com/community/CommandLineResources") is a good resource.

If the whole DE is frozen, you can often reset things by hitting <Ctrl>+<Alt>+<Delete>. This does not reboot the system like it does in Windows. Instead, it forces a logout, which is clean, and puts you into the login screen. Starting with 10.04, I believe, the more powerful <Ctrl>+<Alt>+<Backspace> was disabled by default, but you can re-enable it by going into System Settings>Keyboard Layout>Options>"Key sequence to kill the X server" and activating the checkbox. This will allow you to kill your whole X session in future if your DE totally freezes up (you can't even bring up a terminal). You will lose any unsaved work, but the Linux system underneath will still be rock solid.

Alternatively, you can hit <Crtl>+<Alt>+<F1> to get to a pure bash shell command line console and kill/restart your DE from there with```
sudo service lightdm restart
```Last but not least, if your computer is really gummed up, you can ssh into your frozen box from another computer altogether and initiate a complete shutdown or reboot. This technique is probably too involved for you at the moment, but it's nice to know that it's another option when you do have the time to explore it.

---

### Post by whitesmith on 2013-10-05
To speak a little more on my own behalf, I sought to prevent propagation of the erroneous (but widespread) notion that "Windows got there first." This manifests itself in comments I've heard such as this doozie: "Since Linux has a Windows key, you guys are obviously ripping them off." Most newcomers don't know, or even care, that Windows is a borrowing from the Macintosh gui, which in turn is a borrowing from work done at PARC, which incorporates the xwindows system used in Linux today. It's just genuinely, sincerely painful that people can't see beyond marketing stunts, and the nonsense uttered by Microsoft's paid flacs. End of soapbox rant, and an apology to anyone who took my words the wrong way. Like everyone else I have a lot to learn.

---

### Post by DuckHook on 2013-10-05
> **whitesmith said:**
> To speak a little more on my own behalf, I sought to prevent propagation of the erroneous (but widespread) notion that "Windows got there first." This manifests itself in comments I've heard such as this doozie: "Since Linux has a Windows key, you guys are obviously ripping them off." Most newcomers don't know, or even care, that Windows is a borrowing from the Macintosh gui, which in turn is a borrowing from work done at PARC, which incorporates the xwindows system used in Linux today. It's just genuinely, sincerely painful that people can't see beyond marketing stunts, and the nonsense uttered by Microsoft's paid flacs. End of soapbox rant, and an apology to anyone who took my words the wrong way. Like everyone else I have a lot to learn.

Notwithstanding the, ehrr, charged passion (which I hope doesn't raise the ire of the mods), I agree with everything you've said. But I still use Windows and Apples. They have their uses, and didn't start out full of FUD and disinformation.

---

### Post by adithya2 on 2013-10-05
Thanks a lot guys.That was very helpful.

---

### Post by craig10x on 2013-10-05
Unity has been the desktop on ubuntu since 11.04 so i can't see how he would have installed it to avoid unity...in fact, i am assuming he likes it....
I would suggest to him that he install 13.10 after Oct 17th when it is released as it is really excellent and has many improvements over that old 11.10 he is using...
and also because that 11.10 no longer gets updates...

---

### Post by Prime624 on 2013-10-06
I'm a little confused. I tried Alt+SysReq, and it just restarted the computer without warning. My programs didn't save or stay open, so it's just as good as a hard shutdown.

If I can't open the terminal (because the system is frozen), is there a way to salvage it, or do I just have to lose all my work because one app (often the software center) froze?

---

### Post by DuckHook on 2013-10-06
The <Alt>+<SysReq> method *is* a shutdown/reboot cycle. It just does it in a way that properly shuts down files and system resources, and flushes caches so that nothing gets corrupted (vs just yanking out the power cord). It most definitely does not save your work for you. It is not elegant, was not meant to be, and is a last-ditch method to free up a frozen computer. If you want to exercise finer kill control, you must use the methods I already explained in my previous post.

EDIT

Apologies. Just re-read your latest post. You mention that you cannot even bring up a terminal. In that case, try <Ctrl>+<Alt>+<F1> to switch to a completely separate bash shell. If it works, be warned that you will be in a stark command line environment. At first it is intimidating, but with time and practice it is not bad at all. Login to the bash shell and do the ps/kill commands I've already given instructions on. If you cannot even <Ctrl>+<Alt>+<F1>, then one last alternative is to ssh into your frozen box from another computer--the method I described at the end of my post. Only if all else fails should you <Alt>+<Sysreq>. And to be absolutely clear, whether you <Ctrl>+<Alt>+<Delete>, <Ctrl>+<Alt>+<Backspace>, or <Alt>+<Sysreq>, you will lose any unsaved work. None of these methods are elegant. They are meant to kill a balky DE, which includes all programs running within it.

If you continually get a frozen system from running certain programs, that is a different matter that should be addressed in a different thread.

/EDIT

---

### Post by Prime624 on 2013-10-06
Great!!! That's better than what I hoped. The only problem now is that I can't log in. I have tried numerous times with the same login/password I use when I start up Ubuntu. Is there some trick to this?
Thanks for all your help btw.

---

### Post by DuckHook on 2013-10-06
> **Prime624 said:**
> The only problem now is that I can't log in. I have tried numerous times with the same login/password I use when I start up Ubuntu. Is there some trick to this?Do you mean that you can't log in when you do <Ctrl>+<Alt>+<F1>? If so, then that's a real head-scratcher. You should be able to log in. In fact, it makes no sense that you can log in to a GUI session, but not a CLI session. There's no trick to it and you now have me stumped.

Are you sure you don't have CAPSLOCK on? Linux is case-sensitive, so any difference even in case will gum up your login. Therefore, make sure that your login ID is *exactly* the same. Also your password. Be careful about logging in as DuckHook in the GUI, but Duckhook in the CLI (lower case 'h'). That's really the only advice I can give on this problem.

---

### Post by heir4c on 2013-10-06
> **Prime624 said:**
> Great!!! That's better than what I hoped. The only problem now is that I can't log in. I have tried numerous times with the same login/password I use when I start up Ubuntu. Is there some trick to this?
Thanks for all your help btw.

You meant when you use Ctrl+Alt+F1 ?
U see nothing when you type your password not even "stars". You must type it "blind" after you see 'password:' And than click Enter.

---

### Post by Prime624 on 2013-10-06
> **DuckHook said:**
> Do you mean that you can't log in when you do <Ctrl>+<Alt>+<F1>? If so, then that's a real head-scratcher. You should be able to log in. In fact, it makes no sense that you can log in to a GUI session, but not a CLI session. There's no trick to it and you now have me stumped.

Are you sure you don't have CAPSLOCK on? Linux is case-sensitive, so any difference even in case will gum up your login. Therefore, make sure that your login ID is *exactly* the same. Also your password. Be careful about logging in as DuckHook in the GUI, but Duckhook in the CLI (lower case 'h'). That's really the only advice I can give on this problem.

That's what it was. My login is "Brexton", but in CLI I use "brexton". That's weird. Oh well. Thanks again.

---

### Post by Prime624 on 2013-10-06
> **heir4c said:**
> You meant when you use Ctrl+Alt+F1 ?
U see nothing when you type your password not even "stars". You must type it "blind" after you see 'password:' And than click Enter.

Thanks but I knew *that *already. I'm not *that *&#8203;new to Ubuntu. lol

---

### Post by Iowan on 2013-10-06
I've had occasion when one (or more) of the terminals (<Ctrl>+<Alt>+<F*>) wouldn't accept my login. I tried a few others until I found one that worked.

---

### Post by heir4c on 2013-10-06
> That's what it was. My login is "Brexton", but in CLI I use "brexton". That's weird. Oh well. Thanks again. 
Not weird. 
In Linux you can make many files with the name Linux. But in a different way: Linux; LINUX; linux; LinuX; ....etc.... are all different file names.

---

### Post by heir4c on 2013-10-06
> **Prime624 said:**
> Thanks but I knew *that *already. I'm not *that *&#8203;new to Ubuntu. lol

I don't know that. :) But it's always good for others who read this.

---

### Post by Prime624 on 2013-10-06
> **heir4c said:**
> Not weird. 
In Linux you can make many files with the name Linux. But in a different way: Linux; LINUX; linux; LinuX; ....etc.... are all different file names.

That's what I'm saying. Even though I could make many names with different capitalisation, I have to use all lowercase to login, even though it is partly capitalised.

---

### Post by DuckHook on 2013-10-06
> **Prime624 said:**
> My login is "Brexton", but in CLI I use "brexton".There's a difference between your UserID which is "brexton" and the User Information which you defined when you first installed the OS, which apparently was "Brexton". Had you put down Brexton_LastName, or Firstname_Brexton, it would be either of these "Aliases" that show up on the GUI login screen because the login manager doesn't actually display your login UserID, but just your "Alias". People get the two confused all the time, so it's quite common. In your case, just remember your lowercase ID. It's the important one.

---

### Post by deadflowr on 2013-10-06
> **whitesmith said:**
> No "superiority" was intended. One problem we have in the Linux world is the necessity of accommodating people who know more about Windows than Linux. Take the Super key. We *could* call it the Windows key, but that's a hat tip to Redmond. Shortcut falls into the same category. Unfortunately, the community is not always consistent, as your screenshot demonstrates. Have a pleasant weekend.

I usually refer to this key as a Windows key merely because it has the Windows logo on it.
If it had a picture of Redd Foxx, I'd refer others to the Redd Foxx, or  Fred Sanford key.

I can't fully blame microsoft for this, as it's a keyboard makers decision to put it there.

---

### Post by craig10x on 2013-10-06
@deadflowr: I've always called it the Fred Sanford Key myself :D

---

### Post by DuckHook on 2013-10-06
> **craig10x said:**
> @deadflowr: I've always called it the Fred Sanford Key myself :DI've glued a cute icon of Tux over mine. :biggrin:

---

### Post by rocketfish201 on 2013-10-06
> **deadflowr said:**
> I usually refer to this key as a Windows key merely because it has the Windows logo on it.
If it had a picture of Redd Foxx, I'd refer others to the Redd Foxx, or  Fred Sanford key.

Are you trying to tell me that they make keyboards that don't have a Redd Foxx key in between the Ctrl and Alt?

---

