---
title: "Trying to install CHIRP with pipx on UBUNTU 23.04"
date: 2023-05-26
forum: New to Ubuntu
---

### Post by savvikas on 2023-05-26
Dear ladies and gents,

I am trying to install the CHIRP software as per instruction on the CHRIP site. I start by installing pipx follow the steps but cannot execute the command below:
*_**pipx install --system-site-packages ./chirp-20230515-py3-none-any.whl**_*
I always get the message below:
*_**Unable to parse package spec: ./chirp-20230509-py3-none-any.whl**_*
I would like to ask should I rephrase the command to 
*_**pipx install --system-site-packages .downloads/chirp-20230515-py3-none-any.whl**_*
or another line of command. As I am new user I do not have so much knowledge on routing to a folder.

Please help me.

---

### Post by Holger_Gehrke on 2023-05-27
The original command ('pipx install --system-site-packages ./chirp-20230515-py3-none-any.whl') assumes the package file is in the current working directory (that's what the './' at the beginning of the path means). So if you just change the current working directory to the directory where the file is it should work. To change the current working directory you use the 'cd' command, for example 'cd ~/Downloads' (a '~' followed directly by a '/' at the beginning of a path is a short way of referring to your home directory). Your second command ('pipx install --system-site-packages .downloads/chirp-20230515-py3-none-any.whl') wouldn't work for two reasons: '.downloads' would be a hidden directory that is a sub-directory of the current working directory (if you meant a directory named 'downloads' that is a subdirectory of the current working directory you could either write '.**/**downloads/' or just 'downloads', either would work); the second problem is that Linux is case sensitive, so there probably is no directory 'downloads' - but there should be one named '**D**ownloads'.

In general: all paths not starting with a '/' are relative to the current working directory. To find out the current working directory you can either look at the prompt (it defaults to '${USER}@$(hostname):$PWD') or enter 'pwd' (**p**rint **w**orking **d**irectory). Components of a path are separated by '/'. A path starting with a '/' is an absolute path that starts at the root of the directory tree. A single '.' as a path component references the current directory (and can under most circumstances be left out); so '/usr/./share' is the same as '/usr/share/'. The './' in the pipx command is necessary because pipx - similarly to pip, pip3, and apt - will interpret names that don't contain any '/' as packages to be downloaded from the python package archive. Two '.' or '..' as a path component means 'one step up in the directory hierarchy'; so '/var/../usr/' is the same as '/usr'. A '.' at the beginning of a file or directory name marks it as hidden; this is more of a convention than anything else and was supposedly a bug that turned into a feature (the original intention was to hide the entries for '.' and '..' that every directory has); you can show hidden files with the '-a' option to 'ls' and most file managers have a way to turn hiding of dot-files on and off.

Holger

---

### Post by savvikas on 2023-05-28
Thank you very much for your answer and the quick lesson on the directories. I will try it and post again here in case I have questions. Again thank you very much.

---

### Post by savvikas on 2023-05-28
Again Thank you very much. I managed to install CHIRP with pipx and also learned something in the process. Again thank you very much. Also I would be grateful if you could propose any site or book to read to know the basics on Linux and terminal.

Kind regards,

Savvas

---

### Post by Holger_Gehrke on 2023-05-28
[http://www.linuxcommand.org](http://www.linuxcommand.org) has a lot of good information and hosts the free download of William Shotts' book "The Linux Command Line". This is not just another free text about the shell, it's free, it's good and there are several translations. There's also a second part - "Adventures with the Linux Command Line" that covers additional topics - not necessarily advanced topics, but stuff that didn't fit in the first one like for example the "Midnight Commander", terminal multiplexers, tput or awk.

Holger

---

### Post by savvikas on 2023-05-28
Again thank you very much. I managed to make CHIRP run and download from my vhf radio. Now I will test it thoroughly.

---

### Post by vk5gdr on 2024-04-14
um, where did you download the actual .whl file, I can't seem to find it even with a google search?

regards
Geoff'
VK5GDR

---

### Post by vk5gdr on 2024-04-14
Hi,

Had the same problem as OP.

Except i hadn't downloaded the package.   So I tried to find it with google and came up blank.

So since you say the ./ part is for a local file and pip will try and pull it from the online packages I tried leaving it out.

(vk5gdr@vk5gdr-radioroom:~$ pipx install --system-site-packages chirp-20230509-py3-none-any.whl
Fatal error from pip prevented installation. Full pip output in file:
    /home/vk5gdr/.local/pipx/logs/cmd_2024-04-15_12.35.19_pip_errors.log

Some possibly relevant errors from pip install:
    ERROR: Could not find a version that satisfies the requirement chirp-20230509-py3-none-any-whl (from versions: none)
    ERROR: No matching distribution found for chirp-20230509-py3-none-any-whl

Error installing chirp-20230509-py3-none-any-whl.)

I'm about ready to throw linux out the window if just updating a preinstalled package is this hard.  I even tried from Muon to update to the latest chirp it has, but that has the same bug (related to python 3 apparently) that the installed version does.
For all I know there's an even later version, but I've no idea where to find out.

So the preinstalled chirp is broken and I can't seem to update it to a version that works.   It's DragonOS which seems to be Lubuntu underneath.

Any help appreciated.

Regards

Geoff
VK5GDR

---

### Post by vk5gdr on 2024-04-14
Never mind, I found the .whl file which predictably is a much later build.   Sorry to be a pain.  But virtually everything in Linux is.

Cheers
Geoff
VK5GDR

---

### Post by coffeecat on 2024-04-15
Old thread closed to prevent further necromancy. If anyone needs help about the same or similar problem, please start your own thread. You may link back to this thread if it helps.

---

