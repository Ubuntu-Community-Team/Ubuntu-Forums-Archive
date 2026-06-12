---
title: "HOWTO: Installing and compiling the latest latex and kile packages"
date: 2006-07-31
forum: Outdated Tutorials &amp; Tips
---

### Post by jordilin on 2006-07-31
Tetex is no longer mantained (see [http://www.tug.org/tetex/](http://www.tug.org/tetex/), so if we want the latest and greatest, we must install the latex system from the latest TeX live cd install.
First of all remove tetex-base, tetex-common, tetex-bin and kile from the repos.
The tetex package is no longer mantained so get the TeX Live Cd and kile source code from :
[http://www.tug.org/ftp/texlive/Images/](http://www.tug.org/ftp/texlive/Images/)
[http://kile.sourceforge.net/download.php](http://kile.sourceforge.net/download.php)

Get the packages texlive2005-inst-20051102.iso.zip and kile-1.9.1.tar.bz2

Once downloaded the tex live cd iso image unzip it by:
**unzip texlive2005-inst-20051102.iso.zip** and you'll get the iso image. Burn it using your preferred burning app. 

**Installing the Tex system:**
Go to the directory where the TeX Live cd is mounted /media/cdrom and execute:
```
sudo bash ./install-tl.sh
```
You'll get a menu with several options:
Type S (Scheme) and C (install everything). 
Type D (Directory) and you'll get the predefined installation directories. You don't have to change them if you don't want to. The 2 option I changed it to /usr/local/texmf-local but the default is Ok.
Press R to return to the main menu and type I (install). It will take a while to install the tex system in your computer. Once finished you'll get the following screenshot:

[IMG]http://personal.telefonica.terra.es/web/personalinfo/texconfiguraciolivecd.png[/IMG]

Add the following line to your **.bashrc**:
```
PATH=$PATH:/usr/local/texlive/2005/bin/i386-linux
```
close the Console, open a new one and you'll get all the latex tools in the command line :-)
When running latex if you get the error:
/home/yourusername/.texlive2005/texmf-var/ls-R: Permission denied
then go into the /home/yourusername/.texlive2005/texmf-var/ and type
```
sudo chown username:username ls-R
```

**Installing Kile from source**
Install the following packages from the repos:
kde-devel
xlibs-dev
Take into account that kde-devel has more than one hundred dependencies, but it takes less than 15 minutes to download them and install them if you are in a broadband connection.
type:
```
tar -xjvf kile-1.9.1.tar.bz2
```
```
cd kile-1.9.1
```
type ```
kde-config --prefix
``` and you'll get /usr
then 
```
./configure --prefix=/usr
```
if you don't get any errors, then
```
make
```
and ```
sudo make install
```. That's all

If you need the latex2html package download it from [http://www.latex2html.org/](http://www.latex2html.org/) and get the package

latex2html-2002-2-1.tar.gz

type:

```
./configure
```

```
make
```

```
sudo make install 
```

Happy TeXing!!

---

### Post by rlgc79 on 2006-08-13
Nice HOWTO. I didn't known that tetex is no longer maintained. It is the most important piece of software for me.

Some suggestions:
1) You should replace ./configure –prefix=/usr by 
./configure --prefix=/usr

2) I would suggest to use "sudo checkinstall" instead of "sudo make install"

(you have to install checkinstall first: "sudo apt-get install checkinstall")

3) In my opinion, we should always try to give some references, in case there is a mistake in our HOWTO. E.g., [http://kile.sourceforge.net/help.php#compile](http://kile.sourceforge.net/help.php#compile)

4) The first link redirects to the wrong page. It goes to [http://www.tug.org/tetex/](http://www.tug.org/tetex/)) instead of [http://www.tug.org/tetex/](http://www.tug.org/tetex/)  (note the presence of ")" at the end of the address)


Best

---

### Post by jordilin on 2006-08-13
> **rlgc79 said:**
> Nice HOWTO. I didn't known that tetex is no longer maintained. It is the most important piece of software for me.

Some suggestions:
1) You should replace ./configure –prefix=/usr by 
./configure --prefix=/usr

2) I would suggest to use "sudo checkinstall" instead of "sudo make install"

(you have to install checkinstall first: "sudo apt-get install checkinstall")

3) In my opinion, we should always try to give some references, in case there is a mistake in our HOWTO. E.g., [http://kile.sourceforge.net/help.php#compile](http://kile.sourceforge.net/help.php#compile)

4) The first link redirects to the wrong page. It goes to [http://www.tug.org/tetex/](http://www.tug.org/tetex/)) instead of [http://www.tug.org/tetex/](http://www.tug.org/tetex/)  (note the presence of ")" at the end of the address)

Best

1) and 4). Yes, these are typing errors. I'm gonna correct them.

---

### Post by Carolx on 2006-08-13
I alread have kile and some others packages installed but the accents isn't works (Im teX in portugese, and i need a lot of accents, ç,ã,é...). I would like to repair and update the packages on-line (without burn cd). It's possible? 
Im a beginning user of kubuntu (6.06) kde 3.5.2
My trouble-kile is 1.8.1 
I tried some things, but doesn't work yet...
Thank's

---

### Post by jordilin on 2006-08-13
> **Carolx said:**
> I alread have kile and some others packages installed but the accents isn't works (Im teX in portugese, and i need a lot of accents, ç,ã,é...). I would like to repair and update the packages on-line (without burn cd). It's possible? 
Im a beginning user of kubuntu (6.06) kde 3.5.2
My trouble-kile is 1.8.1 
I tried some things, but doesn't work yet...
Thank's

I would recommend upgrading!! As for the accents in kile, you have to go to Settings->Configure Kile go to the left side Editor->Open/Save option and in file format choose the encoding to iso 8859-15 western european and you'll display the accents. Hope it helps!! 8)

---

### Post by rlgc79 on 2006-08-13
Hi, Carolx.

I am able to type in Portuguese using Kile 1.9.1 under Ubuntu Dapper... It should work in Kubuntu as well.

---

### Post by Carolx on 2006-08-30
The thing about accents worked. Thanks. How I do the update?

---

### Post by Copter on 2006-09-02
hi!

thanks jordilin for this howto. i think that i will quit openoffice and start writing some real documents :)

your method is good but it needs some tweaking. first of all if someone uses checkinstall (which i also highly recommend) then kile should be installed this way
```


sudo checkinstall -D
sudo dpkg **--force-overwrite** -i kile_1.9.2-1_i386.deb

```
this way some kate's syntax-highlight files will be updated. i have no idea how to do it without --force-overwrite. i think that this way it is safe.

another thing is that after installing kile it will complain about paths. adding PATHs to .bashrc does not work on my case. kile's system check failes. it is unable to find needed files (latex, makeindex etc.). the trick is to run kile with this command
```


env PATH=$PATH:/usr/local/texlive/2005/bin/i386-linux kile

```
k menu item modification is attached.

[COLOR="Red"]UPDATE[/COLOR]

BTW. we dont need to burn downloaded iso cd. we can mount it
```


mkdir /tmp/iso
sudo mount texlive2005-inst-20051102.iso -t iso9660 /tmp/iso/ -o loop
cd /tmp/iso/
sudo ./install-tl.sh
...

```


copter :]

---

### Post by jordilin on 2006-09-02
Copter,
you are right, kile does not found the latex path unless you execute it from the command line!! that's the reason of writing the path in your .bashrc. I didn't update that, so thanks to point it out.

---

### Post by exisn on 2006-09-04
I can't get it to install through checkinstall with --force-overwrite. I get the following error.

```
Unpacking kile (from kile_1.9.2-1_i386.deb) ...
dpkg: error processing kile_1.9.2-1_i386.deb (--install):
 trying to overwrite `/usr/share/apps/katepart/syntax/bibtex.xml', which is also in package kdelibs-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing --force-overwrite (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 kile_1.9.2-1_i386.deb
 --force-overwrite

```

Any suggestions?

---

### Post by Copter on 2006-09-04
Hi Exisn,

You are correct! it should be
```


sudo dpkg --force-overwrite -i kile_1.9.2-1_i386.deb

```
I will correct that. Thanks for pointing this. When you write --force-overwrite as the last argument than it thinks that it is a package name :). Therefor it should be written as first argument. It should work ok now.

thnx,
Copter :]

---

### Post by exisn on 2006-09-05
It does indeed work now, thanks for the help.

---

### Post by andiii on 2006-09-06
I followed the instructions and installed kile 192 with the checkinstall command.

1) Everything worked out fine, but the manual (F1) is gone. How can I get the kile help back?

2) ubuntu updater wants to update to 1.8 and gives me notices all the time. i don't want to disable the automatic updates because i like the idea. but can i exclude kile from this process somehow?

---

### Post by Cogito² on 2006-09-10
Hi I just started using ubuntu (and linux for that matter) so I don't really understand the OS that well. I went through the installation process in the first post, but I can't actually find 'kile' anywhere in my applications. Is there anything obvious I'm doing wrong here?

---

### Post by canarsie on 2006-09-12
Will kile work if I am using gnome? and if not what should I use instead?

---

### Post by andiii on 2006-09-13
Yes, you can. Just follow the instructions in this thread. The only thing is, you need to install all the depending kde packages.

But having it installed once it's worth the effort!
I installed it with make install instead of checkinstall to exclude it from the package management. Otherwise ubuntu kept telling me that I should update (from 1.9 to 1.8 ](*,) ).

My manual still doesn't work. Also "man kile" won't put out anything. Can I donwload the manual somewhere?

---

### Post by Ruth Lazkoz on 2006-12-04
Hi,

Is it possible to replace the texlive CD installation process by an installation from repositories? 

I guess it would be easier for newbies like me. 

Then of course I would try to do the kile installation as given in the instructions.

---

### Post by Copter on 2006-12-05
Hi Ruth.

Isnt this fixed in Edgy? I thought this silly process with installing TeX from CD was Dapper's issue. I must say that I have no idea how to 'convert' CD content into .deb package.

sorry and good luck,
Copter :]

---

### Post by celsofaf on 2006-12-05
> **canarsie said:**
> Will kile work if I am using gnome? and if not what should I use instead?
Yes. Before I switched fully to KDE and uninstalled Gnome, I used Kile without a problem.

---

### Post by Ruth Lazkoz on 2006-12-05
> **Copter said:**
> Hi Ruth.

Isnt this fixed in Edgy? I thought this silly process with installing TeX from CD was Dapper's issue. I must say that I have no idea how to 'convert' CD content into .deb package.

sorry and good luck,
Copter :]

I got kile+texlive working fine following the instructions in this thread, but now when I restart the computer it says kile icon wasn't found (I am traslating from spanish) 

I have installed Kile 1.9.3, and I managed to add a launcher for kile on the panel with the right icon (which I dowloaded in .svg format), but on the applications menu Kile appears with no icon.

Any hint?

---

### Post by Copter on 2006-12-05
Hmmm. I have no idea why the icon was missing. Maybe try istalling the .deb package once again. I think it shouldnt mess any user defined config files and such.

As far as I know, rebooting Linux box can only mess kernel modules when upgrading or programs that are started on boot (deamons etc.). Kile and TeX enviroment is neither of them, so rebooting shouldnt affect it. Strange...

Copter :]

---

