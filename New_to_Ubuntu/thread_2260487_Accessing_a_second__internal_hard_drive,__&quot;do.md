---
title: "Accessing a second  internal hard drive,  &quot;do not have permissions&quot; pictures folder."
date: 2015-01-12
forum: New to Ubuntu
---

### Post by gary53 on 2015-01-12
Hello. I,m wondering if someone can lead me in the right direction here. I am totally new using a Linux operating system and performing commands. Ill explain what I am trying to do best I can. Again I'm totally a noob at this so I need someone with patience and to give step by step directions as I've spent countless hrs trying to do this and it comes down to I just don't know what the hell I'm doing. 
I have a PC that has two hard drives inside it. One drive has nothing on it but strictly Ubuntu. The other drive is a drive I pulled from an i- Mac. Ubuntu does recognize the Mac drive in the file Manager. My goal is I am just trying to pull the pictures off the Mac drive as the drive is failing. That is all I want to do. The pictures are located in the Pictures folder. I could not to this task in Win 7 as the drive was for some reason not being recognized at all. 
I noticed the drives are not lettered like in Windows. C D etc . When I open file manager the mac drive says "Macintosh HD". I double click that and go to users and click on the users name. In this case there are two users. When click one of the user names, I goto the "pictures" folder and double click and get a grey and white box with a message that says: This location can not be displayed. You do not have the permissions to view the contents of "Pictures" I have no idea what to do from here . Can someone actually please walk me through this step by step in laymans terms on how to accomplish what I want to do. I know how to get the to terminal, goto sudo su then my password and thats it. Again, a total noob to this. I don't know how to really apply the commands and or access the mac drive, let alone get permission to take what I need out of the pictures folder from it. Any help would be appreciated. I d be willing to even speak with someone over the phone or via text so that it would be easier and would be able to confirm that what I'm doing is correct. I've watched you tube Vids, read from forums and websites but just can not seem to apply it and get it done. The commands are Mostly Greek to me but I have to learn somewhere. Thank you in advance !!

---

### Post by grahammechanical on 2015-01-12
When we install Ubuntu we create a user account with a password. When we run Ubuntu we work as a standard user until we need to do something that requires administrator authorisation. Then we are asked to authenticate the action and as we are both a standard user and an administrator user our password will authenticate the action. Once the action is completed and a few minutes have passed we cease being the administrator and revert to working as a standard user.

There are many terminal commands that we can run as a standard user but when we need to run a command that only an administrator can run we put "sudo" in front of the command and enter our password and the command runs.

There is no need to run sudo su to do what you want to do. What version of Ubuntu are you using? That is always useful information for us especially if you want step by step explanations. For example, I could say to you to open the file manager by running

```
gksudo nautilus
```

That will open the file manager (Nautilus) with administrator privileges if you are using Ubuntu 12.04. But if you are using a newer version of Ubuntu you will find that gksu is not installed and you have to install it. If you are using one of the flavours of Ubuntu then a different file manager will be used. Do you understand?

You need to run the file manager with administrator privileges and that may give you access to the files on that disk. But note when you copy those files onto the Ubuntu partition those files will be owned by you as administrator (also called root in Linux) so you will have the same problem accessing those files unless you run the file manager as administrator and change the permissions of the files and folders.

You, as standard user will be able to access the files and folders but you will not be able to Create and Delete the files or folders. You will need to run the file manager as administrator to do that. But you should be able to copy the files and folders. The process of copying should make you, as standard user, the owner of the files with the power to create or delete files.

If it sounds unnecessarily complicated just remember this is done to prevent anyone gaining access to the computer and changing things without our agreement.

Regards.

P.S. A tip: first use the file manager as a standard user and try to access that hard disk. That will "mount" the drive. Then when you open the file manager as an administrator you will see that drive in the list of Devices.

---

### Post by oldrocker99 on 2015-01-12
Once the drive is mounted, you can also try this:
```
sudo chown username:username [path/to/drive]
```

Chown is the "change ownership" command.

For "username:username," you use your login ID twice, for your group, and for you as the user. The "path/to/drive" should be /media/username/name-of-drive.

Good luck!

---

### Post by The Cog on 2015-01-12
I don't think that trying to change the ownership on the mac drive is a good idea. It is failing anyway, and writing to it is just encouraging trouble (even if a mac drive can store linux file permissions which I'm not sure of). I think copying the files off first is the best bet. Use one of these three commands to get a root-privilege file manager running:
```
gksu nautilus
or
gksudo nautilus
or these two:
sudo -i
nautilus
```
then copy the files off - preferably into the home directory of one of the Linux users. You can worry about fixing the permissons on the copies later, not the original disk.

---

### Post by coffeecat on 2015-01-12
> **The Cog said:**
> I don't think that trying to change the ownership on the mac drive is a good idea.

Not only is it not a good idea, it's not going to work anyway. :) The Mac drive will be formatted journalled HFS+ which can be mounted read-only in Ubuntu, and hence cannot be written to. 

@gary53, follow the advice you have been given to use a root-owned nautilus (file browser) to browse the mounted Mac drive. If you get an error running "gksudo nautilus" or "gksu nautilus" you will probably need to install the gksu package before it will work.

Very brief explanation about the problems you are getting: Mac drives are formatted with Apple's own filesystem called HFS+ which Windows cannot read at all - hence Windows 7 not recognising it. Ubuntu can read from HFS+ but not write to it. Complicating this is the Unix system of ownership and permissions shared by both Ubuntu and MacOS. The files on your Mac drive have a different UID (user ID) from your Ubuntu account. Hence all the problems browsing into sub-folders. A root-owned file browser should cut through all that, except for Ubuntu's inability to write to HFS+.

---

### Post by gary53 on 2015-01-12
grammechanical greetings ,  thank you for replying. I'm currently running ubuntu 14.10. I did just download gksu. As far as using it, well thats a different story. Im just literally starting out with this so its ALL new to me. Ive never used nothing but windows my entire life.  Its like speaking english my whole life and trying to learn and another language now.   The lingo/ terminology. I ve spoken to some people in other boards and they were talking to me about it as if I were a seasoned Ubuntu user.   I just have a hard time comprehending some of the directions and applying the commands when I'm reading them. Now that I have gksu Id like to go to the next step and try to access this files that are the Mac drive. I do understand  pretty much what you explained.  Any chance we can go a little further in the process ?  Thank you.

---

### Post by gary53 on 2015-01-12
Thanks to all who responded. I have not done anything as of yet but appreciate the comments.

---

### Post by yancek on 2015-01-12
If you now have gksu installed, open a terminal by holding down the Ctrl+Alt+t keys simultaneously then type in:  gksu nautilus
That should open the file manager and you can navigate to the folder you want as you described in your initial post.  You don't need write permissions as you are just going to be copying FROM that location to another location.

---

### Post by gary53 on 2015-01-12
when i run gksudo nautilus, it opens up a file manger, but there is no Mac Drive under DEVICES,  just my external drive and computer.

---

### Post by yancek on 2015-01-12
Check the /media/user name folder.  Use your actual user name.  Are you saying you no longer see the MacIntosh Drive you mentioned in your first post?

---

### Post by mc4man on 2015-01-13
A root nautilus will only show in the sidebar volumes already mounted. 
So mount the volume by other means then it will be visible in the root browser window.

---

### Post by The Cog on 2015-01-13
> **mc4man said:**
> A root nautilus will only show in the sidebar volumes already mounted. 
I wasn't aware of that. You learn something every day.
> So mount the volume by other means then it will be visible in the root browser window.
So probably the easiest thing to do is open the drive with your normal file manager, and then use gksudo nautilus to launch a file manager with root permissions, that should then be able to view the mac drive contents.

You probably won't be able to drag the files from the root nautilus to the normal nautilus window - I think the destination window is responsible for actually doing the behind-the-scenes copying, and the normal nautilus doesn't have read access to the files. So you probably need two gksudo nautilus windows to actually perform the drag/drop copy.

---

