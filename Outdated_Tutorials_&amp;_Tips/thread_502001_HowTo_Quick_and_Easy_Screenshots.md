---
title: "HowTo: Quick and Easy Screenshots"
date: 2007-07-16
forum: Outdated Tutorials &amp; Tips
---

### Post by noynac on 2007-07-16
I experienced stability problems with the default Ubuntu screenshot utility and desired an easy method to view screenshots once taken. After researching various alternatives, I found a solution that works for me and thought it might be of use to others. 

Two small utilities--named scrot and feh--are needed. They are easily installed by way of the Synaptic Package Manager but can also be installed by typing the following into a terminal window:

```
sudo apt-get install scrot
```

```
sudo apt-get install feh
```

Once the required utilities are installed, the screenshot command needs to be assigned to the PrintScreen key. To do this, start the configuration-editor utility by going to applications->system tools->configuration editor. Then, scroll down the left pane to /apps/metacity/global_keybindings and click on this item. Look in the right pane for run_command_screenshot and, if necessary, change the value of this item to Print. 

Back in the left pane scroll down just one key and click on keybinding_commands. In the right pane, change the value of command_screenshot to:

```
scrot -q 75 '/home/username/screenshots/%m.%d.%y at %H.%M.%S.png'
```

I should add a few comments on the above:

* You have to change username to your actual user name.

* I save all screenshots to a directory named screenshots. You can use whatever directory you like, but you do, of course, have to create the directory.

* The name of each screenshot file is set by "%m.%d.%y at %H.%M.%S.png" and is the date and time the file was created . You can use whatever file name you like--look at the scrot man page for more options. 

* I save the screenshots in PNG format, but scrot supports other formats as well. Just change the file extension to reflect the desired file format.

* The -q 75 option determines the amount of compression. The default value--and the value I use--is 75.

That's it for the screenshot part. You should probably give it a try at this point to make sure all is working properly. Just press the PrintScreen key a few times and look for the files in the screenshots directory. 

The command line to view screenshots is:

```
feh --sort filename /home/username/screenshots/
```

This command can be invoked in various ways. The method described below utilizes a panel icon; you could also assign this command to a key using the configuration editor. 

As most of you know, the process to add an icon to a panel is:

1) Right click on the panel and select "add to the panel..." 

2) Click on the custom-application-launcher button. 

3) Give the icon a name, insert the command line from above, and, if necessary, change type to application. 

That's it for the viewer. Click on the icon you just created to view the oldest screenshot (feh will not start if there are not any files in the target directory). Use the right and left arrow keys to move through the screenshots. Do not use the page-up or page-down keys because the screenshots may not be viewed in their proper sequence and some may not be viewed at all. Use the cntrl-delete key combination to erase the currently-viewed screenshot file from your hard drive (bypassing the trash bin). 

Feh has many command-line options that allow you to customize how files are viewed. Just type "man feh" in a terminal window to view these options. 

I take and view screenshots a lot, so I found this procedure to be quite helpful, although it is limited in two respects. First, you cannot print a screenshot from within feh. You will have to use another program for this purpose. Secondly, the procedure described above produces a screenshot of the entire desktop. As presently released, scrot does not have the option to do a screenshot of the currently-active window without user intervention. A patch that will allow this is available but incorporating it into and compiling the scrot source code is beyond my abilities. 

By way of acknowleddgment, and as required by forum guidelines, please note that:

* Both scrot and feh were written by Tom Gilbert ([www.linuxbrit.co.uk](www.linuxbrit.co.uk)). I appreciate Tom taking the time to write these utilities. 

* The thread that prompted me to utilize scrot for screenshots is located at: [http://ubuntuforums.org/showthread.php?t=36323](http://ubuntuforums.org/showthread.php?t=36323)

* I am using Ubuntu 7.04, and the instructions contained in the HowTo have been tested only in Ubuntu 7.04.

* This HowTo is posted without promise of support.

---

