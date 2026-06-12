---
title: "User password needed"
date: 2022-03-28
forum: New to Ubuntu
---

### Post by pussekatt on 2022-03-28
I have Ubuntu 20.04 and I am trying to install Nautilus but I keep getting asked for my password.As I am the only one that uses this PC I dont have a password.When I was installing Ubuntu and I came to the enter password part I just hir enter.So,how do I get past this password thing ?

---

### Post by TheFu on 2022-03-28
> **pussekatt said:**
> I have Ubuntu 20.04 and I am trying to install Nautilus but I keep getting asked for my password.As I am the only one that uses this PC I dont have a password.When I was installing Ubuntu and I came to the enter password part I just hir enter.So,how do I get past this password thing ?

Well, that was a bad thing to do.  You should have entered a password. There are many, many, reasons.  

Did you happen to try hitting <enter> when the password request happens?  Does it not work?

If not, there are a few possible methods to solve this, but since you've just installed the system (I hope), reinstalling AND setting a password (make it 16+ random, characters), will allow the userid to elevate for administrator rights.

The other solutions are basically hacking into the system and for someone new will be very difficult to accomplish. If you want to accomplish this, there are a number of 'how to replace password' how-to guides on the internet. All need terminal commands. All take advantage of physical access to the system.  The easiest is probably to boot using the recovery mode (Choose the Advanced... option when Grub is displayed, then choose "recovery").  [https://coderwall.com/p/1qptsw/ubuntu-recovery-mode-r-w-file-system](https://coderwall.com/p/1qptsw/ubuntu-recovery-mode-r-w-file-system)

If your system has been installed more than a week, I'm extremely fearful that updates haven't been happening all this time.  That's really bad and could allow remote attackers to take over the system. There are a number of already fixed remote access methods in 20.04, but if the system hasn't been patched all this time ... ouch.

---

### Post by coffeecat on 2022-03-28
> **pussekatt said:**
> When I was installing Ubuntu and I came to the enter password part I just hir enter.

Um, no. Not possible.

Just to be 101% sure, I've just run the 20.04 installer and reassured myself that when you get to the "Who are you?" page - as shown here - [https://ubuntu.com/tutorials/install-ubuntu-desktop#9-create-your-login-details](https://ubuntu.com/tutorials/install-ubuntu-desktop#9-create-your-login-details) - the continue button remains greyed out until you fill in an identical password in the two password fields. To be clear - you cannot install Ubuntu without setting a password.

Do you mean perhaps that you selected "Log in automatically?" That is an entirely different thing from what you describe. If you select "Log in automatically" you will have set a password - it's simply that you won't be required to use your password for logging into the dektop. But you will have the password you chose for doing things such as installing software. Which brings us to:

> **pussekatt said:**
> I have Ubuntu 20.04 and I am trying to install Nautilus

If you have Ubuntu (as opposed to Kubuntu, Xubuntu, Lubuntu, etc) Nautilus will be installed already. Not only will it be installed but it's a fundamental part of the gnome desktop environment, without which your GUI will be comprehensively broken. Perhaps you should clarify what you mean.

---

### Post by ActionParsnip on 2022-03-28
You can boot to root recovery console, mount the file system read/write with
```

mount -o remount,rw /

```

then run:
```

passwd username

```

Replace username with your actual username. Then run
```

reboot

```

Then let the system boot and use the password as you expect. When you use sudo in a terminal you will not get any feedback but just type the password and hit ENTER when asked

---

### Post by pussekatt on 2022-03-29
@ coffeecat,I have Ubuntu 20.04 but there is no Nautilis in the "apps "  ( the 12 dots at bottom left of screen )

@Action Parsnip,I am going to try what you suggested

---

### Post by pussekatt on 2022-03-29
@ Action Parsnip,well that did not work.I get the message "only root can use mount"

---

### Post by tea for one on 2022-03-29
> **pussekatt said:**
> I have Ubuntu 20.04 but there is no Nautilis in the "apps "  ( the 12 dots at bottom left of screen )

Nautilus is also known as Files.
Hot corner > Type to Search > Files

---

### Post by ajgreeny on 2022-03-29
I don't use nautilus or gnome but from what I know of it, what happens if you click on Activities (I think that's what shows top left of the screen) and start typing **nautilus**, or even open a terminal and use command **nautilus**?

---

### Post by TheFu on 2022-03-29
> **pussekatt said:**
> @ coffeecat,I have Ubuntu 20.04 but there is no Nautilis in the "apps "  ( the 12 dots at bottom left of screen )

@Action Parsnip,I am going to try what you suggested

Look for  "Files" as the name in the menu.  That's Nautilus.
Ninja'd by @tea for one

---

### Post by TheFu on 2022-03-29
> **pussekatt said:**
> @ Action Parsnip,well that did not work.I get the message "only root can use mount"

Did you boot into the recovery console?

I sorta said in my first reply that for some good folks, the fix would be a challenge and a reinstall is the best option.

---

### Post by pussekatt on 2022-03-30
There is no nautilus in files and I tried to reinstall Ubuntu over my existing install and it did not work,so I tried to install Lubuntu on a different partition and it got as far as a screensaver ( with what looks like blue smoke ) then a message said Lubuntu failed.

---

### Post by coffeecat on 2022-03-30
> **pussekatt said:**
> There is no nautilus in files 

As someone has already said in this thread, Nautilus **is** the Files app. It can't be in itself! 

Too late now that you overwritten your Ubuntu with a failed Lubuntu installation, but for the record in case you return to Ubuntu, the file manager in mainstream Ubuntu with the Gnome desktop used to be called Nautilus upfront. A few years ago the gnome developers decided to refer to it as "Files". That is what you see if you click on "About" in an open file manager window. And "Files" is what you see in the list of apps if you click on the 9 (not 12) dots at bottom left of screen. If you search for Nautilus above the list of apps, you will be prompted for "Files". The name change is a bit confusing for newcomers but worth knowing about as experienced users will tend to refer to Nautilus as that was what it was called for years. And it is still referred to as nautilus in the installation package for the application. Also, as I said before, Nautilus/Files, being the file manager, is a fundamental part of the gnome desktop environment.

But you won't find it in a default installation of Lubuntu. Lubuntu is a different desktop environment from the gnome of standard Ubuntu and it has its own file manager. I'm not sure of the name - I don't use Lubuntu and you'd have to ask a Lubuntu user.

Good luck with Lubuntu, if you manage to install it. And good luck with Ubuntu, if you decide to return to it.

---

### Post by ActionParsnip on 2022-03-30
> **pussekatt said:**
> @ Action Parsnip,well that did not work.I get the message "only root can use mount"
Did you reboot to root recovery mode?

---

### Post by TheFu on 2022-03-30
> **pussekatt said:**
> There is no nautilus in files and I tried to reinstall Ubuntu over my existing install and it did not work,so I tried to install Lubuntu on a different partition and it got as far as a screensaver ( with what looks like blue smoke ) then a message said Lubuntu failed.

Whoooosh.

I thought this was about Ubuntu Desktop (Gnome3+ Ubuntu), not Lubuntu (LXQT Ubuntu).
"Files" is the name for Nautilus in Gnome3+.  Yes, it is confusing.  An attempt to make things easier, that failed.  Canonical and Gnome do that a bunch.  For someone with little knowledge, it usually isn't an issue. For people with more knowledge, it becomes confusing. You seem to be in the latter group ... slightly.  

What is it about Nautilus that is so important? There are lots of other file managers. The one installed may be fine.  I use Caja myself, when I need a file manager (which is very seldom), but I'm odd (some would say very odd). ;)  OTOH, knowing the password for a userid that has sudo abilities really is mandatory. No _good_ way around that for any Unix system. That's just how it is.

Lubuntu is LXQt for 20.04 and later.

Lubuntu is LXDE for any earlier releases. The Lubuntu team needed to do something to stay with supported underlying libraries. They didn't have any choice. So either move to a later version of GTK+ (which is what Gnome uses) or switch to a version of Qt, which is what KDE uses. Both were going to be major rewrites.

While it is possible to mix DEs (LXQt, LXDE and Gnome), that can lead to some configuration file conflicts when both are used by the same userid. The Qt and GTK+ libraries tend to use very different config files, so any conflicts between them should be minimal, if any.  OTOH, using multiple GTK+-based DEs (Gnome3, Gnome4, LXDE, Cinnamon, Mate, .... there is a longer list) is very likely to bring config conflicts.  The way to avoid that is by using different userids for each.  

But there is a chicken-egg problem.  Creating a new userid needs sudo and without a working password for the account(s) in the sudo group, it isn't possible to create new userids.

If has been days for this issue.  After about 1 hour of effort, I would have backed up my $HOME directory to external storage, then wiped the entire system and performed a fresh install, wiping everything, as part of the process.  That probably would take less than 30 minutes total.

---

### Post by pussekatt on 2022-04-01
@ coffeecat > I tried to install Lubuntu but the instilation failed but Ubuntu is working just fine.What I am trying to do is transfer pictures and music from my PC to my smartphone and vice versa.
@ ActionParsnip > I tried what you said ( see reply above ) but I get the message that I cant use root.

---

### Post by TheFu on 2022-04-01
> **pussekatt said:**
> @ coffeecat > I tried to install Lubuntu but the instilation failed but Ubuntu is working just fine.What I am trying to do is transfer pictures and music from my PC to my smartphone and vice versa.
@ ActionParsnip > I tried what you said ( see reply above ) but I get the message that I cant use root.

Nautilus isn't special for accessing smartphones.  Every file manager I've seen can do it, provided the correct driver for the smartphone is known to udev.  If it doesn't "just work",  and you don't have sudo ability, there isn't much that can be done.

In short, it is time to **perform a wipe and reinstall** - _this time keep track of the password entered during install._ If the computer is in a physically secure location, write most of the password down on a post-it note and stick it to your monitor. Leave off the last few, perhaps 8, characters.  This way, you can have a random part at the beginning and something only you know at the end of the password. The random part is important for security. The part only you know it important so that an admin password isn't left written in the open. This idea of writing down only the 1st half of passwords isn't new, but it makes having much stronger passwords easier.

Obviously, backup to external storage any files you don't want to lose so you can put them back after the reinstall.

---

### Post by ActionParsnip on 2022-04-01
[https://www.psychocats.net/ubuntu/resetpassword](https://www.psychocats.net/ubuntu/resetpassword)

---

### Post by pussekatt on 2022-04-02
Yes,certainly looks like the only option I have left.One thing though,I have tried Lubuntu before and it is much faster on my laptop than Ubuntu,any "major"differences between these 2 os ?

---

### Post by him610 on 2022-04-02
> ....any "major"differences between these 2 os ?
No, only difference is the graphical user interface (GUI). Some may differ with this statement, but underneath the GUI, it is all the same, including the **need to set a password**.

---

