---
title: "Nothing works trying to download programs?"
date: 2022-02-18
forum: New to Ubuntu
---

### Post by deronmoped on 2022-02-18
I tried downloading two programs. MPC HC (Media Player Classic Home Cinema) and REW (room equalizer wizard) and I can not get permission to install them. I have permission to open Chrome and I can use su in the terminal to access that. But if I go to software it will not give me permission and files will not let me save. I have been trying things for days trying to solve this with searching for solutions. Otherwise Ubuntu works for me. I would hate to abandon Ubuntu because of these issues. Any suggestions that do not need a professional to solve?
Thanks, Deron.

---

### Post by vanadium on 2022-02-18
It is a matter of acting as root to do interventions at the level of the system files. Prefer to use the package manager, else make sure you know well what you are doing.

---

### Post by grahammechanical on 2022-02-18
The mpc-hc.org website tells me that it is no longer under development and has not been since 2017. It is also described as a "light-weight media player for Windows."

I am not surprised that you cannot install it. The situation is better for REW-Room EQ Wizard, It does have a Linux installer. So, I assume that there is a Linux version.

[https://www.roomeqwizard.com/](https://www.roomeqwizard.com/)

Why not investigate ones of these programs?

[https://www.makeuseof.com/tag/awesome-linux-media-center-distros-htpc/](https://www.makeuseof.com/tag/awesome-linux-media-center-distros-htpc/)

Regards

---

### Post by SeijiSensei on 2022-02-18
For media playback, try this
```
sudo apt install mpv smplayer
```
Then launch SMPlayer.

---

### Post by deronmoped on 2022-02-18
[COLOR=#000000]"It is a matter of acting as root to do interventions at the level of the system files. Prefer to use the package manager, else make sure you know well what you are doing."

 That is the problem, I have not taken a course in Ubuntu and really don't care too much on doing that. What your telling me is gobbledygook to me. If I'm to proceed, I need step by step instructions, even at that, I can not follow them as people leave steps out and what applies to one persons system does not necessarily apply to mine.  [/COLOR]

---

### Post by deronmoped on 2022-02-18
[COLOR=#000000]"The mpc-hc.org website tells me that it is no longer under development and has not been since 2017. It is also described as a "light-weight media player for Windows."[/COLOR]

[COLOR=#000000]I am not surprised that you cannot install it. The situation is better for REW-Room EQ Wizard, It does have a Linux installer. So, I assume that there is a Linux version."[/COLOR]

[COLOR=#000000]Some one took over development. I had used it under windows and it worked really well for me. Worked better then VLC media player. [/COLOR]
[COLOR=#000000]I was able to download MPC HC and it installed without too much intervention on my part. But it was extremely broken up playback. I tried a reinstall from the software section of Ubuntu, but I could not authorize it, could not figure out the password. 
REW wizard I could download it, but all it would do is write the code to gedit. And then the save button was grayed out.
 [/COLOR]

---

### Post by ajgreeny on 2022-02-18
> **deronmoped said:**
> [COLOR=#000000]"It is a matter of acting as root to do interventions at the level of the system files. Prefer to use the package manager, else make sure you know well what you are doing."

 That is the problem, I have not taken a course in Ubuntu and really don't care too much on doing that. What your telling me is gobbledygook to me. If I'm to proceed, I need step by step instructions, even at that, I can not follow them as people leave steps out and what applies to one persons system does not necessarily apply to mine.  [/COLOR]

Telling us this seems to me to suggest that you are probably not yet ready to use Ubuntu or any other Linux OS.

Linux is not Windows, was never meant to be Windows, and never will be; to properly use Ubuntu you must learn to think differently from when using Windows and you will have to learn to do things such as installing applications using the utilities available in the OS.  Forget about the old way of searching for and downloading applications from the Internet and use the various package management methods available by default in Ubuntu.
Don't fight the system  but learn to use what it offers and you will learn that it's incredibly powerful and useful, but not used in the manner you're trying to use it at present.

---

### Post by deronmoped on 2022-02-18
[COLOR=#000000][INDENT]"Telling us this seems to me to suggest that you are probably not yet ready to use Ubuntu or any other Linux OS.

Linux is not Windows, was never meant to be Windows, and never will be; to properly use Ubuntu you must learn to think differently from when using Windows and you will have to learn to do things such as installing applications using the utilities available in the OS. Forget about the old way of searching for and downloading applications from the Internet and use the various package management methods available by default in Ubuntu.
Don't fight the system but learn to use what it offers and you will learn that it's incredibly powerful and useful, but not used in the manner you're trying to use it at present."

Yeah, well I beat my head against the wall many times working with windows. It's not necessarily the operating system, most of the time it was something that could not be fixed with the usual commands. I'm having no problems using the terminal to install things. Copy and paste is pretty easy, with the proper instructions given. But the issue I'm having is no authorization to install software from Ubuntu's software. Something is a miss with the password. I can reset my password in terminal, but that does not change it for getting authorization for Ubuntu software install. I went as far as following how to steps to change permissions to yes to fix that issue, but with no luck. For me, passwords cause more problems then they avoid. I hate them.   [/INDENT]
[/COLOR]

---

### Post by deronmoped on 2022-02-18
REW (Room Eq Wizard) when I download it opens in the text editor. Why does it not install it? It says it's loading it on the text editor. The save button is grayed out. When it does finish loading, takes like a fifteen to twenty minutes and all the controls on the text editor are sluggish, it says there are problems with the text.

I just installed [COLOR=#1B1E23][FONT=-apple-system]Holm Impulse another audio measuring program, it did not do the same as REW and use the text editor. Holm runs find, right out of the box. What's up with REW and Holm Impulse is not designed for Ubuntu. [/FONT][/COLOR]

---

### Post by deronmoped on 2022-02-18
OK, I got REW working by downloading the windows version. At first I assumed the linux download would work.

---

### Post by vanadium on 2022-02-19
> **deronmoped said:**
> [COLOR=#000000]"It is a matter of acting as root to do interventions at the level of the system files. Prefer to use the package manager, else make sure you know well what you are doing."

 That is the problem, I have not taken a course in Ubuntu and really don't care too much on doing that. What your telling me is gobbledygook to me. If I'm to proceed, I need step by step instructions, even at that, I can not follow them as people leave steps out and what applies to one persons system does not necessarily apply to mine.  [/COLOR]

No problem at all. It is difficult to estimate the level of the user, and others may be offended when one starts on a too basic level. So just tell you need more basic instructions, and people will adapt.

"root" is the administrator. "Using the package manager" boils down to installing software from the software center, which users can do if they have root priviledges. If you have to install software from somewhere else, then it can be very specific. Sometimes websites provide clear instructions, other times not.

---

