---
title: "Looking for an easy way to compile..."
date: 2010-03-24
forum: Programming Talk
---

### Post by jsriz on 2010-03-24
well I do a lot of c++ compiling i just want to find out if there is a way to add an entry in the right click menu that would open up a terminal and run g++ filename.cpp in it.
or anything  easier than going to a terminal and typing g++ filename.cpp.............

---

### Post by nothingspecial on 2010-03-24
Try geany or codeblocks.

They are in the repos

---

### Post by rory526 on 2010-03-24
you could make a function like the following and put it in your .bashrc file in your home directory.

```
compile() {
g++ -o "$1" "$1".cpp
}
```

then typing

 ```
compile myProgram
``` 

will compile myProgram.cpp

---

### Post by jsriz on 2010-03-24
no no i just love the terminal and do not want to go for a IDE cos they need to be "installed".....
and also am looking forward to start off shell scripting ......

---

### Post by jsriz on 2010-03-24
> **rory526 said:**
> you could make a function like the following and put it in your .bashrc file in your home directory.

```
compile() {
g++ -o "$1" "$1".cpp
}
```then typing

 ```
compile myProgram
```will compile myProgram.cpp
wow
I have a small doubt if i add this:
```

comnrun() 
{
g++ "$1".cpp
./a.out
}


```running "comnrun myprog" will it do a compile and run??
and is there a way to add it to the right click menu of a .cpp file (since the right click menu is different for different type of files )......

---

### Post by rnerwein on 2010-03-24
hi
if you like the good old, but very powerfull unix/linux tools then have a look at " man make ".
but the normal manual pages on the system only gives you i think only 0.00001% percent of the
power of make. have a look at the GNU manual pages ( google a little bit ).
ciao

---

### Post by jsriz on 2010-03-24
> **rory526 said:**
> you could make a function like the following and put it in your .bashrc file in your home directory.

Is there a particular way to make a function or just append the code you gave to the ./bashrc 
I just tried that out and it didnt work out.....
it just gives compile : command not found...

---

### Post by nothingspecial on 2010-03-24
> **jsriz said:**
> i just want to find out if there is a way to add an entry in the right click menu that would open up a terminal and run g++ filename.cpp in it.


> **jsriz said:**
> no no i just love the terminal and do not want to go for a IDE cos they need to be "installed".....
and also am looking forward to start off shell scripting ......

You confuse me. Either you want to do this in the gui (right clicking mouse), or you want to do it in the terminal -

- elaborate please :D

---

### Post by jsriz on 2010-03-24
> **nothingspecial said:**
> You confuse me. Either you want to do this  in the gui (right clicking mouse), or you want to do it in the terminal  -

- elaborate please :D
actually i want the right click menu of .cpp files to have a  entry  "compile" clicking on which would open up a terminal and execute g++  .....
i know its too imaginative but even happy to have something similar to  that...

---

### Post by nothingspecial on 2010-03-24
I don`t know how to do that.

I`ll bet it`s easier in openbox than gnome though.

Cheers :D

---

### Post by rory526 on 2010-03-24
you could make a launcher that runs the following shell script:

```

#! /bin/bash
program=$(zenity --entry)
g++ -o $program $program.cpp

```

save the script in a ".sh" file in your home directory, let's say compile.sh.

then make it executable. In the terminal:

```
chmod +x compile.sh 
```

Next, left-click on the panel at the top of the screen. Click on "Add to Panel...". Select "Custom Application Launcher". In the "Command" box, enter

```
./compile.sh
```

and whatever you want for the "Name" and "Comment" boxes. You can choose your own picture for the icon too. Click on the springboard and choose one of the gnome icons, or use (or code) another svg file.

When want to compile something, click the icon and a textbox will appear. enter the path and name of the source file and click "ok".
You can add the path to your source file's directory to the shell script above if entering it in the box is tedious.

```

#! /bin/bash
program=$(zenity --entry)
g++ -o path/to/$program path/to/$program.cpp

```

---

### Post by rory526 on 2010-03-24
> **jsriz said:**
> Is there a particular way to make a function or just append the code you gave to the ./bashrc 
I just tried that out and it didnt work out.....
it just gives compile : command not found...

You have to open a new terminal window for the changes to .bashrc to take effect.

also note that the name of the file is ".bashrc", not "./bashrc". It might have been a typo, but I want to be sure! :)

.bashrc is a hidden file and exists already in your home directory. all hidden files in linux start with a ".".

---

### Post by nothingspecial on 2010-03-24
or just type ```
bash
```

Still can`t figure out how to add it to your right click menu for .cpp files though.

---

### Post by rory526 on 2010-03-24
> **jsriz said:**
> wow
I have a small doubt if i add this:
```

comnrun() 
{
g++ "$1".cpp
./a.out
}


```running "comnrun myprog" will it do a compile and run??
and is there a way to add it to the right click menu of a .cpp file (since the right click menu is different for different type of files )......

I haven't tested it, but I think it should work.

I'm not sure how to alter the right-click menu of a file... but this is linux! there is always a way!

---

### Post by jsriz on 2010-03-24
> **rory526 said:**
> You have to open a new terminal window for the changes to .bashrc to take effect.

also note that the name of the file is ".bashrc", not "./bashrc". It might have been a typo, but I want to be sure! :)

.bashrc is a hidden file and exists already in your home directory. all hidden files in linux start with a ".".
Sorry myBad it does work 
ya tried out the script also 
thanks for the replies
could you please tell me how to change the title of the box that appears......
True its Linux and there is always a way to do it
hope to find out a way to alter the right click menu soon

---

### Post by rory526 on 2010-03-24
> **jsriz said:**
> Sorry myBad it does work 
ya tried out the script also 
thanks for the replies
could you please tell me how to change the title of the box that appears......
True its Linux and there is always a way to do it
hope to find out a way to alter the right click menu soon

Is NOW too late?!?! :)

check out this:

[http://techthrob.com/2009/03/02/howto-add-items-to-the-right-click-menu-in-nautilus/](http://techthrob.com/2009/03/02/howto-add-items-to-the-right-click-menu-in-nautilus/)

I haven't finished going through it yet, but it looks promising.

To alter the title of the box that comes up, alter the shell script as follows:

```
#! /bin/bash
program=$(zenity --entry --title "This is the title of the box" --text "This is the text of the box")
g++ -o $program $program.cpp
```

---

### Post by rory526 on 2010-03-28
Did you get your right-click compile button set up in the end?

---

### Post by jsriz on 2010-03-28
well I had hard time finding it with :"Once installed, you&#8217;ll find a new entry in your System menu, under  &#8220;Preferences&#8221; titled &#8220;Nautilus Actions Configuration."
cos I use the button instead of the three tabs of application places and system

but its not running
well i ran its command "nautilus-actions-config-tool" in the terminal and i get this
```

/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:173: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:214: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:320: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:327: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:341: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:363: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:365: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:389: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:395: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:434: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:440: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:517: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:550: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:552: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:571: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:572: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:606: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:607: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:647: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:649: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:672: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:674: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:706: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:707: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:721: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:722: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:741: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:743: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:772: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:775: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:791: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:807: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:830: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:871: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:878: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:897: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:904: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:943: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:945: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:990: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:997: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:1181: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:1184: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:1269: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:1276: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:1313: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:1315: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:1330: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:1335: Murrine configuration option "profile" is no longer supported and will be ignored.

(nautilus-actions-config-tool:386): NA-nact-CRITICAL **: get_actions_list_treeview: assertion `GTK_IS_TREE_VIEW( treeview )' failed

(nautilus-actions-config-tool:386): Gtk-CRITICAL **: gtk_tree_view_get_selection: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(nautilus-actions-config-tool:386): Gtk-CRITICAL **: gtk_tree_selection_set_mode: assertion `GTK_IS_TREE_SELECTION (selection)' failed

(nautilus-actions-config-tool:386): NA-nact-CRITICAL **: get_actions_list_treeview: assertion `GTK_IS_TREE_VIEW( treeview )' failed

(nautilus-actions-config-tool:386): Gtk-CRITICAL **: gtk_label_set_mnemonic_widget: assertion `GTK_IS_LABEL (label)' failed

(nautilus-actions-config-tool:386): NA-nact-CRITICAL **: nact_tree_model_initial_load: assertion `GTK_IS_TREE_VIEW( treeview )' failed

(nautilus-actions-config-tool:386): Gtk-CRITICAL **: gtk_tree_view_set_enable_tree_lines: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(nautilus-actions-config-tool:386): Gtk-CRITICAL **: gtk_tree_view_append_column: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(nautilus-actions-config-tool:386): Gtk-CRITICAL **: gtk_tree_view_append_column: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(nautilus-actions-config-tool:386): Gtk-CRITICAL **: gtk_combo_box_set_model: assertion `GTK_IS_COMBO_BOX (combo_box)' failed

(nautilus-actions-config-tool:386): Gtk-CRITICAL **: gtk_combo_box_entry_get_text_column: assertion `GTK_IS_COMBO_BOX_ENTRY (entry_box)' failed

(nautilus-actions-config-tool:386): Gtk-CRITICAL **: gtk_cell_layout_clear: assertion `GTK_IS_CELL_LAYOUT (cell_layout)' failed

(nautilus-actions-config-tool:386): Gtk-CRITICAL **: gtk_cell_layout_pack_start: assertion `GTK_IS_CELL_LAYOUT (cell_layout)' failed

(nautilus-actions-config-tool:386): Gtk-CRITICAL **: gtk_cell_layout_add_attribute: assertion `GTK_IS_CELL_LAYOUT (cell_layout)' failed

(nautilus-actions-config-tool:386): Gtk-CRITICAL **: gtk_cell_layout_pack_start: assertion `GTK_IS_CELL_LAYOUT (cell_layout)' failed

(nautilus-actions-config-tool:386): Gtk-CRITICAL **: gtk_cell_layout_add_attribute: assertion `GTK_IS_CELL_LAYOUT (cell_layout)' failed

(nautilus-actions-config-tool:386): Gtk-CRITICAL **: gtk_combo_box_set_active: assertion `GTK_IS_COMBO_BOX (combo_box)' failed
**
NA-nact:ERROR:nact-ibackground-tab.c:381:get_folders_treeview: assertion failed: (GTK_IS_TREE_VIEW( treeview ))
Aborted (core dumped)

```

---

### Post by jsriz on 2010-03-28
Once I get that i guess that i only have to pass the 
path as 
/usr/bin/g++
and parameters as 
-o  %f %f.cpp
and set the required conditions
that would be easy right

---

### Post by jsriz on 2010-03-29
still unable to get nautilus-actions-config-tool to get running.....

---

### Post by rory526 on 2010-03-30
hmm. I can't to get it to work either.

Try restarting nautilus? ```
nautilus -q
```

---

### Post by jsriz on 2010-03-30
> **rory526 said:**
> hmm. I can't to get it to work either.

Try restarting nautilus? ```
nautilus -q
```
I tried that and also restarting the system but still the same result..
I guess i will post it in a new thread 
[http://ubuntuforums.org/showthread.php?t=1442977](http://ubuntuforums.org/showthread.php?t=1442977)

---

### Post by davyzhu on 2010-03-31
> **jsriz said:**
> well I do a lot of c++ compiling i just want to find out if there is a way to add an entry in the right click menu that would open up a terminal and run g++ filename.cpp in it.
or anything  easier than going to a terminal and typing g++ filename.cpp.............
 Try GNU make.
1. create a file name "Makefile"
the content is sth like

hello: hello.c
    gcc -o hello hello.c

2. command line
$ make hello

3. you can get hello

---

### Post by rickcjmac on 2011-01-13
I know this is an old thread, but maybe it still gets some google hits? This is a shell script I wrote for the same thing. 

* If there is an argument given (without the file extension) it compiles that, otherwise it

* Looks for c program files

   -If there is only one c program in the current directory then
    that specific code is compiled

   -If there are multiple c program files in the current  
    directory then a list appears and prompts the user to
    input a number according to which program they want to 
    compile

* After creating the executable file, it runs the program then promptly deletes the executable file. I did this so that the directory doesn't get all junked up. To undo this feature simply remove the ```
rm output
``` from the shell script.

```
#!/bin/bash

num=$( find . -maxdepth 1 -name "*.c" | wc -l )
fil=$( find . -maxdepth 1 -name "*.c" )

if [ $# -gt 0 ]
then
   gcc -o output $1.c
   ./output
   rm output
   exit
elif [ "$num" -gt "1" ]
then
   echo Which file do you want to compile?
   select item in $fil
   do
      gcc -o output $item
      ./output
      rm output
      break
   done
   exit
else
   gcc -o output *.c
   ./output
   rm output
   exit
fi
```

Also, I run this code a lot from the terminal. I created an alias: ```
alias c='~/.gnome2/nautilus-scripts/c'
``` and put this in my .bashrc file. This way if I want to run the script all I have to do is type "c" and "enter" into the terminal and the script is run from my current directory. 

Hope this helps someone :)

---

