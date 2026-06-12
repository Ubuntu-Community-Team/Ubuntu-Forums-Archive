---
title: "Adobe Reader doesn't initialize"
date: 2023-12-22
forum: New to Ubuntu
---

### Post by rodrigo7linux on 2023-12-22
Hey, guys! I'm new at Linux Distributions and I decided to start with the classical Ubuntu. But I'm facing a problem installing my Adobe Acrobat Reader. I've installed following the instructions coming from this site:


[https://www.geeksforgeeks.org/how-to-install-adobe-acrobat-reader-on-ubuntu/](https://www.geeksforgeeks.org/how-to-install-adobe-acrobat-reader-on-ubuntu/)


But when I finished it and started the app, it doesn't initialize, no matter how many times I click on it's shortcut. By the way, I've used the file extension .deb with his command dpkg to install it; the instructions from that website were followed until the setup of architecture i386 with **sudo dpkg --add-architecture i386**. After that, when I tried to install the Adobe PDF using **sudo dpkg -i adobe.deb**, it went through an error about dependencies and something about i386; for this, I've used the command sudo apt install -f to correct all dependencies and then I've got success in **sudo dpkg -i adobe.deb**.
Any solution (I know that there is...) please let me know!

---

### Post by MAFoElffen on 2023-12-22
Did you notice that that article was written fro Ubuntu Hirsute 21.04? And the package was for Arch i386? I lot of those libraries aren't there anymore...

What do you need in a pdf app? There are a lot of current, modern alternatives to that now.

---

### Post by deadflowr on 2023-12-23
Should install fine, all those listed i386 packages are still built for Ubuntu up to at least 23.10.
(That also includes all depends those have as well)

Not sure if the OP did it, but you need to run sudo apt update after running the dpkg --add-architecture i386 command.

---

### Post by rodrigo7linux on 2023-12-23
Well, about i386 architecture I've notice that, but I thought if my architecture is x86_64 / amd64 it would work correctly since it's compatible with 32 bits. Please correct me if I'm wrong. The ubuntu's version I didn't notice, however I also couldn't find about its version in that article, where can I find?.
So, what I need in a Pdf App, if you're going to suggest me a better software, is a simple and stable app that saves my last opened pdfs. Like, if I open these pdfs: MagicOfOz.pdf, JavaSpecification.pdf and CrimeAndPunishment.pdf, I need to, when I close the app, the next use of it will restore these files where I've stopped.

---

### Post by rodrigo7linux on 2023-12-23
> **deadflowr said:**
> Should install fine, all those listed i386 packages are still built for Ubuntu up to at least 23.10.
(That also includes all depends those have as well)

Not sure if the OP did it, but you need to run sudo apt update after running the dpkg --add-architecture i386 command.

Strange... So I'm going to reinstall it and see if it works. If not' I'm going to change the PDF app that I will use. 
Also about sudo apt update I've done that after the dpkg --add-architecure i386., but, as we saw, it didn't start the app.

---

### Post by Dennis N on 2023-12-23
If you are not doing so, try to start the program from the terminal. If there is a missing library, it will output an error message. Like this game:

```
dmn@Sydney:~/games/thomasLinuxStandalone$ ./thomasWasAlone
./thomasWasAlone: [COLOR="#FF0000"]error while loading shared libraries: libGLU.so.1: cannot open shared object file: No such file or directory[/COLOR]
```

Then you have to find the package that supplies the needed library using Ubuntu Package Search:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

and install it.

Then repeat.

By the way, the "add-architecture" is no longer necessary (in olden times, it used to be). You were correct that 32-bit support is already there. To verify:
From my U 23.10:

```
dmn@Kayleigh:~$ dpkg --print-foreign-architectures
i386

```

---

### Post by Holger_Gehrke on 2023-12-23
You are aware that that is version 9.5 of Acrobat Reader ? That's more than 12 years old. Adobe stopped supporting Linux a long time ago. You're probably better of using something - anything - else for working with pdf.

Holger

---

### Post by Dennis N on 2023-12-23
>  I need to, when I close the app, the next use of it will restore these files where I've stopped. 
If this is the feature you're looking for, the default Document Viewer does this. To be sure, I opened a pdf document, browsed to page 10, then closed it. Opened it again, and it opened to page 10 where I left off.

---

### Post by MAFoElffen on 2023-12-23
I remember (for Linux) when Adobe changed Acrobat Reader from free to non-free. And that, with that last free version, we kept installing it until I started to wonder if it was wise to use something so old. The copyrights on it are dated 1984-2010...

That version of Acrobat Reader worked well for many years, for what it was... I just spun up a VM of Ubuntu Mate 22.04 LTS and it installed and runs fine. (See screenshot.)

Since then, there are many PDF Readers and Editors that are free and work very well.

EDIT: 
If you look at the photo's in the article, when it did an update to refresh the apt cache, look at the release it displayed of the repo's. That is what gave it away as being for Hirsute. That is a giveaway, and a reminder... 

There are many articles out on the web that are out there for almost forever. If you look for things to do, pay attention to those details to give clues if something may be current or not. Just because something was once possible, and it was once published, doesn't mean it necessarily is current for what you have now. This one still works. But please be careful of that in the future.

I applaud your enthusiasm and sense of adventure. Doing things new helps me to learn new things. It is fun. Welcome to your journey. Have fun.

---

### Post by ActionParsnip on 2023-12-26
[https://linuxconfig.org/how-to-install-adobe-acrobat-reader-on-ubuntu-22-04-jammy-jellyfish-linux](https://linuxconfig.org/how-to-install-adobe-acrobat-reader-on-ubuntu-22-04-jammy-jellyfish-linux)

Please read the warning here. The version you are going to be able to install is from 2013.

I wouldn't bother.....

---

### Post by rodrigo7linux on 2023-12-26
Hm, surely, I've not seen that Adobe was outdated for Linux. It seens that another applications are also in this situation. Before I was installing Adobe PDF, I tried Foxit PDF Reader coming from my Windows experience, but here in Ubuntu this app is very different from Windows, without many functionalities and the GUI was very limited comparing to Windows version.
Btw, only for the experience, as we know that Adobe PDF is not anymore updated for Linux, I ran the Adobe from Terminal as @DennisN suggested and found a similar error.


**[FONT=courier new]./acroread: error while loading shared libraries: libBIB.so: cannot open shared object file: No such file or directory[/FONT]**


I didn't find this library from Ubuntu's package website and also when I run the sudo apt-get install libBIB it doesn't find the related package. If anyone can find any information about this or if I'm comitting a mistake, please share with me.


So, now I will try Okular PDF or adapt my workspace to use the Document Viewer.
Even though, thanks for all of your help and knowledge given, I will pay more attention about app's version next time. We shall continue our journey.

---

### Post by ActionParsnip on 2023-12-27
Lets do this another way as the Acrobat Reader you are trying to install is ancient.....Why are you installing the Adobe PDF reader, specifically? What are you trying to achieve?

---

### Post by MAFoElffen on 2023-12-27
The "Why" meaning (translation) whether you just need to read/view PDFs, edit them or create them... Answering that will help ActionParsnip in recommending a current tool that might fit better.

---

### Post by Impavidus on 2023-12-27
As nobody else commented on this:
> **rodrigo7linux said:**
> Well, about i386 architecture I've notice that, but I thought if my architecture is x86_64 / amd64 it would work correctly since it's compatible with 32 bits. Please correct me if I'm wrong. 
I will.

A processor with amd64 architecture can indeed run both 64 and 32 bit code. However, you can't mix them freely. If you try to run a 32 bit executable using 64 bit libraries, or the other way around, it will fail, as the executable and the libraries aren't binary compatible. They assume different layout for the data in memory.

---

### Post by ActionParsnip on 2023-12-28
May solve the missing libraries issue
[https://askubuntu.com/questions/373532/when-executing-acroreader-it-fails-with-error-while-loading-shared-libraries-l](https://askubuntu.com/questions/373532/when-executing-acroreader-it-fails-with-error-while-loading-shared-libraries-l)

Its a bit old but you are trying to install an old version of Acrobat Reader. I suggest you abandon this and use something newer

---

### Post by Norm24 on 2023-12-30
>  Before I was installing Adobe PDF, I tried Foxit PDF Reader coming from my Windows experience, but here in Ubuntu this app is very different from Windows, without many functionalities and the GUI was very limited comparing to Windows version. 

You won't get anymore functionality out of Adobe Reader 9.5.5 than Foxit.Personally I like the simplicity of Linux version of Foxit,I only use it to read PDF files.

---

