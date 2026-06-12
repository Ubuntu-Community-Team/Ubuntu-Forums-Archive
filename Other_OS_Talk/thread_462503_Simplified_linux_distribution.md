---
title: "Simplified linux distribution"
date: 2007-06-02
forum: Other OS Talk
---

### Post by Pete White on 2007-06-02
I keep thinking this must have been done, but I have never managed to find it. So please point me at it and save me doing it myself!

I'd like to find (or failing that, create) a simplified Linux distribution for non-technical people, perhaps based on ubuntu.  A bit of background about my target audience.

- They don't know anything about computers. That means that they don't
  know about certain concepts.
  - "Operating system"
  - "Application / program" (though they sort of understand that there
    programs are something to do with computers)
  - "Document format"
  - Firewall. Nope, just too technical.
  - Viruses and security. Nope, again just too technical.
  - Server. Ditto.
  - Backup. Never heard of the concept.

- They do understand some concepts.
  - Email : somebody with a computer far away can send you stuff.
  - Photos : that stuff can include pictures of your grand children
  - ISP : you have to pay somebody for the connection
  - Word processor : my father spent his life using a manual
    typewriter. Now the computer does the same thing.
  - The web : you can use IE and go to a website with stuff on it you
    can read.

- A few of them have got jobs where they have had to learn to do stuff
  like use spreadsheets etc. However, their knowledge is really shaky
  outside the area of what they have directly learned to do.

I'd like to be able to install a computer for these people in under an hour.
That must set them up with all the stuff I'd install for them (firewall and security
settings, backup process etc.) with almost no choices. Unfortunately, if I
try this, there are just too many choices, and it takes too long. That's fine if
I'm installing my computer (I'll be there to fix it / figure out the problems)
but not if I'm installing for somebody else.

To get there from where we are, you'd need to just
- tweak the install a bit to reduce the number of choices and force them to do something sensible about security, backups and file layout
- write some simple task based documentation and provide it on screen

Does anybody know of such a project, to simplify linux install and use as much as possible, either as part of ubuntu or elsewhere?

cheers, Pete

---

### Post by Inxsible on 2007-06-02
I think distros such as Linspire, or Mandriva are very user oriented and when i say user oriented, i mean for users that you describe.

Ubuntu doesnt necessarily have to be *your* distro. There are many flavors of Linus available and depending on one's need, they can choose the one they like best and the one that best fits them and their usage.

---

### Post by raja on 2007-06-02
The default Ubuntu install is perfect for your purposes. It can be installed in about 30 mins, does not need anything special to be set up for security. You can browse the net, send email, use a word processor (maybe install Abiword and use instead of openoffice), view photos, etc out of the box. They dont have to worry about using antiviruses and anti-spyware, defragging the disk, etc. 

What more do you want?

---

### Post by tdrusk on 2007-06-02
You could even take a version of Ubuntu, set it up just how you like with icons on the desktop saying, "Internet","Word Processor", "Email", burn the iso to a CD, and be set.

---

### Post by smoker on 2007-06-02
> **Pete White said:**
> 
- They don't know anything about computers. That means that they don't
  know about certain concepts.
  - "Operating system"
  - "Application / program" (though they sort of understand that there
    programs are something to do with computers)
  - "Document format"
  - Firewall. Nope, just too technical.
  - Viruses and security. Nope, again just too technical.
  - Server. Ditto.
  - Backup. Never heard of the concept.

- They do understand some concepts.
  - Email : somebody with a computer far away can send you stuff.
  - Photos : that stuff can include pictures of your grand children
  - ISP : you have to pay somebody for the connection
  - Word processor : my father spent his life using a manual
    typewriter. Now the computer does the same thing.
  - The web : you can use IE and go to a website with stuff on it you
    can read.

hi, have a look at this link, it may be something that would interest you:
[http://cl33n.com/faq.html](http://cl33n.com/faq.html)

no one could fail to use this, it only starts a web browser, and you do everything through that!

best of luck:D

---

### Post by tgalati4 on 2007-06-02
Linspire/Freespire may fit the bill.  It's the "AOL" of Linux.  Since new versions of Freespire will be based on Ubuntu, they have already done most of the simplification work already.  The Click-N-Run (CNR) makes additional program installation easy, although sudo apt-get install anythingyouwant also works in the terminal.

Freespire uses KDE for the desktop so it's a little heavier (that is slower) to use on older hardware.  If you have a newer machine, then Freespire may be the ticket.

You can always configure the default Ubuntu to get it exactly how you want it, but that takes time.   Besides, people are individuals, so it doesn't really make sense to configure them all the same.  As soon as they get them:  "How do I load games?"

Load either Ubuntu or Freespire and let folks go wild.

---

### Post by aysiu on 2007-06-02
What you're describing sounds a lot like Ubuntu.

Of course, other distros could also fit the bill: Linux Mint, PCLinuxOS, Xandros, Mepis, Blag, Linspire.

Bottom line, as long as someone (probably you) installs and configures the distro, the choice of distro won't matter so much as how you install it for them. Ubuntu's defaults are pretty good, but if someone doesn't understand what the difference is between an operating system and a program, she's not very likely to be able to install *any* operating system.

---

### Post by ugm6hr on 2007-06-03
Xubuntu7.04 is reasonable as a starting point.  It includes Firefox, Thunderbird, AbiWord and GAIM.  Obviously, their internet would have to be connected for them (perhaps with Network Manager as an extra install if wireless).  They would also need media codecs / flash as a minimum, which are not included in any Ubuntu.

Removing the multiple "virtual desktops" (workspaces) is probably advisable, since it can be confusing to *lose* your open windows with a single click.  This takes 10 seconds to remove.

Adding launchers to the taskbar for all the programs they might use also makes things easier, so they never have to use the Applications menu at all (and it could even be removed in their username, with it present for the Administrator).  As mentioned, similar launchers could be on the desktop too, with "easy" appropriate names and icons.  This will take slightly longer, depending on how many programs they want.  A "You've got mail" alarm is also useful (again - easy).

The auto-mount function for USB/CD is another important factor, since the concept of mounting is quite abstract for most people in this category.  The thing they will have to be taught is how to unmount these (this is no different than "safely remove" in Windows, but can cause more problems if not adhered to).  Xubuntu has an add-on "mounting/unmounting" taskbar icon - but I've not used it - but it sounds like it works like the "safely remove hardware" icon in Windows.

One thing I think would be useful for some people is to disable the minimise/maximise/taskbar size window options.  If you could make every application open in maximised size, and remove the bottom taskbar, users would find it difficult to open more than one application at a time.  While this would be severely limiting for most, I think it is necessary for some people who can't help but *lose* their open windows on the desktop workspace.

As for getting this done in 1 hour....

Oh... forgot about the pictures issue.  Haven't tried it on Linux yet (but it is available) - Picasa would be perfect for digital albums.  You don't even need to organise your photos - they can just live in the main user directory, and Picasa should theoretically find and sort them.  I believe the installer includes WINE, but is available as a .deb, so should theoretically just work.

The only downside with (X)Ubuntu is that you have to login.  So they would have to remember their username and password.  Generally, any Linux distro that doesn't require this automatically logs in as root, which I think is a recipe for disaster.

---

### Post by Tux Aubrey on 2007-06-03
I think a guy called Steve Jobs already did this.  The problem he had - and you will also have - is there is no such thing as a standard PC or a standard user.  He solved the machine problem by making everyone buy the same hardware.

Personally, I think Ubuntu is getting pretty close to being idiot proof (although I do my darndest to disprove that every day).

---

### Post by Feba on 2007-06-03
I've considered trying to make something like this, Newbuntu, the main point would be: simplifying the GUI by making everything easy to access and basically eliminating the moving/resizing portions of window management (you can minimize or you can maximize), change some standard apps around a bit (like, rename Firefox to Internet, Evolution to Email, and making GAIM into a single window+frames/tabs app, so it could be minimized/maximized.), make it impossible for the user to touch anything outside /home/, basically dumb it down enough where a three year old or a greatgrandmother could use it without having to worry about EVER messing something up. Ubuntu is already like this in some ways, although a simplified GUI could be useful to some people.

The main thing though, the people this would be most aimed towards would be the elderly, who can probably use regular ubuntu without screwing it up, and children, and to tell the truth I think simplifying an OS for kids would be doing them a disservice, since it just handicaps them later. Little kids are able to do some pretty impressive things if you let them, hell, I was able to use a VCR by the time I was 10 months old.

---

### Post by tdrusk on 2007-06-03
> **Feba said:**
> I've considered trying to make something like this, Newbuntu, the main point would be: simplifying the GUI by making everything easy to access and basically eliminating the moving/resizing portions of window management (you can minimize or you can maximize), change some standard apps around a bit (like, rename Firefox to Internet, Evolution to Email, and making GAIM into a single window+frames/tabs app, so it could be minimized/maximized.), make it impossible for the user to touch anything outside /home/, basically dumb it down enough where a three year old or a greatgrandmother could use it without having to worry about EVER messing something up. Ubuntu is already like this in some ways, although a simplified GUI could be useful to some people.

The main thing though, the people this would be most aimed towards would be the elderly, who can probably use regular ubuntu without screwing it up, and children, and to tell the truth I think simplifying an OS for kids would be doing them a disservice, since it just handicaps them later. Little kids are able to do some pretty impressive things if you let them, hell, I was able to use a VCR by the time I was 10 months old.

I think n00buntu would be the proper name. :P

---

### Post by Pete White on 2007-06-03
Thanks for all the feedback.

The question about "what's missing" I think is pretty straightforward. The software is (finally) there, and any one of a number of distributions is good enough. The documentation and process is hard enough that most people don't know where to start - and that's why I'm looking for a very simple install with very clear documentation targetted at new users.

I've had a look at freespire, and I'll have a shot at installing that and see if it's close enough for what I want. It's certainly closer than any other project I'd seen. If not, I'll probably just slap ubuntu on a box and start playing around with layout.

---

### Post by tgalati4 on 2007-06-03
The advantage of Freespire is it is in active development, so you can make suggestions and they may get incorporated.  Freespire will get rolled up into Linspire which is a boxed version that sells for ~$69 at your big box retailers.

Linspire has agreed to use Ubuntu as their base distribution, so any Ubuntu goodness will get rolled into Freespire/Linspire.  I look at Linspire as a Kubuntu with a little more polish and simplification of some configuration items.  Lift the hood and it's mostly Debian/Ubuntu.

I explained to my father-in-law (who had never used a keyboard before) that the current keyboard is a combination of typewriter and adding machine mushed together.  The functions keys were added because there were not enough keys available to do extra things.  "Escape" means "Get me outta here!"

He got it and now he sends me old-folks jokes.

Seniors are smarter than you think.  They made it this far didn't they?

---

### Post by ubromtoo on 2007-06-03
SMOKER :


     thank you for the CL33n link....it looks really fun !  :D

---

### Post by gn2 on 2007-06-03
Aysiu has already mentioned PCLinuxOS, which along with it's XFCE offshoot Sam Linux has to be the most new-user friendly distro.

Another option to consider is Wubi.

---

### Post by bone43 on 2007-06-03
> **Feba said:**
> I've considered trying to make something like this, Newbuntu, the main point would be: simplifying the GUI by making everything easy to access and basically eliminating the moving/resizing portions of window management (you can minimize or you can maximize), change some standard apps around a bit (like, rename Firefox to Internet, Evolution to Email, and making GAIM into a single window+frames/tabs app, so it could be minimized/maximized.), make it impossible for the user to touch anything outside /home/, basically dumb it down enough where a three year old or a greatgrandmother could use it without having to worry about EVER messing something up. Ubuntu is already like this in some ways, although a simplified GUI could be useful to some people.

The main thing though, the people this would be most aimed towards would be the elderly, who can probably use regular ubuntu without screwing it up, and children, and to tell the truth I think simplifying an OS for kids would be doing them a disservice, since it just handicaps them later. Little kids are able to do some pretty impressive things if you let them, hell, I was able to use a VCR by the time I was 10 months old.

There is a kids educatioanl version see here..

[http://www.edubuntu.org/](http://www.edubuntu.org/)

---

### Post by gimmy_bond on 2007-06-03
Pete,
you wrote what I have been screaming for quite some time.
IF Linux COMMUNITY WISHES TO BE A RESPECTABLE COMPETITION 0R REPLACEMENT TO MS WINDOWS. THEN BE ONE.  Unfortunately, even when KDE & GNOME are trying to provide GUI to make Linux a user friendly. It still remains the geek's world.

I for one, am an owner of small business. Even though I love to tinker with electronic gudgets. Nonetheless, for my work, I need to get from point A to point B as fast, easy, cheapest and most reliable method. I simply have no time, nor the inclination to dabble with arcane command lines to do the Job. (That is the very reason why DOS based OS took off only after GUI  in Windows was included. In my experience, this is the bottleneck which  holds people like me (and perhaps yourself) from moving from WIN to Linux. 

Perhaps this post should have been addressed to the KDE & GNOME developers. As more provision of "point-n-click" as more people will use the Linux OS.

---

### Post by Feba on 2007-06-03
Not educational, and not for n00bs, for people that only need a computer for a few games, chatting, internet, email, writing, and little more, something that would be as easy to operate as an RC car compared to a big rig.

Edubuntu looks alright, but it's more targeted to be used in education, not to be used for people who can barely use a computer.


And Gimmy, the command line can be much faster and easier than a GUI, once you learn how to use it.

---

### Post by tdrusk on 2007-06-03
I am going to set to work on a Ubuntu distro that it meant for old people and children. I will keep you up to date on how it is going. It won't be anything amazing, but I'm sure some people would find it useful.

---

### Post by pelle.k on 2007-06-03
> Does anybody know of such a project, to simplify linux install and use as much as possible, either as part of ubuntu or elsewhere?
See, the best things that have happened to linux from a user-friendly perspective the last couple of years is not the glue, i.e. the distro itself, but rather the pieces from which it is built.
A distro can provide a good base to play with. Beyond that, you're going to have to resort to ugly hacks. 100+ distros have tried, and largely failed at being the "perfect distro". I mean the "perfect distro" for the masses that is. I might not apply to you.
Some examples are dbus, hal, gnome-volume-manager, xorg (esp 7.3), ntfs-3g, xine, gstreamer, dcop. Those technologies made complicated tasks "easy" to handle.They weren't available until they were done. debian didn't make it happen, and neither did pclinuxos.
What i'm saying is, if you're going to build something "easier" than currently available (e.g. ubuntu, pclinux and whatnot), you will either have to do magic, or really ugly hacks that makes a mess instead.

> IF Linux COMMUNITY WISHES TO BE A RESPECTABLE COMPETITION 0R REPLACEMENT TO MS WINDOWS. THEN BE ONE. Unfortunately, even when KDE & GNOME are trying to provide GUI to make Linux a user friendly. It still remains the geek's world.
I'm not sure that the "linux community" at large wants a "REPLACEMENT TO MS WINDOWS". An alternative,sure, but not a replacement.
But were getting there. You can't just do "GUIs" on top of everything. You have to integrate new technologies that makes sense first. Like hal and dbus. before those two you didn't have gnome-volume-manager automount for ya.
A "GUI" solution back then would have been both messy and broken for the most part.

---

### Post by gimmy_bond on 2007-06-03
> **Feba said:**
> Not educational, and not for n00bs, for people that only need a computer for a few games, chatting, internet, email, writing, and little more, something that would be as easy to operate as an RC car compared to a big rig.

Edubuntu looks alright, but it's more targeted to be used in education, not to be used for people who can barely use a computer.


And Gimmy, the command line can be much faster and easier than a GUI, once you learn how to use it.

OK my good man / woman. I am ready to try learning the CLI. Could you please refer me to a site where all the ubuntu commands are displayed, and which I can print them into 1 or 2 pages and refer to them whenever need to.

thanks

---

### Post by Feba on 2007-06-03
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

If you didn't erase them, check out the Ubuntu links in your default firefox installation.

---

