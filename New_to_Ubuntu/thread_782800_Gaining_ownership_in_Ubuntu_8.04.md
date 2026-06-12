---
title: "Gaining ownership in Ubuntu 8.04"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by greenaged on 2008-05-05
Hi. I Whenever I try to save anything in my Files System, or in my Slave Drive I get a message stating " Could not save. You do not have the permission necessary to save this file."
Secondly, when I try to create a new Folder in either of the drives the option is grayed-out, in-operable. Same for the option to Create Document.I don't have have that problem on the desktop.
Question: is there some way to overcome these obstacles, for if I cannot store stuff on  my slave drive it is as good as dead.
Thank you.:confused:
greenaged
[email]merve@att.net[/email]

---

### Post by hyper_ch on 2008-05-05
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by SupaSonic on 2008-05-05
> **greenaged said:**
> Hi. I Whenever I try to save anything in my Files System, or in my Slave Drive I get a message stating " Could not save. You do not have the permission necessary to save this file."
Secondly, when I try to create a new Folder in either of the drives the option is grayed-out, in-operable. Same for the option to Create Document.I don't have have that problem on the desktop.
Question: is there some way to overcome these obstacles, for if I cannot store stuff on  my slave drive it is as good as dead.
Thank you.:confused:
greenaged
[email]merve@att.net[/email]

You generally should use your home folder, '/home/your_username' to save all your personal files. If it still gives you errors, run 
```
chown -R your_username /home/your_username
```

---

### Post by erginemr on 2008-05-05
I suggest you to read the link given by **hyper_ch** first and also:
[http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html)
to learn more about file permissions.

In Ubuntu, you can do almost anything with "sudo" prefix, which gives you root permissions:
[http://www.xkcd.com/149/](http://www.xkcd.com/149/) :D

So, from a terminal:
```
cd /usr/share -> Moves to /usr/share folder
mkdir my_dir -> Tries to create a my_dir directory there but fails since you don't have enough permissions
touch my_file -> Tries to create a my_file document there but fails since you don't have enough permissions
sudo mkdir my_dir -> Asks for your password and creates the directory with enough (i.e. root) permissions
sudo touch my_file -> Asks for your password and creates the document with enough (i.e. root) permissions
```

This is the way it works for your root (/) system except your home folder (~/) and a few other specific folders (such as /tmp, /var/tmp, etc.), to where you can write with normal user permissions.

However, your mention of a slave drive deserves extra attention. Can you please inform us more about this drive? Is it internal or external, ntfs or ext2/3 formatted?

---

### Post by greenaged on 2008-05-05
> **hyper_ch said:**
> [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Thank you hyper, but, but being an absolute beginner I can't follow the advice given on the site you recommemded.
greenaged

---

### Post by greenaged on 2008-05-05
> **SupaSonic said:**
> You generally should use your home folder, '/home/your_username' to save all your personal files. If it still gives you errors, run 
```
chown -R your_username /home/your_username
```

Thank you for your response, but when I tried the above CODE I got this reply: chown: cannot access `/home/username/.gvfs': Permission denied

greenaged

---

### Post by greenaged on 2008-05-05
> **erginemr said:**
> I suggest you to read the link given by **hyper_ch** first and also:
[http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html)
to learn more about file permissions.

In Ubuntu, you can do almost anything with "sudo" prefix, which gives you root permissions:
[http://www.xkcd.com/149/](http://www.xkcd.com/149/) :D

So, from a terminal:
```
cd /usr/share -> Moves to /usr/share folder
mkdir my_dir -> Tries to create a my_dir directory there but fails since you don't have enough permissions
touch my_file -> Tries to create a my_file document there but fails since you don't have enough permissions
sudo mkdir my_dir -> Asks for your password and creates the directory with enough (i.e. root) permissions
sudo touch my_file -> Asks for your password and creates the document with enough (i.e. root) permissions
```

This is the way it works for your root (/) system except your home folder (~/) and a few other specific folders (such as /tmp, /var/tmp, etc.), to where you can write with normal user permissions.

However, your mention of a slave drive deserves extra attention. Can you please inform us more about this drive? Is it internal or external, ntfs or ext2/3 formatted?

Thanks for your response, erginemr. The drive is internal and formatted ext3. I guess I've been spoiled rotten by Windows, but your advice is too technical for me. I am too much of a beginner. 
greenaged

---

### Post by PeterJS on 2008-05-05
What's not making sense? The theory of how permissions and ownership work, or the more pratical aspect of which commands do what and how to use that to solve your problem?

---

### Post by wolfen69 on 2008-05-05
you must use sudo first in the following line:
```
sudo chown -R your_username /home/your_username
```

---

### Post by greenaged on 2008-05-05
> **PeterJS said:**
> What's not making sense? The theory of how permissions and ownership work, or the more pratical aspect of which commands do what and how to use that to solve your problem?

None of the above. It's why. Why PERMISSIONS? Why OWNERSHIP? I already have a log-in ID and a password, so why do I have to get permission or prove ownership to do something on my PC? That's what I can't understand
greenaged

---

### Post by Don1500 on 2008-05-05
> **greenaged said:**
>  I guess I've been spoiled rotten by Windows, but your advice is too technical for me. I am too much of a beginner. 
greenaged


Ahhh, Just copy the code, cut and paste, then read it. Then exicute it. Not much you can do at this point, since you are an absolute beginner, all you have to do is reinstall if you really screw up. (I must have reinstalled about 15~20 times when I started!)

Just do it.

---

### Post by greenaged on 2008-05-05
> **wolfen69 said:**
> you must use sudo first in the following line:
```
sudo chown -R your_username /home/your_username
```

Thanks for your response,but I tried that and it didn't work.
greenaged

---

### Post by oldos2er on 2008-05-05
> **greenaged said:**
> None of the above. It's why. Why PERMISSIONS? Why OWNERSHIP? I already have a log-in ID and a password, so why do I have to get permission or prove ownership to do something on my PC? That's what I can't understand
greenaged

 In a word: security.

---

### Post by Don1500 on 2008-05-05
> **greenaged said:**
> None of the above. It's why. Why PERMISSIONS? Why OWNERSHIP? I already have a log-in ID and a password, so why do I have to get permission or prove ownership to do something on my PC? That's what I can't understand
greenaged

You can log in as "Root" then you will have access to everything. I better get my flame suit on. IT IS NOT ADVISED TO RUN IN ROOT IF YOU ARE CONNECTED TO THE INTERNET. (OK guys?)

The reason is security, if you run in root anyone that can hack into your system can do anything they want. Your defenses are down. 

So stay out of root, unless you must, and learn how to access what you need in the terminal, "sudo" is your friend.

---

### Post by greenaged on 2008-05-05
> **greenaged said:**
> Thanks for your response,but I tried that and it didn't work.
greenaged

Lemme see. Is this the right way to enter the code:

sudo chown -R_username /home/_username

---

### Post by Fixman on 2008-05-05
Go to places=>home folder.

That is your home folder, the only folder you can modify besides orf its subfolders.

---

### Post by greenaged on 2008-05-05
> **oldos2er said:**
> In a word: security.

Then it should be optional-enable/disable. In my environment I don't need that security.
greenaged

---

### Post by Don1500 on 2008-05-05
> **greenaged said:**
> Lemme see. Is this the right way to enter the code:

sudo chown -R_username /home/_username

No

Like this

sudo chown -R your_username /home/your_username

where your_username is Your User Name.

for me that would be:
sudo chown -R don /home/don

---

### Post by PeterJS on 2008-05-05
> **greenaged said:**
> None of the above. It's why. Why PERMISSIONS? Why OWNERSHIP? I already have a log-in ID and a password, so why do I have to get permission or prove ownership to do something on my PC? That's what I can't understand
greenaged

As Oldos2er said security. You may know that you're you and you're supposed to have administrative access to your machine, but you computer has no way to know that without you proving that you are in fact you with your password. The biggest flaw in the windows security model is the assumption that any program running as your user is doing so with your consent, full understanding, and blessing. Another thing is the history, windows grew up as a single user OS, one user, one machine, the user had full control because it was their machine. Linux grew out of UNIX, it was a multi user OS from day one, just because a user can log in to a machine doesn't mean they should have administrative access to that machine. I believe it was stated above, you can log in as root if you want to but this isn't supported, isn't a good idea, and you will find little sympathy if you break your system as a result of intentionally subverting the security system.

---

### Post by PeterJS on 2008-05-05
> **greenaged said:**
> Then it should be optional-enable/disable. In my environment I don't need that security.
greenaged

The consensus is that if you don't know how to disable the security system, you don't understand the security system well enough to fully understand the impact and potential harm of your decision.

[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

---

### Post by Don1500 on 2008-05-05
> **Don1500 said:**
> Ahhh, Just copy the code, cut and paste, then read it. Then exicute it. Not much you can do at this point, since you are an absolute beginner, all you have to do is reinstall if you really screw up. (I must have reinstalled about 15~20 times when I started!)

Just do it.


I do have one thing to add to this:

**WARING:** If anyone tells you to do [COLOR="Red"]sudo rm -rf ANYTHING [/COLOR]do NOT do it.

---

### Post by greenaged on 2008-05-05
> **Don1500 said:**
> You can log in as "Root" then you will have access to everything. I better get my flame suit on. IT IS NOT ADVISED TO RUN IN ROOT IF YOU ARE CONNECTED TO THE INTERNET. (OK guys?)

The reason is security, if you run in root anyone that can hack into your system can do anything they want. Your defenses are down. 

So stay out of root, unless you must, and learn how to access what you need in the terminal, "sudo" is your friend.


  Ah! Come on. I've been using Windows for over ten years and I could do literally anything with my PC without getting PERMISSIONS, or proving, or establishing, OWNERSHIP, and I've never had a security problem.

---

### Post by Fixman on 2008-05-05
> **greenaged said:**
> Ah! Come on. I've been using Windows for over ten years and I could do literally anything with my PC without getting PERMISSIONS, or proving, or establishing, OWNERSHIP, and I've never had a security problem.

Come on:

Forget about permissions for some months. You will not have to care about it.
Forget about all commands on this thread
Go to places->home folder. You can modify and save files on that folder.

done.

---

### Post by akiratheoni on 2008-05-05
> **greenaged said:**
> Ah! Come on. I've been using Windows for over ten years and I could do literally anything with my PC without getting PERMISSIONS, or proving, or establishing, OWNERSHIP, and I've never had a security problem.

Then go ahead and enable the root account. But if you mess something up, don't blame us.

If you're really looking forward to using Linux to its fullest capacity, you need to work WITH the system, not against it.

Sorry if it sounds harsh, but the reason why you think you can do anything with your PC is because you're used to the Windows mindset. If you're using Linux, you'll need to get used to a different model of (inherently) better security.

EDIT: I also find it hard to believe that you've never, ever, in ten years of using Windows, had at least one piece of spyware or virus affect you. Guess why viruses and spyware can install? Because you, the user, can install anything. That also means spyware and viruses can install.

---

### Post by SunnyRabbiera on 2008-05-05
> **greenaged said:**
> Ah! Come on. I've been using Windows for over ten years and I could do literally anything with my PC without getting PERMISSIONS, or proving, or establishing, OWNERSHIP, and I've never had a security problem.

well you might be one of the lucky ones, but still the cause of most system infections and stuff in windows is the way it is set up.
Only recently it seems Microsoft has got a clue on how to protect one from malicious software with the UAC.
I know it seems hard to understand after using windows for so long, but we have things set up the way they are fro a reason.
Remember that unix in general is very focussed on security, sure it lowers ease of use but in the long run it is for the better.

---

### Post by Sinkingships7 on 2008-05-05
You shouldn't be attempting to write things to your filesystem in the first place. There's generally no point. But you're right. It's your system; do with it what you please. What I'm going to give to you, I encourage you to use for your SLAVE DRIVE ONLY. Only modify or write to the filesystem if you absolutely know what you're doing:

This code will open a nautilus window with full root privileges:
```
gksudo nautilus
```
Navigate to your slave drive and double-click to access it. On the white space inside, right click, choose properties, and go to permissions. Select yourself from the drop-down menu and set your file permissions to read and write. Do this for the next one down, as well. For the "Others" one, set it to no access.

Unmount the slave drive and exit the root nautilus window. Mount the drive again. You should now have read and write access to that drive.


You should listen to the people on this forum. They know what they're talking about.

---

### Post by hyper_ch on 2008-05-06
> **greenaged said:**
> Ah! Come on. I've been using Windows for over ten years and I could do literally anything with my PC without getting PERMISSIONS, or proving, or establishing, OWNERSHIP, and I've never had a security problem.
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

> **SunnyRabbiera said:**
> sure it lowers ease of use but in the long run it is for the better.
How is the ease of use lowered???

---

### Post by jw5801 on 2008-05-06
> **greenaged said:**
> Ah! Come on. I've been using Windows for over ten years and I could do literally anything with my PC without getting PERMISSIONS, or proving, or establishing, OWNERSHIP, and I've never had a security problem.

Then use Windows? I honestly don't see the issue. If you like the way Windows works, then use it. Horses for courses, to quote the old adage.

This is the way we do things, if you don't like it, you don't have to do it. If you want to use the root account, then google "root login ubuntu" and I'm sure you'll find your answer.

---

### Post by erginemr on 2008-05-06
> **hyper_ch said:**
> [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

:lolflag:

I am always fond of your concise replies... :cool:

---

### Post by hyper_ch on 2008-05-06
> **erginemr said:**
> :lolflag:

I am always fond of your concise replies... :cool:

Doing my best ;)

---

### Post by oldos2er on 2008-05-06
> **greenaged said:**
> Ah! Come on. I've been using Windows for over ten years and I could do literally anything with my PC without getting PERMISSIONS, or proving, or establishing, OWNERSHIP, and I've never had a security problem.

 Linux is not Windows. If you want to learn more, go to [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/) and search on keywords "security" and "permissions."

---

### Post by greenaged on 2008-05-06
> **oldos2er said:**
> Linux is not Windows. If you want to learn more, go to [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/) and search on keywords "security" and "permissions."

Thank you. Will do even tho' I got the problem solved by my nephew who knows a bit about Unix and Linux.
greenaged:)

---

### Post by greenaged on 2008-05-06
Hi! I wish to thank all of you guys and dolls for the support and help I received from you with my problem, and to inform you that the problem has been solved by my nephew, who knows a bit about Unix and Linux. I didn't want to ask him to help me as he has done quite a lot for me already, to get into Ubuntu, even though he once told me, in nicer terms, that he can't understand why an old goat like me, at my age and level of computer know-how should want to mess with Ubuntu.
Once again thanks, and I am very grateful.
greenaged

---

### Post by that_IT_guy on 2008-05-14
I believe I caused this problem by installing my Amarok media player through the root account on my box.(was troubleshooting and didn't think about it.)
The way I easily fixed this problem was by logging in under the root user account then going to system> administrator> Users and Groups, then select manage groups.  Select the root group and click properties, you should see in the lower box section of the menu your standard user name and the root user name with little radio boxes next to them, add a check to you standard user name and save the changes. log out of the root account and your permission problem should be fixed.

If not Ill recommend again that you thoroughly read the information in the two links provided near the beginning of this thread.  Although you may be new to Linux as am I,if you read them and try some the things they tell you to do, you can learn quite abit about the file system and it's hierarchy structure.
They are what helped me.:guitar:

So thank you you two =)

---

