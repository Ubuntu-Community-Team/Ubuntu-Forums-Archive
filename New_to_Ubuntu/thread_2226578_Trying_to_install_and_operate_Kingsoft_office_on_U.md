---
title: "Trying to install and operate Kingsoft office on Ubunto 14"
date: 2014-05-28
forum: New to Ubuntu
---

### Post by stanley3 on 2014-05-28
I am trying the Ubunto as a replacement for Windows XP 
I am trying to install and operate Kingston office .
I finally managed to install it When I tried to ope it I get a message runs

 from a terminal     et,wpp,wps_error_check.sh

I eventually worked out what  is and how to open the terminal.
I then typed in   et,wpp,wps_error_check.sh 

but got back a error message 

Any help would be much appreciated. This probably a very basic  thing but as I wrote I have only just started to work with Ubunto 

Thanks 

Stanley

---

### Post by Mark de J on 2014-05-28
Why would you use Kingston office in Ubuntu 14.04 if Ubuntu has Libre Office by default?

---

### Post by lisati on 2014-05-28
Do you get the error message when you try to insatll the .deb file?

---

### Post by Bucky Ball on 2014-05-28
... and what exactly is that error message? Vital information. 

I, too, am curious as to why Kingston Office? :-k

---

### Post by zemega on 2014-05-28
Kingston? You will be better off with Kingsoft Office.

---

### Post by mastablasta on 2014-05-28
Download .deb file for linux. Open the file using software center or double click it. wait for it to install. shortcuts will appear and you can run it using those.

why Kingsoft office? interface is isimalr to MS office and they (supposedly) have better compatiility with MS office.

---

### Post by squakie on 2014-05-28
Where did you find it for Linux?  The only link I have found so far is to a non-kingsoft site, and when I see things in the middle of a page that are suddenly in a language I don't know and has a bunch of devil icons by it I tend to shy away.

---

### Post by su:bhatta on 2014-05-28
You get the Alpha from here : [http://wps-community.org/download.html](http://wps-community.org/download.html)
Just download the Alpha12 patch 4 Deb file and use Software Center or GDebi to  install.
Never had any issues installing it.

Used it for 3-4 months, very similar to MS Office, but as for compatibility I didn't come across anything really special.
But then I used it for very normal Word and Excel docs.
LibreOffice does that good for me too, so I don't use up extra 300Mb's for Kingsoft anymore.
Overall, nice experience.

---

### Post by mastablasta on 2014-05-29
oh yeah Kingsoft office is called originally WPS office (in China). the also have android version. not sure about iOS...

---

### Post by LastDino on 2014-05-29
I think OP opted for Kingsoft office because it does save the documents in MS office format by default and it looks very similar to MS. But that was an old news, I too used it for only month or so and went back to Libre office. If we can't trust US I doubt we can trust China :p

---

### Post by zemega on 2014-05-29
> **LastDino said:**
> I think OP opted for Kingsoft office because it does save the documents in MS office format by default and it looks very similar to MS. But that was an old news, I too used it for only month or so and went back to Libre office. If we can't trust US I doubt we can trust China :p

Well, according to this blog post below, Canonical is teaming up with Kingsoft to produce a business version. Can we get a confirmation on that?

[http://opensuseadventures.blogspot.ca/2014/05/is-canonical-planning-to-take-out.html](http://opensuseadventures.blogspot.ca/2014/05/is-canonical-planning-to-take-out.html)

---

### Post by stanley3 on 2014-05-29
Thanks for all the suggestions. A couple of points I meant  to write Kingsoft  not Kingston.
Why Kingsoft ? I used it with XP  and was used to it. However the main reason was I am very new to Ubunto I am trying to find out how to use it on a second computer    mostly by trial and error before I switch. The literature for beginners is not so easy to follow for example I had a message that the programme is started from a terminal and I had no idea what a terminal is 

It keeps me occupied 

Stan

---

### Post by LastDino on 2014-05-29
> **stanley3 said:**
> Thanks for all the suggestions. A couple of points I meant  to write Kingsoft  not Kingston.
Why Kingsoft ? I used it with XP  and was used to it. However the main reason was I am very new to Ubunto I am trying to find out how to use it on a second computer    mostly by trial and error before I switch. The literature for beginners is not so easy to follow for example I had a message that the programme is started from a terminal and I had no idea what a terminal is 

It keeps me occupied 

Stan

Google is my best friend whenever I find myself in similar situations. Try to be more precise with searches and you will often have desired answers withing few minutes. Especially when you are using something like Linux which is quite well documented.

---

### Post by su:bhatta on 2014-06-02
> **stanley3 said:**
> .
. However the main reason was I am very new to *Ubunto* I am trying to find out how to use it on a second computer    mostly by trial and error before I switch. The literature for beginners is not so easy to follow for example I had a message that the programme is started from a terminal and I had no idea what a terminal is 


First things first , it is Ubuntu not Ubunto :)

Next, Kingsoft office, once installed can be started from the Icons and Terminal is not required.
Once installed, if you are using Ubuntu 14.04, you can search them from the 'Dash' which is the first icon on the 'Dock' on the left side of your screen.
A terminal is the Command line way to interact with your system. You can find it by using the shortcut : Ctrl+T when in Desktop, or again, you can use the 'Dash' to find the terminal.

---

### Post by Vladlenin5000 on 2014-06-02
If you haven't managed to install it yet, the following method should work. All you need is the terminal (open it with _CTRL+ALT+T_ or search in the dash, "ter" should be enough) and **lots of patience** (it can take several minutes, don't close the terminal before everything is finished, ie, when it gets back to a line with your username and "$"):

You need to know whether you Ubuntu is 32 or 64-bit because the package you're going to install is for 32-bit systems. Installing in a 64-bit system requires additional step prior to the actual installation. That said use the following commands, one at the time and one per line. Copy from here with CTRL+C as usual or right-click -> Copy, then paste it in the terminal right after the $ symbol with _CTRL+SHIFT+V_ or right-click -> Paste, then ENTER; type your password when prompted.

**For 64-bit systems only **(start with the commands in the next code box if yours is 32-bit)
```
sudo dpkg --add-architecture i386 && sudo apt-get update
```

**For 32-bit/64-bit systems** (this is the actual download, installation and removal of DEB package when no longer needed)
```
cd && wget -O kingsoft-office-NoobsLab.deb  http://drive.noobslab.com/data/apps/kingsoft-office/kingsoft-office_9.1.0.4280~a12p4_i386.deb
sudo dpkg -i kingsoft-office-NoobsLab.deb
rm kingsoft-office-NoobsLab.deb
```

Original source: [http://www.noobslab.com/2013/05/microsoft-office-alternative-kingsoft.html](http://www.noobslab.com/2013/05/microsoft-office-alternative-kingsoft.html)

---

