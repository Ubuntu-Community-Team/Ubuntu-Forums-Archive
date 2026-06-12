---
title: "Wine won't install"
date: 2007-05-23
forum: Programming Talk
---

### Post by abdelilah on 2007-05-23
Hello

i have an old but the most stable ubuntu distribution 5.10,i want to install the newest wine so i compile the source everythink is Ok 
./configure                   echo $?  0
make depend               echo $?  0
make                            echo $?  0

but when i want install wine this ugly thinks happend

abdel@ubuntu:~/Desktop/wine_complete/wine/wine-0.9.37$ sudo make install
make[1]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools »
make[1]: « makedep » est à jour.
make[1]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools »
make[1]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/libs »
make[2]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/libs/port »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/libs/port »
make[2]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/libs/wine »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/libs/wine »
make[2]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/libs/wpp »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/libs/wpp »
make[1]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/libs »
make[1]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools »
make[2]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/widl »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/widl »
make[2]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/winebuild »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/winebuild »
make[2]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/winedump »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/winedump »
make[2]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/winegcc »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/winegcc »
make[2]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/wmc »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/wmc »
make[2]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/wrc »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/wrc »
make[1]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools »
make[1]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/include »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/include »
make[1]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/include »
../tools/mkinstalldirs -m 755 /usr/local/include/wine/windows/ddk
make[1]: execvp: ../tools/mkinstalldirs: Permission non accordée
make[1]: *** [/usr/local/include/wine/windows/ddk] Erreur 127
make[1]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/include »
make: *** [include/__install__] Erreur 2
abdel@ubuntu:~/Desktop/wine_complete/wine/wine-0.9.37$
abdel@ubuntu:~/Desktop/wine_complete/wine/wine-0.9.37$ sudo make install
make[1]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools »
make[1]: « makedep » est à jour.
make[1]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools »
make[1]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/libs »
make[2]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/libs/port »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/libs/port »
make[2]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/libs/wine »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/libs/wine »
make[2]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/libs/wpp »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/libs/wpp »
make[1]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/libs »
make[1]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools »
make[2]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/widl »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/widl »
make[2]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/winebuild »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/winebuild »
make[2]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/winedump »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/winedump »
make[2]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/winegcc »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/winegcc »
make[2]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/wmc »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/wmc »
make[2]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/wrc »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/wrc »
make[1]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools »
make[1]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/include »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/include »
make[1]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/include »
../tools/mkinstalldirs -m 755 /usr/local/include/wine/windows/ddk
make[1]: execvp: ../tools/mkinstalldirs: Permission non accordée
make[1]: *** [/usr/local/include/wine/windows/ddk] Erreur 127
make[1]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/include »
make: *** [include/__install__] Erreur 2
abdel@ubuntu:~/Desktop/wine_complete/wine/wine-0.9.37$ cd tools/
abdel@ubuntu:~/Desktop/wine_complete/wine/wine-0.9.37/tools$ sudo sh install-sh 
install-sh: no input file specified.
abdel@ubuntu:~/Desktop/wine_complete/wine/wine-0.9.37/tools$ sudo sh install-sh mkinstalldirs
install-sh: no input file specified.
abdel@ubuntu:~/Desktop/wine_complete/wine/wine-0.9.37/tools$ cd .. abdel@ubuntu:~/Desktop/wine_complete/wine/wine-0.9.37$ sudo make install make[1]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools »
make[1]: « makedep » est à jour.
make[1]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools »
make[1]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/libs »
make[2]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/libs/port »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/libs/port »
make[2]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/libs/wine »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/libs/wine »
make[2]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/libs/wpp »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/libs/wpp »
make[1]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/libs »
make[1]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools »
make[2]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/widl »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/widl »
make[2]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/winebuild »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/winebuild »
make[2]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/winedump »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/winedump »
make[2]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/winegcc »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/winegcc »
make[2]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/wmc »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/wmc »
make[2]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/wrc »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools/wrc »
make[1]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/tools »
make[1]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/include »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/include »
make[1]: entrant dans le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/include »
../tools/mkinstalldirs -m 755 /usr/local/include/wine/windows/ddk
make[1]: execvp: ../tools/mkinstalldirs: Permission non accordée
make[1]: *** [/usr/local/include/wine/windows/ddk] Erreur 127
make[1]: quittant le répertoire « /home/abdel/Desktop/wine_complete/wine/wine-0.9.37/include »
make: *** [include/__install__] Erreur 2

i know it is written in french but this mean Permission non accordée=you don't have permission
 even if when i use sudo. 
can someone help me please .

---

### Post by treak007 on 2007-05-24
hmm, the only thing I can think of is to try giving your user permission to write to the folder it's trying write to.  I've noticed that sometimes a file will be marked as read-only, and neither my user account, not the superuser can write to it.

idk, just a guess.

---

