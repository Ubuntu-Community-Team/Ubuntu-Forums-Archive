---
title: "Problem in installing software in Ubuntu 20.04.1 LTS"
date: 2021-01-18
forum: New to Ubuntu
---

### Post by sureshdesh on 2021-01-18
[COLOR=#000000][FONT=Helvetica][SIZE=2][COLOR=#141414][FONT=Segoe UI]I had used Computers for many years, but [/FONT][/COLOR]I am a Newbie in Linux.

[COLOR=#141414][FONT=&amp]I bought a Laptop with Ubuntu 18.04, which got upgraded to Ubuntu 20.04.1 LTS.

[/FONT][/COLOR][COLOR=#141414][FONT=&amp]I have a problem with installation of ‘MahaSecure’ – an authentic net-banking software downloaded from the Bank’s website.

[/FONT][FONT=Segoe UI]1. I downloaded the compressed file ‘mahasecure-64bit.tar.gz[/FONT]’ [FONT=Segoe UI]to my ‘Desktop.

2. Extracted 2 files, MahaSecure.tar.gzand [MahaSecureInstaller.sh]("https://www.rediffmail.com/cgi-bin/red.cgi?red=http://MahaSecureInstaller.sh&isImage=0&BlockImage=0&rediffng=0&rdf=VXMJflUgB2dSfF1hCndUZAE3B3BbaFY%2BV3pcOlVr&rogue=5c1161873ad32195b60c32d19db6a73081c7a8ab") [/FONT][/COLOR][COLOR=#141414][FONT=Segoe UI]to ‘Desktop’.

[/FONT][FONT=&amp]3. Opened Terminal, reached contents of ‘Desktop’ and ran Command -

[/FONT][FONT=Segoe UI]                                    sudo ./[MahaSecureInstaller.sh]("https://www.rediffmail.com/cgi-bin/red.cgi?red=http://MahaSecureInstaller.sh&isImage=0&BlockImage=0&rediffng=0&rdf=VXMJflUgB2dSfF1hCndUZAE3B3BbaFY%2BV3pcOlVr&rogue=5c1161873ad32195b60c32d19db6a73081c7a8ab")(see screenshot ‘*Mah Desktop 1*[/FONT][/COLOR][/SIZE][I][SIZE=2][COLOR=#141414]’[/COLOR][/SIZE][COLOR=#141414][FONT=Segoe UI][SIZE=2][SIZE=2])[/SIZE]
[/SIZE]
[ATTACH=CONFIG]287769[/ATTACH]

[SIZE=2][COLOR=#000000][FONT=Helvetica][COLOR=#141414][FONT=Segoe UI]4. After entering Password, I got the output as shown in screenshot ‘[/FONT][/COLOR][/FONT][/COLOR][COLOR=#141414][FONT=Helvetica][FONT=Segoe UI]*Mah Desktop 2*[/FONT][/FONT][/COLOR][/SIZE][I][SIZE=2][COLOR=#000000][FONT=Helvetica][COLOR=#141414]’[/COLOR][/FONT][/COLOR][/SIZE][COLOR=#000000][FONT=Helvetica][COLOR=#141414][FONT=Segoe UI][SIZE=2].[/SIZE]

[/FONT][/COLOR][/FONT][/COLOR][/I][ATTACH=CONFIG]287770[/ATTACH]


[/FONT][/COLOR][/I][/FONT][/COLOR][COLOR=#000000][FONT=Helvetica][SIZE=2][COLOR=#141414][FONT=Segoe UI]5. The installation did not happen.[/FONT][/COLOR]

[COLOR=#141414][FONT=Segoe UI]6. I also tried by downloading the compressed Installation file to a separate Folder under ‘Home’. I extracted the contents of it to the same Folder. Then I opened the Terminal, navigated to the contents of the Folder and ran Command - 'sudo ./[MahaSecureInstaller.sh]("https://www.rediffmail.com/cgi-bin/red.cgi?red=http://MahaSecureInstaller.sh&isImage=0&BlockImage=0&rediffng=0&rdf=VXMJflUgB2dSfF1hCndUZAE3B3BbaFY%2BV3pcOlVr&rogue=5c1161873ad32195b60c32d19db6a73081c7a8ab").' But the result was identical as after point 4 above.[/FONT][/COLOR]

[COLOR=#141414][FONT=Segoe UI]Request you to help me please![/FONT][/COLOR]
[/SIZE]

[/FONT][/COLOR]


[I][COLOR=#141414][FONT=Segoe UI]
[/FONT][/COLOR][/I]

---

### Post by CelticWarrior on 2021-01-19
The installation did happen. Search the program and you should find it.
What you shouldn't do (in current Gnome) is to save and run such files from the desktop and certainly shouldn't create additional folders under /home where only users' folders should be. Use you own user's Downloads folder instead or save, extract to and run from /home/<your_username> which incidentally is where the terminal opens by default.

---

### Post by ActionParsnip on 2021-01-19
Seems the installer like to be run from $HOME and not $HOME/Desktop

Move the installer and rerun. Might work OK

---

### Post by Impavidus on 2021-01-19
The first line of output reads:```
/root/MahaSecure
```Maybe that is the directory where the software was installed. If so, it installed in $HOME, but as you ran the command with sudo, and from 20.04 onwards sudo defaults to setting the new user's home directory, this was root's home directory. Root's home directory has no Desktop directory, which led to some failures.

To confirm, run```
sudo ls /root/MahaSecure
```If this shows the contents of the MahaSecure directory, my guess was right. You can then delete /root/MahaSecure and its contents and reinstall the software without sudo. It appears that this software wasn't packaged for system-wide installation. Which is actually a small security problem.

On the other hand, if it attempted to install in the current directory (as ActionParsnip guesses), it would be installed in ~/Desktop. In that case, first move the installer to your home directory, then install. And don't use sudo, as that will set ownership of the installed files to root.

---

### Post by sureshdesh on 2021-01-21
[COLOR=#000000][FONT=Ubuntu]Thanks a lot – CelticWarrior, ActionParsnip, Impavidus!

[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu]@Impavidus – running the command “[COLOR=#000000]sudo ls /root/MahaSecure” [/COLOR][COLOR=#000000]gave the output -

[/COLOR][/FONT][/COLOR][COLOR=#000000]*[FONT=Ubuntu]bin resource shared[/FONT]*[/COLOR]
[COLOR=#000000]
[/COLOR][COLOR=#000000][FONT=Ubuntu]which happen to be the contents of compressed file [COLOR=#141414]‘[/COLOR][COLOR=#141414]mahasecure-64bit.tar.gz[/COLOR][COLOR=#141414]’[/COLOR][COLOR=#141414]downloaded from the source. Please see the Sceenshot.
[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu][COLOR=#141414]I did not know how to ‘[/COLOR][COLOR=#141414]delete /root/MahaSecure and its contents[/COLOR][COLOR=#141414]’ as suggested by you, so not yet done it.[/COLOR][/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu][COLOR=#141414]But I went ahead and [/COLOR][COLOR=#141414]took action as per your next suggestion - [/COLOR][/FONT][COLOR=#141414]‘[/COLOR][COLOR=#141414][FONT=Ubuntu]first move the installer to your home directory, [/FONT][/COLOR][COLOR=#141414][FONT=Ubuntu]then install. And don't use sudo, as that will set ownership of the installed files to root’.
[/FONT][/COLOR][/COLOR]
[COLOR=#000000][FONT=Ubuntu][COLOR=#141414]I did ‘extract to and run from /home/suresh’.
[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu][COLOR=#141414]Then I used the command ‘ ./MahaSecureInstaller.sh’. The Output I got is shown in the Screenshot.

I still do not see the Installed Program. But I do see a File 'MahaSecure.Desktop, which open to a Text File -  please see the Screenshot.









[/COLOR][/FONT][/COLOR]
[COLOR=#000000][COLOR=#141414][FONT=Ubuntu]



[/FONT][/COLOR][/COLOR]
[COLOR=#000000][FONT=Ubuntu]



[/FONT][/COLOR]

---

### Post by sureshdesh on 2021-01-22
Please forgive me - I am not successful in uploading the last Screenshot, which shows a Text file 'MahaSecure.desktop' file on the desktop, and with this file opened as Text file. I am giving below the contents of the Text File 'MahaSecure.desktop' - 

1 [COLOR=#ff0000][Desktop Entry][/COLOR]
2 [COLOR=#008000]Version[/COLOR]=1.[COLOR=#800080]0[/COLOR]
3 [COLOR=#006400]Type[/COLOR]=Application
4 [COLOR=#008000]Terminal[/COLOR]=[COLOR=#800080]false[/COLOR]
5 [COLOR=#008000]Name[/COLOR][COLOR=#4b0082][en_IN][/COLOR]=MahaSecure
6 [COLOR=#008000]Exec[/COLOR]=/home/suresh/MahaSecure/bin/MahaSecure.sh
7 [COLOR=#008000]Name[/COLOR]=MahaSecure
8 [COLOR=#008000]Icon[/COLOR]=/home/suresh/MahaSecure/Resource/appIcon.png

---

