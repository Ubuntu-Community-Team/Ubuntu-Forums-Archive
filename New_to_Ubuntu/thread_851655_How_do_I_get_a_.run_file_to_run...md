---
title: "How do I get a .run file to run.."
date: 2008-07-06
forum: New to Ubuntu
---

### Post by Vindicate86 on 2008-07-06
I just downloaded the linux client to get my Enemy Territories Quake Wars running on Linux to see how different it'd run compared to windows.. Well, apparently Linux doesn't run .run files... My friend who's been tryen to tutor me briefly said something about going into terminal and going cd(insert directy/file name here)... Well I tried cd/home/brody/ETQW-client-1.5-full.x86.run... and it didn't work.. I'm very new to Linux so this is all very confusing to me.. Please help.

---

### Post by sdennie on 2008-07-06
Try:

```

cd
sh ETQW-client-1.5-full.x86.run

```

If that doesn't work, try:

```

cd
sudo sh ETQW-client-1.5-full.x86.run

```

---

### Post by pytheas22 on 2008-07-06
Try:
```

sh /home/brody/ETQW-client-1.5-full.x86.run
```

If it's a bash file, this will make it work.  If it doesn't, please post the output of this command:
```

file /home/brody/ETQW-client-1.5-full.x86.run
```

This will tell you what kind of file the .run file is, which is the clue you need to make it work.

---

### Post by Vindicate86 on 2008-07-06
brody@brody-desktop:~$ sh /home/brody/ETQW-client-1.5-full.x86.run
/home/brody/ETQW-client-1.5-full.x86.run: 1: Syntax error: "(" unexpected
brody@brody-desktop:~$ file /home/brody/ETQW-client-1.5-full.x86.run
/home/brody/ETQW-client-1.5-full.x86.run: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.4.1, dynamically linked (uses shared libs), not stripped
brody@brody-desktop:~$

---

### Post by Vindicate86 on 2008-07-06
Bump

---

### Post by pytheas22 on 2008-07-07
From the output of "file," it looks like this might just be an executable binary.  Try:
```

cd /home/brody
chmod +x ETQW-client-1.5-full.x86.run
./ETQW-client-1.5-full.x86.run
```

If that doesn't work, please upload that file here so we can take a look.

---

### Post by Vindicate86 on 2008-07-07
Yea that didn't work.. How do I upload the file? It's 550mb lol.. So it may not be feasible..

---

### Post by aktiwers on 2008-07-07
Does it have a readme? Seams like you are missing some libs?

---

### Post by Vindicate86 on 2008-07-07
Yea... I'm very very stupid... :( I realized the .run file Im trying to run... Was a bad download.. I just checked the properties of it... and it's only 289mb when its supposed to be 530mb.. Im re-downloading it right now. And Ill try the stuff all you suggested. Im sorry for wasting your guys' time lol.. Such a scatter brain sometimes.

---

### Post by aktiwers on 2008-07-07
Hehehehe :D
When you are done downloading, this would do fine for installing
[http://ubuntuforums.org/showpost.php?p=5334548&postcount=6](http://ubuntuforums.org/showpost.php?p=5334548&postcount=6)
(Its pytheas22s post number 6 here)

---

### Post by Vindicate86 on 2008-07-07
Ok I must be doing something wrong... When I drag on drop onto terminal this is whats its called...

 '/home/brody/Desktop/ETQW-client-1.5-full.x86.run' 

I tried every single one of those codes again.. Nothing works.

This is what I get:

brody@brody-desktop:~$ cd /home/brody
brody@brody-desktop:~$ chmod +x ETQW-client-1.5-full.x86.run
chmod: cannot access `ETQW-client-1.5-full.x86.run': No such file or directory
brody@brody-desktop:~$ ./ETQW-client-1.5-full.x86.run
bash: ./ETQW-client-1.5-full.x86.run: No such file or directory
brody@brody-desktop:~$

---

### Post by Vindicate86 on 2008-07-07
Nvm... After reading over my post I realized I just had to add "/Desktop" after home/brody... oi.. Im a newb

---

### Post by Vindicate86 on 2008-07-07
Ok.. I can get into the installer... But everytime I try and install I get mkdir failed after inputting Accept User License > Tutorial Read clicked next > Enter Path where its to be installed /home/Quake Wars also tried home/Quake Wars > Toggled Punkbuster and Copy files from DVD > Punkbuster EULA > Fatal Error - mkdir failed > Finish - There were errors. We will now put things back to how they were..

---

### Post by Alpinist on 2008-07-07
You probably need to run as sudo

[INDENT]cd /home/brody
chmod +x ETQW-client-1.5-full.x86.run
[COLOR="SandyBrown"]sudo[/COLOR] ./ETQW-client-1.5-full.x86.run[/INDENT]

And enter your password when prompted.  I'll probably try installing this in a few days myself.

---

### Post by Vindicate86 on 2008-07-07
Everything is working 100% hunky dory! Thanks all!

---

### Post by pytheas22 on 2008-07-08
> Ok.. I can get into the installer... But everytime I try and install I get mkdir failed after inputting Accept User License > Tutorial Read clicked next > Enter Path where its to be installed /home/Quake Wars also tried home/Quake Wars > Toggled Punkbuster and Copy files from DVD > Punkbuster EULA > Fatal Error - mkdir failed > Finish - There were errors. We will now put things back to how they were..

I'm glad it's working now.  But just FYI: you should probably have entered /home/brody, or a subdirectory of that path, as the installation directory.  /home by itself is a system directory (hence your inability to write to it without using sudo)...if you create a directory at /home/Quake Wars, the system would think that it's the /home folder of a user named "Quake Wars."

Anyway it didn't do any damage and everything should still run fine, but I just wanted to point this out in the interest of giving you a better understand of Linux.

EDIT: also, another nice thing to know that might have helped you out is that in the terminal, if you start to type the name of a file or a command, you can press tab to autocomplete.  This can save you from having to drag and drop icons into the terminal when you don't want to type out long names by hand.

---

