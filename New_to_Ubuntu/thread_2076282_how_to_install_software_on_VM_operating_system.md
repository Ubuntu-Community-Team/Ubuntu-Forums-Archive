---
title: "how to install software on VM operating system"
date: 2012-10-25
forum: New to Ubuntu
---

### Post by syednasirraza on 2012-10-25
i have ubuntu 12 on my system , and i installed virtual box on it,, on which i hav installed windows xp... now i want to install some softwares on xp,, but i am having sources on my hardrive which is visible there to ubuntu???can i access it from xp and install software or i need to copy it to that xp harddrive and then install  it from there???how to copy in this case to xp harddrive???

---

### Post by snowpine on 2012-10-25
Hi, please try to use correct capitalization and punctuation, it will make it easier to understand you, thanks. :)

You install windows applications in your windows xp guest just like normal. In fact xp does not know it is a guest of another OS, it thinks it is "normal."

So your question then becomes, how do you get the installer files from your linux host to the windows guest? This guide explains how to set up a Shared Folder: [https://www.virtualbox.org/manual/ch04.html#sharedfolders](https://www.virtualbox.org/manual/ch04.html#sharedfolders)

---

### Post by syednasirraza on 2012-10-26
thnx snowpine for guideline
1....as per req i had to install guest addition in host operating system(xp in my case),, i have done that..secondly it requried to create shared folder in host operating system (ubuntu in my case),, which will be accessed from xp later...but i dont know how to create some shared folder in ubuntu?????that will be accesible from host operating system xp later....plz guide
2....i could not get using correct capitailization and pucntuation???would u plz point out my mistake , so that  i avoid that in future.....

---

### Post by snowpine on 2012-10-26
In VirtualBox: Machine -> Settings -> Shared Folders

---

### Post by JKyleOKC on 2012-10-26
> **syednasirraza said:**
>  i dont know how to create some shared folder in ubuntu?????that will be accesible from host operating system xp later....plz guideLaunch VirtualBox and get XP running. At the bottom of the vbox screen you'll see a row of icons, one of which resembles a folder. Click that one to get a dialog listing your shared folders. Click the "add" button in that dialog and select the "More..." option that comes up. Then browse to the folder that contains your downloaded windows packages and select it, finally OK out of the dialog. Now, in XP, select the "Network Places" icon, then the VBox server's icon from the four shown in the next window, and from that server double-click the shared folder you just created. It will open an Explorer window just as if it were a Windows folder, but it will be your shared Ubuntu folder. From there proceed as you would in Windows.

You don't need to do anything in Ubuntu to make the folder capable of being shared; VirtualBox does it all behind the scene.

Hope this helps!

---

### Post by syednasirraza on 2012-10-26
thaks alot dear snowpine....i got my data access....thnx
thnx jim too for ur detailed reply

---

