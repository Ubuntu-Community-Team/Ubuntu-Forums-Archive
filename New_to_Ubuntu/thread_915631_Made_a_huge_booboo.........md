---
title: "Made a huge booboo........"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by jakewc2 on 2008-09-10
I have been playing around with my ubuntu, and somehow,I have added something that has now madeitkubuntu.and I cant get it back to how it was.Problem is, I'm not sure what it was I added that turned it into Kubuntu. :(

Can somebody help me return my program back toubuntu?

Thank you.

John.

---

### Post by u-slayer on 2008-09-10
When you start GDM. There is an option to choose your "session" Choose Gnome.

---

### Post by skippuff54 on 2008-09-10
sounds like u installed the k desktop environment (kde) which is a different graphical user interface (GUI) than GNOME, which ships with ubuntu. see if u can use synaptic or whatever ur package manager, i guess now its kynpatic, to install GNOME.

---

### Post by skippuff54 on 2008-09-10
> **u-slayer said:**
> When you start GDM. There is an option to choose your "session" Choose Gnome.

yeah try that first before u go installin/uninstallin anything

---

### Post by jakewc2 on 2008-09-10
Oh wow,thank you so much for all you messages.

I only installed this yesterday, by GDM what do you mean? When I start the pc, I only get two options, one is to start windows the other to start Ubuntu, when I clcik on that, it goes through the process, and starts Kubuntu.

Sorry to be so dumb. :(

---

### Post by hyper_ch on 2008-09-10
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---

### Post by jakewc2 on 2008-09-10
Have changed the title, still not sure its good enough sorry about that. :( Was in a bit of a panic. :(

---

### Post by kpkeerthi on 2008-09-10
GDM is your login screen. Stands for GNOME display manager.

---

### Post by skippuff54 on 2008-09-10
do u recall installin anything "just to see what it was?" nothin wrong with that at all, good way to learn, but u may have inadvertently installed KDE over GNOME.

also, r u sure that u d/led the correct iso image? is it possible that u downloaded Kubuntu when u thought u were gettin ubuntu?

what do u see when u get to the login screen? is there a dropbox where u can choose ur session? if so, look for GDM. if u don't see it, it's likely that u somehow swapped out GNOME for KDE.

---

### Post by jakewc2 on 2008-09-10
Hi, I thought that might be what you meant, I went in logged off, then the Kubuntu log in screan came up, I chose Gnome, but it still has Kubuntu come up. :( Teach me to stop meddling. :( 

What else do I need to do?

Is Kubuntu better than Ubuntu? Does it make a difference? Apart from what it looks like? 

Also, I installed Thunderbird yesterday, it worked when it was Ubuntu, not it wont work, gives an error

Could not launch application

ailed to execute child process "/home/jakewc2/.mozilla/firefox/jlyjhf4i.default/bookmarks.html" (Permission denied)

How do get that back as well?

Thank you for you help.

p.s. I did try to change the thread title, but it looks like as I logged out, I cant change it now, sorry about that. :(

John

---

### Post by jakewc2 on 2008-09-10
What happens is, when I start the pc, I get the partition page up,with Windows and Ubuntu, I choose Ubuntu, then when the screen comes up, it is Kubuntu, I look forthe drop down menu, choose Gnome, it logs in, In the system drop down menu it has Ubuntu, but in ther other drop down menus its got all Kubunu menus. :(

---

### Post by jakewc2 on 2008-09-10
Just wondered, would it be better just to uninstall Ubuntu and reinstall it?

---

### Post by Elfy on 2008-09-10
When you install kubuntu-desktop - the menus become rather on the large side. If you've logged into gnome that is what you are running.

To get back try this

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by skippuff54 on 2008-09-10
> **jakewc2 said:**
> Hi, I thought that might be what you meant, I went in logged off, then the Kubuntu log in screan came up, I chose Gnome, but it still has Kubuntu come up. :( Teach me to stop meddling. :( 

nah keep up ur meddling there's no other way to learn.


> What else do I need to do?


try logging in, find ur package manager, which should be called synaptic (ubuntu) or kynaptic (kubuntu) and should be located at System > Administration > Synaptic Package Manager. 

this is most likely where ur experiment went awry in the first place. fyi a package is a set of software, and u will often have to install dependent packages (many times called libraries or libxxx) when u need a certain program.

GNOME is what u want for the traditional ubuntu system. search for it with the package manager, or search the forums/internet for instructions on how to re-install.

> Is Kubuntu better than Ubuntu? Does it make a difference? Apart from what it looks like? 

read more here :[http://www.psychocats.net/ubuntu/kde]("http://www.psychocats.net/ubuntu/kde")

in my experience KDE/kubuntu is a little slower and less stable, but looks cooler.
> 
Also, I installed Thunderbird yesterday, it worked when it was Ubuntu, not it wont work, gives an error

Could not launch application

ailed to execute child process "/home/jakewc2/.mozilla/firefox/jlyjhf4i.default/bookmarks.html" (Permission denied)

How do get that back as well?

1. thunderbird or firefox? thunderbird is an e-mail client, firefox is the web browser.

2. apparently having to do with permissions. likely that when u switched to KDE, some permissions got mixed up and firefox/tbird doesn't realize that it's really u who is logged in trying to access the program. search the forums/internet for that error message and how to correct permissions in different desktop sessions.

lastly i am gonna offer this: if u have time on ur hands and feel like learnin the hard way, keep pressin on. it will be worth it in the long run when u encounter other issues (and u will). but that said, don't hesitate to simply reinstall if u hit a roadblock and need the computer for productivity.

---

### Post by jakewc2 on 2008-09-10
Hi, I just wanted to say thank you for not giving up on me, I really appreciate it. I am not that good with new stuff, I fiddle get lost and panic. :( To have somebody that seems to understand is really helpful. :) I will try what you have suggested.

It is Thunderbird that I'm trying to open, and that is the error I get, which does seem odd. That error only came when I messed up. I click on the TB Icon, and that error appears.

---

### Post by skippuff54 on 2008-09-10
ok, thunderbird and firefox are obviously written by the same folks over at mozilla. and i'm guessin that they've set up thunderbird to do something, i dunno what, with your firefox bookmarks when TB starts up. just a guess.

i'm also guessin that when u switched desktop environments (gnome ---> kde), something happened to a file or files somewhere that associates your desktop user with the mozilla programs. specifically, the computer lost the knowledge that you, under your login name for your new desktop environment, are allowed to start up firefox and/or thunderbird.

is firefox workin?

i'm guessin yet again that this thunderbird issue relates back to the same issue you are facin with your desktop environment. the TB error in particular has to do with permissions for your desktop user.

fyi i'm goin to sleep soon so if u don't hear back, no offense or nothin but i'm gonna have to check back tomorrow.

---

### Post by t0p on 2008-09-10
If I understand you correctly: you installed kubuntu-desktop, which has given you the KDE desktop and KDE applications.  You don't want the KDE stuff, you want to switch back to the original ubuntu stuff.  Right?

If that's what you want to do - have you followed the advice given to you earlier by **forestpixie**?  If you follow that advice, you'll get what you want.  You'll get back to the original ubuntu set-up.

**EDIT:** here's the link forestpixie gave you to follow - [http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/puregnome").  Click on it and follow the instructions.

---

### Post by jakewc2 on 2008-09-10
Hi everybody, unfortunately, I had a bit of a problem with the things I was fiddling with, and ended up messing things up really badly, in the end I had to reinstall. This time I think I have everything in order, well it seems to be.

Just wanted to say thank you for all the suggestions, they really helped.

---

