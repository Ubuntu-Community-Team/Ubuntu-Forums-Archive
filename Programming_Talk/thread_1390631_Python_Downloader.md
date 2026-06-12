---
title: "Python Downloader?"
date: 2010-01-25
forum: Programming Talk
---

### Post by ctult on 2010-01-25
Hi all,
I need a Python or Java application that tells whether you have Windows, Mac, or Linux, then depending on the OS it creates a folder called "ct" in either C:/ct (windows), /home/NAME/ct (linux), and whatever it is for Mac.  I can fill that in later.  Then it downloads and runs a native executable (again, depending on the OS).

I would do it, but I am not a good Python or Java programmer:D.


Thanks in advance,
  CTuLT

---

### Post by wmcbrine on 2010-01-26
Since there are of course no existing programs that meet these exact specs, and since you say you don't want to program it yourself, I assume you're looking to hire someone?

---

### Post by Bodsda on 2010-01-26
> **ctult said:**
> Hi all,
I need a Python or Java application that tells whether you have Windows, Mac, or Linux, then depending on the OS it creates a folder called "ct" in either C:/ct (windows), /home/NAME/ct (linux), and whatever it is for Mac. I can fill that in later. Then it downloads and runs a native executable (again, depending on the OS).
 
I would do it, but I am not a good Python or Java programmer:D.
 
 
Thanks in advance,
CTuLT
 
Your probably not going to find someone who will write this for you. Besides the fact that it sounds like homework, you have made no obvious effort to find the answers for yourself.
 
This can be done in about 10 lines of python, it really is not that hard. You should look at the python modules 'os' and 'urllib' and perhaps the bash command 'uname'. 
 
Bodsda
 
 
EDIT: Having thought about this a bit more, you could be asking us to write a trojan for you, a program that downloads an executable (could be a virus) depending on the OS, and then runs it.

---

### Post by ctult on 2010-01-26
I could do it myself I guess.  I just need a tutorial.  Oh, and I am NOT making a virus.  I am making a web server that self-installs to the client computer. And again, no.  I am just putting the python program on the client computer(Jython does not work well enough for CherryPy)

I have no intent to create a virus.  I could very well have(when i had a Windows) been the world record of most viruses on one computer.


EDIT: At least point me somewhere where I can figure out how to do it.

---

### Post by ctult on 2010-01-26
> **wmcbrine said:**
> Since there are of course no existing programs that meet these exact specs, and since you say you don't want to program it yourself, I assume you're looking to hire someone?


I tried to hire someone.  The cheap ones did not work, and the others were $5000 and up.

I DO NOT HAVE $5000 THAT I CAN JUST GIVE AWAY TO SOME RANDOM GUY.

---

### Post by wmcbrine on 2010-01-26
So, you want us to work for free?

---

### Post by ctult on 2010-01-26
> **wmcbrine said:**
> So, you want us to work for free?


I do not have resources to pay you,  and it wouldn't be very nice to take my already depleting money. :(

---

### Post by lukeiamyourfather on 2010-01-26
> **ctult said:**
> I tried to hire someone.  The cheap ones did not work, and the others were $5000 and up.

I DO NOT HAVE $5000 THAT I CAN JUST GIVE AWAY TO SOME RANDOM GUY.

You get what you pay for. If it takes a week of somebody's time then count on it costing about 2% of their salary. For an experienced programmer that sounds about right. Cheers!

---

### Post by Simian Man on 2010-01-26
> **ctult said:**
> I am making a web server that self-installs to the client computer. And again, no.  I am just putting the python program on the client computer(Jython does not work well enough for CherryPy)

You're making a web server?  Like Apache?  Because that's a hell of a lot harder than what you're asking here.  Or are you making some other kind of server application?  Or a website?

Either way the best way to do this is on your website - not on the client's computers.  The correct way to do this is:
[LIST=1]
[*]Make a package/installer for each system you support.  Or, if you're feeling lazy, a zip file with instructions.
[*]On your website, check the useragent string in javascript and display the correct link given their stated system
[*]If it's a system you don't know just list all of the systems and let the user pick
[/LIST]

You really don't need what you're asking.

---

### Post by HalfEmptyHero on 2010-01-26
I'm not the best python programmer, but this should work. I've only testing it on linux though, as I don't have windows or mac.

[PHP]#!/usr/bin/env python

import os
import urllib
url = 'http://www.example.com/file.ext'
filename = '/file.ext'

lin_folder = '/home/' + os.getenv("USERNAME") + '/ct'
mac_folder = '/Users/' + os.getenv("USERNAME") + '/ct'


if os.name == 'nt':
    if os.path.isdir('c:/ct') == 0:
        os.mkdir('c:/ct')
    urllib.urlretrieve(url, 'c:/ct' + filename)
    os.system('c:/ct' + filename)

elif os.name == 'mac':
    if os.path.isdir(mac_folder) == 0:
        os.mkdir(mac_folder)
    urllib.urlretrieve(url, mac_folder + filename)
    os.system(mac_folder + filename)

else:
    if not os.path.exists(lin_folder):
        os.mkdir(lin_folder)    
    urllib.urlretrieve(url, lin_folder + filename)
    os.system(lin_folder + filename)[/PHP]

---

### Post by Bodsda on 2010-01-27
> **HalfEmptyHero said:**
> I'm not the best python programmer, but this should work. I've only testing it on linux though, as I don't have windows or mac.

[PHP]#!/usr/bin/env python

import os
import urllib
url = 'http://www.example.com/file.ext'
filename = '/file.ext'

lin_folder = '/home/' + os.getenv("USERNAME") + '/ct'
mac_folder = '/Users/' + os.getenv("USERNAME") + '/ct'


if os.name == 'nt':
    if os.path.isdir('c:/ct') == 0:
        os.mkdir('c:/ct')
    urllib.urlretrieve(url, win_folder + filename)
    os.system('c:/ct' + filename)

elif os.name == 'mac':
    if os.path.isdir(mac_folder) == 0:
        os.mkdir(mac_folder)
    urllib.urlretrieve(url, mac_folder + filename)
    os.system(mac_folder + filename)

else:
    if not os.path.exists(lin_folder):
        os.mkdir(lin_folder)    
    urllib.urlretrieve(url, lin_folder + filename)
    os.system(lin_folder + filename)[/PHP]

I'd be surprised if that works, looks to me as if your missing a win_folder variable declaration. The script should still run on Linux and Mac without issue. But I think the os.name is going to be a problem, what about windows operating systems before NT, that wont match your conditional?

---

### Post by HalfEmptyHero on 2010-01-27
yeah, I did forget to put win_folder in there. I suppose that is true about the windows before nt.

---

### Post by Zugzwang on 2010-01-27
Also, what makes you think that "C:" is actually the right drive letter to install your program on? Easily, Windows can be installed on "F:". Likewise, the user could install programs on a different drive since "C" might be out of space.

There are so many special cases, which is precisely the reason why Windows program installers usually ask for where to put the stuff.

BTW, this is not meant to be picking on your solution. It's more a remark stating to the OP that the problem is not so trivial as it seems, which is probably why the task isn't so simple/cheap as it looks.

---

### Post by lukeiamyourfather on 2010-01-27
> **Zugzwang said:**
> Also, what makes you think that "C:" is actually the right drive letter to install your program on? Easily, Windows can be installed on "F:". Likewise, the user could install programs on a different drive since "C" might be out of space.

There are so many special cases, which is precisely the reason why Windows program installers usually ask for where to put the stuff.

BTW, this is not meant to be picking on your solution. It's more a remark stating to the OP that the problem is not so trivial as it seems, which is probably why the task isn't so simple/cheap as it looks.

Ditto. If done properly its not a trivial task and I can see why other developers quoted $5,000+ to do it. Especially if you consider a GUI, proxy or no proxy, checking permissions first, verifying the download, there's so many things to consider (to do it properly).

---

### Post by ctult on 2010-01-30
> **Bodsda said:**
> I'd be surprised if that works, looks to me as if your missing a win_folder variable declaration. The script should still run on Linux and Mac without issue. But I think the os.name is going to be a problem, what about windows operating systems before NT, that wont match your conditional?

It will not work on older versions of Windows(Anyway... who still uses Win3.0?:))

---

### Post by ctult on 2010-01-30
I think I will fix it with the Jython--Swing combo.  And yes, I know that Windows has more than just the C:/ drive.  That is one reason I switched to Ubuntu Linux.

---

