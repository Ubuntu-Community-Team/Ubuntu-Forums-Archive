---
title: "Where should downloaded applications be extracted in Ubuntu 8.04?"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by UbuDad on 2008-08-03
I'm downloading some animation apps (Pencil, Blender, etc.) for Ubuntu 8.04 and each time I am asked to extract the files I'm confused about where I should do so?  Where should these apps be extracted/installed to? 

I'd also like to make them easily accessible from the Applications Menu.  I know how to add them, finding them is the problem. I'd like them all in one location. Hence my question.

Many thanks.

---

### Post by frankjan on 2008-08-03
make a folder-move them there and use  extract here

---

### Post by UbuDad on 2008-08-03
I guess I should clarify... is there a default location in the file system where apps are installed, similar to Windows' Program Files folder?

---

### Post by lhb1142 on 2008-08-03
There is no default location of which I'm aware but you can do as I did and make one.

Go to "Places -> Home Folder." Then go to "File -> Create Folder." Name this newly created folder "Downloaded Programs" (or whatever you prefer).

Go into this new folder and go to "Bookmarks -> +Add Bookmark." Click on that and your newly created folder (bookmark) will appear in "Places."

You can then specify in Firefox to download all programs to that folder and, when you extract files, you can specify that they all appear in that folder. (Go, in Firefox, to "Edit -> Preferences." On the main page you will see, under "Downloads" a button labeled "Save files to." Browse for your newly created folder and specify that all downloaded program should be saved in that location.)

You will want to uncheck "Ask me where to save files" and make sure that the "Save files to" option is checked.

Once you have extracted (specifying that new folder as the place to which you want the program files extracted - thereby finding everything in one place) and installed your newly downloaded program, it should, if appropriate, appear in your "Applications" section under the appropriate type ("Sound & Video," for example, or "Graphics," etc.). Note that some downloaded items, especially those that add codecs, for example, to existing programs, will not appear in your "Applications" section but they will still do their job. (Libdvdcss2 is an example.)

I find this convenient and easy. I hope you do too and I hope this has helped you.

---

### Post by blue_shift on 2008-08-03
Just to clarify, it's much easier to install from the repositories using ```
 sudo apt-get install [programme name]
``` or synaptic, since packages, dependencies and menu entries are taken care of in one click.

---

### Post by UbuDad on 2008-08-03
> **lhb1142 said:**
> There is no default location of which I'm aware but you can do as I did and make one.

Go to "Places -> Home Folder." Then go to "File -> Create Folder." Name this newly created folder "Downloaded Programs" (or whatever you prefer).

Go into this new folder and go to "Bookmarks -> +Add Bookmark." Click on that and your newly created folder (bookmark) will appear in "Places."

You can then specify in Firefox to download all programs to that folder and, when you extract files, you can specify that they all appear in that folder. (Go, in Firefox, to "Edit -> Preferences." On the main page you will see, under "Downloads" a button labeled "Save files to." Browse for your newly created folder and specify that all downloaded program should be saved in that location.)

You will want to uncheck "Ask me where to save files" and make sure that the "Save files to" option is checked.

Once you have extracted and installed your newly downloaded program(s), they should, if appropriate, appear in your "Applications" section under the appropriate type ("Sound & Video," for example, or "Graphics," etc.).

I find this convenient and easy. I hope you do too and I hope this has helped you.
@lhb1142

Makes complete sense. I'll definitely remember where I extract/install packages that way.  Many thanks.

---

### Post by northern lights on 2008-08-03
> **UbuDad said:**
> I guess I should clarify... is there a default location in the file system where apps are installed, similar to Windows' Program Files folder?

Near-all applications are in '/usr/bin'.

Nonetheless, while that answers the above question it is not related to your problem at all. You're not wanting to know where to extract, but how to install.

First, check in the Ubuntu repositories. Thereafter try finding a .deb file.

You have downloaded source and that needs compilation.

As for the particular apps you mentionend, 'blender' is in the repos. Navigate to "System > Administration > Software Sources" and enable everything but 'proposed' and 'backports'. Run ```
sudo apt-get install blender
``` from the terminal.

[Here]("http://getdeb.net/app/Pencil")'s a .deb for pencil. It should install via double-clicking on it. If not, run ```
sudo apt-get install gdebi
```first

---

### Post by Catalyst2Death on 2008-08-03
While there isn't a particular place where you need to install applications, there are some guidelines.  If for instance, you would like to run programs from the terminal.  Instead of having a dedicated folder + registry settings like windows, linux uses an environment variable called PATH to look for executable files which are then treated like commands.  So, in order to "install" a program, you extract it to wherever you want it to live (generally /home/(username)/(nameofprogram) is good) and then, you either modify the PATH variable by adding a new entry for this path in your terminal (Applications>Accessories>Terminal):

```
$ export PATH=/path/to/directory:$PATH
$ echo $PATH

```

This will let you run executable files in your directory as commands.
To make it stick you need to add the export line to your .bash_profile in:
/home/(username)/.bashprofile  if it doesn't exist you can make one:

$ gedit /home/(username)/.bashprofile

And then paste the export line above and save it.  More info here:
[http://www.troubleshooters.com/linux/prepostpath.htm](http://www.troubleshooters.com/linux/prepostpath.htm)

Now, when you want to create a desktop icon for the program, all you need to do is right click on the desktop select "Create Launcher" and fill in the fields.

Name: Name that will be displayed on desktop
Command:  Name of executable to run (if PATH points to your program directory, you can just type the name of the executable, otherwise browse to it using th Browse... button
Comment: Tool tip text that will pop up if you hover over the icon

Sometimes the executable will have its own icon that will change when you type in the command, if it doesn't you can modify the icon by clicking on the springboard picture and browsing to the icon you want to use (custom icons can be stored in /home/(username)/.icons/

Note that using the Browse button is more user friendly than modifying your path, so if thats more comfortable go that way.  Also notice that files/folders which begin with a period are hidden, to see them in the file browser hit Ctrl+H, and if your in the terminal use:
```
$ ls -l
```

to see all files and folders in a directory

---

### Post by mcduck on 2008-08-03
So do you have working Internet connection on the Ubuntu machine?  If you do, it's not really necessary to download & install programs by hand. You should use Ubuntu's package management tools. Downloading and installing manually is more of a windows thing, Linux has better ways to handle this kind of stuff,a t least as long as you have Internet connection..

For example, try the "Add/Remove.." in the Applications menu, it will give you easy access to most commonly used programs. And to get access to all the software in Ubuntu's servers try Synaptic Package Manager, in System/Administration.

And you definitely should read this: [How to install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

---

