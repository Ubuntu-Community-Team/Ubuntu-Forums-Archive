---
title: "Unable to install Anything on Ubuntu 7.10"
date: 2013-07-13
forum: New to Ubuntu
---

### Post by shanikushwaha on 2013-07-13
Hi All,

I am a New member and started learning Linux.
all i did is Installed ubuntu 7.10 server i386 on my VMWare Virtual Machine.
After installation when i started playing around in the system i checked that few things do not work properly or may be i am doing it incorrectly.

1:- if i type "apropos ls" i got ls:nothing appropriate.
[ATTACH=CONFIG]244702[/ATTACH]
2:- i tried to edit .bashrc and tried to edit aliases for 'clear' & 'rm -i' as following.
#alias c='clear'
#alias rm='rm -i'
[ATTACH=CONFIG]244703[/ATTACH]
and saved them but when tried got an error as  "-bash: c: command not found."

3:- emacs is not there so i tried to install it.

[ATTACH=CONFIG]244704[/ATTACH]
I tried with [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update
[/FONT][/COLOR]but it was the same.


pls check and give a solution for these.

---

### Post by bry012 on 2013-07-13
In regards to emacs, I don't think emacs 22 is available in the ubuntu repositories. However emacs 23 and 24 are available. So unless there is a reason you need emacs 22 I would try one of those.

I don't know if you have restarted your terminal but aliases only take effect after a reboot of the terminal. I am not too familiar with working with servers so I am not sure if you can just restart bash or if you will need to restart the whole server. Hope this provides a little insight.

---

### Post by Dennis N on 2013-07-13
The 7.10 release is too old (Oct 2007)  - get and install a supported release such as 12.04, 12.10 or 13.04 and try again.

---

### Post by deadflowr on 2013-07-13
7.10?
That version is dead.
The repos for that version have been killed/moved to the old release archives.
To use it, you'll have to change the repositories from the 7.10 repos to the old-release repos.

In truth, though, just upgrade to a newer release, as the packages in the old-release are full of all the existing bugs and problems that might have plagued the release when it's support ended several, at this point, years ago.

---

### Post by Impavidus on 2013-07-13
7.10 is end of live (and has been for ages). Instead of trying to get such an old version to work, you can better install a supported version (&#8805;12.04).

Concerning making that alias, you have to reload your .bashrc before they work.```
source .bashrc
```

---

### Post by deadflowr on 2013-07-13
> **Impavidus said:**
> 
Concerning making that alias, you have to reload your .bashrc before they work.```
source .bashrc
```

And shouldn't the aliases be uncommented as well. ie, remove the # symbol before alias.

---

### Post by shanikushwaha on 2013-07-13
Thanks All ...
Well i restarted the terminal and tried [I]source .bashrc 
[/I]after all the suggestions made,I would better upgrade to a newer version.
I installed 7.10 as a learning tool only.
anyways, Once i am done with anything above 12.* , I would come back with problems as i know i am a dumbass :lolflag:

Thanks Everyone for the suggestions ):P

---

