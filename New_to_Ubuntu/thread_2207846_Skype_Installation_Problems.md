---
title: "Skype Installation Problems"
date: 2014-02-25
forum: New to Ubuntu
---

### Post by Bob_Lade on 2014-02-25
Hi guys. I'm new to Ubuntu and Linux. I installed version 12.04LTS on my Acer netbook with absolutely no problems. I have it runing alongside my soon-to-be-obsolete Windows XP. So, here's what i've done so far.

I have gone to the Skype site and downloaded the recommended version. The download seems to go OK and I eventually was asked for my password which I typed in. The program seemed to be installing, but when it was complete (and the page said "installed") I was returned to the software center. I then closed the software center and firefox and looked on the launcher and there was no skype icon. I see that i did infact download the file because i can find it in the files and folders section of Ubuntu. I have tried re-installing it and then I re-downloaded it and tried again. Same results.

I then did some reading here on the forum and found some posts by Ian-Weisser who suggested going to the "terminal" and entering this code:

sudo apt-add-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) $(lsb_release -sc) partner"   and
sudo apt-get update && sudo apt-get install skype

After reading up a little on "Terminal" (kinda like the old DOS prompt in Windows) I entered the code and got the following error message:

E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

Basically, I wanted to use Linux to resurrect this old net book and use it pretty much just for Skype, so I really would like to get this working. Any help would be greatly be appreciated.

-Dr. Bob

---

### Post by oldrocker99 on 2014-02-25
For what it is worth, I personally (and the rest of my family) prefer Google Hangouts to Skype. The video and audio are superior to Skype, and it's built right into Chrome (with the installation of a talk plugin). Don't listen to Microsoft with their usual tone-deaf "scroogled" FUD. Microsoft owns Skype, and I personally mistrust them more than I do mistrust Google.

FWIW.

---

### Post by Bob_Lade on 2014-02-25
rocker I agree with you. unfortunately a number friends use Skype so I'm stuck with that program. thanks for your comments.

---

### Post by ibjsb4 on 2014-02-25
> E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)

Whats on line 56?

```
cat -n /etc/apt/sources.list
```

---

### Post by mikewhatever on 2014-02-25
Let's look at the end of your sources list, and figure out what's wrong. Can you post the output of -
```

tail /etc/apt/sources.list

```

---

### Post by Bob_Lade on 2014-02-25
I guess I don't know what I'm doing. I typed ur code into terminal and here's what i get:

bob@Muffin:~$ cat -n etc/apt/sources.list
cat: etc/apt/sources.list: No such file or directory

---

### Post by chris_dummer on 2014-02-25
try to google skype ver 4.2.0.11 for unix and install that the latest download ver 4.2.0.13-1 did not work from the skype download page on my system(an old ibm think centre resurected with ubuntu)
all ok apart from ocasionall sound breakup.
good luck.

---

### Post by ibjsb4 on 2014-02-25
> **Bob_Lade said:**
> I guess I don't know what I'm doing. I typed ur code into terminal and here's what i get:

bob@Muffin:~$ cat -n etc/apt/sources.list
cat: etc/apt/sources.list: No such file or directory

You missed a slash.  copy and paste

---

### Post by Bob_Lade on 2014-02-25
Here's what I get:

bob@Muffin:~$ tail /etc/apt/sources.list
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.canonical.com/](http://archive.canonical.com/) partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
bob@Muffin:~$

---

### Post by Bob_Lade on 2014-02-25
OK, Here's the list:

  43    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
    44    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    51    # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    56    deb [http://archive.canonical.com/](http://archive.canonical.com/) partner
    57    deb-src [http://archive.canonical.com/](http://archive.canonical.com/) partner
    58    deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
    59    deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
    60    deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
bob@Muffin:~$

---

### Post by ibjsb4 on 2014-02-25
Comment out (#) lines 56 and 57.

```
gksudo gedit /etc/apt/sources.list
```

Make a backup first:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
```

---

### Post by Bob_Lade on 2014-02-25
[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar1729120_35.gif[/IMG]]("http://ubuntuforums.org/member.php?u=1729120")[**[COLOR=#000000]ibjsb4[/COLOR]**]("http://ubuntuforums.org/member.php?u=1729120") 	 

 						[IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-online.png[/IMG]: After I comment out lines 56 and 57 what would be the next step? I'm so new to Terminal and forgot all the Unix I once know that I'm reading frantically to re-learn the commands. so I'll make a copy of the list and comment out the lines. Then what?  by the way, I appreciate the time you are taking to help me...

-Dr. Bob

---

### Post by ibjsb4 on 2014-02-25
Do an update after, that one problem should now be cleared.  Please ask questions, glad to explain :)

---

### Post by newb85 on 2014-02-25
I believe lines 56 through 59 should have "ubuntu" after the "http://archive.canonical.com/" (with no space between) similar to line 50.

---

### Post by Bob_Lade on 2014-02-25
[COLOR=#DD4814][COLOR=#000000][ibjsb4]("http://ubuntuforums.org/member.php?u=1729120"):  OK, I'll make a copy of the list, comment out lines 56 and 57. Then do an "update" How do I do the update? (sorry for the stupid questions, I've only been running Linux for about 20 hours now so I'm pretty green.)

-Dr. Bob[/COLOR][/COLOR]

---

### Post by newb85 on 2014-02-25
```
 sudo apt-get update 
```

---

### Post by ibjsb4 on 2014-02-25
> **Bob_Lade said:**
> [COLOR=#DD4814][COLOR=#000000][ibjsb4]("http://ubuntuforums.org/member.php?u=1729120"):  OK, I'll make a copy of the list, comment out lines 56 and 57. Then do an "update" How do I do the update? (sorry for the stupid questions, I've only been running Linux for about 20 hours now so I'm pretty green.)

-Dr. Bob[/COLOR][/COLOR]

No problem

```
sudo apt-get update && sudo apt-get upgrade
```

Here's a handy list:

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by ibjsb4 on 2014-02-25
You also have manuals installed by default.

```
man apt-get
```

or try this

```
man man
```

Use your arrow keys.

Put "man" then name of package

---

### Post by Bob_Lade on 2014-02-25
OK, now when I do an gedit  I get a black screen with black text. is there a way to change the text or bg color so i can see what I'm trying to edit?

---

### Post by ibjsb4 on 2014-02-26
> OK, now when I do an gedit I get a black screen with black text. is there a way to change the text or bg color so i can see what I'm trying to edit? 

Thats another problem that needs to be resolved, but first lets get you updated.  An update can solve problems.  So lets just use another editor instead of "gedit" just use "nano" editor.

```
sudo nano /etc/apt/sources.list

```
[https://help.ubuntu.com/community/Nano](https://help.ubuntu.com/community/Nano)

Do backup first

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
```

---

### Post by Bob_Lade on 2014-02-26
[COLOR=#000000]ibjsb4: Thanks. I'll try the new editor, but I had a crash so I've been spending my time re-installing 12.04 LTS and now I'm back to the beginning. I'll tackle the Skype installation next and let you now how it goes. Again, thanks for all your help!

-Dr. Bob[/COLOR]

---

### Post by Bob_Lade on 2014-02-26
OK, I now have a fresh copy of Ubuntu 12.04 LTS installed and I went to the "Software Center" and added the canonical sources so my current sources.list file looks like the below. But after doing that I don't see Skpe listed as an available package to install. So I guess I need to take the next step, whatever that isl Here's what the sources.list file looks like:

bob@Muffin:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release i386 (20140204)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
bob@Muffin:~$ 

Thanks again for your help. i am slowly learning how to navigate around with the command lines. Takes me way back to my old VMS days...

-Dr. Bob

---

### Post by Bob_Lade on 2014-02-26
Wow! Good things come to those who wait! This afternoon I went into the Software Center and Voila! there was the Skype client. I opened it and it works fine. I guess it takes time for the Software Center to populate the outside clients... Thanks to all for all the help. this was a great exercise to learn about some of the inner workings of Linux/Ubuntu.

I don't know how to mark this issue as closed, but will someone do that for me? thanks!!!

-Dr. Bob

---

### Post by artie3 on 2014-03-05
Hi Bob,

I had a similar issue when I tried to install skype from the skype web page. I ended up downloading it as suggested in your first post (after adding the canonical ppa).

Everything worked for me, after I did a sudo apt-get purge skype. The skype install from skype.com failed, but left related files on your system. Using the 'purge' command cleaned out all the aborted install files.

I also recently learned about Ekiga, which works far better than skype and google voice. It's free and open source, and has no BIG BROTHER syndrome/privacy issues. 

Enjoy.

Artie

---

