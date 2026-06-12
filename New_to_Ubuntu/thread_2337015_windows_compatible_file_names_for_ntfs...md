---
title: "windows compatible file names for ntfs..???"
date: 2016-09-13
forum: New to Ubuntu
---

### Post by a.dusty.trail on 2016-09-13
i save a lot of stuff for in ubuntu that i review in windows
i find that i have a lot of problems with ubuntu saving thins with incompatible file names..
mostly with firefox saving webpages for off line use..

how do i set up my system so that ubuntu will only use windows compatible filenames for ntfs???

---

### Post by oldfred on 2016-09-13
windows_names in fstab?

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

---

### Post by a.dusty.trail on 2016-09-14
but what aout writing to ext3 and ext4 partitions.. i would like those filenames compatible as well..
is that possible?

---

### Post by sudodus on 2016-09-14
You could create file names via a script, or parse existing files through a script, which finds bad names and either suggests what to change or just tells you which files are violating the NTFS standard. *oldfred* gave you the recipe, which characters to avoid :-)

I would not use those characters in linux anyway, but I have seen files with : (colon).

In addition, I would not use ' (single quote). Blank (space) is accepted, but creates problems in some programs and scripts.

---

### Post by a.dusty.trail on 2016-09-14
so your saying that when i use ubuntu firefox to save webpages and it saves them with windows incompatible charaters
if i want to see those offline files i have to parse them through a script before they can be compatible with windows?
and there is no application that might preform this action?

when i save the same webpages in windows the issue never comes up..
(you would think that the webpage format would be the same but there must be changes)

is there no way to set ubuntu to just to save things in a compatible way?

makes bual booting almost not worth it for the headaces.
prefer to surf in ubuntu but most everything else has to be done in windows.

---

### Post by sudodus on 2016-09-14
I don't say, because I don't know, if there is a program or tweak, that can do it, or not. Maybe there is, and in that case, let us hope someone (who reads this and knows) will tell us about it :-)

I say that it should be possible to do something fairly simple to fix it, depending on what you want. But are you talking about web addresses? I'm afraid, that if you change them, it will not work. Or are you talking about downloading html pages and subdirectories? In that case why do you want them off-line, and portable between Windows and linux?

---

### Post by Geoffrey_Arndt on 2016-09-14
Can you provide an example web page that renders good in Firefox on Linux, and not so good in Firefox on Windows?   Please provide the full web page code & links.

---

### Post by a.dusty.trail on 2016-09-16
[URL="https://ubuntuforums.org/member.php?u=1499021"][B][COLOR=#DD4814][B]
@sudodus[/B][/COLOR][/B][/URL] 	 
why ask why?  i keep information that i want to have for offline use.. i have archives of information going back to my first days online.
90% of which is information gone now, and if it is out there is it impossible to find. but its information that i want to keep.
and since the easiest way to do that is by saving a webpage in firefox  that is what i do most of the time.
(you know in fire fox click menu then "save page"), sometimes when there is more than one page i use htttrack.
i use these file across all my devices. laptops with ubuntu, desktops with windows, tablets with android. etc

and i have to say that compatibility is best with things saved from windows and read on everything else..
but i would really prefer to save everything in ubuntu and read it on everything else
(and not not every device has access to the internet,nor do i want them all to, i don't need everything connected to the internet)

if i can ever find a good app that will save webpages in epub format i will be quite happy

@ 				 				 					 						 	[**[COLOR=#000000]Geoffrey_Arndt[/COLOR]**]("https://ubuntuforums.org/member.php?u=1973436")

why are you asking about rendering in firefox? that is not what my question is about.

---

### Post by sudodus on 2016-09-16
Thanks for the explanation :-)

Have you tried other web browsers in linux, for example chromium-browser, chrome, opera? ONe of them might create off-line pages, that are more compatible. But in the end, if a browser in Windows does a better job, use it for this purpose.

---

