---
title: "How do I find and run an installed program?"
date: 2015-08-13
forum: New to Ubuntu
---

### Post by Tony_Fendall on 2015-08-13
I have installed 'Fraqtive', or so Ubuntu says, and I can see a screen shot in 'Software Manager' but how do I find it and run it.
I have searched everywhere on the computer.  
Most frustrating; why can't software be easily installed like 'Windows'?
Tony

---

### Post by Bucky Ball on 2015-08-13
How did you install it? Have you tried opening a terminal and typing:

```
fraqtive
```

then hitting return? Make sure you type in the exact name of the software (correct spelling). Let us know what happens.

---

### Post by stalkingwolf on 2015-08-13
im running Mint 13 mate, on this system it is under education.

---

### Post by Bucky Ball on 2015-08-13
How did you install it? Have you tried opening a terminal and typing:

```
fraqtive
```

then hitting return? Make sure you type in the exact name of the software (correct spelling). Let us know what happens. 

> **Tony_Fendall said:**
> 
Most frustrating; why can't software be easily installed like 'Windows'?
Tony

If you install from the official repos they generally do install easily. And Ubuntu is not Windows. ;)

When posting for support give as much info as possible. Release and flavour you are using would be a help.

Just noticed this:

> **stalkingwolf said:**
> im running Mint 13 mate, on this system it is under education.

Did you install from Software Centre/Synaptics and that's where it ended up, stalkingwolf?

---

### Post by grahammechanical on 2015-08-13
I am using Ubuntu 15.10 with the Unity user interface and as a test I have just installed through the Ubuntu Software Centre the application called Fractive. An icon for it appears in the Launcher and an icon for it also shows up in the Dash Applications scope Installed filter. If I type "fraq" the application icon shows up.

The installation was very easy. I found the application in the Software Centre and I clicked the Install button. No. I most definitely do not want Ubuntu to be more like Windows.

Removal could not be more easier either.

---

### Post by Tony_Fendall on 2015-08-13
I have found an icon for program search at the top of the left hand icons and it's in there.
Can you put icons for favourite programs on the desktop, if so how.
Ubuntu 14.04
Tony

---

### Post by tristan16 on 2015-08-13
> **Tony_Fendall said:**
> I have found an icon for program search at the top of the left hand icons and it's in there.
Can you put icons for favourite programs on the desktop, if so how.
Ubuntu 14.04
Tony

Open Nautilus, click on Computer, and navigate to /usr/share/applications. Find the program you want on the desktop, right click it, select "Copy to..." and select the desktop.

IMO, Ubuntu seems to prefer you lock programs to the launcher rather than use the desktop, but it works either way.

---

### Post by Geoffrey_Arndt on 2015-08-13
Perhaps Tony is already referring to the launcher . . . may not know the difference betwixt the launcher and the desktop.

Tony . . . IF you are running the standard Ubuntu with the "Unity" desktop, you can find your program icons easily by clicking on the topmost icon in the launcher (which is called Dash, and is a search tool.).   Then, you'll see various icons depending on what you type in the search field.

Bottom line Tony, , , it's not rocket science, you just select and drag the icon displayed via search, over to the launcher strip at the left side of screen.

There are plenty of tutorials about the ABC's of Ubuntu (or any other Linux version) on youtube.com.    Just watch 2 or 3 of those - - you'll have no trouble at all.

---

### Post by SeijiSensei on 2015-08-13
> **Tony_Fendall said:**
> Can you put icons for favourite programs on the desktop, if so how.

> **tristan16 said:**
> Open Nautilus, click on Computer, and navigate to /usr/share/applications. Find the program you want on the desktop, right click it, select "Copy to..." and select the desktop.

IMO, Ubuntu seems to prefer you lock programs to the launcher rather than use the desktop, but it works either way.

I'll take this opportunity to advertise for KDE and [Kubuntu]("http://www.kubuntu.org/").  To place a program launcher icon on the desktop in KDE, you find the program in the main menu, right-click its icon, and choose "Add to Desktop."  Can't be much easier than that.  There's also an "Add to Panel" option.

---

### Post by buzzingrobot on 2015-08-13
Applications that are properly packaged for Linux will put a file in /usr/share/applications.  information in that file is used by the desktop environment to find the appropriate icon for display, add an entry to a menu, etc.

Some poorly ported Windows application do not adhere to those standards.

In Unity, these icons appear on the Dash. The recommended way to locate one of these icons so you can launch it is to tap the Windows key and begin entering the name of the app, or, in most cases, something else that might relate to the app.  When enough of the name or other info has been entered to identify it, that icon will be displayed in the top left of the Dash.

The Launcher -- the dock fixed to the left side -- is populated by default. Icons can be added or removed at the user's pleasure. For example, a running app will display an icon in the Launcher.  A right click will show an option to keep the icon in the Launcher, or remove it if it is already there.

I like to use Unity by exploiting the virtual desktops to place one app on each desktop, avoiding icons on the desktop and avoiding the need to frequently minimize windows to clear space. But, that's just my preference. Using it in Windows-esque fashion is certainly as good an option. No one is keeping score.

---

### Post by CantankRus on 2015-08-13
Yes, I found it really hard too. #-o
Took at least 30 secs from opening the software centre to
having a fraqtive window open on my desktop. :rolleyes:

I've attached a video to illustrate all the trouble I had to go through.

---

### Post by mystics on 2015-08-14
> **Tony_Fendall said:**
> Most frustrating; why can't software be easily installed like 'Windows'?

Simply put, this isn't Windows. Things aren't going to behave the same here as they do in Windows. By that, I mean you'll rarely have the option to download an installer from online. Normally, searching for applications online will either send you to the Software Center, give you a tar or zip file with instructions for that specific application, or tell you to go to the terminal and type in various commands. 

That said, if you want to have a more traditional experience, you can use the Ubuntu Software Center. It behaves more like the Windows Store, Google Play Store, or Apple's App Store. That should feel a little more familiar. And while I'm not sure about other flavors, I know that in [Xubuntu]("http://xubuntu.org/"), installing from the Software Center will tell you where to find the application in the "start" menu (to put things in Windows terms).

Another alternative is to use the Synaptic Package Manger. It behaves relatively similar to the Software Center, in that you can search for applications and install them, but it will come across as a little more unwieldy at first. Still, I personally prefer it.

Basically, both of these options are easier on new users than typing commands in a terminal, and they are especially easier than downloading a tar or zip and following whatever instructions they give you. In the end, I would give at least one of these options a chance before completely writing things off as not being easy.

---

### Post by stalkingwolf on 2015-08-14
yes I installed it from synaptic.

I prefer the mate DE.  its just easier for me. but thats my choice.

---

