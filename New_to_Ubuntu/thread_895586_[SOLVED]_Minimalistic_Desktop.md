---
title: "[SOLVED] Minimalistic Desktop"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by Nxion on 2008-08-20
Hi All!,

I am currently using Gnome with Open box window manager. To be hones the only reason I have this combination is because I use wireless a lot and like to have Network Manager running so I can quickly switch wireless networks as well as view what my battery life is at. I know they make different bars like fbpanel and pypanel as replacements. My problem is actually getting thoes icons to appear on the bar. I want a bar that is pretty minimal and not like the gnome bar, meaning big and bulky. It would be cool it it told me whatwindows I have open as well but thats really not a requirement.

 I would really like to use either openbox or fluxbox, it doesnt matter. Can any one give me some info on what I might be doing wrong or point me in a general direction?

Thanks in advance to all!

---

### Post by swisscow on 2008-08-20
Have a look at crunchbang linux - ubuntu with openbox. It has some panels with network manager (not battery I think). I use it on a laptop, pretty cool.

---

### Post by CarlosNYB on 2008-08-20
With fluxbox you can get the network manager applet from Gnome to appear in the apps dock.

Open the file ~/.fluxbox/startup with a text editor

Down later in the file you will see this section:

# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#

Type in this line:

```
nm-applet &

```Save.

---

### Post by Nxion on 2008-08-21
> **swisscow said:**
> Have a look at crunchbang linux - ubuntu with openbox. It has some panels with network manager (not battery I think). I use it on a laptop, pretty cool.


I downloaded it and fired it up in a vm session and I am impressed. It is such a wonderful distro IMO. This is great because it is so straight froward. Sadly at this time I might stick whit the setup I have and force my self to go straight open box or flux box. I have to much settings and applications I installed on my current machine. Unless you can suggest an easyway to move my seetings and data to crunchbang? :)

---

### Post by Nxion on 2008-08-21
> **CarlosNYB said:**
> With fluxbox you can get the network manager applet from Gnome to appear in the apps dock.

Open the file ~/.fluxbox/startup with a text editor

Down later in the file you will see this section:

# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#

Type in this line:

```
nm-applet &

```Save.


Thanks for this. Ill give that a try as well :)

---

### Post by snowpine on 2008-08-21
> **Nxion said:**
> I downloaded it and fired it up in a vm session and I am impressed. It is such a wonderful distro IMO. This is great because it is so straight froward. Sadly at this time I might stick whit the setup I have and force my self to go straight open box or flux box. I have to much settings and applications I installed on my current machine. Unless you can suggest an easyway to move my seetings and data to crunchbang? :)

USE THIS METHOD AT YOUR OWN RISK!
Crunchbang can be installed on top of an existing Ubuntu build using a script. The intention of this feature is that you can install the command line only using the Minimal CD, then "net install" Crunchbang. It is also theoretically possible to do this over an existing "full" install, but it is completely untested if it will mess up any of your settings/documents!!!

[http://crunchbang.org/forums/topic/crunchbang-linux-80402-alternative-installation](http://crunchbang.org/forums/topic/crunchbang-linux-80402-alternative-installation)

I would suggest testing it out in a virtual machine first. And back up anything important!

---

### Post by rockerphil on 2008-08-21
you could always do what i did and build your Ubuntu OS from the command line up using lightweight apps using the minimal ISO Ubuntu CD, here's the tutorial i used to achieve this, and just for a bit of info it runs great on my Dell Dimension 1500cx with a 500 MHz Intel Pentium processor and 128 MB of pc133 SD RAM

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

hope this helps,

Phil

---

### Post by Nxion on 2008-08-21
> **snowpine said:**
> USE THIS METHOD AT YOUR OWN RISK!
Crunchbang can be installed on top of an existing Ubuntu build using a script. The intention of this feature is that you can install the command line only using the Minimal CD, then "net install" Crunchbang. It is also theoretically possible to do this over an existing "full" install, but it is completely untested if it will mess up any of your settings/documents!!!

[http://crunchbang.org/forums/topic/crunchbang-linux-80402-alternative-installation](http://crunchbang.org/forums/topic/crunchbang-linux-80402-alternative-installation)

I would suggest testing it out in a virtual machine first. And back up anything important!

Does the installer scripts have to run while I am logged to the machine I want to transform? Or do I have to boot off a live CD and run it that way?

---

### Post by Nxion on 2008-08-21
> **rockerphil said:**
> you could always do what i did and build your Ubuntu OS from the command line up using lightweight apps using the minimal ISO Ubuntu CD, here's the tutorial i used to achieve this, and just for a bit of info it runs great on my Dell Dimension 1500cx with a 500 MHz Intel Pentium processor and 128 MB of pc133 SD RAM

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

hope this helps,

Phil

Does this mean that the mini cd is a live cd. I don't mean to sound stupid but I'm just trying to clarify :|

---

### Post by Nxion on 2008-08-21
> **snowpine said:**
> 
I would suggest testing it out in a virtual machine first. And back up anything important!

Do you mean to try this on a blank vm session meaning like it is installing from scratch or load a clean install of ubuntu and go from there?

---

### Post by snowpine on 2008-08-21
> **Nxion said:**
> Does the installer scrips have to run while I am logged to the machine I want to transform? Or do I have to boot off a live CD and run it that way?

The scripts are run from the computer you wish to transform. It is sort of the crunchbang equivalent of 'sudo apt-get install ubuntu-desktop' if you know what I mean. 

This installation method is designed for a fresh crunchbang install on low-spec computers that can't run the crunchbang live cd (which you have already tried, yes?). It is not really tested for your purposes, so proceed with caution.

Follow the link from my last email for more info.

---

### Post by snowpine on 2008-08-21
> **Nxion said:**
> Do you mean to try this on a blank vm session meaning like it is installing from scratch or load a clean install of ubuntu and go from there?

Install Ubuntu+Openbox in a VM session and then try to put Crunchbang on top of it. I am suggesting it as an experiment to see what will break! I am personally curious so I want you to do the research for me. :)

My completely untested assumptions are: 
1. Most/all of your applications will still work.
2. All of the data in your /home directory will still be there.
3. Any existing Openbox configuration (menus, startup, themes, etc.) will be replaced by Crunchbang.

I enjoy this kind of experiment. I have done some crazy things like trying to put Fluxbuntu on top of Crunchbang... :)

---

### Post by snowpine on 2008-08-21
> **Nxion said:**
> Does this mean that the mini cd is a live cd. I don't mean to sound stupid but I'm just trying to clarify :|

The Minimal CD is not a live CD--it's installation only. Boot from it and type 'cli' and it will install command-line Ubuntu (no apps or GUI) as a base for you to build up your own system. I believe the Alternate Install CD also has this as an option (never tried it personally).

The Minimal CD is what you would generally use as a starting point if you wanted to make your own distro like crunchbang or fluxbuntu.

---

### Post by rockerphil on 2008-08-21
> **snowpine said:**
> The Minimal CD is not a live CD--it's installation only. Boot from it and type 'cli' and it will install command-line Ubuntu (no apps or GUI) as a base for you to build up your own system. I believe the Alternate Install CD also has this as an option (never tried it personally).

The Minimal CD is what you would generally use as a starting point if you wanted to make your own distro like crunchbang or fluxbuntu.

this is exactly what i did, and yes, the alternate install CD has the same option, but if you're installing just a CLI why download hundreds of megs when you can download the minimal ISO which is less than 10 MB? hope this info was helpful,

Phil

---

