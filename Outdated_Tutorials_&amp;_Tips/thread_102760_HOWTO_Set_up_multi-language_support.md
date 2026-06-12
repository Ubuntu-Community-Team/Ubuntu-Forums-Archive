---
title: "HOWTO: Set up multi-language support"
date: 2005-12-12
forum: Outdated Tutorials &amp; Tips
---

### Post by sethmahoney on 2005-12-12
I had to go through this myself, and I know other people on here are struggling with the same issues, so I'm posting a howto for people who want to be able to switch between multiple languages.  Here goes:

**Installing a new keyboard layout:**
1.  Go to System->Preferences->Keyboard
2.  Click the "Layouts" tab
3.  Click "Add..."
4.  Pick your new keyboard layout.

**Adding the keyboard layout indicator:**
1.  Right-click on an empty spot on your Gnome panel.
2.  Click "Add to panel..."
3.  Select the Keyboard Indicator applet (in Utilities).
4.  Click Add.
Whenever you click on this applet, it will toggle between the available keyboard layouts.

**Setting up a hotkey combination to switch between keyboard layouts:**
(Quick note: Doing this step is _VERY IMPORTANT_, because if your screen locks, it will only accept your password if you are using your default keyboard layout.)
1.  Go to System->Preferences->Keyboard
2.  Click the "Layout Options" tab.
3.  Click "Group Shift/Lock behavior".
4.  Select a hotkey combination.
Now whenever you hit that hotkey combination, Gnome will toggle between available keyboard layouts.

**Setting up OpenOffice:**
1.  Open Synaptic
2.  Click "Search"
3.  In the search dialog that comes up, type "myspell-" (without the quotes) followed by the two letter language code for the language you want.  Select the package that comes up.
4.  To enable the user interface (along with word-completion) in the additional language, search for "openoffice.org" (without the quotes) and the two letter language code for the language you want.

**To switch between languages in OpenOffice:**
1.  Click on the Tools menu and then Options.
2.  Go to "Language Settings" and then "Languages"
3.  To enable spellcheck, under "Default languages for documents", select the language you want to use.  If you want to use that language only for the current document, check the "For current document only" box.  You may also want to change the Locale setting (dates and whatnot) and Default currency settings to the appropriate language.
4.  To change the user interface to the new language, set User interface to the new language.

**Help!  Non-Latin text looks funny in Nautilus!**
(Don't know about all languages that use non-Latin characters, but I know this works for Cyrillic and Arabic fonts.)
1.  Go to System->Preferences->Fonts
2.  Change the application font and the desktop font to Bitstream Vera Sans Roman.
3.  Change the window title font to Bitstream Vera Sans Bold.
4.  Click close.

Preview of coming attractions: Setting up templates so you don't have to go through this nonsense with every new document you create.

---

### Post by Triste! on 2006-01-11
thank you! thank you! thank you!

---

### Post by kosty on 2006-01-20
Hi,

I used to type in just two languages, but sometimes I need more. Is it possible to configure keyboard indicator so it would hold all the layouts desired, but cycle only some of them once corresponding key is pressed? (Idea was inspired by Fedora, where GSwitchIt behaves this way. )

regards.

---

### Post by sethmahoney on 2006-01-26
[QUOTE=kosty]Hi,

I used to type in just two languages, but sometimes I need more. Is it possible to configure keyboard indicator so it would hold all the layouts desired, but cycle only some of them once corresponding key is pressed? (Idea was inspired by Fedora, where GSwitchIt behaves this way. )

regards.[/QUOTE]

Not that I know of, but it is probably possible.  You might be able to do something with a script and a hotkey setup, but I'm not sure how you'd go about it.

---

### Post by lomomo on 2006-02-07
the keyboard layout indicator is not working for me.

It works when i set it up, but restarting session or rebooting makes it stop working. 
For makeing it work again i need to reset layout values and add again a new layout.

The hotkey combination does not work anyway.

Wat's wrong? i'm working with the spanish and arabic layouts.

---

### Post by sethmahoney on 2006-02-07
First question: Are you using Ubuntu or Kubuntu?

Second question: Are you using the Breezy release or the Dapper release?

---

### Post by lomomo on 2006-02-07
i'm using ubuntu breezy.

When i reboot or restart session the keyboard layout applet does only display the spanish layout, and clicking on it has no effect. Right clicking on it i can see the two layouts in the group submenu, but i can't make it work.

In the keyboard preferences the spanish and arabic layouts are installed, but i can only use the first one, and the only way to make arabic layout work is to reset values and install it again.

---

### Post by bountonw on 2006-02-07
Thank you for the big help.  I have a problem with synaptic and apt-get right now, but am working on that in another thread.  Anyway, I was able to install the Thai keyboard and can now toggle between the two languages nicely. Example: &#3616;&#3634;&#3625;&#3634;&#3652;&#3607;&#3618;&#3652;&#3617;&#3656;&#3618;&#3634;&#3585;&#3629;&#3618;&#3656;&#3634;&#3591;&#3607;&#3637;&#3656;&#3588;&#3636;&#3604;

The problem I have is in gedit when I type Thai it doesn't show the tops of some of the taller characters or the tone markers.  It seems that the lines are too narrow.  Is there anything that I can do about this?

Eventually I plan on writing a program that will replace text written in Thai with text written in English.  (This will have limited functionality, but I have a specific use for it.)  Not seeing the tone markers or the tops of characters makes it difficult to check the spelling of Thai words.

---

### Post by lomomo on 2006-02-08
hi bountonw, i'm having the same problem with arabic here. It will be nice to know how to fix this too.

---

### Post by lomomo on 2006-02-08
me again, my problem changing the keyboard layout seems to be working now.

What i did was reset default values, install again the arabic layout and disable all options in the layout options, by defoult i got the 'both alt keys together change group' enabled in the group shift/lock behavior. At this moment all seems to work nice, then i went back to the layout options and enabled the control+shift changes group options, and this seems to work nice.

So the problem is in the 'both alt keys change group' option, as every time i enable it the applet stops working. Not sure what the problem is, maybe there's something freak in my keyboard as i'm on a laptop.

---

### Post by bountonw on 2006-02-08
There is no "myspell" for Thai as far as I can tell (or Lao either for that matter.)  

I updated upgraded and installed the super install with synaptic (finally got my internet connection configured right.)

I know I have Thai fonts somewhere, because I can type in Thai &#3588;&#3609;&#3629;&#3639;&#3656;&#3609;&#3592;&#3632;&#3629;&#3656;&#3634;&#3609;&#3652;&#3604;&#3657;&#3627;&#3619;&#3639;&#3629;&#3648;&#3611;&#3621;&#3656;&#3634;&#3585;&#3655;&#3652;&#3617;&#3656;&#3619;&#3641;&#3657;

But I can not type Thai in Oowriter.  No Thai fonts are installed there.  I also have the problem that I mentioned earlier in this thread of typing Thai in gedit that the lines are too narrow or too close together and it chops the tops off the taller fonts.  I really need to use Thai on my computers at home and office and if this is not resolved I will be forced to return to Windows.  I have only been in the linux community for about a week now, and am loving it.  I really don't want to go back to Windows. Be patient with me and give me the code, walk me through the steps.  Tell me where to read.  But don't send me back:cry: :cry: :cry: 

I have to have Thai in order to remain in linux as half of my computer  activity is in Thai.  (I am working on  3 translation projects , writing e-mails and running a website in Thai.  I also hope to write a program to convert certain Thai words to English text in a text editor of some kind.)  Having Lao would also be nice, but I can live without that.  

Currently I have my supervisor questioning my migration to linux.  I am holding him off telling him that the time I am spending in learning this new OS is an investment that will pay off.  In the meantime, I am going to have to start getting some work done, which brings me to my Thai problem.  I can't get any Thai  work done while Ooowriter won't type Thai.  (The gedit is a smaller problem and I could live without that.  Although, it would be nice if the Thai I typed in gedit was the full font too.)

Sorry for the appeal.  I am caught between a rock and a hard place and really want to make this linux thing work inspite of the flack that I am getting from my supervisor.

---

### Post by bountonw on 2006-02-08
Not to get all excited or anything, but I really need help and am stuck on this one.  I need to be able to use Thai in Ooowriter.  (see above post)

---

### Post by bountonw on 2006-02-08
I went on the Open Office forum and with their guidence diagnosed the problem.  No Thai fonts are loaded in OOoffice.  They suggested that I re-install the Thai fonts. I know I have Thai fonts on my computer as I can see them and type in them &#3607;&#3635;&#3652;&#3617;&#3617;&#3633;&#3609;&#3605;&#3657;&#3629;&#3591;&#3618;&#3634;&#3585;&#3629;&#3618;&#3656;&#3634;&#3591;&#3609;&#3637;&#3657;

But no Thai fonts are coming up in OOoWriter.

Please help.

---

### Post by lomomo on 2006-02-09
have you tryed to install some of the thai fonts packages, maybe that helps.

Try installing the xfonts-thai and see if it fixes your problem.

---

### Post by bountonw on 2006-02-09
No xfonts-thai are in synaptic, so I downloaded them to my desktop from here:


[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fx%2Fxfonts-thai-ttf%2Fxfonts-thai-ttf_0.cvs.20030411-0.2ubuntu1_all.deb&md5sum=df2b0d3b5484559bfc4369d01d9a9448&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fx%2Fxfonts-thai-ttf%2Fxfonts-thai-ttf_0.cvs.20030411-0.2ubuntu1_all.deb&md5sum=df2b0d3b5484559bfc4369d01d9a9448&arch=all&type=main)

This is the package name 
> xfonts-thai-ttf_0.cvs.20030411-0.2ubuntu1_all.deb

I tried opening it, but the archive could not open 

>  Could not open "xfonts-thai-ttf_0.cvs.20030411-0.2ubuntu1_all.deb"

Archive type not supported.

There is also this site from Debien that has too many options for me to understand.  (But when I follow the link that I think I am supposed to the Debien server is down for maintainence.)

[http://packages.qa.debian.org/x/xfonts-thai-ttf.html](http://packages.qa.debian.org/x/xfonts-thai-ttf.html)

I am not sure what to do.  Should I change the sources.list? I am not sure how to install by hand.  Will try to search for that next.

---

### Post by bountonw on 2006-02-09
I found the following site on intalling fonts (in case someone is reading this with the same problem)  

[https://wiki.ubuntu.com/FontInstallHowto?highlight=%28install%29%7C%28font%29](https://wiki.ubuntu.com/FontInstallHowto?highlight=%28install%29%7C%28font%29)

I am a little afraid to proceed since the archive manager couldn't open it.  I want to do this in command line, but also don't want to damage my system.

---

### Post by bountonw on 2006-02-09
My favorite thread

[http://www.ubuntuforums.org/showthread.php?p=468342&highlight=.deb#post4683](http://www.ubuntuforums.org/showthread.php?p=468342&highlight=.deb#post4683)

There is so much, I keep having to re-read it.  Anyway, I followed the steps and ended up with this.
>  Install x-ttcidfont-conf to use xfonts-thai-ttf with X                    &#9474;
 &#9474;                                                                           &#9474;
 &#9474; Package xfonts-thai-ttf now uses defoma for font registration,            &#9474;
 &#9474; therefore, to use these Thai fonts with X, users are required to install  &#9474;
 &#9474; package x-ttcidfont-conf and follow the instruction on how to config      &#9474;
 &#9474; TrueType font path. The font path is likely to be                         &#9474;
 &#9474;                                                                           &#9474;
 &#9474; FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"               &#9474;
 &#9474;                                                                           &#9474;
 &#9474; Please edit /etc/X11/XF86Config-4, /etc/X11/fs/config and/or              &#9474;
 &#9474; /etc/X11/fs-xtt/config.                                                   &#9474;
 &#9474;                              

For the record, here is my terminal record
> 
ton@afmoff01:~/Desktop$ sudo dpkg -i xfonts-thai-ttf_0.cvs.20030411-0.2ubuntu1_all.deb
Password:
Selecting previously deselected package xfonts-thai-ttf.
(Reading database ... 62387 files and directories currently installed.)
Unpacking xfonts-thai-ttf (from xfonts-thai-ttf_0.cvs.20030411-0.2ubuntu1_all.deb) ...
Setting up xfonts-thai-ttf (0.cvs.20030411-0.2ubuntu1) ...


(I am on my office computer, but it has the same font problem as my home computer.)

I see that the Thai fonts are in /usr/share/fonts/truetype/thai

But they are not showing in OOwriter.

---

### Post by bountonw on 2006-02-09
On the font installation wiki mentioned above

[https://wiki.ubuntu.com/FontInstallHowto?highlight=%28install%29%7C%28font%29](https://wiki.ubuntu.com/FontInstallHowto?highlight=%28install%29%7C%28font%29)

I see the following.

> cd /usr/share/fonts/truetype     (presumably this could be done in /usr/local/share/fonts/truetype, instead) 
sudo mkdir myfonts
cd myfonts
sudo cp ~/*.ttf .
sudo chown root.root *.ttf
sudo mkfontdir
cd ..
fc-cache 

I didn't do this as I installed using dpkg -i

Now what?  Note previous posts on terminal screen.

---

### Post by lomomo on 2006-02-09
the xfonts-thai package was in my synaptic package manager, so i supose i changed my sources list.

Anyway, i see there's a package called language-support-th:

> metapackage for Thai language support
This metapackage depends on all packages that provide native language
support for applications in Ubuntu (like spell
checkers, dictionaries, OpenOffice and Mozilla locale packages,
etc.).

If you also want your applications and the desktop to be translated,
please additionally install language-pack-th.

Language: Thai

---

### Post by bountonw on 2006-02-09
Thank you.

I already have that installed using System>Administration>Language Selector.

Any help with the sources.list would be appreciated as I will want updates of Thai fonts as they come.

Now that the current Thai fonts are on my computer in /usr/share/fonts/truetype/thai

How do I make OOwriter and other programs recognize them?

---

### Post by bountonw on 2006-02-09
Still working on this problem.  I really appreciate this forum.  Searching the forum and reading the wikipedia has answered so many problems and saved me from answering questions.  I am looking forward to the day when I know enough to be of help to other people like they have been to me.

I still don't know how to do the following on my office computer.

> Now that the current Thai fonts are on my computer in /usr/share/fonts/truetype/thai

How do I make OOwriter and other programs recognize them?

For my home computer my apt-get update ...upgrade gave me Thai fonts.  They are installed and OOwriter recognizes them.  The problem on my office computer hasn't been resolved yet.

---

### Post by jsiii on 2006-02-10
Is there any way how to change spell checking in Gaim IM? I want to use the different language than Ubuntu UI. Or is there any way how disable it? Thank you.

---

### Post by rajneesh on 2006-02-10
i am new to linux and ubuntu (breezy). i added two more keyboard layouts. i don't understand this group shift behaviour. i selected alt+shift hotkey combination for switching between layouts. but this is not working.

why is it called group. is in the layout register 'make seperate group for each window'  has to be checked? what is a window here. this is much more complex than windows.

---

### Post by bountonw on 2006-02-11
rajeesh,

This is the blind leading the blind.  I am new to this whole linux thing and don't have all of my questions answered (see this thread).  But I will help with what I can.  Have you set up the keyboard indicator on the Gnome panal? (note first post in this thread.)  This adds a little keyboard indicator at the top line of your screen. (You can read the first post of this thread again on how to do that.)

Choosing your hotkey Go to Key board Preferences > Layout Options > Group Shift Lock Behavior

Then click on the keyboard combination that you want to shift between keyboards.
You mentioned alt+shift.

When you hit alt+shift, you should see a change up on the keyboard indicator.  If you don't, your problem is with how you set up the hotkey.  If it does change, but you can't type in all the langauges, it probably has something to do with your fonts.

Like I said, I am new, but I hope that this helps.  If any of the gurus out there see that I  am completely off the wall, please correct.

---

### Post by bountonw on 2006-02-11
rajeesh,

Look at post #10 by lomomo.  Maybe you have more than one keyboard combination clicked and they are canceling each other out.

jsiii, 

I looked through the gaim preferences and didn't see anything.  If anyone out there can answer jsiii's quetions I think that it would benefit a lot of people as not everyone chats in English.

---

### Post by bountonw on 2006-02-14
For cross referencing purposes, the following thread called 

> Tutorial - Setup Keyboard (Language) Indicator & Install Foreign (Language) Fonts

is very good.

[http://www.ubuntuforums.org/showthread.php?p=733610#post733610](http://www.ubuntuforums.org/showthread.php?p=733610#post733610)

---

### Post by bountonw on 2006-02-14
For cross referencing purposes, the following thread called 

> Tutorial - Setup Keyboard (Language) Indicator & Install Foreign (Language) Fonts

is very good.

[http://www.ubuntuforums.org/showthread.php?t=129860](http://www.ubuntuforums.org/showthread.php?t=129860)

---

### Post by jasonli on 2006-02-24
Hi sethmahoney,

Thank you so much for the keyboard switch set-up teaching. It works great for me. Now I can type both in English and French. 

Many thanks!

---

### Post by detyabozhye on 2006-04-24
Thanks for the OOo thing, been struggling that for a while now. Any way to do spell checking for two languages simultaniously in a mixed document?

---

### Post by dant on 2006-04-29
[QUOTE=sethmahoney]
**Installing a new keyboard layout:**
1.  Go to System->Preferences->Keyboard
2.  Click the "Layouts" tab
3.  Click "Add..."
4.  Pick your new keyboard layout.

**Adding the keyboard layout indicator:**
1.  Right-click on an empty spot on your Gnome panel.
2.  Click "Add to panel..."
3.  Select the Keyboard Indicator applet (in Utilities).
4.  Click Add.
Whenever you click on this applet, it will toggle between the available keyboard layouts.

[/QUOTE]

Precisely what I needed!!  Thank you very much!

Dant   :-D

---

### Post by Arjunanda on 2006-06-15
I need a transliteration layout for transliterating sankrit to roman script. Previously I was using Mandrake with KDE and created this layout with kxkb. Now, is there a way to use this same layout with gswitchit? How does one manually edit the layouts for this app? Does it use the xkb layouts, or its own format? The homepage of gswitchit is not very helpful in this matter.

Second thing - when I run last apt-get upgrade, my gswitchit keyboard settings got broken: The "Add" button in "Layouts" tab is inactive and no matter what I do I cannot make it active. I cannot even see if there is already a sanskrit transliteration layout available, as the button does not work. Any tips would be more than appreciated :)

I am using Ubuntu Breezy.

---

### Post by Naturally on 2007-01-01
I have to add a note of thanks.

I could not use Arabic before. All working well now.

This is my Thanks in Arabic

[SIZE="5"]&#1588;&#1603;&#1585;&#1575;[/SIZE]

---

