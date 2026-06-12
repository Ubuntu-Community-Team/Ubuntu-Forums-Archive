---
title: "aMSN 0.97RC1 with antialising+winks+webcam+chameleon Installation script(gutsy)"
date: 2007-10-29
forum: Outdated Tutorials &amp; Tips
---

### Post by gsiliceo on 2007-10-29
**[COLOR="Red"]Update: i've moved to Hardy Heron, and aMSN 0.97 final is in the repositories i'm afraid i can't test this script to help you gutsy users.[/COLOR]**

Hi everyone, i picked up this **script to install aMSN 0.97rc1 with winks, webcam, antialising and desktop integration**. in the spanish ubuntu forums and found it extremenly usefull. I translated it and added chameleon plugin support(for better desktop integration).

Here the description of the plugins i added to this script.

Desktop Integration plug-in for aMSN
For KDE or GNOME users. It shows desktop-like dialogs instead of tcl/tk ones. It also sets some options to fit better in the desktop.

Chameleon plug-in for aMSN
This plugin allows you to change aMSN look and feel using the Tile extension for Tk. This changes the way the toolkit looks so you might have a native, Qt or GTK2 look instead of Tk.

**It works in gutsy gibbon.**

*It's just a compilation of commands that you need to do to compile aMsn, but makes it easy because you just have to input your password a few times(or one if you are lucky) and nothing else.*

You just need to download it to your user folder, give it executing privileges(right click on the **icon>properties>permisions/privileges>allow execution**) and then in the terminal go the folder where you downloaded the script and do:
> ./aMSN_Installer.sh
Hope some of you find it useful.

[COLOR="Red"]**UPDATE**[/COLOR]
Thanks to Resadent (see posts 14 and 17) we have and update script that install the lastest stable aMSN(0.97 to the date of this edit) and an uninstaller. Cheers for him!

You can download them in the links below this line.

[COLOR="Red"]**UPDATE**[/COLOR]
There was a problem with Wish, a package needed to run aMSN that now has been fixed thanks to Resadent, now fixed in the latest script.

---

### Post by rebegin on 2007-10-29
hey, thanks for the script, it worked perfectly. should it work on a 64bit kubuntu version too?

---

### Post by fvds on 2007-10-29
Great script! Works like a charm!

---

### Post by gsiliceo on 2007-10-29
> **rebegin said:**
> hey, thanks for the script, it worked perfectly. should it work on a 64bit kubuntu version too?

Only in 32 bit version for now :( sorry.

It does work with ia32 libs installed, thx giorgosts

---

### Post by gardara on 2007-10-29
Good script.... But too bad how buggy amsn is...

---

### Post by giorgosts on 2007-10-30
> **gsiliceo said:**
> Only in 32 bit version for now :( sorry.

Works for me Kubuntu Gutsy AMD64 with ia32 libs installed.

Compiling source code shouldn't be a problem for different architectures, as long as the correct dependencies are met, and the right development tools installed.

---

### Post by vervelover on 2007-11-08
Hi, thank you for this it worked great! But, just in case, how do I uninstall it?

---

### Post by dn* on 2007-11-08
Users may find it easier to just install from the repositories:

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=amsn&searchon=names&version=all&release=all&exact=1](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=amsn&searchon=names&version=all&release=all&exact=1)

---

### Post by gsiliceo on 2007-11-08
True that, use them =)

---

### Post by pb_online on 2007-11-26
Very very good. Use it!

---

### Post by Brian031168 on 2007-12-10
How do I uninstall this?

---

### Post by mdpalow on 2007-12-16
You can upload another four files. Would you or anyone mind uploading 4 screenshots?

Thanks

---

### Post by giannis1_86 on 2008-02-06
awesome.........

---

### Post by resadent on 2008-02-06
I updated the script now it uses tcl/tk 8.5.1 and amsn 0.97 stable.:wink:

---

### Post by gsiliceo on 2008-02-06
With your permission ill add your script to the original post. With reference of course.

---

### Post by resadent on 2008-02-06
> **gsiliceo said:**
> With your permission ill add your script to the original post. With reference of course.
You have my permission. I think it has no errors, but you can revise it.

---

### Post by resadent on 2008-02-06
> **gsiliceo said:**
> With your permission ill add your script to the original post. With reference of course.

You have my permission. I think it has no errors but you can revise it.

EDIT:[QUOTE=Brian031168]How do I uninstall this?[/QUOTE]
AMSN:
sudo rm -Rf /usr/share/amsn
sudo rm -f /usr/bin/amsn
sudo rm -f /usr/bin/amsn-remote
sudo rm -f /usr/bin/amsn-remote-CLI
sudo rm -f /usr/share/applications/amsn.desktop
sudo rm -f /usr/share/pixmaps/amsn.png

TCL:
sudo rm -r /usr/lib/tcl8.5

TK:
sudo rm -r /usr/lib/tk8.5/

I am going to make a script called "uninstall".

;-)

---

### Post by gsiliceo on 2008-02-06
Excellent! I updated the original post, don't you just love the community here?

---

### Post by theodorebelousi on 2008-02-23
It's not a long time since I' installed Linux, so your help would be valuable.
I downloaded the file and wrote the command "sudo...". The installation completed, and as far as I can tell, aMSN had been reinstalled and a message at the end of the installation informed me that I could find it at Applications->Internet. However, when I click on the aMSN icon, nothing happens.

---

### Post by gsiliceo on 2008-02-23
Ok, use the uninstall script please, then
sudo apt-get install amsn
sudo apt-get remove amsn
And then install again
That combination should fix your problem.

---

### Post by theodorebelousi on 2008-02-23
Thank you for your immediate answer answer, but it doesn't seem to work. Do you have another idea?

---

### Post by gsiliceo on 2008-02-23
What happends when you input > amsn in the terminal?
Does it give you an error message?

---

### Post by theodorebelousi on 2008-02-23
I repeated the whole process again, and when I finished, there was no aMSN icon in the Applications->Internet menu.
When I input ```
amsn
``` it says that   amsn program is not installed.

---

### Post by gsiliceo on 2008-02-23
try > amsn2

---

### Post by theodorebelousi on 2008-02-23
To sum up:

I ran the install script without having uninstalled aMSN. It said the installation was successful and that I could find aMSN in the Applications->Internet menu. However, when I clicked the icon, nothing happened.

I afterwards ran the uninstall script, installed aMSN (sudo apt-get install amsn) and uninstalled it.

I ran once again the install script, which according to the terminal output was successful, but aMSN wasn't in Applications->Internet menu. When inputing ```
amsn
```
terminal printed that there wasn't any aMSN program.

I finally ran the uninstall script and installed the aMSN (sudo ... amsn), but when clicking Applications->Internet->aMSN, nothing happens.

In order to be more specific:
1. Every time I ran the install script, it seemed to download and install the aMSN.
2. Among all the commands, I restarted the system, just in case (because I am new to Linux, as I've said, and I wanted to be sure :oops: )
3. To be more... sure, I repeated all the above processes, without rebooting :oops: :oops: .
4. Just before asking me to choose which aMSN version I want to install, the terminal prints out: "rm: cannot remove `wish': No such file or directory". Moreover, at the end of the installation, it printed out:> unzip:  cannot find or open desktop_integration, desktop_integration.zip or desktop_integration.ZIP.
REMOVING INSTALLATION FILES
those are the only "problems" I could spot during the script performance.
5. When inputing "amsn2" (after running the install script again), it printed ou that this is an unknown command.

This script is really useful for users using greek and not only fonts, so your help would be valuable in the rare occasion that the script does not perform successfully.

Thank you in advance.

---

### Post by gsiliceo on 2008-02-23
Could you please post the outcome of this command
> locate wish

---

### Post by theodorebelousi on 2008-02-23
.> /usr/man/man1/wish.1
/usr/bin/wish
/usr/bin/wish8.5


---

### Post by gsiliceo on 2008-02-23
Ok do this and then try to start amsn.
cd /usr/bin
sudo rm wish
sudo ln -s wish8.5 wish
Well this is assuming you have amsn installed(with the script or using apt-get)

---

### Post by resadent on 2008-02-27
Did you miss me? I have done a revision of the script that fixes the problem with wish ;-)

---

### Post by gsiliceo on 2008-02-27
lol yeah, thx you are awesome i updated the original script

---

### Post by paneas13 on 2008-03-23
well if you try to download aMSN from Gutsy's repos then you will find out some unsolved problems. These problems interfere with fonts style and enconding of none English languages. For instance, i use Greek Ubuntu and I used to see enormous letters and missing characters. All my problems solved, by giving a try to this excellent script. Bravo!

---

### Post by Starlight on 2008-04-13
It's not working :( It seems to do everything without any errors, but the supposedly installed aMSN is not there... it doesn't appear in the menu, and when I type "amsn" in the console it says that amsn is not installed... :(

---

### Post by gsiliceo on 2008-04-13
I looked at it and yes it failed, thou i used to work.
Try again the script i fixed the problem.

---

### Post by Pa$aboku on 2008-05-01
i can't activate chameleon 
Plugin system: Can't initialize plugin:init procedure caused an internal error.
what's wrong?

---

### Post by gsiliceo on 2008-05-01
Im sorry i cant support this script no more, i've moved to hardy and the final version of amsn is there in the repositories.

---

### Post by sanone on 2008-05-08
Hi,

As most pidgin users I wanted video chat so I installed aMSN today. Later I found out about chameleon. Which seems like a good plugin for aMSN since in the tcl/tk is plain ugly!!!

I'm also using hardy and I was wondering if you got chameleon working under 8.04? I get this error:

```
Plugin system: Can't initialize plugin:init procedure caused an internal error.
```

I just read that the plugin is not maintained anymore ([source]("http://www.amsn-project.net/forums/viewtopic.php?t=618")) but perhaps it does still work for the time being.

Let me know.. 

Cheers,
San

---

### Post by gsiliceo on 2008-05-08
Sorry, tried and didnt worked, i've moved to **emesene** anyway, its way lighter than amsn, it uses gtk by default, it doesnt crash, the different user profiles work, winks, nudges, emoticons, send/recieve files work, i dont use webcam nor audio conversations so it doesnt matter to me that it doesnt support them(webcam is on the way thou), and the current song pluging works perfectly.

---

### Post by nikos.mathi on 2008-12-14
thanks

---

