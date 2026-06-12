---
title: "Last thing I need now is an Error Message"
date: 2016-09-09
forum: New to Ubuntu
---

### Post by oskar44 on 2016-09-09
It’s about a week I installed Ubuntu 16.04.1 desktop-amd64 in my laptop (using VMware desktop) and trying to find my way around. Have never used Linux / Ubuntu before so everything is quite new to me (been using Windows since 1987).
 
Today I opened Ubuntu and all was fine but after a couple of minutes I got this long error message: “Opening the cache (E:Malformed entry55 in list file/etc/apt/Sources.list(Component), This usually means that your installed packages have unmet dependencies. Please run package Manager from the right click menu or apt-get”
 
I don’t know what the above means so in the Terminal I typed apt-get and I got a few lines (sorry don’t remember them) and at the end it says “This apt has super Cow Powers”
 
Any help will be appreciated
Nicolas

---

### Post by oldfred on 2016-09-09
Super Cow Powers is an Easter egg. Terminal or text cow image.
```

fred@Asusz97:~$ apt-get moo
                 (__) 
                 (oo) 
           /------\/ 
          / |    ||   
         *  /\---/\ 
            ~~   ~~   


..."Have you mooed today?"...
```

Check line 55 in /etc/apt/sources.list.

sudo nano /etc/apt/sources.list

---

### Post by oskar44 on 2016-09-09
Thanks for the help but not sure what you are asking me to do
 
When I type apt-get moo I get the same image as you do
 
When I type sudo nano/etc/apt/sources.list I get &#8220;command not found&#8221;
 
Perhaps nano means something else? (don&#8217;t have such a directory)

---

### Post by &amp;KyT$0P# on 2016-09-09
> **oskar44 said:**
> When I type sudo nano/etc/apt/sources.list I get “command not found”
Because you're missing a space after "nano"

---

### Post by mikodo on 2016-09-09
like above

```
sudo nano /etc/apt/sources.list
```
That may show something causing the error in line 55.

---

### Post by Geoffrey_Arndt on 2016-09-09
Nano is not a directory, it is a text editor.   

So, many programs such as "gedit" can be used to edit the sources.list text configuration file.   Text files are the main type of file used in the "etcee" (/etc) directory for configuring many aspects of the desktop or core applications in Linux.

---

### Post by oskar44 on 2016-09-10
Thanks to all for the help and I apologize for my ignorance
 
So I got the command working and now I have an empty Terminal window and at the bottom of this window there are many commands but I don&#8217;t know how to activate them
 
For example I see one of them says &#8220;Go to Line&#8221; and I assume if I could activate that command I will put 55 (for line 55) and see the results but whatever I tried it doesn&#8217;t work
 
How do I activate the command and how do I get line 55?

---

### Post by howefield on 2016-09-10
It should be an empty file, are you sure you typed the command correctly (with no capitalisation as in your first post). I'd come out of that with Ctrl + X keys and not save it when prompted.

Try this command..

```
sudo apt edit-sources
```  

Then press enter to select option 2 which is nano, your sources.list file should now be opened.

Might be easier to post the contents of the file here so someone can tell you exactly which lines to remove/comment out/fix.

---

### Post by oskar44 on 2016-09-10
I don’t know why but I retyped sudo nano /etc/apt/sources.list and now I got a screen full of text. I sniped that screen and I post here the .JPG file because I don’t know which file to post here as requested.
 
I also typed sudo apt edit-sources and I got the 4 options but before I hit enter to select the default(2) there was a message: “E: Malformed entry 55 in list /etc/apt/sources.list (Component). Failed to parse /etc/apt/sources.list. Edit again?

---

### Post by oldrocker99 on 2016-09-10
Yes, edit again; you need to put # at the beginning of line 55 (I think). Use "(W)here is" in nano to find 55. The # will make the line to be ignored.

---

### Post by howefield on 2016-09-10
> **oskar44 said:**
> I don’t know why but I retyped sudo nano /etc/apt/sources.list and now I got a screen full of text. I sniped that screen and I post here the .JPG file because I don’t know which file to post here as requested.
 
I also typed sudo apt edit-sources and I got the 4 options but before I hit enter to select the default(2) there was a message: “E: Malformed entry 55 in list /etc/apt/sources.list (Component). Failed to parse /etc/apt/sources.list. Edit again?

As oldrocker99 said a # sign at the front of the offending line would "comment" it out so it isn't used. The .jpg image you posted stops short of line 55 so it is unknown as to what it is as yet.

Perhaps an easier way to get you up and running would be to create a fresh sources.list file, there are a number of ways to do this, but the easiest might be to use the following terminal commands..

```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
```

which will keep your sources.list, rename it but not use it, and then

```
sudo cp /etc/apt/sources.list.save /etc/apt/sources.list
```

which will make the .save copy of the sources.list the one that is actually used.

You should then be good to go.

---

### Post by oskar44 on 2016-09-10
Sorry, I don’t understand. Is it possible to tell me what I should type in the Terminal?
 
I use: sudo nano W#55 and I get a screen with nothing

---

### Post by oskar44 on 2016-09-10
I just noticed the last post, I will do the commands and post the results

Thanks

---

### Post by oskar44 on 2016-09-10
That did the trick, thank you
 
BTW I have downloaded the "Ubuntu 16.04 Getting Started with.pdf" and that&#8217;s a good start to learn however there is nothing in there about the terminal syntax / commands. Is there another guide for beginners to learn at least the basics to work with the Terminal?

---

### Post by howefield on 2016-09-10
> **oskar44 said:**
> That did the trick, thank you

Cool, glad you got it.

However we do not know what you did to your system that resulted in the error. If you want to move on and forget it, that's fine. If you want to understand what went wrong you could try the following command..

```
tail -n 20 /ect/apt/sources.list.old
``` 

that will list the last 20 lines of your sources.list.old file (formerly the sources.list) - highlight all text in the terminal and right click and select copy, then paste into a post back here and someone will tell you what went wrong. Hopefully you have no more than 75 lines in the file :)
 
> BTW I have downloaded the "Ubuntu 16.04 Getting Started with.pdf" and that&#8217;s a good start to learn however there is nothing in there about the terminal syntax / commands. Is there another guide for beginners to learn at least the basics to work with the Terminal?

A million and one youtube videos, none I'd recommend in particular but there are loads that will take you from the basics right up to pretty advanced.

Also, there is this thread in the forums [https://ubuntuforums.org/showthread.php?t=1624385](https://ubuntuforums.org/showthread.php?t=1624385) that will give you some links, fairly old but the links will still be good in the main, there are a ton of others that you can search out.

---

### Post by Geoffrey_Arndt on 2016-09-10
Oskar,  for the newbie, editing text config files may only happen once in a "blue moon" . . . or like once or twice in a year or two or three even.

SO, I fail to see the point of using Nano (or similar editors at all like vi, emacs, and so on).   **Not** user friendly.   You can use a standard text editor like "gedit" - - get a normal wysiwig and then do your editing and save.   

Re learning the CLI (command line interface) (aka Linux "Terminal" or Linux "Konsole" . . )  - - well, the best way is to attend University and take CompSci.    Short of that there are many websites and even youtube videos that offer CLI tutorials.   BUT . . . CLI is absolutely NOT required to be a home Linux user.   On some occasions, it can make life easier for the enthusiast and IS required for a Linux or Systems Admin . . but for home user . . . heck no.

CLI is very useful, fast and can do things the GUI interface cannot - - but I know users that run Linux and haven't opened a Terminal (Alt+Ctrl+T) _in years_ (. . . really).   BTW, the offical "sources file" can be modified entirely via the Ubuntu furnished desktop GUI.

---

### Post by oskar44 on 2016-09-10
> **howefield said:**
> Cool, glad you got it.

However we do not know what you did to your system that resulted in the error. If you want to move on and forget it, that's fine. If you want to understand what went wrong you could try the following command..

```
tail -n 20 /ect/apt/sources.list.old
``` 

I didn’t know we can do that but it’s too late now because I re installed Ubuntu. I think I created the problem because at the same time I installed Ubuntu I also installed Linuxcnc for my cnc mill and I was trying some commands on Linuxcnc and probably instead of applying them on Linuxcnc I did then on Ubuntu.
 
I found the Linuxcnc very complicated to configure my cnc mill and I gave up however my intentions are to get comfortable with Ubuntu and after give another try on Linuxcnc.

The link you provided to learn is fantastic and appreciated

---

### Post by oskar44 on 2016-09-10
Thank you Geoggrey for your input however I&#8217;m a guy who likes to go into the &#8220;nuts and bolts&#8221; of almost anything. I kind of suspect what nano is and your advice to go with gedit / wysiwyg is good but I still have to know how / what to edit on a config file.
 
I&#8217;m not an expert either in Microsoft command prompt but I do a lot of work on it and when I stumble I still have the 430 pages MS-DOS users guide published in 1987 to give me a hand + Google.
 
Learning the CLI will be a challenge but I don&#8217;t intend to be an expert with it, just to know the basics will be sufficient for me.
 
Windows10 was the turning point for me because with that OS Microsoft had a better control of my PC than I do and that&#8217;s something I can&#8217;t accept. So it&#8217;s time for a change

---

### Post by Geoffrey_Arndt on 2016-09-11
OK, if you're open to the learning curve - - then all is good.   Just didn't want you to have the impression it was required for functional use of Ubuntu.   I learned (and forgot since) many CLI commands on a DEC PDP/1011 Mini-Mainframe (Unix).   At that time, there were 3 methods of input/communication with the host (but no GUI).

Here is a site that might be interesting and useful - - [https://linuxjourney.com/](https://linuxjourney.com/)

---

### Post by howefield on 2016-09-11
> **oskar44 said:**
> I didn’t know we can do that but it’s too late now because I re installed Ubuntu. I think I created the problem because at the same time I installed Ubuntu I also installed Linuxcnc for my cnc mill and I was trying some commands on Linuxcnc and probably instead of applying them on Linuxcnc I did then on Ubuntu.
 
I found the Linuxcnc very complicated to configure my cnc mill and I gave up however my intentions are to get comfortable with Ubuntu and after give another try on Linuxcnc.

The link you provided to learn is fantastic and appreciated

Good luck and you're welcome, looks as if Linuxcnc is better run as a dual boot installed alongside Ubuntu rather than installed within it. In any event, if and when you get back to it just post the questions if you need help :)

One thing I found helpful is to take an image of the Ubuntu partition/disk with something like Clonezilla which is good insurance for when you break your installation and want to quickly get back to a "pristine" working state. I don't offer it as a backup tool given that it is just a snapshot in time which can age fairly quickly, I have data and documents separate to the operating system on another partition so taking an image is only of the operating system, even if it has aged a little the worst I need to do is run the system updater.  Not for everyone, just a suggestion.

---

### Post by oskar44 on 2016-09-11
Geoffrey the link is an eye opener on Linux, many thanks.
 
Howefield I had the Linuxcnc installed in an old desktop in my workshop and Ubuntu is installed in a laptop I have in my home office. The laptop is running Windows 8.1 and I have a virtual PC on it (VMware Workstation) where I have installed Ubuntu among other OS&#8217;s.
 
Good thing you mentioned Clonezilla because I didn&#8217;t know about it and definitely I will check it up later. I always backing up my systems and have used almost all available Windows back up programs in the past but I found the Macrium Reflect the best. I have a 1.5TB Seagate USB HD where I do all my backups regularly but for the Ubuntu I find it easier for now to re install it from the  .iso I made on a DVD.
 
I follow the same strategy as you do, OS in one partition and everything else in another partition

---

