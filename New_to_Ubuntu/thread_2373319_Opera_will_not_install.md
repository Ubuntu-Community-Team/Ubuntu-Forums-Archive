---
title: "Opera will not install"
date: 2017-10-05
forum: New to Ubuntu
---

### Post by cosimomo on 2017-10-05
I have been using Opera for a number of years and have tried installing in Ubuntu which I am using in a dual boot system. I have tried 17.4, didn't work. So then I installed 16.4LTS, didn't work. I have downloaded the .iso from both a torrent and  the Usbootin site. Altogether have reinstalled Ubuntu 4 times to no avail.

What happens is I get Ubuntu installed(not live), download the opera browser. I then open the download and the Ubuntu Software manager opens to the Opera install page. I click Install... and NOTHING. Nothing happens. I have been through this several times so here I am...
If anyone has any suggestions to get Opera installed I would most appreciate it.

Thanks

---

### Post by howefield on 2017-10-05
Reinstalling the operating system because Opera won't install is a bit extreme ;)

Personally I would install via the terminal, with the command..

```
sudo apt install ~/Dowloads/opera-stable_48.0.2685.35_amd64.deb
```

That assumes that the file is named as above and is in the ~/Downloads folder, if it isn't change the command to suit.

---

### Post by cosimomo on 2017-10-05
Thanks very much for your help... I am a newbie and unskilled at Terminal to say the least... I guess it takes time and practice

BTW, I did overcome your misspelling of Downloads in the command, so I guess thats something :)

I'll keep working on it

Thanks again

---

### Post by su:bhatta on 2017-10-05
Make sure that the opera-stable_48.0.2685.35_amd64.deb is in Downloads folder

Then issue the howefield's command 

```
sudo apt install ~/Downloads/opera-stable_48.0.2685.35_amd64.deb
```

Open a Terminal  and paste the command.
It will ask for password, type in the password, NOTE: Password will not show up on screen, not even *'s will show.

once command prompt is back, check in Applications, you should have Opera installed.

If there are any Error messages after you put password in terminal, please copy paste here.

---

### Post by KenUBF on 2017-10-05
cosimomo, 

Since you're not very familiar with the command line you can go to the Opera website and download a debian installer file. This will install on Ubuntu. [https://www.opera.com/download/linux/](https://www.opera.com/download/linux/)   Just choose the correct file for your system, either 32-bit or 64-bit. Hope this helps!

---

### Post by howefield on 2017-10-07
> **cosimomo said:**
> BTW, I did overcome your misspelling of Downloads in the command, so I guess thats something :)

Cool ;)

---

### Post by linuxissuperawesome on 2017-10-09
I Agree That Re-Installing Ubuntu Is A Bit Extreme.

Assuming Your File Is opera-stable_48.0.2685.35_amd64.deb And Is In The Downloads Folder The Command Would Be:-
```
sudo dpkg -i ~/Downloads/opera-stable_48.0.2685.35_amd64.deb
```
Also If You Like Double-Click Installation For Deb Files.Try Installing gDebi
```
sudo apt-get install gdebi
``` And Setting You Default Deb Application To "GDebi"
:D

---

### Post by MelvinGoo on 2017-10-10
Thanks for the code i used it and all went well:D
MG

---

