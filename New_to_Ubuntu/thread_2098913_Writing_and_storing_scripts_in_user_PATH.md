---
title: "Writing and storing scripts in user PATH?"
date: 2012-12-28
forum: New to Ubuntu
---

### Post by ACuriousGuy on 2012-12-28
Hello. Looking for help for a newbie (even though I've been using it for awhile). I have recently re-installed Ubuntu 12.10 using WUBI after many problems/no solutions to my browser issue. Anyway, after the install/update I went ahead and downloaded the KDE desktop. I figured I would play with both and see which I liked.

I wanted to change the default media player in KDE to Dragon. But after Googling it I found that if I did that, when I relaunched in Gnome, I would be using the Dragon player instead of VLC. Then I found [this link which described how to have different programs as the default choice depending on which environment you're using]("http://askubuntu.com/questions/182920/setting-different-default-applications-for-different-desktop-environment") (Gnome, KDE, etc). My first thought was "AWESOME!"

But then I realized I didn't know how to do what it was suggesting. The first step says "save custom-open script on your computer preferably on your path but doesn't have to be."

??? I have zero idea on how to "write" a script (what program do I use?). And zero idea on how to put it in my "path." Where/how would I write that and where would I store it so that it is in my "path?"

The next step is "save .custom-open.ini in your home directory ~/.custom-open.ini" ... OK. Please read my first question. I have no idea on how/where to write it. I'm guessing by "home directory" it means the directory where my default stuff is (pictures, etc).

And step three is "set custom-open as the default application for any file types you want handled by it." That is what I was trying to learn in the first place. How do I set a file type to automatically be opened by a certain program. 

This script has gotten a number of praises and seems to do what everyone wants. I just have no idea on how to go about it.

If anyone can offer so easy, step-by-step examples of how to write a script and store it in the proper directories it would be SOOOOOOOOO very much appreciated.

Thank you in advance for any and all help that you can give. I've been a member for awhile but am still so very, very new. Thanks.

---

### Post by audiomick on 2012-12-28
To write a script, use the text editor. A script is generally just a text file. The standard text editor on Ubuntu is gedit. On pre-unity versions, it is in the accessories menu. On unity, search gedit in the dash. Or open a terminal and type 
```
gedit
```. 

If you ever get to the point where you want to operate on text files that belong to root, you need an instance with root privileges. Use
```
gksudo gedit
```

Having said that, you wrote
> The first step says "save custom-open script on your computer preferably on your path but doesn't have to be."
which suggests that there was a file being offered on that site with a finished script. Or was it written out there, and you would have had to cut and paste it into the text editor to save as a .txt file on your machine?

If you want to point something at the script to have it run as seems to have been described in the instructions you are following, I think you would have to mark the file as executable. I'm not sure about that, as I have only dabbled with that stuff once or twice. Anyway, right click on the file, choose properties. On the "permissions" tab, set a tick in the box to make the file executable.

While you are there in properties, look at the tab "open with". That is where you set the default program to be opened with a particular file type.

I'm a bit hazy on "path". I know roughly what it is: when you type a command in your terminal that starts a program, there is a list of places that the system goes off to and looks for the program in. That is the gist of it.

If I understand things correctly, there is a path that the whole system uses. I suppose you could theoretically go into that, but I gather the thing to do is add someting user related. I think this is the right instructions for doing that. It basically adds something to your user profile that says "and also, go and look here".
[http://askubuntu.com/questions/141718/what-is-path-environment-variable-and-how-to-add-it]("http://askubuntu.com/questions/141718/what-is-path-environment-variable-and-how-to-add-it")

Hope that is of some help to you.

---

### Post by coldcritter64 on 2012-12-28
Your current system path can be checked in a terminal (ctrl+alt+t keyboard combination), with the code (which can be copied and pasted directly into a terminal from your browser window),
```
echo $PATH
``` the capital letters are necessary for the environment variable $PATH.

To add a user folder for scripts, create a "bin" folder in your home directory. Copying/pasting the following code into a terminal will do so for you,
```
mkdir ~/bin
``` the ~ symbol is a system variable for your home folder. This makes the /home/<your-username>/bin folder.

Now to use the bin folder, log out of and then log back into your desktop session. 

Run the "echo $PATH" command above and you should see your /home/<your-usnrname>/bin folder in the system path. 

Any script you generate in gedit as audiomick mentions, should be stored here, and are launchable by name in terminal if marked as "executable" permissions wise.

Edit2:  :) cheers 'Mick (post #4, next)

---

### Post by audiomick on 2012-12-28
Well, I'll be jiggered. That works. ;)

Thanks for the explanation, coldcritter. ):P

---

