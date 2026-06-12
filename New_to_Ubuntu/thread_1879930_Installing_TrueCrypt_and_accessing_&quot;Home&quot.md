---
title: "Installing TrueCrypt and accessing &quot;Home&quot; decryption code"
date: 2011-11-12
forum: New to Ubuntu
---

### Post by bedpotato on 2011-11-12
Hello! Please can somebody help me? I am an absolute beginner at Linux and being sick of viruses and Windows in general I have just installed Ubuntu 11.10 via CD onto my Acer Aspire 5735 laptop. For the moment I have kept my Windows there alongside it, until I get things figured out. Not being the most knowledgeable sort of person when it comes to computers, I am finding it all rather fascinating trying to get things figured out, because I love learning new things. It's all so much more "hands on" than Windows!

It's all up and running but here are my main two problems so far: I want to install my beloved TrueCrypt, which I've got over on Windows, but when I try and download the Linux version, I am not sure if I should select 32 or 64 bit option. I do not really know what "bits" are. I tried both, but neither of them worked and just froze up when I tried installing them. In this thread here it says I need to "unpack" them. What does that mean, please, and how do I do it? Clearly, installing software is far more complex than just a simple click like you can do with Windows, but I don't mind because I'm learning a lot in the process.

[http://ubuntuforums.org/showthread.php?t=1861455](http://ubuntuforums.org/showthread.php?t=1861455)

Also, when installing Ubuntu I ticked the option for it to encrypt my "Home,"  and once launched for the first time, Ubuntu popped up with a window saying it had generated a random "Home" encryption password that I would need to access and note down in case I ever needed to access it manually. It told me to type in my user password to get to the encryption password, but when I tried typing it in, nothing happened. The cursor just kept flashing and it did not register my typing. How do I get to it, please?

As you can see I am not very savvy, but all I want my laptop for is surfing the net, uploading my photos, drafting and printing the occasional document, and updating my iPhone, so once I get to know how things work, it shouldn't be too hard - right? My only reservation is that I have not yet found out if iTunes will run on Linux or whether my printer drives will work, but if they do, then hopefully I can just delete Windows and never go back to it again! Hooray! (I actually hate iTunes and never use it for listening to music but it's a necessary evil for updating one's phone).

---

### Post by carranty on 2011-11-12
Where are you trying to download the linux version of truecrypt from?  The simplest way is to open a terminal and type
[I]
sudo apt-get install truecrypt

[/I]That will install the correct version for your architecture*.  *There are two ways to open a terminal.  The first is to click on the Dash icon and then search for terminal, then click on the 'Terminal' icon. The other is to press Ctrl + Alt + T.

As for 32 or 64bit, when downloading the ubuntu iso you had a choice of Ubuntu 32bit or Ubuntu 64bit.  64bit is usually run on higher spec computers as 32bit can only use around 4GB of ram (I'm not sure of the exact figure), no matter how much you actually have installed.  However since most people use the 32bit version, its better supported (programs sometimes don't work so well in the 64bit versions).  To see which you have open a terminal again and type[I]

uname -m

[/I]If the response is i686, you have 32-bit Ubuntu. If t says x86_64, you have 64bit.

I'm not sure about the second question, I've never encrypted my home folder.

---

### Post by bedpotato on 2011-11-12
Thank you very much for your advice. 

I was trying to download it from [http://www.truecrypt.org/downloads](http://www.truecrypt.org/downloads) Should I have been doing it via somewhere different?

When I tried typing what you said about Truecrypt into a terminal, it said:

[B]Package truecrypt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'truecrypt' has no installation candidate[/B]

When I typed in what you said about the bits, it said:

**i686**

so I have 32 bit then. Thank you. :)

Regarding the encryption: I suppose I don't really need it, since I plan to create encrypted TrueCrypt partitions to keep my stuff in anyway. I am just a very paranoid person so I thought "the more encryption the better" so when I saw the box giving me the option to encrypt my Home, I ticked it. Having something encrypted and not knowing the password for it is not very desirable though. (That's an understatement)! Does anyone know if I can change it back to normal, or is it too late? Thank you. :)

---

### Post by carranty on 2011-11-12
> **bedpotato said:**
> 
When I tried typing what you said about Truecrypt into a terminal, it said:

[B]Package truecrypt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'truecrypt' has no installation candidate[/B]


Huh, you're right.  I guess it's not in the repositories. So....

Go to the site your using ([http://www.truecrypt.org/downloads](http://www.truecrypt.org/downloads)) and download

[I]standard - 32 bit (x86)

[/I]Make sure you click 'Save File' rather than 'Open With'.

It comes as a tar.gz file, which is rather like a windows zip or rar file.  You'll need to unpack it.  To do this again go to your terminal and navigate to whatever directory you downloaded* the file into then  type
[I]
tar -xzvf truecrypt-7.1-linux-x86.tar.gz[/I]

writing

[I]tar -xzvf tru

[/I]and then pressing tab should also work (autocompletion saves time).  Now its unpacked, but you still need to run it.  Do this by typing

[I]./truecrypt-7.1-setup-x86 

[/I]into the terminal.  You should now get the install wizard, and can install it fairly easily.

After installation, type 

[I]truecrypt

[/I]into a terminal and it should run.

* For example if you downloaded it to your 'Downloads' directory you'll need to type *cd ~/Downloads* in the terminal

---

### Post by cottfcfan on 2011-11-12
Its much easier just to right click the tar.gz package and "extract here".
Then double click the file that's extracted and follow the on screen instructions.

---

### Post by carranty on 2011-11-12
> **bedpotato said:**
>  It told me to type in my user password to get to the encryption password, but when I tried typing it in, nothing happened. The cursor just kept flashing and it did not register my typing. How do I get to it, please?


Ah, unlike in Windows, when you type a password into a command prompt in Ubuntu (or any flavour of linux for that matter) the cursor doesn't respond.  I think this is a security measure to prevent people who may be looking over you're shoulder how many characters you're password has.  It flummoxed me at first. Anyway, had you typed in your password and pressed Enter, it probably would have worked fine.

---

### Post by Norm24 on 2011-11-12
Or why not download Easycrypt from the repos?

---

### Post by bedpotato on 2011-11-12
> **carranty said:**
>  go to your terminal and navigate to whatever directory you downloaded the file into 

How do I do that, please?  

Gosh, this is fascinating, but it's all Greek to me. (All this computer code I have to type in, I mean). In Windows all you had to do was click on a button, but here there are no buttons and you have to talk to the computer in computer language instead! :) (which is what Windows is actually doing behind the scenes when we click on those buttons, I suppose)!

Is there a link to somewhere where I can find out common commands that I will need to type in and memorise them rather than coming on here and asking for help every time I need to do ANYTHING?  

I am very grateful for your help. It is nice of you to help an ignorant, humble newbie.:oops:

---

### Post by bedpotato on 2011-11-12
> **Norm24 said:**
> Or why not download Easycrypt from the repos?

Because I already have an encrypted USB with my stuff on. I encypted it with TrueCrypt. Will Easycrypt be compatible with it? :confused:

Thanks to everyone for their replies!. :)

---

### Post by Norm24 on 2011-11-12
> **bedpotato said:**
> Because I already have an encrypted USB with my stuff on. I encypted it with TrueCrypt. Will Easycrypt be compatible with it? :confused:

Thanks to everyone for their replies!. :)

Supposedly Easycrypt is compatible.

---

### Post by carranty on 2011-11-12
> **cottfcfan said:**
> Its much easier just to right click the tar.gz package and "extract here".
Then double click the file that's extracted and follow the on screen instructions.

Quite possibly.  There are always two ways to do things in Ubuntu, either by using the GUI (as in Windows) or using the command line.  Learning the command line was one of the things that drew me to Ubuntu in the first place, and now I find it easier to do most things from it.  It takes less than 5 seconds for me to navigate to, unpack and run a file from the terminal, so for me its easier that way.  But its really a matter of opinion.

---

### Post by carranty on 2011-11-12
> **bedpotato said:**
> How do I do that, please?


To change directory in the terminal you use the cd command.  Say I want to navigate to my Pictures folder.  I type

*cd /home/carranty/Pictures*

At first, it takes longer to use the terminal, as there appears to be a lot to type but I could also navigate there by using the shorthand

*cd ~/Pictures*

The computer knows  that by ~/ I mean /home/carranty.  To be even quicker I could type

*cd ~/P*

and then press the tab key, it would then autocomplete the command for me.

You've most likely saved the file to your Downloads folder, so you'll need to type

cd /home/[your username]/Downloads


Also, and this is getting a bit ahead of the post now, you don't really need to even go to the directory, you could pass the location to the tar program as you run it

tar -xzvf ~/Documents/truecrypt-7.1-linux-x86.tar.gz

or even

tar -xzvf ~/Do[TAB]tru[TAB]

where by [TAB] I mean press the tab key.  This is why I said earlier that to me, using the terminal is easier and quicker.

---

### Post by fleamour on 2011-11-12
As for recovering encryption passphrase, type the following into the black terminal window:

```
ecryptfs-unwrap-passphrase
```

Hopefully you'll never need it.

---

### Post by bedpotato on 2011-11-12
> **cottfcfan said:**
> Its much easier just to right click the tar.gz package and "extract here".
Then double click the file that's extracted and follow the on screen instructions.

I am going crazy trying a million ways to install it once extracted, but it keeps coming up with an error message in the terminal window. :(

---

### Post by carranty on 2011-11-12
> **bedpotato said:**
> 
Is there a link to somewhere where I can find out common commands that I will need to type in and memorise them rather than coming on here and asking for help every time I need to do ANYTHING? 


There's a free book here that I found very useful when starting out

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

---

### Post by carranty on 2011-11-12
> **bedpotato said:**
> I am going crazy trying a million ways to install it once extracted, but it keeps coming up with an error message in the terminal window. :(

Ok run the command in the terminal, let it spit out the error message and then copy and paste the whole thing (command AND error message) into this thread.

---

### Post by bedpotato on 2011-11-12
> **carranty said:**
> Ok run the command in the terminal, let it spit out the error message and then copy and paste the whole thing (command AND error message) into this thread.

Yes, I already tried doing that, but it won't let me copy and paste. I am used to using CTRL + C as second nature, or right-clicking and selecting copy, but when I tried to select and copy the text in the terminal, it froze and things jammed.

I may have to do a screenshot instead.

I dare say I will get used to this eventually! :lol:

---

### Post by carranty on 2011-11-12
> **bedpotato said:**
> but when I tried to select and copy the text in the terminal, it froze and things jammed.


That's odd.  A screenshot will be fine.

---

### Post by cottfcfan on 2011-11-12
Bedpotato.
You don't need to use the Terminal.
Just follow my above post.

---

### Post by cottfcfan on 2011-11-12
Sorry I can see your new. Let me run through it step by step.
1. Download the standard tar.gz package to your Home folder from here:
[http://www.truecrypt.org/downloads](http://www.truecrypt.org/downloads)
2. Go to your home Folder find the package, Right click, and "Extract here".
3. An extracted package will appear, Double click, and follow online instructions.
4. Truecrypt is now installed.
5. The Application can be started from Accessories.

---

### Post by bedpotato on 2011-11-12
> **cottfcfan said:**
> Bedpotato.
You don't need to use the Terminal.
Just follow my above post.

I am not "using the terminal" in the sense of starting out at it, but it always ends up there! When I click on Install TrueCrypt now, it then asks me for my password for permission to proceed, and then comes up with (what I think is) a terminal window, explaining why it can't install it. When I try and copy that text to post here, it crashes all my windows in the sense that I cannot access the little window icons to close, minimise, or maximise anything. I can shift from one window to another using Alt and Tab, but can't actually DO anything. Everything freezes and jams. All that works is doing CTL, ALT DELETE and logging out and logging back in again. I have done this several times now and am getting very tired so I will give things a break. I don't know what on earth I'm doing wrong; it's all totally new to me and I'm way out of my depth! At least I have noted down my encryption password thanks to advice on this thread, so that's one out of two! Oh, and I tried downloading the other encryption app said to be compatible with Truecrypt, but it said something along the lines of "this is not available via your current sources."

Thanks everyone.

---

### Post by carranty on 2011-11-12
By following cottfcfan's advice in the previous thread, installation of truecrypt should be fast and painless.  It seems there is a larger problem with your installation thats causing you all this hassle.  Sometimes fresh installations just don't 'take', are you trying Ubuntu 11.10.  If things are still playing up tomorrow, and we can't resolve them in the forum, you may want to try the more stable 10.04 version.

I'm sorry this has happened on your first foray into the world of Linux :(, stick with it though, its well worth it!:)

---

### Post by bedpotato on 2011-11-12
Thank you for your kind words. Maybe I just did something terribly wrong without realising it. 

I wish there was somebody here to help. :( I do not know anyone who would be able to help me in real life.

---

### Post by carranty on 2011-11-12
I sympathise, perhaps you can take a photo of the error message, and upload it here?  It really is very difficult for people to advise you on the best course of action without knowing exactly what's wrong

---

### Post by bedpotato on 2011-11-12
[img]http://my.picresize.com/vault2/SAI8B9TWU9.jpg [/img][IMG]http://my.picresize.com/vault2/SAI8B9TWU9.jpg%20[/IMG]

---

### Post by carranty on 2011-11-12
OK, that helps a lot.  Try running the below in a terminal

*sudo apt-get install gtk2-engines-pixbuf*

Hopefully that'll sort you out.

---

### Post by bedpotato on 2011-11-13
Thank you! It seems to have worked now, although now I'm having other weird glitches (such as the curser not responding AT ALL and having to reboot via the off button).  But Truecrypt has installed now, so I will mark this thread as resolved and go off and start other ones if need be! 

Thank you to everyone who replied to this thread and tried to help me out. :)

---

