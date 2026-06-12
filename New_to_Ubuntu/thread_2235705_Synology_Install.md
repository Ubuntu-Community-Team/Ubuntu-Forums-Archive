---
title: "Synology Install"
date: 2014-07-22
forum: New to Ubuntu
---

### Post by Lagbehind on 2014-07-22
I have a Synology DS213j unit which I wish to attach to the my Ubuntu pc using Synology Assistant. I have downloaded the files from the website and unzipped them and have the following instructions which I can not understand.

The file names are:

[LIST]
[*]SynologyAssistant-5.0-4448.tar.gz 
[*]install.sh 
[*]HowToInstallAssistant.txt - this is the one above 
[/LIST]


Please can some one help?

[SIZE=1][FONT=arial]Instructions on how to install and run Synology Assistant:

(1) To install Synology Assistant, run the script "install.sh" which will
    guide you through the following steps:

    (a) Remove the Beta version if any:

    sudo rm -rf /usr/local/Synology /usr/local/bin/SynologyAssistant

    (b) Unpack file "SynologyAssistant-5.0-XXXX.tar.gz" to the directory
        you want, such as "/usr/local" or ".":

    tar -C ./ -zxvf SynologyAssistant-5.0-XXXX.tar.gz

    (c) Create the shortcut to /usr/local/bin:

        sudo ln -sf /path/install/SynologyAssistant/SynologyAssistant \
    /usr/local/bin/SynologyAssistant

(2) To run Synology Assistant, you can either command:

    /path/install/SynologyAssistant/SynologyAssistant

    or run the shortcut:

        /usr/local/bin/SynologyAssistant

    (if "/usr/local/bin" is existed in your environment variable $PATH,
    just type:             
    SynologyAssistant)[/FONT][/SIZE]

---

