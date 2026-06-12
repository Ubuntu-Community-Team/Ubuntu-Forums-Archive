---
title: "Networking"
date: 2012-05-07
forum: New to Ubuntu
---

### Post by DaveMcC on 2012-05-07
Hi, please try and keep the answer simple, as I am old and daft.

I have 2 computers here side by side, this one, my main one is running "ubuntu 10.10 maverick" other is running ubuntu 9 which I will shortly be changing to Xubuntu 11.04
They are both wired to the same Netgear router 

So, how ! do I get Ubuntu 10.10 to see Xubuntu on a net work for storing files, like drag and drop?

Dave

---

### Post by bab1 on 2012-05-07
> **DaveMcC said:**
> Hi, please try and keep the answer simple, as I am old and daft.

I have 2 computers here side by side, this one, my main one is running "ubuntu 10.10 maverick" other is running ubuntu 9 which I will shortly be changing to Xubuntu 11.04
They are both wired to the same Netgear router 

So, how ! do I get Ubuntu 10.10 to see Xubuntu on a net work for storing files, like drag and drop?

Dave

Install Samba server on the machine you will be serving the files from.  You can install Samba server on both machines if you wish.  Make sure it is Samba 3.5 not Samba4.

---

### Post by DaveMcC on 2012-05-07
Tryed to install Samba and got the following

Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

Don't know what to do next ?

Dave

---

### Post by jerome1232 on 2012-05-07
10.10 has met it's EOL (end of life), so it won't be able to contact the servers to install anything, I highly recomend you either install 10.04 LTS which still has a year of support, or upgrade it to a more recent version of Ubuntu.

This is a how to about upgrading an EOL release.
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by DaveMcC on 2012-05-07
> **jerome1232 said:**
> 10.10 has met it's EOL (end of life), so it won't be able to contact the servers to install anything, I highly recomend you either install 10.04 LTS which still has a year of support, or upgrade it to a more recent version of Ubuntu.

This is a how to about upgrading an EOL release.
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)


Thanks but NO, 
Computer is stable, it does what I want it to do and I hate the look of ubuntu 11, and ver 12, some thing a child drew up reminds me of Microsoft

Dave

---

### Post by bab1 on 2012-05-07
> **DaveMcC said:**
> Thanks but NO, 
Computer is stable, it does what I want it to do and I hate the look of ubuntu 11, and ver 12, some thing a child drew up reminds me of microshaft

Dave

Unfortunately NO is not an option.  You can't just stay where you are.  Your options are```

1. use archived repos for you existing version
2. Install 12.04 (and use Gnome Shell for the older look)
3. Install 10.04 (for Gnome 2 look)  
```

All of these require some complex effort.  

Option 1 will work but you will not have security updates and development of the apps.

Option 2 will provide you with stability for the next 5 years. The look is somewhat updated, but if you use Gnome Shell it's as close as you can get to Gnome 2 (not the same but close enough that it's worth consideration).

Option 3 puts you back one version but is still supported for 1 more year.  Gnome 2 is the default desktop so it will look like your current set up.

I myself currently run 10.04 and am waiting for the first point release (12.04.1) before I upgrade.  I understand your reluctance to the Unity interface.  I will be using Gnome Shell when I upgrade.

FWIW I would check to see if your repos are still available and if not convert to the archived repos.  Why?  To provide you time  to think about the inevitable upgrade to Ubuntu 12.04 after the first point update.  You could get to the inevitable update (12.04.1) with the install of 10.04 but it is a lot more work.

[**_[COLOR="Blue"]Here[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1673225") is the method of setting up your sources list (the repos) for 10.10 archived.  Post #2 at the bottom has the link.

I assume you have **all of your data backed up**.

---

### Post by Paqman on 2012-05-07
> **DaveMcC said:**
> Thanks but NO, 
Computer is stable, it does what I want it to do and I hate the look of ubuntu 11, and ver 12, some thing a child drew up reminds me of microshaft


If this machine is connected to the internet, I would strongly advise you to reconsider. You are no longer receiving security updates, so will not be protected should any new vulnerabilities be discovered in packages on your machine. The machine may be "stable", but it is no longer secure.

You don't have to move to a later version. There's an earlier one (10.04) that's still supported, and would be a much wiser version to run.

However if the machine is not connected to the internet, I see no reason why you couldn't continue to use 10.10 for as long as you like.

---

### Post by jerome1232 on 2012-05-07
Ubuntu is not OSX or Windows; you aren't hammered into Unity by upgrading. It's just the default environment, there is gnome-failback, which is gnome3 but looks much like gnome2, there is MATE, which is actually a fork of gnome2, plus the other DE's, KDE, XFCE, LXDE and more.

I think you'd like MATE or Cinnamon, both have that old look to them.

I personally think your best option is to downgrade to 10.04 LTS and use it until 12.04.1 LTS is released, at which point you can upgrade and try the various Desktop Environments available to find one to your liking.

-----------------------
Just to throw my 2cents out there I think gnome2 looks like a 10 year old OS, gnome3 looks fantastic, both gnome-shell and Unity. Everyone will have their various preferences, the great thing is you have many options in Linux.

---

### Post by sir_cheats_a_lot on 2012-05-09
Unfortunately this is true, Dave.  it's often best to stick to LTS releases of Ubuntu, other wise you'll be forced to upgrade every year.  if it bugs you: move to standard Debian. chances are pretty good you'll get close to 6 or more years a version there.   I imagine though it would be a huge pain getting things setup the way you want them since by default they only include "free" software in their repository, so you'd be adding a bunch more to the repo-list, just to get your basics working.

As others have already stated-Unity is merely ONE choice among about NINE other desktop environments. you aren't stuck with it..though it's entrenched pretty deeply in 12.04, and can't be completely removed...but you at least don't have to look at it ;)

---

### Post by jerome1232 on 2012-05-09
> **sir_cheats_a_lot said:**
> 
it's entrenched pretty deeply in 12.04, and can't be completely removed...but you at least don't have to look at it ;)

That's not true at all, you can remove it completely. You can also just not install it to begin with if you so choose (by installing a xubuntu, lubuntu, or kubuntu) You can also install a basic commandline only install, and build up as you so choose from there. 

As an aside it would be nice if Ubuntu would just switch to dvd's already and give a few options for your DE as a 'customize' option in the installer.

---

### Post by sir_cheats_a_lot on 2012-05-09
actually it is true.   if you mark unity and all it's components for complete removal, it'll also mark your gnome DE, and it's components, for removal as well.  Which basically means, I'm not wrong, you are indeed stuck with it, BUT like I said, you just don't have to USE it or LOOK at it. 

   Besides, I honestly doubt anyone would just happen to have all of those variants on hand, of the same version of Ubuntu.  I mean, really, if you wanted KDE, LXDE, XFCE, or fluxbox you'd download Kubuntu,Lubuntu,Xubuntu, or fluxbuntu, and wouldn't be wasting a disc for regular Ubuntu.   why on earth would somebody want to burn that many different variants of the same OS? ESPECIALLY, since those environments can all installed from the package manager? It not only wouldn't make sense, but it would be a waste of discs. 

In any case, we're drifting a tad offtopic.  If Dave wishes to keep his old version of Ubuntu, he'll have to add supported repositories to his source list(debian might be a good candidate), then reload his package list, and install samba as directed.   We can't really protect people from themselves you know?  No sense in trying.  Some older people can be like children sometimes, you tell them no and they go do it anyway because that's what they want to do...my parents are guilty of this.  They *_really_* dislike change(especially changes in UI), so they'll do everything in their power to resist it...even if it means staying on an unsupported system(Windows XP is a good example).

---

### Post by jerome1232 on 2012-05-09
> **sir_cheats_a_lot said:**
> actually it is true.   if you mark unity and all it's components for complete removal, it'll also mark your gnome DE, and it's components, for removal as well. 

Missinformation, removing the unity package will only remove the ubuntu-desktop meta package and unity. I actually tested this on my netbook, and it worked fine.

---

### Post by AlanR8 on 2012-05-09
Just to go of at a tangent here, how about installing Dropbox on both machines then you can keep both in synch.

---

### Post by sir_cheats_a_lot on 2012-05-10
Dropbox, might be a viable option depending on his connection speeds.  Of course he'll have to keep an eye on the storage space he's using on the service(it think it's like a 2-4GB limit for the free version) but it still means he'd have to wait for his files to upload to the account, then redownload it on the other computer.

  However, I think he'd be better off investing in an external hard drive that way he can keep regular backups as well, and just moving what he needs that way.  Especially if he needs to get it done quickly.

---

### Post by deadflowr on 2012-05-10
Your options are limited, if you have decided to hold back with upgrading for fear of having to deal with unity. I see several choices.

1) Go here
[http://www.samba.org/]("http://www.samba.org/")

and try to compile samba yourself.

2) Upgrade to 11.04(Natty Narwhal).Though unity is the default DE, Natty is built on Gnome 2.x.As such Classic Gnome is easily accessible, and is installed by default(for machines incapable of unity 3d prowess)(unity-2d was added as the default in 11.10)

3)Downgrade to 10.04(Lucid Lynx). The advantage of this over 11.04 is the support lasts longer(by six months)

4)Try a cloud-based storage like dropbox,or ubuntuone.

4)Get an external hard drive and constantly mount and unmount between to two PCs.

5)Install from the current alternate download, where you can pick your DE, though I believe it is limited(sans cinnamon)

Personally, I would upgrade all the way up to 12.04. You might even see about other ubuntu variants like xubuntu, or lubuntu, and even kubuntu.

---

### Post by Zill on 2012-05-10
> **DaveMcC said:**
> ...So, how ! do I get Ubuntu 10.10 to see Xubuntu on a net work for storing files, like drag and drop?
Obviously, before going any further, the OP has to decide on how to upgrade Ubuntu 10.10 to a supported release.  Apart from the suggestions already made I would also suggest taking a look at [Linux Mint]("http://linuxmint.com/"), which tries to keep a fairly conventional theme without the apparent dumbing-down of Unity.

Going back to the OP's orginal question, Samba has been suggested for networking the machines.  However, as Samba is primarily a system intended to allow Linux machines to network with Windows machines (smb is a Microsoft protocol), the traditional way to link an all-Linux network is via the Network File System (NFS).  See the following link for more info:

[LIST]
[*][SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")
[/LIST]

---

### Post by bab1 on 2012-05-10
> **Zill said:**
> Obviously, before going any further, the OP has to decide on how to upgrade Ubuntu 10.10 to a supported release.  Apart from the suggestions already made I would also suggest taking a look at [Linux Mint]("http://linuxmint.com/"), which tries to keep a fairly conventional theme without the apparent dumbing-down of Unity.

Going back to the OP's orginal question, Samba has been suggested for networking the machines.  However, as Samba is primarily a system intended to allow Linux machines to network with Windows machines (smb is a Microsoft protocol), the traditional way to link an all-Linux network is via the Network File System (NFS).  See the following link for more info:

[LIST]
[*][SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")
[/LIST]

At this point both Samba and NFS are well known userspace vfs.  The difference to me is Samba shares can be visually browsed to and mounted while NFS must be ***explicitly*** mounted to the hosts filesystem via either the terminal, a script or fstab (no browsing).

The OP stated > So, how ! do I get Ubuntu 10.10 to see Xubuntu ***on a net work for storing files, like drag and drop?***I take that as visually (via a GUI (browsing)).

---

### Post by deadflowr on 2012-05-10
I think, regardless of how we all feel about various file-sharing applications; and the smattering of alternative desktop environments, most pressing is definitely getting the OP's PC running a currently supported system, whether within the ubuntu family, or others such as mint. I would hope the OP finds a solution to that first.

---

### Post by 3rdalbum on 2012-05-11
> **DaveMcC said:**
> Hi, please try and keep the answer simple, as I am old and daft.

I can tell from the rest of your post, that you are certainly not daft.

> I have 2 computers here side by side, this one, my main one is running "ubuntu 10.10 maverick" other is running ubuntu 9 which I will shortly be changing to Xubuntu 11.04
They are both wired to the same Netgear router 

So, how ! do I get Ubuntu 10.10 to see Xubuntu on a net work for storing files, like drag and drop?

Dave

Other posters have said that you need to update the 10.10 computer in order to do what you want to do. **I disagree**. Certainly, I would recommend that you keep your system on a supported version of Ubuntu. **However**, for what you **specifically** asked to do (have a file server running on Xubuntu 11.04 that can be accessed by the Ubuntu 10.10 machine) you don't need to update anything. To do it vice-versa, you would need updating, but for the way you asked, you don't.

On the Xubuntu 11.04 computer, you can install a package called "system-config-samba". It will also install the Samba server. The 10.10 computer already contains the Samba client so there's nothing extra to install there.

If you don't know how to install packages on your system, then open a terminal on Xubuntu and type:

```
sudo apt-get install system-config-samba
```

Now run the new Samba program that appears in your Applications menu, or type this into the terminal:

```
sudo system-config-samba
```

Click on the + button in this window and choose a directory to share, and give the share a one-word name. Click the Writable box. In the Access tab, click on your username (assuming it's the same as on the other computer - if not, then click Allow Access to Everyone instead). After creating the shared folder the changes should take effect within a minute, although if the next steps don't work I'd recommend rebooting both computers, for luck :-)

Open a file browser on Ubuntu 10.10 and click on the Network icon on the left pane. Or, go to Places and come down to Network. It will show an icon called Windows Network. Double-click on this and it should show another icon that probably says "WORKGROUP". Double-click on this, and your shared folder on the Xubuntu 11.04 machine should be visible and you can open it and see its contents, and also be able to drag files into it.

---

### Post by zandman on 2012-05-11
If you only have to share between to Ubuntu machines then NFS should be good enough to get the job done. Samba must be used when you also have Windows machines on your network.
Set up NFS: [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

As others said before: best to upgrade the 10.10 to 11.10 or 12.04 first.
If you want to stick with Gnome: [http://ubuntuforums.org/showthread.php?t=1859961&highlight=gnome+classic](http://ubuntuforums.org/showthread.php?t=1859961&highlight=gnome+classic)
First post explains how to install and start with Gnome instead of Unity.

---

### Post by Zill on 2012-05-11
> **bab1 said:**
> At this point both Samba and NFS are well known userspace vfs.  The difference to me is Samba shares can be visually browsed to and mounted while NFS must be ***explicitly*** mounted to the hosts filesystem via either the terminal, a script or fstab (no browsing).
The OP stated
> So, how ! do I get Ubuntu 10.10 to see Xubuntu on a net work for storing files, like drag and drop?
I take that as visually (via a GUI (browsing)).
Once a NFS share is mounted (this can easily be done automatically by including it in the fstab file) then that share is seen as simply another directory within the filesystem.  eg.  files can be manipulated either with the terminal or, of course, with any GUI file manager (such as Nautilus) via drag and drop.

---

### Post by jtarin on 2012-05-11
[You might also consider sharing files with vsftpd ftp server!]("http://ubuntuforums.org/showthread.php?t=91887")

---

### Post by deadflowr on 2012-05-11
As you can see there are bountiful ways to skin the cat with regards to file sharing. Samba is mentioned often as it is fairly easy to setup.
As for aggresively pushing you to upgrade, there are a myriad of reasons to, supported systems get bug fixes, security fixes power consumption fixes and so on.
On the flip side though, as an eternal optimist, with the glass half-full, an end of life distro will always be as stable as it will ever be.And you will never have to worry about updates junking up a favorite application, or something like that.

---

