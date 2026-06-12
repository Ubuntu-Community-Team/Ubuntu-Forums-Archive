---
title: "programs"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by ericsonlouis on 2012-08-20
Ok I got a question what application should i download to open the executable file?

---

### Post by Frogs Hair on 2012-08-20
What kind of file or program ? If it is a Windows exe you would need to install wine from the software center. Not all programs run in Wine. [http://www.winehq.org/](http://www.winehq.org/)

---

### Post by critin on 2012-08-20
Do you have a Windows lan network?  Separate machines?  If you share your ubuntu/linux files, samba will be installed so you should be able to open windows files.

I don't use Wine and have no issues getting to my windows files on separate machines.   If Windows is on the same machine, another partition, sharing through Samba should be all you need to do.  (hopefully)
I am NOT speaking of games.

---

### Post by anewguy on 2012-08-20
As Frogs Hair stated, you said you want to OPEN an executable file not share windows files across a network.  Here are 3 scenarios I can think of:

(1) You want to open (execute) a Linux program.  To do this, you either just type the program name in, double-click on it from the file explorer, or for your own or other programs go to the folder they are in and type ./<your program name here>

(2) You want to open (execute) a Windows program (.exe, etc.) in Linux.  Can't just do that.  You must install something like Wine (free) or crossover (I think that's the name, and the last I checked it wasn't free).  Windows isn't Linux, Linux isn't Windows.  You can't mix executables - they are linked against totally different items.  You could also install playonlinux (in the repositories or the software center) - it's a "helper" to Wine.

(3) You have a Windows self-extracting archive as a .exe that you want to get the files from in Linux.  You can try to open it with the archive manager - it may or may not work. Again, as a Windows .exe file you can not open (execute) it in Linux without something like Wine or a virtual machine running Windows.

---

### Post by synaptix on 2012-08-20
> **Frogs Hair said:**
> What kind of file or program ? If it is a Windows exe you would need to install wine from the software center. Not all programs run in Wine. [http://www.winehq.org/](http://www.winehq.org/)

If it doesn't work in Wine, one can always install either Virtualbox OSE from Software Center or get the [Oracle VM VirtualBox here]("https://www.virtualbox.org/wiki/Linux_Downloads") and install a Windows guest system onto it.

---

### Post by ericsonlouis on 2012-08-20
It is a bot said to be made for linux. It works for other people but it will not work for me

---

### Post by llamabr on 2012-08-20
> **ericsonlouis said:**
> It is a bot said to be made for linux. It works for other people but it will not work for me

Maybe you should show us exactly what you're trying to run.

If it really is an .exe file, it probably will not run.  You may be able to get it going with wine, but wine is very rarely the correct solution to your problem.  Usually there is a native application which work do what you want, and which will work better.

If by 'executable file' you mean a .bin or .sh, probably we can give you some guidance.

---

### Post by spjackson on 2012-08-21
> **ericsonlouis said:**
> It is a bot said to be made for linux. It works for other people but it will not work for meIf you downloaded some sort of executable directly (i.e. not in a zip or tar archive or similar), you will need to explicitly make it executable. Suppose the program is called myprogram and you downloaded it to your Downloads directory, then in a terminal do:
```

cd ~/Downloads
chmod +x myprogram
./myprogram

```This assumes, of course, that you trust this program and the source you got it from.

Note that this won't work if it's a binary executable that needs shared libraries that you don't have (or different versions thereof), or if it's a script e.g. a Perl script and you don't have perl installed.

What do other people do to run it? What happens when you do the same?

---

### Post by anewguy on 2012-08-21
Give us the name and where you downloaded it from and perhaps we can see more of what it is you are trying to ask.

---

### Post by ericsonlouis on 2012-08-21
It is a yaeb bot and ppl tell me make it excutable then run it but it does not work for me

---

### Post by spjackson on 2012-08-21
> **ericsonlouis said:**
> It is a yaeb bot and ppl tell me make it excutable then run it but it does not work for meYou need to be explicit about what steps you have taken and what the results are if you want people to be able to help you.

[LIST]
[*]What command did you run to make it executable?
[*]Did any error message appear when you ran that command?
[*]What command did you use to run the program?
[*]Did any error message appear when you ran this command?
[/LIST]

---

### Post by newb85 on 2012-08-21
It sounds like the file you downloaded is a .rar file.  Because the .rar format is proprietary, Ubuntu doesn't include support by default, but it can be easily added.

First, go to Software Sources and enable the Multiverse Repository.

Then, from the command line, 

```
sudo apt-get isntall unrar
```

Once you've installed unrar, you should be able to open the .rar file using Archive Manager, which will allow you to extract the appropriate file from it.  Once you've extracted the appropriate file, make it executable, and it should work from there.

---

### Post by Frogs Hair on 2012-08-21
There are a number different yaeb bots available, so the knowing the source would help.

---

### Post by ericsonlouis on 2012-08-21
I downloaded it from  [http://www.sendspace.com/pro/dl/502mzl](http://www.sendspace.com/pro/dl/502mzl)  

but u have to be a member to download it and i made yaeb excutable through properties and where is software scources

---

### Post by wirelessmonkey on 2012-08-21
Clicking the link did actually download the binary.  I did not run it, nor will I, but if you are truly willing to risk it here's what you need to do to run it.

Open a terminal, then:

```

cd Downloads
sudo chmod +x YAEB2550

```

Then you should type 
```

./YAEB2550

```

This should start your 'bot'

---

### Post by newb85 on 2012-08-21
> **ericsonlouis said:**
> where is software scources

There are several ways to access the Software Sources.  From the Software Center, "Edit>Software Sources".  In Synaptic, "Settings>Repositories".  Or in Update Manager, click "Settings..."    All three take you the same place.  (Once upon a time, simply typing "Software Sources" in Unity's dash or Gnome's search would take you there, but that's no longer the case.)

However, it looks like my advice about unrar doesn't apply in this case.  The first YAEB bot my Google search turned up was in a .rar file, but yours doesn't seem to be.

---

