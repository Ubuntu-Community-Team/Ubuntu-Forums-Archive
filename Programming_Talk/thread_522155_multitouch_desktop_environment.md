---
title: "multitouch desktop environment"
date: 2007-08-10
forum: Programming Talk
---

### Post by bigbang on 2007-08-10
[SIZE="3"] Abstract [/SIZE]
I have been thinking of a desktop environment for a couple of months now that uses Multitouch and is very uniform in the way it handles applications. The desktop environment would run on tables similar but smaller than the Microsoft surface tables. Projects to make DIY tables like these are quite advanced so making one shouldn&#8217;t be too difficult. The idea is that within the environment, all applications would have no buttons and be interfaceless (at least the main part of the applications) tools would be used by performing gestures.
[SIZE="3"] Description [/SIZE]
** Desktop **
The desktop is the place where all the application are held. It also acts as a file manager. The desktop starts with an applications icon a files icon and a root icon making the Ubuntu circle, plus all the drives (not including the hard drive) floating around it. It is important to note that the desktop is infinite and can be scaled with a scaling gesture with two fingers touching it. It can also be moved and rotated by using one or two fingers.
When you click one of the icons it will open up all the files and folder it contains by having them expand in circles around the icon pushing the other icons out of the way. Clicking on folders does the same thing. A file is a picture of the file in its last state. Clicking a file or one of the 3 icons will make it absorb all its files and folders again (allowing the icons pushed to go back to there places). To keep a file or folder out you keep one finger on it while pressing the folder/icon (the icon still belongs to that folder even though it is kept out so it will go back into the folder when you shut down the computer). To move a file/folder into a new folder you simply drag it on to it.
Files and folders can be dragged, rotated and rescaled in the same way as the desktop.
** the App Folder **
Inside the app folder there are blank files of each type of application on the computer. These can be organized into folders if wished.
** the Root and Files Folder **
The root icon leads to the root directory and files to the home directory.
** the Main App Section **
This is the part of the file that is shown as an image on the desktop. To activate and application from the picture found on the desktop you have to pin the picture. This prevents the application from moving so that its application specific gestures can be used on it and it converts the image it was up to this point into the actual application by loading the program then loading the file and placing it exactly the same place as the image was.
When pinned the gesture option panel is opened next to the main app section.
The main app section should contain no buttons unless it is an application that requires them such as a calculator app (which incidentally cant be saved so can only be opened by navigation through the app icon to its blank state picture).
An application closes, and returns to just being a picture representation of itself, not when it is unpinned but when it is unpinned and returned to the closed folder from which it came.
** the Gesture Option Panel **
The gesture option panel can be moved, rotated and scaled and carries the options for each tool currently assigned to each gesture. It is specific to each app currently pinned. It is similar in function to the option panel sported by all the macromedia applications. The options it contains can be collapsed to a vertical column and expanded to a horizontal header with text and text boxes underneath.
** Gesture Assignment Options **
These options control which tools are assigned to which gestures and how the gesture affects the tool. And example of this would a rescale tool assigned to a two-finger motion. The layout of this panel is similar to the gesture option panel.
To access this panel you have to make a two fingered flipping motion on the gesture option panel. This flips the panel revealing the gesture assignment options panel.
** Application Options **
The application options are laidout in the same style as the other options but affect all the options of the applications (but not its gestures).
To access this you must unpin the application and flip it in the same was as the gesture option panel.
** Pinning **
To pin an application you must tap twice with two fingers on the application. Doing the same gesture on a pinned app unpins it.
** System Options **
Flipping the desktop in the same way as everything else accesses the system options. These options are laid out in the same way as the other options but they have sub categories, as well, to expand. 
** Notification **
Notification would be done with transparent symbols that appear around the boarder of the screen and can be click on to send you to a place in the options or open a blank application.
[SIZE="3"] GTK compatibility [/SIZE]
I wanted this desktop environment to be compatible with GTK so that programs don&#8217;t have to be rewritten.
** Tools and App Options **
The app options are the windows that can be opened from the file, edit &#8230; buttons at the top of an application (the ones that end with `&#8230;`). Tools are all the other things in file, edit&#8230; menus. The tools can be assigned to gestures using the gesture assignment options.
** Gesture Option Panel **
Here I am not sure what I could use from the GTK libraries to make these options.
[SIZE="3"] Mock Up [/SIZE]
I am going to make a video mock up but I want to know what applications people would like me to show in the mock up (e.g. Firefox, the Gimp). And secondly, what is the best application in Ubuntu to do this (I can always resort to flash).
[SIZE="3"] My Big Fat Problem [/SIZE]
I am only just learning to program in c++ so I don&#8217;t think I would be able to put these ideas into action. Is there a way of working this idea?

---

### Post by Nekiruhs on 2007-08-10
[How to get people to work on your project]("http://www.somethingsimilar.com/wordpress/2007/08/06/how-to-get-your-project-moving-or-my-ego-is-massive-and-you-should-listen-to-me/")

---

### Post by pmasiar on 2007-08-10
I played a game years ago where mouse had gestures: when you swipe over an object horizontally you had different menu as when swiped vertically, and menu was *around* the object, not box aside, so there was less mouse moving to accomplish everything. Very neat.

But.... creating the whole desktop is hundreds, if not thousands of man-years of work, so it will not be easy.

Read link above, learn programming, participate in GNOME or KDE so you will learn how smart people designed desktop. Years from now, when your name will be well known and regarded in community, you can start that project, and people  might join you and help you. If you will start alone, for reasons mentioned in the link in previous comment, nobody will notice untill you have something usable. Getting something usable by coding alone is years of work, you will burn out (or retire :-) ) before first alpha release.

BTW, look at Python: Sugar (desktop for "one laptop per child" project) is in Python. It does not *have* to be in C++, even if KDE and GNOME are.

---

### Post by slavik on 2007-08-10
> **pmasiar said:**
> I played a game years ago where mouse had gestures: when you swipe over an object horizontally you had different menu as when swiped vertically, and menu was *around* the object, not box aside, so there was less mouse moving to accomplish everything. Very neat.

But.... creating the whole desktop is hundreds, if not thousands of man-years of work, so it will not be easy.

Read link above, learn programming, participate in GNOME or KDE so you will learn how smart people designed desktop. Years from now, when your name will be well known and regarded in community, you can start that project, and people  might join you and help you. If you will start alone, for reasons mentioned in the link in previous comment, nobody will notice untill you have something usable. Getting something usable by coding alone is years of work, you will burn out (or retire :-) ) before first alpha release.

BTW, look at Python: Sugar (desktop for "one laptop per child" project) is in Python. It does not *have* to be in C++, even if KDE and GNOME are.
even Solaris 10 doesn't use C or C++ for the GUI (it's Java)

---

### Post by bigbang on 2007-08-10
i have a feeling that this is something that people are really looking for at the moment. so if i do start the project like the link says and make some videos and so on, then i recon people might come to the project from the comunity drawn to the diy multitouch tables. maybe there is a better place to put this. the main object of the post was find out peoples thoughts on the idea and what programs to display in the video and which to use to make it.

---

### Post by pmasiar on 2007-08-10
> **bigbang said:**
> i have a feeling that this is something that people are really looking for at the moment. so if i do start the project like the link says and make some videos and so on,... .

Hardly video will be enough. Maybe some coder might start *his own* project inspired by your video. You obviously did not read the link in comment #2

---

### Post by Steveway on 2007-08-10
There is MPX.
[http://wearables.unisa.edu.au/mpx/](http://wearables.unisa.edu.au/mpx/)
It allows for use of multiple Inputdevices while each has its own cursor and it supports Multitouchtablets.
We should first focus on the technical level and get that into Xorg, development is going very well recently.
After this is figured out we can focus on those usability things.

---

### Post by bigbang on 2007-08-11
> **Steveway said:**
> There is MPX.
[http://wearables.unisa.edu.au/mpx/](http://wearables.unisa.edu.au/mpx/)
It allows for use of multiple Inputdevices while each has its own cursor and it supports Multitouchtablets.
We should first focus on the technical level and get that into Xorg, development is going very well recently.
After this is figured out we can focus on those usability things.
that sounds very good in deed. i think once that is put into the xserver it will make my project much easier.
> Hardly video will be enough. Maybe some coder might start *his own* project inspired by your video. You obviously did not read the link in comment #2
i wasnt going to stop at the video. i was going to make it first so that i have something clear about the objective. then i was going to start coding it as soon as i have finished reading a c++ book i got from the library. i know it will be tough but im going to try any way and see how it goes. either way, it will be good coding practice.

---

