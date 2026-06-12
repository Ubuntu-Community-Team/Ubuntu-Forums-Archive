---
title: "[SOLVED] themes"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by im new here on 2008-07-29
i downloaded a new theme package how can i use it ?

---

### Post by rraj.be on 2008-07-29
Just right click in desktop and select change desktop background.

In that select Theams tab.

Click on Install.

Now search for your new downloaded theam and install and Click Apply.

Thats it.

---

### Post by im new here on 2008-07-29
there is nothing called desktop background and there is nothing like a theme tab do u remember that im using xubuntu

---

### Post by ModdTaco on 2008-07-29
You should be able to extract it to /home/username/.themes and use the regular theme chooser to select it. At least thats how you do it in xubuntu. In Ubuntu you would right click and go to Change Desktop Backround. It really depends on what version you are using.

---

### Post by steveneddy on 2008-07-29
I was about to say that i just answered this question, but the OP has it tagged as xubuntu.

---

### Post by im new here on 2008-07-30
there is nothing in /home/username called .themes an its not even a hidden file or folder

---

### Post by Brightbelt on 2008-07-30
Hi, I use Xubuntu. the easy way is to download and install themes through the Synaptic Package Manager (that's from Xfce Menu/System/Synaptic Package Manager).

Once you're in Synaptic do a search for say Xfce-gtk and themes will come up. Right-click what you want to select and choose 'Mark for Installation', and then Click 'Apply' up on the interface there.

Once you've done that, you can go to the Xfce Menu/Settings/Settings Manager and that pulls up your whole interface to configure your desktop.
Once that's up, choose the icon labeled 'User Interface' and because you installed your themes in Synaptic, they'll be there in the list to choose from.

I hope this helps,...Frank B.

---

### Post by Brightbelt on 2008-07-30
Also, here's a good resource... Things are well explained here...

[http://xubuntublog.wordpress.com/2008/02/10/design-your-own-desktop-with-xfce-44/](http://xubuntublog.wordpress.com/2008/02/10/design-your-own-desktop-with-xfce-44/)

---

### Post by mali2297 on 2008-07-30
> **im new here said:**
> there is nothing in /home/username called .themes an its not even a hidden file or folder

Well, create it then. From the terminal,
```

mkdir ~/.themes

```
Alternatively, use the file manager Thunar to create the folder.

Another resource:
[http://wiki.xfce.org/howto/install_new_themes](http://wiki.xfce.org/howto/install_new_themes)

---

### Post by JoneYee on 2008-07-30
[https://help.ubuntu.com/community/UbuntuEyeCandy](https://help.ubuntu.com/community/UbuntuEyeCandy) - Ubuntu Eye Candy Instructions

---

### Post by im new here on 2008-07-30
i think that nobody here usues xubuntu which is different

---

### Post by JoneYee on 2008-07-30
> **im new here said:**
> i think that nobody here usues xubuntu which is different

Oops....

[How to Install a Theme in Xubuntu]("http://ubuntuforums.org/showthread.php?t=462556")

---

### Post by im new here on 2008-07-30
JoneYee the problem wasnt solved in that thread

---

### Post by JoneYee on 2008-07-30
> **im new here said:**
> JoneYee the problem wasnt solved in that thread

From what I read it is as simple as extracting it to /home/username/.themes

From there use the Xubuntu Theme Chooser.

Just trying to understand where it is failing in that process.

---

### Post by im new here on 2008-07-30
the failing is because the theme chooser dosnt locate the theme

---

### Post by aomlives on 2008-07-30
You have to select the theme in the Window Manager, not the User Interface Settings. I have Xubuntu myself and I just tested it, so it works.

Here's my source:
[http://www.linuxquestions.org/questions/ubuntu-63/xubuntu-6.06-trouble-installing-themes-449229/](http://www.linuxquestions.org/questions/ubuntu-63/xubuntu-6.06-trouble-installing-themes-449229/)

---

### Post by JoneYee on 2008-07-30
> **im new here said:**
> the failing is because the theme chooser dosnt locate the theme

Ok...

1. Make sure it is a XFCE theme and not a Gnome Theme. 
2. Extract the TAR.GZ to /home/*username*/.themes
3. Choose in Theme Chooser.

I am going to DL Xubuntu and install onto a VM to try to replicate this.  Can you tell me where you DL the exact theme tarball you are trying to install?

Edit:  My replication may have to wait a bit, Xubuntu is taking a very long time to download at work.

---

### Post by aomlives on 2008-07-30
> **JoneYee said:**
> I am going to DL Xubuntu (...)

I really wouldn't do that if I were you. It's simply not necessary. Just went to [http://www.xfce-look.org/](http://www.xfce-look.org/) and tried to install the most downloaded Mac OS Aqua theme and it worked again, although this time it showed up in the User Interface Settings. The instructions above really do work, just need to figure out where in the configuration panel the theme will show up.

---

### Post by JoneYee on 2008-07-30
> **aomlives said:**
> I really wouldn't do that if I were you. It's simply not necessary. Just went to [http://www.xfce-look.org/](http://www.xfce-look.org/) and tried to install the most downloaded Mac OS Aqua theme and it worked again, although this time it showed up in the User Interface Settings. The instructions above really do work, just need to figure out where in the configuration panel the theme will show up.

Thanks for verifying the instructions

I have no issue having a Vm for Xubuntu, never know when I may need it for another question.

---

### Post by im new here on 2008-07-30
i have some news ok i found the themes folder in /usr/share/themes i tried to copy the new theme folder to the /usr/share/themes but the paste butten in right click menu is grey

---

### Post by JoneYee on 2008-07-30
> **im new here said:**
> i have some news ok i found the themes folder in /usr/share/themes i tried to copy the new theme folder to the /usr/share/themes but the paste butten in right click menu is grey

You arent navigating as root

```
sudo nautilus
```

Then try to put the tar.gz into the folder.

---

### Post by mali2297 on 2008-07-30
I suggest that you rather put the extracted theme in a .themes folder in your home directory. Did you actually try that?

---

### Post by im new here on 2008-07-30
and please dont tell me to extract th package to that location beacause i already tried and it said thats it is unable to do that

---

### Post by im new here on 2008-07-30
sudo nautilus !!! im using xubuntu and i think i dont have nautilus

---

### Post by aomlives on 2008-07-30
It's ```
sudo thunar
``` in Xubuntu

---

### Post by JoneYee on 2008-07-30
> **aomlives said:**
> It's ```
sudo thunar
``` in Xubuntu

Why do i keep forgetting that... thanks. Prolly cause its after lunch and my brain is disengaging.

---

### Post by im new here on 2008-07-30
plz explain what is that root thing i dont understand it but i all i know is that i enter a user name and password before starting xubuntu

---

### Post by JoneYee on 2008-07-30
> **im new here said:**
> plz explain what is that root thing i dont understand it but i all i know is that i enter a user name and password before starting xubuntu

open Terminal

type this in
```
sudo thunar
```

It should open a file browser, in which you have total admin permissions.  Navigate to where the extracted tar.gz is.... copy the extracted folder, navigate to /home/*username*/.themes and paste it there.  

root is the god admin for your installation.  Some functions require admin permissions to execute.  Copying to a folder you are not owner of, or do not have write permission to would require admin/root authority.

---

### Post by mali2297 on 2008-07-30
> **im new here said:**
> and please dont tell me to extract th package to that location beacause i already tried and it said thats it is unable to do that

..and you created the directory first?

Please post the exact errors that you get.

---

### Post by im new here on 2008-07-30
yeaaaaaaaaaaaaa its copied first step done now the folder dosnt apear in th theme chooser should i restart th computer

---

### Post by JoneYee on 2008-07-30
I will defer to aomlives here... The files are copied... (not the tar.gz but the folder that was in the tar.gz right?)

I am not familiar with the Xubuntu Theme Chooser's behavior, so I would wait for an answer from him or a familiar Xubuntu user.

---

### Post by im new here on 2008-07-30
i have a clue for u JoneYee look the folder of the new theme in the new location has a x on it does that meen something like permission or read and write ?

---

### Post by mali2297 on 2008-07-30
> **im new here said:**
> yeaaaaaaaaaaaaa its copied first step done now the folder dosnt apear in th theme chooser should i restart th computer

No, you should not need to do that. Try reopening the theme chooser.

---

### Post by im new here on 2008-07-30
i did mali2297 but it didnt appear that x has to do something with the problem

---

### Post by mali2297 on 2008-07-30
Open a terminal, and copy/paste
```

ls -l ~/.themes /usr/share/themes

```
What is the output?

---

### Post by aomlives on 2008-07-30
Did you look in both the User Interface Settings and Window Manager? (see screenshot, I believe that's what these menus are called in English, sorry about my Dutch translations and the quick and inaccurate drawing:))

Indeed it's not necessary to reboot. It should work just look in both sections.

---

### Post by im new here on 2008-07-30
listed all themes and also indicated the new theme folder 

ill also want to explain something the x is on the new copied folder not on the folder "themes"

---

### Post by mali2297 on 2008-07-30
> **im new here said:**
> listed all themes and also indicated the new theme folder 

ill also want to explain something the x is on the new copied folder not on the folder "themes"

Fine, but would you please post the output. Then I will be able to see that the theme is at the right place and also see whether you need to change permissions.

---

### Post by im new here on 2008-07-30
how could i paste the output here mali

---

### Post by mali2297 on 2008-07-30
> **im new here said:**
> how could i paste the output here mali

Highlight the text that you want to copy (left-click and drag), then move the cursor to the place where you want to paste, left-click (to focus) and lastly *middle-click*. If you don't have a middle mouse button, press two buttons simultaneously instead.

---

### Post by im new here on 2008-07-30
that doesnt work in terminal

---

### Post by aomlives on 2008-07-30
Just drag (hold left mouse button) to select the output in the terminal, then right click and choose copy. Then you can past it here.

---

### Post by mali2297 on 2008-07-30
> **im new here said:**
> that doesnt work in terminal

It should. Can't you highlight the text?

Note that you don't need to use any menus. Just highlight the text, then go directly to the browser without closing the terminal, left-click in the message box here and middle-click.

EDIT: While you're at it, could you post a link to the theme that you are trying to install?

---

### Post by im new here on 2008-07-30
thanks everybody i got it now after collecting information from all posts : 

1-extract package
2-open a terminal and type sudo thunar 
3-a new application will open use it to copy the folder extracted from the package to /usr/share/themes
4-now open applications>>>>>>settings>>>>>settings manager >>>>>>>>> user interface preferences and chose the theme :)

---

### Post by im new here on 2008-07-30
can anybody help me with my bluetooth threads

---

