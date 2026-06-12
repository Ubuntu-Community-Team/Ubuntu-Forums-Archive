---
title: "Pidgin Plugin Install."
date: 2008-08-08
forum: New to Ubuntu
---

### Post by PaperRoses on 2008-08-08
HELP!
I use Pidgin Instant Messenger, and I recently tried to install Purple Plugin Pack. I have all the files on my computer, but I need to know how to make them work for Pidgin. I'm only a beginner with Gnome Ubuntu so can anyone please post a clear step by step tutorial or tell me where to find one, to install the files onto Pidgin?
Thank you so much!
=] xx

---

### Post by freak42 on 2008-08-08
afaik it's in the repos..

type ```
sudo apt-get install pidgin-plugin-pack
```
in your favorite console or tick it in synaptic package manager to automatically download AND install it.

hth

---

### Post by PaperRoses on 2008-08-09
Say what?
Computer talk confuses me.
I'm an idiot, please talk slowly.:confused:

---

### Post by starcannon on 2008-08-09
In non geek speak that is in the menu's at:

System->Administration->Synaptic Package Manager

Search: pidgin-plugin-pack

Put a check mark in the box next to it

Click "Apply"

Then:
Click "Apply" again.

Close the windows, your plugins are now installed properly and will be updated automatically.

---

### Post by PaperRoses on 2008-08-09
Right.
I'm going to sound so stupid saying this
But I can't find Synaptic Package Manager on my System Administration Menu 
I have Keyring Manager
Network Tools
Printing
System Log
System Monitor
Update Manger
But nothing else :?
Is my computer weird or am I just REALLY stupid?
](*,)

---

### Post by starcannon on 2008-08-09
Paper Roses

1) your not stupid, I'm guessing your new to linux; that said, give yourself time to learn, not a single one of us in here was born knowing anything about Ubuntu

2)If the list you gave us was definitive, then something is wrong, either with your install, or your user account. The menu's are set up alphabetically, so if you don't see it in its appropriate spot, then either your gui is goofed up, your permissions are goofed up, or your install is goofed up.

Hang in there, and don't give up, I promise, truly, once you get the hang of this, its much much simpler than anything you've probably used before, your just getting through the "its all so new to me pains"

---

### Post by PaperRoses on 2008-08-09
In that case I'm stupid for Linux.
Ah well nevermind.
I might just switch to Windows..
But in the mean time is there any way that I can install the plugins WITHOUT the Synaptic Package Manager?
Thanks xx

---

### Post by starcannon on 2008-08-09
without the package manager try:

Applications->Accessories-Terminal

then either type or copy paste in the following:

```
sudo apt-get install pidgin-plugin-pack
```

That should get you the features your looking for.

GL

---

### Post by Sirron on 2008-08-09
While you've got the terminal open, try launching synaptic from there. Just type sudo synaptic and press enter. If works then rejoice, if not, it should tell you why.

---

### Post by PaperRoses on 2008-08-09
Okay...
Terminal is not doing anything interesting.
In fact, it's not doing anything but asking me for my password.
Then when I type it in it just does nothing.
I do think my computer is done for.
:(
Thanks for all the help though guys!
I think I might get Windows soon; I'm too stupid to use Linux :)
xxx

---

### Post by aloshbennett on 2008-08-10
Hi! Please dont go!

These are the issues you are facing:
1. You are not an administrator. Because of which,
   a) You dont have Synaptic Package Managaer
   b) Terminal doesnt do anything intersting.

Solution:
Under System-> Administrator -> Users and Group, select your user and click on 'Properties'. 
Under User Privilages tab, 'Administer the System' checkbox must be selected

These options would not be editable. To edit them, click on the 'Unlock' button on the 'User Settings' window.

For every installation of ubuntu, there must be a user with admin rights. For your ubuntu machine, looks like you are not the admin.

Who installed Ubuntu on the machine? Do you see someone else's name in the 'Users Settings' window?

Have a little patience and you wouldn't regret it :)

---

### Post by Sirron on 2008-08-10
I forgot to mention, sorry, when you type a password into the terminal, it doesn't show ****. It LOOKS like nothing is happening, but it is, just type your password and press enter.

But as the last post says, you're probably not an administrator. That's the same on Windows, if you don't have an admin account you can't change anything on the computer other than things like what fonts and screensaver to use.

Imagine if the computer was in a school, you wouldn't want the kids to be able to change system files, but you wouldn't mind if they could change the desktop wallpaper.

---

### Post by PaperRoses on 2008-08-11
Yea, that could be what's wrong...
That would probably make my brother the System Administrator.
I will talk to him when he gets back from work and ask to use his account.
Thanks guys :D
xxx

---

### Post by PaperRoses on 2008-08-24
Mkay..
Brother has Windows and doesn't have a clue how to work Ubuntu Linux.
Great.
So how do I become a System Administrator then?
:popcorn:

---

### Post by aloshbennett on 2008-08-24
Goto System -> Administrator -> Users and Groups
Click on Unlock button.

In the prompt that comes up, select your brother's account and ask him to enter his password.

Select your user, Properties button and User Privileges tab and give your self Administrator privileges.

Welcome to the real world, PaperRoses :)

---

### Post by PaperRoses on 2008-08-26
Well...
That option isn't there either =]
Still pretty far from the real world =/

---

### Post by Speed Demon on 2009-01-11
Download Ubuntu Intepid from Ubuntu.com and call it a day :P

---

