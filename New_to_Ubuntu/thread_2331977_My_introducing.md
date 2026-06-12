---
title: "My introducing"
date: 2016-07-27
forum: New to Ubuntu
---

### Post by noname34 on 2016-07-27
Good evening. Please be patient with me and my words. If i am enough gifted for write in english, i think i make a lot of mistakes. That's normal, i'm french and not bilingual. Don't hesitate to correct me, if i do mistakes of language. I am twenty three years old, and computer belongs my hobbies.  I came here because i discovered two months ago the greatest system Lubuntu : simple, fast, easy... But, i had a lot of problems. Like computer is a hobbie for me, i did a lot of manipulations, and, obviously, i did mistakes, but i learned a lot of like that : i read tutoriels, and that helped me. 


I would like understand why, when i installed Lubuntu 16.04 by my USB key, a message "dev/sda1 :  58555548969 files /   clean/ blocks. I didn't remember exactly the content of this message. 
I resolved this problem in installing Lubuntu 14.04, and i did a "sudo do-release upgrade -d", after (sudo apt update and sudo apt full-upgrade) thanks to french blog "angristan" for this solution... But that take time to make like that. So, now it's ok, but,[B] how resolved this problem directly and why i had this problem ? 
[/B]
And, when my computer was in stand by, and i start it after, cursor became invisible. This problem was resolved at my four installation, maybe thanks to updates. Where can i find updates historic and their descriptions ?



Thanks for your help...:)

---

### Post by grahammechanical on 2016-07-27
> "dev/sda1 :  58555548969 files /   clean/ blocks

I see that message every time I load Ubuntu. It is nothing to worry about. It is not a reason to install an older version of Ubuntu when the latest version is working very well.

Ubuntu runs on the Linux kernel (core part). And Linux produces system messages as it loads relating to the tasks that are being started and completed. Most of the time those system messages are hidden by a splash screen but often as the loading process switches from loading Linux to loading Ubuntu on Linux we see some system messages.

The message that you are seeing refers to Linux doing a file system check (fsck) on the hard disk partition that Linux is loading on. It tells us of the number of blocks of the hard disk that have been checked and the result. In your case and in my case the result is "Clean." That means there are no physical faults with the hard disk. This file system check is not a problem. And should not be seen as a problem. Linux is checking the health of the hard disk.

By the way this command was the wrong command. "sudo do-release upgrade -d." If we are using the Ubuntu server edition to upgrade to the next version of Ubuntu we run

```
sudo do-release upgrade
```

But if we use this command

```
sudo do-release upgrade -d
```

we upgrade to the next development version of Ubuntu. The inclusion of -d means development version. We upgrade to a version of Ubuntu that is still being developed and is not stable. It is my guess that you upgraded to Ubuntu 16.10 (code name xenial xerus).

Please see this wiki page under the section: Upgrading to development releases.

[https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)

What version of Lubuntu are you now using? Please look at the section Upgrading from the last release

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

It is my understanding that Lubuntu 14.04 is supported for 3 years from  the end of April 2014. That means that you will need to move on to  Lubuntu 16.04 next year. It would have been better if you had not  changed from Lubuntu 16.04 in the first place.

[http://askubuntu.com/questions/449376/why-do-ubuntu-lubuntu-14-04-have-different-support-periods](http://askubuntu.com/questions/449376/why-do-ubuntu-lubuntu-14-04-have-different-support-periods)

Regards.

---

### Post by noname34 on 2016-07-27
I think i was not too enough precise. I would like say i saw this message : "dev/sda1 : 58555548969 files / clean/ blocks" 


But, when i installed Lubuntu 16.04, i could not boot graphically. How can we resolve problem ? With what lines commands? 

I promise i resolved this problem thanks to french blog "angristan", thanks to an installation to lubuntu 14.04, and after, i did  "sudo do-release-upgrade -d", and after to wait a moment and answered to some questions and reboot my PC, Lubuntu 16.04 could booted graphically. I say the truth... 

Thanks for your explanations, i will verify my version. You said me "sudo do-release-upgrade -d" was a wrong command, but that did not work when i writed my line command without the "-d". Now, my lubuntu works perfectly, i want just understand what the message means. 

I will read the links what you gived me, but read it is not too easy for me like for you ! :) 

Thanks again to helped me ! :) 

Edit : i verified my version, and i'm on Lubuntu 16.04.1 (64 bits). 

Other thing : before, when i booted, and i put my computer in stand by, cursor became invisible...At the four installation of Lubuntu 16.04, that worked. 
Edit 2 : unfortunately, problem is again here... he is come back, i don't understand, but i saw my history thanks to the line command "history", and i think, maybe "sudo apt clean", "sudo apt autoclean", and "sudo apt autoremove", create this problem. I am not sure, but i would like have your opinion to this subject...

What do you think it? 


Finally, i have still an other problem. I would like my keyboard do like under Windows. When i use the touch "uppercase" (majuscule, (with the padlock)), that write "&é"'(", but i prefer my keyboard works like windows. I would like, if it's possible, this touch does 123456....

Thanks again for your help ! :)

---

### Post by chopra on 2016-07-27
> **noname34 said:**
> [COLOR=#000000][I]


Finally, i have still an other problem. I would like my keyboard do like under Windows. When i use the touch "uppercase" (majuscule, (with the padlock)), that write "&é"'(", but i prefer my keyboard works like windows. I would like, if it's possible, this touch does [/I][/COLOR]123456....

Thanks again for your help ! :)

I'm not entirely sure what you're trying to say here, are you referring to the Caps Lock key when you say "touch uppercase"?  And what does 123456... mean? Are you referring to the Num Lock key?  The behavior can be altered depending on what the language settings are for your keyboard. 
The link below shows how to alter the language settings of the keyboard.  Note, the first two steps might be different for you if you're using the Unity Desktop.

[http://www.wikihow.com/Change-Keyboard-Layout-in-Ubuntu](http://www.wikihow.com/Change-Keyboard-Layout-in-Ubuntu)

---

### Post by noname34 on 2016-07-28
Hello, thanks for your answer ! Yes, i wanted to refer me to the CAPS Lock. I haven't a "Num Lock", on my computer. I will try, but i don't know if i will arrive to make what i want. Thanks again for your help :) I will come back here after  have tried.

Edit : I tried to do what was writed on the tutorial, but i find it is very complicated, because i am on Lubuntu and not Ubuntu, and all the commands are in english...I will continue to try but it's not obvious...

---

### Post by Geoffrey_Arndt on 2016-07-28
Ubuntu Mint has very good French language support.    The XFCE version of Mint should run well on your system also . . . and you can use the French forum to quickly and correctly list your questions:
[URL="https://forums.linuxmint.com/viewforum.php?f=63"]
https://forums.linuxmint.com/viewforum.php?f=63[/URL]

---

### Post by noname34 on 2016-07-30
Thanks, but this board concerns Linux Mint and not Lubuntu... I have the environment LXDE...

---

### Post by leozinho29_eu on 2016-07-30
The problem have happened likely due to a graphics error.

That message is normal, but the step to activate the graphic interface fails and then the boot freezes there. I suppose your computer has a Intel Graphics GPU. The Lubuntu 16.04 ISO lacks a relevant package for Intel Graphics to function, but the 16.04.1 added it. 

The details about it and how I solved the issue in my notebook are here: [https://ubuntuforums.org/showthread.php?t=2331482&p=13521052#post13521052](https://ubuntuforums.org/showthread.php?t=2331482&p=13521052#post13521052)

But now I think the best thing to do is to use only the Lubuntu 16.04.1 ISO instead of 16.04.

I hope it helps.

---

### Post by noname34 on 2016-08-03
Thank you ! I read your post. I don't think i will come back answer on this subject, but i think i will come back (on this subject) when i need help again. 

If i must reinstall my system and if your tutorial works for me, i will come back here for say it. 

If you want we can close the subject, but i don't know how can i do that. 

Thank you again :)

---

