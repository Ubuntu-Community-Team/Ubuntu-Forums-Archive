---
title: "Finding &amp; Deleting Files II"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by faron45 on 2008-08-08
[Slight] Repost 


 Downloaded a couple of things from the internet that I've now decided that I really don't want on my pc [plus,I'm not really sure if they're even compatible with the op sys.And,I found similar programs under add/remove].Problem is...I'm extremely new to the [linux/xubuntu] operating system [and,comps too really] & now I need to know how to find these files & delete them.Please help a nervous computer user [who's done MUCH searching on this subject].For any/all help.....thanks in advance.If it helps...I [have] found these 2 downloads in firefox under tools/downloads.When I right-click them,"open","open containing folder" & "go to download page" cannot be selected.In other words,those 3 options are greyed out. 
 
          Thanks much,       
                      J.Garcia.:guitar:
       
      "Never ever learned to read or write so well,but,he could play a guitar just like a ringin' a bell".

---

### Post by Cypher on 2008-08-08
In Firefox on the Downloads tab there should be an indication of where the files are being stored. If you didn't modify this setting ever, the files should be on your Desktop. So minimize all windows and see if you can find these files on your Desktop, if so you should be able to highlight them and delete them. Based on what the files were and if you "installed" them we might have to do a few more steps to really get the stuff cleaned up..

---

### Post by issih on 2008-08-08
If they actually aren't compatible with the operating system then chances are all you have to get rid of is the original installation file, as nothing will have happened when you tried to run it.

If you are talking about a windows program (i.e. one with a file extension .exe) then as long as you haven't installed wine then that will be true.

If you have actually succeeded in installing a program you no longer want, you have a few options.

If it was installed via the add/remove dialog simply go back there and untick it.

If it was installed from a .deb file downloaded from the internet, open synaptic package manager, search for the package and unselect it in there.

If it was distributed as source and you compiled it (sounds unlikely given what you've said) then you'll have to follow the instructions in the install instructions, typically the appropriate command is "make uninstall" in the directory containing the sourcecode.

Hope that helps

P.S. what a lot of 'If's that was :)

---

### Post by faron45 on 2008-08-08
Okay.Very,very sorry it's taken me so long to reply folks.I'm just not used to getting replies so fast in other forums so,I usually just walk away for awhile.I will try to respond more quickly from now on.Thanks. 
 Issih,not found in synaptic.Did find noteie.zip in there though.And,no files on desktop.Actually,the first program I downloaded was on the desk.But,that one is no longer a problem.I [will] tell you,wine is installed.But,at this point,I've no idea how to use it."Distrubuted as source"...hmmmm.What's that mean ? Heh,heh.
 Okay...now to tell you exactly what I did...from download.com,I downloaded "noteit.zip" & "postits-lite..................

---

### Post by st33med on 2008-08-08
Usually, the files are downloaded to either your /tmp folder or your Desktop. Check both for those files.

Also, /tmp files are deleted after a certain amount of time. If you want an easier way to keep track of downloads on Firefox, I would recommend [this plugin.]("https://addons.mozilla.org/en-US/firefox/addon/26")

---

### Post by LowSky on 2008-08-08
faron45 please use spaces between the words and puntuation you type like normal grammer rules suggest. My eyes hurt from reading your scribble.

By the Way, Firefox downloads things to your desktop or to your home folder. Check there.

Source code means that the application is in its purest for and has not been packaged for installatoin into a distrobution. For instance Ubuntu uses files labeled with .DEB to install programs, while Fedora uses .RPM

---

### Post by faron45 on 2008-08-08
Lowsky,thanks for info.Sorry my "scribble" hurt your eyes.I'll try to do better.Heh,heh,heh.Desktop,home & temp folders already checked.Just can't seem to find these files anywhere.Hmmmmmmmmm.Thanks again,everybody.

---

