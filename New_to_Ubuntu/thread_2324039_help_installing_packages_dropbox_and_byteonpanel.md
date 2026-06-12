---
title: "help installing packages dropbox and byteonpanel"
date: 2016-05-10
forum: New to Ubuntu
---

### Post by rmlazzari on 2016-05-10
Hi, my name is Renato and I'm begginer to Linux SOs, using Lubuntu 15.10. (I've got tyied of viruses and commercial exploit with the MS OS) I've installed this SO in my son's PC (his name is Gabriel) and now I'd like to install two applications: one, to monitor the Internet traffic (sometimes it fails) and other, Dropbox (my son uses this for studies and work).

I've downloaded and unzip (right-click in the downloaded files and "extract here") two packages, "dropbox_2015.10.28_i386" and "byteonpanel-0.2.0". Now I have two folders under the standard Firefox folder "Downloads", the same name of the packages.

The instruction I have to install Dropbox is:

1 - tar xjf ./nautilus-dropbox-1.6.1.tar.bz2


2 - cd ./nautilus-dropbox-1.6.1; ./configure; make; make install;

I changed the second instruction to "/home/gabriel/Downloads/dropbox_2015.10.28_i386",
opened LXTerminal and typed "cd /home/gabriel/Downloads/dropbox_2015.10.28_i386", it seems to work, but the instruction
".\configure" doesn't worked, it answer "arquivo ou diretório não encontrado" in brazilian portuguese. ("File ou folder
doesn't found" in English, I guess).

Then, before asking you I read the "readme" and "install" files from the byteonpanel folder and it refers
the similars instructions (configure, make, etc.). I guess I have to open LXTerminal as administrator
but I don't know how to do that.

I've get this packages from "https://bitbucket.org/mozbugbox/byteonpanel/wiki/Home" and
"https://www.dropbox.com/install?os=lnx". The first package unziped created files and folders
but the second created only anothers .gz files.

I'd like you to ask you to excuse my not-too-good English and to ask you, if you can, to give me
simple instructions starting from the download operation,
on how to install these packages. The "Central de Programas do Lubuntu" doesn't
show me neither of this two. And more, could I install something called "configure" or "make" before install
these packages?

Thanks a lot.

---

### Post by howefield on 2016-05-10
Any reason why you wouldn't use the deb package for dropbox ? It would be much easier to install for yo, download the relevant package (seems like 32bit is what you need) and double click to install..

Not sure about byteonpanel, it looks quite old and unmaintained, I'd probably suggest looking for something current.

---

### Post by rmlazzari on 2016-05-10
Thank you for answer, howefield.

For Dropbox, no reason at all. Could you indicate a link? Or, if there is no link, something like "sudo apt-get..."? I've seached and tryied to found something like that but I didn't get any. Could I download and unzip something? Where I could double-click?

Now, for byteonpanel, it's the only program I know to monitoring the network activity, but I realy need a program like that because my ISP is very unstable then we never know if our request was "listened" by our Internet server. I remember the MS Windows showed two computers in the tray, and they blinked. Now it's unsecure for us to know if we have - or not - to reset the modem or the router... if the Internet are realy being availeble for us.

As I asked, please excuse if my questions are primarily.

Thanks

---

### Post by howefield on 2016-05-10
> **rmlazzari said:**
> For Dropbox, no reason at all. Could you indicate a link? Or, if there is no link, something like "sudo apt-get..."? I've seached and tryied to found something like that but I didn't get any. Could I download and unzip something? Where I could double-click?

On the same page that you indicated getting the dropbox tarball from, you will see an option for an Ubuntu 32 bit deb package. The Ubuntu package will do fine for Lubuntu.

[https://www.dropbox.com/install?os=lnx](https://www.dropbox.com/install?os=lnx)

From your posts above I think that you are running 32 bit Ubuntu but if in fact you are using 64 bit Ubuntu, then you can click the 64 bit package link., double clicking on the deb package once downloaded should start the installation process and (hopefully) be self explanatory from there.

---

### Post by rmlazzari on 2016-05-10
It worked for Dropbox, thanks! It was just double-click in the downloaded file.

And I think I'm actualy using the 32bits system, as you can see above (copied from system information):

-Computer-
Processor        : 2x Intel(R) Celeron(R) CPU        E3400  @ 2.60GHz
Memory        : 2053MB (495MB used)
Operating System        : Ubuntu 15.10
User Name        : gabriel (Gabriel)
Date/Time        : Ter 10 Mai 2016 12:38:14 BRT

-Version-
Kernel        : Linux 4.2.0-36-generic (i686)
Compiled        : #41-Ubuntu SMP Mon Apr 18 15:47:56 UTC 2016
C Library        : Unknown
Default C Compiler        : Unknown
Distribution        : Ubuntu 15.10
-Current Session-
Computer Name        : gabriel-DK-7529
User Name        : gabriel (Gabriel)
Home Directory        : /home/gabriel
Desktop Environment        : LXDE (Lubuntu)
-Misc-
Uptime        : 57 minutes
Load Average        : 0,00, 0,00, 0,00

---

### Post by rmlazzari on 2016-05-10
Now, about byteonpanel... I don't care if this is old and unmaintained since it works. And it remains the question: if not this byteonpanel, what program for my SO can indicate to me that my Internet is realy working? And, if is possible but not essential, with witch speed?

---

### Post by buzzingrobot on 2016-05-10
> **rmlazzari said:**
> ... ./configure; make; make install;


That's the traditional, and very generic, series of commands used to build and install source code.  The file you were working with was an archive of source code for Dropbox, not an archive that contains something installable. (Those archives end with ".deb".)

Strong recommendation:  Avoid trying to build and install software from source code archives.  

Your first choice for software should always be the (L)Ubuntu repositories. 

For the other program you're interested in, I would make a new post asking for suggestions about software that can do what you're looking for.

(BTW, if you just want to see if your net connection is working, open a terminal and try, for example, "ping google.com", or some other known address.  If you see messages coming back about "..bytes from..." you're good.)

---

### Post by howefield on 2016-05-10
> **rmlazzari said:**
> Now, about byteonpanel... I don't care if this is old and unmaintained since it works.

As I said I wouldn't recommend it but you seem to accept the risks, I only have a 16.04 Lubuntu installation for the moment but to get byteonpanel it was fairly simple. Assuming that the tarball has been extracted to the Downloads folder.

```
cd Downloads/byteonpanel-0.2.0/
```
```
sudo apt-get install gcc intltool pkg-config libcairo2-dev libgtk-3-dev
```
```
./configure
``` 
```
make
```
```
sudo make install
```

Logout or reboot and ByteonPanel can be found in the Internet menu.

As said, this is on 16.04, I'll test on a 15.10 installation and let you know if it the process is exactly the same.

---

### Post by rmlazzari on 2016-05-11
Thank you, buzzingrobot. Actualy I'd love to find something from "Central de Programas do Lubuntu". I've intalled Libreoffice from this and this was very easy and fast. Or, as howefield instructed me, a simple double-click on the downloaded file for Dropbox. Thank you too for the "ping" suggestion. But I'll try once more to do what howefield is orienting me.

---

### Post by rmlazzari on 2016-05-11
> **howefield said:**
> As I said I wouldn't recommend it but you seem to accept the risks, I only have a 16.04 Lubuntu installation for the moment but to get byteonpanel it was fairly simple. Assuming that the tarball has been extracted to the Downloads folder.

```
cd Downloads/byteonpanel-0.2.0/
```
```
sudo apt-get install gcc intltool pkg-config libcairo2-dev libgtk-3-dev
```
```
./configure
``` 
```
make
```
```
sudo make install
```

Logout or reboot and ByteonPanel can be found in the Internet menu.

As said, this is on 16.04, I'll test on a 15.10 installation and let you know if it the process is exactly the same.

Thank you again, howefield. I did what you suggested but I'm affraid it doesn't worked. The answer was:

gabriel@gabriel-DK-7529:~/Downloads/byteonpanel-0.2.0$ sudo apt-get install gcc intltool pkg-config libcairo2-dev libgtk-3-dev
[sudo] senha para gabriel:
Lendo listas de pacotes... Pronto
Construindo árvore de dependências       
Lendo informação de estado... Pronto
O pacote gcc não está disponível, mas é referenciado por outro pacote.
Isto pode significar que o pacote está faltando, ficou obsoleto ou
está disponível somente a partir de outra fonte

E: O pacote 'gcc' não possui candidato para instalação
E: Impossível encontrar o pacote intltool
E: Impossível encontrar o pacote pkg-config
E: Impossível encontrar o pacote libcairo2-dev
E: Impossível encontrar o pacote libgtk-3-dev

---

### Post by howefield on 2016-05-11
As I said, that was on a 16.04 install, I won't have a 15.10 machine until later today to test.

---

### Post by rmlazzari on 2016-05-11
Thanks again, howefield, for your extreme good will on help me, including installing that old version (15.10) in your own machine. Realy nice from you!
Well... and following you and buzzingrobot advices I quit with this byteonpanel. I've joined an LXDE forum and asked there an alternative newer to that utility.
As soon as I get an answer, I will post here.

Thanks a lot again!

---

### Post by howefield on 2016-05-11
Cool rmlazzeri.

Installing Byteonpanel worked fine on 15.10 with the instructions as posted earlier, the only "issue" being that the byteonpanel.desktop file was not created automatically (it did on 16.04) - that error is non fatal and easily worked around by creating the file manually. So it does work but I'd agree with finding an alternative, but if you don't come up with anything we can revisit this thread.

Good luck.

---

### Post by rmlazzari on 2016-05-13
Easier than I thought, without any installing extras! Maybe help somebody:

Just right-click in taskbar, "Panel configuration", "Panel appletes", "Add", "Network Status Monitor".
Double-click in the tray icon and changed "eth0" to "enp2s0" or "lo" and... voilá! Now we know if the connexion is active or not!

Thanks howefield and buzzingrobot for your good will!

---

### Post by rmlazzari on 2016-05-13
Ops! I spoke too fast... When I reboot, the tray icon now shows a "STOP" signal (a red circle with a white bar in it). Then a double-click in that icon shows me a window where I changed "eth0" to "enp2s0": it turned back to "eth0". When I try to configure this option, the system answer me: "A interface não existe. Verifique se ela está escrita corretamente e se seu sistema tem suporte a ela." (in my horrible english, "The interface doesn't exists. Verify if it is correctly wrote and if your system has support to it.")

Can you help me?

---

### Post by CantankRus on 2016-05-13
Maybe your panel is running before your network interface is up so the Byteonpanel applet reverts to default???
Don't have solution for that.

To check your interface ...in the terminal ...
```
netstat -i
```
eg
```
**[COLOR="#006400"]glen@Xenial:~$[/COLOR] netstat -i**
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
**enp3s0**     1500 0   1395532      0      0 0        854817      0      0      0 BMRU
lo        65536 0     14734      0      0 0         14734      0      0      0 LRU
```

Here in unity I use conky to display various system info including netspeed.
You can create your own little window to sit above other windows showing just net speeds.
[ATTACH=CONFIG]269034[/ATTACH]  [ATTACH=CONFIG]269035[/ATTACH]

or 
have a system info conky on your desktop....
[ATTACH=CONFIG]269033[/ATTACH]

If interested let me know and I'll help you get started with conky.

---

### Post by vasa1 on 2016-05-14
> **CantankRus said:**
> Maybe your panel is running before your network interface is up so the Byteonpanel applet reverts to default???
Don't have solution for that.

...
Maybe OP could add a delay for starting the panel in the autostart file.

---

