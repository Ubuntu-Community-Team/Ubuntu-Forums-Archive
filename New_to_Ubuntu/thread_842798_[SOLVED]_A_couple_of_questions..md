---
title: "[SOLVED] A couple of questions."
date: 2008-06-27
forum: New to Ubuntu
---

### Post by iption on 2008-06-27
I have a couple of easy questions I couldn't find an answer, hopefully someone will.

1. I want to bookmark a folder on my disk called My documents. When I put in .gtk-bookmarks file:///media/disk/My Documents nothing happens, only other bookmarks are loaded. I tried with " and ' but it doesn't work. How do I make it work?

2. I want to mount my disk on startup. I pasted a command in .profile but nothing. How do I mount it?

3. My firefox always opens in offline mode. In about:config , browser.offline is set to false. Do I have to do something else?

4. Can I change icons of menus and items in main menu?

5. When I connect my xp and ubuntu comp via ethernet I installed samba and gave each of them static ip. Now I can access the ubuntus shared files thru \\192.168.1.68 - the ubuntus static ip and I can see the shared files. How do I write the ip in ubuntu i tried \\ and // 192.168.1.69 and it doesn't work?

Thank you in advance, and I hope those are not too hard :popcorn:

---

### Post by Nepherte on 2008-06-27
2. You can mount your drives automatically by editing the /etc/fstab file.

3. See [http://ubuntuforums.org/showthread.php?t=800179](http://ubuntuforums.org/showthread.php?t=800179)

4. Yes, go to system > preferences > main menu

5. In nautilus, type smb://192.168.1.68

---

### Post by iption on 2008-06-28
1. -?
2. This is my fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda7
UUID=6bf40b74-faa1-464e-9bd3-e48a32bbcbd0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda6
UUID=4c5e13ec-d2f4-4936-be22-129326f9dbdd none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
How do I change it? i can't see my ntsf drive in it.

4. I know about changing main menu, but not the icons. I put some  extra menus and it just shows me icons of folders, and some extra launchers that have default icon. Hoe to change that?

Couple more:
6. Is there a power saving program in ubuntu? I can feel that the hard disk is really heating up after a while (it is just below the touchpad).

7. Can I start programs like gedit or system monitor with keyboard shortcuts? These programs are not there and I don't see a way to add them. I would like system monitor to be started when i press Ctrl+Alt+Del.

---

### Post by masterjonny on 2008-06-28
6. I find powertop a good program for managing power and the likes.

How to get it, use it and set it up can all be found about halfway down [this page]("http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron-p2") under the heading "Reduce Power Consumption"

---

### Post by robertchahine on 2008-06-28
about the icons, usually u can change them by customizing your theme.
go to system>preferences>appearence, chose the "theme" tab, then press on customize button so you can customizes your icons and tabs...

---

### Post by rraj.be on 2008-06-28
> **iption said:**
> 1. -?
2. This is my fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda7
UUID=6bf40b74-faa1-464e-9bd3-e48a32bbcbd0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda6
UUID=4c5e13ec-d2f4-4936-be22-129326f9dbdd none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
How do I change it? i can't see my ntsf drive in it.



Than editing fstab there is an easy way.

Open

```
Applications --> System tools --> NTFS configuration tools.
```

Select the required NTFS partition's and select the mount point's.

Now click apply.

This wil pop up another window and in that check

```
Enable read write access to internal drives.
```

Clcik apply.

Thus you enabled auto mounting NTFS drives.

When ever you boot all your NTFS drives will be auto mounted.

---

### Post by hyper_ch on 2008-06-28
it is also adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

and it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

### Post by iption on 2008-06-28
> Applications --> System tools --> NTFS configuration tools.
Where is that? Is that changed in hardy or do I have to install something?

> **hyper_ch said:**
> it is also adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

and it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Are you suggesting that next time I put every question in a new thread? That would be rather time consuming for me and for people who answer these questions. 

Not solved: 1,7

---

### Post by rraj.be on 2008-06-28
I think you dont have it installed.

Try this to install.

```
sudo apt-get install ntfs-config

```

And as Hyperch said its better to make new threads to each question.

Even though its time consuming, it will be easy for you or others to search latter and further it will make people know what is the exact problem and what are the questions you got solved and what they should answer.

---

### Post by mcduck on 2008-06-28
1. Why not just create the bookmark from Nautilus? Go to the directory you wish to bookmark and use Bookmarks/Add bookmark from the menu (or hit Ctrl-D)?

If you are using Spatial mode in Nautius it's in Places/Add Bookmark.

---

### Post by iption on 2008-06-28
Thanks guys, you have been really helpful. I found the solution to 7. [here]("http://www.codejacked.com/create-custom-keyboard-shortcuts-in-linux/").

> And as Hyperch said its better to make new threads to each question.
Ok ill do that next time, and if I will have the time i'll collect all noob questions and put it in one place.

---

