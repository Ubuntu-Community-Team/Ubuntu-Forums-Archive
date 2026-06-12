---
title: "Huawei e220 (and variants, any network) simple n00b HOWTO"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by Fingers &amp; Thumbs on 2008-06-22
Welcome to my first HOWTO.
   Before I begin, I would like to point out that I am NOT a computer expert, but after 6 months spent with ubuntu I have come to love computers as I no longer feel restricted or dictated to by my OS, in fact, I feel liberated, and I would like to thank all of the forum members as it is their contribution that makes all of the hurdles of computing shrink to a size that I feel I can approach with confidence.

  As a result, I now feel confident enough to write a HOWTO and believe I actually have one to fill a much needed gap.

  Anyway.....

Initially when I was trying to set up my e220, it was, quite simply, a headache. There are dozens of threads, within these forums alone, and countless elsewhere, but as these were generally responses to threads along the lines of "HELP!! Modem not working" they're generally asking for that users specific outputs and troubleshooting them, without explaining what was actually going on.

One HOWTO exists by tazz_tux, and I must acknowledge this as it definately helped me a gain a better understanding, although for a n00b like myself much of it was over my head.

So lets get your modem working shall we......

Firstly, you should make sure you have wvdial installed, it is in the repositories, you can either open synaptic package manager and look for it there.

Main menu >System >Administration >Synaptic Package Manager

 or open a terminal and type

```
sudo apt-get install wvdial
```

Now, with your modem plugged into an available USB port...
(note:: this is more reliable connected directly to your computer as opposed to a hub, and also, some users report problems with the longer cable, but I have had no such problems on the 5 I have set up personally.)

```
sudo wvdialconf
```

What this does is reads all of the settings you will need directly from your modem and writes them to a file called wvdial.conf. Without sudo it will read from the modem but cannot write the file.

IMPORTANT!! You should NOT edit any of the completed lines in wvdial.conf, the settings that the above command wrote to that file are unique to your modem/service provider, so copying anyone elses from a thread will only prevent yours from functioning. However you will need to edit 3 lines of text: Phone, Username and Password.

Again, in a terminal type...
```
sudo gedit /etc/wvdial
```

This will invoke your text editor (gedit) to open the file at location /etc/wvdial.conf, with administrative privaledges (sudo).

This will look something like this:

```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 9600
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
; Phone
; Password
; Username
```

As you can see, Phone, Password and Username are not designated and are also preceeded by a ; followed by a space. First of all delete the ;'s and spaces so that P,P and U respectively are the first characters on their lines. now following the same format as the completed fields add ( = )to each line and give them a value, so you should have something that looks like this.
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 9600
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = *99#
Password = Anything
Username = Anything
```

Before you save the file and exit, make a note of the second word in the first line, in the case of my example (Defaults) This is the name of the profile you will need to invoke for a connection.

How you wish to connect now is a matter of preference, I will now explain your options and try to outline the pro's and cons of each.

Firstly, If you feel happy having a connection with no GUI, no taskbar applet or any visual feedback on your desktop, then it's very easy.

Press Alt-F2 and type 

```
wvdial Defaults
```

Or replace the word Defaults with whatever was in the first line of your wvdial.conf.

If you wish for your modem to connect automatically at log on, take your mouse to the the panel menu and navigate >System >Preferences >Sessions and under the "Startup Programs" Tab, click the "Add" button and where it says "Command" Type:

```
wvdial Defaults
```

Be sure also to fill in the "Name" box, but what you type in there is up to you, simply "Modem" or "E220" is ideal for your own future reference.





Now you may prefer a graphical user interface to get connected, if so you have a few choices.

If you use gnome then i reckommend gnome-ppp

```
sudo apt-get install gnome-ppp
```

for kde...

```
sudo apt-get install kppp
```

Another one some people are using is vodafone-mobile-connect-card-driver-for-linux, (what amouthful) but you will not find this in the repositories and it is quite a bulky program (like it's name) that requires rather a lot of python dependencies. It does have some extra functions but I am yet to see any of them work, although to be fair I have not tried it with a vodafone sim, but it will still connect you nonetheless.

Whichever utility you choose the following instructions are the same.

If you closed your text editor after saving wvdial.conf then type:

```
gedit /etc/wvdial.conf
```

To bring it back up. Notice there was no sudo this time? Don't worry, Admin privaledges aren't necessary as we won't be editing the file, we just need that information at hand.

All that needs to be done is to complete any fields in your ppp's GUI's settings, using wvdial.conf as reference.

Some points of possible confusion explained.

What's an init string??

see the line in wvdial conf that looks something like  ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK, well that's what you need to put in the init string box.

What's the phone number??

My connection is with 3uk, so the number I set mine to dial is *99#
If you have another provider it will no doubt be different, but google should be able to answer that, or contact your provider.

That's it, click connect you should be up and running. try opening up your browser and searching, if all is well, happy browsing. Perhaps you get a message saying "Offline Mode" This is just Firefox thinking it knows best, simply click on the browsers "File" in the tool bar and deselect "Work offline"

Still no connection???

If you're using a GUI to connect, there may be a function called "Stupid Mode" selecting this "apparently" forces your modem to ignore init strings,and will usually sort this problem, but at this point I am unable to explain why and I'm only just scratching at what an init string does myself so I'll avoid any further details here to avoid confusion or giving misleading info. I may edit this at a later date if I concider it appropriate

If your GUI doesn't have this option, or you have opted for my no-GUI approach, then you can go back to....

```
sudo gedit /etc/wvdial.conf
```

And add the line...

```
Stupid mode = 1
```

Now I hope you are connected.

As I mentioned at the beginning, I am no expert, I am just relaying my experience of setting up 5 such modems, perhaps this howto doesn't work for you, if so leave a message, I'm quite sure I've read just about everything on the net about setting it up under linux, so if you have a problem, I've probably heard it before, and will probably know where to look.

One final note, If you have used this HOWTO and are still having problems, please let me know. Maybe you think I could have been clearer about something. In any case all feedback will be welcomed and appreciated. If you have got it working, which I sincerely hope you have, please leave a message saying which type of setup you opted for, which GUI, or no GUI, this could prove helpful to others in the future.

Just as I hope you have found this helpful.

---

### Post by snowblind on 2008-06-28
Thanks Fingers & Thumbs. Worked nearly flawlesly.

One thing to add, I had to enter something in to Username and Password box and click remember password.

Then it worked. :)

---

### Post by hyper_ch on 2008-06-28
If you format it a bit (titles and stuff) you should publish that in the Tutorials section ;)

---

### Post by Fingers &amp; Thumbs on 2008-06-28
Ah! yes, thanks for pointing that out snowblind, an oversight on my part, I shall edit that.

Thank you also, hyper_ch for the heads up. As a relatively new user I am a little ignorant of the forums protocol, I will do that, but first I will make some ammendements as I have learned some other points through experimentation

---

