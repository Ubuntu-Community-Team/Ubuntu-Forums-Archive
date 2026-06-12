---
title: "HOWTO take tiled screens of video in one image(easy way)"
date: 2008-04-25
forum: Outdated Tutorials &amp; Tips
---

### Post by Sjovan on 2008-04-25
**What you need:**
```

sudo apt-get install mplayer
sudo apt-get install imagemagic
cd ~/bin/
wget -O vcs http://p.outlyer.net/vcs/files/vcs-1.0.12
wget http://home.no.net/sjovan01/scripts/pr0nscreen

NOTE: check for latest version of vcs on [home of vcs]("http://p.outlyer.net/vcs/")
      

Edit: Got some new info :) -O flag in wget changes the name of the download, so you don't have to rename the vcs-script later on.

```
**NOTE: if you don't have the folder ~/bin/, then I recomend that you make one (mkdir ~/bin), and do the command --> export PATH=~/bin:$PATH <--- adds ~/bin to the list where the shell is going to look for scripts. If you don't want to make folder bin, then you can put the scripts in /usr/local/bin <-- anoying to do sudo if you want to edit the script huh?**

NOTE2 (for people that are really new to Linux):
~ <--- is the same as saying home/yourusername
cd is the command for going to a location in your filesystem
wget is a command that you use (can use) to download files from a specific adress
apt-get is the command you use (can use) for installing programs from the repo (if you have a fresh install of Ubuntu you have to go system --> administration --> software sources and check everything on the list and do the command sudo apt-get update).
sudo allows a permitted user to execute a command as the superuser.
You should man <command/prog> that you want to learn how to use ---> example: man man to fined out more about man :)


vcs is a awsome script that Toni Corvera made. The script uses mplayer to take X amount of screens of a file. in vcs you tell imagemagic how to handel the screens you take. imagemagic then takes all the screens and put them together on one picture.  

**Oh, awsome! Why do I need pr0nscreen then?**
1. My script has a neat make screens of all the *.avi, *.mpg, *.wmv, *.mpeg in folder function, and it puts the screens in ../Screens/<name of the folder you ran the command from>.
You could always add other movie-formats and change the dir you put the screens in in the script (nano ~/bin/pr0nscreen **if you downloaded it to /usr/local/bin** ---> nano /usr/local/bin/pr0nscreen).

2. it's easy to change number of pics and how many colums you want. you don't have to remember the vcs command and stuff.

3. Have you ever got a error when takeing screens of a short file? can't capture the last screen, well, this script solves it :) You can force the end offset with $3. it has a default by 1 minute, so you don't get a anoying black frame as last capture. (if you don't like the offset, then just use -1 as $3)

4. The script makes the folder (or just check that the folder exist) ../Screens/name of folder you ran the script from and moves all the done pics to that folder.

Edit:
**I forgot to thank Toni for giving me the fix on taking screens of short files**

**How to get the scripts working?**
```

cd ~/bin/ **if you download it to /usr/local/bin** ---> cd /usr/local/bin

NOTE: If you are planing to use this script for other stuff then pr0n, then just rename the script. :)
      command ---> mv pr0nscreen <new name>

chmod o+x vcs
chmod o+x pr0nscreen **or the edited name of the script**



```

**So how do I use pr0nscreen then?**
cd /folder/with/file(s)/to/take/screens/of
pr0nscreen **or the edited name of the script** <number of screens> <number of colums> <add morem minutes to offset (-1 if you don't want any offset)> <alternativ input - "filename.typeoffile">

open the script or /msg me if you need more info :)

example:
pr0nscreen 10 2 0
pr0nscreen 6 3 2 "jalla movie.avi" or jalla\ movie.avi

example result:
[[IMG]http://b.imagehost.org/t/0723/Showdown_In_Little_Tokyo_1991_avi.jpg[/IMG]](http://b.imagehost.org/view/0723/Showdown_In_Little_Tokyo_1991_avi.jpg)
as you can see... if I had added more to end-offset then I wouldn't get that last black screen

---

### Post by Sjovan on 2008-04-29
For anyone that have downloaded the script before to day. I don't know why, but it had a # before the vcs command where you spesify the inputfile. Remove the "#" from that line or download pr0nscreen again.

My export command was mixed up, but it's edited now. Sorry for the errors guys :)

---

### Post by Sjovan on 2008-05-07
I have noticed that the vcs-script bugs out on some *.wmv files capturing screens in the middle of the file. There is prob. something you can do to force a change to vnc-script so that it doesn't take a screen at a specific moment in the video.

Some good scripters out there that can help me?

The bold part fixed the other error (taken from pr0nscreen):
vcs -n $screens -c$colons -H 192 **-O MIN_LENGTH_FOR_END_OFFSET=0 -E$offset** "$file" --jpeg

Maybe some one with some more knowledge can take a look at the vnc-script and help me out? I have sent another mail to Toni.

---

