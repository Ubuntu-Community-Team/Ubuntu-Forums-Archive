---
title: "icons disappear, other bad stuff"
date: 2012-10-10
forum: New to Ubuntu
---

### Post by jonabark on 2012-10-10
I transferred some music files from an iPod to rhythmbox and it seems to have worked fine but sometime during the couple hours of using ubuntu several things started happening. 1) 5 icons disappeared from the launcher leaving a grey button ( that still opens the program), icons also disappeared from the dash home box and there is no volume control thing on the top right bar (with battery and connection icons) 2) the settings icon in top right was unresponsive and would not allow shut down 3) when I downloaded the latest 30 updates the launcher icons all reverted to a large size after having spent hours on this forum getting help to use a script to make them smaller.

---

### Post by NikTh on 2012-10-10
> **jonabark said:**
> the launcher icons all reverted to a large size **after having spent hours on this forum getting help to use a script to make them smaller.**

Hi , 

I assume that you are taking about **ubuntu-2d** **(unity-2d)** and not compiz (ubuntu - Unity 3d). 

Probably with the update some system configuration files be replaced as others not and now you have this miss-configured system. 

If and only If you are taking about **unity-2d** then follow this. 

Press Ctrl+Alt+F2 keys combo to revert in Console Mode. Login there with username & password and then give (carefully) bellow commands

```
sudo service lightdm stop
sudo apt-get install --reinstall unity-2d-common unity-2d-shell unity-2d-panel unity-2d
sudo dpkg-reconfigure unity-2d-common unity-2d-shell unity-2d-panel unity-2d
sudo apt-get install -f
sudo dpkg --configure -a 
sudo service lightdm start
```Hopefully above commands will : reinstall config files of Unity-2D , reconfigure the packages , install or remove any broken packages and solve your problem. 
**Tip:** The Bash Completion can take place in Console Mode. So if you want auto-fill (cuz in Console mode you have not Desktop Environment) use the [TAB] key to auto-fill the names of the packages in case you don't remember them. 

Thanks

---

### Post by jonabark on 2012-10-10
Yes I do not have a video card insufficient to run 3D so have 2D and was given a script and procedure to reduce the icon size to 32. I haven't used console mode  much so am still unsure on the details of the procedure you sugggst. Can I copy your commands in a single batch, then Console mode ,name /pass, and then paste the commands? Or will I need to do them one line at a time? Also I don't get the part about the auto fill with the tabs?

---

### Post by vasa1 on 2012-10-10
> **jonabark said:**
> **I'm increasingly skeptical about ubuntu**. ... the launcher icons all reverted to a large size after having **spent hours on this forum** getting help to use a script to make them smaller.

It would help if you cut out the "commentary" and focus on the issue at hand.

If you spent time searching the forum, you could have come across this thread, [Changing icon size in Unity 2d Ubuntu 12.04]("http://ubuntuforums.org/showthread.php?t=1943423&highlight=unity"), which indicate [here]("http://ubuntuforums.org/showpost.php?p=11783581&postcount=5"), [here]("http://ubuntuforums.org/showpost.php?p=11846042&postcount=9"), [here]("http://ubuntuforums.org/showpost.php?p=11916303&postcount=16"), and elsewhere in that thread that each update of Unity 2D will cause the icons to revert to their larger size.

Anyway, Windows 8 will soon be available.

---

### Post by jonabark on 2012-10-10
OK, since your comments are in sync with the advice on getting quick response on the ubuntu forums I am, after some inner debate and attempts to clarify myself, simply going with it, removing the comments and asking for help. l have icons that have just disappeared and are grey buttons: the home folder, the calculator, the gedit, and several more in the dash home area. What can I do?

---

### Post by audiomick on 2012-10-10
> **jonabark said:**
>  Can I copy your commands in a single batch, then Console mode ,name /pass, and then paste the commands? Or will I need to do them one line at a time?

Best do them one at a time. You wont have to put in your password every time. When you do a sudo, it sticks for a while. As long as you don't mess around too much you will probably only have to give the password for the first command

>  Also I don't get the part about the auto fill with the tabs?

Try it out. Type in the first letter or two of a command that you know to exist and then hit the tab key.

I just tried that myself to make sure of what happens. On the basis of what I have read, I was expecting the terminal to auto-fill in the rest of the command, but what I actually got was a list of the commands that start with those letters and then a new prompt with the couple of letters still there waiting to continue. Any rate, if you get stuck half way through a command, hit tab to let the terminal guess what you are trying to type.

---

### Post by jonabark on 2012-10-10
I tried Nik Th's sudo ?? commands and they seemed to be doing things but nothing changed . The icon images are still missing.

---

### Post by NikTh on 2012-10-10
Hi , 
you said , you used a script  to change the configuration of Unity-2D. Can you provide this script ? (or the link you found it?) 

Also provide the last updates . ```
sudo cat /var/log/apt/term.log > history.txt
gedit history.txt
```scroll down and take a look at the date.

Also see ```
sudo cat /var/log/apt/history.log >> history2.txt
gedit history2.txt
``` 

Post the results _(of the specific date)_ back here. **Put the results between the brackets** [noparse]```
Here
```[/noparse] so can be readable.

Thanks

---

### Post by jonabark on 2012-10-10
Below is the script placed in the home folder. The code to activate was
(sudo python ./script.py 32

But my main concern now are the icons

```
import shutil
import sys
import os

def getparent (content, line_nr):
    for i in range (line_nr - 1, -1, -1):
        if "{" in content[i].lstrip():
            return content[i].lstrip().split(" ")[0]

def change_line (content, key, value, parent):
    line_nr = 0
    for line in content:
        if line.lstrip().startswith(key + ":"):
            lparent = getparent(content, line_nr)
            if parent == lparent:
                content[line_nr] = key + ": " + value + "\n"
                return content
        line_nr = line_nr + 1        

def load_file (filename):
    file = open (filename, "r")
    content = file.readlines()
    file.close()
    return content
    
def write_file (filename, content):
    shutil.copyfile (filename, filename + ".bak")
    file = open (filename, "w")
    for line in content:
        file.write (line)
    file.close()
    return 
            
shell_qml = "/usr/share/unity-2d/shell/Shell.qml"
icontile_qml = "/usr/share/unity-2d/shell/common/IconTile.qml"
launcherlist_qml = "/usr/share/unity-2d/shell/launcher/LauncherList.qml"
launcheritem_qml = "/usr/share/unity-2d/shell/launcher/LauncherItem.qml"

if (len(sys.argv) > 1):
    icon_size = int(sys.argv[1])
else:
    sys.exit("Please enter your desired icon size as the first argument.")
    
if not os.geteuid() == 0:
    sys.exit("Script must be run as root.")
 
content = load_file (shell_qml)
content = change_line (content, "width", str (icon_size + 16), "LauncherLoader")
write_file (shell_qml, content)
content = load_file (icontile_qml)
content = change_line (content, "sourceSize.width", str (icon_size), "Image")
content = change_line (content, "sourceSize.height", str (icon_size), "Image")
write_file (icontile_qml, content)
content = load_file (launcherlist_qml)
content = change_line (content, "property int tileSize", str (icon_size + 6), "AutoScrollingListView")
content = change_line (content, "property int selectionOutlineSize", str (icon_size + 16), "AutoScrollingListView")
write_file (launcherlist_qml, content)
```

---

### Post by vasa1 on 2012-10-10
I would not be comfortable using a script. There's no telling when it will break because of changes in the format (wording, line numbers, comments) or content.
From the links I provided, I was quite interested in reducing the icon size, but mods to the underlying files were coming too frequently for my liking.

---

### Post by jonabark on 2012-10-10
alternate suggestion? is there a more permanent resize that will not be affected by updates, or should I find another version of linux  that is less reliant on the 3d unity? Debian? or maybe forget about the clunky icons and just get to where everything else works the way we want it to.

---

### Post by vasa1 on 2012-10-11
> **jonabark said:**
> alternate suggestion? is there a more permanent resize that will not be affected by updates, or should I find another version of linux  that is less reliant on the 3d unity? Debian? or maybe forget about the clunky icons and just get to where everything else works the way we want it to.
If there is a permanent way, I've not come across it.

Yes, it may be a good idea to look around: Ubuntu itself has several "flavors" with different approaches. I suspect that's a whole new topic by itself and would totally depend on your sense of aesthetics, your work needs, your competence, your computer's specs and so on. 

I myself have tried out Unity 3D, Unity 2D, Xfce and now LXDE.

---

### Post by jonabark on 2012-10-11
OK vasa, or others. Hints on where to start looking for a good fit Linux OS? Here is what Priscilla would like on her small new aspire one D270 netbook Intel Atom 1.6 Ghz 1 MB ram .  
A stable reasonably fast OS
1)A mail program that does a full address book and will import v cards- prefer thunderbird
2) A good word program 
3) a music player that will transfer MP3's from ipod and play online radio
4) chromium
5) a simple photo program

Lubuntu?, Debian?, CentOS?

---

