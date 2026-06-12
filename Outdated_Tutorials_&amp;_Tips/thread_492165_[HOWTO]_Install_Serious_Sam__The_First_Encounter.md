---
title: "[HOWTO] Install Serious Sam : The First Encounter"
date: 2007-07-04
forum: Outdated Tutorials &amp; Tips
---

### Post by bobbocanfly on 2007-07-04
**How-To Install Serious Sam : The First Encounter on Ubuntu 7.10**

This tutorial will help you to install Serious Sam : The First Encounter on Ubuntu 7.10, not using the standard Wine way (which doesnt really work very well)

**One - Downloading the custom installer**

Firstly you need to go to [http://www.liflg.org/?catid=6&gameid=71](http://www.liflg.org/?catid=6&gameid=71) and grab the Loki custom installer for Serious Sam. Download the file to your desktop either through bit-torrent or through a direct download (I used the direct download, so i dont know how many seeders the torrent has). Once you download the file, move it to your home directory if it isnt already there.

**Two - Preparing for the installation**

Now it is time to dig out your Serious Sam disk. Load it into your CD drive and mount it if it doesnt automatically. Then open up your terminal and type:

```

cd ~/
mv serious.sam.tfe_1.05beta3-english-2.run ssamInstall.run
chmod u+x ssamInstall.run
./ssamInstall.run

```

This should load up the Serious Sam installer. If it doesnt make sure you set the permissions correctly and try again.

**Three - Installing the game**

Once the installer has loaded it is a simple point and click interface. Remember where you install the game (A directory within your home directory is recommended (i used ~/bin/serioussam)), and make sure you tick the "Put symlink in Home directory box", to make things simpler later. The game should now be installed but dont run it just yet! Just one more thing to do.

**Four - Creating launcher script**

The final job is to create a simple bash script so you can launch sam just by typing serioussam into your terminal. For this you need to be able to use sudo so make sure you have sufficient privileges to use it. Once you are sure you can use sudo open your terminal and type:

```

cd /usr/bin
sudo gedit serioussam

```

Once gedit has opened type:

```

echo "Starting Serious Sam: The First Encounter"
cd /installdirectory/ssamtfe
./ssamtfe

```

Save the file and go back into your terminal and type:

```

chmod 777 serioussam
serioussam

```

Serious Sam : The First Encounter should now load and run.

**If there are any problems with the bash scripts above please tell me**

---

### Post by go_beep_yourself on 2007-11-24
> **bobbocanfly said:**
> **How-To Install Serious Sam : The First Encounter on Ubuntu 7.10**

This tutorial will help you to install Serious Sam : The First Encounter on Ubuntu 7.10, not using the standard Wine way (which doesnt really work very well)

**One - Downloading the custom installer**

Firstly you need to go to [http://www.liflg.org/?catid=6&gameid=71](http://www.liflg.org/?catid=6&gameid=71) and grab the Loki custom installer for Serious Sam. Download the file to your desktop either through bit-torrent or through a direct download (I used the direct download, so i dont know how many seeders the torrent has). Once you download the file, move it to your home directory if it isnt already there.

**Two - Preparing for the installation**

Now it is time to dig out your Serious Sam disk. Load it into your CD drive and mount it if it doesnt automatically. Then open up your terminal and type:

```

cd ~/
mv serious.sam.tfe_1.05beta3-english-2.run ssamInstall.run
chmod u+x ssamInstall.run
./ssamInstall.run

```

This should load up the Serious Sam installer. If it doesnt make sure you set the permissions correctly and try again.

**Three - Installing the game**

Once the installer has loaded it is a simple point and click interface. Remember where you install the game (A directory within your home directory is recommended (i used ~/bin/serioussam)), and make sure you tick the "Put symlink in Home directory box", to make things simpler later. The game should now be installed but dont run it just yet! Just one more thing to do.

**Four - Creating launcher script**

The final job is to create a simple bash script so you can launch sam just by typing serioussam into your terminal. For this you need to be able to use sudo so make sure you have sufficient privileges to use it. Once you are sure you can use sudo open your terminal and type:

```

cd /usr/bin
sudo gedit serioussam

```

Once gedit has opened type:

```

echo "Starting Serious Sam: The First Encounter"
cd /installdirectory/ssamtfe
./ssamtfe

```

Save the file and go back into your terminal and type:

```

chmod 777 serioussam
serioussam

```

Serious Sam : The First Encounter should now load and run.

**If there are any problems with the bash scripts above please tell me**

Why do you believe a serioussam script needs to be created? Have you ever used a gamepad in this game? Why does the game only take a square portion of the center of the screen surrounded by black? I guess Linux just isn't much of a gaming os, and I'll have to use wintendo. @$%@#$%^

---

### Post by smartboyathome on 2007-11-24
1) A script has to be created so that the game appears in the applications menu.
2) I have not.
3) Because the Resolution is set lower than your monitor's resolution.
4) Get more games to come to Linux and it will become a better gaming OS. :)

---

### Post by go_beep_yourself on 2007-11-25
> **smartboyathome said:**
> 1) A script has to be created so that the game appears in the applications menu.
2) I have not.
3) Because the Resolution is set lower than your monitor's resolution.
4) Get more games to come to Linux and it will become a better gaming OS. :)

Just typing ssamtfe would start the game for me. Maybe /usr/local/bin is not in your path, and you should add it there. I can tell you how if you need help doing that. Even if you did not correct your bash, the script is not needed. You could simply put this as the command in your applications menu

```
bash -c "cd /usr/local/bin;./ssamtfe"
```

I got the game for the split screen multiplayer. It took me a while, but I finally got it working in 64 bit. Actually there is a hack to get Serious Sam 2 working in 64 bit Linux. No one knew the solution to this. I saw several people on the gentoo forums with the same problem. I spoke directly to the developer of the problem. He was not aware of the problem. He gave me a solution to the problem. He couldn't test it out himself because he was away from his office, so I tried it, and it worked. I'll make a how to and post it up on the forums. If anyone has an account to the gentoo forums, he or she should link them to the how to.

Do you know of any other games that allow 2 or more people to play from the same computer?

Have you or do you know how to get a gamepad working with Serious Same FE?

---

