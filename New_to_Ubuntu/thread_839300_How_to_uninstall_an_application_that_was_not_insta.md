---
title: "How to uninstall an application that was not installed via Add/Remove?"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by swarup on 2008-06-24
I am running Ubuntu Hardy, and installed a text-to-speech program called "Verbose" that has a Linux version. It is not part of the Ubuntu repos, and so of course is not listed in the Add/Remove application. I downloaded it off the web and it installed. But now it opens itself every time I boot the computer, and I want to get rid of it.

Add/Remove and Synaptic Package Manager can't be used in this situation, I presume, since "Verbose" is not listed there.

How do I uninstall it?

---

### Post by vambo on 2008-06-24
If you downloaded a deb package you can use:
```
sudo dpkg -r <name_of_package>
```

If it was a tarball, there might be a "make remove" option - see the documentation that came with it.

---

### Post by WRDN on 2008-06-24
To uninstall a package, use the following command:

```
sudo apt-get remove [package]
```

---

### Post by swarup on 2008-06-24
> **vambo said:**
> If you downloaded a deb package you can use:
```
sudo dpkg -r <name_of_package>
```

If it was a tarball, there might be a "make remove" option - see the documentation that came with it.

The name of the file to download is vb.tar.gz, and it is a Tar archive. So I guess that means it is a tarball, right? Can something be both a deb package and a tarball, or is it that if it is a tarball then that means it is not a deb package?

Does the above give you a better sense of how I would have to uninstall it?

If it is useful for you to see it, here is its website: [http://www.nch.com.au/verbose/index.html](http://www.nch.com.au/verbose/index.html)

It looks like a pretty interesting program actually, but I couldn't understand how to work it properly.

For any interested, here is the description of the program:

> Verbose is a text to speech program which will read aloud any text or save it as mp3.

After you have installed this text reading software you can assign a system wide hot key. Then whenever you want Verbose to read the text on your screen just push that key and the software will read it aloud.

Verbose text to voice software can also save your text documents or emails to mp3 or wav for you to store them on your Pocket PC or MP3 player, such as an iPod, so you can listen to them on your way home. 

---

### Post by swarup on 2008-06-24
> **WRDN said:**
> To uninstall a package, use the following command:

```
sudo apt-get remove [package]
```

Does this apply for *any* program, whether or not it comes from the Ubuntu repo and whether it is a deb package or tarball or anything else?

---

### Post by vambo on 2008-06-24
Actually this looks as if it's a binary just packaged with tar.
Did you have to do anything to build it after downloading? Like:
./configure
make
make install

If you did then you have the source as well.

In either case you'll have to hand remove it either via File Manager or using the rm command in terminal

---

### Post by swarup on 2008-06-24
You know, it's actually not my computer but my partner's. I say that by way of explaining that I'm not *so* familiar with the situation on the computer, or what he did when he downloaded it. But this much I can say for sure-- I know he didn't compile it (./configure etc). I thought he might have done something simple to get it to install like right-click and activate a package manager or something like that if that's all that were involved. But the truth is, I'm not certain whether or not it is actually installed. This much I know-- every time the computer boots, Verbose opens a window in the upper left hand corner of the screen and it is written something to the effect that it needs a synthetic voice to work. And if you click on that window, then another window opens filling the entire screen, which says V-E-R-B-O-S-E in big letters. Does it sound like it is installed?

---

### Post by vambo on 2008-06-24
It does sound as if it's installed - also sounds like a pain in the rear.
If it's coming up when you boot, probably best to just disable it via Settings -> Autostarted apps.
Note this is for xfce, I do know there's an equivalent in gnome, but can't remember what it's proper name is.

FYI, if you want text to speech have a look at espeak - that is in the repos

---

### Post by the_doc on 2008-06-24
Pretty sure that's just a binary in an archive.

---

### Post by Canis familiaris on 2008-06-24
> **vambo said:**
> It does sound as if it's installed - also sounds like a pain in the rear.
If it's coming up when you boot, probably best to just disable it via Settings -> Autostarted apps.
Note this is for xfce, I do know there's an equivalent in gnome, but can't remember what it's proper name is.

FYI, if you want text to speech have a look at espeak - that is in the repos

In GNOME System->Preferences->Sessions, delete the verbose entry.

@OP:
I installed it to help you but even I cannot remove it either.
I am evaluating how to uninstall it.

---

### Post by swarup on 2008-06-24
> **Anurag_panda said:**
> In GNOME System->Preferences->Sessions, delete the verbose entry.

@OP:
I installed it to help you but even I cannot remove it either.
I am evaluating how to uninstall it.

I appreciate your kind help in having gone to the effort of installing it. :) Please do let me know if you get success in uninstalling it.

And by the way, I was also interested in knowing how to use it. While you have it installed, perhaps you'd like to see as well? It seems that the only thing missing for it to work, is a "voice engine". And it gives reference to a place in its website where one can go to download a voice engine so that the program can produce human sound. But when you go to that site, it looks like all the voice engines available are ".exe" i.e. are windows executables. Which of course wouldn't help us at all. Do you know where one could get a Linux voice engine which would work in Verbose? Then at least I could see how well it works as a text-to-speech utility.

---

### Post by swarup on 2008-06-24
> **vambo said:**
> FYI, if you want text to speech have a look at espeak - that is in the repos

I checked in Synaptic Package Manager and espeak actually shows as being installed in my computer. But when I try to open it via a terminal window, nothing happens. How do you start it up?

```
swarup@swarup-laptop:~$ espeak

```

---

### Post by Canis familiaris on 2008-06-24
> **swarup said:**
> I appreciate your kind help in having gone to the effort of installing it. :) Please do let me know if you get success in uninstalling it.

And by the way, I was also interested in knowing how to use it. While you have it installed, perhaps you'd like to see as well? It seems that the only thing missing for it to work, is a "voice engine". And it gives reference to a place in its website where one can go to download a voice engine so that the program can produce human sound. But when you go to that site, it looks like all the voice engines available are ".exe" i.e. are windows executables. Which of course wouldn't help us at all. Do you know where one could get a Linux voice engine which would work in Verbose? Then at least I could see how well it works as a text-to-speech utility.
Yes I was also wondering the same! I mean they created a Linux native for their application but there is no clue for a voice engine.
BTW I haven't been able to uninstall it yet.

---

### Post by Canis familiaris on 2008-06-24
> **swarup said:**
> I checked in Synaptic Package Manager and espeak actually shows as being installed in my computer. But when I try to open it via a terminal window, nothing happens. How do you start it up?

```
swarup@swarup-laptop:~$ espeak

```
epseak seems to be a Command line program
I created a text file called abc and wrote Hello

and then the computer spoke "hello" by:

```
espeak -f abc
```

I am trying to read PDF files using it

---

### Post by jonathan.gardner04 on 2008-06-24
If the application was compiled via source and then installed via make you will have to run 

> make uninstall form the installation directory

---

### Post by Canis familiaris on 2008-06-24
> **jonathan.gardner04 said:**
> If the application was compiled via source and then installed via make you will have to run 

 form the installation directory

Actually it was a binary installation

---

### Post by jonathan.gardner04 on 2008-06-24
Check out this link

[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by vambo on 2008-06-24
For espeak try, in terminal:

```
echo "Hello World" | espeak
```

---

### Post by swarup on 2008-06-24
> **Anurag_panda said:**
> epseak seems to be a Command line program
I created a text file called abc and wrote Hello

and then the computer spoke "hello" by:

```
espeak -f abc
```

I am trying to read PDF files using it

I see. 

1. Wouldn't one need to provide the actual pathway to the text file in the command line?

2. I guess this program will only "read out" the text, and will not provide a wav or mp3 file of it for later listening?

3. I wonder whether one would have the option of providing different voice engines for it, if one did not prefer the default voice?

My guess is that the espeak program is quite basic, and so may not provide the above facilities. But I did a google search, and it looks like there are a couple of more developed text-to-speech programs out there for Linux. One of them is called "Festival". But the install looked like it may be a bit troublesome. It was dealing with "rpm"s and "yum"s which I think are usually meant more for other distros, not Ubuntu. Right?

---

### Post by swarup on 2008-06-24
> **vambo said:**
> For espeak try, in terminal:

```
echo "Hello World" | espeak
```

Yep, it works. Pretty basic stuff. :) Some of what I mentioned above may hopefully be more sophisticated and provide a better reproduction of a human voice. There is some pretty powerful text-to-speech software available for Windows these days. I'm hoping that some of it has filtered over to the Linux side as well.

---

### Post by Canis familiaris on 2008-06-24
> **swarup said:**
> I see. 

1. Wouldn't one need to provide the actual pathway to the text file in the command line?

2. I guess this program will only "read out" the text, and will not provide a wav or mp3 file of it for later listening?

3. I wonder whether one would have the option of providing different voice engines for it, if one did not prefer the default voice?

My guess is that the espeak program is quite basic, and so may not provide the above facilities. But I did a google search, and it looks like there are a couple of more developed text-to-speech programs out there for Linux. One of them is called "Festival". But the install looked like it may be a bit troublesome. It was dealing with "rpm"s and "yum"s which I think are usually meant more for other distros, not Ubuntu. Right?

1. Yes but in my command the file was in the home directory

3. I did not prefer the default voice as well. And I'm lookiing at alternate voice too.

BTW festival is in the repos.
```
sudo apt-get install festival
```

But it is command line as well. However there maybe a GUI

---

### Post by vambo on 2008-06-24
> **swarup said:**
> Yep, it works. Pretty basic stuff. :) Some of what I mentioned above may hopefully be more sophisticated and provide a better reproduction of a human voice. There is some pretty powerful text-to-speech software available for Windows these days. I'm hoping that some of it has filtered over to the Linux side as well.

Have a look at:

```
espeak --voices
```

And just for fun try:

```
echo "hello World" | espeak -v en-sc
```

:)

---

### Post by hovzio on 2008-06-24
hi, I just tried out espeak (just after reading this thread, didn't even know of such a program..cool) and the output I'm getting is rather garbled. Doesn't really sound to good and a few terms are barley understandable. Just wanted to know if this was normal or if there need be any fine tuning and so forth? Thanks

---

### Post by vambo on 2008-06-24
> **hovzio said:**
> hi, I just tried out espeak (just after reading this thread, didn't even know of such a program..cool) and the output I'm getting is rather garbled. Doesn't really sound to good and a few terms are barley understandable. Just wanted to know if this was normal or if there need be any fine tuning and so forth? Thanks

Does sound a bit like a Dalek I grant. However, have a look at the man page. You can play with amplitude, pitch, speed etc.

---

### Post by hovzio on 2008-06-24
> **vambo said:**
> Does sound a bit like a Dalek I grant. However, have a look at the man page. You can play with amplitude, pitch, speed etc.

Thanks! I slowed down the whole thing and it sounds a lot better. The default speed is 160. I found 110 (words per min.) to sound a lot better. You can set the speed with -s 0 - 200.The -a option is for amplitude. Default is 100 but in my opinion 50 is not quite as high pitched.

```
echo "hello world, how's it goin? " | espeak -s 110 -a 50
```

---

