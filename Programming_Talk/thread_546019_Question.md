---
title: "Question"
date: 2007-09-08
forum: Programming Talk
---

### Post by xiownthisplacex on 2007-09-08
Hi. This is not a particular question about ubuntu, but, I have made a windows program, a bitclient and I want to know how I can compile it to make it work in linux, can anyone help me? Thanks in advance.

---

### Post by Tomosaur on 2007-09-08
> **xiownthisplacex said:**
> Hi. This is not a particular question about ubuntu, but, I have made a windows program, a bitclient and I want to know how I can compile it to make it work in linux, can anyone help me? Thanks in advance.

That depends on what language it's coded in, what libraries you used, so on and so forth. If you didn't create it using Windows specific APIs and libraries, then chances are you will be able to port it to Linux with the minimum of fuss.

Be warned, however - you should check the licence on the libraries you've used. If you've used the Windows SDK, then you're probably out of luck. If you've used GPLd libraries or some other library which is available for Linux, then yes, it should be possible.

What you need is a cross compiler. The GNU compilation tools are able to compile for other platforms, but the easiest method is to just compile it **on** Linux.

So what language etc did you use? Do you have the sources to hand, in which case can you just post them here, or provide a link to the website or whatever?

---

### Post by xiownthisplacex on 2007-09-08
i modified bittornado's source into my own bitclient, it is in python, i haven't really finished it yet, because i am not the only one working on it, just need some little adjustments. when its completely done, i will post here the source code so you can see, but if you want to check it out already you can get the original bittornado source code here h**p://download2.bittornado.com/download/BitTornado-0.3.18.zip
and can tell me what to do when i am done with my program. i have ubuntu installed, so using linux to compile it will not be a problem..thanks

---

### Post by xiownthisplacex on 2007-09-08
well actually it was this programa, here is the source code. [http://downloads.sourceforge.net/tsc1/torrentsearcherclient10-source.rar?modtime=1184773752&big_mirror=0](http://downloads.sourceforge.net/tsc1/torrentsearcherclient10-source.rar?modtime=1184773752&big_mirror=0)

---

### Post by Tomosaur on 2007-09-08
If it's in python, then your job will be much easier - provided you've programmed it in a platform independent manner (no hard coding of file paths, no assumptions about the system etc). Python is platform-independent, you should just try running your program as-is.

My concern is the GUI - what toolkit does it use?

---

### Post by xiownthisplacex on 2007-09-08
sorry for not understanding, but i am portugues, what do you mean by My concern is the GUI - what toolkit does it use?
everything i needed (and my helpers) was in the link i gave you. since im from portugal, i translated everything to portuguese and my friend compiled the program, he said everything he used was in the link i gave you to compile the program.. no extras..

---

### Post by Tomosaur on 2007-09-09
Ok, here's the results of my quick test :)

The programmer of this has assumed the user is running Windows.

The good news is that the program runs fine for the most part. It looks like everything works to do with functionality - you can download torrents, open files etc etc.

The problem, as I suspected, is the GUI (Graphical User Interface). The good news is that it uses wxWidgets to draw the GUI - which is available on Linux. The bad news is that it seems to have trouble with the language file. This probably won't require much work to get working.

Here is a screenshot of the program running on Linux (click the link to see it):
[http://ubuntuforums.org/attachment.php?attachmentid=43107&stc=1&d=1189378131](http://ubuntuforums.org/attachment.php?attachmentid=43107&stc=1&d=1189378131)

As you can see, all the text is missing. The terminal gives lots of errors about 'Can't read the language file!'.

With a little work, I reckon you can get this working just fine.

---

### Post by xiownthisplacex on 2007-09-09
nice! ok, this is the latest beta that we have made i have uploaded the source code to here [http://rapidshare.com/files/54581156/Codigo_Fonte.rar](http://rapidshare.com/files/54581156/Codigo_Fonte.rar)
what should i do to compile it to be used in linux and how do i get past the test errors? thanks once again!

---

### Post by Tomosaur on 2007-09-09
> **xiownthisplacex said:**
> nice! ok, this is the latest beta that we have made i have uploaded the source code to here [http://rapidshare.com/files/54581156/Codigo_Fonte.rar](http://rapidshare.com/files/54581156/Codigo_Fonte.rar)
what should i do to compile it to be used in linux and how do i get past the test errors? thanks once again!

Since you've written it in Python, and the GUI uses wxWidgets, then it should just run fine on Linux anyway. The only issue I can see so far is that the language files can't be read. I'm not sure where exactly the issue lies, but I suspect it is within the tsc.nsi file, since that seems to be where you're registering all of that kind of stuff with the system. The only way you can iron out all of the bugs and such though, is to run it on Linux yourself and try to track down the problems.

Because it's written in Python, all we need to do to run the program is use the following command in the program directory:
```

python ./tsc.py

```

On Windows, the program gets compiled to a .exe file. Linux doesn't use these, so we just ignore all of the stuff involved in that.

I don't know how you'll get past the issues with the text - the best way is to remove all Windows specific code, and use purely platform independent coding. Python is perfect for this. This means you don't need to maintain both a Windows and Linux version - users can just download either.

Windows users also do not need .exe files. That is the beauty of Python.

---

### Post by xiownthisplacex on 2007-09-11
ok, about the fonts, what font is both used in windows and linux? like that i would have just one source code..

---

### Post by Tomosaur on 2007-09-12
> **xiownthisplacex said:**
> ok, about the fonts, what font is both used in windows and linux? like that i would have just one source code..

Most of the 'basic' fonts (Arial, Times New Roman etc) are available in both - but if you just stick to the default system font then there should be no problem.

The problem is the reading of the language files - the error literally says 'Could not read language file'.

Again, the easiest way to go about this would be to just install Linux and see what I'm talking about. Use some kind of virtual machine or emulator to do so - One such is called [QEmu](http://fabrice.bellard.free.fr/qemu/about.html). Using this you can install Linux straight into Windows and run it when you need it - just start QEmu with a Linux installer image.

If you just use system defaults for fonts and such-like, you should have no issues. The problem is the language files.

---

