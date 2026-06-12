---
title: "HOWTO : Disable Multiple Instances of VLC."
date: 2008-08-29
forum: Outdated Tutorials &amp; Tips
---

### Post by ashmew2 on 2008-08-29
Hello people , ive been tired of looking around the Internet for solutions regarding the Multiple Instances of VLC. When i failed , I decided to get a solution. Although Im not very good at shell scripting but i still put together a few lines.


[SIZE="4"]This Guide is not needed for people Running Intrepid Ibex (Alpha 6 as of now) because the *VLC 0.9.2 Grishenko* available in the repos allows the option for Disabling Multiple Instances!!![/SIZE]

Okay , so disable the Multiple Instances of VLC , Follow these Steps :

[SIZE="4"]**1.**[/SIZE] Open up the Terminal , and type :

```
gedit vlc.sh
```

This will open a new blank file , inside the file , copy and paste the following :

```
#!/bin/sh

#Script to Disable Multiple Instances of VLC Media Player.

pid=$(pidof vlc)

kill $pid

vlc "$1"

```

Save the File and Close it.

**[SIZE="4"]2.[/SIZE]**Make Script Executable.
In the terminal , do :
```

chmod a+x ~/vlc.sh
```

[SIZE="4"]**3.**[/SIZE]Change File Associations.

Right Click a .mp3 file , go to Properties.
Now click the "Open With" tab.
Click Add.
Click "Add a Custom Command".
Click Browse and select the vlc.sh 
(Its the file u just created in your home directory in Step 1.)
Click Add.
Click Close.

[SIZE="4"]**Do This For all the Extensions you want to Run using VLC , For example ,AVI ,M3U , MPEG , etc **[/SIZE]

That's About it I guess. Now Whenever u new file , VLC will close if its running and play the new item. If you face any issues , bugs or anything Funny , Do Let me Know!

[SIZE="4"]**If you do Not like it , and want to Revert for reasons unknown :P **[/SIZE]

Just Change the File Associations 
(the one u changed to vlc.sh in Step 3. back to VLC Media Player)

Delete the vlc.sh file (It will be in the ~ Folder).

I Do not think that this file makes any changes to ur system , although if you find so , do let me know.


Thanks PierreDeKat for the following :
[SIZE="4"]
Optional (Opening files via Browsers Directly)[/SIZE] :

[QUOTE="PierreDeKat"]The file associations part works great with regard to browsing and double clicking files in Nautilus, on the desktop, or whatever. But if you want to add this function in Firefox , Seamonkey , etc., you will want to set up the file associations in your browser as well.

In Firefox, you would go to Preferences->Applications, find and highlight the file type, scroll down to "use other...", browse to your ~/vlc.sh file, click "Open", move onto the next file type, next, next, ..., and then close your Firefox preferences.[/QUOTE]

---

### Post by PierreDeKat on 2008-08-29
Awesome! Multiple VLCs have been bugging me to death!

Now then, I haven't tried your patch yet, as I am wondering if you can tell me how to undo it if anything goes wrong.

Can I manually edit a particular file to do and undo what needs to be done?

---

### Post by ashmew2 on 2008-08-29
Hey , Yeah sure ill tell u how to undo , plus ill include it in the HOWTO.
Thanks for the heads up.

For Undoing this , 

Simply remove the file associations 
(Change them to VLC MEDIA PLAYER instead of the vlc.sh).

Delete the vlc.sh file (in ur home directory).

---

### Post by PierreDeKat on 2008-08-29
Okay, works like a charm!

Just a couple of notes to add:

1) The file associations part works great with regard to browsing and double clicking files in Nautilus, on the desktop, or whatever. But if you want to add this function in Firefox , Seamonkey , etc., you will want to set up the file associations in your browser as well.

In Firefox, you would go to Preferences->Applications, find and highlight the file type, scroll down to "use other...", browse to your ~/vlc.sh file, click "Open", move onto the next file type, next, next, ..., and then close your Firefox preferences.

2) It is possible to name this file ~/.vlc.sh (note the extra period in front of "vlc.sh"). This will make the file invisible to Nautilus, etc., unless you do View->Show Hidden Files. But it does make it trickier to set up the ~/.vlc.sh file as the preferred application, since you have to figure out how to *see* it in order to select it.

There are ways to *see* it, and those methods vary.

But thanks so much, ashmew2. This fixes a major nuisance for me.

**Edit:** Actually what I decided to do instead of hiding my vlc.sh file from Nautilus was to do it a whole lot simpler. I just created a folder in my home directory called "Launchers" and set up my vlc.sh file in there. 

I don't have to see it every time I browse my home folder, but I can find it easily by browsing to my "Launchers" folder. Duh! Sometimes the simplest solutions are the best. :)

---

### Post by ashmew2 on 2008-08-29
Thanks for The Input. And Im Glad I could help.

---

### Post by shirilover on 2008-08-29
Or, you could activate two options in VLC's preferences.
They should be in the interface settings(not completely sure as I'm using 0.9.0).
One is 'Allow only one running instance'
and the other is 'Enqueue files in playlist when in one instance mode'

---

### Post by Vivaldi Gloria on 2008-08-29
> **shirilover said:**
> Or, you could activate two options in VLC's preferences.
They should be in the interface settings(not completely sure as I'm using 0.9.0).
One is 'Allow only one running instance'
and the other is 'Enqueue files in playlist when in one instance mode'

"One instance open" is in the todo list of vlc 0.9 but I don't think that it's out yet. Where did you get it from?

---

### Post by shirilover on 2008-08-29
In 0.8.6, it's located in the Advanced section.
[IMG]http://i36.tinypic.com/2hsadly.jpg[/IMG]

---

### Post by ashmew2 on 2008-08-29
That must be Under Windows ...My VLC still doesnt have any of those options..No one in the Linux Community has those options ..the ones u listed lol...

---

### Post by ashmew2 on 2008-08-29
Im Running 0.8.6e Janus  , Here's a Screenshot of my VLC Advanced Preferences :


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=83330&stc=1&d=1220067058[/IMG]

---

### Post by ashmew2 on 2008-08-29
> **Vivaldi Gloria said:**
> "One instance open" is in the todo list of vlc 0.9 but I don't think that it's out yet. Where did you get it from?

+1 .. According to the official page : [http://www.videolan.org/vlc/download-sources.html](http://www.videolan.org/vlc/download-sources.html)

They are providing only source code of 0.8.6i and Ubuntu Repos contain 0.8.6e (the one I'm Using)....Are you sure that you have 0.9.0 ? If yes , HOW ?

---

### Post by bapoumba on 2008-08-30
Thread moved to "Tutorials & Tips".

---

### Post by ashmew2 on 2008-08-30
> **bapoumba said:**
> Thread moved to "Tutorials & Tips".

My Bad...Should've posted it under Tutorials & Tips . Thanks.

---

### Post by bapoumba on 2008-08-30
> **ashmew2 said:**
> My Bad...Should've posted it under Tutorials & Tips . Thanks.
No problem :)
It was a good suggestion from someone else via a report. I just agreed ^^

---

