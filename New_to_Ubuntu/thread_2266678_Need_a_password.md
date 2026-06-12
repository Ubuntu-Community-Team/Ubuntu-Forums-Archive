---
title: "Need a password"
date: 2015-02-24
forum: New to Ubuntu
---

### Post by jerry38 on 2015-02-24
hello

     I am new to Linux Lubuntu  and I just did a clean install from Windows Xp Professional because Windows Xp is no longer supported.  I installed version 14.04.1 using a 32 bit machine.  There are things to do after installing.  My situation is this.  

     When I open up LX Terminal and I typing in  coding.  I hit enter and  it asks for a password.  I just try  typing  in any password hit enter it skips a line and still needs an active password and repeat  the same pasword.  Nothing.  I also tried  typing in the password I sign into Lubuntu with which doesn't work.  Is there a password I can use so I can continue to work with this computer.

---

### Post by lisati on 2015-02-24
Just use your normal password that you'd use to login to your machine. Nothing will show when you type, this is normal, your password will still be accepted.

---

### Post by ajgreeny on 2015-02-24
The password needed is the one you must have given when installing the OS, after you you gave the username you need.  There is no root password in Ubuntu or Lubuntu, just the user's password.

---

### Post by deadflowr on 2015-02-24
If new, why not forgo using the terminal to start and instead use the graphical components, the update manager and the lubuntu software center, to update the system and install new applications.
And then slowly wade in the waters of command line usages.

After all, we do not even know what commands you were trying to run...

---

### Post by grahammechanical on 2015-02-24
In the Ubuntu family of Linux distributions you will find that that are many commands that we can enter into the terminal and that do not need a password. But certain commands that affect the system and require a password we enter using the prefix of sudo. for example

```
sudo apt-get update
```

We are then asked for a password and when we enter the password we created when we installed Ubuntu the command will run. Are you prefixing these commands with the word sudo?

Regards.

---

### Post by buzzingrobot on 2015-02-24
> **jerry38 said:**
> ...also tried  typing in the password I sign into Lubuntu with which doesn't work.

That's the password to use. Obviously, be sure you're entering it correctly, using the right case, etc.

---

### Post by jerry38 on 2015-02-25
hello

      Can I ask.  LX Terminal has begun to accepting  my password and was not a mater of being case sensitive or such as that.    I went back and did another clean install which  worked.  After the clean install I updated  and then ran these commands in LX Terminal.  sudo apt-get update && sudo apt-get upgrade ( hit enter)  sudo apt-get install lubuntu-restricted-extras.  LX Terminal than ran and  asked to me to select yes or no to accept these commands.  I typed in "y" for yes pressed enter and than ask me to to agree to the linence  and terms.  I try to agreeing to them by pressing the enter key.  But the license agreement popup still displays.  Not sure what to do.  Will work if I just dismiss the license agreement  screen.  Please any sugestions.  

      Lastly.  What brought me here in regard to the password situation.   I was  trying to download xampp for Linux / Lubuntu  but was not able to get passed the initial download screen.  Meaning I clicked  the download link and  the box to select  save which never appears and  tried the download  several times ( This was  prior to the clean install ).    My directiions are after the download I open LX Terminal and  type  in  necessary coding and continue.   Why is this happening.    I would like to download other  programs and appications on the computer.    Does this sort of problem  sound farmilar to anyone.  If so are  there  tutoirials  avaible to correct this.  Please any advice on these two issues.   Thank you.

---

### Post by deadflowr on 2015-02-25
To accept the agreement hit tab and the left/right button to select, then hit enter.

---

### Post by jerry38 on 2015-02-25
hello

      Sorry to say LX Terminal has failed to recognise my password again.   I am not sure what else to try on my end.  If this no other way  to get around this.  Please disregard the post.  Sorry for any other inconviences.  Jerry

---

### Post by Rex Bouwense on 2015-02-25
If you are new to Linux, it is best to install applications that are in the Lubuntu/ubuntu repositories.  They have already been tested and are generally compatible with your installed version.  If an application is not in the repositories, it may install and work flawlessly but it also may have some problems.  Since you are new, stick with the tested stuff until you get your feet on the ground.

Information on lost password can be found here:
[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

---

### Post by mastablasta on 2015-02-26
> **jerry38 said:**
> 
      Sorry to say LX Terminal has failed to recognise my password again.   I am not sure what else to try on my end.  If this no other way  to get around this.  Please disregard the post.  Sorry for any other inconviences.  Jerry


copy what is in terminal (all output) and post it here using the code tags (the # icon in the thread menu)

terminal can be replaced with another one if for some reason it is not working well. it's hard to say from the information you provided what is wrong.

on a different not what do you plan to do with xampp? do you know there is a LAMP server available in repository? and quite easy to install. there are also premade images available (such as turnkeylinux or bitnami stack) fo various web applications & servers).

if you plan on setting up a server there are also plenty of easily installed GUI available. but you need to solve you password issue first. I am very much interested to see what you did in terminal.

also you can skip to another console (that isnot LX) if you press alt+ctrl+f1 though F6. you can then login and do you magic.

---

