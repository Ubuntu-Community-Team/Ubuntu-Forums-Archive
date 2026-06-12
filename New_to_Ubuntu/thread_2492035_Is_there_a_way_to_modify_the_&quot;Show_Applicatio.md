---
title: "Is there a way to modify the &quot;Show Applications&quot; launcher/menu/screen?"
date: 2023-10-28
forum: New to Ubuntu
---

### Post by ozaz on 2023-10-28
Hi,

I'm new to Ubuntu (and Linux in general). Up to now I've mostly been using Windows.
I've installed Ubuntu Desktop 23.04.3 LTS.

I've tried to give it some time, but I'm not particularly keen on the launcher/menu/screen that you get to by clicking the "Show Applications" button on the dock (not sure what the proper term is, so I'll just refer to it as a launcher in the remainder of this post). Are there any user-configuration settings for this launcher? I've been looking through the system settings app but I can't find anything.

Here are behaviours that I'd like to adjust if its possible
* I don't like that when an application is added to favourites it gets removed from the launcher
* I don't like that application names get truncated and you have to hover mouse over the icon to see the full name
* I'd like to be able to switch to vertical scrolling instead of horizontal scrolling
* I'd like to be able to increase the number of rows of icons that are shown on the screen

If there are no options to modify the behaviour, is it possible for me to install a different launcher to replace "show applications"?

I'm aware that I could try a different flavour of Ubuntu, but I'm first trying to establish what I could do instead of this, as the "show applications" launcher is really the only aspect of the interface that I'm not keen on.

Thanks

---

### Post by vanadium on 2023-10-28
I use a Gnome Shell extension, [Switcher](https://extensions.gnome.org/extension/973/switcher/) by dlandau. It is a highly efficient keyboard based launcher that reveals itself as a list. It actually also doubles as an efficient window switcher. Personally, I also do not like the full screen launcher, because I find this way too disruptive in my workflow.

You may also consider Gnome Shell extensions that open a more traditional menu when you click "Activities".  [ArcMenu](https://extensions.gnome.org/extension/3628/arcmenu/) by andrew_z likely is king here, being around for a long time and very well maintained. It presents a classical menu with a layout of your choice that is both clickable and searchable.

---

### Post by Dennis N on 2023-10-28
Gnome has a fast search function for launching any application. I never use that grid. 
Press super key to reach the Overview screen. 
Start typing the name of what you want to launch until it's icon appears.
Highlight it and press Enter to launch.
I also returns results based on general words like 'text', which will return the text editors.
It's my preferred method for launching applications not pinned to the dock.

The search also finds other content (Settings, files, and even software in the repository that matches your search and not yet installed). Very handy.

---

### Post by ozaz on 2023-10-28
> **vanadium said:**
> I use a Gnome Shell extension, [Switcher]("https://extensions.gnome.org/extension/973/switcher/") by dlandau. It is a highly efficient keyboard based launcher that reveals itself as a list. It actually also doubles as an efficient window switcher. Personally, I also do not like the full screen launcher, because I find this way too disruptive in my workflow.

You may also consider Gnome Shell extensions that open a more traditional menu when you click "Activities".  [ArcMenu]("https://extensions.gnome.org/extension/3628/arcmenu/") by andrew_z likely is king here, being around for a long time and very well maintained. It presents a classical menu with a layout of your choice that is both clickable and searchable.

Thanks. I will take a look at these. I think I had already read somewhere that extensions existed, but I didn't know where to go to look for them.
Is there a reason I can't find them in the ubuntu software store and need to install from website instead? 

> **Dennis N said:**
> Gnome has a fast search function for launching any application. I never use that grid. 
Press super key to reach the Overview screen. 
Start typing the name of what you want to launch until it's icon appears.
Highlight it and press Enter to launch.
I also returns results based on general words like 'text', which will return the text editors.
It's my preferred method for launching applications not pinned to the dock.

The search also finds other content (Settings, files, and even software in the repository that matches your search and not yet installed). Very handy.

Thanks. I had actually discovered this already. However, similar to my initial post I don't like that the application names are truncated in the search results, and worse, hovering over them doesn't reveal their full name (unlike pre-search). I also didn't mention that I'm looking to setup a couple of home computers that will probably also be used by some family members who have little interest in learning new ways of doing things. This includes one who never uses the search feature on their smartphones to quickly get to applications no matter how many times I tell them this feature exists (probably because they don't remember the full names of the applications). Hence desire for a software launcher that provides better ease/clarity whilst simply browsing the listed applications.

---

### Post by vanadium on 2023-10-29
> **ozaz said:**
> Thanks. I will take a look at these. I think I had already read somewhere that extensions existed, but I didn't know where to go to look for them.
Is there a reason I can't find them in the ubuntu software store and need to install from website instead? 

You are touching the weak spot of Gnome Shell extensions. These are for the majority third party efforts. They can break some functionality or cause problems, and may suddenly not anymore be maintained. So yes, it is up to yourself to trust or not trust an extension.

Ubuntu ships a few in the software center, but the list has much decreased in recent versions of Ubuntu. You can list them with the command "apt-cache search gnome-shell-extension | grep gnome-shell-ext".

The package "gnome-shell-extensions" contains a few officially supported extensions by the Gnome developpers themselves. These mostly are intended to make Gnome Shell behave somewhat like the old Gnome 2, with a top panel including an "Applications" and "Places" menu, and a taskbar at the bottom. The "Applications"  menu indeed will give you a traditional dropdown menu, but it is not searchable.

---

### Post by tea for one on 2023-10-29
> **ozaz said:**
> Thanks. I will take a look at these. I think I had already read somewhere that extensions existed, but I didn't know where to go to look for them.
[https://github.com/mjakeman/extension-manager](https://github.com/mjakeman/extension-manager)
The package is in the universe repository.
If you want to try it, you can install it with this command:-
```
sudo apt install gnome-shell-extension-manager
```

---

### Post by Dennis N on 2023-10-29
You can't easily manage extensions without the gnome-shell-extensions-manager. You need it as well as Tweaks to customize Gnome and make it really usable. You can search and find numerous lists of "best" extensions to get some ideas. For Gnome 44 & 45, I use these:

All Widows
Places Status Indicator
Applications Menu
Media Controls
Net Speed Simplified
Removable Drive Menu
Workspace Indicator
User Themes
Blur My Shell
Just Perfection

---

