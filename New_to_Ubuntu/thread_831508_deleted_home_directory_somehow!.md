---
title: "deleted home directory somehow!"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by BetterSense on 2008-06-16
I posted earlier in theupdates forum about a machine I had that was still beta version and needed 600 some updates. Well, I ran apt-get upgrade and everything seemed to work.

That is until I rebooted and found all the folders of my home directory sitting on my desktop. Annoying! I like by desktop blank. I figured it was just an aesthetic decision for the stable release to have symbolic links on the desktop. So I highlighted them all and hit delete, thinking this would surely just delete the icon, and not the actual folder. 

Well, there is nothing in my home directory now, no videos, no pictures, documents, nothing. 

W. 
T. 
F.

So I went to Trash, saw all the folders here, and highlighted them and dragged to desktop. Now there is a file operation ( which has apparently frozen) that says it is preparing to move 235GB of files. It won't die and I don't know what the process is to kill it. I don't know where files in the Trash actually live, I assumed it was /lost+found but I can't cd into that even using sudo, it says sudo: cd: command not found.

This is all completely preposterous. How did my operating system just decide to move all my home directory folders to my desktop? Did it really do that? Seriously what the heck, my home is a complete separate partion, why is deciding to just rearrange my files?. Even from the terminal I cd and ls and get nothing. I'm freaking out here. I can click on the trashcan and a window will come up that shows my files, but I can't click on them because it's frozen. I have four frozen Trash - File Managers open right now.

```
chaz@brutus:~$ cd /home/chaz/
chaz@brutus:~$ ls
chaz@brutus:~$     
```

---

### Post by ibuclaw on 2008-06-16
Chaz, your trash directory is in your **~/.local/share/Trash** folder, so "ls" on it's own won't show that hidden directory.

try this instead
```
ls -A
```
If you get a list of files/folders with a "." dot infront of them, cd here:
```
cd ~/.local/share/Trash/files
```
check that everything is there
```
ls
```
Then mv everything back into place
```
mv * ~/
```

Regards
Iain

---

### Post by BetterSense on 2008-06-16
attempting to ls -a

---

### Post by BetterSense on 2008-06-16
O great, it seems to have partially worked. I got my music and documents and stuff back. Maybe hardy didn't really move my folders to /home/chaz/Desktop, but put symlinks on my desktop, and then highlighting icons and hitting delete deletes the source file? Would never have guessed that.

But anyway, all my trash programs are still open and frozen, and I can't mv a certain directory back to home. It's called VAST and was originally placed in my home by ktorrent. Sorry for posting my trash, but here it is. You can clearly see the directory when you ls but it says it doesn't exist.

```
chaz@brutus:~/.local/share/Trash/files$ ls
0519082239.jpg                                                        Screenshot-1.png                                                    VTS_02_0.BUP
0519082240a.jpg                                                       Screenshot.png                                                      VTS_02_0.IFO
0519082240.jpg                                                        Spirited_Away.DVD(H264.AC3)[KAA][4b692121].mkv [mininova].torrent   VTS_02_1.VOB
100windows                                                            Spirited_Away_DVD_H264_AC3_KAA_4b692121_mkv[www.btmon.com].torrent  VTS_03_0.BUP
2000-10-06 FLCL Vol 2.zip [mininova].torrent                          starvi1.gif                                                         VTS_03_0.IFO
asc06-Anderson.wmv                                                    starving_inside_big.JPG                                             VTS_03_1.VOB
blah.jpg                                                              starving_nate_inside.jpg                                            VTS_04_0.BUP
Dabrye___OneThree.torrent                                             swh-plugins-0.4.15                                                  VTS_04_0.IFO
DVD Shrink 3.2.desktop                                                tap-plugins                                                         VTS_04_0.VOB
DVD Shrink 3.2.lnk                                                    tap-plugins.rdf                                                     VTS_04_1.VOB
essential-20071007                                                    tap-plugins.tar.gz                                                  VTS_04_2.VOB
fathersday.pdf                                                        The Pillows [mininova].torrent                                      VTS_04_3.VOB
front.jpg                                                             untitled folder                                                     VTS_04_4.VOB
graf.png                                                              VAST                                                                VTS_04_5.VOB
graph.png                                                             VIDEO_TS.BUP                                                        VTS_05_0.BUP
install_flash_player_9_linux                                          VIDEO_TS.IFO                                                        VTS_05_0.IFO
[KB] Cowboy Bebop Remix 01-26 DVD H264 AC3 [www.Fulldls.com].torrent  VIDEO_TS.VOB                                                        VTS_05_1.VOB
lee.zip                                                               virtualbox_1.5.6-28266_Ubuntu_gutsy_i386.deb                        winbalcalc.zip
mozilla.pdf                                                           VTS_01_0.BUP                                                        winisdbeta.exe
rear.jpg                                                              VTS_01_0.IFO                                                        xmms-bs2b-0.3.210
saballistics-1.3.3                                                    VTS_01_0.VOB                                                        xmms-bs2b-0.3.210.tar.gz
SCOGBK-411.pdf                                                        VTS_01_1.VOB
chaz@brutus:~/.local/share/Trash/files$ cd Vast
bash: cd: Vast: No such file or directory
chaz@brutus:~/.local/share/Trash/files$ mv Vast /home/chaz
mv: cannot stat `Vast': No such file or directory
chaz@brutus:~/.local/share/Trash/files$                           
```

---

### Post by ibuclaw on 2008-06-16
Chaz, the Linux terminal is "**CASE-SENSITIVE**"

ie:
a file named **one** does not have the same name as a file named **ONE** in the same directory.
(Here's a test output by me)
```
iain@fredbuntu:~/test$ ls
one  onE  oNe  oNE  One  ONe  ONE
iain@fredbuntu:~/test$ 

```
To enter the directory you want to enter, type this instead
```
cd VAST
```

Regards
Iain

---

### Post by BetterSense on 2008-06-16
Thank you! So I moved it back afterall. BUT, the )*%#)@} folder icons are back on my desktop! Ahh! How am I supposed to get rid of them?


See, I thought, very naively, that what you saw on the desktop was what was contained in /home/chaz/Desktop. Because all the stuff I ever put on my desktop, I could access from the command line by going to /home/chaz/Desktop. But now, I have two folders in /home/chaz/Desktop that are NOT showing up on the desktop, even though they did before. AND, I now have a bunch of icons including an unwanted 'blank cdr' icon on my desktop that are NOT in my /home/chaz/Desktop folder. This is making me very confused.

Could it have something to do with my renaming my Music folder music, my Videos folder videos, and so on etc? I don't like shifting when I don't have to. I changed desktop back to Desktop because I thought maybe that had something to do with it, but nothing happned.

---

### Post by ibuclaw on 2008-06-16
OK, I think I can explain this.

Open up "gconf-editor". Press **Alt+F2** and type it into the run app text bar.

The Press **Ctrl+F** and search for the key "**desktop_is_home_dir**", you have to check "Search also in key names" to do this.

The search should get back the result
**/apps/nautilus/preferences/desktop_is_home_dir**

Select it, and check whether or not that key is enabled. If it is, disable it, then logout/login for the changes to take effect.

Regards
Iain

[EDIT]
Running one of these two commands in the terminal should acheive this as well, just incase you get stuck on the previous.
```
gconftool-2 -t bool -s /apps/nautilus/preferences/desktop_is_home_dir false
```
```
sed -i '/desktop_is_home_dir/s/false/true/' ~/.gconf/apps/nautilus/preferences/%gconf.xml
```

---

### Post by BetterSense on 2008-06-17
I looked it up and it was NOT checked. So I didn't check it; if I understood your post correctly I'm supposed to not have it checked?

---

### Post by ibuclaw on 2008-06-17
Yes, it is supposed to be unchecked.

The purpose of the key is to enable/disable having your home folder on your desktop.

Perhaps, enabling and disabling the feature might fix this.

Also, check that the system-wide level isn't enabled either, run this command
```
sudo gconftool-2 -t bool -s /apps/nautilus/preferences/desktop_is_home_dir false
```
It's exactly the same as the one above, it just has **sudo** in it.

Also, can you post the output of these sequence of commands.
```

cd
ls -lA
cd Desktop
ls -lA

```
So I can be sure that they are indeed files and not symlinks.

If you don't want to flood your next post with the output, just put it all into a [pastebin]("http://pastebin.ubuntu.com/") and send us the link.

Regards
Iain

---

### Post by BetterSense on 2008-06-17
Google actually found me a bug report where checking or unchecking the home-is-desktop thing doesn't work. I concluded that's what I have since it wasn't doing anything. 

One of the fixes suggested was to go ~/.config/user-dirs.dirs and manually edit the text file adding whatever directory you wanted to be the desktop. It was currently set to /home, so I set it to ./home/desktop.

I think what probably happened, is I had renamed my /Desktop folder to /desktop, out of preference. So when I updated to Hardy, it must not have found a /Desktop file, and so it decided to kick itself into a mode where my whole home was on the desktop. I would have thought it would just create a /Desktop directory, but go figure.

---

