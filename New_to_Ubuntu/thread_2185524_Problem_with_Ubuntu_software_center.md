---
title: "Problem with Ubuntu software center"
date: 2013-11-03
forum: New to Ubuntu
---

### Post by taniakurland on 2013-11-03
I can't open Software Center, I have ubuntu 12.04 LTS, intel proccessor 64 bit. The error on the right end screen says 'Error: opening the catche (E: Encountered a section with no package: header, E problem with mergeList/var/lib/apt/lists/extras.ubuntu.com_ubunt_dists_precise_main_binary_i386_packages,E: THe package lists or status file could not be parsed or opened). This usually means that your installed packages have unmet dependencies.

When I click on software center it tries to open and the shut down. I got the computer with ubuntu one already installed in it few weeks ago. Initially the software center worked. Downloaded VLC, Skype and Google Chromium. After that it stoped working. I have no background in ubuntu or in progreming. I had to search what terminal means and how to open it. I appreciate any help with instructin to a very new beginner.

---

### Post by QIII on 2013-11-03
Moved to new thread.

---

### Post by fantab on 2013-11-03
> **taniakurland said:**
> I can't open Software Center, I have ubuntu 12.04 LTS, intel proccessor 64 bit. The error on the right end screen says 'Error: opening the catche (E: Encountered a section with no package: header, E problem with mergeList/var/lib/apt/lists/extras.ubuntu.com_ubunt_dists_precise_main_binary_i386_packages,E: THe package lists or status file could not be parsed or opened). This usually means that your installed packages have unmet dependencies.

When I click on software center it tries to open and the shut down. I got the computer with ubuntu one already installed in it few weeks ago. Initially the software center worked. Downloaded VLC, Skype and Google Chromium. After that it stoped working. I have no background in ubuntu or in progreming. I had to search what terminal means and how to open it. I appreciate any help with instructin to a very new beginner.

Post the output of:
```
sudo apt-get update
```
from the terminal.

---

### Post by taniakurland on 2013-11-04
Many thanks. Wiil do. Tania

---

### Post by taniakurland on 2013-11-04
Hi again,
I am afraid it did not work. I got a long respond and an Error was identified in line 51. This is what I have got "Get:51 http/archive ubuntu.com precise-update/universe translation-er Fetch 22.3 MB in 17s Reading Package lists...Error! W:GPG error:[http://archive.canonical.com](http://archive.canonical.com) precise Release: The following signatures were invalid:BADSIG 40976EAF437DO5B% ubuntu Archive Automatic signing key<ftmaster@ubunto.com. W: an error occured during the signature verification. The repository is not updted and the previous index files will be used.
Then it continues on concluding : W:failed to fetch [http://extras.ubuntu.com.precise/relese](http://extras.ubuntu.com.precise/relese). W:some files failed to download. They have been ignored or old ones used.
So- Any suggestion? Or should I download a new Ubuntu OP via external disc writer/reader (my computer is a netbook with no disc drive). Appreciate any suggestion.

---

### Post by uzumakifahim on 2013-11-04
Try the following commands in terminal

```
[FONT=Ubuntu Mono]$ sudo -i[/FONT]# apt-get clean
# cd /var/lib/apt
# mv lists lists.old
# mkdir -p lists/partial
# apt-get clean [FONT=Ubuntu Mono]# apt-get update[/FONT]
```

Source : [http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

---

### Post by fantab on 2013-11-04
> **taniakurland said:**
> Hi again,
I am afraid it did not work. I got a long respond and an Error was identified in line 51. This is what I have got "Get:51 http/archive ubuntu.com precise-update/universe translation-er Fetch 22.3 MB in 17s Reading Package lists...Error! W:GPG error:[http://archive.canonical.com](http://archive.canonical.com) precise Release: The following signatures were invalid:BADSIG 40976EAF437DO5B% ubuntu Archive Automatic signing key<ftmaster@ubunto.com. W: an error occured during the signature verification. The repository is not updted and the previous index files will be used.
Then it continues on concluding : W:failed to fetch [http://extras.ubuntu.com.precise/relese](http://extras.ubuntu.com.precise/relese). W:some files failed to download. They have been ignored or old ones used.
So- Any suggestion? Or should I download a new Ubuntu OP via external disc writer/reader (my computer is a netbook with no disc drive). Appreciate any suggestion.

You must post the full output with code tags [#] from the editor.

Run the following commands in the Terminal:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

### Post by taniakurland on 2013-11-04
this is what I got rm: cannot remove `/var/lib/apt/lists/partial': Is a directory

---

### Post by taniakurland on 2013-11-04
still not working- this is what I have got: $ sudo -i# apt-get clean
sudo: invalid option -- '#'
usage: sudo [-D level] -h | -K | -k | -V
usage: sudo -v [-AknS] [-D level] [-g groupname|#gid] [-p prompt] [-u user
            name|#uid]
usage: sudo -l[l] [-AknS] [-D level] [-g groupname|#gid] [-p prompt] [-U user
            name] [-u user name|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-D level] [-g groupname|#gid] [-p prompt] [-u
            user name|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-D level] [-g groupname|#gid] [-p prompt] [-u
            user name|#uid] file ...
tania@tania-1015E:~$ # cd /var/lib/apt
tania@tania-1015E:~$ # mv lists lists.old
tania@tania-1015E:~$ # mkdir -p lists/partial
tania@tania-1015E:~$ # apt-get clean # apt-get update

---

### Post by taniakurland on 2013-11-04
Thank you all so much!!!
 I just looked at my Software Center and it is working again. I am not sure which of the suggestions worked in the end. I think it start working again after I re-logged to the computer. Anyway, thank you all, very greatfull and made me want to learn more about ubuntu.

---

