---
title: "Launching a script/application on audioCD insertion."
date: 2008-11-14
forum: Outdated Tutorials &amp; Tips
---

### Post by djhash on 2008-11-14
Ok..  so i've been searching high and low on how to make nautilus (gnome 2.22.3, nautilus 2.22.5.1) in Ubuntu 8.04 run an application other than those listed in the nautilus Edit->preferences->Media when an audioCD is inserted.

   Seems like previously there was an ability to run a command under System->Preferences->Removable Media and Drives. but somehow this feature was removed.

   So here are the steps to get it working:-
          (the following example uses abcde. a program that is previously installed and works as it should. I think you can easily modify this to run a script)

     Step #1:  Create a launcher on your desktop. 

             -Right click on the desktop
             -Click on "Create Launcher"
                    [IMG]http://imagebin.org/31175[/IMG]
             -Type in a name for the launcher
              (I have not tried a name with spaces, not sure if it will work or not.)
             -Then type in the command to run. hit ok

               [IMG]http://imagebin.org/31176[/IMG]

             - Now you have a launcher on your desktop.

             - Open up terminal and type: ls ~/Desktop/abcde.*
```

djhash@linux-test:~/Desktop$ ls abcde.*

abcde.desktop
```

             - your launchers file name is name.desktop

         Step #2: Placing the launcher in the proper folders..
             - Copy this file to /usr/share/app-install/desktop and to /usr/share/applications.
```

sudo cp /home/djhash/Desktop/abcde.desktop /usr/share/applications/.
sudo cp /home/djhash/Desktop/abcde.desktop /usr/share/app-install/desktop/.

```

             ** I am not 100% sure the you need to copy the file to both folders, but its not gonna hurt.

         Step #3: Telling your computer there is one more choice for dealing with audioCDs.

             -In terminal type the following:
             
```

cd ~
cd .local
cd share
cd applications

```

             - There is a file called  mimeapps.list  you need to edit that file. so..

```

pico mimeapps.list

```

And change this:
```
x-content/audio-cdda=rhythmbox.desktop;sound-juicer.desktop;
```

to
```
x-content/audio-cdda=rhythmbox.desktop;sound-juicer.desktop;abcde.desktop;
```

Now log out and then log back in.

Go to Places->home folder
then go to Edit->preferences->Media
click on the drop down menu next to audioCD
click on Open with acde. 

TADA... :lolflag:

Let me know how it goes.

---

