---
title: "Linux (Ubuntu) Newbie Tips and Tricks"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by bim27142 on 2011-10-16
Hi Guys!

I am very new to this forums and of course I am an absolute newbie to Linux (Ubuntu)... I am interested to learn Linux for 3 main reasons...

1.) I want to explore something new (new learning, new experiences, additional skills as an IT person)
2.) I want to be part of the Linux team in my office one day (one step at a time) :D
3.) I got bored with Windows... :D

I hope to enjoy this adventure and any quick tips and tricks (links or references as I am still trying to explore this site as well) will be sincerely appreciated...

Thanks and more power to all Linux (Ubuntu) users!  :guitar:

---

### Post by gsmanners on 2011-10-16
Welcome. :D

Have a look around. Feel free to share your experiences.

---

### Post by oldgeekster on 2011-10-16
Just a hint, you might want to bookmark [http://www.googlubuntu.com/](http://www.googlubuntu.com/)

If you cannot find an answer to a specific question or problem area by searching the forums, chances are you will get some good "finds" out of googlubuntu. :cool:

---

### Post by mushy365 on 2011-10-16
I've had ubuntu for a while, when windows crashed. But only in the last two weeks have i really learnt anything about it. The reason was i started using the terminal for everything, and started taking on challenges. I've been on a steep learning curve since. Even today i learnt a few simple commands that i didnt know before. 

So my first tip would be to use terminal no matter how akward it is at first. Instead of ubuntu software manager to install files i used sudo apt-get install packagenam

Using the terminal even when its not practical is the best way to learn. For example instead of using gedit ive started using a termimal text editor vim, i find it more akward like i said but it gets me used to changing directory, mkdir , rmdir, compileing, make a program and executable with chmod -x filename. I even use terminal to copy and paste files instead of using just drag and drop, because of that in the last few days i learnt commands like pwd = print working directory, also learnt that when typing in a long directory name it auto completes which is useful and just realised that yesterday

Another great way to learn is to install servers, i installed vsftpd (ftp server), samba server, apache server

I read tutorials on how to install and configure these, doing this kind of thing gives you an idea of where things are located in the file system. Which im just getting used to 

ie config files are usually in /etc/

you have to edit config files when configuring servers. 
Then after you configure something you have to restart the server for the changes to take effect  so you will learn like 

/etc/init.d/apache2 restart 
to restart apache webserver 

or use like service smbd restart 

installing and configuring samba, allows me to share my music files with my whole family on my network.  I read tutorials on how to configure and followed them 

i learnt that /srv/ root directory was for servers, so i knew to put the shared folders there 

earlier today on here i learnt about symbolic links so i can have all my media in different folders without taking up twice the space. 

i just find new challenges. Today i formatted an external hard drive as i wanted to store media on it and share it on my network with samba. 

So i had a go and messed it up, so read up and read about types of file types mine was mounted as vfat which does not support permissions so i couldnt share it on samba 

so i reformated it as ext4 as suggested online. But i had problems with that, then after asking on here i was told i needed to open a root shell by using sudo su  - i never knew about this

this allowed me to cd to the folder and mkdir and change permissions.

So today i basically 
copied all files from ipod to folder - got a mp3 tagger tool and renamed the files from their tags as ipods change the filename to gibberish like XGHT.mp3

Then i reformated my hard drive, which got me using commands like - df -T 
Then i created a symbolic link from the media on my external hard drive to my shared samba folder.

Sorry for the long post but i love using ubuntu now. Even tho im a noob i feel like some sort of l33t genius lol

---

### Post by Bmonsterboy on 2011-10-16
Hey and welcome to the party man :)

I find that one of the best ways to learn is by having an objective to achieve; something that you are trying to do. As an example, I learnt SSH, Bash scripting and some other stuff too via setting up an FTP server. It really helps to have something to put your learning into practice.

---

### Post by bim27142 on 2011-10-17
@ [mushy365]("http://ubuntuforums.org/member.php?u=1286452") thanks! that was very informative...

thanks guys! i will look around this forum and see how far i can get from there... :D

---

