---
title: "broken packages!"
date: 2013-06-07
forum: New to Ubuntu
---

### Post by vagelism on 2013-06-07
Hello to all.
I got broken packages of mysql in my system and it doesnt let me install or remove any other packages!
How can I resolve it?

---

### Post by Bashing-om on 2013-06-07
vagelism; Hi !

Have you taken dpkg's advise and ran the terminal code:
```
sudo apt-get -f install
sudo apt-get update

```
If so, and still errors - post the complete output for additional guidance.[INDENT=3]
just try'n to help

[/INDENT]

---

### Post by vagelism on 2013-06-07
> **Bashing-om said:**
> vagelism; Hi !

Have you taken dpkg's advise and ran the terminal code:
```
sudo apt-get -f install
sudo apt-get update

```
If so, and still errors - post the complete output for additional guidance.[INDENT=3]
just try'n to help

[/INDENT]

```
[CODE]&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#923;&#953;&#963;&#964;&#974;&#957; &#928;&#945;&#954;&#941;&#964;&#969;&#957;... &#927;&#955;&#959;&#954;&#955;&#951;&#961;&#974;&#952;&#951;&#954;&#949;
&#922;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#942; &#916;&#941;&#957;&#948;&#961;&#959;&#965; &#917;&#958;&#945;&#961;&#964;&#942;&#963;&#949;&#969;&#957;                  
&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#960;&#949;&#961;&#953;&#947;&#961;&#945;&#966;&#942;&#962; &#964;&#951;&#962; &#964;&#961;&#941;&#967;&#959;&#965;&#963;&#945;&#962; &#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951;... &#927;&#955;&#959;&#954;&#955;&#951;&#961;&#974;&#952;&#951;&#954;&#949;
&#916;&#953;&#972;&#961;&#952;&#969;&#963;&#951; &#949;&#958;&#945;&#961;&#964;&#942;&#963;&#949;&#969;&#957;... &#917;&#964;&#959;&#953;&#956;&#959;
&#932;&#945; &#945;&#954;&#972;&#955;&#959;&#965;&#952;&#945; &#949;&#960;&#953;&#960;&#955;&#941;&#959;&#957; &#960;&#945;&#954;&#941;&#964;&#945; &#952;&#945; &#949;&#947;&#954;&#945;&#964;&#945;&#963;&#964;&#945;&#952;&#959;&#973;&#957;:
  mysql-server-5.5
&#928;&#961;&#959;&#964;&#949;&#953;&#957;&#972;&#956;&#949;&#957;&#945; &#960;&#945;&#954;&#941;&#964;&#945;:
  tinyca mailx
&#932;&#945; &#945;&#954;&#972;&#955;&#959;&#965;&#952;&#945; &#960;&#945;&#954;&#941;&#964;&#945; &#952;&#945; &#945;&#957;&#945;&#946;&#945;&#952;&#956;&#953;&#963;&#964;&#959;&#973;&#957;:
  mysql-server-5.5
1 &#945;&#957;&#945;&#946;&#945;&#952;&#956;&#943;&#963;&#964;&#951;&#954;&#945;&#957;, 0 &#957;&#941;&#959; &#949;&#947;&#954;&#945;&#964;&#949;&#963;&#964;&#951;&#956;&#941;&#957;&#945;, 0 &#952;&#945; &#945;&#966;&#945;&#953;&#961;&#949;&#952;&#959;&#973;&#957; &#954;&#945;&#953; 50 &#948;&#949;&#957; &#945;&#957;&#945;&#946;&#945;&#952;&#956;&#943;&#950;&#959;&#957;&#964;&#945;&#953;.
2 &#956;&#951; &#960;&#955;&#942;&#961;&#969;&#962; &#949;&#947;&#954;&#945;&#964;&#949;&#963;&#964;&#951;&#956;&#941;&#957;&#945; &#942; &#945;&#966;&#945;&#953;&#961;&#941;&#952;&#951;&#954;&#945;&#957;.
&#935;&#961;&#949;&#953;&#940;&#950;&#949;&#964;&#945;&#953; &#957;&#945; &#956;&#949;&#964;&#945;&#966;&#959;&#961;&#964;&#969;&#952;&#959;&#973;&#957; 0 B/8746 kB &#945;&#960;&#972; &#945;&#961;&#967;&#949;&#943;&#945;.
&#924;&#949;&#964;&#940; &#945;&#960;&#972; &#945;&#965;&#964;&#942; &#964;&#951; &#955;&#949;&#953;&#964;&#959;&#965;&#961;&#947;&#943;&#945;, &#952;&#945; &#967;&#961;&#951;&#963;&#953;&#956;&#959;&#960;&#959;&#953;&#951;&#952;&#959;&#973;&#957; 0 B &#967;&#974;&#961;&#959;&#965; &#945;&#960;&#972; &#964;&#959; &#948;&#943;&#963;&#954;&#959;.
&#920;&#941;&#955;&#949;&#964;&#949; &#957;&#945; &#963;&#965;&#957;&#949;&#967;&#943;&#963;&#949;&#964;&#949; [&#925;/&#959;]; yes
&#928;&#961;&#959;&#961;&#973;&#952;&#956;&#953;&#963;&#951; &#960;&#945;&#954;&#941;&#964;&#969;&#957; ... 
(&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#946;&#940;&#963;&#951;&#962; &#948;&#949;&#948;&#959;&#956;&#941;&#957;&#969;&#957; ... 366373 files and directories currently installed.)
&#928;&#961;&#959;&#949;&#964;&#959;&#953;&#956;&#945;&#963;&#943;&#945; &#947;&#953;&#945; &#945;&#957;&#964;&#953;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; mysql-server-5.5 5.5.31-0ubuntu0.12.04.1 (&#967;&#961;&#951;&#963;&#953;&#956;&#959;&#960;&#959;&#953;&#974;&#957;&#964;&#945;&#962; &#964;&#959; .../mysql-server-5.5_5.5.31-0ubuntu0.12.04.2_i386.deb) ...
invoke-rc.d: unknown initscript, /etc/init.d/mysql not found.
dpkg: warning: &#951; &#965;&#960;&#959;&#948;&#953;&#949;&#961;&#947;&#945;&#963;&#943;&#945; &#960;&#945;&#955;&#953;&#972; &#963;&#949;&#957;&#940;&#961;&#953;&#959; pre-removal &#949;&#960;&#941;&#963;&#964;&#961;&#949;&#968;&#949; &#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; &#955;&#940;&#952;&#959;&#965;&#962; 100
dpkg - &#948;&#959;&#954;&#953;&#956;&#940;&#950;&#949;&#964;&#945;&#953; &#949;&#957;&#945;&#955;&#955;&#945;&#954;&#964;&#953;&#954;&#940; &#964;&#959; &#963;&#949;&#957;&#940;&#961;&#953;&#959; &#945;&#960;&#972; &#964;&#959; &#957;&#941;&#959; &#960;&#945;&#954;&#941;&#964;&#959; ...
invoke-rc.d: unknown initscript, /etc/init.d/mysql not found.
dpkg: &#963;&#966;&#940;&#955;&#956;&#945; &#963;&#964;&#951;&#957; &#949;&#960;&#949;&#958;&#949;&#961;&#947;&#945;&#963;&#943;&#945; &#964;&#959;&#965; /var/cache/apt/archives/mysql-server-5.5_5.5.31-0ubuntu0.12.04.2_i386.deb (--unpack):
 &#951; &#965;&#960;&#959;&#948;&#953;&#949;&#961;&#947;&#945;&#963;&#943;&#945; &#957;&#941;&#959; &#963;&#949;&#957;&#940;&#961;&#953;&#959; pre-removal  &#949;&#960;&#941;&#963;&#964;&#961;&#949;&#968;&#949; &#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; &#955;&#940;&#952;&#959;&#965;&#962; 100
No apport report written because MaxReports is reached already
                                                              invoke-rc.d: unknown initscript, /etc/init.d/mysql not found.
invoke-rc.d: unknown initscript, /etc/init.d/mysql not found.
dpkg: &#963;&#966;&#940;&#955;&#956;&#945; &#954;&#945;&#964;&#940; &#964;&#959;&#957; &#954;&#945;&#952;&#945;&#961;&#953;&#963;&#956;&#972;:
 &#951; &#965;&#960;&#959;&#948;&#953;&#949;&#961;&#947;&#945;&#963;&#943;&#945; installed post-installation script &#949;&#960;&#941;&#963;&#964;&#961;&#949;&#968;&#949; &#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; &#955;&#940;&#952;&#959;&#965;&#962; 100
&#928;&#961;&#959;&#941;&#954;&#965;&#968;&#945;&#957; &#963;&#966;&#940;&#955;&#956;&#945;&#964;&#945; &#954;&#945;&#964;&#940; &#964;&#951;&#957; &#949;&#960;&#949;&#958;&#949;&#961;&#947;&#945;&#963;&#943;&#945; &#964;&#959;&#965;:
 /var/cache/apt/archives/mysql-server-5.5_5.5.31-0ubuntu0.12.04.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```[/CODE]


Sorry for the language but this problem doesnt allow me to change the language to english ...

---

### Post by yakult on 2013-06-07
sly@sly-desktop:~$ sudo apt-get -f install /home/sly/Área de Trabalho/firefox-21.0.tar.bz2
E: Não foi possível obter trava /var/lib/dpkg/lock - open (11 Recurso temporariamente indisponível)

---

### Post by Bashing-om on 2013-06-07
[COLOR=#000000]vagelism;

English is the only language I "know" --limiting for sure --...from your output I can garner that "mysql-server" is problematic (maybe others ?) ...
try terminal command :
[/COLOR]```
sudo dpkg-reconfigure mysql-server
```
see what effect that has.

[COLOR=#000000]@ yakult ;
That error indicates more than one instance of a package manager is trying to run... only one may do so, close all out and reboot.
Try again with only a single instance of a package manager running, If problems persist, start another thread, as your problem is not related to the situation in this thread.[/COLOR][INDENT=3][COLOR=#000000]best regards

[/COLOR][/INDENT]

---

### Post by slickymaster on 2013-06-07
> **yakult said:**
> sly@sly-desktop:~$ sudo apt-get -f install /home/sly/Área de Trabalho/firefox-21.0.tar.bz2
E: Não foi possível obter trava /var/lib/dpkg/lock - open (11 Recurso temporariamente indisponível)
yakult isso quer dizer que provavelmente estaria aberto ou o Ubuntu Software Center ou o Synaptic, quando executaste o comando no terminal. O que tens a fazer é garantires que estão fechados antes de excutar o comando.

Mas tal como o Bashing-om aconselhou, é melhor começares uma thread nova e não te aproveitares desta. Não só porque isso é contra a política do forum como também torna tudo muito confuso.

---

