---
title: "cant open Ubuntu software center or synaptic package manager"
date: 2014-05-15
forum: New to Ubuntu
---

### Post by Ody_Mishael on 2014-05-15
i cant open either one of them this is what the error says when i open synaptic:


E: Malformed line 7 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by slickymaster on 2014-05-15
Hi Ody_Mishael, welcome to the forums.

Can you please open a terminal window and run the following:```

cat /etc/apt/sources.list
```and then post back in this thread the output you got.

---

### Post by Ody_Mishael on 2014-05-15
> **slickymaster said:**
> Hi Ody_Mishael, welcome to the forums.

Can you please open a terminal window and run the following:```

cat /etc/apt/sources.list
```and then post back in this thread the output you got.

THanks, alot4 you help. here it is

(precise)ody@localhost:~$ cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
deb [http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu](http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu) main
deb-src [http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu](http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu) main
deb [http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu](http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu) 12.04 main
deb-src [http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu](http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu) 12.04 main

---

### Post by Ody_Mishael on 2014-05-15
bttw i was trying to follow a tutorial on when this happened the tutorial was on how to get Kali linux tools on Ubuntu but it didnt work and the this is what happend

---

### Post by slickymaster on 2014-05-15
> **Ody_Mishael said:**
> THanks, alot4 you help. here it is

(precise)ody@localhost:~$ cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
deb [http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu](http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu) main
deb-src [http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu](http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu) main
deb [http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu](http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu) 12.04 main
deb-src [http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu](http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu) 12.04 main

Is just that the content of your sources list? Please run the following in the terminal:```
cat /etc/apt/sources.list > list.txt
```and afterwards copy/past here the content of the list.txt file

---

### Post by Ody_Mishael on 2014-05-15
> **slickymaster said:**
> Is just that the content of your sources list? Please run the following in the terminal:```
cat /etc/apt/sources.list > list.txt
```and afterwards copy/past here the content of the list.txt file


noting happens when i type this in the terminal [COLOR=#000000][FONT=Ubuntu Mono]cat /etc/apt/sources.list > list.txt[/FONT][/COLOR]

---

### Post by Ody_Mishael on 2014-05-15
when i type this [COLOR=#000000][FONT=Ubuntu Mono]cat /etc/apt/sources.list 

[/FONT][/COLOR]
[COLOR=#000000]*deb *[/COLOR][http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)[COLOR=#000000]* precise main restricted universe multiverse*[/COLOR]
[COLOR=#000000]*deb-src *[/COLOR][http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)[COLOR=#000000]* precise main restricted universe multiverse*[/COLOR]
[COLOR=#000000]*deb *[/COLOR][http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)[COLOR=#000000]* precise-updates main restricted universe multiverse*[/COLOR]
[COLOR=#000000]*deb-src *[/COLOR][http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)[COLOR=#000000]* precise-updates main restricted universe multiverse*[/COLOR]
[COLOR=#000000]*deb *[/COLOR][http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)[COLOR=#000000]* precise-security main restricted universe multiverse*[/COLOR]
[COLOR=#000000]*deb-src *[/COLOR][http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)[COLOR=#000000]* precise-security main restricted universe multiverse*[/COLOR]
[COLOR=#000000]*deb *[/COLOR][http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu](http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu)[COLOR=#000000]* main*[/COLOR]
[COLOR=#000000]*deb-src *[/COLOR][http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu](http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu)[COLOR=#000000]* main*[/COLOR]
[COLOR=#000000]*deb *[/COLOR][http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu](http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu)[COLOR=#000000]* 12.04 main*[/COLOR]
[COLOR=#000000]*deb-src *[/COLOR][http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu](http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu)[COLOR=#000000][I] 12.04 main

this is what shows up[/I][/COLOR]

---

### Post by slickymaster on 2014-05-15
> **Ody_Mishael said:**
> noting happens when i type this in the terminal [COLOR=#000000][FONT=Ubuntu Mono]cat /etc/apt/sources.list > list.txt[/FONT][/COLOR]

After running that command a file named **list.txt** is created in your home folder. Just open it and copy/past its content here.

---

### Post by Ody_Mishael on 2014-05-15
> **slickymaster said:**
> After running that command a file named **list.txt** is created in your home folder. Just open it and copy/past its content here.

ahh ok,, here is what was in it:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
deb [http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu](http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu) main
deb-src [http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu](http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu) main
deb [http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu](http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu) 12.04 main
deb-src [http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu](http://ppa.launchpad.net/wagungs/kali-linux2/ubuntu) 12.04 main

---

### Post by slickymaster on 2014-05-15
There's something strangely wrong with your sources list.

I would recommend you to completely replacing the content with another sources.list file with repository entry from Main Server:
[LIST=1]
[*]Go to the Ubuntu sources list generator site [here]("http://repogen.simplylinux.ch/")
[*]Select your country
[*]Select your desired branches, such as Main, Restricted, Multiverse, Universe,
[*]Select desired update list
[*]Select any third party repository list if you wish,
[*]Click Generate list at the bottom of the page, you will be given a list with repositories,
[*]Copy that list and replace with **sources.list** file you have.
[/LIST]

---

### Post by Ody_Mishael on 2014-05-15
> **slickymaster said:**
> There's something strangely wrong with your sources list.

I would recommend you to completely replacing the content with another sources.list file with repository entry from Main Server:
[LIST=1]
[*]Go to the Ubuntu sources list generator site [here]("http://repogen.simplylinux.ch/")
[*]Select your country
[*]Select your desired branches, such as Main, Restricted, Multiverse, Universe,
[*]Select desired update list
[*]Select any third party repository list if you wish,
[*]Click Generate list at the bottom of the page, you will be given a list with repositories,
[*]Copy that list and replace with **sources.list** file you have.
[/LIST]


ok how do i replace it?

---

### Post by Ody_Mishael on 2014-05-15
this is what i got:

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################


###### Ubuntu Main Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main 


###### Ubuntu Update Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security main 


how do i replace it?

---

### Post by slickymaster on 2014-05-15
> **Ody_Mishael said:**
> ok how do i replace it?

After hitting the “Generate List” button, you'll be redirected to another page page where you should see three big boxes. The first box at the top contains the sources list that you have selected and you will need to copy/paste them into your **sources.list** file. In your terminal run the following:```
gksu gedit /etc/apt/sources.list
```Save and exit.
If you have added third party software’s PPA, it will show you the PPA key that you need to add to your system. Run the commands in your terminal, line by line.
To complete the process, you need to update and upgrade your system:```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Ody_Mishael on 2014-05-15
> **slickymaster said:**
> After hitting the “Generate List” button, you'll be redirected to another page page where you should see three big boxes. The first box at the top contains the sources list that you have selected and you will need to copy/paste them into your **sources.list** file. In your terminal run the following:```
gksu gedit /etc/apt/sources.list
```Save and exit.
If you have added third party software’s PPA, it will show you the PPA key that you need to add to your system. Run the commands in your terminal, line by line.
To complete the process, you need to update and upgrade your system:```
sudo apt-get update && sudo apt-get upgrade
```

sorry, im having a hard time understanding is this correct?
so i should paste this in list.txt:

[COLOR=#000000]deb [/COLOR][http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)[COLOR=#000000] precise main [/COLOR]
[COLOR=#000000]deb [/COLOR][http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)[COLOR=#000000] precise-security main 

and then type this in the terminal:
[/COLOR]gksu gedit /etc/apt/sources.list

---

### Post by slickymaster on 2014-05-15
> **Ody_Mishael said:**
> sorry, im having a hard time understanding is this correct?
so i should paste this in list.txt:

[COLOR=#000000]deb [/COLOR][http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)[COLOR=#000000] precise main [/COLOR]
[COLOR=#000000]deb [/COLOR][http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)[COLOR=#000000] precise-security main 

and then type this in the terminal:
[/COLOR]gksu gedit /etc/apt/sources.list

No, the output you got from the first box in the Ubuntu Sources List Generator site should be pasted into your **/etc/apt/sources.list** file. For you, to be able to edit that file you have first to run```
gksu gedit /etc/apt/sources.list
```which will open it and will allow to edit and save it.

---

### Post by Ody_Mishael on 2014-05-15
> **slickymaster said:**
> No, the output you got from the first box in the Ubuntu Sources List Generator site should be pasted into your **/etc/apt/sources.list** file. For you, to be able to edit that file you have first to run```
gksu gedit /etc/apt/sources.list
```which will open it and will allow to edit and save it.

when i type this into the terminal nothing opens?
gksu gedit /etc/apt/sources.list

---

### Post by slickymaster on 2014-05-15
> **Ody_Mishael said:**
> when i type this into the terminal nothing opens?
gksu gedit /etc/apt/sources.list

Perhaps you don't have gedit installed as your text editor. Do you know what text editor you have installed?

---

### Post by Ody_Mishael on 2014-05-15
> **slickymaster said:**
> Perhaps you don't have gedit installed as your text editor. Do you know what text editor you have installed?

Notepad

---

### Post by slickymaster on 2014-05-15
> **Ody_Mishael said:**
> Notepad

I must confess that I don't know that text editor, but all you have to do is to replace the term gedit in the command with the name of your text editor:```
gksu name_of_text_editor /etc/apt/sources.list
```

---

### Post by Ody_Mishael on 2014-05-15
> **slickymaster said:**
> I must confess that I don't know that text editor, but all you have to do is to replace the term gedit in the command with the name of your text editor:```
gksu name_of_text_editor /etc/apt/sources.list
```


awesome!! it worked!! at first i tried with notepad and it opened up a different notepad that i had with wine and it didn't work it said no path found i was about to give up,, then i found out i had another text editor called mousepad and it worked!
thanks a ton for your help!

---

