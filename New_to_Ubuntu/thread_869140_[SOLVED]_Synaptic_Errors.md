---
title: "[SOLVED] Synaptic Errors"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by BFraser85 on 2008-07-24
Here is an APT error that occurred while using the Synaptic Package Management system...
 (Heres the Deal, I was trying to install the hobbit client so I could efficiently monitor my Home Network.)  First off the program did not install properly on Ubuntu and ever since, I have had no luck completely removing the program using Synaptic package manager. I get the same error even while installing important Ubuntu updates. Now I'm not saying the updates aren't successfully installing, I'm just saying I get the same error for the installation of the Hobbit-client and here it is in terminal details after each update:...

(Reading database ... 111628 files and directories currently installed.)
Removing hobbit-client ...
hostname: Unknown host
invoke-rc.d: initscript hobbit-client, action "stop" failed.
dpkg: error processing hobbit-client (--purge):
 Subprocess pre-removal script returned error exit status 1
/usr/share/themes/Darklooks/gtk-2.0/gtkrc:181: Invalid symbolic color 'tooltip_bg_color'
/usr/share/themes/Darklooks/gtk-2.0/gtkrc:181: error: invalid identifier 'tooltip_bg_color', expected valid identifier
hostname: unknown host
dpkg: error while cleaning up:
 subprocess prost-installation script returned error exit status 1
Errors were encountered while processing:
 hobbit-client
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:

Now if your anal like me and do not like to see this happen everytime you update, is there a way to stop this process from trying to do whatever it is trying to do everytime you update Ubuntu?

Whats going on... Im and Audio guy not a programmer...:confused:

Also this can't be the only program this is happening to so in general whats the next step to take when dealing with stubborn files...



Thanks to the Ubuntu forums I believe we can overcome a simple obstacle like this... I hope...

---

### Post by Kevbert on 2008-07-24
In terminal you could try
```
sudo apt-get install -f
```
to try to repair the damaged package
and
```
sudo apt-get remove --purge hobbit-client
```
to completely remove hobbit-client and all associated files. [COLOR="Red"] Be careful when entering this command as it could do untold damage to your system if you enter it wrongly.[/COLOR]

---

### Post by BFraser85 on 2008-07-24
Thankyou kevbert, 

     Both commands were utilized but neither corrected the error. Same error is taking place. for example at the moment I am going to pick out a game package to install... Lets download 3d chess which requires an additional required package to use called "xaw3dg", now that both are marked for installation I apply changes which brings up a summary dialog of "TO BE REMOVED"  hobbit-client
                              "TO BE INSTALLED" 3dchess, xaw3dg

I now apply the changes ... After I get another error dialog 
"E: hobbit-client: subprocess pre-removal script returned error exit status 1"

3d chess installed correctly yet the hobbit-client was unable to be removed...

Just another learning process.  I appreciate all input.

Brian

---

### Post by Potatoj316 on 2008-07-24
Ive noticed aptitude works a little better sometimes.  Try the above commands but replace the apt-get with aptitude

---

### Post by ajgreeny on 2008-07-24
At the bottom of synaptic in the status bar there may be a mention of the broken package.  If so go to Edit>>Fix Broken Packages.  In theory that is the same as ```
sudo apt-get install -f
``` but some times it seems to work when apt-get doesn't.

---

### Post by BFraser85 on 2008-07-24
I thank you all for your help! aptitude substitute did not take care of the hobbit-client issues and I appreciate the posts because i am sure hobbit-client isnt the only package that can create such an annoyance, but thats whats great about linux there seems to always be an antedote. I hope others will learn from this thread. because I'm Positive that I'm not the only one having such an issue. You have all been great but so far unsolved, But aint that the fun of the challenge? I dunno I sure enjoy it.

Keep Posting this not only helps me but the community as well! :) feel free to send me an email or an aim instant message through pidgin or whatever. Also remember all massachusettes linux enthusiast that on August 2nd in cambridge at Mit their will be a free Ubuntu mass team get together for all who are interested. :)

You guys are the best take it easy and One day at a time.

]

---

### Post by BFraser85 on 2008-07-24
I give all credit to **drs305**

Though the troubles I have had with this package It was through the help of this community member to bring this challenge to a halt. 


:guitar:
*Create a list of installed packages:

sudo dpkg --get-selections >~/Desktop/package-list

We'll make a backup so you can restore everything the way it was before we started:

cp ~/Desktop/package-list ~/Desktop/package-list-original

This command uses gedit but use whatever text editor you are comfortable with: Edit the list, removing any reference to the troublesome apps/package(s) - I think it's 'hobbit-client' or however it's listed.

gksudo gedit ~/Desktop/package-list

Once you have removed the entry(s), Save, then:

sudo dpkg --set-selections <~/Desktop/package-list
sudo apt-get update
\\sudo apt-get dselect-upgrade i did not have to use this command but it doesnt hurt not to.

Let's see what happens! (Nothing dangerous, I assure you.)

 Note: you really don't need to run the last command (...dselect-upgrade). You can run whatever install command was giving you the problems.

Amazing thanks again for all that post. It seems that forums are the foundation to a quality OS :)

:guitar: Current Track - All That Remains - "Whispers (I Hear You)"

---

### Post by drs305 on 2008-07-24
Welcome to ubuntu

---

