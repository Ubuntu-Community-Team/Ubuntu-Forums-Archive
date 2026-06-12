---
title: "terminal"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by eilyn on 2008-09-25
I truly screw up,,
i was trying to download vlp i did something and my terminal setting went white.empty.... i must change something....so i was trying to delete everything hopping for a default option and i don't have any, i turn off the computer hopping for the same and nop i still got the same message: "There was a problem with the command for this terminal: Text was empty (or contained only whitespace)"

I tried as well terminal/reset and reset and clear no changes neither,
then i tried terminal/set character encoding/add and remove....i am able to add but not to changes in the automatic default which is UTF 8.... so what i should do now????

---

### Post by Ryadt on 2008-09-25
Try alt+f2 and ```
gnome-terminal --command=bash
```
Post back any errors.

---

### Post by Pelham123 on 2008-09-25
So are you saying that you can 'Start' the terminal, but the terminal box is completely white with no text or flashing cursor etc?

I would try having a look at the configuration menu...

Can access it by going to Applications->System Tools->Configuration Editor 

OR

by hitting 'F2' and typing gconf-editor

When config is up have a look in Apps->Gnome-terminal->Profiles->Defaults

Cant really suggest what to look for, but its pretty intuitive and look at the descriptions.

Good luck ;)

---

### Post by eilyn on 2008-09-25
Thanks, but is not working..... i am going to back up my information and reset the program.....some how i change the default  setting and is not allowing me to do as normal and since i don't have anything doc that is really important in this computer i am going to start again!!!!! but thanks any way for your advice. Have a great day!!!!:)

---

### Post by QUESTER on 2008-10-28
> **eilyn said:**
> I truly screw up,,
i was trying to download vlp i did something and my terminal setting went white.empty.... i must change something....so i was trying to delete everything hopping for a default option and i don't have any, i turn off the computer hopping for the same and nop i still got the same message: "There was a problem with the command for this terminal: Text was empty (or contained only whitespace)"

I tried as well terminal/reset and reset and clear no changes neither,
then i tried terminal/set character encoding/add and remove....i am able to add but not to changes in the automatic default which is UTF 8.... so what i should do now????
[COLOR=Lime][I][B]Hi everyone!
[/B][/I][/COLOR]and
Hi [COLOR=RoyalBlue]***eilyn***[/COLOR],

I'm new to this forum, new to Linux & new to Ubuntu.
I've been stumbling around in the dark, getting to grips with this O.S & one hell of an O.S. it is!!!

Now bruised & battered & very war-torn I think I can save you the tears of purple shines (drama & intro aside) hears my two sense forward, i hope it proves useful to you if you still are using Ubuntu or someone, anyone who may.

I am using **_[COLOR=DarkOrange]Ubuntu 8.04 LTS Desktop Edition[/COLOR]_** and this was the fix I used to overcome the very same problem *_**[COLOR=Navy]eilyn[/COLOR]**_* is having:

if the error message below, is the message you received, then carry on reading:
 
[I]**[COLOR=DarkOrchid]" [/COLOR]**_**[COLOR=DarkOrchid]there was a problem with the command for this terminal: text was empty (or containing only whitespace[/COLOR]**_**[COLOR=DarkOrchid])[/COLOR]****[COLOR=DarkOrchid]  " [/COLOR]**[U][B][COLOR=DarkOrchid]
[/COLOR][/B][/U][/I]
***[COLOR=RoyalBlue]HERE'S WHAT I DID[/COLOR]***

**[COLOR=DarkRed]1.[/COLOR]**    click **[COLOR=DarkSlateBlue]"[COLOR=Red]_Applications_[/COLOR]"[/COLOR]** on your toolbar.

[COLOR=DarkRed]**2.**[/COLOR]    (a menu will unfold) point to highlight [COLOR=DarkSlateBlue]**"_[COLOR=Red]Accessories[/COLOR]_"**[/COLOR]

[COLOR=DarkRed]**3.**[/COLOR]    (a menu will unfold) point to highlight & click on **[COLOR=DarkSlateBlue]"_[COLOR=Red]Terminal[/COLOR]_"[/COLOR]**

[COLOR=DarkRed]**4.**[/COLOR]    a window will now open & if you see an error message box with similar text as follows then carry on reading:

***[COLOR=Indigo]" [COLOR=Indigo]there was a problem with the command for this terminal: text was empty (or containing only whitespace)[/COLOR]  "[/COLOR]***

**[COLOR=DarkRed]5.[/COLOR]**    on the new window click on **[COLOR=DarkSlateBlue]"[/COLOR][COLOR=Red]_Edit_[/COLOR][COLOR=DarkSlateBlue]"[/COLOR]** (a menu will unfold) point to highlight & click on [COLOR=DarkSlateBlue][B]"_[COLOR=Red]Current Profile[/COLOR]_"
[/B][/COLOR]
[COLOR=DarkRed]**6.**[/COLOR]    (a window will open named (**_[COLOR=Red]Editing Profile "Default"[/COLOR]_**)) point to highlight & click on the tabbed button named **[COLOR=DarkSlateBlue]"[COLOR=Red]_Title And Command_[/COLOR]"[/COLOR]**

**[COLOR=DarkRed]7.[/COLOR]**    you will now see a section named **[COLOR=DarkSlateBlue]"[COLOR=Red]_Command_[/COLOR]"[/COLOR]** with five options:

 **[COLOR=Red]*[/COLOR][COLOR=DarkOliveGreen]_Run command as a login shell _[/COLOR]**                  [COLOR=Purple] ([COLOR=Red]**_TICK_**[/COLOR] THE CHECK BOX)[/COLOR]
    
**[COLOR=Red] *[/COLOR]_[COLOR=DarkOliveGreen]Update login records when command is launched[/COLOR]_**    [COLOR=Purple](**_[COLOR=Red]TICK[/COLOR]_** THE CHECK BOX)[/COLOR]
    
**[COLOR=Red] *[/COLOR]_[COLOR=DarkOliveGreen]Run a custom command instead of my shell[/COLOR]_**   [COLOR=Purple] ([COLOR=Red]_**UN[COLOR=Blue]-TICK[/COLOR]**_[/COLOR], MAKE SURE TO **[COLOR=Red]_U N T I C K_!!![/COLOR]** THE CHECK BOX)[/COLOR]
    
 **[COLOR=Red]*[/COLOR]**[COLOR=DarkOliveGreen]**_Custom Command_:** [/COLOR]        [COLOR=Purple] (THIS ITEM SHOULD NOW BE **_TRANSPARENT_** & **_UN-SELECTABLE_**)
    [/COLOR]
[COLOR=DarkOliveGreen]**[COLOR=Red] [/COLOR][COLOR=Red]*[/COLOR]_When command exits_:**[/COLOR]           [COLOR=Purple] (MAKE SURE THE BOX SHOWS:)    [ _[COLOR=Orange]**EXIT THE TERMINAL**[/COLOR]_ ][/COLOR]

**[COLOR=DarkRed]8.[/COLOR]**    ONCE YOU HAVE DONE ALL THE ABOVE CLICK THE **_[COLOR=Red]CLOSE[/COLOR]_** BUTTON _**[COLOR=Magenta]*(under some circumstances a pc restart maybe required)*[/COLOR]**_
 
[COLOR=DarkRed]**9.**[/COLOR]    NOW RE-OPEN THE TERMINAL AND ALL SHOULD BE AS IT WAS ORIGINALLY!

 ***[COLOR=RoyalBlue]   !!! Oh yeh, almost forgot to mention the [/COLOR]*****[COLOR=RoyalBlue]"[COLOR=Red]_RESET_[/COLOR]"[/COLOR]*****[COLOR=RoyalBlue] & [/COLOR]*****[COLOR=RoyalBlue]"_[COLOR=Red]RESET AND CLEAR[/COLOR]_"[/COLOR]*****[COLOR=RoyalBlue] commands found under [/COLOR]*****[COLOR=RoyalBlue]"_[COLOR=Red]TERMINAL[/COLOR]_"[/COLOR]*****[COLOR=RoyalBlue] Fold-Down Menu are like dos commands [/COLOR]*****[COLOR=RoyalBlue]"[COLOR=Red]_CLS_[/COLOR]"[/COLOR]*****[COLOR=RoyalBlue] &  [/COLOR]*****[COLOR=RoyalBlue]"_[COLOR=Red]CLS /ALL[/COLOR]_"[/COLOR]*****[COLOR=RoyalBlue] they are to clean the TERMINAL screen of text and/or reset any commands previously typed.[/COLOR]***


***[COLOR=DarkOrange]hope this comes as to some help for someone; GOOD LUCK!!![/COLOR]***

---

### Post by NomadDave on 2008-10-30
That was the information I was looking for... How to clear previously typed in information in the terminal window.

I tried it and all previous entries were still there. So, does someone else know how to clear the history or cache of the terminal window?:confused:

Thanks

---

### Post by jesseedavis on 2009-09-05
I'm needing like the opposite information. I need to know how to view a list or so of every command that has been typed into the terminal since we put the OS on here. When I hold the up arrow down to go through the previous commands, I can go all the way back that far, but I need to view everything that has shown up in some sort of text file. Is this possible? Where can I go to find this information?

---

### Post by XCan on 2009-09-05
All the way back to when the OS was installed? I don't know about that, but everything you see when you press the up arrow should be viewable in ```
 ~/.bash_history 
```

---

### Post by jesseedavis on 2009-09-05
We only installed the OS earlier this week, so there isn't too much. This command isn't working, it says its not found.

---

### Post by winotree on 2009-09-05
~/.bash_history *is shorthand*.  Look in /home/user/.bash_history -- it's a single file.  Or preface the command with the name of your favorite text editor, in *my* case it looks like **mousepad ~/.bash_history ** ;)

---

### Post by jesseedavis on 2009-09-05
Ok that worked! Thank you!! It even went back to when we set the password for the user!

---

### Post by winotree on 2009-09-05
You're more than welcome!  :D

---

### Post by zipperback on 2009-09-05
> **jesseedavis said:**
> We only installed the OS earlier this week, so there isn't too much. This command isn't working, it says its not found.


Applications --> Accessories --> Terminal

```

less ~/.bash_history

```

Then you can page up and page down through it.
When finished just press q and it will exit.

- zipperback

---

