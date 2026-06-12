---
title: "terminal"
date: 2014-04-06
forum: New to Ubuntu
---

### Post by sammy3 on 2014-04-06
and again as always, having problems. (really starting to not like linux anymore)

trying to download this Happy Baby Hack Tool for a friend and I'm guessing I have to use terminal to help me the rest of the way? cause what ever WINE program I need, I don't have or can't find. Terminal is unable to locate file (it's an .exe file and I don't know if it has to be changed or if I'm doing something wrong.) 

She said it works for linux but I just can't figure out how to download it.

---

### Post by panorain on 2014-04-06
I don't know for certain but files ending in .exe might not be executable in the terminal.

---

### Post by sammy3 on 2014-04-06
know of anything that might help?

---

### Post by 3rdalbum on 2014-04-06
Relax, this is easy. You're just not familiar with Linux yet.

Install Wine from the Ubuntu Software Center program, or type 'sudo apt-get install wine' into the terminal. Log out and log in again. Right-click the Exe file and choose Open With Wine.

---

### Post by sammy3 on 2014-04-06
it's saying I have it and it's at its latest version

---

### Post by panorain on 2014-04-06
I decided to install Wine and see what's going on with this as well.  then I downloaded 'Happy Baby Hack Tool' and extracted the folder labeled [Facebook Cheat Installer.Rar] to  desktop. Finally I see the following file---->Facebook Cheat  Installer.exe then I right clicked on it and selcted [open with wine]  and get this error. 

Here is a screenshot of the Wine error I receive listed below.

[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=251782&stc=1&thumb=1&d=1396835692[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=251782&d=1396836867")

If you read the instruction.txt file. It states the following.
--------------------------------------------------------------------------------
After extrating the file, install it. 
 
Let it finish intalling. Aftwerwards go to:  
 
================================== 
     [http://bit.ly/1h7zDgs](http://bit.ly/1h7zDgs) 
================================== 
 
 
This is important, since the file will not work without the firmware. 
 
Do not worry it is a direct download, and survey free. 
 
After downloading it install it and the program will run smoothly. 
 
THANKS!!!
____________________________________________________________________________________________________________________________________________
What do you think the [firmware might do to the pc]? What is this 'embedding html to work properly'? I think Gecko is referring to Mozilla firefox maybe. Any suggestions?

---

### Post by sammy3 on 2014-04-06
that's the problem I'm having and I have no idea what to do about it. I don't even know about the firmware either.

---

### Post by panorain on 2014-04-06
Are you receiving the same 'Wine' error as I am?

This is becoming very interesting actually.

---

### Post by sammy3 on 2014-04-06
no, mine either won't open or they are having technical difficulties. maybe I have the wrong wine program. Q4Wine, Wine configure and Wine windows program loader. that's all I found in the software center, i even installed it a few months ago through terminal for another program i was trying to get.

---

### Post by buzzingrobot on 2014-04-07
> **sammy3 said:**
> no, mine either won't open or they are having technical difficulties. maybe I have the wrong wine program. Q4Wine....

When I search for "Wine" with the Software Center, the first result listed is "Microsoft Windows Compatiblilty Layer (Meta-Package) wine". That's what you need to install.

---

### Post by sammy3 on 2014-04-07
It says it is installed.

---

### Post by buzzingrobot on 2014-04-07
> **sammy3 said:**
> It says it is installed.

If the Software Center says it is installed, it was very likely as a dependency to Q4Wine.

---

### Post by plurga on 2014-04-07
maybe this thread can help u 

[http://ubuntuforums.org/showthread.php?t=634464](http://ubuntuforums.org/showthread.php?t=634464)

---

### Post by m-dw on 2014-04-07
> **panorain said:**
>  What do you think the [firmware might do to the pc]? What is this 'embedding html to work properly'? I think Gecko is referring to Mozilla firefox maybe. Any suggestions?

There is a package called wine-gecko listed in synaptic (search for wine).  Claims to be an HTML rendering engine to display embedded web pages in Wine applications.

---

### Post by sammy3 on 2014-04-07
I've looked up some videos on youtube and they kinda helped a different way but terminal is showing it differently for me and not working correctly. 
[ATTACH=CONFIG]251816[/ATTACH]

They used Wine Windows Program Loader to open their program and it worked fine for them.
(I cannot yet open it with that because the program is obviously not installed)

---

### Post by panorain on 2014-04-09
Do you think there might be a difference trying to run this program under wine vs. a real live running Windows computer with registry and all that installed? This has actually been a interesting post to follow so far. Your trying to run 'Happy Baby Hack tool' with Q4-wine now right? I am running through the initial Q4-wine setup now but get stuck on the 'Console application settings'. What 'Sorry specify console binary' be set at?

---

### Post by sammy3 on 2014-04-10
the only windows computer in the house is my brothers and its an old version (sent from a friend of his cause his computer is down from a bad part) and I'm not sure if he would put it on his even for a few minutes long enough to get whatever done. and even though it is safe and will not cause harm to his computer i don't think he'll take any chances and I don't blame him. 

the one actual problem i am having is just installing it. I used the "sudo" thing and it just can't locate the package. where do you suggest putting it for it to actually find it? it's on the desktop right now so i won't lose it.

---

