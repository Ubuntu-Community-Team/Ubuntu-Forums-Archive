---
title: "type in chinese"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by k12321 on 2008-11-12
I am a first time Ubuntu user
i have already installed the chinese language pack but i am having problems to type in chinese in firefox or other programs 
is there some shortcut key to change language more easily as there is in Windows Xp?
and how can i have the language setting on my desktop?

and yep am on ubuntu 8.10

---

### Post by seuzy13 on 2008-11-12
You can install scim on your computer along with Anthy, and then whenever you press Ctrl + Space, a toolbar will come up in the corner with some options and information and you can begin typing. I use this program to type in Japanese. I'm sure it's a little different for Chinese, but it's not hard to figure it out. If you need help installing, it would probably be easiest to open a terminal and type

sudo apt-get install scim anthy scim-anthy

All of the dependencies should install along with. If you would rather, you can also do this in synaptic (System > Administration > Synaptic Package Mangager) and find the packages scim, anthy, and scim-anthy.

---

### Post by k12321 on 2008-11-12
> **seuzy13 said:**
> You can install scim on your computer along with Anthy, and then whenever you press Ctrl + Space, a toolbar will come up in the corner with some options and information and you can begin typing. I use this program to type in Japanese. I'm sure it's a little different for Chinese, but it's not hard to figure it out. If you need help installing, it would probably be easiest to open a terminal and type

sudo apt-get install scim anthy scim-anthy

All of the dependencies should install along with. If you would rather, you can also do this in synaptic (System > Administration > Synaptic Package Mangager) and find the packages scim, anthy, and scim-anthy.


i've tried that before the ctrl space but it did not work let me try via the terminal

---

### Post by k12321 on 2008-11-12
still not working 
ie the ctrl 
i have already install both via terminal 
when i open text editor and right click scmi input method then it works but as soon as i close the text pad it disappears and i am unable to type in firefox or when chatting....

---

### Post by expatCM on 2008-11-13
I thought that Anthy was specific to Japanese ....

If you look for scim in synaptic you will find several additional items you can install which relate to the keyboard / simplified or traditional and similar matters.  Perhaps you want to review these to see if there is anything for you to consider there.

Do you see the icon of a keyboard in your system tray?  This will allow you to quickly switch between English and Chinese input.

I have scim in the System / Preferences / Sessions as an event loaded on startup .... 

I take it that you have enabled Chinese in the Language settings (System / Administration / Language support and clicked the option to allow complex character support?  If you did, when you click on Chinese and then on the Details underneath the window some more options appear ...

---

