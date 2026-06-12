---
title: "complete noob questions regarding software install....?"
date: 2012-12-26
forum: New to Ubuntu
---

### Post by buntuo on 2012-12-26
Trying to repair a downloaded avi file , its plays ok in vlc after re indexing , but i need to transfer via usb to watch on another device. 

So I found divfix a free program to fix the file , it says one click install ? upon opening the downloaded file in chromium , it opens a window with a lot of script , *divfix++one click install v0.01 (1).ymp ?

the script seems like a mix of commands and the same time description of the software ! sorry if this seems like a completely noob question, I only installed Ubuntu 12.10 last night , and Im learning as I go. 

This is the first such type of file and situation i have encounted , please can anyone tell me how to proceed...

if anyones interested the script in box is as follows.......

Thank you very mucho in advance-o ! 

ok didnt show the scrip , think some of it is image file/link cause when i try to post it says contains 18 images and im only allowed 8 , but im sure there somebody who is familiar to my query

---

### Post by oldos2er on 2012-12-26
You should get the *.deb files instead, either [http://sourceforge.net/projects/divfixpp/files/DivFix%2B%2B/v0.34/divfix%2B%2B_0.34-1_i386.deb/download](http://sourceforge.net/projects/divfixpp/files/DivFix%2B%2B/v0.34/divfix%2B%2B_0.34-1_i386.deb/download) or [http://sourceforge.net/projects/divfixpp/files/DivFix%2B%2B/v0.34/divfix%2B%2B_0.34-1_amd64.deb/download](http://sourceforge.net/projects/divfixpp/files/DivFix%2B%2B/v0.34/divfix%2B%2B_0.34-1_amd64.deb/download) whichever matches your architecture. Install it at your own risk.

Normally you'd want to stick to installing software from the repositories. See [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware) and [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by JayKay3OOO on 2012-12-26
[http://sourceforge.net/projects/divfixpp/files/DivFix%2B%2B/v0.34/](http://sourceforge.net/projects/divfixpp/files/DivFix%2B%2B/v0.34/)

Choose the deb file (presuming you are using ubuntu or a debian based distro)

Open the terminal and type sudo dpkg -i

drag the downloaded deb into the terminal after -i. It'll come up with like /home/yourusername/Downloads/divfix++_0.34-1_i386.deb

Press enter and input your login password if it asks for one. Don't worry it will look like you are typing blank as no * will come up. If you put the wrong pass in it will ask you to do it again.

Simples.


sudo dpkg -i /home/yourusername/Downloads/divfix++_0.34-1_i386.deb

---

### Post by NikTh on 2012-12-26
Hi  and welcome 

The philosophy in general is to use progams and applications that you are 100% trust. We avoid to install apps from sites - Internet .. etc and run scripts that we don't know what exactly do. 

I suggest to try mencoder and ffmpeg first, and see if you can repair your corrupted avi file. 

This dvix++ repair application is OLD . Last stable release is 0.34 from 2009 , see here => [http://www.divfix.org/](http://www.divfix.org/)
also this One Click install I don't know what is it.. If I want to install this app , I would prefer a .deb package.. 
The .deb packages are here : [http://sourceforge.net/projects/divfixpp/files/DivFix%2B%2B/v0.34/](http://sourceforge.net/projects/divfixpp/files/DivFix%2B%2B/v0.34/)
but again.. is OLD application and I'm not sure if you can install it to a new system. 

Search  for mencoder and ffmpeg repair avi at Google. 

Thanks

---

### Post by buntuo on 2012-12-26
wow ! thanks for the all the info ! so many quick useful replys , like no forum i ever been in lol. and during the holidays 

thanks very much , information duly assimilated

---

