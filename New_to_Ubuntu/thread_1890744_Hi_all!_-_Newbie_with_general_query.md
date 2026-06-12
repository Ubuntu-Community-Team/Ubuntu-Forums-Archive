---
title: "Hi all! - Newbie with general query"
date: 2011-12-04
forum: New to Ubuntu
---

### Post by quronos on 2011-12-04
Hi all!

I am a new user to Ubuntu. I came across the Ubuntu website on my old windows 7 setup 6 months ago and thought wow this looks quite good so gave it a go and now its my only OS running right now - some might say I've jumped in at the deep end!

Overall I'm very impressed, but probably my biggest problem is first of all finding and then installing additional software. I've been spoiled by windows in this area i think as software is abundant and installation is so easy, but when it comes to Ubuntu - i find myself getting a bit stuck and confused!

For the most part, I've been using the software center  to find new software and install it. I've also used the software centre to install other programs I've obtained such as boxee.
So far, its been a challenge but I'm learning slowly!

I do have one problem right now which is why I'm here at the moment. That is a program called Eldy. I've build a PC for my dad and instead of giving him the standard windows installation - i want to give him Ubuntu as a base and then Eldy on top!
I have downloaded the Eldi Ubuntu/Linux installation file, but I've no idea how to actually install it. The help file on Eldy's website mentions typing commands but doesnt say where I have to type the commands or if there is just an easier way to do it.

I'm really lost here guys can you help?

---

### Post by new123 on 2011-12-04
Hi and welcome :D
Since I am new too, maybe I could help you with 'where to type commands' :)
Your file Eldy23.tar.gz is probably in /home/*username*/Downloads (where  *username* is your user name ofc :D) so open your file manager and go  there.
Open the tar.gz I wrote up there and extract the folder... on Desktop?
Now open Terminal and type: "cd  /home/*username*/Desktop/*EldyFolderName*" (no quotes) Have on your mind  that "desktop" and "Desktop" are not the same. :)
Now type commands from Help page you found :)

Hope this helps.

---

### Post by JRV on 2011-12-04
What is the name of the file you downloaded?
What version of Ubuntu are you running?

---

### Post by Nixxus on 2011-12-04
if you're using a GUI, just go to applications > accessories > terminal if you have a gnome setup (bar at top nd bottom, no dock on the side).

if you're using unity (dock at the side) go into the full applications menu and search for "terminal" and use the commands there.

and welcome to Ubuntu, grab a mug :D

---

### Post by marrabld on 2011-12-04
Give us a little bit more info on the program you are trying to install.  Post a link.

To find the file, press your 'Windows'/meta key, and just type the name in the search bar.  You can refine your search by pressing the files filter down the bottom.

As far as 'how to install' either post the link or post the install instructions in the help file.

---

### Post by quronos on 2011-12-04
A big thanks for the welcome and help!

I am currently using Ubuntu 11.10 (application bar on the left)

The program I am trying to install can be found at [http://download.eldy.net/eldy23.tar.gz](http://download.eldy.net/eldy23.tar.gz)

The destructions they provide are at [http://howtos.eldy.net/](http://howtos.eldy.net/)

I'm pretty sure Java is already installed on my system ..well it is according to my software center it is and this is so say a requirement.

Can someone please guide me through the motions as simply as possible so I can learn for future reference

Kind Regards

---

### Post by quronos on 2011-12-04
any help would be great

---

### Post by cryptotheslow on 2011-12-04
According to here:
[http://linuxforelderly.wordpress.com/](http://linuxforelderly.wordpress.com/)

It is possible to add a repository for Eldy and use apt-get (or Synaptic etc.) to install it. Benefit being it should also keep itself updated.

The linked guide is a few years old though so you may want to confirm its validity on the Eldy forums: [http://eldy.net/forums](http://eldy.net/forums)

---

### Post by Dubslow on 2011-12-04
Where to issue commands, somebody above mentioned the "Terminal", you'll generally want to use that whenever something tells you to issue a command. You can find the terminal by going to Applications/Accessories (it might be different in your Graphical User Interface, I've never tried Unity in 11.10). 
Running the command 
```

tar -xf
```
will generally extract any compressed folders, such as the one you downloaded. 

Taking a quick look at the download file, it also looks like you'll need to compile the source code; I'm not too well versed there.

---

### Post by grahammechanical on 2011-12-04
I wish that you had given warning that clicking on that link would lead to an immediate download. I suggest:

1) you create a new folder called Eldy.

2) you copy the eldy23.tar.gz file into the Eldy folder.

3) In file manager you right click eldy23.tar.gz and select Open with Archive Manager. Then you select extract.

4) When you open the eldy23 folder you will see a file called eldy.jar. Now you have a choice

a) right click on the file and select Open with OpenJDK Java 6 Runtime and see what happens.

b) wait for a forum member to explain what to do with this file.

This is as far as I go. I am tempted to open the file with OpenJDK Java 6 Runtime but as I do not want this program and I do not want to be left with a program that I do not know how to remove I am not going to experiment further.

Regards.

---

### Post by marrabld on 2011-12-04
Okay, you can install Eldy without using the terminal.

1. download the file, right click-->save as-->Desktop
2. left click on eldy.tar.gz, it should open up in archive manager
3. Choose the extract icon up the top
4. Choose the folder that you would like to extract to.  This will become your launch folder unless you move it.  So I suggest something like /<home>/Applications.  
5. Enter the folder you just extracted. 
6. Left click on the eldy.sh, when prompted "Do you want to run "eldy.sh", or display its contents?"  choose Run.
7. Be patient, it took a while to load for me.  
8. Enjoy the software..... what ever it is.

Good luck

---

### Post by quronos on 2011-12-05
Big thanks to all who helped sorry to be a pain. :-)

---

