---
title: "i want to install this ide on MX :: the uPyCraft IDE"
date: 2019-10-03
forum: Programming Talk
---

### Post by dilbert_one on 2019-10-03
hello and good evening, 



i want to install this ide on MX - Linux. 

the uPyCraft IDE .. guess i can use this tutorial:
LINK. [https://randomnerdtutorials.com/install-upycraft-ide-linux-ubuntu-instructions/](https://randomnerdtutorials.com/install-upycraft-ide-linux-ubuntu-instructions/)




**link** [https://randomnerdtutorials.com/uPyCraftLinux.](https://randomnerdtutorials.com/uPyCraftLinux.)


```




$ cd Downloads
$ ls -l
  uPyCraft_linux_V1.X
[IMG]https://ubuntuforums.org/image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==[/IMG]



```

and this 


```

$ chmod +x uPyCraft_linux_V1.X
[IMG]https://ubuntuforums.org/image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==[/IMG]

```




see the piece of code: 
```

$ ./uPyCraft_linux_V1.X[IMG]https://ubuntuforums.org/image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==[/IMG]



```


and then it goes like so:



I do not have Ubuntu here - but i have a MX-Linux here.  But as i want to install uPyCraft on the Mx-System i guess that i can use the above mentioned commands too. Since Ubuntu relies on Debian and MX does too.  This is all the reason for this above mentioned thread!


i sometimes make sure myself in something while writing things down.  And in this case i just wanted to ask you - if you can confirm the idea - that  Since Ubuntu relies on Debian and MX does too  - i would have no issues to install the above mentioned ide on the MX18.03




```

update : if i do so i stuck here: 
insgesamt 26620
-rw-r--r-- 1 martin martin 27256160 Sep 26 19:16 uPyCraft_linux_V1.0
martin@MartinsMX-Rechner:~/Downloads
$ ls -l
insgesamt 26620
-rw-r--r-- 1 martin martin 27256160 Sep 26 19:16 uPyCraft_linux_V1.0
martin@MartinsMX-Rechner:~/Downloads
$ ^C
martin@MartinsMX-Rechner:~/Downloads
$ chmod +x uPyCraft_linux_V1.X
chmod: Zugriff auf 'uPyCraft_linux_V1.X' nicht möglich: Datei oder Verzeichnis nicht gefunden
martin@MartinsMX-Rechner:~/Downloads
$ chmod +x uPyCraft_linux_V1.X
chmod: Zugriff auf 'uPyCraft_linux_V1.X' nicht möglich: Datei oder Verzeichnis nicht gefunden
martin@MartinsMX-Rechner:~/Downloads
$ chmod +x uPyCraft_linux_V1.0
martin@MartinsMX-Rechner:~/Downloads
$ chmod +x uPyCraft_linux_V1.0
martin@MartinsMX-Rechner:~/Downloads
$ ./uPyCraft_linux_V1.X
bash: ./uPyCraft_linux_V1.X: Datei oder Verzeichnis nicht gefunden
martin@MartinsMX-Rechner:~/Downloads
$ ls -l
insgesamt 26620
-rwxr-xr-x 1 martin martin 27256160 Sep 26 19:16 uPyCraft_linux_V1.0
martin@MartinsMX-Rechner:~/Downloads
$ [IMG]https://ubuntuforums.org/image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==[/IMG]

```








the uPyCraft IDE  see the  tutorial. [https://randomnerdtutorials.com/install-upycraft-ide-linux-ubuntu-instructions/](https://randomnerdtutorials.com/install-upycraft-ide-linux-ubuntu-instructions/)
and see this  [https://randomnerdtutorials.com/uPyCraftLinux](https://randomnerdtutorials.com/uPyCraftLinux).






```


$ cd Downloads
$ ls -l
 
```
 
uPyCraft_linux_V1.X






and see this 


```




$ chmod +x uPyCraft_linux_V1.X



```





see the piece of code: 


```




$ ./uPyCraft_linux_V1.X

```


finally i got this here


```




root@MartinsMX-Rechner:/home/martin# su
root@MartinsMX-Rechner:/home/martin# apt-get install python3-venv
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
The following additional packages will be installed:
  python3.5-venv
Die folgenden NEUEN Pakete werden installiert:
  python3-venv python3.5-venv
0 aktualisiert, 2 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
Es müssen [ration werden 39,9 kB Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren? [J/n] j
Holen:1 http://ftp.de.debian.org/debian stretch/main amd64 python3.5-venv amd64 3.5.3-1+deb9u1 [5.954 B]
Holen:2 http://ftp.de.debian.org/debian stretch/main amd64 python3-venv amd64 3.5.3-1 [1.066 B]
Es wurden 7.020 B in 0 s geholt (40,6 kB/s).
Vormals nicht ausgewähltes Paket python3.5-venv wird gewählt.
(Lese Datenbank ... 256952 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Entpacken von .../python3.5-venv_3.5.3-1+deb9u1_amd64.deb ...
Entpacken von python3.5-venv (3.5.3-1+deb9u1) ...
Vormals nicht ausgewähltes Paket python3-venv wird gewählt.
Vorbereitung zum Entpacken von .../python3-venv_3.5.3-1_amd64.deb ...
Entpacken von python3-venv (3.5.3-1) ...
python3.5-venv (3.5.3-1+deb9u1) wird eingerichtet ...
Trigger für man-db (2.7.6.1-2) werden verarbeitet ...
python3-venv (3.5.3-1) wird eingerichtet ...
root@MartinsMX-Rechner:/home/martin



```



well  something goes wrong here.  i have to find out what goes on here. 


note: the system gives back the the data were not found.. 


any idea ?


[B]
update: [/B]

[COLOR=#353C41][FONT=&amp]finally got there :
 
 
i followed the instructions:
[https://randomnerdtutorials.com/install-upycraft-ide-linux-ubuntu-instructions/](https://randomnerdtutorials.com/install-upycraft-ide-linux-ubuntu-instructions/)
 
 
Once i have activated the virtual environment,  i  should be able to list out packages using pip list and verify version using python --version.
 
that said - i continued: 
 
[/FONT][/COLOR]>  
[COLOR=#353C41][FONT=&amp][COLOR=#000000]python3 -m venv myVirtEnv

root@MartinsMX-Rechner:/home/martin# python3 -m venv myVirtEnv

root@MartinsMX-Rechner:/home/martin# source myVirtEnv/bin/activate

(myVirtEnv) root@MartinsMX-Rechner:/home/martin# python --version
Python 3.5.3
(myVirtEnv) root@MartinsMX-Rechner:/home/martin# pip list

DEPRECATION: The default format will switch to columns in the future. You can use --format=(legacy|columns) (or define a format=(legacy|columns) in your pip.conf under the 
[list] section) to disable this warning.

pip (9.0.1)

pkg-resources (0.0.0)

setuptools (33.1.1)

(myVirtEnv) root@MartinsMX-Rechner:/home/martin#
[/COLOR][/FONT][/COLOR] 
[COLOR=#353C41][FONT=&amp] 
well i guess that i now can proceed with the futher steps
 
 
see the [COLOR=#000000][FONT=monospace]myVirtEnv AND  where it is located...`?![/FONT][/COLOR]


> [COLOR=#000000]myVirtEnv) root@MartinsMX-Rechner:/home/martin# python --version
Python 3.5.3
(myVirtEnv) root@MartinsMX-Rechner:/home/martin# pip list
DEPRECATION: The default format will switch to columns in the future. You can use --format=(legacy|columns) (or define a format=(legacy|columns) in your pip.conf under the 
[list] section) to disable this warning.
pip (9.0.1)
pkg-resources (0.0.0)
setuptools (33.1.1)
(myVirtEnv) root@MartinsMX-Rechner:/home/martin# ./uPyCraft_linux_V1.0
bash: ./uPyCraft_linux_V1.0: Datei oder Verzeichnis nicht gefunden
(myVirtEnv) root@MartinsMX-Rechner:/home/martin# ls -l
insgesamt 48
-rw-r--r-- 1 martin martin    0 Okt 14 10:09 2019_10_14___10__uhr+#
drwxr-xr-x 3 martin martin 4096 Sep 30 11:05 AppData
drwxr-xr-x 2 martin martin 4096 Sep 30 11:10 Bilder
drwxr-xr-x 2 martin martin 4096 Okt  7 14:08 cp210x
drwxr-xr-x 2 martin martin 4096 Sep 24 20:49 Desktop
drwxr-xr-x 2 martin martin 4096 Sep 24 21:28 Dokumente
drwxr-xr-x 3 martin martin 4096 Okt  7 14:26 Downloads
drwxr-xr-x 2 martin martin 4096 Sep 24 21:28 Musik
drwxr-xr-x 6 martin martin 4096 Okt 14 10:19 myVirtEnv
drwxr-xr-x 2 martin martin 4096 Sep 24 21:28 Öffentlich
drwxr-xr-x 3 martin martin 4096 Sep 30 09:17 PycharmProjects
drwxr-xr-x 2 martin martin 4096 Sep 24 1:28 Videos
drwxr-xr-x 2 martin martin 4096 Sep 24 21:28 Vorlagen
(myVirtEnv) root@MartinsMX-Rechner:/home/martin#[/COLOR]
[/FONT][/COLOR]

look forward to hear from you 

love to hear  from you

---

