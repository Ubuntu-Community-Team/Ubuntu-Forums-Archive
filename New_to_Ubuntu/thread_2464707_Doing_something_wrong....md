---
title: "Doing something wrong..."
date: 2021-07-09
forum: New to Ubuntu
---

### Post by Innernet on 2021-07-09
Hi.
A guide to install Chrome browser ----> [http://lubuntuhowto.blogspot.com/2018/06/how-to-install-google-chrome-on-lubuntu-1804.html](http://lubuntuhowto.blogspot.com/2018/06/how-to-install-google-chrome-on-lubuntu-1804.html)

tells me how to; and the result is error. How to fix it ?

[sudo] password for externet: 
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal InRelease
Reading package lists... Done
externet@externet-presariocq57notebookpc:~$ sudo apt-get install fonts-liberation
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fonts-liberation is already the newest version (1:1.07.4-11).
fonts-liberation set to manually installed.
The following packages were automatically installed and are no longer required:
  fonts-beng-extra fonts-deva-extra fonts-gargi fonts-gubbi
  fonts-gujr-extra fonts-guru-extra fonts-kalapi fonts-nakula fonts-navilu
  fonts-orya-extra fonts-sahadeva fonts-samyak-deva fonts-samyak-gujr
  fonts-samyak-mlym fonts-samyak-taml fonts-sarai fonts-smc-anjalioldlipi
  fonts-smc-chilanka fonts-smc-dyuthi fonts-smc-gayathri fonts-smc-karumbi
  fonts-smc-manjari fonts-smc-meera fonts-smc-rachana fonts-telu-extra
  fonts-yrsa-rasa
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
externet@externet-presariocq57notebookpc:~$ sudo dpkg -i ~/Downloads/google-chrome-stable_current_amd64.deb
dpkg: error: cannot access archive '/home/externet/Downloads/google-chrome-stable_current_amd64.deb': No such file or directory
externet@externet-presariocq57notebookpc:~$ 


As I never remember how to paste the terminal properly, the above is its text paste.   To paste the terminal, instructions found say  :

2.) Make the console terminal window fullscreen, click edit, select all, click edit again, select copy (or Ctrl+Insert), then click in the post or reply, click the toolbar's code button, right click and paste (or Shift+Insert). Tip: you can type "clear" to clear the contents of the terminal before running a new command, if you want.

And of course, there is no "select all" on the 'edit' choice.   Selecting all by passing the mouse over text, yields the text copied.  So pasted the terminal text instead as above.

---

### Post by deadflowr on 2021-07-09
Try 
```
cd Downloads
sudo apt install ./google-chrome-stable_...
```
The trick is to press the tab button to use tab completion, which will only complete the file name if it exists.
Probably press it after goo, or google.

File names with the same first letters require you to write out more of the file name,
as tab completion won't know which file name to use until your output is unique among them.
The trick for that is if when you press tab nothing happens, try double-pressing it and if there are multiple files with the character strings you've entered exist, 
it'll output those in a listing.
And if nothing happens when you double press, it means the filename you typed is wrong, or does not exist in the current folder.

---

### Post by grahammechanical on 2021-07-09
Have you actually downloaded the google chrome installer package? Either from the Google download page or by the command line?

```
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
```

```
sudo dpkg -i google-chrome-stable_current_amd64.deb
```

We need a Google repository to be listed in a sources.list file and the chrome installer makes that edit to the sources.list file.

[https://www.omgubuntu.co.uk/how-to-install-google-chrome-on-ubuntu](https://www.omgubuntu.co.uk/how-to-install-google-chrome-on-ubuntu)

Regards

---

### Post by Impavidus on 2021-07-09
You're running Lubuntu 20.04, which is good, as Lubuntu 18.04 has already reached end of life. The instructions you linked to are for Lubuntu 18.04 (or Ubuntu, as it's the same for all flavours). The instructions don't necessarily apply to 20.04 and indeed are overly complex (although they should work). After downloading the package, deadflowr's command is all you need. If this is properly packaged, there should be no need to install that font first. I don't think you need the Canonical Partners repository either.

The error message indicates you didn't download the .deb file, or saved it in a directory other than your Downloads directory, or saved it under a different name.

---

### Post by Innernet on 2021-07-09
Thanks, gentlemen.  
Trying to follow deadflower, me, the flag bearer of compfuser idiots gets :

externet@externet-presariocq57notebookpc:~$ cd Downloads                                                  
externet@externet-presariocq57notebookpc:~/Downloads$ sudo apt install ./google-chrome-stable_
[sudo] password for externet:                                                                                                         
Reading package lists... Done                                                                                                         
E: Unsupported file ./google-chrome-stable_ given on commandline                                                                      
externet@externet-presariocq57notebookpc:~/Downloads$ 



Following grahammechanical, got the terminal text :

externet@externet-presariocq57notebookpc:~$ wget [https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb](https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb)
--2021-07-09 14:26:29--  [https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb](https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb)
Resolving dl.google.com (dl.google.com)... 2607:f8b0:4009:804::200e, 142.250.190.46
Connecting to dl.google.com (dl.google.com)|2607:f8b0:4009:804::200e|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 83565736 (80M) [application/x-debian-package]
Saving to: &#8216;google-chrome-stable_current_amd64.deb&#8217;

google-chrome-stable_current_amd6 100%[===========================================================>]  79.69M  4.08MB/s    in 20s     

2021-07-09 14:26:49 (3.99 MB/s) - &#8216;google-chrome-stable_current_amd64.deb&#8217; saved [83565736/83565736]

externet@externet-presariocq57notebookpc:~$ sudo dpkg -i google-chrome-stable_current_amd64.deb
[sudo] password for externet: 
Selecting previously unselected package google-chrome-stable.
(Reading database ... 267985 files and directories currently installed.)
Preparing to unpack google-chrome-stable_current_amd64.deb ...
Unpacking google-chrome-stable (91.0.4472.114-1) ...
Setting up google-chrome-stable (91.0.4472.114-1) ...
update-alternatives: using /usr/bin/google-chrome-stable to provide /usr/bin/x-www-browser (x-www-browser) in auto mode
update-alternatives: using /usr/bin/google-chrome-stable to provide /usr/bin/gnome-www-browser (gnome-www-browser) in auto mode
update-alternatives: using /usr/bin/google-chrome-stable to provide /usr/bin/google-chrome (google-chrome) in auto mode
Processing triggers for desktop-file-utils (0.24-1ubuntu3) ...
Processing triggers for mime-support (3.64ubuntu1) ...
Processing triggers for man-db (2.9.1-1) ...
externet@externet-presariocq57notebookpc:~$ 


Will see if got the Chrome browser...

---

### Post by Innernet on 2021-07-09
Saw nothing related to Chrome in the downloads folder nor on the desktops icons :(

( You are dealing with an old fart )

---

### Post by yancek on 2021-07-09
> Saw nothing related to Chrome in the downloads folder nor on the desktops icons 

Not sure why you would expect it there.  The command below shows you ran the installation from /home/externet:

> externet@externet-presariocq57notebookpc:~$ wget [https://dl.google.com/linux/direct/g...rent_amd64.deb]("https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb") 

The output following seems to show it was installed.  I wouldn't expect an icon for the app on the Desktop, you can put one there if you want.  You should be able to start it with:

```
/usr/bin/google-chrome
```

---

### Post by Innernet on 2021-07-09
Great, yancek.  It worked following your instruction above ! =d>

---

### Post by monkeybrain20122 on 2021-07-09
You should be able to just download the Chrome installer from its website, right click it and install, I am sorry, I think all these command line stuffs just make the whole thing unnecessarily confusing for new users. 

I never have to use command line to install a .deb (depending on your flavour you may have to install gdebi or the software center or equivalent will pop up to install after right clicking)

---

