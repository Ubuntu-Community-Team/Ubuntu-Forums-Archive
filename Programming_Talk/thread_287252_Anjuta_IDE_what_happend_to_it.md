---
title: "Anjuta IDE what happend to it????"
date: 2006-10-28
forum: Programming Talk
---

### Post by thenetduck on 2006-10-28
Hi, 
  I just installed Edgy Efy. (I'm sorry to say that I'm only impressed with the new design and flow, lost of things seem to be missing, im considering going back to dapper) and installed Anjuta. Has anyone used Anjuta in Edgy yet? I'm a little confused at how it functions. It's changed a lot and I can't seem to be able to bring up a file. Am I just doing something wrong? or does it seem way to much of a hassle to create a simple c++ file in this new Anjuta IDE? Before this I loved Anjuta but right now, i'm looking for a new IDE if it's ganna lack being user friendly. 

 Anyone have any thoughts? 
 
 Thanks,  

 The Net Duck

---

### Post by chmurli on 2006-10-29
i have got the same problem. in edgy is new 2.02 anjuta, this ver. have many bugs ;/. i dont know how to install old version 1.2x because dependencies are quite big ;/. now i use geany ide.

---

### Post by FyreBrand on 2006-10-29
Anjuta 2.02 doesn't seem to work right, at least not for me.  The person in this thread was having problems with it.  In my [**post in that thread**]("http://www.ubuntuforums.org/showpost.php?p=1683980&postcount=3") I recommended alternatives.

I like Geany for smaller tasks and Code::Blocks for larger tasks.  Code::Blocks has a lot of potential and the people on that website are really nice.

---

### Post by nimrod_abing on 2006-10-29
> **FyreBrand said:**
> Anjuta 2.02 doesn't seem to work right, at least not for me.  The person in this thread was having problems with it.  In my [**post in that thread**]("http://www.ubuntuforums.org/showpost.php?p=1683980&postcount=3") I recommended alternatives.

I like Geany for smaller tasks and Code::Blocks for larger tasks.  Code::Blocks has a lot of potential and the people on that website are really nice.

The gedit that comes with Edgy (gedit 2.16.1) has a lot of improved functionality to make programming tasks easier. If you don't need integrated debugging and project management features, then I suggest you try the following:[LIST=1]
[*]Open Applications/Accessories/Text Editor from the main menu.
[*]From the gedit main menu, go to Edit/Preferences...
[*]Click on the Plugins tab.
[*]Enable "External Tools", "File Browser Pane", "Indent Lines".
[*]Go to Documents/External Tools and configure your Build command (personally I use scons) and add more commands as you need them.[/LIST]For larger tasks, as FyreBrand suggested, use Code::Blocks. I like it because it has really nice integration with wxWidgets.

For even larger tasks (and larger memory consumption :D) use Eclipse with the CDT plugin.

You can also check out JEdit, which was my personal favorite until the latest gedit :)

---

### Post by Tiede on 2006-10-30
ditto here. I cannot even compile my progs anymore... 
Where has the command gone?
For example, I cannot compile this trivial program for my C class...
Where is the 'Build' menu?
[Link to image](http://img98.imageshack.us/img98/991/anjutamissbm9.png)

---

### Post by Tiede on 2006-11-03
I found the build menu, hidden in the plugins that won't even stayed saved (known bug [#63126](https://launchpad.net/distros/ubuntu/+source/anjuta/+bug/63126)) .
For some reason though, I cannot even test programs in Anjuta since it won't run the programs... It will compile (successfully) but it won't execute. I remember before, I would just type F9(Compile) then F11(Build) and F3(Execute) and I could test that my programs ran perfectly. Now everything I try fail, I just can't get my programs to run at all. I am sorry, but without testing, what good is an IDE?
I remember loving anjuta so much since at school they use DevC++ on the windows machines and the anjuta interface was quite similar to that. Now I have to try to find some other IDE that is just as good (not that easy, since Geany won't run my stuff neither - complains about not being able to create some "start-script"... FRUSTRATING!!!
(Oh, I can't even do F9 to compile in Anjuta anymore by the way...)
I guess this is my experience with the dark side of Open Source - No control... Seriously though, with [so many bugs](https://launchpad.net/distros/ubuntu/+bugs?field.searchtext=anjuta&orderby=-importance&search=Search&field.status%3Alist=Unconfirmed&field.status%3Alist=Confirmed&field.status%3Alist=In+Progress&field.status%3Alist=Needs+Info&field.status%3Alist=Fix+Committed&field.assignee=&field.owner=&field.omit_dupes=on&field.has_patch=&field.has_no_package=) in the new anjuta ide, why did they decide to put it in edgy?

---

### Post by FyreBrand on 2006-11-03
Well there are some other options mentioned you could try.  Or you if you want Anjuta then I think most people using it are downloading CVS.

---

### Post by daniloeu on 2006-11-07
To downgrade Anjuta with three easy steps, see this posts:

[http://ubuntuforums.org/showthread.php?t=288480](http://ubuntuforums.org/showthread.php?t=288480)
[http://www.danilocesar.com/blog/2006/11/07/anjuta124-on-edgy-its-possible/](http://www.danilocesar.com/blog/2006/11/07/anjuta124-on-edgy-its-possible/)

---

