---
title: "HowTo: Install from a .bin file"
date: 2011-09-29
forum: New to Ubuntu
---

### Post by Trent T on 2011-09-29
Problem:
I obtained a software package for Linux in the form of a .bin file-- Call it NewApp.bin.  The directions that came with the file were;
1) download NewApp.bin
2) mark the file to enable running it as a program
3) install file using CLI, and follow the prompts.

I need a bit more detail, and I eventually came up with the following.
This is what I could have done, if I had known how at the time...

1) Downloaded the file, which left it in my 'Downloads' directory;
/home/MyUserName/Downloads

I moved the file to my home directory
/home/MyUserName/NewApp.bin

2) I right-clicked NewApp.bin file, selected 'Properties'
   Clicked the 'Permissions' tab, and checked 'allow eXecuting file as program,' then closed the properties box.

3) From the main menu (top right), I clicked Applications - Accessories - Terminal to start the Command Line Interface (CLI), then typed the following command;

bash NewApp.bin

and hit [enter].  

NewApp.bin then installed my New App.

I don't do this kind of installation very often - the Synaptic Package Manager has spoiled me !  So I am mostly leaving this as a note to myself so that, 3 years from now, I can look it up and know how to do it again.  

And hopefully, this info will be helpful to someone else too :)

---

### Post by StevoSn on 2011-09-29
Hey!

in essence:
download, change permissions via chmod 777 /path/file.bin and run the bin file via /path/file.bin

Cheers!
Stevo


----
well, I should read before posting.. :-)

---

### Post by thenudehamster on 2011-10-10
> **Trent T said:**
> And hopefully, this info will be helpful to someone else too :)

And was it ever! 
I found similar advice somewhere on the net a few months ago when trying to install the device manager software for an NAS device (the manufacturer's website gave installation instructions for PC and Mac, but assumed Linux users know all about every install method under the sun - and their machine uses a modified Linux distro to operate!) and when I had to rebuild one of my machines, could I find the information again? Could I 'eck!

Your information was very handy, as was Stevo's addition. On that score, Stevo, does "chmod a+x *filename*" work as well as the '777'? My memory says that's what the original info I used said, but I was reluctant to try it unverified as incorrect commands can often do a lot of damage...

---

