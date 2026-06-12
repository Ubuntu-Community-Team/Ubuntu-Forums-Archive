---
title: "Question about apt-get message"
date: 2012-10-17
forum: New to Ubuntu
---

### Post by patilsb on 2012-10-17
hi my friends i[SIZE=3] unpack tg[SIZE=3]z file  and msg showing like:
[/SIZE][/SIZE] satish@satish-PATIL:~$ cd /home/satish/Downloads/android-sdk-linux/
satish@satish-PATIL:~/Downloads/android-sdk-linux$ sudo apt-get install 
[sudo] password for satish: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[SIZE=3][COLOR=Magenta]The following packages were automatically installed and are no longer required:[/COLOR][/SIZE]
  language-pack-kde-zh-hans-base calligra-l10n-engb firefox-locale-zh-hans
  calligra-l10n-zhcn language-pack-kde-en kde-l10n-engb
  language-pack-zh-hans-base kde-l10n-zhcn language-pack-zh-hans
  language-pack-kde-zh-hans language-pack-kde-en-base
Use 'apt-get autoremove' to remove them.
                                                   tell me how can i install my packages automatically ?

---

### Post by CharlesA on 2012-10-17
If it is a tar.gz, you would have to compile the program in order to get it to run.

As for the apt-get message, it just tells you there are packages installed that are no longer needed.

---

