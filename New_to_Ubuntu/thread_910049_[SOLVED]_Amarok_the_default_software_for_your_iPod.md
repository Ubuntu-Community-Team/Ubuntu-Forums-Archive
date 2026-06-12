---
title: "[SOLVED] Amarok the default software for your iPod"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by unknown user on 2008-09-04
[FONT="Verdana"]Last night I set up Amarok to allow me to upload tunes from my local drive to my ipod and after a bit of playing around it worked a treat, I was well chuffed that I had done it and can totally move from my windows system.  I used this site [http://www.simplehelp.net/2007/07/04/how-to-use-amarok-to-manage-your-ipod-in-ubuntu/](http://www.simplehelp.net/2007/07/04/how-to-use-amarok-to-manage-your-ipod-in-ubuntu/)

Within section ‘How to make Amarok the default software for your iPod’ I opened the ‘Removable Drives and Media Preferences’ window from System -> Preferences -> Removable Drives and Media, looking for the Multimedia tab, but it was not there, nor was the ‘Input Devices’ tab.

Does anyone know how I can get this tab to show so that I can make Amarok the default software for my iPod?[/FONT]

---

### Post by nothingspecial on 2008-09-06
Just to give you an unhelpful reply, that guide was for Gutsy 7.10, for which those instructions are correct.
My unhelpfulness comes from the fact that I`m still using Gutsy.

---

### Post by Wobblybob on 2008-09-06
Try this, it works for me on Hardy
[http://www.cooper2004.karoo.net/iPod.html]("http://www.cooper2004.karoo.net/iPod.html")

---

### Post by unknown user on 2008-09-15
**Thanks for this guys, I will try it later and let you know :)**

---

### Post by unknown user on 2008-09-15
Wobblybob thanks for the link, I was able to do the first part, but when I come to do the second line in the terminal window, I hit a few issues.  I entered this line 'sudo cp /usr/share/app-install/desktop/amarok.desktop /usr/share/applications/' changing usr to my system name and nothing.  

Does anyone know what I need to put here to make it work?

Also I have installed Nautilus and when I go to edit there is nothing in the list, does anyoe know how I can complete the rest of the action?

When I plug in my IPod I get the message saying that it can not mount the volume on the first time.  When I click in the IPod for the second time Amarok does launch but not open in the main screen.  The icon shows in the panel at the top and a sond starts playing but no window is showing.

Can anyone help?:confused:

---

### Post by Mornedhel on 2008-09-15
/usr is the actual /usr directory, not your username. There's an entire hierarchy under /usr.

Also, please consider not writing all in purple, it hurts !

---

### Post by unknown user on 2008-09-15
Colour Done

When I do the line I press return and get this unknown@unknown-laptop:~$

---

### Post by Wobblybob on 2008-09-15
Hi mate, note sure why you are getting that message are you typing or copying and pasting the exact text as follows:

sudo cp /usr/share/app-install/desktop/amarok.desktop /usr/share/applications/ with no changes and all spaces into your terminal as 1 line then pressing enter?

and are you using the gnome desktop or KDE?

---

### Post by Mornedhel on 2008-09-15
Looks like he's using Gnome (from the dialog and menus he describes in the OP).

Then he mentions he "installed Nautilus"...

Now I'm confused.

---

### Post by Wobblybob on 2008-09-15
> **Mornedhel said:**
> Looks like he's using Gnome (from the dialog and menus he describes in the OP).

Then he mentions he "installed Nautilus"...

Now I'm confused.

That's why I asked! I'm also confused by that...

---

### Post by unknown user on 2008-09-15
Wobblybob I pasted this line and was asked for my password, entered that and nothing

---

### Post by Mornedhel on 2008-09-15
cp doesn't output anything unless it fails, so that's a good thing.

Have you tried the rest of the instructions provided by Wobblyjob's link ?

"Now log out and back in, open Nautilus, go to [Edit], [Preferences], [Media] and in the [Music Player] option select Amarok from the drop down list. When you next plug in your iPod, Amarok will launch." (from the link)

---

### Post by Wobblybob on 2008-09-15
Sounds like it worked, just continue with the instructions and all should be ok. You often don't get any message in a linux terminal window unless the command fails.

Good Luck

---

### Post by unknown user on 2008-09-17
Guys, I was following the link ([http://sofabedz.co.uk/linux/iPod.html#Open%20Amarok%20by%20default](http://sofabedz.co.uk/linux/iPod.html#Open%20Amarok%20by%20default)) which stated:

[I]Thanks to mamcgrath on ubuntu forums for this tip, see the thread here

Copy and paste the following into a Terminal;

martin@linux:~$ sudo gedit /etc/gnome/defaults.list

then edit the file changing the line 'x-content/audio-player=rhythmbox.desktop' to 'x-content/audio-player=amarok.desktop' then save the file and close gedit.

This creates several launcher files - amarok.desktop - but doesn't create one in '/usr/share/applications'. To solve this copy and paste the following into the Terminal;

martin@linux:~$ sudo cp /usr/share/app-install/desktop/amarok.desktop /usr/share/applications/

Now log out and back in, open Nautilus, go to [Edit], [Preferences], [Media] and in the [Music Player] option select Amarok from the drop down list. When you next plug in your iPod, Amarok will launch.[/I]

I got the first bit done all OK, but the second bit from (This creates several launcher files - amarok.desktop) is where it all went wrong.

---

### Post by unknown user on 2008-09-18
Guys an ideas?Cool it sounds like this has worked as there was no error message in the shown after I entered my system password.  Any ideas why when I open Nautilus it is blank?

Cheers, for your help, I am nearly there

---

### Post by mc4man on 2008-09-18
> when I open Nautilus it is blank?
When someone is saying 'open nautilus' they mean open the file browser, ie. open any folder or go to places -> home folder. What are you doing?

In any event, the method linked to, while it will open Amarok when you connect the ipod I can't see it doing it properly. I believe it will load all of your tracks at once into amarok. 
At this point ck. it and if not suitable I'll show you a 'better' way.

side note: there is no reason to go into or edit your root folders/files to add additional choices to any of the default media 'autorun' possibilities. Everything can be handled locally in your home directory.

---

### Post by Wobblybob on 2008-09-22
have you copied and pasted:

sudo cp /usr/share/app-install/desktop/amarok.desktop /usr/share/applications/

into a terminl and pressed enter?

---

### Post by unknown user on 2008-09-23
mc4man - cheers for that, not it is clear.  I did this and it was already set to Amarok which was great.

Wobblybob - Thanks for that I will try that tonight, but I think I am almost there now.

---

### Post by Nat90 on 2008-12-07
I had the same problem with the second step,(terminal told me that the directory didn't exist), so I just skipped it and everything worked out fine

---

