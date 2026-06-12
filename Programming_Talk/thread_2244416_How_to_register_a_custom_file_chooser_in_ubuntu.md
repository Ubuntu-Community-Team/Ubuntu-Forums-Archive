---
title: "How to register a custom file chooser in ubuntu ?"
date: 2014-09-16
forum: Programming Talk
---

### Post by astre on 2014-09-16
Hi,

I would like to override the file chooser(currently gtkfilchooser) with a custom file chooser on my Ubuntu OS ? Is this possible in any way ? I'm using Ubuntu 10.04 LTS

---

### Post by TheFu on 2014-09-16
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) was EOL in 2013.

Also, which language are you programming using ... for after you get onto a supported release?

---

### Post by astre on 2014-09-17
Yes i know it has reached EOL. But still we have it on one of our production servers. I would prefer any language for creating it. It's just that i want to make the file chooser more restricted.

---

### Post by Bucky Ball on 2014-09-17
We can not give much support for 10.04 LTS as, as stated, it is EOL. Too old and few are familiar with it now. Please refer here:

EOL release recommendations:
[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

Upgrade to a supported release. It is a bad idea to be using an EOL release on a production machine, particularly if it is online. You've had no security updates for a year and a half and the machine will only become more vulnerable as time goes on.

PS: The repos are closed for 10.04 so even if you find another file chooser you won't be able to install it from the official repos.

---

### Post by QIII on 2014-09-17
If a person were to pose a programming question in the Programming sub-forum ...

---

### Post by astre on 2014-09-17
> PS: The repos are closed for 10.04 so even if you find another file  chooser you won't be able to install it from the official repos.

Alright we will upgrade to latest one. But is it possible to create a custom file chooser and register it so that whenever other applications request the new custom one will be invoked ?

> If a person were to pose a programming question in the Programming sub-forum ...

Hmm, being a new here i was unaware of this. I'll post it there.

---

### Post by astre on 2014-09-17
Hi All,

Sorry to post it here again. Original post [http://ubuntuforums.org/showthread.php?t=2244416](http://ubuntuforums.org/showthread.php?t=2244416)

I would like to override the file chooser(currently gtkfilchooser) with a  custom file chooser on my Ubuntu OS ?
After registering it, any external application which request a filechooser, the OS should invoke this new custom filechooser.
Is this possible in any way ?
I'm ready to code it in any language as long as my requirement is satisfied.

---

### Post by slickymaster on 2014-09-17
[COLOR=#000000][FONT=Arial]Threads merged.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Please do not create duplicate threads, it dilutes community effort.[/FONT][/COLOR]

---

### Post by TheFu on 2014-09-17
[http://www.gtk.org/api/2.6/gtk/GtkFileChooser.html](http://www.gtk.org/api/2.6/gtk/GtkFileChooser.html) provides the API to do what you want for a single instance. 
Or [https://developer.gnome.org/gtk3/stable/GtkFileChooser.html#gtk-file-chooser-add-filter](https://developer.gnome.org/gtk3/stable/GtkFileChooser.html#gtk-file-chooser-add-filter)

That means inside 1 program that you write.  It would be unwise to do it system wide, so that isn't easy ... well, you could get the GTK library code and modify it yourself, but it will break lots of other programs.

C or C++ are the languages for this. I suppose you could use ASM, but that would be painful.  Many languages have wrappers for GTK which may or may not support the filter construct. If you are short on time, you'll want to pay a C/C++ expert.  Gaining the knowledge that modifying a core library like that from zero C programming background is a 1-2 yr exercise.  Doing it for 1 program alone ... probably 3-6 months.

Of course, you probably are much, much, much, smarter than me.

---

### Post by ofnuts on 2014-09-17
You are mistaken if you think there is one single fle chooser. As a KDE-centric person, I see two of them, the one for the GTK apps and the one for the Qt apps (as a minimum). And any Java app would likely come with its own, derived from the Java one.

This said, for GTK2, all the answers I find are of the type 'it's open source, cook your own GTK lib'.

If you want to "restrict" the user, just do it properly by setting the adequate authorizations on files and directories? A user can completely bypass the UI and enter file path/names directly...

---

### Post by astre on 2014-09-18
Thanks for clearing the fact.
Please refer the below image:

[IMG]http://i.imgur.com/jyAIqlq.jpg[/IMG]

I want to change the default "Save in Folder" path viz. here "Home folder for user john" to something else. So that whenever a filechooser is opened, "Save in Folder" would point to a directory which i have set and not the default home folder.
Any ideas how to do this ?

---

### Post by ofnuts on 2014-09-18
No... the old GTK file chooser would by default open in the application current directory, but the new one completely shuns that concept, it opens in the users "Documents" directory.

Digging a bit into this.... my fave GTK2 application saves by default to "Documents". After some grep-ping in my profile files, I find that this is because the GTK2 file chooser actually looks into a  ~/.config/user-dirs.dirs that lists some related user directories (Documents, Videos, Images...) and picks the "Documents" one. Changing that line in user-dirs.dir indeed makes the file chooser dialog (in save mode) use the new directory.

---

### Post by astre on 2014-09-19
Yes it seems its older one. May be since i'm using Ubuntu 10.04. Also it seems that user-dirs.dirs was not introduced at that time. Any idea how to make it work with this older filechooser ?

---

### Post by ofnuts on 2014-09-19
If you use the oldest GTK file choose then IIRC it justs starts in the current directory, so it's just a matter of issuing a CD to the appropriate directpry before starting the app. Or, if you are lucky, the desktop manager has a setting for this.

---

### Post by astre on 2014-09-19
I found these settings in .config/gtk-2.0/gtkfilechooser.ini

[Filechooser Settings]
LocationMode=path-bar
ShowHidden=false
ExpandFolders=true
ShowSizeColumn=true
GeometryX=422
GeometryY=180
GeometryWidth=693
GeometryHeight=531
SortColumn=name
SortOrder=ascending

Any idea which one is the relevant ?

---

### Post by ofnuts on 2014-09-19
None is relevant... The file chooser takes the application current directory.

---

### Post by astre on 2014-09-19
Hmm.. So any other way how to achieve this without upgrading the OS ? Or I have to accept the way how it is currently.

---

### Post by Bucky Ball on 2014-09-19
[This.]("http://ubuntuforums.org/showthread.php?t=2229730")

Or accept the way it is currently. Unfortunately I can't imagine there's much help forthcoming for such an old release. Things change, people forget. You can't update/grade anything.

I'd back up what you have to and do a clean install of 14.04 LTS. Supported until April 2019.

---

### Post by ofnuts on 2014-09-20
> **astre said:**
> Hmm.. So any other way how to achieve this without upgrading the OS ? Or I have to accept the way how it is currently.

My suggestion above doesn't require to upgrade the OS. This is how I worked with Gimp on Ubuntu 10.04... I just updated the "work path" in the launch icon to be the directory where the GTK file chooser would open by default.

---

### Post by astre on 2014-09-20
That will work if doing from Graphical View. But how to do that from command line or when calling an application using process from another appliation. for eg. launching gimp from my application.

---

### Post by ofnuts on 2014-09-20
Set the application's working directory.... at worst start it via a script that does, the child processes inherit the working directory of their parent.

---

### Post by astre on 2014-09-20
Thanks ill try it out..

---

