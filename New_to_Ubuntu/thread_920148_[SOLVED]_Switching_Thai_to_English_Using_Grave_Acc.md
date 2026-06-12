---
title: "[SOLVED] Switching Thai to English Using Grave Accent Key (`)"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by lorenbr on 2008-09-15
First off, I'm dreadfully new to Ubuntu, and to these forums, so forgive me if I faux pas a bit.

I am interested in figuring how to toggle a language switch for the keyboard, in my case between Thai and English, using the grave accent key (`) that is in the upper left hand of the keyboard.  There was a post about it some 2 years ago, but the issue never seems to have been resolved, and I can't reopen the old post.

The post was titled "Would like to use Grave accent ( ` ) changing language " and here is the link: 
[http://ubuntuforums.org/showthread.php?t=190130&highlight=keyboard+thai](http://ubuntuforums.org/showthread.php?t=190130&highlight=keyboard+thai)

I tried to find a more effective way to refer to the last post, but I couldn't.

I have successfully installed the Thai language support, and have found that there are a number of options for language toggling, involving the windows key, alt, control, shift, etc.  However, I am trying to get Ubuntu to behave as much like Windows does as possible (otherwise I fear I will have a hard time convincing my coworkers to switch over), hence the interest in binding the specific key for language switching.

Is this possible?  I'd be willing to go through a little work to make the switch, but my skill set doesn't really go beyond copying and pasting a command into the terminal.

Thanks

---

### Post by Pro-reason on 2008-09-15
I use SCIM for complex-script support (e.g. Chinese).  By default, Ctrl-` turns it on and off.

As for simply changing between keyboard layouts, I can't find a way of making GNOME use the grave key.  It offers a large range of possible shortcuts, but that's not one of them.

---

### Post by lorenbr on 2008-09-15
I appreciate your taking the time to get back to me.  I'm now having a bit of trouble with SCIM (as in the languages don't really seem to switch anymore), so I think I need to do a bit of digging/exploring to see if I can figure out.  Wish me luck.

---

### Post by visarute on 2008-09-17
I want to use grave accent too.
I have ever use previous version of Ubuntu(I can't remember version) It can use grave accent to change layout.

Why I can't use grave accent to switch layout in 8.04LTS.

Who know how to use patch or any other way to use grave
PLEASE HELP ME!

---

### Post by lorenbr on 2008-09-18
Something I came across while trying to solve another problem on another thread ([http://ubuntuforums.org/showthread.php?t=920227](http://ubuntuforums.org/showthread.php?t=920227)) might be useful here.  Is there a way you can change the /etc/X11/xorg.conf to do this?  I'm thinking specifically the line like this:

Option "XkbOptions" "grp:alt_shift_toggle"

Which I assumed could be changed to "grp:grave_toggle."  But that hasn't worked, and in fact now I can't run the gksu gpedit /etc/X11/xorg.conf to change anything back.  But that's a different story.  Is there a way this line can be changed to make that grave accent change happen?

---

### Post by lorenbr on 2008-09-19
Alright,

I figured out that if I "gksu gedit /etc/X11/xorg.conf" and add the following line:

Option "XkbVariant" "winkeys"

before the "XkbOptions" line, then I can change the "XkbOptions" line to:

Option "XkbOptions" "lwin_toggle"

And the left windows key will toggle between the languages.  Without the "XkbVariant" "winkeys" line the "lwin_toggle" does nothing.  So that says to me there's got to be a variant or some such that can be input to allow the grave accent key to do the language switching, as visarute and I (and I think, almost every Ubuntu user in Thailand) wants.  I've been trying to find the relevant information in some Xkb Configuration Guides online, but its a bit over my head.

Any suggestions?

---

### Post by lorenbr on 2008-09-21
Figured it out, with the help of a Linux guy here in Thailand.  There's a Debian Package available on the OpenTLE website which adds a "Grave Changes Group" checkbox to the "Layout Options" window off the "Layouts" tab of the "Keyboard Preferences."  Here's the link:

[http://www.opentle.org/node/4944](http://www.opentle.org/node/4944)

The text is all in Thai, but the download is available right at the top after the words "Download Package."  Then the steps to take (which are pretty intuitive anyways) are laid out in picture format.  The one thing I'm unclear on is whether it is necessary to alter your xorg.conf file as well as toggling the "Grave Changes Group" checkbox.  I altered just the xorg.conf file first and it didn't work, but after I made the change on the Layout Options screen, the change appears to be permanent.  I do assume the change to the xorg.conf file is necessary as it is written in at the bottom of the instructions.  But I don't read Thai very well, so I'm not sure.

---

### Post by visarute on 2008-09-27
Yeah!

I gonna install Ubuntu again after delete it all after I can't find the way to use grave(`) to switch language.

I hope it gonna work!

---

