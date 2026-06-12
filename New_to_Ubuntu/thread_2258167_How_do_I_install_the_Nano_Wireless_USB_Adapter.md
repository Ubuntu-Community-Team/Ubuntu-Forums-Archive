---
title: "How do I install the Nano Wireless USB Adapter?"
date: 2014-12-25
forum: New to Ubuntu
---

### Post by Noah_Kiger on 2014-12-25
Please walk me through this like I'm a five year old, I'm very new to Ubuntu and I've been having issues with installing my Nano Wireless USB Adapter. Whenever I try to open the install folder it says Archive type not found.

---

### Post by Kagrabular on 2014-12-25
Hello there Noah_Kiger, 

What is the filename extension (ie. "filename.rar" .rar being the extension type associated with Windows)? Typically this dialogue appears when you attempt to open an archive extension that is not supported, or has perhaps been mislabeled. An "install" program for Linux looks different than Windows or Mac, and often you must run a script or simply run the source. Typical archive formats for Ubuntu include; "filename.tar"  "filename.gz" "filename.bz2"

---

### Post by Noah_Kiger on 2014-12-25
> **Kagrabular said:**
> Hello there Noah_Kinger, 

What is the filename extension (ie. "filename.rar" .rar being the extension type associated with Windows)? Typically this dialogue appears when you attempt to open an archive extension that is not supported, or has perhaps been mislabeled. An "install" program for Linux looks different than Windows or Mac, and often you must run a script or simply run the source. Typical archive formats for Ubuntu include; "filename.tar"  "filename.gz" "filename.bz2"

The file i first run into in the Linux folder for the driver is a .bz2, but inside the .bz2 I run into an unknown file type, which is where I find the error mention earlier.

---

### Post by Kagrabular on 2014-12-25
.bz2 is a compression archive format (think a .zip file in Windows if you're familiar). You can enter the file, but in order to work with it you must expand it first. To do this you will run: bzip2 -d "filename".bz2 (please note that this will not preserve the original file. If you wish to keep a copy of both add a 'k' after the -d for example; bzip2 -dk "filename".bz2)

---

### Post by Noah_Kiger on 2014-12-25
> **Kagrabular said:**
> .bz2 is a compression archive format (think a .zip file in Windows if you're familiar). You can enter the file, but in order to work with it you must expand it first. To do this you will run: bzip2 -d "filename".bz2 (please note that this will not preserve the original file. If you wish to keep a copy of both add a 'k' after the -d for example; bzip2 -dk "filename".bz2)

Sorry, I lost you at "you will run"

---

### Post by Kagrabular on 2014-12-25
No worries, I apologize for not being more clear.  

Open up a terminal in Ubuntu, it is usually on the sidebar by defualt, but you can search for it by clicking in the upper portion of the sidebar and using the search function, simply type in 'terminal'. When it comes up you will see your username and host name something like this 

"User@Host:~$" 

you will also see a blinking cursor mark. In that terminal type "bzip2 -d thenameofyourfile.bz2" without the quotation marks, substitute 'thenameofyourfile' for the actual name of the bz2 file you wish to decompress. It should decompress the file in the same directory ('folder') where it is already stored. You will then have access to the contents. When you get there let me know the contents of the file and I can help you from there.

it will look something like this;

user@host:$ bzip2 -d thenameofyourfile.bz2

Then press enter.

---

### Post by Noah_Kiger on 2014-12-25
> **Kagrabular said:**
> No worries, I apologize for not being more clear.  

Open up a terminal in Ubuntu, it is usually on the sidebar by defualt, but you can search for it by clicking in the upper portion of the sidebar and using the search function, simply type in 'terminal'. When it comes up you will see your username and host name something like this 

"User@Host:~$" 

you will also see a blinking cursor mark. In that terminal type "bzip2 -d thenameofyourfile.bz2" without the quotation marks, substitute 'thenameofyourfile' for the actual name of the bz2 file you wish to decompress. It should decompress the file in the same directory ('folder') where it is already stored. You will then have access to the contents. When you get there let me know the contents of the file and I can help you from there.

it will look something like this;

user@host:$ bzip2 -d thenameofyourfile.bz2

Then press enter.

I know I type in the file name exactly as it is, but the terminal responds with "No such file or directory."

---

### Post by Kagrabular on 2014-12-25
Okay, this is my fault. I failed to mention that you need to make sure you are in the correct place in the terminal. By default your terminal typically places you at home or the "$" in user@host:$



In order to get to the right place you need to know where the file is located. Is it located in Downloads? Home? Documents? Where do you go in order to 'physically' click on the file?

find the name of that folder or 'directory' and change your location to that in order to access it. 

To change to a different directory type;

user@host:$ cd "nameoffolder" 

To make it easier to remember cd stands for 'Change Directory'

For example if your bz2 file is located in 'Downloads' you will type

user@host:$ cd Downloads

your terminal will now look like this 

user@host:~/Downloads$

Now to list what is in this directory (to make sure it's where your bz2 file is) type 'ls' like so:

user@host:~/Downloads$ ls

This will give you a list of all the contents of this directory. 
Once you are in the correct directory follow the steps listed in my previous post to decompress the file.

---

### Post by Noah_Kiger on 2014-12-25
> **Kagrabular said:**
> Okay, this is my fault. I forgot to mention that you need to make sure you are in the correct place in the terminal. By default your terminal typically places you at home or the "$" in user@host:$



In order to get to the right place you need to know where the file is located. Is it located in Downloads? Home? Documents? Where do you go in order to 'physically' click on the file?

find the name of that folder or 'directory' and change your location to that in order to access it. 

To change to a different directory type;

user@host:$ cd "nameoffolder" 

To make it easier to remember cd stands for 'Change Directory'

For example if your bz2 file is located in 'Downloads' you will type

user@host:$ cd Downloads

your terminal will now look like this 

user@host:~/Downloads$

Now to list what is in this directory (to make sure it's where your bz2 file is) type 'ls' like so:

user@host:~/Downloads$ ls

This will give you a list of all the contents of this directory. 
Once you are in the correct directory follow the steps listed in my previous post to decompress the file.

When I try to change the directory, no matter what file I try to direct it to it says "No such file or directory".

---

### Post by Kagrabular on 2014-12-25
Are you trying to direct it to a file or a directory (you can visualize these as 'folders')?

You can only 'cd' to a directory. So make sure you are in a place where you can see that directory. Typing 'ls' will give you all available directories from your current location. 

If 'Downloads' is not listed, you may be in a place where you cannot immediately access that directory. To go back to the default directory simply type 'cd' and nothing else in the terminal.

If you would like I can help you further if you;

In terminal type only : ls

user@host:~$ ls

and tell me what is listed.

You can just copy and paste from the terminal to here if you wish.

---

### Post by Noah_Kiger on 2014-12-25
> **Kagrabular said:**
> Are you trying to direct it to a file or a directory (you can visualize these as 'folders')?

In terminal type only : ls

user@host:~$ ls

and tell me what is listed.

You can just copy and paste from the terminal to here if you wish.

Desktop, documents, downloads, examples.desktop, music, pictures, public, templates, videos

The folder in which the file is located in is under devices, then a folder named Linux.

---

### Post by Kagrabular on 2014-12-25
Also, it sounds like you could benefit from some very beginning tutorials. You have Ubuntu installed obviously, so learning how to use the terminal should be your next priority. There are plenty of resources out there if you search for beginning tutorials. 

If you copy and paste "Guide to Unix using linux filetype:pdf" into google without the quotation marks literally the first listed item is a pretty good beginners guide from the very beginning on using the terminal.

---

### Post by Kagrabular on 2014-12-25
If it is under devices that means you are trying to access a folder that is in the usb adapter? For example, if you clicked on 'files' on the toolbar you would see a list of various things and then a category for 'devices' and under it you would see your usb adapter? You click on that and then you see the folder 'linux'?

---

### Post by Kagrabular on 2014-12-25
I have to leave soon, but try these steps to get to the folder, and then use previous posts to uncompress the bz2

In order to change to the directory where the device is held you need to know the name of the device. 
Type;

user@host:~$ cd

Then type 


user@host:~$ cd /media

it will look like this;


user@host:~/media$

then type

user@host:~/media$ ls

in Ubuntu you should see your user name as the only thing listed. Type;


user@host:~/media$ cd 'username'

It will look like this now;

user@host:~$/media/username$ 

Then type;

user@host:~$/media/username$ ls

Find the name of the device you wish to access (your usb adapter) and type

user@host:~$/media/username$ cd 'nameofadapteraslisted'

Then type; 'ls' to find the folder 'linux'
Then type; 'cd linux'
type: 'ls' to list the contents of the folder
once you see the file filename.bz2 you can now decompress it using the aforementioned steps.

You can use these steps and the basic tools provided to navigate wherever you may need to go. Make use of the guide I pointed you to as well. 
I'll try and answer questions as I can.

---

### Post by Mike_Walsh on 2014-12-25
@Kagrabular:-

Excuse me, but I'm trying to get my head round this... Isn't it expecting a bit much for a beginner to jump straight into 'heavy' terminal stuff? Granted, it's very much faster WHEN you know what you're doing, but..... :-k

I know we're talking about Linux here, but Canonical have been going out of their way to ensure that Ubuntu is 'user' friendly these days... Newbs shouldn't expect to have to do much more than copy/paste with the terminal in the early stages! 

Linux is no longer JUST for 'geeks'. BTW, please don't take offence at this; I'm well aware that unlike me, not everybody has 30+ years of experience with these things.....

@Noah:- 

What model of wireless adapter are you using? I take it you're just trying to connect to the internet, yes? Or are you attempting to do something else with the software installed in the adapter?

We would also benefit from knowing what model of computer you're using, CPU, RAM, graphics card, that kind of thing. It makes it easier to decide what the next step should be, you see.

Could you post the output of

```
lshw
```

(This LITERALLY means '**l**i**s**t **h**ard**w**are'.)



In Linux, you don't very often have to install drivers; the kernel of the operating system contains just about every driver ever released, and it is updated very regularly. It would have to be VERY old hardware indeed, not to be supported. Things DO take a wee bit of getting used to in Linux..!

Regards,

Mike. ;)

---

