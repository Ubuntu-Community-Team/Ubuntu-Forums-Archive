---
title: "Trouble with `unrar`"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by Lakeside on 2008-10-24
I have a  `rar` file I`m trying to open on Ubuntu Hardy Heron,  so I took this advice:  `[UPDATE: to install unrar in Ubuntu you need the Multiverse Repository enabled.]
Basically, to unrar a file in Linux, just navigate to the directory where your rar archive is and type **unrar x [filename.rar]**, replacing [filename.rar] with the name of your rar archive.`  Well, first of all, I don`t know what the multivers Rep. is or how to find it but..I did enter unrar x [filename.rar), substituting my filename, and minus the brackets, and also putting sudo before it all. Of course I did this at the terminal, and not sure what they meant about  `navigate to the directory where your rar archive is`, how would I type a command in thereÉ  Anyway it didn`t work. I got this: 
`Cannot open ******.rar
No such file or directory
No files to extract` Grateful for any help, thanks

---

### Post by Dark Ocean on 2008-10-24
I don't know exactly what you mean but, in a terminal use;

```
sudo apt-get install rar
```

Then just browse to the file, not via the terminal, and right click the file. Choose extract here.

---

### Post by cashmoney on 2008-10-24
The only way I have gotten anything to work with .rar files in ubuntu was to install wine and install winrar into wine.  I've had no luck with any of the other methods.

> Sudo apt-get install wine

download winrar
Right-click on winrar.exe and open with wine.

next you'll navigate to winrar in wine Applications>Wine>Browse C:\ Drive 

Winrar installs to /program files/winrar/bin/winrar.exe open it 
then click file>open> and navigate to the .rar file.

If you need more detailed instructions let me know.

Nate

---

### Post by Archmage on 2008-10-24
Here is an example to navigate to the folder you want.

[http://easierbuntu.blogspot.com/2008/07/navigating-folders-from-command-line.html](http://easierbuntu.blogspot.com/2008/07/navigating-folders-from-command-line.html)

But it might be easier to do this with the graphical GUI and simply use Nautilus.

---

### Post by Crandom on 2008-10-24
Go to System > Administration > Software Sources and check the box that says: "Software restricted by copyright or legal issues (multiverse)" then press ok.

Then open a terminal and type these 2 commands:
```
sudo apt-get update
sudo apt-get install unrar
```
to navigate in the terminal, use the cd command, for example:
```
cd Documents
```
will take you to your documents. Type "ls" to list the files and folders in your current directory. Then type unrar x [filename.rar]

---

### Post by Sarmacid on 2008-10-24
> **Dark Ocean said:**
> I don't know exactly what you mean but, in a terminal use;

```
sudo apt-get install rar
```

Then just browse to the file, not via the terminal, and right click the file. Choose extract here.

This is the way to go. Either type that in a console, or go to System->Administration->Synaptic package manager, scroll down to rar, right click, select install and click the apply button.

Now you can just go to the folder where you have the file without the need for console, double click it or right click -> extract here.

---

### Post by Lakeside on 2008-10-24
Thanks everyone, sorry for the late post, I was busy getting confused with stuff lol.  Anyway, I got wne installed, and am `unraring` things. :), and I have more than one way to do it now, which is great!

---

### Post by Lakeside on 2008-10-25
Also forgot to thank Archmage for the link, now I know how to `navigate` too (reminds me a little of the old ms dos, and directories..aaaahhh  lol)

---

### Post by misswham on 2008-10-28
i have just reinstalled ubuntu and with the prior installation rar worked fine but now i that i have reinstalled ubuntu, rar keeps giving me an error message 

Read error in the file /home/aretha/Documents/Chris.Rock.Kill.The.Messenger.INTERNAL.HDTV.XviD-aAF/aaf-chris.rock.kill.the.messenger.hdtv.r01_FILES [R]etry, [A]bort 
Read error in the file /home/aretha/Documents/Chris.Rock.Kill.The.Messenger.INTERNAL.HDTV.XviD-aAF/aaf-chris.rock.kill.the.messenger.hdtv.r01_FILES
Inappropriate ioctl for device

and i have done all of the things above.  Any ideas to what I can do?

---

