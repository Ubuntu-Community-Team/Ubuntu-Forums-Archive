---
title: "Could not open location 'file:///"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Echodeck on 2008-05-27
When I try to open for instance home,  or documents in places on the desktop, all I get is an error message saying: could  not open location `file:///home/ and so on. What has happened? Tried to search the web for solutions, but I couldn`t find any deasent answers.

X-ray

---

### Post by quelx on 2008-05-27
try ```
   update-desktop-database
   update-mime-database /usr/share/mime 
   killall nautilus

```

shamelessly lifted from [http://www.deevans.net/blog/gnu](http://www.deevans.net/blog/gnu)

---

### Post by alexforcefive on 2008-05-27
*edit* quelx beat me to the punch. Stupid quelx!

---

### Post by Echodeck on 2008-05-27
File '/usr/share/applications/gxine.desktop' contains invalid MIME type 'x-content/video-vcdx-content/video-vcd' that has more than one slash

this is what I get after typing the first line

---

### Post by Echodeck on 2008-05-27
after typing cd /home/, and the ls, I get to my home folder, and then my username appears. So I can get access apparently. Is it just the links on the desktop which is corrupt or something? By the way, this error involves all of the folders in "places," My desktop is empty as well. Forgot to say that.

---

### Post by quelx on 2008-05-27
> **Echodeck said:**
> File '/usr/share/applications/gxine.desktop' contains invalid MIME type 'x-content/video-vcdx-content/video-vcd' that has more than one slash

this is what I get after typing the first line

Throw a **sudo** in front of those lines

---

### Post by Echodeck on 2008-05-28
> **quelx said:**
> Throw a **sudo** in front of those lines

Still get the same  message..

---

### Post by Echodeck on 2008-05-28
> **quelx said:**
> Throw a **sudo** in front of those lines

root@Echodeck:/home/x-ray# cd home
bash: cd: home: No such file or directory
root@Echodeck:/home/x-ray# cd /home/
root@Echodeck:/home# ls
x-ray
root@Echodeck:/home#

---

### Post by Echodeck on 2008-05-28
> **quelx said:**
> try ```
   update-desktop-database
   update-mime-database /usr/share/mime 
   killall nautilus

```

shamelessly lifted from [http://www.deevans.net/blog/gnu](http://www.deevans.net/blog/gnu)

root@Echodeck:/home# su update-desktop-database
Unknown id: update-desktop-database
root@Echodeck:/home# sudo update-desktop-database
File '/usr/share/applications/gxine.desktop' contains invalid MIME type 'x-content/video-vcdx-content/video-vcd' that has more than one slash
root@Echodeck:/home# 

What now?

---

### Post by wyrless2002 on 2008-10-31
Echodeck,
I had this problem after I upgraded to 8.10, Intrepid Ibex, and it seems to be a loss of file (type) associations. Just like it says, there's no program associated with that link, which is literally just a "folder", so it doesn't know what program to use to open a "folder" with. After reading this post and around 50 more, I wandered into this fix. 

Press ALT+F2 and type nautilus then press "ENTER" (remember,lower case) to get into the file manager. You should be in /home/Echodeck (or your username) already. Click the "UP ARROW" on the tool bar, that opens the parent folder (or erase the username so that you only have location: /home showing in the address bar and press "ENTER"). Now you should be in the /home folder, and looking at a list of the usernames if you have several, at least one of them, a folder named Echodeck (or, you guessed it, your username). right click on it, select "PROPERTIES" at the bottom. You should get a pop up menu box that says Echodeck Properties, click on the "Open With" tab. I got an empty box that said "select an application to open Echodeck and files of type "folder". Click on "ADD" at the bottom and then scroll down to File Browser and select it from the list of programs.  Click "CLOSE".

Hopefully, the problem was really just that simple, and you're done. 

If someone else reads this this and can give the quick and clean command line instructions to get to this point, please do. CLI is still a little foreign to me, and it's not first nature yet, but I'm sure much more surgically precise.

---

### Post by wyrless2002 on 2008-10-31
Echodeck,
I had this problem after I upgraded to 8.10, Intrepid Ibex, and it seems to be a loss of file (type) associations. Just like it says, there's no program associated with that link, which is literally just a "folder", so it doesn't know what program to use to open a "folder" with. After reading this post and around 50 more, I wandered into this fix. 

Press ALT+F2 and type nautilus then press "ENTER" (remember,lower case) to get into the file manager. You should be in /home/Echodeck (or your username) already. Click the "UP ARROW" on the tool bar, that opens the parent folder (or erase the username so that you only have location: /home showing in the address bar and press "ENTER"). Now you should be in the /home folder, and looking at a list of the usernames if you have several, at least one of them, a folder named Echodeck (or, you guessed it, your username). right click on it, select "PROPERTIES" at the bottom. You should get a pop up menu box that says Echodeck Properties, click on the "Open With" tab. I got an empty box that said "select an application to open Echodeck and files of type "folder". Click on "ADD" at the bottom and then scroll down to File Browser and select it from the list of programs.  Click "CLOSE".

Hopefully, the problem was really just that simple, and you're done. 

If someone else reads this this and can give the quick and clean command line instructions to get to this point, please do. C.L.I. is still a little foreign to me, and it's not first nature yet, but I'm sure much more surgically precise.

---

### Post by distortedstar on 2008-10-31
Awesome! Thanks for that fix...worked perfectly!

---

### Post by heatpumpcontrol on 2008-11-27
> **wyrless2002 said:**
> Echodeck,
I had this problem after I upgraded to 8.10, Intrepid Ibex, and it seems to be a loss of file (type) associations. Just like it says, there's no program associated with that link, which is literally just a "folder", so it doesn't know what program to use to open a "folder" with. After reading this post and around 50 more, I wandered into this fix. 

Press ALT+F2 and type nautilus then press "ENTER" (remember,lower case) to get into the file manager. You should be in /home/Echodeck (or your username) already. Click the "UP ARROW" on the tool bar, that opens the parent folder (or erase the username so that you only have location: /home showing in the address bar and press "ENTER"). Now you should be in the /home folder, and looking at a list of the usernames if you have several, at least one of them, a folder named Echodeck (or, you guessed it, your username). right click on it, select "PROPERTIES" at the bottom. You should get a pop up menu box that says Echodeck Properties, click on the "Open With" tab. I got an empty box that said "select an application to open Echodeck and files of type "folder". Click on "ADD" at the bottom and then scroll down to File Browser and select it from the list of programs.  Click "CLOSE".

Hopefully, the problem was really just that simple, and you're done. 

If someone else reads this this and can give the quick and clean command line instructions to get to this point, please do. C.L.I. is still a little foreign to me, and it's not first nature yet, but I'm sure much more surgically precise.


Worked! thanks

---

### Post by statmonkey on 2009-01-01
> **wyrless2002 said:**
> Echodeck,
I had this problem after I upgraded to 8.10, Intrepid Ibex, and it seems to be a loss of file (type) associations. Just like it says, there's no program associated with that link, which is literally just a "folder", so it doesn't know what program to use to open a "folder" with. After reading this post and around 50 more, I wandered into this fix. 

Press ALT+F2 and type nautilus then press "ENTER" (remember,lower case) to get into the file manager. You should be in /home/Echodeck (or your username) already. Click the "UP ARROW" on the tool bar, that opens the parent folder (or erase the username so that you only have location: /home showing in the address bar and press "ENTER"). Now you should be in the /home folder, and looking at a list of the usernames if you have several, at least one of them, a folder named Echodeck (or, you guessed it, your username). right click on it, select "PROPERTIES" at the bottom. You should get a pop up menu box that says Echodeck Properties, click on the "Open With" tab. I got an empty box that said "select an application to open Echodeck and files of type "folder". Click on "ADD" at the bottom and then scroll down to File Browser and select it from the list of programs.  Click "CLOSE".

Hopefully, the problem was really just that simple, and you're done. 

If someone else reads this this and can give the quick and clean command line instructions to get to this point, please do. C.L.I. is still a little foreign to me, and it's not first nature yet, but I'm sure much more surgically precise.


Just wanted to say thanks.  Perfect fix.

---

### Post by gabore on 2009-02-11
Well, for me it happened after I uninstalled all the bluetooth-related stuff, using Synaptic, in order to be able to install the new Blueman. Of course, I removed Nautilus - the main file manager, as well, by this accident. So after finding this out, it is enough to search for nautilus in Synaptic and install it, folders are open again. I just wonder why did Synaptic remove all the nonbluetooth things? Why is nautilus dependent on bluetooth?? :confused:

---

### Post by evilsectoid on 2009-05-04
wyrless2002 thanks!!!

---

### Post by hopwon on 2009-06-19
> **gabore said:**
> Well, for me it happened after I uninstalled all the bluetooth-related stuff, using Synaptic, in order to be able to install the new Blueman. Of course, I removed Nautilus - the main file manager, as well, by this accident. So after finding this out, it is enough to search for nautilus in Synaptic and install it, folders are open again. I just wonder why did Synaptic remove all the nonbluetooth things? Why is nautilus dependent on bluetooth?? :confused:

EXACTLY same thing happened to me after uninstalling bluez after I stuffed up my BT.
Great fix thanks!

---

### Post by sandroreis on 2009-06-24
I justa want to say Thanks !!
Work fine for me this fix!!!

Tks :P
Sandro

---

### Post by Nyken on 2009-07-19
Worked for me to! Seems when I uninstalled bluetooth's crap it undid Nautilus. A reinstall of Nautilus fixed everything just fine!  Hope to God they don't make Nautilus dependant or linked in anyway to bluetooth crap in Karmic! **BIG FREAKING HINT!!!**

---

### Post by siegfried78 on 2009-11-03
sudo apt-get install nautilus

THAT'S ALL! ;)

---

### Post by BiynaYahu on 2010-04-22
I know this is an old thread, but I too have the same problem.  Unfortunately, neither of the solutions presented have worked for me.  I've Googled, and Googled, but came up empty.  Is there any other issues that could be causing this?

Thank you in advance,
Mike Browell.

---

### Post by stuartziane on 2010-07-24
I had this issue, and my solution is as follows -

sudo apt-get remove nautilus

then

sudo apt-get install nautilus


The issue just appeared randomly half-way through a session, and all I did was use the internet via a wireless connection, and I didn't do any installs or upgrades or anything. weird!

---

### Post by shrivatsa on 2010-09-04
i have tried all the solution above mentioned but problem still persists somebody please help

---

### Post by BillyBoa on 2010-10-16
Oct 2010 and still the solution is working. Thanks

---

### Post by AuFreelanceWriter on 2011-02-04
I used all of the solutions in this thread to solve my issue. 
My windows would not minimize, maximize, or close, and when i loaded terminal it went to the top left corner, with the menu bar flush with top of the screen (hiding the title bar and buttons)
While the cause was complicated, the solution was as simple as reinstalling the windows manager and file manager.

The below steps will remove metacity, then reinstall it, and nautilus.

sudo apt-get remove metacity
sudo apt-get install metacity
sudo apt-get remove nautilus
sudo apt-get install nautilus

IF you are getting the error: 
"Can not open folder ..." when you click desktop, documents, or music in the places drop down menu, open a terminal and type in:

nautilus

The file browser should open. Click on file system in the left collumn, open the home folder, and right click on your username's home folder. 
Select open with other application. 
In the window that pops up, select use a custom command, and type in: 
nautilus
(Spelling AND Punctuation do count)

I had to run all of these steps in ubuntu 10.10. 
Recently installed Festival's cmu arctic voices and had to add 3-4 extra lines of code in festival.smc to make my alsa the default player. This caused orca to stop working, so i attempted a reboot and viola, instant frustration. =)

If everyone who experiences this error could please post what they were doing  when the error occurred, we can prevent it in future releases.
(WE being the users who use this wonderful open source operating system as well as the programmers)

---

