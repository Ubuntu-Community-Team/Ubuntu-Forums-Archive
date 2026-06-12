---
title: "Help with Rhythmbox plugins"
date: 2014-04-23
forum: New to Ubuntu
---

### Post by Jamie_Freeman on 2014-04-23
Hi,

I am completely new to this and am trying to make the switch from Windows - one thing I would like to get working is a decent music player and I have been trying to play around with Rhythmbox and install some plugins...
[FONT=arial]
... from the following website ([http://askubuntu.com/questions/147942/how-do-i-install-third-party-rhythmbox-plugins](http://askubuntu.com/questions/147942/how-do-i-install-third-party-rhythmbox-plugins)) I have tried running the following command:
[/FONT]
[FONT=courier new]sudo apt-get install rhythmbox-plugin-complete   
[/FONT]
and get the following error message: 

[FONT=courier new]E: Unable to locate package rhythmbox-plugin-coverart-browser[/FONT]

These are the very first commands I have tried to run from the terminal and it makes me quite nervous because I really have no idea what I am doing... Anyway, any help for an absolute beginner would be much appreciated.

Thanks in advance.

---

### Post by PotatoHead007 on 2014-04-23
Hello, welcome to the forums and the world of Open Source :D

It seems that the link you sent does not work with the new version of Rythimbox. But running this command should do the trick:
```
sudo apt-get install ubuntu-restricted-extras
```
No worries about terminal, just read [this thread](http://ubuntuforums.org/announcement.php?f=326) and check what is safe and what not :)

---

### Post by Jamie_Freeman on 2014-04-23
Thank you very much for the quick reply - I take it from the command (that I am in the process of running) that this is installing a number of extra things...

Another complete beginners question: a box comes up in the terminal with this title: Configuring ttf-mscorefonts-installer

This has an '<OK>' button to accept the Licence agreement but I can't seem to accept it...

Again - thanks for the help and I'll try to start digesting the link you posted :)

---

### Post by Jamie_Freeman on 2014-04-23
Sorry - posted before Googleing. Solved this now (Tab and Spacebar)

Thanks again :)

---

### Post by Jamie_Freeman on 2014-04-23
Sorry - more questions. Successfully ran the code and I now have many more fonts in Office but I don't seem to have anymore plugins available in Rhythmbox. In particular I am looking to get an Album Art view in Rhythmbox - I realise that this might be trying to recreate I-Tunes but I do like looking at Artwork when listening to music :). I have just been trying to use the following forum ([http://askubuntu.com/questions/112148/how-to-browse-by-album-art-in-rhythmbox](http://askubuntu.com/questions/112148/how-to-browse-by-album-art-in-rhythmbox)) but I am getting in a muddle... :(

Thanks.

---

### Post by davidmohammed on 2014-04-25
Hi,

  I'm the PPA owner - and the answerer of that question you linked to.

Sorry you are having so much problems.

Can you take a step back - you have added my PPA using sudo add-apt-repository ppa:fossfreedom/rhythmbox-plugins

then you ran

sudo apt-get update

Then you have installed the coverart plugin via

sudo apt-get install rhythmbox-plugin-coverart-browser

Start Rhythmbox from a terminal via

rhythmbox

and from the edit menu choose Tools - plugins and tick the coverart-browser plugin.

Does coverart-browser appear?  If not, any errors in the terminal that you can copy and paste here?

---

