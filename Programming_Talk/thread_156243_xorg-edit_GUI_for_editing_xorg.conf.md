---
title: "xorg-edit: GUI for editing xorg.conf"
date: 2006-04-06
forum: Programming Talk
---

### Post by dee.dw on 2006-04-06
Hello,

because there were several biddings about a better way to edit the xorg.conf in the German Ubuntu Forum ([Link](http://forum.ubuntuusers.de/topic/26538/)) I write a little GUI to edit the xorg.conf.

- [Project Page](http://www.deesaster.org/progxorg.php)

 - [Download-Page](http://sourceforge.net/projects/xorg-edit)

 - [Repository for Deb Package](http://www.geole.info/index.php?id=1&l=1)

Greetings, Dee
I use wxWidgets to create the GUI, so you need libwxgtk2.6-0 to start it.

I would be very happy if there is someone who would like to test it and post his opinion.

Greetings, Dee

---

### Post by oldmanstan on 2006-04-06
that looks pretty sweet!

---

### Post by dabear on 2006-04-06
Dapper user here, what are the dependencies? There's a wxwidgets dependency I can' figure out, 
> 
bjorninge@LappyDapper:~/Desktop$ ./xorg-edit
./xorg-edit: error while loading shared libraries: libwx_gtk-2.4.so.1: cannot open shared object file: No such file or directory
bjorninge@LappyDapper:~/Desktop$



---

### Post by dee.dw on 2006-04-07
@oldmanstan: Thanks! :)

[QUOTE=dabear]Dapper user here, what are the dependencies? There's a wxwidgets dependency I can' figure out,[/QUOTE]

Do you have **libwxgtk2.4-1** installed? If so, check if there is some file /usr/lib/libwx_gtk-2.4.so.1. 

Greetings, Dee

---

### Post by dee.dw on 2006-04-11
So, there is a new version and I use wx2.6 now. So you need libwxgtk-2.6-0.

Greetings, Dee

---

### Post by adamkane on 2006-04-11
Thank you for the valuable work.

 I use an ATI Radeon 7200. I had PageFlip enabled, and had to manually disable it to load xorg-edit.

> 
Option        "EnablePageFlip"     "true


I would like to see some configuration options or basic help menus.

---

### Post by dee.dw on 2006-04-11
[QUOTE=adamkane]Thank you for the valuable work.
 I use an ATI Radeon 7200. I had PageFlip enabled, and had to manually disable it to load xorg-edit.
[/QUOTE]
Is the option line correct that you have posted? If so, there is a " missing at the end. My tool don't recognize the options itself but they must be in the format
```
Option "name" "value"
``` or only ```
Option "name"
```

If the error still exists, please post (or mail me) your xorg.conf, so that can I take a look at this.

> I would like to see some configuration options or basic help menus.

This is the next step! I want to create some XML-files where all options and possible values are listed so taht the user can select from a drop down list and can do nothing wrong while editing.

Thanks for testing, :)
Dee

---

### Post by motin on 2006-04-16
[QUOTE=dee.dw]Hello,

because there were several biddings about a better way to edit the xorg.conf in the German Ubuntu Forum ([Link](http://forum.ubuntuusers.de/topic/26538/)) I write a little GUI to edit the xorg.conf.

- [Project Page](http://www.cyskat.de/dee/progxorg.htm)

I use wxWidgets to create the GUI, so you need libwxgtk2.6-0 to start it.

I would be very happy if there is someone who would like to test it and post his opinion.

Greetings, Dee[/QUOTE]

Wonderful!

I will NEVER go back to edit xorg.conf manually again (if I screw something up, I'll probably restore the backup and start gnome again).

Could you get this into the debian repositories and eventually part of the tools under System -> Administration in Gnome? Definitely belongs there, under "Advanced graphics options" or similar. 

Suggestions:
- Auto-backup of xorg.conf when starting app (in ~/.xorg-edit/backups/ or similar)
- Possibility to choose enabled/disabled for an option
- Some general info about configuring X, like that sudo dpkg-reconfigure -phigh xserver-xorg will rebuild it if something screws up

This is certainly THE step for debian users to be able to skip the tedious manual xorg.conf-editing. Hopefully, the auto-configure done at installation will be enough for most people, thus never have to edit xorg.conf with this app, but whenever xgl, tv-out and dual monitor support is not enabled by default, this app helps a lot!

Thanks!

---

### Post by motin on 2006-04-16
You might want to look at [http://www.ubuntuforums.org/showthread.php?p=926906](http://www.ubuntuforums.org/showthread.php?p=926906), a thread where your tool is discussed amongst other things.

---

### Post by dee.dw on 2006-04-16
New version...

v06.04.16:
- Bugfix: many, many... most are gone with the old design
- Bugfix: save status flag is set when adding or deleting elements
- Design: redesign of elements, less buttons
- Design: current config file name is shown in frame bar
- Feature: backup files will be saved with date and time
- Feature: new menu entrys for closing current config and creating empty config file
- Feature: maximum of screens and input devices in server layout are recognized by available devices
- Feature: question if some entries should be deleted
- Internal: deleted menu entry for load backup file and load standard xorg.conf
- Internal: more integrity checks (e.g. empty fields)
- Internal: disable some integrity checks while reading config file,
	    so it is possible to load a misconfigured file and "repair" it

Greetings, Dee

---

### Post by dee.dw on 2006-04-16
@motin: Thanks for testing and that you find the tool useful...

> Could you get this into the debian repositories and eventually part of the tools under System -> Administration in Gnome? Definitely belongs there, under "Advanced graphics options" or similar. I don't know if this becomes part of the repos so fast. The tool isn't a month old! ... And I don't know how to get it there... :) Same with the menu entries...

Now to your suggestions...
> Auto-backup of xorg.conf when starting app (in ~/.xorg-edit/backups/ or similar)I don't think that it is a good idea to store a backup everytime the tool starts... Because why should I create a backup if the user do not want to save his changes? I think it's better to create a backup before saving. But i could backup files where the original is located and the same backup in the user folder. That would be no problem!

> Possibility to choose enabled/disabled for an optionI have this in mind for further releases. Unfortunately there are such a amount of options that I don't know where to start at all. I think you especially mean the device options, don't you?

> Some general info about configuring X, like that sudo dpkg-reconfigure -phigh xserver-xorg will rebuild it if something screws up Hm, what to do you mean exactly? I could mention this in the warning at the bottom of the tool.

And thanks for mentioning the other thread...

Greetings, Dee

---

### Post by gant1979 on 2006-04-16
I download it from the "Project Page", but it is in German although the screenshots display the program with English language...

---

### Post by motin on 2006-04-16
[QUOTE=dee.dw]I don't know if this becomes part of the repos so fast. The tool isn't a month old! ... And I don't know how to get it there... :) Same with the menu entries...[/QUOTE]

Try to get hold of those who knows about this. Your tool really deserves a permanent place in Ubuntu. :)

[QUOTE=dee.dw]I don't think that it is a good idea to store a backup everytime the tool starts... Because why should I create a backup if the user do not want to save his changes? I think it's better to create a backup before saving. But i could backup files where the original is located and the same backup in the user folder. That would be no problem![/QUOTE]

Of course it would be better for auto-backups only when saving. You are so correct. But auto-backup in general is important when creating a GUI that modifies such an important file. 

[QUOTE=dee.dw]I have this in mind for further releases. Unfortunately there are such a amount of options that I don't know where to start at all. I think you especially mean the device options, don't you?[/QUOTE]

I meant simply to instead of having to delete an existing option, one should be able to uncheck the "Enabled" checkbox, and thus have that line commented in the generated file.  

[QUOTE=dee.dw]Hm, what to do you mean exactly? I could mention this in the warning at the bottom of the tool.[/QUOTE]

Well, maybe more a warning in the bottom, about the general level of caution that should be taken when editing xorg.conf in any way, as one could end up without menus, mouse, nothing (in beginner's talk) together with a short instruction (maybe with a proposal of having the user write them down...) of how to easily get X up and running again if something fails. (sudo dpkg-reconfigure -phigh xserver-xorg or instructions/script of how to restore an xorg-edit backup together with the commands to start up gnome.)

Cheers!

---

### Post by motin on 2006-04-16
Just tried the newer version. Built 18:46 :)

I liked the old interface, although it must have been confusing for many, so this is better. 

I'll test it more and return with feedback. 

Great job!

---

### Post by dee.dw on 2006-04-16
[QUOTE=gant1979]I download it from the "Project Page", but it is in German although the screenshots display the program with English language...[/QUOTE]
Then you have the German locales installed! So just delete de de_DE-folder and the tool is in English! I will add en_EN in the next update...

> I meant simply to instead of having to delete an existing option, one should be able to uncheck the "Enabled" checkbox, and thus have that line commented in the generated file.Then I must parse all comments in the xorg.conf and check if there are some options behind a #. The real "problem" is another checkbox - and another redesign. The simpelst thing of all: If you have a option you do not need, just mark it with "no" instead of "yes". :)

I will think about a "bigger" warning at the start of the tool (maybe with a checkbox to see this annoying message everytime. :))

Greetings, Dee

---

### Post by motin on 2006-04-16
[QUOTE=dee.dw]Then I must parse all comments in the xorg.conf and check if there are some options behind a #. The real "problem" is another checkbox - and another redesign. The simpelst thing of all: If you have a option you do not need, just mark it with "no" instead of "yes". :)[/QUOTE]

I guess I was too late. Your finished redesign kind of surprised me, coming just an hour after I found your app :). 

About the parsing: Just comment it in a unique way, like #{xorg-edit disabled option}## Option "Aight" "Yes" or similar. 

And btw, it would be great to be able to include comments in xorg.conf without it being stripped away by your nice app :)

[QUOTE=dee.dw]I will think about a "bigger" warning at the start of the tool (maybe with a checkbox to see this annoying message everytime. :))[/QUOTE]

Great!

Cheers!

---

### Post by dee.dw on 2006-04-17
[QUOTE=motin]I guess I was too late. Your finished redesign kind of surprised me, coming just an hour after I found your app :).[/quote] Pure luck... A user in the German forum has said that there are too much buttons a week ago. And I agreed so I redesigned it and finished it yesterday... :)

> Just comment it in a unique way, like #{xorg-edit disabled option}## Option "Aight" "Yes" or similar. I will think about it... 

> And btw, it would be great to be able to include comments in xorg.conf without it being stripped away by your nice app :) In such a case it would be nice if you say how I could integrate it in the design... I mean a user comment to every option would be too much, the GUI will become to fat. Of course it's possible, but you must find a way between user freedom and GUI complexity...

I have in mind that before the tool before saving the file shows in a extra text box the whole file as it should be written and the user can add comments there... But I must think about the how!

I'm not very happy with the current comment state too... :(

Greetings, Dee

---

### Post by motin on 2006-04-17
About comments: People may have explanations and or commented sections that they want to keep for later. Another type of commenting is temporarily disabling options for diagnosis. Some of these are numeric and can thus not be disabled by a "no" or similar. 

The latter type should be rather easy to maintain. Only allow it for Options, and comment then in a unique way. In the gui, it could be integrated by a third option in the menu: Add option, Delete current option, Disable current option. Then the option would be commented out in the unique way and it's title would change to "Option-name (temporarily disabled)" or similar. Of course the menu item would be Enable current option. 

The first type is trickier, but could be accomplished by :

1. When parsing initially, let all found comments group in the end under a section "Comments from before xorg-editing", and no connection with this in the gui. At least they wont disappear completely. 

2. Implementing support for one comment for each montior, inputdevice, device, screen, serverlayout, serverflag, extension, module, font path, dri and option have one comment each. Not necessarily for users comment only (there wouldnt have to be any option in the gui to be able to edit these comments) but it would be a place to be able to input information about the current instance for the inexperienced. If user-editing should be available, then maybe a subtle button with an "i" on it could bring up not only the information about the option or whatever, but also allow for editing of it.

Cheers!

---

### Post by dee.dw on 2006-04-29
new version...

v06.04.29:

- Bugfix: input device options in server layout will be stored correctly
- Bugfix: server layouts will be stored correctly (had double entries before)
- Bugfix: language file will be found if the tool is started from another directory
- Bugfix: file could be closed and program quit even if there are some wrong entries 
- Bugfix: saved status is set to false if some options are added
- Bugfix: options in Screen Section will be recognized
- Design: separated Input Devices and Monitors from Device tab
- Feature: preview of file possible with "Extras -> Show" or key F5
- Feature: language can be changed in application between English and German
- Feature: added rgb and module paths in files section
- Feature: added viewport for display in screen section
- Feature: files paths, server flags, monitor modelines extensions, modules and all options can be de/activated (resp. un/commented)
- Feature: commented options will be loaded and set as inactive
- Internal: delete all accept functions and check text fields directly for changes
- Internal: delete class for modelines
- Internal: create single class for options

Link: [http://www.cyskat.de/dee/progxorg.htm](http://www.cyskat.de/dee/progxorg.htm)

@motin: As you see I have integrate the de/activate-function which let the user comment options and several other things.
In the next version I will create some fields in the GUI for adding comments to all sections and some options.

I have also noted your other ideas on my todo-list... :)

Greetings, Dee

---

### Post by motin on 2006-05-01
[QUOTE=dee.dw]@motin: As you see I have integrate the de/activate-function which let the user comment options and several other things.
In the next version I will create some fields in the GUI for adding comments to all sections and some options.

I have also noted your other ideas on my todo-list... :)

Greetings, Dee[/QUOTE]

Nice Dee!  Your new version will certainly help in the quest for S-Video output enabling for i915. 

I will come back after I have tried it out. Do not have time to do it directly. 

Cheers!

---

### Post by dee.dw on 2006-05-26
Hm, you never come back... I hope my tool does not let you PC explode.... ;)

New version v06.05.25:

- Bugfix: device options will be saved now
- Bugfix: "save file as" will create backup copy with date and time
- Feature: big warning message at start of the tool
- Internal: divided current file in filename and directory

Greetings, Dee

---

### Post by henriquemaia on 2006-05-26
[quote=dee.dw]Hm, you never come back... I hope my tool does not let you PC explode.... ;)

New version v06.05.25:

- Bugfix: device options will be saved now
- Bugfix: "save file as" will create backup copy with date and time
- Feature: big warning message at start of the tool
- Internal: divided current file in filename and directory

Greetings, Dee[/quote] 
Hi, Neat Idea. Thanks for making it true.

I get this error while running it:

```
 sudo ./xorg-edit
./xorg-edit: error while loading shared libraries: libwx_gtk2u_xrc-2.6.so.0: cannot open shared object file: No such file or directory
```

I have libwxgtk2.6-0 installed. Is it because I'm running Dapper?

---

### Post by dee.dw on 2006-05-26
As you can see [here](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libwx_gtk2u_xrc-2.6.so.0&searchmode=searchfiles&case=insensitive&version=dapper&arch=i386) "libwx_gtk2u_xrc-2.6.so.0" is a file in "libwxgtk2.6-0". Please reinstall the package.

If you use Synaptics you can check the installed files of this package there and take a look if this single file is missing.... It may be a bug in Dapper, but I found several people who could use this tool in Dapper.

Greetings, Dee

---

### Post by henriquemaia on 2006-05-26
[quote=dee.dw]As you can see [here]("http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libwx_gtk2u_xrc-2.6.so.0&searchmode=searchfiles&case=insensitive&version=dapper&arch=i386") "libwx_gtk2u_xrc-2.6.so.0" is a file in "libwxgtk2.6-0". Please reinstall the package.

If you use Synaptics you can check the installed files of this package there and take a look if this single file is missing.... It may be a bug in Dapper, but I found several people who could use this tool in Dapper.

Greetings, Dee[/quote]

Hi,

/usr/lib/libwx_gtk2u_xrc-2.6.so.0 is indeed installed, by I still get the error after reinstalling the package. Maybe a Dapper bug.

---

### Post by dee.dw on 2006-05-26
This is really strange... Have you check the /usr/lib folder if the library really is there or did you only check the package files in Synaptics?

Otherwise I don't have a clue because the error says the library is missing but when it is installed I don't know what to do.

Hm, could you post the out of "ls -al /usr/lib | grep libwx_gtk2u_xrc"?

Greetings, Dee

---

### Post by henriquemaia on 2006-05-26
[quote=dee.dw]This is really strange... Have you check the /usr/lib folder if the library really is there or did you only check the package files in Synaptics?

Otherwise I don't have a clue because the error says the library is missing but when it is installed I don't know what to do.

Hm, could you post the out of "ls -al /usr/lib | grep libwx_gtk2u_xrc"?

Greetings, Dee[/quote]
```

ls -al /usr/lib | grep libwx_gtk2u_xrc
lrwxrwxrwx   1 root root       28 2006-05-26 13:15 libwx_gtk2u_xrc-2.6.so.0 -> libwx_gtk2u_xrc-2.6.so.0.0.0
-rw-r--r--   1 root root   566960 2005-11-17 19:21 libwx_gtk2u_xrc-2.6.so.0.0.0
```

Is this because I'm running Dapper 64bit version?

---

### Post by dee.dw on 2006-05-26
The link seems okay, but it is possible that the i386-precompiled-version doesn't run on a  64bit machine. Maybe you could download the source from my website and just type "make" in the terminal in the "source" folder to compile it on your machine. I think it should run then... You will need libwxgtk2.6-dev for compiling!

Greetings, Dee

---

### Post by henriquemaia on 2006-05-26
[quote=dee.dw]The link seems okay, but it is possible that the i386-precompiled-version doesn't run on a  64bit machine. Maybe you could download the source from my website and just type "make" in the terminal in the "source" folder to compile it on your machine. I think it should run then... You will need libwxgtk2.6-dev for compiling!

Greetings, Dee[/quote]

Ok. I compiled it. It works fine.

As for the application in itself, it's great. For a newbie, this is a MUCH nicer approach. Is there any plans this in Edgy Eft as standard xorg.conf editor?

---

### Post by dee.dw on 2006-05-26
[QUOTE=henriquemaia]Ok. I compiled it. It works fine.[/quote] Great... :)

> Is there any plans this in Edgy Eft as standard xorg.conf editor?
Some other users also mentioned this and it exist a launchpad request for such a tool. Unfortunately I don't understand how to edit or post a message there so that the people see that there is such a tool.

I wait for someone who helps me with the distribution... :) Most project sites like Freshmeat or SourceForge are to complex in my opinion.... I have an account there but have not the time to insert xorg-edit there. :(

Greetings, Dee

---

### Post by henriquemaia on 2006-05-26
[quote=dee.dw]Great... :)


Some other users also mentioned this and it exist a launchpad request for such a tool. Unfortunately I don't understand how to edit or post a message there so that the people see that there is such a tool.

I wait for someone who helps me with the distribution... :) Most project sites like Freshmeat or SourceForge are to complex in my opinion.... I have an account there but have not the time to insert xorg-edit there. :(

Greetings, Dee[/quote]

But have you shared you views/program with the Ubuntu developers?

---

### Post by motin on 2006-05-26
[QUOTE=dee.dw]Hm, you never come back... I hope my tool does not let you PC explode.... ;)

New version v06.05.25:

- Bugfix: device options will be saved now
- Bugfix: "save file as" will create backup copy with date and time
- Feature: big warning message at start of the tool
- Internal: divided current file in filename and directory

Greetings, Dee[/QUOTE]

Terribly sorry for not returning. A journey to South America (3 months...) is coming up and I've have had to switch S-Video efforts to actually finish my commercial projects before the trip... 

I am very glad that you are keeping up this great effort and that you got that big fat warning at the start of the tool :), it will really save many people's frustration... 

You should definitely reply in a comment to the launchpad request, linking to this thread and your efforts. 

Also, you can use the Dapper development mailing lists ( I assume there are some...) and ask for help in distributing your efforts to the world :). IMO, you should not have to distribute it yourself, hopefully someone will help you (and thus all of us) out with it, so that you can spend some more time on the app, or in the sun, or whatever. You've done your part...

Keep up the great work! :)

Cheers!

---

### Post by dee.dw on 2006-05-26
[QUOTE=henriquemaia]But have you shared you views/program with the Ubuntu developers?[/QUOTE]

Hm, I thought Launchpad is the official way to get connected to them... What do you suggest?

Greetings, Deee

---

### Post by henriquemaia on 2006-05-26
[quote=dee.dw]Hm, I thought Launchpad is the official way to get connected to them... What do you suggest?

Greetings, Deee[/quote]

In the Ubuntu Cafe Forum, there is a thread going about suggestions to Edgy. A few people there have already suggested a tool like yours for editing xorg.conf. I posted there a link pointing to this thread, so that your tool gets some attention. I really think this can help a lot of people.

The link to the discussion:

[http://ubuntuforums.org/showthread.php?t=182127](http://ubuntuforums.org/showthread.php?t=182127)

---

### Post by dee.dw on 2006-06-02
Update v06.06.02:

- Feature: add field for virtual screen size
- Feature: add question if misconfigured file should be loaded further after read error

Download: [http://www.cyskat.de/dee/progxorg.htm](http://www.cyskat.de/dee/progxorg.htm)

Greetings, Dee

---

### Post by kripkenstein on 2006-06-06
This looks like it is getting to be a great tool. Nice work.

One question, though - I don't see license explanations anywhere (on the site or in the sources). Will this be under the GPL?

---

### Post by dee.dw on 2006-06-08
Hello,

yes, I think it's under GPL. :) I have never been concerned with this... I will add tis in the next version.

Thanks, Dee

---

### Post by munwin on 2006-06-08
Nice work.
Some suggestions - 
 What about configuring multiple monitors & video cards ?
 Detecting the currently installed hardware & drivers, and downloading / installing the proprietry ones, if needed.

Love your work.

---

### Post by dee.dw on 2006-06-11
v06.06.11:

- Leaving Beta Status ! :)

- Bugfix: Virtual Size and ViewPort will be deleted not in Display after copying
- Feature: comments in xorg.conf will be read, stored and written (but cannot be changed yet)
- Internal: add comments to every class

Download: [http://www.cyskat.de/dee/progxorg.htm](http://www.cyskat.de/dee/progxorg.htm)
-------------------

And could someone create a WikiSpecification for xorg-edit like Daniel Holbach suggested: [https://launchpad.net/distros/ubuntu/+spec/xorg-config-ui](https://launchpad.net/distros/ubuntu/+spec/xorg-config-ui)
I would do it myself but I could not log on there.... :( Thanks!

@munwin: Detecting the hardware is not that easy so I refer to xorg.conf because most users have a good configured file when they can start xorg-edit. :)
The configuration of video cards is on my todo-list... Unfortunately it's not that easy  - especially without help. :( I only have a ATI card so I could not test the options for nVidia or other cards. And I don't have another Monitor to test twinview or something like that. 

Greetings, Dee

---

### Post by dee.dw on 2006-06-13
There exists a debian package which you can install per apt-get or whatever you use: [http://www.geole.de/9.0.html](http://www.geole.de/9.0.html)

Greetings, Dee

---

### Post by WorLord on 2006-06-22
I like the way this tool is headed, but it doesn't yet seem to offer much more usefullness than raw editing of the xorg.conf file.  So far, all the tool seems to do is parse xorg.conf, and change the options that already exist there via a GUI.  Which is nice - nicer than directly editing xorg.conf itself, certainly - but it doesn't really provide many benefits outside of making the xorg.conf editing process more GUIfied.

What I'd like to know is if this tool will come complete with some of the more commonly used defauts/switches/resolutions/xorg options built-in, so that options and switches can be added without one having to have memorized them.  

For example: Currently, if you wanted to, say, add the 'Option "RenderAccel" "True"' switch, you can do that with this tool - but you have to have that option memorized, and you have to know under which section (Device?) it belongs.

Will there ever be a point where options like that will be included with the tool, so that people don't have to memorize obscure things like that in order to take advantage of X?  Will I be able to pull up this tool, click on the device tab, click on the "option" pull-down, and have RenderAccel, EnableGLXComposite (or whatever it is) VideoOverlay (GL, XV, etc), and EnableHardwareMouse there in the GUI for me to choose from and add?

---

### Post by dee.dw on 2006-06-22
> I like the way this tool is headed, Thanks! :)

> but it doesn't yet seem to offer much more usefullness than raw editing of the xorg.conf file. I don't think so... Many users often make mistakes editing this file. Of course it is possible to create a misconfigurated file with xorg-edit but the chances are smaller than with manual editing.

> Will there ever be a point where options like that will be included with the tool, so that people don't have to memorize obscure things like that in order to take advantage of X? As you can read above: Yes I have this in mind... But: It will take a lot of time and of course help of other people because I do not know any device options. Further many options depend on the graphic card and driver, so that I must separate this. If it would be this easy I would have implement it right away... ;)

So first there must a correct list with options names, option values, the place where the option belongs and under which circumstances the option can be used.

So, the tool is not finished but should provide help for new ubuntu users that may change there monitor refresh rates easy or something like this.

Greetings, Dee

---

### Post by WorLord on 2006-06-22
It seems you are actively working on this program still... if so, I can try to compile a list of options I've used in the past for X.  This laptop has an ATI card, so I have enough tools to compile a list of fglrx-specific things.  I have two nVidia-based machines at home, and a copy of the readme/appendix for the nvidia driver (which lists the extra nvidia-driver-specific options in there), and I'm more than familiar with those.

And I've just had to set up a dual-head radeon-driver setup as well, so I'm familiar with those...

Would that help?

---

### Post by dee.dw on 2006-06-23
> It seems you are actively working on this program still...Of course I do! :) The last update was a few days ago and I try to manage it to implement new ideas if I have time. (Unfortunately my job in real life and virtually do not leave much time actually.)

> I can try to compile a list of options I've used in the past for X.That would be great. For ati it would be important if I can use these option only with fglrx or even with ati or radeon-driver. Same with nv and nvidia.
So a list would really help. I think I will write them into some text files (xml), so that it's easier to add new options without changing my program. But I haven't thought about the snytax yet...

Thanks in advance! :)

Greetings, Dee

---

### Post by Dzo on 2006-06-23
Right sounds daft, manually i can (or have done this in the past without a problem) thought i'd use the gui to see what it was like but i can't find a way of doing what i need to (i think i'm just being stupid tbh! :rolleyes: )

I just need some help with what needs to be set to what within the gui.

I have a Laptop with a display of 1024x768 and a TFT External Monitor with a display of 1280x1024

I want the external TFT to clone the display of the laptop but at a resolution of 1280x1024 :)

Is this possible at the moment or do i manually edit it?

---

### Post by dee.dw on 2006-06-23
Unfortunately you are not able to do this automatically. xorg-edit only helps to edit xorg.conf to reduce typing mistakes and error. So you can use it to creat ethe necessary options aso.

The problem here is: On nVida cards I have seen that you only need some options to clone the display. On Ati cards there is not such a way, you must create a second monitor and set them both in the server layout section I think.

Greetings, Dee

---

### Post by MetalMusicAddict on 2006-07-07
This tool looks good.:) The site that is linked is in German. Could you or anyone post a link to the .deb/right repo? Thanx.

---

### Post by dee.dw on 2006-07-07
Hello,

I have add a repository on my homepage. Just add> deb [http://ubuntu.geole.de/](http://ubuntu.geole.de/) dapper universe or > deb [http://ubuntu.geole.de/](http://ubuntu.geole.de/) breezy universe to your /etc/apt/sources.list and you can install xorg-edit via package management.

And you can download a debian package on [http://sourceforge.net/projects/xorg-edit/](http://sourceforge.net/projects/xorg-edit/)

Greetings, Dee

---

### Post by vek on 2006-07-08
This is a pretty useful tool.  I remember countless times I hand edited my xorg.conf file and it failed to start - because of a mistyping, bad copy/paste, missing inverted commas... that kind of syntax error.  Its not hard to find the error, but it takes time to keep restarting X until it works...

---

### Post by Somenoob on 2006-07-08
Looks indeed like a more comfortable and better way for altering the "xorg.conf" file.

---

### Post by Priyantha Bleeker on 2006-07-10
Tool looks very nice !
I've made an ebuild for Gentoo for it.
You can find it here: [http://bugs.gentoo.org/show_bug.cgi?id=139850](http://bugs.gentoo.org/show_bug.cgi?id=139850)
It works also good on Gentoo ;)
Nice stuff

An other question, is it possible to change the filename of the sourcecode tar.gz ?
Then it is an bit easier to maintain the version update's.

---

### Post by dee.dw on 2006-07-22
Thanks for this Gentoo-File. :)

What name do you need? xorg-edit-src-060611.tar.gz ? And do I need do rename the xorg-edit folder in it too?

I haven't used the version in the filename because a few weeks ago I have posted the version directly (without SorceForge) and do not want to correct the link everytime a new version apears.

Greetings, Dee

PS: Sorry for the delay but I was in holidays... :)

---

### Post by dee.dw on 2006-07-30
New version:

Update v06.07.30:

- Feature: integrated modeline generator (using gtf)
- Feature: automatical detection of DisplaySize (using xdpyinfo)
- Feature: automatical detection of monitor refresh rates (using ddcprobe)

---------------------

And I have changed the filename of the tarballs.

Greetings, Dee

---

### Post by Anduu on 2006-07-31
I need a little help....

There is someting about my xorg.conf that hangs xorg-edit.

If i create a new config via xorg-edit it works fine...however as soon as I try to save or preview my existing xorg.conf my cpu usage jumps to 100% and xorg-edit freezes.

Anyway here it is if someone cares to see...


```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option      "Buttons" "7"
	Option	    "Protocol" "ExplorerPS/2"
	Option      "ButtonMapping"         "1 2 3 7 6"
	Option	    "ZAxisMapping" "4 5"
	Option      "Resolution" "800"
#	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Insignia"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Monitor    "Insignia"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection


```

---

### Post by dee.dw on 2006-08-01
Bug is fixed! Sorry for that...

See new version at [http://sourceforge.net/projects/xorg-edit/](http://sourceforge.net/projects/xorg-edit/)
 Deb will be available during the day!

Greetings, Dee

---

### Post by Georg W. Leonhardt on 2006-08-01
The URL of the Repo geole.de and the GPG-Key changed. New URL: [www.geole.info]("http://www.geole.info")

New entry for sources.list
```
deb http://ubuntu.geole.info/ dapper universe multiverse
```
New GPG-Key
```
wget http://www.geole.info/fileadmin/data/misc/geole.info-apt-key.gpg
sudo apt-key add geole.info-apt-key.gpg
```

Greetz Georg

---

### Post by Anduu on 2006-08-01
> **dee.dw said:**
> Bug is fixed! Sorry for that...

See new version at [http://sourceforge.net/projects/xorg-edit/](http://sourceforge.net/projects/xorg-edit/)
 Deb will be available during the day!

Greetings, Dee

Great stuff...works like a charm now :KS

---

### Post by H.E. Pennypacker on 2006-08-01
I can't believe something as basic as this does not come default on all Linux distributions.  If I am not mistaken, X is used on *all* Linux distros, and there is no reason why something like Xorg-Edit (the GUI) should not be implemented by default.  

If you're worried about space issues, dump all those waste-of-space games that come with Ubuntu.  I don't know about you, but I don't even play games!

Edit: This is to the creator of this GUI...why create such an obvious warning ?  Anyone editing X should always be careful, and this GUI is not anymore dangerous than editing X manually.

---

### Post by Anduu on 2006-08-02
Oops another bug for me...Save as works fine however if I try to just Save I get:

```

Could not create copy of the file "/etc/X11/xorg.conf". Will not save file!
```

```
can't create file '/etc/X11/xorg.conf_01/08/06_10:12:40 PM' (error 2: No such file or directory)

```

A permission problem?

---

### Post by dee.dw on 2006-08-02
[quote="Anduu"]A permission problem?[/quote] Are you working as root? Otherwise you have no permission to save this file there! In the next version I will check if the user is root before starting and give a little message or something like this.

[quote="H.E. Pennypacker"]why create such an obvious warning ?[/quote] See page 1 or 2 of this thread. As a programmer of software you always should say that your program is not responsible for the result. Otherwise I think there may be people who will blame me for that!

> If I am not mistaken, X is used on all Linux distros, and there is no reason why something like Xorg-Edit (the GUI) should not be implemented by default. This is right I think I don't know either why there haven't been such a tool in Ubuntu. Suse has Sax2 which is really fine. And there are still some other tools like mine... See [http://ubuntuforums.org/showthread.php?p=1327452](http://ubuntuforums.org/showthread.php?p=1327452)

Greetings, Dee

---

### Post by Anduu on 2006-08-02
> **dee.dw said:**
> Are you working as root? Otherwise you have no permission to save this file there! In the next version I will check if the user is root before starting and give a little message or something like this.

Greetings, Dee

When I launch xorg-edit the "Enter administrative password" dialogue pops up and then accepts my password so....

---

### Post by dee.dw on 2006-08-02
Hm, strange... Choose "File -> Save as" and first save the file in your home-directory (in your own, not of root). If this works fine, try to save the file directly under /etc/X11/xorg.conf2. Then post the permissions of these files here...

Greetings, Dee

---

### Post by Anduu on 2006-08-02
> **dee.dw said:**
> Hm, strange... Choose "File -> Save as" and first save the file in your home-directory (in your own, not of root). If this works fine, try to save the file directly under /etc/X11/xorg.conf2. Then post the permissions of these files here...

Greetings, Dee

Ok both files saved fine and are owned by root with 644 permissions....:-k

---

### Post by dee.dw on 2006-08-02
Okay, so please check the permission of the /etc/X11/xorg.conf... Maybe it's only 444.

Greetings, Dee

---

### Post by Anduu on 2006-08-02
Sigh....nope it is 644 as well....sniff :(

---

### Post by Anduu on 2006-08-02
I just set permissions of my xorg.conf to 666 and it still won't save...very odd.

Edit:

Gave myself ownership of xorg.conf...still no go....waaaaaaaaaaaa!

---

### Post by dee.dw on 2006-08-02
Now it becomes really strange.... Cann you overwrite the file with a copy of the xorg.conf previously saved separately? There are only ...

One moment, man am I really dumb.... I should read the error messages better! It says that it could not create a backup of the xorg.conf. And the reason is the formatting of your date: "/etc/X11/xorg.conf_01/08/06_10:12:40 PM"

It tries to save in subfolders that don't exist!

So let me think about it... Somehow I must change the slashes to points or something like this. I will write a new version for 6.8.1 in the evening!

Greetings, Dee

---

### Post by Anduu on 2006-08-02
Doh #-o 

Strange that I am the only one it seems to be having these troubles :p

Thanks for the live support :wink:

---

### Post by dee.dw on 2006-08-02
So, I have fixed it: [http://sourceforge.net/projects/xorg-edit/](http://sourceforge.net/projects/xorg-edit/)

And even if the backup file is not created you will be asked now if you want to save the xorg.conf. If I had implemented this earlier you could have used the tool even with this error.

But next time you should first collect all errors. ;)

Greetings, Dee

---

### Post by Anduu on 2006-08-02
> **dee.dw said:**
> So, I have fixed it: [http://sourceforge.net/projects/xorg-edit/](http://sourceforge.net/projects/xorg-edit/)

And even if the backup file is not created you will be asked now if you want to save the xorg.conf. If I had implemented this earlier you could have used the tool even with this error.

But next time you should first collect all errors. ;)

Greetings, Dee

Cool 8)  

Seeing as I have installed thru synaptic I'll wait for the update from your repo :D

---

### Post by dee.dw on 2006-08-26
New version v06.08.26:

- Bugfix: unknown options will be stored correctly now in the corresponding section as comment
- Feature: modelname, vendorname and boardname are no longer unkown options but will only be add as comment
- Feature: Device, Monitor, Input Device, Screen and Server Layout can be copied now with a single click (for configuring TV-OUT maybe)
- Feature: when deleting a referenced entry user is asked if he want to delete this reference too

For all German users: I will write a tutorial the next days how to delete the unnecessary wacom-entries in Dapper and how to set up dual-monitoring with a few clicks.

Greetings, Dee

---

### Post by Miademora on 2006-09-03
> **dee.dw said:**
> 
 - [Repository for Deb Package](http://www.geole.de/9.0.html)


Great its one of the most annoying things in linux left. Ill give it a try.

However the link i quoted isnt working for me. Only leads to a site full of useless advertisements.

---

### Post by dee.dw on 2006-09-03
> However the link i quoted isnt working for me. Only leads to a site full of useless advertisements. Oh, I'm sorry... The URL has changed to [http://www.geole.info/index.php?id=1&l=1](http://www.geole.info/index.php?id=1&l=1)

Greetings, Dee

---

### Post by Darkspace on 2006-09-08
Looks interesting, I'd like to give this a go. Would I be able to use this to get my video card to output 1366x768 for me HDTV? 

If so how do I install libwxgtk2.6-0? I couldn't find it in synaptic.

---

### Post by etcpool on 2006-09-09
This should be added to the next release of ubuntu-desktop

---

### Post by SlayerMan on 2006-09-09
I fully agree to etcpool.

---

### Post by missmoondog on 2006-09-09
just happened to catch the topic of this thread on the front page. great looking tool. installed it on an old gateway with an ancient nvidia card. seems to work properly. don't think i'll install it on my other six systems though until i play with it more, which shouldn't really be necessary, should it? :p 

did subscribe to this thread though to remember it.

---

### Post by arkangel on 2006-09-09
DEUTSCHLAND LAND DER IDEEN

Gute Arbeit = Good Job

---

### Post by missmoondog on 2006-09-09
wasn't planning on getting on this computer of mine today, but wife needed to use it, so once she got off winblows, i rebooted to kubuntu. 

this tool doesn't have any effect on this system. i can change any of the numbers/settings to anything i want and there is no difference. can't even make x quit working on purpose! bummer too, as this machine won't let me set the refresh rate any lower than 85mhz and i want 75. guess i'm going to have to add the modline and then i wind up with 75 as the only refresh rate possible then.

edit:
have tried this on 2 of machines now. has no effect on either! yes, i'm saving settings and rebooting and anything else. oh well, i can live with the settings i have and editing the x11 file manually.

---

### Post by stani on 2006-09-10
Digg it to give this project the attention it deserves! 

[http://digg.com/linux_unix/Xorg_Editor_for_Ubuntu](http://digg.com/linux_unix/Xorg_Editor_for_Ubuntu)

---

### Post by dee.dw on 2006-09-30
Sorry for not posting that long but I haven't get any email notification that there are new answers... Let's see if this is just temporary...

@arkangel: Thanks for this great praise. :)

But now I need you help...

Currently I develop a file format for saving the xorg-options so that other users can create or add new options easily. I think of something like this:

1. The folder **options** holds all xorg.conf options.
2. In this folder there are other folders for each section, so **devices**, **inputdevices**, aso.
3. In each folder you find a file with the name of a driver. In devices maybe **radeon**, **fglrx**, **nvidia**, aso.
4. In these files finally the store the options. I have written an example: [http://www.ubuntuusers.de/paste/3918/?format=txt](http://www.ubuntuusers.de/paste/3918/?format=txt)

Do you think this is easy enough? If someone wants to add a new driver he can create a new file with all options. Otherwise if someone wants to add new options to a driver he only must add them to a single file.

Greetings, Dee

---

### Post by po0f on 2006-09-30
dee.dw,

I always end up using the command line for stuff like this, but this looks promising enough that I might even use it.  About the file format:  it looks good.  If this is going to be the final format for the file, I'll see if I can whip up an nVidia one for use.

---

### Post by dee.dw on 2006-09-30
That would be great, but I think you will have enough time for it, because I must do some changes in my program to the correct option type. Strings are good to use overall but not if you want to check if something is valid. ;) I have asked the question in the german board too and will post if the final design is ready...

Greetings, Dee

---

### Post by SlayerMan on 2006-10-01
@dee.dw:

Nice idea, keep up the good work

---

### Post by loko on 2006-10-02
This program is good work.

I think at this point a good documentation is needed.

Because i am not much experienced in editing xorg, so even with this program i cannot get the s-video of my notebook work.

all i want is to edit the xorg-file that the output to tv works, but even with this program i am lost.

So what about a documentation?

---

### Post by dee.dw on 2006-10-02
Hello loko,

a _real_ documentation for the program would be as long as the documentation for xorg.conf.

A much more intuitiv GUI would be great but I don't have the right ideas to build one.

For DualMonitoring (or TV-Out) I have written a short tutorial but only in German at this time. The problem is that I do not have a TV-Out to check the tutorial. It's just the way it should work...

But I think someone in this forum (in another thread) could help you with it.

Greetings, Dee

---

### Post by loko on 2006-10-02
Hello Dee,

thanks for your fast answereing.

german is my native language, so i think i will understand this tutorial well (zumindest kann ich es lesen, verstehen ist dann wieder 'ne andere sache)

Where can i found this tutorial for DualMonitoring, so i can check it for you if it works or not.

greetings

loko

---

### Post by SebMKd on 2006-10-05
Hello! Hallo!
This tool seems to be exactly what I need. I've had screen resolution issues on Dapper 6.06-1 (i386): only had one resolution available :-k 
I've tried to manually modify Xorg, but I'm a newbie to Linux and barely managed to add HorizSync and VertRefresh to the Xorg.config file. But don't ask me how!! It seems that it works. However, I'd perfer using this tool than attempting to go into xorg.conf again :???: 

One of the condition for me to use this would be to be able to install it offline! My Linux rig doesn't have internet. So I've read a lot online here and downloaded what I thought would be necessary. Could you just let me know if I've got all I need, and if my code is correct? I'd really appreciate.:biggrin: 

I've downloaded: **wxWidgets.2.6.3.tar.gz** and **libwxgtk2.6-0.tar.gz** from [http://packages.debian.org/unstable/libs/libwxgtk2.6-0](http://packages.debian.org/unstable/libs/libwxgtk2.6-0) and 
**Xorg-edit.deb** from [http://sourceforge.net/projects/xorg-edit/](http://sourceforge.net/projects/xorg-edit/)

1. I believe I need to install libwxgtk2.6-0 first( which is a .deb file compressed in libwxgtk2.6-0.tar.gz):
- Drag and drop uncompressed .deb file in '/usr/lib/'
- Open terminal and type: [FONT="Courier New"]sudo dpkg -i libwxgtk2.6-0_2.6.3.2.1.5_i386.deb[/FONT]

2. Then WxWidgets:
- Drag and drop the wxWidgets.tar file content in root directory '/'
- Open terminal and type:
[FONT="Courier New"]mkdir buildgtk
cd buildgtk
../configure --with-gtk
make
sudo make install
ldconfig[/FONT]

3. Now I should be able to Install Xorg-Edit:
- Drag and drop xorg-edit .deb file in root directory '/'
- Open terminal and type: [FONT="Courier New"] sudo dpkg -i xorg-edit_06.08.26-1_i386.deb[/FONT]

4. Then to run Xorg-Edit:
- Open terminal and type: [FONT="Courier New"]sudo ./xorg-edit[/FONT]

Many thanks!
Vielen Danke!;) 

S.

---

### Post by dee.dw on 2006-10-05
@SebMKd: Almost correct but please ignore point 2. You have already installed wxWidgets in 1. :) But please do not use some debian-packages... Take a look at [http://packages.ubuntu.com](http://packages.ubuntu.com) and download the correct one for Dapper (or Edgy).

@loko: Take a look at the UU-Wiki: [http://wiki.ubuntuusers.de/XServer_einrichten_mit_xorg-edit#Dualmonitor](http://wiki.ubuntuusers.de/XServer_einrichten_mit_xorg-edit#Dualmonitor)

Greetings, Dee

---

### Post by SebMKd on 2006-10-06
Hi Dee.Dw and thanks for the prompt answer.

- I've downloaded the following files: xorg-edit_06.08.26-1_i386.deb and libwxgtk2.6-0_2.6.1.2ubuntu2_i386.deb (one from you, the other one from the Ubuntu Package website you refered to)
- Installed the library: sudo dpkg -i libwxgtk2.6-0_2.6.1.2ubuntu2_i386.deb
- Installed Xorg-Edit: sudo dpkg -i xorg-edit_06.08.26-1_i386.deb
- Then launch Worg-Edit: sudo xorg-edit

Everything went smoothly!  =; However, now I'm facing new issues after I'm loading my Xorg.conf...

-> What is device identifier?
-> Where do I enter HorizSync and VertRefresh? (In option? under screen tab? Do I have to type in these words? Where do I enter the frequencies?)
Currently on my screen the date, ON/OFF button and trash are in the middle, instead of being to the right. So there might be something not right to my xorg.conf?!

Again, I'd appreciate your help! :-k 

Thanks
Danke! 
S.

---

### Post by dee.dw on 2006-10-07
> What is device identifier? Choose one! ;) No, it really doesn't matter what you use there.

> Where do I enter HorizSync and VertRefresh? How about the both fields Hor.Sync and Vert.Refresh in the monitor-tab? ;)

> Do I have to type in these words? Try to hit the "get refresh rate" button. Maybe you don't have to do nothing at all. Otherwise the format normally is "30-96", means "lowest freq dash highest freq" - without the quotes!

> Currently on my screen the date, ON/OFF button and trash are in the middle, instead of being to the right. So there might be something not right to my xorg.conf?! Ehm, nope. I think something isn't right with you panel. You shouldn't center it. But this is another issue for another thread please.

@all: The design for the option files is finished now. See [http://www.ubuntuusers.de/paste/4120/?format=txt](http://www.ubuntuusers.de/paste/4120/?format=txt) for an example and description. It would be great if someone could write some option files...
Any other opinion is appreciated as well.

A new version will be out tomorrow (I hope) with a very great feature (imho ;)).

Greetings, Dee

---

### Post by dee.dw on 2006-10-08
Update v06.10.08:

- Feature: add option for testing configuration before saving (!)
- Feature: add support for device drivers and input device drivers
- Feature: add support for driver options (adding these will come next update)
- Feature: create settings file ~/.xorg-edit with some options
- Feature: add settings menu
- Feature: add menu item to restore config (to last saved)
- Internal: rewrite some code to make program faster
- Internal: create new classes for file handling

The package and archives holds examples for the xml-files. The syntax is really easy.

But the best feature imho is the configuration test without restarting the XServer. So you will see if the XServer starts the next time.

Greetings, Dee

---

### Post by SebMKd on 2006-10-08
OK, I understand now the device identifier is more or less the video card. I use the onboard video chipset on my rig, so I've entered '_SiS 740_'!

Now I can go to the second tab! And so I see the 'Get refresh rate'. I couldn't before, that why I've asked about the Horiz and Vert frequency! :-| 

Upon restart my resolution droped sometimes down to 640x480 - and I couldn't change it. I used to reboot to remedy to this issue, however, now with a new [COLOR="Red"]xorg.conf[/COLOR] it seems solved!

Thanks for your support! Great work. I'll check your upcoming asap.8) 

Regarding my other issue, I'll start a new Thread.

TTYL
S.

---

### Post by po0f on 2006-10-08
dee.dw,

I have already started writing the xml file (about halfway through actually) for Nvidia cards and was wondering about any limits there might be on comment length.  Some of the comments I have written are rather lenghty (:)) so before I get finished and have to edit everything, please post back as to the limit.

I haven't actually used the program yet.  Did you set the comment to display in a label or a textarea?  And how will your program handle empty defaults?  Some of the options are deprecated, but I threw them in there for completeness' sake.

Looking forward to hearing from you.

---

### Post by dee.dw on 2006-10-09
> I haven't actually used the program yet. Did you set the comment to display in a label or a textarea? Until now it's shown nowhere. The next update I want to create some frame like shown attached. So the length isn't important at all because there should be breaks later. But anyway more than one screen length would be too much I think. If you want to descrive the arguments and all you can use the <!-- --> Tags inside the xml-file.
Further I want to display some tooltips (Don't know how yet), so a short comment would be great. Maybe I should differ between shortcomment and longcomment...

> And how will your program handle empty defaults? You will get an error. :) If an option has no default don't use the tags. I will check later before saving if there are fields that are empty.

Greetings, Dee

---

### Post by po0f on 2006-10-09
dee.dw,

I'll post the finished xml file tomorrow.  For the deprecated options, I'll just comment the whole thing, like so (leaving out any possible arguments):
```
<!--
<option name="DeprecatedOption" value="boolean" comment="Don't use this." />
-->
```

Is this fine for you, or do you prefer another format?  Or do you want me to leave them out all together?

---

### Post by dee.dw on 2006-10-09
If you comment them out I will not recognize them and only someone who edit the xml file will see it. If this was your intention I'm fine with it. :)
If this option should be selectable in the program later leave the comments away and add deprecated="true" in the line.

What should I do with these options later? Display them separately in another tab?

Greetings, Dee

---

### Post by po0f on 2006-10-09
dee.dw,

The deprecated options are options that shouldn't be used anymore.  I just wanted to add them for completeness' sake.  As they are unneeded (they aren't even recognized by the driver), I can just totally leave them out.

Don't worry about displaying them, the end user shouldn't see them anyway.  :)

---

### Post by dee.dw on 2006-10-09
If the end user shouldn't see them and even the driver does not recognize them if you would use them you can leave it away I think.

But what do you think about the shortcomment/longcomment option? Or better comment="..." is for short comments and description="..." gives a whole description of the option. Do you think that would be better?

And as I mentioned Tabs before. What do you think of some section="..."? So you could separate the options into some pre-defined (!) sections and I would create some tabs later. So the options wouldn't stand in a long list but keeps a little bit ordered.

Greetings, Dee

---

### Post by po0f on 2006-10-09
dee.dw,

I guess I could try to categorize the options into sections.  I think the Miscellaneous section will be the biggest though.  ;)  I will try to abbreviate my comments to ~250 characters, is this fine?  I would like to see the option of displaying the comment so the user knows what they are modifying (but if they don't know what they are modifying, why are they doing it? ;)).

I guess I could do the comment/description approach.  Like if the user selects an option, it displays the availabe values and the short description.  If they click a "Read more.." button or something, a small window will pop up with the full description.  This is probably doable.  I don't know much wxGTK (this is what you are using, correct?) so I can't help you there.

Sometime tomorrow I'll get off my butt and download a wxGTK tutorial, and see if I can't help you out a little.  :)

---

### Post by dee.dw on 2006-10-09
> Sometime tomorrow I'll get off my butt and download a wxGTK tutorial, and see if I can't help you out a little. That probably won't help - I use wxWidgets. ;) See [www.wxwindows.org](www.wxwindows.org) for more information.

> I guess I could do the comment/description approach. Like if the user selects an option, it displays the availabe values and the short description. If they click a "Read more.." button or something, a small window will pop up with the full description. The "Read More"-Buttons sounds fine... The problem is just that I don't want too much buttons, but I think one 20x20 button doesn't hurt too much.

> I guess I could try to categorize the options into sections. I think the Miscellaneous section will be the biggest though. What for sections are necessary? "General", "Misc", "TV", "Optimize" (means FSAA etc.),... We should define this explicitly before you start.

> I will try to abbreviate my comments to ~250 characters, is this fine? Hm, I don't know. I haven't written the GUI yet, so I don't know how much chars are fit in one line... Maybe you should wait a moment with further comments until we know this.

Greetings, Dee

---

### Post by po0f on 2006-10-09
dee.dw,

wxGTK is the Linux version of wxWidgets, unless you are using wxWidgets for X11/Motif?

Do you have webspace for this project?  Maybe we can codevelop this, unless this project is your baby.  ;)

---

### Post by dee.dw on 2006-10-09
> wxGTK is the Linux version of wxWidgets Right, my mistake.

> Do you have webspace for this project? What do you mean with webspace exactly? Sourceforge or my own webspace?

> Maybe we can codevelop this, unless this project is your baby. It's my baby but help is appreciated. But a warning: The code is badly commented. I haven't had the time yet to do so.

If you just want to help with wxGTK it's fine either, the only necessary file would be guiframe.cpp/.h.

Maybe we can do the programming talk outside this thread. My email is included in the program. :)

Greetings, Dee

---

### Post by Aardfox on 2006-10-10
I installed this via synaptic but there's nothing listed in the applications menu.
Where can I find it?

---

### Post by Anduu on 2006-10-10
It is under System>Administration...called X-Server...

---

### Post by dee.dw on 2006-10-11
I think Systen -> Settings -> X-Server would be the correct path. I will talk to the maintainer because I think Administration would be the better place and maybe xorg-edit the better name...

Greetings, Dee

---

### Post by SebMKd on 2006-10-26
Hey, Does your tool works well on Edgy? I'm trying to find out if I  should upgrade or not...

Thanks! Danke!

---

### Post by dee.dw on 2006-10-26
It should. wxWidgets is the same version as in Dapper.

Greetings, Dee

---

### Post by randyleepublic on 2006-11-07
Much thanks for this truely inspirational piece of work!! :-D 

Tools like this will bring linux/ubuntu into the mainstream.  I am an experienced and capable Windows wrangler.  (You have to wrestle windows into submission to make it do what you want. :rolleyes: )  But, I have been extremely frustrated by the what I percieve as the total chaos of the linux "system".](*,)   I have dual monitors on an Nvidia card and it has been hell getting it to work right.  When I had to switch to one head-dvi and one head-vga, I thought that I would never get it to work again.  Then I found xorg-edit. :-D 

Your tool made it easy for me to debug my xorg.conf.  The best feature IMHO is the preview followed by immediate and pain-free access to the log.  That made it simple: 
1) Change a setting
2) Preview it
3) Examine the log
4) Repeat until done

Sure, an exhaustive and well-documented implementation of all the "options" would be nice, but in the meantime the above use case really bridges the gap very nicely.

Thanks again,

---

### Post by dee.dw on 2006-11-12
New version v06.11.12:

- Internal [ALL]: GUI (xorgedit) and LIB (libxorgedit) are clearly separated now

- Bugfix [GUI]: some element indices were out of range
- Bugfix [GUI]: textfields will be translated even if they are not active
- Bugfix [GUI]: changing languages made the last line of the warning disappear
- Bugfix [LIB]: in lines with comments at the end the argument was wrongly surrounded by quotes sometimes
- Bugfix [LIB]: option lines with no valid arguments will create an error
- Bugfix [LIB]: empty commented lines will be stored correctly
- Feature [ALL]: added "nvidia" driver file (thanks to Casanunda)
- Feature [ALL]: added support for driver option section and description
- Feature [GUI]: deleted settings menu and added settings dialog
- Feature [GUI]: added tool tips for driver options
- Feature [GUI]: added list entry for adding new options/add empty option in device and input device
- Feature [GUI]: added dialog for managing options
- Internal [ALL]: xorg conf driver options will be checked for case conversion and maybe changed after loading and before saving
- Internal [GUI]: removed element counters
- Internal [GUI]: disabled check if monitors or devices exists when adding screens
- Internal [GUI]: disabled integrity check in preview
- Internal [GUI]: only update the currently visible tab
- Internal [GUI]: do not update screen or server layout anymore when device, inpute device, monitor or screen has changed
- Internal [GUI]: driver lists will be read again if option dir has changed
- Internal [GUI]: choosing a list element does not change save status
- Internal [GUI]: changing driver or option name will update driver options list, values and tool tips
- Internal [GUI]: list of boolean values is extended to "false/true", "yes/no", "off/on" and "0/1"
- Internal [GUI]: strict and boolean values cannot be changed
- Internal [GUI]: added menu item for checking xorg.conf
- Internal [LIB]: added element counter for all lists
- Internal [LIB]: added some more checks in xorg file
- Internal [LIB]: added functions for modifying current element in lists
- Internal [LIB]: disabled check if screens or input devices in server layout are double
- Internal [LIB]: empty comments will be ignored and not saved
- Internal [LIB]: made options (and all derived classes) case-insensitive
- Internal [LIB]: print error when two option have the same name
- Internal [LIB]: derived Extensions and ServerFlags directly from OptionList
- Internal [LIB]: moved integrity checks from XorgFile to each element
- Internal [LIB]: checking xorg.conf involves check of driver options (type and strict)

It would be great if I could get more driver options for other video cards than nvidia. :)

Greetings, Dee

---

### Post by chownsb on 2006-12-01
Hey, I tried this xorg-edit program on Edgy.  It looks great, if it worked!  Almost everything I try to do crashes the program.  Index out of bounds messages, files won't save, etc.

Looks like it has potential though.

---

### Post by dee.dw on 2006-12-02
Please fill out a bug report. Either on SourceForge with you xorg.conf, what you have done to crash the program and the current error message. Several users use the program and have not complained about such crashes...

Greetings, Dee

---

### Post by ozp on 2006-12-30
I say that this tool is wonderfull
I was waiting for something like that for years!!

I still cannot use ubuntu in my main computer, because its still lacks many features for the enduser 

 But this tool got it closer


I hope someday this make to the ubuntu main system

---

### Post by dee.dw on 2007-01-04
Update v07.01.04:

- Bugfix [GUI]: options/modelines can now be added even when there are no other options/modelines
- Bugfix [GUI]: changed yes/no-Button after an error occured
- BUGFIX [GUI]: loading a new file accidently ignored all erros in the config file
- BUGFIX [LIB]: Monitor-Modelines will now be written correctly
- Bugfix [LIB]: empty lines will not seen as comment unless it starts with a hash #
- Bugfix [LIB]: EndSection will not be seen as comment after reading xorg.conf a second time
- Feature [GUI]: added more translations (for German users)
- Feature [GUI]: added button for adding generated modelines directly

@chownsb: Still no response from your side... I cannot fix bugs I cannot see or reproduce.

Greetings, Dee

---

### Post by handaxe on 2007-01-09
Thanks for the update.

No debs at the repo - intentional or holiday hangover of the repo?

Used the tar.gz - easy enough tho' binary is named differently (-bin gone).

Small issue - the version number is wrong under help -about (had me puzzled for a mo' why it was not upgraded :-)

Regards,

HA

---

### Post by dee.dw on 2007-01-09
> **handaxe said:**
>  The package maintainer seems to be a little bit busy. I hope he will create a package this week.

> Used the tar.gz - easy enough tho' binary is named differently (-bin gone). That may be because I (as programmer) call the binary xorg-edit, bur the maintainer created a special script called xorg-edit and renamed my binary. It's a little bit complicated here. ;)

[quote]small issue - the version number is wrong under help -about (had me puzzled for a mo' why it was not upgraded :-) Oops... I will fix this immediately. :)

Greetings, Dee

---

### Post by Xealot on 2007-01-12
used xorg-edit from the repo, and im using a completely fresh install of ubuntu

heres what happens when you load the program or try to load the xorg config:
[screenshot]("http://xealot.yaoi.se/~xealot/my_random_images/xorg-edit.png")

---

### Post by dee.dw on 2007-01-12
Okay, number 4... I try to fix this tomorrow... Unfortunately I do not see where the error could be.

Greetings, Dee

---

### Post by dee.dw on 2007-01-12
Update v07.01.12:

 - Bugfix [GUI]: fixed very stupid error with opening file  - sorry for that one
 - Bugfix [GUI]: fixed endless loop in error message
 - Feature [LIB]: write file name for error stack when it could not be opened

A big sorry again for this stupid mistake! Only new users has seen them so everybody else could not reproduce it.

Greetings, Dee

---

### Post by AgenT on 2007-01-14
It should be noted that a program like this already exists:
[http://www.kxgenerator.fe.pl/](http://www.kxgenerator.fe.pl/)

However, your program uses wxWidgets which is *much* better than the above mentioned program using QT. Your program will work in any environment while KXGenerator is only made for KDE.

I point out KXGenerator not to discourage your from your work, but for the possibility that it may give you new GUI or functionality ideas.

---

### Post by dee.dw on 2007-01-14
I don't know if you speak german but I have written an article concerning all graphical configuration utilities I have found (including kcGenerator). You can find the article in the latest version of "freiesMagazin" at [http://www.freies-magazin.de](http://www.freies-magazin.de) and at the German Wiki: [http://wiki.ubuntuusers.de/XServer_grafisch_einrichten](http://wiki.ubuntuusers.de/XServer_grafisch_einrichten).

Greetings, Dee

---

### Post by dee.dw on 2007-01-28
New update v07.01.28:

 - Bugfix [GUI]: screen display options and server layout input device options could not properly be added
 - Bugfix [GUI]: if a device exists but no input device changing tab from "Input Device" had produced an error
 - Bugfix [GUI]: some users could not set option values from driver option list loaded from disk
 - Bugfix [GUI]: if a new entry/option was selected and an error occurs the field is not set back correctly
 - Bugfix [GUI]: reimplement the backup of xorg.conf (It's get lost somehow...)
 - Bugfix [LIB]: deactivated options and modules can now have the same name as an activated one
 - Feature [GUI]: add debug mode that writes all called functions in a logfile
 - Feature [GUI]: if an error occures the correct tab, entry and/or option is opened
 - Feature [LIB]: if an error occures the correct entry/option will be set as current
 - Internal [LIB]: if no default value is given for boolean types "false" is supposed
 - Internal [ALL]: create separate folder for source code with name and version for easier compiling

Greetings, Dee

---

### Post by WakkiTabakki on 2007-02-04
Hi
I've just posted a slightly related application here:
[XConfManager]("http://ubuntuforums.org/showthread.php?t=353103")

While xorg-edit is aimed at editing an xorg.conf file, the XConfManager is meant as a GUI for management of multiple configurations.

/N

---

### Post by TURNER on 2007-04-13
Great tool Dee, fantastic for new users like myself! One of the great attractions to the legacy os is that users can point and click everything, and not roll sleeves up and get stuck in under the bonnet whilst administering the system.

Ubuntu would be well advised to look into tools like this in order to win users! I realise that many users are attracted to linux because it provides the opportunity to REALLY get into your sys, via command line for example..and I agree in this too to a certain extent, but its not everybody's cup of tea as we English might say :D  

Speech over..:)  I've got a small problem.

I downloaded the recent version xorg-edit_07.01.28-0ubuntu1_i386.deb and it installed without any complaints, I ran, entered my root password and amended my screen res (by entering a new mode) and attempted to save.

Upon save I receive the following:

```


can't create file '/etc/X11/xorg.conf_04/13/2007_10:16:54 PM' (error 2: No such file or directory)      
``` 

Followed by

```
Error in file "/etc/X11/xorg.conf_04/13/2007_10:16:54 PM".

Could not create backup file.
Function Stack:
GuiFrame::OnSave ->
GuiFrame::CreateBackup       
```   

running xorg-edit from my terminal works fine...however I receive the following:

```
(xorg-edit-bin:23006): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.
```

I read the German wiki, but my problem here didn't seem to be referenced, any help will be appreciated.

Dee Danke noch mal , das programm ist spitze!

---

### Post by Chris The Ninja Pirate on 2007-04-23
To set the scene I am a complete novice with Ubuntu. I have previously installed 6.06 on a laptop and got everything working on it. However I have recently installed 7.04 on my work laptop and I am completely stumped with the resolution problem. The laptop has an Intel 855GM for the graphics. I can currently display 640x480, 800x600 and 1024x768 which all appeared on install of Ubuntu and are fine for the screen on the laptop (1024x768). However at work I use it plugged into a monitor with a resolution of 1440x900. I have spent the last two days trying to output ANY resolution other than the ones installed on default.

I have installed 915resolution and patched my vBIOS to provide access to other screen resolutions and when I do this the patched resolution (640x480) disappears from my available options but is not replaced by my target resolution (1440x900). I assume I have to change the xserver configuration to allow this but every time I make any manual alterations to this file the xserver crashes and I have to roll back to boot. I have tried using the xorg-edit but I get the same problem as the poster above in that it will not save the changes. I have even used the preview function in xorg-edit and tried to copy the changes into my xorg.conf file but again this caused the xserver to fail on boot.

Currently I am doing my fruit trying to figure this out. Any clues on either how to get xorg-edit to run properly or what changes I should be making to the xorg.conf to allow me to output a 1440x900 resolution to an external monitor, whilst keeping the ability to boot into the default screen would be most welcome.

---

### Post by dee.dw on 2007-04-23
First of all sorry for the delay, but I only received an email today that there a new answers...

[quote="TURNER"]can't create file '/etc/X11/xorg.conf_04/13/2007_10:16:54 PM'[/quote] Yes, I see the error, because the date-variable returns slashes, so it thinks these are subfolders... Hm, I remember the problem some time ago and thought I had fixed it.... 

Anyway I have uploaded a new version (only Source and binary) to Sourceforge. The Deb may take a little. You can use the 32bit-binary and replace it.

The problem concerning libgnomevfs is not directly part of my program. I think wxWidgets has something to do with it.

@Chris: Sorry, but in your special case I could not help. Maybe the XServer does not crash with the new xorg-edit version.

Greetings, Dee

---

### Post by Chris The Ninja Pirate on 2007-04-23
Cheers Dee, I will try the binary tomorrow.

EDIT - New binary works fine although doesn't cure my problem. I haven't quite figured out how to get it to run when I type xorg-edit, and have to run ./xorg-edit from the folder containing the newly extracted folder, but hey I'm new at this.

---

### Post by dee.dw on 2007-05-15
Update v07.05.15:

 - Bugfix [GUI]: adding screen in server layout added wrongly screen in screen-tab
 - Bugfix [GUI]: check if screen in server layout is correct went wrong

Download: [http://sourceforge.net/projects/xorg-edit/](http://sourceforge.net/projects/xorg-edit/)

Greetings, Dee

---

### Post by rocknrolf77 on 2007-06-01
Completely forgot about this great app. Just reminded me when testing the new linux mint. 

Keep up the good work :)

---

### Post by dee.dw on 2007-06-29
Just want to say that I have moved to a new website: [http://www.deesaster.org/progxorg.php](http://www.deesaster.org/progxorg.php) Please adjust your bookmarks.

Greetings, Dee

---

### Post by dee.dw on 2007-08-11
v07.08.11:

 - Internal: changed licence to GPLv3
 - Internal: compiled output is not deleted anymore in Makefile, see bug "[ 1738111 ] xorgedit/Makefile removes what it compiles" on              [http://sourceforge.net/projects/xorg-edit/](http://sourceforge.net/projects/xorg-edit/)

Download: [http://sourceforge.net/projects/xorg-edit/](http://sourceforge.net/projects/xorg-edit/)
Homepage: [http://www.deesaster.org/progxorg.php](http://www.deesaster.org/progxorg.php)

---

### Post by bbboB on 2007-10-01
Feeling extremely stupid, I have spent time off and on the last 4 days trying to get this GUI to load on Dapper 6.06.
I have looked at all the previous posts and find no answers.
The .deb package gives me an error that it can't resolve some dependencies in libc6.
Trying to install from the command line shows that the version numbers for various libraries  on my system are not the vesion numbers needed for the program.
All of the links to repositories posted here come up as 403 or 404 errors, so I can't use Synaptic to find the dependencies for me.
I've tried the .deb from sourcefourge.
So, does this GUI run on Dapper, or do I need a later version of Ubuntu?](*,)

---

### Post by mssever on 2007-10-01
> **bbboB said:**
> Feeling extremely stupid, I have spent time off and on the last 4 days trying to get this GUI to load on Dapper 6.06.
I have looked at all the previous posts and find no answers.
The .deb package gives me an error that it can't resolve some dependencies in libc6.
Trying to install from the command line shows that the version numbers for various libraries  on my system are not the vesion numbers needed for the program.
All of the links to repositories posted here come up as 403 or 404 errors, so I can't use Synaptic to find the dependencies for me.
I've tried the .deb from sourcefourge.
So, does this GUI run on Dapper, or do I need a later version of Ubuntu?](*,)
If it depends on a higher version of libc6, then you either need to upgrade or try building it from source (which may or may not work, depending on why the dependency was listed that way).

---

### Post by dee.dw on 2007-10-02
> So, does this GUI run on Dapper, or do I need a later version of Ubuntu? The GUI ist for every system, not only Ubuntu. But the deb-package is for Ubuntu Feisty, not for Dapper.

If you want to use the program, download the binary file (-bin at the end), extract it and start "xorg-edit" with sudo.

Greetings, Dee

---

### Post by bbboB on 2007-10-02
Dee,
Thanks for getting back to me.
I wish there were a designation on which type of file to download, it would have helped.
Have gotten the binary file and been experimenting with the program.  It is a nice interface and it runs rings around the text style editing.  I especially like the test function, where I can see what is going to happen before I save.
Thanks for the time you've taken to make this program!!

---

### Post by dee.dw on 2007-10-02
> **bbboB said:**
> I wish there were a designation on which type of file to download, it would have helped. Yes, unfortunately Sourceforge has no button for it. :(

But thanks for your comment. :)

Greetings, Dee

---

### Post by RJ Hythloday on 2008-01-25
Thanks for all the work, I've been searching this thread as well as elsewhere on the web and haven't found the answer I'm looking for. 

When I open xorg-edit I go the the monitor tab and in modeline generator I put x=1360 y=720 refresh=60, click generate it auto fills more info. all looks good so far.  When I click add it tells me option name can not be empty, if I try to put anything in the option name I get the same message.

I'm sure I'm doing something wrong here. I'm very much a noob and trying to get kubuntu gutsy running properly. I'm trying to create this resolution so I can switch from the monitor to the plasma I've been using w/ xp. 

I feel pretty stuck and dependent on xp since I haven't got everything running smoothly yet, and the wife is very impatient w/ my trouble shooting skills :lol:

Thanks of any help, I'll check back soon.

Bob

---

### Post by Masterart on 2008-03-23
A newbie here.:)
I just wanted to change gamma value. the white
color on the screen looked glaring.I opened
Xorg-edit changed gamma to 0.6 , reboot.

**Total blackout !**

My linux knowledge is a few days old.
Any Recovery-mode options ?

I have ATI Radeon Xpress 200.

---

### Post by dee.dw on 2008-03-25
> Total blackout ! Not good. What version of Ubuntu do you use? xorg-edit ist not tested with Ubuntu 7.10 Gutsy and do not expect it to work there because of the changes in X.Org 7.3.

> Any Recovery-mode options? Of course, see README for information. I paste it here: >  = Troubleshooting =
 ====================

 == Restore backup in terminal or console ==
 ============================================

In case of a misconfigured xorg.conf the XServer may not start, so you need to restore a backup of an
old config file. Just login in the console and type

  cd /etc/X11

to go to the XServer directory. With

  ls xorg.conf_*

you can see all backup files. In most cases it's the best to restore the last saved file with

  cp xorg.conf_DATE_TIME xorg.conf

where DATE and TIME should match the correct values (without any separators).

After restarting XServer everything should be fine.
Greetings, Dee

---

### Post by CptPicard on 2008-03-25
The lesson is ... do not edit complex config files like xorg.conf using a GUI. If you do, save a backup (well, always save a backup). 

I am very averse to all kinds of GUI tools on Linux because you just never know what they do. They might have bugs or might behave unexpectedly.

---

### Post by dee.dw on 2008-03-25
> The lesson is ... do not edit complex config files like xorg.conf using a GUI. If you do, save a backup (well, always save a backup). You mean: If you (or any program) alter some system files make a backup before. Currently your sentence read as: "If you're using a GUI make a backup. If you edit it manually don't."

> I am very averse to all kinds of GUI tools on Linux because you just never know what they do. They might have bugs or might behave unexpectedly. I like FLOSS. You too? ;)

Greetings, Dee

---

### Post by CptPicard on 2008-03-25
> **dee.dw said:**
> You mean: If you (or any program) alter some system files make a backup before.

Yeah well, you know, Real Men (tm) don't make backups when they edit manually... ;)

---

### Post by Masterart on 2008-04-07
Thanks.
I finally learned how to edit that config file manually.
Yes, I'm using Ubuntu 7.10 and may have
neglected compatibility of this tool.

---

### Post by dee.dw on 2008-08-07
**Update**

v08.08.06:
 - Internal [GUI]: changed accelerator keys for Close to Ctrl+W and for Quit to Ctrl+Q
 - Internal [ALL]: updated mail adress in all files
 - Feature [ALL]: added ifndef in Makefile for INSTALLPATH

v08.08.03:
 - Internal [GUI]: included stdlib.h and string.h in MyString-class because of compile errors under arch linux with missting strlen and atoi/atof
 - Internal [GUI]: updated about-dialog
 - Internal [ALL]: removed debugging flag (-g) from Makefile and added optimization flag (-O3) instead

Download: [http://sourceforge.net/projects/xorg-edit/](http://sourceforge.net/projects/xorg-edit/)

Greetings, Dee

---

### Post by cb34 on 2008-12-28
so does this tool work good, can i use it at this point in time?

i have no probs with hand-modifying the xorg file, but if this tool works good, that would be great.

i dont see any action since Aug. so i'm askin. :D

---

### Post by dee.dw on 2008-12-28
Hello,

since Ubuntu uses the new xserver and a minimal xorg.conf I don't know if xorg-edit still works in this new environments. So I don't develop the program anymore.

Just try it and if it works, tell us. :)

Greetings
Dee

---

### Post by cb34 on 2008-12-28
ok i will.. thanks. :D

looked like a good project though.. props.

---

### Post by nathanpc on 2012-09-30
Congratulations for this awesome tool. Really appreciated how easy it is to edit my xorg.conf using it. :)

---

### Post by overdrank on 2012-09-30
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

