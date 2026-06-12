---
title: "Rhythmbox kept playing after closing"
date: 2012-06-19
forum: New to Ubuntu
---

### Post by RH9R on 2012-06-19
Using live CD, I moved a file from my storage to the music folder in the liveCD to test. It played. I click the 'X' in the window to stop the application. The window disappears like normal, but the music kept playing - and I have nothing on the desktop to get me back to the application to beg it to stop/close. Is this specific to the rhythmbox app? Will this happen w/ other apps? How do get an app to close?

---

### Post by Immolatus on 2012-06-19
for live cd in terminal do:

killall rythmbox


for installed system in terminal:

sudo killall rythmbox

---

### Post by oboedad55 on 2012-06-19
> **RH9R said:**
> Using live CD, I moved a file from my storage to the music folder in the liveCD to test. It played. I click the 'X' in the window to stop the application. The window disappears like normal, but the music kept playing - and I have nothing on the desktop to get me back to the application to beg it to stop/close. Is this specific to the rhythmbox app? Will this happen w/ other apps? How do get an app to close?


Rhythmbox will keep playing and minimize if you already have something playing when you click on the "X". You have to go to the menu and close it or stop the sound file first.

---

### Post by RH9R on 2012-06-19
Thank you both. 'Seems an odd departure from a universal window control killing an app. 
Again, I appreciate your kind help.

---

### Post by frustratedubu on 2012-11-14
Having eventually found CTRL-Q (again) at askubuntu.com I just posted the following rant there:  (don't see why this forum should get off without a rant as well)

<<quote:>>

This must be the third time in the past couple of years I have spent a  good half-hour on the Internet looking for the magical Rhythmbox  CTRL-Q. I don't want to stop Rhythmbox that often but when I do it is  THE most annoying feature of my Linux (Ubuntu) distro that it won't  shutdown via the GUI. Yes I know I could go into the terminal, pull out  my command-line cheatsheet and sort it that way...but this is SUPPOSED  TO BE A GUI.
I'm sure it's too late to change it's default  behaviour but couldn't someone deeper into Linux development than I am  provide a "preference" type setting to make the "X" Close button do what  practically every other application does?  Or at least provide a menu  option SOMEWHERE to shut the b?$£%&! down?  I haven't been able to  find one in my release.  "QUIT"? "CLOSE"?...no use, the music I've  deliberately just "unpaused" as a diagnostic tells me only CTRL-Q or a  command-line "kill" is going to stop it.
  A pointless rant, I know.  And maybe this time the CTRL-Q will stick  in my pathetic little raised-in IBM mainframe computing skull.  But this  sort of inconsistency is why many users try Linux...and then go back to  Windows.  And personally I'd rather see Linux prosper than Microsoft.   Maybe then I wouldn't feel the need to keep an old Windows release  hanging around purely because some of the poker sites can't be bothered  to write a Linux version of their client-side software, because the  poker sites would have seen the market share and done something about  it.  Inconsistencies between terminal commands are a historical fact we  have to live with (i.e. a "useful feature" of Linux if you're a guru)  but surely consistency of basics in the GUI such as the "X" button of an  application are second only to ease of software installation if we want  Linux spread and prosper?  
  Alternatively maybe someone at askubuntu.com could make CTRL-Q a  little more prominent in searches involving "rhythmbox", "close",  "quit", "shutdown" and similar?  

<<end quote>>

Forum user RH9R posted here on 19 June:
"Seems an odd departure from a universal window control killing an app."

I couldn't agree more, RH9R.  Just the sort of "useful feature" in a maverick application which sends someone trying out Linux for the first time straight back to Microsoft.  I've stuck with Linux and 99% of the time prefer it to Windows.  But the point of a GUI is that it should do what the user expects.  If the idea was to allow music to carry on playing if a user absent-mindedly clicks the "X" button why provide the "X" button, at all?  It's not doing what most users expect an "X" control to do; more a "minimize".  And why have separate "close" and "quit" menu options (on my version anyway), both of which do what the "X" control does and leave the application running?  

"Oh, you just have to know what you're doing".  Well the point of a good GUI is that you DON'T have to learn different ways of doing the same thing to different applications or have to resort to the command-line.  Do we want Linux to be more widely used or not?

---

### Post by newb85 on 2012-11-14
I realize rants are generally more beneficial as a means of venting than of receiving valuable answers, and I also realize my answers may not be viewed as valuable.  Nonetheless:

If a user doesn't remember the keyboard shortcut Ctrl+Q, it takes very little searching of the menus to find Music>Quit.  For that matter, tapping Alt to bring up the HUD and starting to type *quit* is also fairly simple.  If I do forget that Rhythmbox will keep running and hit the "X" wanting it to stop, Rhythmbox is integrated into the Sound menu, so I can simply hit the pause button there to stop the music--or, if I'm too lazy to move the mouse that much, I can use the pause media button on my machine.

Using the terminal to kill the rhythmbox process would probably land around slot #5 on my methods for stopping playback.

---

### Post by quentinl on 2012-11-14
it does this to me to. i think it was designed like that but if you go to sound at the top right hand corner there is a pause button. thats how i stop it playing

---

