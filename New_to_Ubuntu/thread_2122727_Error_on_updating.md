---
title: "Error on updating"
date: 2013-03-06
forum: New to Ubuntu
---

### Post by vagelism on 2013-03-06
Hello to all.
I got this error while I run the update command.

Fetched 466 kB in 9s (48.9 kB/s)                                               
W: GPG error: [http://www.bchemnet.com](http://www.bchemnet.com) debian Release: The following signatures were invalid: BADSIG C95104E509BAC46D Samung Unified Linux Driver Repository
W: Failed to fetch copy:/var/lib/apt/lists/partial/liveusb.info_multisystem_depot_dists_all_main_i18n_Translation-en%5fUS  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/liveusb.info_multisystem_depot_dists_all_main_i18n_Translation-en  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en  Encountered a section with no Package: header

E: Some index files failed to download. They have been ignored, or old ones used instead.

How can I resolve it?
Thank you.

---

### Post by fantab on 2013-03-06
Run the following commands one by one in the Terminal:

```
$ sudo -s                 
# apt-get clean
# cd /var/lib/apt
# mv lists lists.old
# mkdir -p lists/partial
# apt-get clean
# apt-get update
# exit
```

OR

```
$ sudo rm /var/lib/apt/lists/* -vf
$ sudo apt-get update
```

---

### Post by vagelism on 2013-03-06
Thank you, worked great!
Can you please explain me what this code did? 
Copy paste is great , but I would like to learn something from it.

---

### Post by ibjsb4 on 2013-03-06
For an explaination you can use googlubuntu

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=BADSIG&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=BADSIG&sa=Search&cof=FORID:9)
[https://help.ubuntu.com/community/UsingTheTerminal#Commands](https://help.ubuntu.com/community/UsingTheTerminal#Commands)
[https://help.ubuntu.com/10.04/basic-commands/C/files-directories-commands.html](https://help.ubuntu.com/10.04/basic-commands/C/files-directories-commands.html)
[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

And so on.  Or you can use the man page.  So open a terminal and enter (one at a time):

```
man apt-get
man mv
man mkdir
```

And so on

---

### Post by schragge on 2013-03-06
Errors like
```

W: [COLOR=#ff0000]Failed to fetch copy[/COLOR]:/var/lib/apt/lists/partial/liveusb.info_multisystem_depot_dists_all_main_i18n_Translation-en%5fUS
[COLOR=#ff0000]Encountered a section with no Package: header[/COLOR]

```mean that some files under the directory */var/lib/apt/lists* got corrupted. Removing them, or just moving them out of the directory makes *apt-get update* regenerate them anew. That's precisely what was suggested to you.

---

### Post by vagelism on 2013-03-06
> **schragge said:**
> ```

W: [COLOR=#ff0000]Failed to fetch copy[/COLOR]:/var/lib/apt/lists/partial/liveusb.info_multisystem_depot_dists_all_main_i18n_Translation-en%5fUS
[COLOR=#ff0000]Encountered a section with no Package: header[/COLOR]

```Those errors mean that some files in the directory */var/lib/apt/lists/partial* got corrupted. If you remove them, or simply move out of the way, apt-get will happily generate them anew. That's precisely what was suggested to you.

Thank you for the advice!
I have plenty of study now!
:P

---

