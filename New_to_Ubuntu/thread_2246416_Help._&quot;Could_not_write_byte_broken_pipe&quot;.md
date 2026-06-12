---
title: "Help. &quot;Could not write byte: broken pipe&quot;"
date: 2014-09-30
forum: New to Ubuntu
---

### Post by YuraB on 2014-09-30
I have read several articles on this issue, but they did not help.
Please, help me!!

What I did: 
1) I go into the mode "Recovery Mode", run the "Enable networking", then "Drop to root shell prompt". 
2) Often found this advice: 


    sudo apt-get update 
    sudo apt-get purge nvidia- * 
    sudo apt-get install nvidia-current-updates 
   
    At the 3rd step returns: 
    The following packages have unmet dependencies: 
    nvidia-current-updates: Depends: nvidia-304-updates but it is not going to be installed 
    E: Unable to correct problems, you have held broken packages. 


3) What should I do? Thank you!

---

### Post by ian-weisser on 2014-09-30
> **YuraB said:**
> nvidia-current-updates: Depends: **nvidia-304-updates** but it is not going to be installed 

1) Is it '**nvidia-304-updates**' or is it '**nvidia-graphics-drivers-304-updates**' ?

2) Open System Settings --> Software & Updates --> Ubuntu Software tab
  Is the checkbox selected for 'Proprietary drivers for devices (restricted)' ?  If not, check the box.
If it was already selected, let us know.

---

### Post by papibe on 2014-09-30
Hi YuraB. Welcome to the forum ):P

I believe there's an error on the commands you are running. In order to remove all nvidia packages there has to be no space between nividia- and the *. Also you better be sure there's no file named nvidia-something on the current directory or the shell expansion will mess up your command. Try this instead:
```
sudo apt-get purge nvidia-\* 
```

BTW, you don't have to go into recovery mode. In a regular session press Ctr+Alt+F1 to get a text mode prompt. Once you run the commands successfully you can reboot your computer by running:
```
sudo reboot
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by YuraB on 2014-09-30
Hello and Thanks, ian-weisser.
 1) I don't know. I am newbie in these questions. I'm just repeating given commands from forums.

2) How can I do this? Ubuntu crashed before entering the desktop. Maybe it possible through terminal ... ?

---

### Post by papibe on 2014-09-30
> **YuraB said:**
> 2) How can I do this? Ubuntu crashed before entering the desktop. Maybe it possible through terminal ... ?
Even if the desktop crashes, there's a good chance that you can get to the text mode my pressing Ctrl+Atl+F1 or Ctrl+Atl+F2.

Just wait a few seconds after the error, or the black screen.

You can do it in recovery mode too. Take a look at a similar situation [here]("http://ubuntuforums.org/showthread.php?t=2164030&p=12790810#post12790810").

Regards

---

### Post by YuraB on 2014-10-02
Hello, Papibe ;)
I tried to use your first advice. 
I replaced  "[COLOR=#000000]sudo apt-get purge nvidia- * [/COLOR]"  with your "[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get purge nvidia-\*[/FONT][/COLOR]"
But I got the same answer.

I used your second advice. But I don't understan--How can i do the 3-rd step? I am saying about: "
[LIST]
[*]Remove all packages separately except for these two:Code:
nvidia-cg-toolkit
nvidia-common
[/LIST]
"
After 2-nd step i got Package nvidia-304 is not installed, so not removed. 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Thus the next steps answer me: nvidia-common...is not installed and etc.

[COLOR=#000000]What should I do? Thank you![/COLOR]

---

