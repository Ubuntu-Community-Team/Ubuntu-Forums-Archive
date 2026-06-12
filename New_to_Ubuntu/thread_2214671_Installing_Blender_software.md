---
title: "Installing Blender software"
date: 2014-04-02
forum: New to Ubuntu
---

### Post by scadger on 2014-04-02
Ubuntu is driving me nuts. Im a newbie, and just installed v13.10 64 bit, which generally appears to have installed ok and work ok.

I want to install Blender (from Blender.org) v1.7 (the latest release).

I followed all the online help about installing software but I'm having problems:

1. I tried the Ubuntu Software Centre, found Blender, but its an older version (2.66) so can't install that
2. I went to the Blender.org website and it lets me download the software (.tar.bz2). I extract it to a folder. I read the Readme.html file which says to extract it then run the Blender executable.
I can see the Blender executable, but when I right click and choose Run, nothing happens. No errors, just does nothing. I'm definitely using the extracted file, not the unextracted tar.bz2 version. If I double-click, nothing happens. 
If I double click the readme.html file (in the same folder) it opens correctly.
I definitely downloaded the 64 bit Linux version of Blender.

I have no idea what to do next. When does the Ubuntu Software Centre get updated? It would be good to have a button which says "Check for latest version" or something like that.

???

---

### Post by su:bhatta on 2014-04-02
Is it absolutely necessary for you to run the latest Blender build? 
If not, then it is suggested to use the version of Blender that is available in the Ubuntu Software Center, coz that has been tested by Ubuntu  and is a stable version.

If you are trying to run the Executable from the tar.gz you have downloaded then right click on the File and see under properties if the permission is set right i.e. it is marked as executable.

See if that helps.
But using a latest buils for someone new to Linux is not advisable as you can run into errors that you may not be able to fix.
Hence, again I mention, use the version of Blender available in Ubuntu Software Center.

P.S.: blender.org says that latest version 2.70 requires glibc 2.11, if that is not installed in 13.10, you will not be able to run it.

---

### Post by scadger on 2014-04-02
Thanks for the quick reply. Yes I'm running Blender 2.7 on several other Windows machines with projects created in that version. I was hoping to install Ubuntu on a few machines to let them churn through the same projects but it looks like I'll have to revert to Windows or wait for the software to be Ubuntu approved.

---

### Post by su:bhatta on 2014-04-02
Well, did you see if the 'Is Executable' is checked under Properties-->Permissions? 
glibc 2.11 should be there in 13.10, if I remember correctly.

I am running the UbuntuStudio 14.04 Beta release and I am having Blender 2.69, and that should be the final version in the final 14.04 release. 
So, yes you may have to wait till 14.10 maybe to get blender version 2.7.

Also, there is no harm in seeing if the stuff you created with Blender 2.7 will run succesfully with Blender 2.66. Maybe all that is there in Blender 2.7 are bugfixes?

Have a look here : [http://wiki.blender.org/index.php/Dev:Ref/Release_Notes/2.70](http://wiki.blender.org/index.php/Dev:Ref/Release_Notes/2.70)
If you can live without those extra features give Blender 2.66 a try. :)

---

### Post by scadger on 2014-04-02
Thanks, yes Execute is checked. And all the permissions are set to "read and write". What I'm surprised about is that it does nothing. I would have thought there would be error messages or warnings but nothing happens. I can try the project in an older version to see as you suggest but would be good to get everything compatible. 

Thanks

---

### Post by 23dornot23d on 2014-04-02
There should not be a reason why you can run Blender 2.7 in Windows and not in Ubuntu 13.10 ..........

other than possibly the graphics not being set up to do so ........

What spec is the machine you are currently running it on - and what is installed in the Linux version you have.

Just out of interest what does the following show you when cut and pasted into a terminal window. ( then press return )

```

date && lsb_release -sd || cat /etc/*release &&  uname     -s -r && unity --version &&     /usr/lib/nux/unity_support_test -p && dpkg -s mesa-utils 				 			

```
__________________________________

 ....... is the idea to give Windows a head start ........ let them run Blender v 2.7 and get them into the routine
of always being first with Linux Software and running the latest version ........

I do not think so ...........

Lets run the new version of Linux software here - waiting for 14.10 ........ lols ;)

But here is a screen shot of it working in Ubuntu 12.04 I think that was what I was using at the time of this ....... 

[IMG]http://i.minus.com/inOnizRTsduwk.jpg[/IMG]

all the dependencies are in the file
that you unzipped ....

The problem you cannot run it may be to do with what you have installed .......

There is no harm in installing v2.66 ......... just to make sure you can run 3d ok in your
current setup ......... v2.70 will still run from its folder.

---

### Post by scadger on 2014-04-02
I tried v2.66 previously. It installed and ran fine from the software centre. I uninstalled it but will try it again.

Thks

---

### Post by scadger on 2014-04-02
It looks like you're using some sort of package manager there. Should I be using that?

---

### Post by 23dornot23d on 2014-04-02
No the synaptic package manager was just showing that I had the latest version on that system from the repository at its latest
version ... which in my case was 2.68a .......

But I use Blender a lot and got so used to having to keep installing different versions on the different platforms of Linux - then
I realized it does not have to be that way ......

All the files are there in the folder you download ... so it seems odd that the new version did not run for you and yet the old one
does .... as that seems to point to another problem ...... are you sure you are running the 64 bit version.

Try downloading the other (i686) 32 bit and see if that runs .... just to be sure ......

Usually you can run Blender from in a terminal and it will give you back any errors if there are any ........

which folder is it in ........ and we can run it directly from there in a terminal to see what if any errors it gives you back.

I have 2.69 running now 11.04 so I know later releases of Blender work ok in older versions ....

---

### Post by scadger on 2014-04-02
Its all in my "Documents" folder. It is extracted to its own folder "blender-2.70-linux-glibc211-x86_64" so I think its the correct version

---

### Post by 23dornot23d on 2014-04-02
I have just run the 32 bit version in 12.04 and that works fine ...... but I cannot as yet check the 64 bit to be sure it is ok 
but I did just run the 64 bit 2.69 in 64bit on 11.04 .......... maybe there is a problem with the 64bit 2.70 as that did not display.

[IMG]http://i.minus.com/i3oVbkPT45V7n.png[/IMG]


If you can open a terminal in your Documents directory and type 

> 

./blender



( see if it gives any other output ....... )

---

### Post by su:bhatta on 2014-04-02
I've just downloaded the Blender2.70 64 bit and it runs fine. Extracted it in Documents and clicked on Blender, it ran smooth .
Screenshot attached.

[ATTACH=CONFIG]251661[/ATTACH]

EDIT: Did you copy the file to some other partition like a NTFS and trying to run from there?
Because I just did that and found that it would not run from my Data partition, which is a NTFS partition.
Else, try to get a fresh download and see if that does the trick.

---

### Post by 23dornot23d on 2014-04-02
[                                                      [IMG]http://ubuntuforums.org/customavatars/avatar1819052_3.gif[/IMG]                                              ]("http://ubuntuforums.org/member.php?u=1819052")                                                                                     [**[COLOR=#000000]bhattabhishek[/COLOR]**]("http://ubuntuforums.org/member.php?u=1819052")

Cheers for doing that and checking it works .... 

I have been hunting for 13.10 to do a check ...... as the older version 11.04 was not a good place to really try from
although I do know for a fact 2.69 runs from there and as 64 bit.

[IMG]http://i.minus.com/iLf9oMGfECl0t.png[/IMG]

I only have a 64 bit 14.04 version which it runs alright in too ..........

---

### Post by su:bhatta on 2014-04-02
> **23dornot23d said:**
>        [**[COLOR=#000000]bhattabhishek[/COLOR]**]("http://ubuntuforums.org/member.php?u=1819052")

Cheers for doing that and checking it works .... 

I have been hunting for 13.10 to do a check ...... as the older version 11.04 was not a good place to really try from
although I do know for a fact 2.69 runs from there and as 64 bit.

I only have a 64 bit 14.04 version which it runs alright in too ..........
Hey Thanks, I got it running on my UbuntuStudio 14.04 AMD64  install :)

I am guessing, the OP has some problem with his download.

---

### Post by 23dornot23d on 2014-04-02
That is my initial thought too ..... that there is a problem with the download .... as the only other thing
is trying to run the 64bit on a 32bit system which will not work.

But there should be no real reason it does not run as far as I know the binary must be good as you and I have
it working on 64 bit ....... but in 14.04 .........

I have a 13.04 version but its 32 bit ... so that too proves nothing ..... so needs someone else with 13.10 to
just do a quick check - if anyone is online and wants to run the latest version of Blender.



@ scadger ...... please type this into a Lxterminal or xterm just for a quick check to make sure its a 64 bit installation.

**uname -a**

---

### Post by su:bhatta on 2014-04-02
I have a working Elementary OS installation, but that would be too old, being based on 12.04.
Another thing that comes to mind is : OP is making some mistake & running 13.10 32 bit or what?

I had no idea that Blender, being the powerful software that it is, runs without installing and is packaged so well.

---

### Post by 23dornot23d on 2014-04-02
**uname -a**

Will let us know what version and if its 64 bit or 32 bit ......... don't be worried about using the terminal to give some information back.

I got into a discussion about the packaging and this very subject of keeping users happy and uptodate by downloading a package with

everything needed in it ........ Blender was the one thing that seems packaged really really well other than Firefox of course ...... which

we can usually do the same thing with ....... download unpack and then just double click it to run it .........

[http://ubuntuforums.org/showthread.php?t=2214315&page=3](http://ubuntuforums.org/showthread.php?t=2214315&page=3)

that works - so this needs to work out ok otherwise it proves I was wrong ..... not that it matters too much ..... but I do like to get things right.

---

### Post by monkeybrain20122 on 2014-04-02
It works here too. Ubuntu 13.10 64 bit. 

As said,the package is self contained, it doesn't require any installation. You don't even need to do any terminal, just extract, open the blender folder and click blender and that's it, you can create a .desktop file if you want. (I don't know why people are giving instructions like going to the terminal, cd into blender directory and type ./blender, while it is simple click and play! While the terminal is powerful for many things, I consider this an abuse. :))

However, you may need to set permission for the executable (right click the file 'blender' and choose Properties > Permission and make sure that the box 'allow to execute .." is checked,--terminal people would tell you "chmod + x path_to_blender") If you are using nautilus, open the file manager, go to "Files" on the top panel and then in the drop down choose Preferences > Behaviour and choose "Ask each time" for Executable text files. The default 'display' makes no sense. Why do I want to stare at an executable file without being able to run it? (Ask each time should take care of the security considerations)

---

### Post by 23dornot23d on 2014-04-02
Cheers for checking it out .....

> 
It works here too. Ubuntu 13.10 64 bit. 

As said,the package is self contained, it doesn't require any  installation. You don't even need to do any terminal, just extract, open  the blender folder and click blender and that's it, you can create a  .desktop file if you want. (I don't know why people are giving  instructions like going to the terminal, cd into blender directory and  type ./blender, while it is simple click and play! While the terminal is  powerful for many things, I consider this an abuse. :smile:)


Lols .... the terminal still is the only thing that will show error messages up ............. properly ................. ( if there are  some to be seen )

I try not to use terminal commands when I know other ways of doing things ....... 
but if someone can point an old user into the new ways of getting error messages back then I am all ears ....... 

I also would like to know how you show the version and os without using the terminal ..... what do you go to - to find if its 64 bit
without using the terminal now ....... even System Monitor has removed the first screen with details on it .......

But its good to know that the 64 bit works in the 13.10 ( 64 bit release ) ....... that at least tells the Original Poster that the files
should be good ........ but now how do we get to see the error messages ........

[ also see post 5 ] its been made executable - [http://ubuntuforums.org/showthread.php?t=2214671&p=12975255#post12975255](http://ubuntuforums.org/showthread.php?t=2214671&p=12975255#post12975255)

Is there something you can type into Unity ......

---

### Post by monkeybrain20122 on 2014-04-02
> **23dornot23d said:**
> Cheers for checking it out .....



Lols .... the terminal still is the only thing that will show error messages up ............. properly ................. ( if there are  some to be seen )

I try not to use terminal commands when I know other ways of doing things ....... 
but if someone can point an old user into the new ways of getting error messages back then I am all ears ....... 

I also would like to know how you show the version and os without using the terminal ..... what do you go to - to find if its 64 bit
without using the terminal now ....... even System Monitor has removed the first screen with details on it .......

But its good to know that the 64 bit works in the 13.10 ( 64 bit release ) ....... that at least tells the Original Poster that the files
should be good ........ but now how do we get to see the error messages ........

Is there something you can type into Unity ......

Well if for some reasons things don't work and you need to read the error messages then of course you use the terminal. But I consider this trouble shooting rather than normal running. ;)

---

### Post by 23dornot23d on 2014-04-02
Maybe you missed this

> 
 			 				 				 					 						 	[**[COLOR=#000000]scadger[/COLOR]**]("http://ubuntuforums.org/member.php?u=1914452") 	 
 						[IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]  					 					 						First Cup of Ubuntu 					 					 						[IMG]http://ubuntuforums.org/images/rank_1.png[/IMG] 					                                           					 					 						 							     						
 					 				
 			
 			 				 					Join DateApr 2014Beans6 					 					 				
 			 		
 	  	 		 		 		 		[h=2]Re: Installing Blender software[/h] 		 				 				 		 			 				[INDENT] 					Thanks, yes Execute is checked. And all the permissions are set to  "read and write". What I'm surprised about is that it does nothing. I  would have thought there would be error messages or warnings but nothing  happens. I can try the project in an older version to see as you  suggest but would be good to get everything compatible. 

Thanks 				[/INDENT] 			
  			   		
 			 				 			 			 			 		
 	



---

### Post by monkeybrain20122 on 2014-04-02
I see. Ok.

---

