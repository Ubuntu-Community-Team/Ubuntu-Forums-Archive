---
title: "HOWTO: Terminal for desktop background."
date: 2005-05-24
forum: Outdated Tutorials &amp; Tips
---

### Post by krusbjorn on 2005-05-24
Hey!

Here's how to get a completely transparent terminal at your desktop background, on all workspaces, without appearing in the taskbar/windows list.

[There was a link to a screenshot here, but somehow the file disappeared. Check korupt's post on page 8 for a screenie.]

First off, you need **Eterm and devilspie**:

```
sudo apt-get install eterm devilspie
```

Next, we need to make a configuration file for devilspie. Copy the code below into your favorite text editor and save the file as **.devilspie.xml** (please note the dot in the beginning of the file name) in your home folder:

```
<?xml version="1.0"?>
<!DOCTYPE devilspie SYSTEM "devilspie.dtd">

<devilspie>
  <flurb name="Eterm pinned and no taskbar">
    <matchers>
       <matcher name="DevilsPieMatcherWindowName">
         <property name="application_name" value="Eterm"/>
       </matcher>
    </matchers>
<!-- The action below will pin Eterm to all workspaces-->
     <actions>
         <action name="DevilsPieActionSetWorkspace">
            <property name="pinned" value="TRUE"/>
      </action>
<!-- The action below will remove Eterm from the windows list and the Workspace Switcher (thanks Trash:)-->
      <action name="DevilsPieActionHide">
        <property name="skip_tasklist" value="TRUE"/>
        <property name="skip_pager" value="TRUE"/>
      </action>
     </actions>
</flurb>
</devilspie>
```
The above code will make devilspie tell gnome not to display Eterm in the windows list and Workspace Switcher, and to pin it to all workspaces.

Now, go to **System -> Preferences -> Sessions**. Add **devilspie** to your startup programs.

Also, you need to **add Eterm to your startup programs**. It could look something like this:
```
Eterm  -x -0 --trans --scrollbar=off --buttonbar 0 --geometry 200x60+80+40 --font-fx none -f white
```
**NOTE**: You probably need to change some of the options applied to Eterm (X and Y offset, terminal size, text colour etc). Those are the options that fit MY desktop. Do:

```
man Eterm
``` 
If you dont know what values to change.

**Dont forget** to make sure devilespie starts BEFORE Eterm on bootup.

**ALSO NOTE**: As long as devilespie is running, it will apply its setting to Eterm whenever you launch it, meaning you wont be able to use Eterm "normally" (in a window etc)


This is my first How-To, so be easy on me if there are any errors.
Good luck!
 -Johannes

---

### Post by trash on 2005-05-24
Great howto! works perfectly on pc

too bad devilspie isn't available for mac!
Has anybody figured out how to fix this(mac issue?)...
$ Eterm
Eterm:  Error:  Can't open pseudo-tty -- No such file or directory
Eterm:  Error:  Unable to run sub-command.

[google search](http://www.google.ca/search?hl=en&client=firefox&rls=org.mozilla%3Aen-US%3Aunofficial&q=ubuntu+Eterm+Can%27t+open+pseudo-tty&btnG=Search&meta=)  turned up a few other people with the same problem but so far no fix:(

also it was reported on this forum but no fix
[http://ubuntuforums.org/showthread.php?t=7730&highlight=eterm+tty](http://ubuntuforums.org/showthread.php?t=7730&highlight=eterm+tty)

---

### Post by 23meg on 2005-05-24
nice to have this info tidied up in one place. you should capitalize the E in Eterm, though.

also, if you don't want Eterm appearing in the workspaces pager, you can add the following to the action flurb under DevilsPieActionHide in .devilspie.xml:

```
<property name="skip_pager" value="TRUE"/>
```

---

### Post by pdk001 on 2005-05-24
it doesnt work for me
what does this "use the "Show Desktop" panel item" meaning?

---

### Post by trash on 2005-05-25
The show desktop thingy is a panel control that when clicked hides all windows on your destop allowing you to see your desktop, when clicked again it restores all the hidden windows... but in this case it won't restore Eterm.
Does Eterm start at all?


EDIT: actually hitting the 'show desktop' again does restore Eterm, all one can't do is restore only Eterm... no biggy really.

I am so loving borderless windows are more apps going to be going this way?

---

### Post by dominik on 2005-05-25
that does not work > sudo apt-get install Eterm devilspie you have to write Eterm like this **e**term ;)

---

### Post by pdk001 on 2005-05-25
oh my mistook
i typed a CAP "eterm" intead of "Eterm"
but this is appear when i hitting a show windows

---

### Post by Leif on 2005-05-25
Thanks for the howto, but I get a problem on my system. Even if I set the startup priority to 99, the Eterm starts before my wallpaper is set, so it gets a random background. Maybe this is because I have xinerama ?

---

### Post by trash on 2005-05-25
[QUOTE=Leif]Thanks for the howto, but I get a problem on my system. Even if I set the startup priority to 99, the Eterm starts before my wallpaper is set, so it gets a random background. Maybe this is because I have xinerama ?[/QUOTE]


I had that problem too all you need to do is save your last session with Eterm NOT running and make sure to delete it from your current session.
hope it works!

---

### Post by krusbjorn on 2005-05-25
Thanks for the input everyone. I've edited the post, so now things should work :)

---

### Post by Rehevkor on 2005-05-25
This is pretty neat, but I can't paste anything into the eterm window. Ctrl-V doesn't work, middle mouse button doesn't work, and there's no context menu with edit functions. Is this normal?

If it is, I'll be uninstalling it shortly ;)

Edit: Ok, so hitting left and right mouse together pastes, but it forces a return immediately. Is there any way to paste at the prompt without triggering a return and executing the pasted command?

---

### Post by krusbjorn on 2005-05-25
[QUOTE=Rehevkor]This is pretty neat, but I can't paste anything into the eterm window. Ctrl-V doesn't work, middle mouse button doesn't work, and there's no context menu with edit functions. Is this normal?

If it is, I'll be uninstalling it shortly ;)

Edit: Ok, so hitting left and right mouse together pastes, but it forces a return immediately. Is there any way to paste at the prompt without triggering a return and executing the pasted command?[/QUOTE]

To me the middle mouse button pastes. 
However, if i close the program from where i copied the text, the clipboard clears. It's been like that since i installed hoary, havent bothered to try to fix it ;)

Edit: oops, lots of typos.

---

### Post by trash on 2005-05-25
[QUOTE=Rehevkor]This is pretty neat, but I can't paste anything into the eterm window. Ctrl-V doesn't work, middle mouse button doesn't work, and there's no context menu with edit functions. Is this normal?

If it is, I'll be uninstalling it shortly ;)

Edit: Ok, so hitting left and right mouse together pastes, but it forces a return immediately. Is there any way to paste at the prompt without triggering a return and executing the pasted command?[/QUOTE]


There are a few helpful hints in this thread too...
[http://ubuntuforums.org/showthread.php?t=36356&highlight=eterm](http://ubuntuforums.org/showthread.php?t=36356&highlight=eterm)

Also I have experienced the 'return' thingy as well and it seems to happen when I copy beyond the last character in the line I am copying.... I have started copying from the end to the start to stop this from happening.

---

### Post by jrobcet on 2005-05-25
[QUOTE=Rehevkor] Is there any way to paste at the prompt without triggering a return and executing the pasted command?[/QUOTE]

I think Shift+Insert is what you're looking for.

---

### Post by trash on 2005-05-25
[QUOTE=krusbjorn]However, if i close the program from where i copied the text, the clipboard clears. It's been like taht since i installe ohary, havent bothered to try to fix it ;)[/QUOTE]


It's soooooo annoying!!

---

### Post by krusbjorn on 2005-05-25
[QUOTE=trash]It's soooooo annoying!![/QUOTE]

I guess this is the way ;)
[http://www.ubuntuforums.org/showthread.php?t=10319](http://www.ubuntuforums.org/showthread.php?t=10319)

---

### Post by Rehevkor on 2005-05-25
[QUOTE=trash]I had that problem too all you need to do is save your last session with Eterm NOT running and make sure to delete it from your current session.
hope it works![/QUOTE]

I have the same problem, but I don't understand what you mean. I know how to save my session when I log out, but what is it that I'm supposed to delete?

Also, since I tried to save the session anyway, firestarter is complaining that I can't start it without root privileges on startup. It was working fine before  ](*,)

Edit: Also, is there a way I can just set it to use a solid background color instead of transparency? I tried removing --trans and adding -b white but it just used one of the random backgrounds instead.

God, that firestarter crap is annoying. It took me forever to fix it when I first installed it, and now I'm stuck with it again. It's in the sudoers file, I'm running it with sudo, and I've tried changing the start order a dozen times. I'm on the verge of just uninstalling the stupid thing :-x

---

### Post by trash on 2005-05-25
Ya, just make sure Eterm is not running when you save session and logout.

I'm running firestarter at boot and I don't have any issues with it... have you tried  setting the  startup order for Eterm from 50 (default) to something like... well mine is at 65.

sorry can't help you with the background thingy.

---

### Post by thomerz on 2005-05-26
I have done everything like written in this tutorial, but when I klick on my "Show Desktop" Icon, the Eterm "Window" is also hidden.

Any idea?

greets thom

---

### Post by #Vizc@ch@ on 2005-05-27
I have a couple of issues: 

1. When i log into gnome, i have to start an application in order to have eterm appear on my desktop  :roll: . Why could this be? Does it has something to do with the number i gave it to boot on system startup ( i have 48 for evilspie and 49 for Eterm)

2. How can i prevent Eterm from being hided when i click "show desktop" icon ?

Thanks for the how to , it's great !  :)

---

### Post by krusbjorn on 2005-05-27
[QUOTE=thomerz]I have done everything like written in this tutorial, but when I klick on my "Show Desktop" Icon, the Eterm "Window" is also hidden.

Any idea?

greets thom[/QUOTE]

As Trash stated is his post:
> EDIT: actually hitting the 'show desktop' again does restore Eterm, all one can't do is restore only Eterm... no biggy really.

---

### Post by thomerz on 2005-05-27
[QUOTE=krusbjorn]As Trash stated is his post:
Quote:
EDIT: actually hitting the 'show desktop' again does restore Eterm, all one can't do is restore only Eterm... no biggy really. [/QUOTE]

yes but when i have opened some windows and want to get do my  desktop with eterm on it, i hit show desktop, when i hit show desktop again, all the other windows are also restored, not only eterm :???:

---

### Post by krusbjorn on 2005-05-27
[QUOTE=thomerz]yes but when i have opened some windows and want to get do my  desktop with eterm on it, i hit show desktop, when i hit show desktop again, all the other windows are also restored, not only eterm :???:[/QUOTE]
Yeah, i dont know how to fix that. If it wouldnt bother you to have Eterm in the "window list", remove <property name="skip_tasklist" value="TRUE"/> from the devilspie xml file, and it will appear on the windows list/taskbar.

---

### Post by JohnC86 on 2005-05-29
HI, good tutorial, however I was wondering:

Is it possible to keep eterm on the bottom of all other windows? so if I click on it, I can type in it, without it showing on top of all my other windows. No biggy really but if it could be pinned underneath everything itd be better imo.

---

### Post by Gandalf on 2005-06-03
Great HOWTO it makes my desktop complete,
[[IMG]http://img157.echo.cx/img157/5751/screenshot6ld.th.jpg[/IMG]](http://img157.echo.cx/my.php?image=screenshot6ld.jpg)

Thanks

a little tip i use myself, because it's a small window without a maximize icon so System -> Preferences -> Keyboard Shortcuts -> Window Management -> Toggle Fullscreen, define it to whatever you want (i use Alt+Enter)
this way on this teminal i just click Alt+Enter to have my Desktop Wallpaper Full Screen with teminal above it


one question though, is it possible to make the Windows hiding icon (bottom left) not to hide the terminal?

---

### Post by baraider on 2005-06-03
[QUOTE=Gandalf]Great HOWTO it makes my desktop complete,
[[IMG]http://img157.echo.cx/img157/5751/screenshot6ld.th.jpg[/IMG]](http://img157.echo.cx/my.php?image=screenshot6ld.jpg)

Thanks

a little tip i use myself, because it's a small window without a maximize icon so System -> Preferences -> Keyboard Shortcuts -> Window Management -> Toggle Fullscreen, define it to whatever you want (i use Alt+Enter)
this way on this teminal i just click Alt+Enter to have my Desktop Wallpaper Full Screen with teminal above it


one question though, is it possible to make the Windows hiding icon (bottom left) not to hide the terminal?[/QUOTE]
 got it working now...

quick question...without boders and menus, how i copy and paste in this eterm.....Shift-clt C/v or Ctlr-c/v does not seem to work.

---

### Post by Gandalf on 2005-06-03
not like this, it's done with Ctrl+Insert to copy and Shift+Insert to paste

---

### Post by baraider on 2005-06-03
[QUOTE=Gandalf]not like this, it's done with Ctrl+Insert to copy and Shift+Insert to paste[/QUOTE]
 Nice....that brings the question...

  Why and can we define how to copy and paste across the system, like Clt-C and Ctl-V.....this will be much easier than to remember how each program copies and pastes

---

### Post by Gandalf on 2005-06-03
[QUOTE=baraider]Nice....that brings the question...

  Why and can we define how to copy and paste across the system, like Clt-C and Ctl-V.....this will be much easier than to remember how each program copies and pastes[/QUOTE]
 i don't know if this is possible i want it too, but you know in terminal Ctrl+C is to terminate a script

---

### Post by Gandalf on 2005-06-05
Hello,
i don't know why but it always load screwed up, look at the pic
[[img]http://img68.echo.cx/img68/7250/screenshot1hw.th.jpg[/img]]](http://img68.echo.cx/my.php?image=screenshot1hw.jpg)
i have to either kill it and re-load it manually or logout/login
it always open like this after i REBOOT my laptop

is there anything to do?
thank

---

### Post by wawa on 2005-06-05
Nice HowTo,  terminal is running ok with transparent backgroung...the only problems I have is:
 When I log in the Gnome splash screen freezes and the terminal is not loaded until I start a program like Firefox or something is when it dessapears and the terminal is loaded
I still have Eterm showing up in the pannel and its showing up in the first workspace only

Devilspie is configured to load and run before Eterm

Any help to solve this will be appreciated

Thanks

---

### Post by Behel on 2005-06-07
I think I had a similar problem...

I just change the time interval between successive loading and it finally worked.

Here is what I used:

gdesklets 45 (if you need)
devilspie   50
Eterm...    55

BL

---

### Post by Behel on 2005-06-07
[QUOTE=Gandalf]Hello,
i don't know why but it always load screwed up, look at the pic
[[img]http://img68.echo.cx/img68/7250/screenshot1hw.th.jpg[/img]]](http://img68.echo.cx/my.php?image=screenshot1hw.jpg)
i have to either kill it and re-load it manually or logout/login
it always open like this after i REBOOT my laptop

is there anything to do?
thank[/QUOTE]


You may load Eterm too soon, and the wallpaper is not loaded yet so that Eterm decides to use one of its own background instead of your wallpaper....

BL

---

### Post by bahumbug on 2005-06-12
no matter what the order i set eterm to (200 is as high as it would go).  I still get the same problem too.  I think my desktop is too graphics intensive?

when I set devilspie to 49 and eterm to 50, then the splash loader thingie just stays at nautilus, and i have to start firefox or something to get eterm loaded.

is there a way to start the wallpaper quickly?

thanks

---

### Post by drewxhawaii on 2005-06-12
the only way i could get it to work with the transparent background is to start a program AFTER devilspie and BEFORE Eterm

this worked out beautifully, however, because i wanted thunderbird (email) to run at start up anyway.

thank you for this tutorial.

my startup programs are as follows:

devilspie 50
mozilla-thunderbird 51
Eterm 52

i hope this helps some of you

---

### Post by drewxhawaii on 2005-06-13
[QUOTE=Gandalf]not like this, it's done with Ctrl+Insert to copy and Shift+Insert to paste[/QUOTE]
awesome!

i was just gonna ask about this

---

### Post by feralert on 2005-06-13
[QUOTE=drewxhawaii]the only way i could get it to work with the transparent background is to start a program AFTER devilspie and BEFORE Eterm

this worked out beautifully, however, because i wanted thunderbird (email) to run at start up anyway.
[/QUOTE]

Thanks drewxhawaii, this works for me too.

I also had the weird background problem but now its gone, this is what i have:

45 devilspie
50 gnome-cliboard-daemon
51 Eterm
52 Eterm

Cheers!  \\:D/

---

### Post by feralert on 2005-06-13
I had Eterm working fine, starting devilspie before Etern and all.

But then i tried to get Eterm to execute a command automatically, with the --execute option, and works fine but the problem is that it displays Eterm in the windows list again!  ](*,) (Im trying to have a 'tail -f' of the most important log files), 

Any clues on how to make it disappear -again-??

(And yes, in case anyone asks, im running devilspire before the Eterms  ;-)  )

---

### Post by Gandalf on 2005-06-13
try to add tail to ~/.devilspie.xml as Eterm has been added

---

### Post by feralert on 2005-06-13
[QUOTE=Gandalf]try to add tail to ~/.devilspie.xml as Eterm has been added[/QUOTE]

Thanks Gandalf. 
Tried that and works but im using another solution which is to use de -T option to give the window the name your like, so i used '-T Eterm' on all of them to have devilspie get rid of them and works like a charm!

 \\:D/ Thaaaanks!!

Edited to add:
BTW i have noticed that if you click on the 'show desktop' and when having all windows minimized you restore any one of them manually and then click on 'show desktop' again,  it wont restore the Eterms anymore, and there is no way to have them back, try it and see.
Something to have Eterm not to obey the 'show desktop' orders is badly needed  O:)

---

### Post by neotope on 2005-06-13
[QUOTE=feralert]Thanks Gandalf. 
Tried that and works but im using another solution which is to use de -T option to give the window the name your like, so i used '-T Eterm' on all of them to have devilspie get rid of them and works like a charm!

 \\:D/ Thaaaanks!!

Edited to add:
BTW i have noticed that if you click on the 'show desktop' and when having all windows minimized you restore any one of them manually and then click on 'show desktop' again,  it wont restore the Eterms anymore, and there is no way to have them back, try it and see.
Something to have Eterm not to obey the 'show desktop' orders is badly needed  O:)[/QUOTE]
 I can't get Eterm to be transparent.  If I run the command from a terminal it will load Eterm with a transparent backup but when I initially start Gnome it has a background.

---

### Post by SqdnGuns on 2005-06-21
For those that are not aware.................to move the terminal around, hold down "alt" and "left click" anywhere in the terminal to move it around...........

---

### Post by simple on 2005-06-21
delete me

---

### Post by SWAT on 2005-06-28
I have the same problem as (simple) just above me. Eterm isn't invisible on the taskbar, which is annoying. I'm using Hoary, Eterm 0.9.2, and devilspie. Help?
Problem SOLVED: I had a typo at the .devilspie.xml file (I forgot the .xml)

This problem I'll to figure out myself ==> At my computer the background of the eterm window is strange (it's not transparant, just some kind of weird background)
It looks like it loads a different Eterm wallpaper everytime it loads, very strange. Anyone know what this could be? When I start Eterm after a full startup it works fine, but I want to autstart it with transparancy! :(

Problem not SOLVED: Just comment out the line _*file %random(`cat pixmaps.list`)*_ in the *_/usr/share/Eterm/themes/trans_* file. Somehow this DOESN'T work

---

### Post by vladuz976 on 2005-07-10
[QUOTE=krusbjorn]Hey!

Here's how to get a completely transparent terminal at your desktop background, on all workspaces, without appearing in the taskbar/windows list.

[Screenshot](http://home.tiscali.se/jossehan/eterm.png) 

First off, you need **Eterm and devilspie**:

```
sudo apt-get install eterm devilspie
```

Next, we need to make a configuration file for devilspie. Copy the code below into your favorite text editor and save the file as **.devilspie.xml** (please note the dot in the beginning of the file name) in your home folder:

```
<?xml version="1.0"?>
<!DOCTYPE devilspie SYSTEM "devilspie.dtd">

<devilspie>
  <flurb name="Eterm pinned and no taskbar">
    <matchers>
       <matcher name="DevilsPieMatcherWindowName">
         <property name="application_name" value="Eterm"/>
       </matcher>
    </matchers>
<!-- The action below will pin Eterm to all workspaces-->
     <actions>
         <action name="DevilsPieActionSetWorkspace">
            <property name="pinned" value="TRUE"/>
      </action>
<!-- The action below will remove Eterm from the windows list and the Workspace Switcher (thanks Trash:)-->
      <action name="DevilsPieActionHide">
        <property name="skip_tasklist" value="TRUE"/>
        <property name="skip_pager" value="TRUE"/>
      </action>
     </actions>
</flurb>
</devilspie>
```
The above code will make devilspie tell gnome not to display Eterm in the windows list and Workspace Switcher, and to pin it to all workspaces.

Now, go to **System -> Preferences -> Sessions**. Add **devilspie** to your startup programs.

Also, you need to **add Eterm to your startup programs**. It could look something like this:
```
Eterm  -x -0 --trans --scrollbar=off --buttonbar 0 --geometry 200x60+80+40 --font-fx none -f white
```
**NOTE**: You probably need to change some of the options applied to Eterm (X and Y offset, terminal size, text colour etc). Those are the options that fit MY desktop. Do:

```
man Eterm
``` 
If you dont know what values to change.

**Dont forget** to make sure devilespie starts BEFORE Eterm on bootup.

**ALSO NOTE**: As long as devilespie is running, it will apply its setting to Eterm whenever you launch it, meaning you wont be able to use Eterm "normally" (in a window etc)


This is my first How-To, so be easy on me if there are any errors. And sorry if my english hardly is understandable ;)

Good luck!
 -Johannes[/QUOTE]
 can i somehow use aterm for this or gnome-terminal. how would i make those borderless and menuless.
eterm is really hard to configure font's in. i am trying to you bitstream-vera-sans-monospace which i had for gnome terminal. really pleasant.

---

### Post by skyboy on 2005-07-11
Worked great for me on KDE 3.4.1
great Howto

---

### Post by ghostintheshell on 2005-07-16
Hi,

for more infos about DevilsPie (I really love this program :D) I invite you to take a look [here](http://www.ubuntuforums.org/showthread.php?t=49347) 

Thank you for your howto (that works well :D) and enjoy DevilsPie not only for Eterm but for all your applications :)

---

### Post by vladuz976 on 2005-07-20
[QUOTE=Behel]I think I had a similar problem...

I just change the time interval between successive loading and it finally worked.

Here is what I used:

gdesklets 45 (if you need)
devilspie   50
Eterm...    55

BL[/QUOTE]
 hi
i followed the instructions carefully and everything works out fine, except that eterm always shows in the gdeklets toolbar (or workspace i guess)
i have tried all combinations i found on this thread but it just doesn't work.
here is my current setup:
45 devilspie
50 gnome-clipboard-daemon
51 gdesklets
52 Eterm .......

anybody any ideas?

---

### Post by bpilgrim1979 on 2005-07-26
This is cool.  I'll check it out.

Right now I use a standard console window with a semi-transparent background.

---

### Post by aran384 on 2005-08-03
i do not like this and was wondering how do i get rid of it???

---

### Post by Shwiing on 2005-08-03
Well I believe you can go in the terminal and type:

package remove eterm

or...

go to Add/Remove Programs and search eterm and uncheck it then click apply.

---

### Post by OttoDestruct on 2005-08-05
Is there a way to 'tint' the window some? I've read over the man but perhaps I just glanced over it, and I'm not seeing a way.

---

### Post by aran384 on 2005-08-06
ive kinda sorted out what was making it so i dont like it but the transparcy isnt working on startup ??? 

i have to Ctrl + right click and toggle transparcy which i dont like also i have to move it everytime i boot up any way to fix these problems ???

---

### Post by krusbjorn on 2005-08-06
[QUOTE=OttoDestruct]Is there a way to 'tint' the window some? I've read over the man but perhaps I just glanced over it, and I'm not seeing a way.[/QUOTE]

From the Eterm man file:

   --tint color
              Tints the background pixmap (either an image file or the  trans&#8208;
              parent  portion can be shaded).  The mask is an integer, usually
              specified in hexadecimal in the form  0xRRGGBB,  where  RR,  GG,
              and BB are hexadecimal numbers between 00 and ff (0 and 255 dec&#8208;
              imal) which represent the brightness of the image’s red,  green,
              and  blue  values,  respectively.   A value of 00 will mask that
              color out entirely, while a value of ff  will  not  change  that
              color at all.

              You  may  also specify an X color such as grey75 or MidnightBlue
              or #babb7f instead of a mask.

---

### Post by krusbjorn on 2005-08-06
[QUOTE=aran384]ive kinda sorted out what was making it so i dont like it but the transparcy isnt working on startup ??? 

i have to Ctrl + right click and toggle transparcy which i dont like also i have to move it everytime i boot up any way to fix these problems ???[/QUOTE]

To adjust where the Eterm window is placed you need to change the offsets. Read the how-to again and you'll notice how.

Eterm should be completely transparent if you use the options i mentioned in the how-to: -x -0 --trans --scrollbar=off --buttonbar 0

---

### Post by spacemonkey on 2005-08-06
Does anyone know how to eliminate the drop shadow on Eterm when using drop shadows with xcompmgr?

---

### Post by Sebischn on 2005-08-16
Hey, nice Howto! 

I got a small and silly question, but I'll ask it anyway :). I've successfully added devilspie to startup, but if I add "Eterm  -x -0 --trans --scrollbar=off --buttonbar 0 --geometry 200x60+80+40 --font-fx none -f white" in the same way, it's always beeing removed from the Sessions Manager. If I run the Command via shell, it works perfect. So, how do I add the Eterm command to startup? Thx in advance. 

Regards..

---

### Post by traherom on 2005-08-16
Ok... this is just grand, but what if you actually put stuff on your desktop? At least for me, they get covered up. (The background loads fine, but as is stated in the man: 
>        -O, --trans
              This gives a  **pseudo-transparent**  Eterm.   The  image  is  taken
              directly  from the root window, so any requests for changing the
              pixmap  are  ignored.   If  you   do   not   use   Enlightenment
              ([http://www.enlightenment.org/](http://www.enlightenment.org/))   as  your  window  manager  (or
              another compliant window manager...I have been told that Window&#8208;
              Maker  works  also),  you  will need to use the Esetroot program
              (found in the utils/ directory)  to  set  your  root  background
              image.
It doesn't sound to me like you ever see your icons, but some of the screenshots appear to have them still. Is there anyway to still be able to use your desktop? (Other than minimizing Eterm or resizing/positioning it so it only covers part of the screen)

Sorry if someone already mentioned this.

---

### Post by jerome bettis on 2005-08-17
wtf is going on here?  it starts up but it's not transparent, it has a different background everytime.  i've played with the order of things, tried adding a program in the middle but nothing works.

has anybody figured this out?????

---

### Post by jerome bettis on 2005-08-17
ok i figured it out.

if you're having problems with the background being random and not transparent, paste this into a shell script

#!/bin/sh
sleep 10 && Eterm  -x -0 --trans --scrollbar=off --buttonbar 0 --geometry 212x57+0+24 --font-fx none -f white

change the geometry stuff for you're screen of course. i put that in ~/bin/eterm and in the sessions thing i start devilspie at 50, and my eterm script at 55. works great, exactly what i wanted.

---

### Post by chaumurky on 2005-08-17
[QUOTE=skyboy]Worked great for me on KDE 3.4.1
great Howto[/QUOTE]
 How does one set the start order in KDE?

---

### Post by arnieboy on 2005-08-17
[QUOTE=jerome bettis]ok i figured it out.

if you're having problems with the background being random and not transparent, paste this into a shell script

#!/bin/sh
sleep 10 && Eterm  -x -0 --trans --scrollbar=off --buttonbar 0 --geometry 212x57+0+24 --font-fx none -f white

change the geometry stuff for you're screen of course. i put that in ~/bin/eterm and in the sessions thing i start devilspie at 50, and my eterm script at 55. works great, exactly what i wanted.[/QUOTE]
solved an identical problem in my case too! cheers dude!!

---

### Post by jerome bettis on 2005-08-17
you're welcome, glad it helped.

now the only thing that is still bugging me about this, is how it goes away with the show desktop button.  somebody has to know how to fix that.  is there a way to have a window be fixed so it can't be moved, resized, minimized etc.  if that's possible the show desktop button shouldn't have any effect on it.  if not, i might look at the code for that button and hack it so it doesn't affect any Eterm windows.

any ideas?

---

### Post by arnieboy on 2005-08-18
[QUOTE=jerome bettis]you're welcome, glad it helped.

now the only thing that is still bugging me about this, is how it goes away with the show desktop button.  somebody has to know how to fix that.  is there a way to have a window be fixed so it can't be moved, resized, minimized etc.  if that's possible the show desktop button shouldn't have any effect on it.  if not, i might look at the code for that button and hack it so it doesn't affect any Eterm windows.

any ideas?[/QUOTE]
not just "show desktop" but alt-F4 (if thats ur shortcut for closing windows) will also close the eterm window if thats in focus. I researched a lot yesterday but could not find a possible hack.. for one thing therez no option in devilspie or eterm that will let u do that. but there surely must be something... its interesting nobody ever came up with this thought earlier on any forum on the net!

---

### Post by jerome bettis on 2005-08-18
well i spent a few hours messing around (tried different window managers, etc etc etc) and it looks like the only option is to wait for devilspie to have these features. i might email the developer and request these features or ask him how i can do it. i looked at the source, and i can't figure out ow it works.

i might actually take a closer look at fluxbox.  it's old and drab but it's very customizeable and it seems to have a lot of features that i want.  getting a terminal like this on the desktop is a snap.

---

### Post by qalimas on 2005-08-21
How would one go about 'pinning' this below all windows?  I noticed when I click on the terminal it was brought to the front, which I don't want.  I want to be able to work my terminal and still ahve other windows cover it up if there are any.

---

### Post by neanderthal // anarchism on 2005-09-05
i had devilspie at 50 and eterm at 55

and i got one of eterm's backgrounds and it's not transparent

i already tried
```
#!/bin/sh
sleep 10 && Eterm -x -0 --trans --scrollbar=off --buttonbar 0 --geometry 212x57+0+24 --font-fx none -f white
``` 

and that didn't work.

---

### Post by Paulus on 2005-09-05
heres a nice command i use on my eterm, makes the brightness/contrast high or low by varying the "cmod" command, looks like HDR!

```
kstart --alldesktops --keepbelow --skippager --skiptaskbar Eterm --geometry 75x25+750+400 --trans=true --borderless --scrollbar=false --buttonbar=false -f black --cmod 400 -c white &
``` 

screeneh:
[[img]http://img23.imageshack.us/img23/1456/snapshot11et.th.jpg[/img]]("http://img23.imageshack.us/my.php?image=snapshot11et.jpg")

---

### Post by vradick on 2005-09-16
if you use this action:
```

<action name="DevilsPieActionSetWintype">
    <property name="wintype" value="DESKTOP"/>
</action>

``` 

Your terminal is in desktop, and if you just "show desktop" you see always your terminal. Try it.

I'm using a terminal such as desktop background since Devil's Pie version 0.6. This [screenshot](http://www.marsultor.com/imgs/Pantallazo-term.png)  is in Ubuntu Warthy.

I use gnome-terminal with a profile: $gnome-terminal --window-with-profile=terminal-desktop

And matcher:
```

<matcher name="DevilsPieMatcherWindowName">
    <property name="window_title" value="terminal-desktop"/>
</matcher>

```

---

### Post by mozz on 2005-09-18
Isn't the most beautiful way, but just insert some

sleep 5

in the script, so Eterm has to wait until the desktop is loaded...(sry for digging around in this old thread)

---

### Post by devilspie on 2005-09-20
[QUOTE=krusbjorn]Hey!

Here's how to get a completely transparent terminal at your desktop background, on all workspaces, without appearing in the taskbar/windows list.

[Screenshot](http://home.tiscali.se/jossehan/eterm.png) 

First off, you need **Eterm and devilspie**:

```
sudo apt-get install eterm devilspie
```

Next, we need to make a configuration file for devilspie. Copy the code below into your favorite text editor and save the file as **.devilspie.xml** (please note the dot in the beginning of the file name) in your home folder:

```
<?xml version="1.0"?>
<!DOCTYPE devilspie SYSTEM "devilspie.dtd">

<devilspie>
  <flurb name="Eterm pinned and no taskbar">
    <matchers>
       <matcher name="DevilsPieMatcherWindowName">
         <property name="application_name" value="Eterm"/>
       </matcher>
    </matchers>
<!-- The action below will pin Eterm to all workspaces-->
     <actions>
         <action name="DevilsPieActionSetWorkspace">
            <property name="pinned" value="TRUE"/>
      </action>
<!-- The action below will remove Eterm from the windows list and the Workspace Switcher (thanks Trash:)-->
      <action name="DevilsPieActionHide">
        <property name="skip_tasklist" value="TRUE"/>
        <property name="skip_pager" value="TRUE"/>
      </action>
     </actions>
</flurb>
</devilspie>
```
The above code will make devilspie tell gnome not to display Eterm in the windows list and Workspace Switcher, and to pin it to all workspaces.

Now, go to **System -> Preferences -> Sessions**. Add **devilspie** to your startup programs.

Also, you need to **add Eterm to your startup programs**. It could look something like this:
```
Eterm  -x -0 --trans --scrollbar=off --buttonbar 0 --geometry 200x60+80+40 --font-fx none -f white
```
**NOTE**: You probably need to change some of the options applied to Eterm (X and Y offset, terminal size, text colour etc). Those are the options that fit MY desktop. Do:

```
man Eterm
``` 
If you dont know what values to change.

**Dont forget** to make sure devilespie starts BEFORE Eterm on bootup.

**ALSO NOTE**: As long as devilespie is running, it will apply its setting to Eterm whenever you launch it, meaning you wont be able to use Eterm "normally" (in a window etc)


This is my first How-To, so be easy on me if there are any errors. And sorry if my english hardly is understandable ;)

Good luck!
 -Johannes[/QUOTE]
 Hello my friend i use devilspie on Gnome,but i want to use devilspien on fluxbox to! Can you please help me???

---

### Post by krusbjorn on 2005-09-20
[QUOTE=devilspie]Hello my friend i use devilspie on Gnome,but i want to use devilspien on fluxbox to! Can you please help me???[/QUOTE]

As far as i know, devilspie is for metacity, and doesnt work in fluxbox (?)

---

### Post by ubuntonista on 2005-09-21
This does not work with the current version of devilspie in hoary - dont even try :)

---

### Post by hippyjim on 2005-09-21
[QUOTE=chaumurky]How does one set the start order in KDE?[/QUOTE]

A problem I had too! Go take a look at this great howto: [http://wiki.chem.indiana.edu/168.html](http://wiki.chem.indiana.edu/168.html) 

Man I love this effect. If only I could get the eterm to always be underneath other windows - and for my desktop icons not to wander into the eterm area and vanish!

I guess I'll just have to be a bit more tidy about where I put things.  :roll:

---

### Post by aran384 on 2005-09-24
with --trans on my eterm is transpacent i have to ctrl + right click and toggle it.....!!! 

any thoughts

---

### Post by jerome bettis on 2005-09-25
[QUOTE=devilspie]Hello my friend i use devilspie on Gnome,but i want to use devilspien on fluxbox to! Can you please help me???[/QUOTE]
 yes devilspie doesn't work in fluxbox but wmctrl does. 

i use aterm with wmctrl on fluxbox and it works perfectly.  i have a bash script that just starts the aterm and calls a python script that uses the output from wmctrl to hide it nicely.  it's a bit of a hack but it works great for me.

```
#!/bin/bash
#/usr/bin/transAterm
aterm -title a -sl 3000 -tr +sb -sr -sk -bg black -fg white -fade 90 -bl -fn -*-courier-*-r-*-*-17-*-*-*-*-*-*-* -g 102x48+2+2 & > /dev/null 2>&1
sleep 3   # give it time to load, 1 or 2 should work but 3 is better
/usr/bin/hideAterm.py > /dev/null 2>&1   # call script to hide it
```

```
#!/usr/bin/env python
# /usr/bin/hideAterm.py

import os
x = os.popen("wmctrl -p -l").readlines()
for i in x:
		if int(i[14]) == 0:  # assuming aterm is the only window that doesn't give a correct 
			    os.popen("wmctrl -i -R " + i[0:10] + " -b toggle,skip_taskbar,skip_pager")
```

in the first script you'll want to change the font / geometry flags to your liking.  i have this start up with fluxbox because the magic behind the second script depends on a miscommunication between aterm and the window manager.   (aterm doesnt support the pid thing and just says 0, whereas every other window i've seen has a real number).  if you have a bunch of windows open when you try to start this it might hide some of them too.  let me know if it does and i'll try to figure something else out, i've been thinking about that ...

---

### Post by ghostintheshell on 2005-10-31
since the 0.13+ version of devilspie, the xml syntax was replaced by the "s-expressions" syntax.

here's the conversion of my *~/.devilspie.xml *file:

- create a *.devilspie* directory in your home folder
```
mkdir ~/.devilspie
``` 

_for eterm:_
- create a *eterm.ds* file in the *~/.devilspie* folder and put this in:
```
(if (is (application_name) "Eterm") (begin skip_tasklist skip_pager pin below))
``` 

_for thunderbird (just FYI):_
- create a *thunderbird.ds* file in the *~/.devilspie* folder and put this in:
```
(if (is (application_name) "mozilla-thunderbird-bin") (begin geometry "+0+0" set_workspace 2))
``` 

restart devilspie with the -a option:
```
killall devilspie
devilspie -a &
``` 

all available actions are listed in the */src/parser.c* file available in the in the *devilspie-0.1x.tar.gz* archive.

enjoy.

---

### Post by korupt on 2006-01-08
found a good wiki page that has some great examples of s-expressions ....
[http://wiki.foosel.net/linux/devilspie](http://wiki.foosel.net/linux/devilspie)

here is the s-expression I am using for transparent terminal (I am using gnome-terminal and not Eterm)

```
(if
    (matches (application_name) "^tterm")
    (begin
        (undecorate)
        (geometry "602x236+416+500")
        (below)
        (skip_pager)
        (skip_tasklist)
    )
)
```

```
gnome-terminal --disable-factory --window-with-profile=tterm --name=tterm --geometry=100x18
```

Edit: who needs AllTerm??.... the above config does the same thing but without the systray icon!! (the order of functions matters, you must call undecorate directly followed by the geometry command or it doesn't work (I smell bug report))


Screenie:
[IMG]http://www.korupt.net/images/deskshot200601081632.png[/IMG]

---

### Post by christopher.pascual on 2006-01-31
anyone have any ideas on how this might be accomplished through Xubuntu?

TIA

---

### Post by nrwilk on 2006-02-04
Thank you! this is great!

---

### Post by nrwilk on 2006-02-05
Well, now I've a question.

Is it possible to make it so the the eterm window is ALWAYS the very bottom window?

I don't like that it can be above other windows.

This will make it perfect!

---

### Post by Maelgwyn on 2006-03-25
Is there a way to get this to work in Dapper?

'cause System->Preferences->Sessions doesn't give the option to give a number to set priority at startup like Breezy did...

Here's a screenshot to show what happens! I can't even click in the terminal to type in exit & get rid of it, nor does the "show desktop" button work...

[IMG]http://nikharris.googlepages.com/Screenshot.png.jpg[/IMG]

---

### Post by sYs^ on 2006-03-26
When I start eterm it writes: "Eterm:  Warning:  Window Manager does not support MWM hints.  Bypassing window manager control for borderless window."

And it stays on top, if I remove '-x' it stays on bottom but it has borders. :\

[http://ubuntuforums.org/showthread.php?t=150277](http://ubuntuforums.org/showthread.php?t=150277)

---

### Post by nexus_6 on 2006-04-24
hi!

i would also suggest adding the following action for the terminal always to stay in the background: 

```
                        <action name="DevilsPieActionLayer">
                                <property name="above" value="FALSE"/>
                        </action>

```

greetings
martin

---

### Post by Toky on 2006-06-06
I got the transparency and the right position (finaly) but still appearing on the taskbar... what could be wrong???
My devilspie.xml:
```
<?xml version="1.0"?>
<!DOCTYPE devilspie SYSTEM "devilspie.dtd">
<devilspie>
	
<flurb name="Eterm pinned and no taskbar">
    <matchers>
         <matcher name="DevilsPieMatcherWindowName">
         <property name="application_name" value="Eterm"/>
         </matcher>
    </matchers>
<!-- The action below will pin Eterm to all workspaces-->
     <actions>
         <action name="DevilsPieActionSetWorkspace">
            <property name="pinned" value="TRUE"/>
      </action>
	<action name="DevilsPieActionLayer">
        <property name="above" value="FALSE"/>
      </action>
<!-- The action below will remove Eterm from the windows list and the Workspace Switcher (thanks Trash:)-->
      <action name="DevilsPieActionHide">
        <property name="skip_tasklist" value="TRUE"/>
        <property name="skip_pager" value="TRUE"/>
      </action>
     </actions>
</flurb>

</devilspie>
```


[QUOTE=nexus_6]hi!

i would also suggest adding the following action for the terminal always to stay in the background: 

```
                        <action name="DevilsPieActionLayer">
                                <property name="above" value="FALSE"/>
                        </action>

```

greetings
martin[/QUOTE]
Its not working for me...
I'm using Dapper, any ideas on how to set it to the background (PERMANENTLY)?

---

### Post by hippyjim on 2006-06-06
Me too. I can get it looking right, but only if I launch eterm using a konsole!

I can't figure out how to make it start automatically, or how to remove it from the taskbar, and how to stop the eterm being minimised when I "show desktop".

I've got the .devilspie.xml from the original howto, plus the .ds file from ghostintheshell's post.

Has anyone got this going in Kubuntu Dapper? I soo miss my terminal! :(

---

### Post by mozz on 2006-07-27
nevermind

---

### Post by lapsey on 2006-10-20
you can get this working in **icewm:**

file:    ~/.icewm/winoptions
```
Eterm.layer: Desktop
Eterm.allWorkspaces: 1
Eterm.ignoreWinList: 1
Eterm.ignoreTaskBar: 1
Eterm.ignoreQuickSwitch: 1
Eterm.fullKeys: 1
```

unfortunately this would mean all eterm windows get pinned in the same way.. (you can do this with practically any app, just use 'xprop |grep WM_CLASS' to ID the name of the window it lets you click, which in this case is Eterm.)

I simply launch using    'Eterm --theme themename --geometry 80x42+5+5'

and there you go. far more elegant than devilspie IMO :)

---

### Post by Kung! on 2006-10-26
Okay, I'm sure I'm missing something obvious, but I must be missing how to adjust the Y offset in the man eterm command.  I've done what you said and it looks GREAT....all I need is for the terminaly to actually stretch all the way up to the bottom of the 'task bar' (or whatever it's called).  Right now it's about an 1/8th of an inch short, and I'm not sure how to adjust.

---

### Post by jackyyll on 2006-10-27
Okay, so i have eterm and devilspie. When i try to run devilspie in the terminal it gives me an error (devilspie:5971): Wnck-WARNING **: Property _NET_STARTUP_ID contained invalid UTF-8 

Using the eterm.ds file.

Also i'm using edgy and i dont know how to set the priority of startup apps.

---

### Post by chunger on 2007-01-29
> **jackyyll said:**
> Okay, so i have eterm and devilspie. When i try to run devilspie in the terminal it gives me an error (devilspie:5971): Wnck-WARNING **: Property _NET_STARTUP_ID contained invalid UTF-8 

Using the eterm.ds file.

Also i'm using edgy and i dont know how to set the priority of startup apps.

I've also got the same error, using the s-expressions eterm.ds file.  Devilspie seems to load and work correctly with other *.ds files that I've created.  The eterm.ds file contains:

(if (is (application_name) "Eterm") (begin skip_tasklist skip_pager pin below))

After devilspie is loaded, and I type in Eterm in a terminal, I get the error: "Wnck-WARNING **: Property _NET_STARTUP_ID contained invalid UTF-8"  and Eterm just starts up normally as if devilspie wasn't running.  

Anyone have any ideas?

Thanks

---

### Post by chunger on 2007-02-04
> **chunger said:**
> I've also got the same error, using the s-expressions eterm.ds file.  Devilspie seems to load and work correctly with other *.ds files that I've created.  The eterm.ds file contains:

(if (is (application_name) "Eterm") (begin skip_tasklist skip_pager pin below))

After devilspie is loaded, and I type in Eterm in a terminal, I get the error: "Wnck-WARNING **: Property _NET_STARTUP_ID contained invalid UTF-8"  and Eterm just starts up normally as if devilspie wasn't running.  

Anyone have any ideas?

Thanks

Just in case anyone is having the same problem, I ended up using the gnome-terminal instead of Eterm.  I've found bits and pieces on creating a *.ds file and here is what I got that worked as far creating a background terminal using devilspie s-expressions.  Here is my *.ds file contents...
> (if
        (matches (window_name) "NAME OF YOUR TERMINAL WINDOW PROFILE")
        (begin
                (below)
                (undecorate)
		(pin)
                (skip_pager)
                (skip_tasklist)
                (wintype "utility")
                (geometry "+0+0")
                (geometry "665x1150")
        )
)


This opens terminal on the left side of my screen pining it on all desktops, and leaving it in the background.  *note that my screen resolution is 1920x1200, so you will have to play around with the geometry #s to get something that looks right for your resolution (the "665x1150" line).  

Just create a gnome-terminal profile that is fully transparent with no menus or scroll bar and put the name of that profile in the *.ds file where it says so.  

As long as you got devilspie -a  in your startup, the dekstop terminal should show up upon restarting X.  

Hope this helps.

---

### Post by c-breakdown on 2007-03-31
I can't seem to get around the problem of Eterm loading before my background does resulting in it using it's default background.  Is there any tricks I can use to fix this?

---

### Post by Catsworth on 2007-05-01
This is working beautifully, thanks.

The only problem I have is that it's still visible on the program bar at the bottom of my screen, any thoughts on how I can get rid of it?

Thanks again.

---

### Post by kdt2007 on 2007-05-01
Followed the guide by Krusbjorn posted here, but after the reboot all my windows have lost their taskbars and the close button. I can't even move any of them. My show desktop button is also giving an error "your window manager does not support the show desktop button". I've tried uninstalling devilspie and Eterm and disabling the running services then saving the session, but the problem still remains. Does anyone here know how to fix this?  Just got everything configured the way I want and would hate to have to reinstall everything.
Cheers

---

### Post by kdt2007 on 2007-05-02
finally got this fixed. if anyone has the same problem this link shows some solutions [http://ubuntuforums.org/showthread.php?t=406225&page=2](http://ubuntuforums.org/showthread.php?t=406225&page=2)
Renaming the session file to session.old under the /.gnome2 folder worked for me :)

---

### Post by dbkungfu on 2009-07-31
> **spacemonkey said:**
> Does anyone know how to eliminate the drop shadow on Eterm when using drop shadows with xcompmgr?

hi
Tried setting up the following, it work for me

in xompmgr goto the window decoration 

in shadow window option - replace "any" with "(any) & !(class=Eterm)" :D

---

