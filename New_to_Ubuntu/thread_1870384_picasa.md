---
title: "picasa"
date: 2011-10-27
forum: New to Ubuntu
---

### Post by Karlof on 2011-10-27
Hi forum
 
I have downloaded picasa and installed.The  terminal confirms it has been installed
 
but it will not work when the icon is activated
 
Thie has happened on two separate discs of ubuntu 11.4 one of which already had
picasa loaded nto the system
 
Linux is great but very reluctant to make it easy to use anything other than its own software
 
If it provides the facility why make it difficult
 
Can anyone help on the picasa problem
 
Cheers Karlof

---

### Post by Lars Noodén on 2011-10-27
Picasa appears to [require WINE](http://picasa.google.com/linux/download.html) and not to run natively.  As such it's a Windows app and not a Linux app.  That might be part of the problem or all of it.  

Did you try Shotwell or Digikam yet?  And if so, where did they fall short?

---

### Post by Karlof on 2011-10-27
Hi

For me picasa is a better crisper layout and easier to use than any
of the ubuntu options

The main point is why include on the ubuntu disc when it can't be used
it is not ethical

Karlof

---

### Post by wolfen69 on 2011-10-27
> **Karlof said:**
> 
The main point is why include on the ubuntu disc when it can't be used
it is not ethical

Karlof

Picasa is not included on the ubuntu disc, and is a windows app, not linux. You need WINE to make it work.

---

### Post by Karlof on 2011-10-27
Hi Sorry but


Ubuntu 11.4 community edition Includes"" Adobe air Adobe flash Adobe reader
Ardour Audacity Picasa skype Virtual box  VLC and much more""

This is the reason I bought the magazine that supported the disc

I am a newbie and maybe computer ignorant,but I thought  picasa is 
Google product what have they to do with Microsoft

On the download site it specifies picasa for linux the edition 3.0 
is beta could this be the problem (not stable yet ???) 

I am sure I read somewhere that linux is integral to Google
If so you would expect picasa to work

Cheers 

Karlof

---

### Post by Lars Noodén on 2011-10-27
> **Karlof said:**
> I am sure I read somewhere that linux is integral to Google
If so you would expect picasa to work



Follow the link in post #2 above and you can see that WINE is part of the installation.  That means that Picasa is NOT a Linux application but instead is a Windows application running in Linux over the WINE APIs.  Not developing a Linux version is a sign that performance on Linux is not a priority.  If it were, there would be a native version and not a kludge using the Windows APIs via WINE.  (Though WINE itself is a fine and useful program, apps run in it are not Linux)

---

### Post by Karlof on 2011-10-27
Hi maybe I thick but

I get on the picasa site through firefox and google

  Click on picasa and there is a download for ubuntu specific i386 deb 32&64

Why?? if it does not work. I have been reading the forums, a great deal of users
are having problems with picasa 

Adobe flash is not linux  why does that work

Cheers Karlof

---

### Post by oldfred on 2011-10-28
I am still on Maverick, so I do not know if this works on the newer versions, but I just install the standard Windows version now 3.8 into wine.

                       [http://www.webupd8.org/2010/04/how-to-install-picasa-36-in-ubuntu.html](http://www.webupd8.org/2010/04/how-to-install-picasa-36-in-ubuntu.html)
    [http://www.ubuntugeek.com/howto-install-picasa-3-5-in-ubuntu.html#more-2019](http://www.ubuntugeek.com/howto-install-picasa-3-5-in-ubuntu.html#more-2019)
    [LEFT][http://www.omgubuntu.co.uk/2009/09/picasa-35-linux-install.html](http://www.omgubuntu.co.uk/2009/09/picasa-35-linux-install.html)[/LEFT]
    [LEFT]But I never installed Picasa 3.0[/LEFT]
    [LEFT][http://ubuntuforums.org/showthread.php?t=1385837](http://ubuntuforums.org/showthread.php?t=1385837)[/LEFT]
    
    [LEFT]  114  wget [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)[/LEFT]
    [LEFT]  115  sudo wget [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)[/LEFT]
    [LEFT]  116  sudo chmod 777 winetricks[/LEFT]
    [LEFT]  117  sudo apt-get install cabextract wine wine-gecko[/LEFT]
    [LEFT]  118  winetricks allfonts fontsmooth-rgb gecko allfonts[/LEFT]
    [LEFT]Then download picasa for windows
[http://dl.google.com/picasa/picasa38-setup.exe](http://dl.google.com/picasa/picasa38-setup.exe)
 ([http://dl.google.com/picasa/picasa36-setup.exe]("http://dl.google.com/picasa/picasa35-setup.exe"))
 run it, and the installer should start.[/LEFT]
    [LEFT]rename to picasa and move to wine programs[/LEFT]
        [LEFT]/home/fred/.wine/drive_c/Program Files/Google/Picasa3/runtime defaults.ini remove chg printer2 to printers[/LEFT]
    [LEFT]printerURL=https://client4.google.com/providers/printers.html[/LEFT]

---

### Post by Karlof on 2011-10-28
Hi Forum 

Well I downloaded picasa from google

Then
sudo apt-get update
sudo apt-get install picasa 

message picasa already installed new version

so I typed into terminal picasa not installed

then in the terminal appeared a message in a box would I like to use gnome for launch

so I said yes
picasa now in system I do not understand what happened in the terminal any ideas


Thanks everybody for your advice and help

cheers karlof

---

### Post by Karlof on 2011-10-30
Hi oldfred

I eventually browbeat the software installer to install picasa

I spent a day trying different ways to install to no avail

cheers

karlof

---

### Post by Paqman on 2011-10-30
> **Karlof said:**
> 
I am sure I read somewhere that linux is integral to Google
If so you would expect picasa to work


Google does use Linux heavily on their servers, but it's a big company. Their Picasa team doesn't seem to think providing a proper Linux version is important.

---

