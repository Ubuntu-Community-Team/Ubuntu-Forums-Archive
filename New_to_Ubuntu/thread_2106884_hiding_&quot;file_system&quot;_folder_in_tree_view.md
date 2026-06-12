---
title: "hiding &quot;file system&quot; folder in tree view in nautilus"
date: 2013-01-20
forum: New to Ubuntu
---

### Post by tojonukokhadush on 2013-01-20
okay i love the tree view of nautilus on the left pane but what i expect is to hide the "file system" folder from there so that it looks clean! like we don't always go into system folder, isn't it? can we do so?

---

### Post by slickymaster on 2013-01-20
Take a look at [Better Way to Hide File / Folder in Nautilus (Ubuntu / Linux]("http://www.fandigital.com/2012/09/better-way-to-hide-file-folder-in.html")). I think it's what your looking for.

---

### Post by tojonukokhadush on 2013-01-20
isn't there any easier way! this seems to indulge commands and terminals which i am a novice in and i do not want to do that unless i know exactly what am i doing ;-)

---

### Post by slickymaster on 2013-01-20
There's another way, but you'll also have to resort to the terminal and the use of commands.

So, open a terminal and type ```
gksu nano
``` and create a file named **.hidden** in the **/ directory**.
In the content of that file just type the name of the files or folders you want to be hidden.

If later you decide on unhiding them, you just have to remove them from the file.

You'll have to replace *nano* with the name of whatever text editor you have installed.

---

### Post by tojonukokhadush on 2013-01-20
by / directory means this one? if i am correct then-

1. i need to create .hidden file in "/" directory.
2. type "File System" there. 


so what does gksu nano does here? if you don't mind explaining please!

---

### Post by NilPointer on 2013-01-20
"File System" refers to root of file system, i.e. "/" catalogue. Typing "File System" won't work.

"gksu nano" means exactly that:

gksu - execute next command with root privileges (you can't just do anything in "/" catalogue from your user account, but if you gain root privileges - you can). gksu is close to sudo, but it's designed to run GUI programs and will ask for admin password inside separate window instead of terminal.
nano - it's small text editor, which works inside terminal. It may be a little unfriendly for novice users, so you may prefer "gksu gedit" to run graphical text editor.

So, that command just runs text editor with root privileges.

---

### Post by slickymaster on 2013-01-20
> **tojonukokhadush said:**
> so what does gksu nano does here? if you don't mind explaining please!

It's not at all advisable to use **sudo** with graphical applications, and nano is a graphical application. You have a detailed and very good explanation here: [Running Sudo Graphically]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by deadflowr on 2013-01-20
> **slickymaster said:**
> It's not at all advisable to use **sudo** with graphical applications, and nano is a graphical application. You have a detailed and very good explanation here: [Running Sudo Graphically]("http://www.psychocats.net/ubuntu/graphicalsudo")

No, nano is not graphical. Gedit is, but nano is not.

If a program does not open it's own interface outside a terminal, it is not graphical.

But yes, use the gksu when opening any graphical program in root.

---

### Post by tojonukokhadush on 2013-01-20
apologies but i got this when i did gksu nano-

---

### Post by slickymaster on 2013-01-20
> **deadflowr said:**
> No, nano is not graphical. Gedit is, but nano is not.
You are a 100% right, deadflowr. I apologise.

> **NilPointer said:**
> nano - it's small text editor, which works inside terminal. It may be a little unfriendly for novice users, so you may prefer "gksu gedit" to run graphical text editor.
@tojonukokhadush:
Use Gedit, instead of Nano.

---

### Post by tojonukokhadush on 2013-01-20
okay now i did this-
1. gksu nautilus in terminal
2. created .hidden file there with "File System" typed in


but what i got is-

---

### Post by NilPointer on 2013-01-20
> **tojonukokhadush said:**
> apologies but i got this when i did gksu nano-

Yes, it's nano, the text editor. You can type text here like in any other text editor. When you added some text, you can save it to file by pressing Ctrl+O.

---

### Post by NilPointer on 2013-01-20
> **tojonukokhadush said:**
> okay now i did this-
1. gksu nautilus in terminal
2. created .hidden file there with "File System" typed in


but what i got is-

No, there's no need to run nautilus with root privileges. What you got on screen is just nautilus spewing warnings and errors into terminal. It happens when you run nautilus under root, but it's nothing critical.

And text "File System" won't work, since it's just how nautilus calls "/" directory.

---

### Post by deadflowr on 2013-01-20
> **NilPointer said:**
> Yes, it's nano, the text editor. You can type text here like in any other text editor. When you added some text, you can save it to file by pressing Ctrl+O.

You can also use ctrl + x to save the file upon exiting.
Just type Y to comfirm modifications, and then hit enter and confirm the file name is right.

But as slickymaster said, use gksu gedit, as it is far more easier to understand than nano.(Open, save and other buttons are far more simple to grasp then key binding like ctrl +o and the like.)

---

### Post by tojonukokhadush on 2013-01-20
so coming to the point-
i created .hidden file in "/" directory with "File System" typed in it!
i even tried making a one in "/root" directory even!!


BUT 

my original problem of hiding "File System" from nautilus is still unsolved!! 
what is the way to do so? please help!!!

---

### Post by deadflowr on 2013-01-20
> **NilPointer said:**
> No, there's no need to run nautilus with root privileges. 

This depends on where the file is going.
If the file is going in your home folder, then root is indeed unnecessary.
 If however, it is going into the another system directory(like /etc, or /usr, or even another users home folder in the /home directory), then root is necessary.

---

### Post by slickymaster on 2013-01-20
"File System" is the label that Nautilus assigns to the **/ directory**. Another thing, be careful not to confuse **/ directory** with **/root**. The first is where everything starts, and everything is contained in this folder, as for the second, it contains the root user&#8217;s files, it's the home folder for root &#8211; the super-administrator.

---

### Post by NilPointer on 2013-01-20
> **deadflowr said:**
> This depends on where the file is going.
If the file is going in your home folder, then root is indeed unnecessary.
 If however, it is going into the another system directory(like /etc, or /usr, or even another users home folder in the /home directory), then root is necessary.

Yes, I know. I meant, to see whether created .hidden file worked or not, root was unnecessary, he could've seen it from normal account.

---

### Post by tojonukokhadush on 2013-01-20
its all okay! 
BUT my problem is-

whatever be the directory be it "/" only or be it "/root"
i tried saving .hidden file typed "File System" with full-fledged ROOT PRIVILEGED file manager!!

STILL

i am unable to make "File System" volume hidden(so that my nautilus shows strictly my other files and folders only when i open it).
i do not want to see "File System" to be seen in my nautilus. that's it!


what shall be done now?? any idea?? any solution??

---

### Post by mc4man on 2013-01-20
You would  need to list ALL the dir.'s (folders) you don't want to see under "File System" in the nautilus **sidebar** in your /.hidden file

As far removing the "File System" entry in the nautilus **sidebar tree view** that likely can not be done without editing the nautilus source.

So all you'll accomplish here is if you expand the "File System" entry in the nautilus sidebar tree view it will be empty. You could just as well Not expand the entry in the 1st. place

---

### Post by tojonukokhadush on 2013-01-20
you got it right Mr. mc4man!!

that's what i too realized finally!! you can not expand the entry in the 1st. place!
the only comfort with .hidden file created with the lists of all those files/folders' names to be hidden is that it saves time to keep renaming those files/folders which would have been infact a cumbersome work in itself otherwise!!

smart move man ;-)


now this is solved!!

---

### Post by mc4man on 2013-01-20
For instance if you did go to the trouble as shown in screen the entry remains but is empty
(if doing so for some reason you have to type in names correctly or the .hidden would be ignored

---

### Post by tojonukokhadush on 2013-08-08
yeah thanks after this long! i could make it empty! and its fine that way either!! :-D :-D



&

Do you know how to add "Trash" entry on the left list of folders??

---

