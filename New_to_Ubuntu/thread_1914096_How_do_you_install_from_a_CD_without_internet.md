---
title: "How do you install from a CD without internet?"
date: 2012-01-23
forum: New to Ubuntu
---

### Post by ac4rb on 2012-01-23
Has anyone tried to install a deb package or any application in Ubuntu 11.10.AMD64 from a CD/DVD without being connected to the internet? I have a Compaq CQ57 and finally got what I thought was everything working but the dial-up internet. You see, not everyone is blessed with highspeed wireless. So I used a friends wireless to upgrade and set up most of my programs. In order to save time I just downloaded a few APPS I thought I would need. I downloaded them from Ubuntu's repository so they should be compatable. They are in deb files. I can go in the software manager and select CD/DVD as a source, but when I click on an application on the CD it appears to start to work. Then it tries to connect to the internet and after about 10 minuets I get flustrated and stop the thing. It is obvious that it is trying to check the internet for something. I have tried just about everything including removing all sources from the download manager except the CD/DVD and still the same. I would even try to do a command line installation if I could find a way to apt-get install from a CD/DVD. Is there a way??


Thanks AC4RB

---

### Post by Cheesemill on 2012-01-23
You should check out [Keryx]("http://keryxproject.org/").

I think the website is currently being updated but searching for 'keryx project' should get you what you need.

---

### Post by dFlyer on 2012-01-23
Have you tried to copy the .deb files to your hd and than try
sudo dpkg -i "packageName.deb" without the quotations marks.

---

### Post by ac4rb on 2012-01-23
> **dFlyer said:**
> Have you tried to copy the .deb files to your hd and than try
sudo dpkg -i "packageName.deb" without the quotations marks.No Garry, But I certainly try. My Ubuntu is installed totally on a 16gb USB drive, but it should work the same. Should I copy it into any specific folder or just in the root?
Thanks again,
Glenn AC4RB

---

### Post by cortman on 2012-01-23
> **ac4rb said:**
> Has anyone tried to install a deb package or any application in Ubuntu 11.10.AMD64 from a CD/DVD without being connected to the internet? I have a Compaq CQ57 and finally got what I thought was everything working but the dial-up internet. You see, not everyone is blessed with highspeed wireless. So I used a friends wireless to upgrade and set up most of my programs. In order to save time I just downloaded a few APPS I thought I would need. I downloaded them from Ubuntu's repository so they should be compatable. They are in deb files. I can go in the software manager and select CD/DVD as a source, but when I click on an application on the CD it appears to start to work. Then it tries to connect to the internet and after about 10 minuets I get flustrated and stop the thing. It is obvious that it is trying to check the internet for something. I have tried just about everything including removing all sources from the download manager except the CD/DVD and still the same. I would even try to do a command line installation if I could find a way to apt-get install from a CD/DVD. Is there a way??


Thanks AC4RB

Check out the link in my signature on offline installation. I think it may be just what you're looking for.

---

### Post by saneearth on 2012-01-23
Should just be able to copy them you your home folder and open and install easily with gdebi.

---

### Post by ac4rb on 2012-01-24
> **dFlyer said:**
> Have you tried to copy the .deb files to your hd and than try
sudo dpkg -i "packageName.deb" without the quotations marks.Gary, Thanks this will do it, however, It didn't install wvdial because of dependancies. This is one of the things that bother me. Very seldom do you know there are dependencies, until you have tried to install the program. Here is what I got when I tried to install. 
  	 	 	 	 	 	 	 	 	 	  glenn@glenn-Presario-CQ57-Notebook-PC:~$ sudo dpkg -i wvdial.deb  
 dpkg: warning: downgrading wvdial from 1.61-4 to 1.60.1+nmu2.  
 (Reading database ... 157969 files and directories currently installed.)  
 Preparing to replace wvdial 1.61-4 (using wvdial.deb) ...  
 Unpacking replacement wvdial ...  
 dpkg: dependency problems prevent configuration of wvdial:  
  wvdial depends on libuniconf4.4; however:  
   Package libuniconf4.4 is not installed.  
  wvdial depends on libwvstreams4.4-base; however:  
   Package libwvstreams4.4-base is not installed.  
  wvdial depends on libwvstreams4.4-extras; however:  
   Package libwvstreams4.4-extras is not installed.  
  wvdial depends on libxplc0.3.13; however:  
   Package libxplc0.3.13 is not installed.  
 dpkg: error processing wvdial (--install):  
  dependency problems - leaving unconfigured  
 Processing triggers for man-db ...  
 Errors were encountered while processing:  
  wvdial  
 glenn@glenn-Presario-CQ57-Notebook-PC:~$



one would think that the dependancies would be packaged with the programs.



Thanks again, Glenn

---

### Post by Cheesemill on 2012-01-24
Check out mine or cortmans post above for the answer.

---

### Post by cortman on 2012-01-24
^^ this. I haven't used Keryx yet, but Synaptic (my program of choice) download scripts include and download all dependent packages for whatever program you select.

---

### Post by mastablasta on 2012-01-24
KeryX is 404 (at least the download page while the main page throws some other BS out, not really much connected to keryx)
 
while synaptics assumes the computer user has access to is a Linux computer (or am i mistaking?). And what if they have windows installed can it be done using liveUSB?

---

### Post by cortman on 2012-01-24
> **mastablasta said:**
> KeryX is 404 (at least the download page while the main page throws some other BS out, not really much connected to keryx)
 
while synaptics assumes the computer user has access to is a Linux computer (or am i mistaking?). And what if they have windows installed can it be done using liveUSB?

LiveUSB or Virtual box, I guess. There's no way that I know of yet to turn a Synaptic package download script into a windows batch file, although with a little know-how it should be easy enough to do. I just don't know DOS well enough.

---

### Post by ac4rb on 2012-01-24
> **cortman said:**
> LiveUSB or Virtual box, I guess. There's no way that I know of yet to turn a Synaptic package download script into a windows batch file, although with a little know-how it should be easy enough to do. I just don't know DOS well enough.
Still hoping for a simple answer. I have used Xandros for about 5 years now and this is one thing that Xandros Networks does with ease. I have failed only a few times to install from the network. It works great with CD/DVD installations also. I used Ubuntu because I haven't saw a Xandros 64bit package that I thought would work on my Compaq CQ57. Other than installing programs, I think Ubuntu is better. Xandros Networks has a very good GUI for doing this. All you do in it is tell it to install from a CD/DVD and it works. Or you can just double click on the program on either a hard drive, CD, or DVD and it takes off installing. I expect some industrious person will do this with Ubuntu soon. I sure hope so. I haven't written any ASM or C++ in so long (been retired for 7 years) I probably could not get it to display "Hello World" so that leaves me out.

Thanks again you guys,
Glenn AC4RB

---

### Post by gordintoronto on 2012-01-24
To get a list of packages installed on an Ubuntu computer, use this command:
dpkg --get-selections "*" > Desktop/applications

Copy the file "applications" to a flash drive, so you have it with you when you download applications.

When you download an application from packages.ubuntu.com, it shows you a list of dependencies. Check it against the list of what you have installed, and download each item which is missing. (And those items may also list dependencies, which you have to check against your list...)

---

### Post by jtarin on 2012-01-24
I'm assuming you are trying to get a working internet connection using "wvdial"? According to your attempted install of the wvdial.deb it is already installed. Have you tried entering the command "wvdial" in a terminal? if so what is the output?[ More info on wvdial.]("http://en.wikipedia.org/wiki/Wvdial")...and [here]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer") for setup w/Ubuntu.

---

### Post by cortman on 2012-01-24
> **ac4rb said:**
> Still hoping for a simple answer. I have used Xandros for about 5 years now and this is one thing that Xandros Networks does with ease. I have failed only a few times to install from the network. It works great with CD/DVD installations also. I used Ubuntu because I haven't saw a Xandros 64bit package that I thought would work on my Compaq CQ57. Other than installing programs, I think Ubuntu is better. Xandros Networks has a very good GUI for doing this. All you do in it is tell it to install from a CD/DVD and it works. Or you can just double click on the program on either a hard drive, CD, or DVD and it takes off installing. I expect some industrious person will do this with Ubuntu soon. I sure hope so. I haven't written any ASM or C++ in so long (been retired for 7 years) I probably could not get it to display "Hello World" so that leaves me out.

Thanks again you guys,
Glenn AC4RB

I'm about finished with a little VB.Net program that would take a Synaptic download script and automatically download all the .deb files in Windows, so you can download Linux programs for an offline machine from any online computer even if it isn't running Linux.
I think it works, and I'm pretty excited about it- with it, no one within reach of an internet cafe or library would have any trouble getting any software at all, even if they don't have a second computer running Linux. We'll see.

---

### Post by mastablasta on 2012-01-25
awesome!  though i do have optics at home i know there is plenty of people that either have dial up only or they use very expencive internet via mobile phone. they would all benefit from an option to just go to an internet cafe (where internet is cheaper) to download stuff.
 
i am surprised that this kind of thing is not included with Ubuntu or available from the site (considering the Mark's idea of CD dispensers for those that can't afford conneciton...).
 
there are deb files but sometimes they do not inlcude dependencies.

---

### Post by cortman on 2012-01-25
Ok, the base program is done. I just need to polish up the UI a bit and then we'll be off to the races.
Of course, as appears to be the case with most software development, as soon as you have a "eureka!" moment, you find that it's been done already- I finally looked into Keryx a little more (what there was of it that wasn't 404). The trouble with Keryx is that it requires Python on the Windows computer, which is a bit of a rarity.
There's also Wubdepends, but I wasn't able to get a functioning .exe from them and it looks like it needs Python too.
My program will need .NET framework, but that's pretty much standard on any Windows PC anymore.

---

### Post by cortman on 2012-01-25
Wassail (windows (a) synaptic script (a) interpreter (l)) is complete! Check it out on sourceforge, and let me know how it works!
[https://sourceforge.net/projects/wassail/]("https://sourceforge.net/projects/wassail/")

---

### Post by ac4rb on 2012-01-26
> **cortman said:**
> Winaptic Interpreter is complete! Check it out on sourceforge, and let me know how it works!
[https://sourceforge.net/projects/winaptic/](https://sourceforge.net/projects/winaptic/)
Thanks Cortman.
   I downloaded synaptic, tried a dpkg install and guess what? It too needed dependancies which were not included with the package. It has been a long time since I did any ASM or C++, but one would think that these or at least some of these dependancies could be placed in the header. As Mastablasta mentioned, this is one thing Windoz has on Linux. If you load a windoz program that requires say DirectX. It is usually included in the package and not only that the newest version at the time packaged is included. Again I am asking a question, can these be put in the header? As Mastablasta said, this is an issue which should be addressed and has been for a long time. Mastablasta also noted that this would cause the package to be larger which is true. However, If I for instance has to download them via dial-up, I much perfer downloading all at once in say a TAR or ZIP file than a few at a time and going through the hassel of installing then find out I needed something else. I usually download the larger packages while I sleep to keep from tying up the phone during the day.

Thanks again guy and gals,

Glenn AC4RB

---

### Post by cortman on 2012-01-26
> **ac4rb said:**
> Thanks Cortman.
   I downloaded synaptic, tried a dpkg install and guess what? It too needed dependancies which were not included with the package. It has been a long time since I did any ASM or C++, but one would think that these or at least some of these dependancies could be placed in the header. As Mastablasta mentioned, this is one thing Windoz has on Linux. If you load a windoz program that requires say DirectX. It is usually included in the package and not only that the newest version at the time packaged is included. Again I am asking a question, can these be put in the header? As Mastablasta said, this is an issue which should be addressed and has been for a long time. Mastablasta also noted that this would cause the package to be larger which is true. However, If I for instance has to download them via dial-up, I much perfer downloading all at once in say a TAR or ZIP file than a few at a time and going through the hassel of installing then find out I needed something else. I usually download the larger packages while I sleep to keep from tying up the phone during the day.

Thanks again guy and gals,

Glenn AC4RB

How did you download Synaptic? In the link for Offline Synaptic Installation/Repo updates I give the entire download script with ALL dependencies- I've tried it on several completely virgin Ubuntu boxes and it installed fine with all the dependencies.
I would recommend you follow the instructions in that tutorial.

---

### Post by ac4rb on 2012-01-27
> **cortman said:**
> I'm about finished with a little VB.Net program that would take a Synaptic download script and automatically download all the .deb files in Windows, so you can download Linux programs for an offline machine from any online computer even if it isn't running Linux.
I think it works, and I'm pretty excited about it- with it, no one within reach of an internet cafe or library would have any trouble getting any software at all, even if they don't have a second computer running Linux. We'll see.
Let me know when you get the Bata release, send me a link, and I will try it.

Thanks,
Glenn AC4RB

---

### Post by cortman on 2012-01-27
> **ac4rb said:**
> Let me know when you get the Bata release, send me a link, and I will try it.

Thanks,
Glenn AC4RB

You can download and try it out [here.]("https://sourceforge.net/projects/wassail/")

---

### Post by mastablasta on 2012-01-28
darn it i use .net version 3.5. don't remember at the moment why but i do know that a site i need to use uses this version as i remmebr i had to upgrade to it :-(

anyway i hope this works for others with windows 7 and that do not need to have the old version installed. it would be good to have a system independent programme script if that is even possible.

edit i see KDE has KDE applicaitons available for download for those that do not have good connection (as source and preppackaged). didn't try them yet though.

---

### Post by cortman on 2012-01-28
> **mastablasta said:**
> darn it i use .net version 3.5. don't remember at the moment why but i do know that a site i need to use uses this version as i remmebr i had to upgrade to it :-(

anyway i hope this works for others with windows 7 and that do not need to have the old version installed. it would be good to have a system independent programme script if that is even possible.

edit i see KDE has KDE applicaitons available for download for those that do not have good connection (as source and preppackaged). didn't try them yet though.

Shoot. Figured this'd happen, but oh well. I think you can upgrade to .NET 4 and still keep 3.5, though.
I'm trying to decide whether to try to cram C and rewrite it in C, or see if I can interest some C master into doing it.

---

