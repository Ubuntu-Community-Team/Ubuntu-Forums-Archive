---
title: "How do I install programs?"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by jhawk2 on 2008-05-02
Hi All!
I recently switched to ubuntu and the hardest thing for me is to install programs. I am used to where you just click the .exe file and wala it installs! How do I do this in ubuntu? I have downloaded programs but they are soooooo hard to install! I have used synaptic package maneger but still they wont install. Can someone tell me how installing works in ubuntu?
Thanks!

---

### Post by optimusmedia on 2008-05-02
Greetings jhawk, can you give a specific example?

---

### Post by seshomaru samma on 2008-05-02
actually its quite easy to install stuff in Ubuntu

say you want to install "amsn" (Linux clone of MSN-messenger)
open Synaptic (System>administration>Synaptic)
click search , put" amsn" in the search box
you will get some results
mark "amsn" and click "apply"

thats it

there are more ways to install stuff - read [THIS]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by Michael.Godawski on 2008-05-02
That is a good site to start:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Diabolis on 2008-05-02
If you downloaded a binary, that would be a .deb file for debian(Ubuntu), you can just double click on it.

In synaptic you search with keywords, from the results check the boxes of the packages(programs) that you want to install and then in the menu on top click apply.

Everything can be done through the terminal, in the future if you get familiar with the terminal this link will help you:
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)


If you downloaded a .tar.gz file for instance, then what you have is the source code and it needs to be compiled and then installed.

You have to post more info about what you want to do so people can help you.

---

### Post by Sef on 2008-05-02
The three basic ways of installing software on Ubuntu:

1) Applications > Add/Remove  

2) System > Administration > Synaptic Package Manager

3) Applications > Accessories > Terminal
then 
```
sudo apt-get update
```
```
sudo apt-get install program_name
```

Note: you may need to open the Universe or Multiverse or both repositories in order to download some applications, to do that either open Add/Remove and Change the box to either 'All OpenSource Applications' or 'All Available Applications', or System > Administration > Software Sources and click on what you want.

Note: Universe contains only Open Source packages, while Multiverse contains proprietary packages.

---

### Post by jhawk2 on 2008-05-02
Ok. So say I wanted to install unreal tournaments. After I download it then I do what?:confused:
This forum is awesome! Thanks for the quick reply's!

---

### Post by Diabolis on 2008-05-02
If thats a windows game, then you have to install it with [wine]("http://appdb.winehq.org/"). So you have to install wine first.

```
sudo apt-get install wine
```

---

### Post by dashnak on 2008-05-02
Not necessarily, UT can be installed natively in Linux.

---

### Post by jhawk2 on 2008-05-02
No, there is a linux version. How would I install it after downloading?

---

### Post by wormeyman on 2008-05-02
I know that i installed ut 2004 on ubuntu using their native linux installer but i couldn't figure out how to uninstall it.

---

### Post by billgoldberg on 2008-05-02
Download from where?

If it's downloaded from synaptic or add/remove or using the terminal, then it's already installed and should be under "applications -> games".

If you downloaded it from the web you'll need to more specific.

is it a .tar.gz or a .deb or something else?

---

### Post by spadewarrior on 2008-05-02
I'm pretty sure you need to download the two ISOs of UT, burn them to discs then use the Loki installer found here.

[http://www.liflg.org/?catid=6](http://www.liflg.org/?catid=6)

That is, if you mean UT99, which is freeware.

At least, that's what I did. I haven't got the URL for the ISOs off hand though.

---

### Post by jhawk2 on 2008-05-02
The website I am downloading it from is :[http://www.unrealtournament2003.com/ut2003/downloads.html](http://www.unrealtournament2003.com/ut2003/downloads.html)

The name of the file is UT2004-LNX-Demo3334.run.gz
What does run.gz mean?
If anyone has installed this demo on linux please tell me how you did it!

---

### Post by jonaphant on 2008-05-02
> **jhawk2 said:**
> No, there is a linux version. How would I install it after downloading?

if you looked for it in synaptic and appeared and you installed it by double clicking the square at the left of the name, the game may appear in applications>games

EDIT: sorry somebody posted it earlier, i didn't notice

---

### Post by dashnak on 2008-05-02
You have to decompress it, and you will get a file with a .run extension.
You open a terminal, an issue
```
sudo sh /path/to/the/file/file.run
```

---

### Post by Diabolis on 2008-05-02
> **jonaphant said:**
> 
EDIT: sorry somebody posted it earlier, i didn't notice

That is why you should read through the thread before posting.

---

### Post by oldos2er on 2008-05-02
> **jhawk2 said:**
> The website I am downloading it from is :[http://www.unrealtournament2003.com/ut2003/downloads.html](http://www.unrealtournament2003.com/ut2003/downloads.html)

The name of the file is UT2004-LNX-Demo3334.run.gz
What does run.gz mean?
If anyone has installed this demo on linux please tell me how you did it!

 "run.gz" means it's a run (binary) file that's been compressed with gunzip.

 Right-click on the file and choose 'Extract here'. This will leave you with a file named UT2004-LNX-Demo3334.run . In a terminal, navigate to the folder where you extracted the file, and type "chmod +x UT2004-LNX-Demo3334.run", then "./UT2004-LNX-Demo3334.run"

---

### Post by awdoyle on 2008-05-02
> **seshomaru samma said:**
> actually its quite easy to install stuff in Ubuntu

say you want to install "amsn" (Linux clone of MSN-messenger)
open Synaptic (System>administration>Synaptic)
click search , put" amsn" in the search box
you will get some results
mark "amsn" and click "apply"

Thank you seshomaru samma; I didn't know that search option existed.

---

### Post by sujith_s80 on 2008-05-02
I also have the same problem.I have to install the file named'kde_xp_full-1.3-2008-04-11.tar.gz " .How can I install this file.If any one can help me with step by step procedure it will be really helpful

---

### Post by zeththedarkmage on 2008-05-02
For the program that I am trying to run I have the .bin but when I double click it nothing happens...

---

### Post by Biggy on 2008-05-02
in terminal :

sh yourfile.bin

---

### Post by zeththedarkmage on 2008-05-02
it says that it cannot open it.

---

### Post by jhawk2 on 2008-05-02
Ok! This has help alot guys! thanks!

---

### Post by jamyskis on 2008-05-02
> **zeththedarkmage said:**
> For the program that I am trying to run I have the .bin but when I double click it nothing happens...

For some old-fashioned Linux software, the installer program is console based. This means that you need to open the terminal and run it from there. Can you give us more info on what you're trying to run?

---

### Post by Amarsingh0793 on 2008-05-02
You'll be glad to know that the next ubuntu should have CNR (Click N Run). Should make installing programs a lot easier for new users:KS

---

### Post by jhawk2 on 2008-05-02
> **seshomaru samma said:**
> actually its quite easy to install stuff in Ubuntu

say you want to install "amsn" (Linux clone of MSN-messenger)
open Synaptic (System>administration>Synaptic)
click search , put" amsn" in the search box
you will get some results
mark "amsn" and click "apply".


Is that assuming you have already downloaded amsn? Or can you search for any program that is on the internet thru synaptic to download?

---

### Post by jhawk2 on 2008-05-02
> **Amarsingh0793 said:**
> You'll be glad to know that the next ubuntu should have CNR (Click N Run). Should make installing programs a lot easier for new users:KS

Awesome! That would make it so easy! What version is it?

---

### Post by Amarsingh0793 on 2008-05-02
Hopefully 8.10. CNR will come from Linspire.

---

### Post by jhawk2 on 2008-05-02
Do you know when 8.10 will be coming out?

---

### Post by Amarsingh0793 on 2008-05-02
About October - atleast 6 months from now:(

---

### Post by Diabolis on 2008-05-02
> **jhawk2 said:**
> Do you know when 8.10 will be coming out?

8.10 stands for 200**8.10** month, so it will be released in october.

The next one will be 9.04, then 9.10 and so on.

---

### Post by oldos2er on 2008-05-02
> **zeththedarkmage said:**
> it says that it cannot open it.

 Try sh ./yourfile.bin

---

### Post by zeththedarkmage on 2008-05-03
I tried that as well and it didn't work either. The program is stepmania version 3.95 and I got the file from here [http://vyhd.homelinux.org/stepmania/Releases/3.95-linux/](http://vyhd.homelinux.org/stepmania/Releases/3.95-linux/)

the stepmania 3.95 linux.zip.

Once I have downloaded it and extracted it, it has most of the folders and a stepmania.bin in the folder but I cant ./configure it or run it or anything.

---

### Post by 3rdalbum on 2008-05-03
Make sure it has "execute" permission - right-click it, go to Properties, the Permissions tab, and it should be obvious from there. Also check that your terminal is in the correct folder.

---

### Post by zeththedarkmage on 2008-05-03
problem fixed, needed some .so files and permission to access. Thanks for all the help.

---

### Post by GCoffee on 2008-05-03
Go to:

Applications >
Add/Remove Programs.

What is synaptic for? I find some packages only appear in synaptic, not sure why though.

---

### Post by Diabolis on 2008-05-03
Synaptic is just a graphic user interface, in the inside uses the command apt-get.

What do you mean with this:
> **GCoffee said:**
> I find some packages only appear in synaptic, not sure why though.

How else do you search them? Synaptic will only show the packages that are available in the repositories listed in your sources.list file, which for default are Ubuntu repositories.

You can add/enable more sources going here:
system / administration / software sources

---

### Post by jhawk2 on 2008-05-03
> **Diabolis said:**
> Synaptic will only show the packages that are available in the repositories listed in your sources.list file, which for default are Ubuntu repositories
What are repositories?

---

### Post by Diabolis on 2008-05-03
Repositories are servers that hold applications so you can download them and install them without having to visit a website, i.e. from the terminal.

Also packages in the Ubuntu repositories are supposed to be tested, so most of the times they work after they have been installed. I said most of the times because some applications need a bit of tweaking after the installation. 

For instance, compiz gave a lot of trouble to some users, but the package has been polished a lot and now it comes pre-installed.

---

### Post by oldos2er on 2008-05-03
> **jhawk2 said:**
> What are repositories?

 [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

---

### Post by apostate on 2008-05-04
> **oldos2er said:**
> [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

This is hard for a lot of new people to understand. A repository is a server or servers, which holds a library of tested software. Rather than going to a web site somewhere and downloading at random, you just use Synaptic to browse the official Ubuntu software "library". When you click a box next to a package in Synaptic, it downloads, configures, and installs it auto-magically. Done. No installing really. So, if you want the game "Open Arena" just use Synaptic, search for "Open Arena". You will see a file that looks right. Check the box, and hit "Apply". It downloads the right version, configures it, and installs it. Poof.

It is a new way for Windows users to install stuff, but once you get used to it, you will be amazed at how cool it is. When you are looking for a new program, go to Synaptic *first* rather than the web. The WWW can be your last resort, not the first. There are more than 20,000 packages in the Ubuntu repositories, and your PC already knows about them. Just search for whatever seems sensible, and watch what comes up. If you need help with a specific file, ask around here.

That said, some apps, particularly commercial ones (like Unreal Tournament) come with a Windows style "Install Shield" type thing. This will be a .bin or .run, rather than a .exe, but the principle is the same. Make sure it is executable, then double-click it.

Finally, you will have heard about compiling apps from source. This sounds terrifying to some ex-Windows folks, but it really isn't. Fact is though, you will rarely ever need to do this. Installing most Linux software involves "shopping" with Synaptic, or running the installer.

Let us know what apps in particular, and we can help.

---

### Post by jhawk2 on 2008-05-04
Ok Great! Now I am starting to understand. But say the program was not in synaptic? How do I install it then?(assuming I have downloaded the file)

---

### Post by evymetal on 2008-05-04
> But say the program was not in synaptic? How do I install it then?

If it is not in synaptic then you would find the website and try to find a ubuntu ".deb" package (like in windows you look for a windows ".exe" package)

Once you have downloaded that you would double click it and it should install itself.

If there isn't a ".deb" file then there's probably a ".tar.gz" file, which is the free equivalent of ".zip" - there would normally be a file inside called "install" or "readme", which would tell you how to install that specific program.

Hope that helps.

---

### Post by jhawk2 on 2008-05-04
Thanks evymetal!
That is what I have been looking for the whole time!

---

