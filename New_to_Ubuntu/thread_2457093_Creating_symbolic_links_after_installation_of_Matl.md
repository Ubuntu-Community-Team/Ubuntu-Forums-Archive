---
title: "Creating symbolic links after installation of Matlab Ubuntu 20.10"
date: 2021-01-25
forum: New to Ubuntu
---

### Post by awildner on 2021-01-25
Yesterday I installed Matlab yesterday using the process outlined in this video:
[https://www.youtube.com/watch?v=Nfg4KdIwEnM](https://www.youtube.com/watch?v=Nfg4KdIwEnM)

After downloading R2020b from the Matlab website from:
[https://www.mathworks.com/downloads/web_downloads/download_release?release=R2020b](https://www.mathworks.com/downloads/web_downloads/download_release?release=R2020b)

I used the commands:

cd Download/Matlab
ls
unzip <name of the file>
cd
sudo ./Downloads/Matlab/install


I got through the installation process, but I can't find Matlab among my applications. I'm thinking maybe this is because during the installation process I may have forgotten to check the box to create a symbolic link? I'm not sure if that would be the reason. As it stands I don't know how to open the app. I was able to find files in usr/local/MATLAB/R2020b which leads me to believe at the vary least it was partially installed.

Thank you in advance for any help.

---

### Post by ActionParsnip on 2021-01-26
What is the output of:
```

sudo updatedb
locate -i matlab*

```
Thanks

---

### Post by awildner on 2021-01-26
sudo: updatedb: command not found

assuming maybe the b at the end of updated was an error:

sudo: update: command not found

and after the locate -i matlab* code:

Command 'locate' not found, but can be installed with:
sudo apt install mlocate  # version 0.26-3ubuntu3, or
sudo apt install plocate  # version 1.0.4-4

---

### Post by SeijiSensei on 2021-01-26
Is there a "bin" directory under /usr/local/MATLAB/R2020b, or perhaps just a file named "matlab" somewhere around there.  If the installer is aware of /usr/local, then there may be an executable in /usr/local/bin.

Locate is a very useful program to have. Run "sudo apt install mlocate".  Then run "sudo updatedb" to build the database of filenames. It will be automatically maintained after that. Now you can type "locate some_string" and get a list of all the files with that string. There are advanced options to use regular expressions and other features. See [man locate](https://linux.die.net/man/1/locate) for details.

---

### Post by Holger_Gehrke on 2021-01-26
The 'db' at the end of that command was not an error; you simply don't have locate installed and therefore the companion program to **update** the **d**ata**b**ase for locate isn't installed either. (Which seems strange to me; I always assumed locate was installed by default ... )

The video you linked to doesn't show the program being started graphically; he starts it from the command line with 'matlab'. In the answer to a comment he explains what the symlink is for: matlab does not change PATH so the program could be called directly, instead it puts a link to the program in a directory that is in $PATH. If you neither change PATH nor create a symlink you can still run the program by entering the full path and the name of the program - something like '/usr/local/MATLAB/R2020b/matlab' or '/usr/local/MATLAB/R2020b/bin/matlab', probably.

By the way, if you don't use (or need) the various toolboxes for Matlab, there's an Open Source replacement available (GNU Octave); version 5.2 is in the repositories for Ubuntu 20.10 and can be installed with a simple 'sudo apt install octave'. AFAIK the language is mostly the same and there are extensions to Octave to replace many of the more popular toolboxes.

Holger

---

### Post by awildner on 2021-01-26
There is a bin directory, /usr/local/MATLAB/R2020b/bin. There is a file titled matlab which is opened as a read-only text editor file. 

I ran "sudo apt install mlocate" to install locate, which was done successfully it seemed.

I ran "sudo updatedb" and the command didn't have any response in the terminal.

I next ran "locate -i matlab" 

The resulting code is too long for this post.

When I ran, '/usr/local/MATLAB/R2020b/bin/matlab' I got this licensing error:

License checkout failed.
License Manager Error -9
This error may occur when: 
-The hostid of this computer does not match the hostid in the license file. 
-A Designated Computer installation is in use by another user. 
If no other user is currently running this program, you may need to activate.

Troubleshoot this issue by visiting: 
[https://www.mathworks.com/support/lme/R2020b/9](https://www.mathworks.com/support/lme/R2020b/9)

Licensing error: -9,57.

I did previously try to install Matlab on this laptop with windows 10 OS (it's a hand-me-down and I've previously been a mac user), but during install the hard drive failed. I bought a new hard drive and figured it was a good time to make the jump to Linux.

Thank you for the open source recommendation, I'll probably give that a go in the future. I need Matlab for school so to avoid unforeseen complications I'll stick with that for now.

---

### Post by awildner on 2021-01-26
Following the steps provided by the link I the code. I'll update when I've completed them.

---

### Post by awildner on 2021-01-27
Those steps work and I'm able to run the program now. Although looks like some part of it failed:

Gtk-Message: 15:20:04.084: Failed to load module "canberra-gtk-module"
Gtk-Message: 01:15:49.418: Failed to load module "canberra-gtk-module"

Is there a way to create an Icon link among my other apps so i don't have to access through my command line every time?

---

### Post by Holger_Gehrke on 2021-01-27
Creating a graphical starter isn't all that complicated. You just need a [.desktop file]("https://specifications.freedesktop.org/desktop-entry-spec/latest/") and put it in one of the places (/usr/share/applications for system wide installation, $HOME/.local/share/applications for user specific installation) where these are supposed to go.
```

[Desktop Entry]
Version=1.0
Type=Application
Name=Matlab
Comment=Matlab R2020
[COLOR=#ff0000]Icon=[/COLOR]
[COLOR=#ff0000]Exec=[/COLOR]
[COLOR=#ff0000]Path=[/COLOR]
NoDisplay=false
Categories=Development;Education;Math
StartupNotify=true
Terminal=false

```
Copy this into an editor, add values to the lines marked in red (Icon is the path and name of an image file to use as the icon for the program; Exec is the command to run; Path is the directory to run the program in) and save under an arbitrary name ending in .desktop in one of the directories named above.

You can disregard the message about 'canberra-gtk-module'; canberra is a module for playing sounds in response to (input-) events; looks like Matlab can use that if it's installed, but it isn't.

Holger

---

