---
title: "Windows don't get focus as they should."
date: 2024-05-11
forum: New to Ubuntu
---

### Post by m-elodie on 2024-05-11
Hello!

I have a problem with Ubuntu (24, LTS).
I use waterfox. Let's suppose I have some windows open (for example Intel FPGA development software right now).
Waterfox is in the dash board. When double-clicking, I would expect that:
- If one window already exists, it's brought to foreground. It works like this on Windows, Mac, sone orher OSs I know.
- If no window exists, it should make a new one on the forground.

But what it does is that the window is created under my current windows.

I suppose it's a bug, because... what woud be the point of immediately hiding an application I obviously want to use.

I'm not sure how to name this problem. I found tons of articles about "focus", so yes, that might be called focus.
Anyway, all the HowTos I found don't work.

Does anybody know how to fix this?

Thanks,

Elodie

---

### Post by m-elodie on 2024-05-12
Hello!

Thanks for your mail and for the rephrasing. However, just in case, I'm working with Ubuntu 24, LTS, not Windows
(see my first sentence above).
Beside this, this is a Ubuntu forum, which is probably one the best places to find help about Ubuntu. Not
sure what your what'sapp group is about.
In the meantime, I found one solution that seems to work. It's a Gnome extension called Steal my focus.
You have to sudo app install chrome-gnome-shell. Don't ask me what it is but for sure in my case, it works.
Elodie.

---

### Post by TheFu on 2024-05-12
As they should?  Or as you think they should?  GUIs on Unix existed 10+ yrs before MS-Windows, so there was a history of how a mouse and windows should behave well before MSFT did anything in a GUI.

Window focus is a very personal choice.  There are many different ways to work with it. The Window Manager should be handling all focus choices, not the DE and definitely NOT any application.  Alas, Gnome does things in unapproved, non-standard ways.  Have you tried any other DEs? You may find them to be more to your liking.  Won't know until you try.

There are 3 main ways to deal with focus choices.
[LIST]
[*]Focus follows the mouse.  This means that where ever the mouse pointer is located, that gains focus.  No click needed.  It may or may not change the Z-level of a window.  I like for the Z-level to remain. Just because a window gains focus, that doesn't mean I want it on top.  To bring a window to the top, I have to click on the border.  This way, I can type in a window with focus, that isn't necessarily fully seen or on top of the Z-list.
[*]Click to focus. This is the way MS-Windows does it by default.  It not only makes the clicked window have focus, but also brings the window to the top. Thankfully, it can be overridden.
[*]Click to focus, leave Z-position alone.
[/LIST]
I use the 1st of those - focus follows mouse, no z-change happens.

To each their own.  I learned the focus follows mouse method long ago watching some Unix gurus work.  Their explanation made sense to me and I started using it then.  It is one of the first things I change in every WM on every desktop I use.  Every mouse settings/WM-settings tool I've seen has a way to set the focus policy.

BTW, on my accounts, alt-tab and shift-alt-tab don't work like most people expect either.  For me, they move through different workspaces, not different windows on the active workspace.

I suspect you've never considered some of these other options.  Everyone is a little different, which is completely fine. Also, Gnome (the newer releases) are splitting more and more away from the typical ways that our desktops worked the last 40 yrs.  You may find other DEs to be more efficient. Something to consider.  You can find lots of youtube videos showing all the different GUIs for Linux.  A GUI is just another program in Unix-like operating systems. It isn't tightly coupled to the OS.  Today, there are about 15 popular GUIs/DEs for Linux. Check out at least 5 to get an idea of the range.

---

### Post by m-elodie on 2024-05-12
Hello!

Thanks for the lecture!

> 
As they should? Or as you think they should? GUIs on Unix existed 10+ yrs before
MS-Windows, so there was a history of how a mouse and windows should behave well
before MSFT did anything in a GUI.


Clearly "as they should". For a couple of reasons:

1. Logical point of view:
If you are doing something, your desktop is full of windows, and suddenly you want
to open a browser to check some documentation online, or you want to open a folder,
then _obviously_ you want to acces to it, _immediately_.

2, I have played as a child with a unix system, with X11, twm, etc, designed even
before microsoft windows existed. And at that time also, any new window came to the front.
Maybe because it was setup that way, but it came to front automatically. And beside
this, the workstation I was using (Sony NEWS station) worked that way, always draw
the latest windows to front.

3. For most of today's users, legacy is not X11, but apple / microsoft, like it or not,
they were not even born in the X11 days.
So if Ubuntu wants to attract new users, a good approach would be to have an
interface as close as possible as what they are used to. If it's configurable, why not
set the default to what most of the people are used to, while leaving options to setup
other behaviors?

But the most important argument is (1). So can you give me an example where you want
to open a new window but you want it to stay under all your current windows?
Sorry, but I can't imagine even a single situation in which I would want to do that.
I'm sure you can find examples, but for the day to day work, being cheking your mail,
opening a browser, opening a folder, or starting ST IDE,  or FPGA progamming tools in
my case, you want it to be available right away.

For other features you are talking about, I can perfectly understand that some people
like the "focus follows mouse" feature. I don't like it but I don't think the logic is
failing in this case. Just another way to use the GUI. My feeling is that you get
irrelevant windows focused when you accidentally move the mouse, but I can understand
some people may like it.
But I fail to understand what can be gained by not showing the window I just opened.

Elodie.

---

### Post by TheFu on 2024-05-12
> **m-elodie said:**
> 
But the most important argument is (1). So can you give me an example where you want
to open a new window but you want it to stay under all your current windows?

...

But I fail to understand what can be gained by not showing the window I just opened.


I open about 10 applications when I login.  Most of them, I want to be iconified. Some I want specifically located on the screen with specific location and size, iin a specific workspace, AND at a specific Z-level.  I certainly don't want them all on top and tiled, though some people might want that.  We all work differently.  Admittedly, I'm odd.  I tend NOT to close programs when I'm done with them for now.  May need them again in 5 hrs.  Just iconify them and let the OS swap them out as needed.  After all, RAM that isn't used is being wasted.  In the Gnome 3 and later worlds, iconifying programs seems to be disallowed.  Fortunately, we can choose a different GUI and have what we want.  Nobody has to use Gnome.

There's no lifetime write count on RAM like there is on SSDs.
```
$ free -h
              total        used        free      shared  buff/cache   available
Mem:           30Gi        20Gi       4.6Gi       103Mi       5.3Gi       9.4Gi
Swap:         4.1Gi       1.7Gi       2.4Gi
```
This shows that the system still has over 9GB of RAM that can be used. I don't have any more applications to start up, however.

We all work differently.  That's fine. Anyway, for controlling focus, there are a number of tools to allow that. Since I don't use Gnome, I cannot provide a specific answer, but there are Gnome extensions and Gnome Tweaks to help navigate all the options that aren't easily accessed through the GUI.  It never hurts to review the Desktop Guide for the specific DE+release you are running too.  [https://help.ubuntu.com/stable/ubuntu-help/](https://help.ubuntu.com/stable/ubuntu-help/)  I assumed you already checked that.

I cannot believe you can't customize the settings to provide the behavior from Windows 3.0 you seem to expect, but Gnome often prevents some common sense things.  Would you consider any other DE, perhaps one with more flexibility and greater controls than the dumbed down Gnome4 stuff?

Linux isn't MacOS nor is it MS-Windows.  Trying to be like those other OSes really isn't a good idea when trying to differentiate your product from the others.  If it is like the others, why would anyone bother switching?   Remember this from just before Win7 was released? [https://www.youtube.com/watch?v=T3ID2CbtnKk](https://www.youtube.com/watch?v=T3ID2CbtnKk)   They loved the new "Windows 7 Beta!"   But it was Linux with KDE.

---

### Post by m-elodie on 2024-05-13
Hello!

I don't close windows either. I usually have one quartus environment open, and usually the
FPGA flashing utility. I also have one STM32 IDE open, because it uses a processor to
communicate with the FPGA I have under programming, so I like to have both of the
environments open at once on a single machine.
It can be done on Windows that I don't like, it can be done on Ubuntu which is better
in my view, that's the reason of my choice.

> 
I cannot believe you can't customize the settings to provide the behavior from Windows
3.0 you seem to expect


I know windows 3.0 only by name. I'm a mac user, but for development, there are things
I cannot do on a mac. For example FPGA design. That's why I started using Ubuntu.
I have some experience with Windows 7, 10, 11 and yes, I want windows to be opened
at once on the front.

> 
Gnome often prevents some common sense things. 


Yes, I noticed: for example it doesn't put new windows on top!!!

Beside this, to pick up an earlier part of your reply:

> 
As they should? Or as you think they should?


Then in this case: Gnome prevents some common sense things: Does it prevent some
common sense settings or does it prevent what you think is common sense?

I use Gnome because it happens to be Ubuntu's default. No other reason. The  advantage
is that it works out of the box. I'm paid for productivity, hard and soft design, not
for tinkering with Ubuntu settings. And I would use KDE or anything else if it happened
to be the default. Good enough and it does the job.

> 
Linux isn't MacOS nor is it MS-Windows. Trying to be like those other OSes really isn't
a good idea when trying to differentiate your product from the others. 


I'm using all 3. In some cases, there are programs working only on Windows, in other
cases only on Windows and Linux, not Mac. Example: Intel's Quartus which works on
windows and linux. So I _have_ to use all 3. Am I alone in this case? If you can live
only with Linux, that's good for you, but let's be honest: in most of the cases, you
cannot work only with one platform.

So having 3 machines with 3 different behaviors would be a headache. I could modify
my Windows keyboard layout so that it works exactly like a Mac, I can easily do it with
Ubuntu because I found a setting for mac keyboards, that's all I want.
Now when looking for a way to configure things, my first reaction is to open the
settings. If the "howto" I find sarts saying I have to sudo apt update, etc, etc,
I usually end up doing it, but I prefer the "mac way", settings with a specific
application. It doesn't make me feel smarter when I sudo shell commands, so I prefer
a mouse click.

> 
If it is like the others, why would anyone bother switching?


Being different can be an advantage if it's better, not because it's different.

Ok, anyway my problem is solved, as said earlier in msg2, so I will stop this discussion.
It goes nowhere. Thanks for your time.

Elodie

---

### Post by Impavidus on 2024-05-13
> **m-elodie said:**
> And I would use KDE or anything else if it happened
to be the default. Good enough and it does the job.

On Kubuntu, one of Ubuntu's official flavours, KDE is the default. Use that if you prefer it.

I use Xubuntu, which comes with xfce. It has settings on how to respond to new windows. Give it focus or not, raise to the top or not.

You have to keep in mind that **you** don't open windows. You ask the DE or the shell or whatever to start a process. Even something like cron can start a process. The new process may ask the window manager to open one or more windows and may do so immediately or later. The WM doesn't know wether the user asked for the window or not. Do you want a pop-up window, not directly triggered by a user interaction, to get focus automatically? I don't. It makes me input text in the wrong window.

I also use focus-follows-mouse. I don't want more than about 3 windows per desktop, at most one of which maximised. That's why I have 15 desktops.

---

### Post by hedgehog123 on 2024-05-13
> **m-elodie said:**
> 
Waterfox is in the dash board. When double-clicking, I would expect that:
- If one window already exists, it's brought to foreground. It works like this on Windows, Mac, sone orher OSs I know.
- If no window exists, it should make a new one on the forground.


I tried it In 22.04, there a double click still opens in foreground. Maybe they changed the behavior so double clicks open the program in the background. Normally only a single click is needed to open programs, even in Windows if it's pinned to the task bar.

---

### Post by m-elodie on 2024-05-14
Hello!

Thanks for your replies.
Sorry for all this mess, maybe I wasn't clear enough. It's solved, as stated in msg 2.

> 
In the meantime, I found one solution that seems to work. It's a Gnome extension called Steal my focus.
You have to sudo app install chrome-gnome-shell. Don't ask me what it is but for sure in my case, it works.


I think a simple settings items would be better, but hey, it works without too much digging in documentations.
And beside this, if this extension (steal my focus) exists, it seems to prove that I'm not alone in this case.

> 
On Kubuntu, one of Ubuntu's official flavours, KDE is the default. Use that if you prefer it.


Thank you for ths suggestion. As it works now and it seems to flawlessly do what I'm expecting, I will leave
it as is as long as it works.

Again, thanks for your replies!

Élodie.

---

### Post by emoxam on 2024-06-27
> **m-elodie said:**
> Hello!

Thanks for your mail and for the rephrasing. However, just in case, I'm working with Ubuntu 24, LTS, not Windows
(see my first sentence above).
Beside this, this is a Ubuntu forum, which is probably one the best places to find help about Ubuntu. Not
sure what your what'sapp group is about.
In the meantime, I found one solution that seems to work. It's a Gnome extension called Steal my focus.
You have to sudo app install chrome-gnome-shell. Don't ask me what it is but for sure in my case, it works.
Elodie.

What can i do i am using
nome-shell --version
GNOME Shell 42.9
It's not supported by a extension 'steal my focus'..

---

### Post by emoxam on 2024-06-28
seems this helped [https://extensions.gnome.org//extension/2182/noannoyance/](https://extensions.gnome.org//extension/2182/noannoyance/)

---

