---
title: "Installing software using terminal"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by Delta62 on 2008-08-05
I just installed Ubuntu for the first time last night, and I've been trying to get my sound to work. I found the appropriate driver for my sound card, and downloaded it.

I have extracted the files onto the desktop. the readme for the files says:

Run one of the following commands as root in the terminal:

   ./installer
   


  OR


   ./installer --with-alsainc=<ALSA_include_directory>

I do know how to open up terminal, and I am very familiar with the Windows cmd terminal. However, I am unfamiliar with the commands for Ubuntu.

What do I need to do to get this driver installed?

Thanks in advance.

---

### Post by bobnutfield on 2008-08-05
This is an install script.  Have you tried typing:

>  sudo ./installer

in a terminal?  You will be prompted for your password.  Try this.

That is what the instructions are tellin you to do.

---

### Post by oldos2er on 2008-08-05
What sound card do you have? 

 To run the installer as root you would enter "sudo ./installer" in the terminal.

---

### Post by Delta62 on 2008-08-05
I have a creative x-fi series card. A beta driver has been released that I found from Creative.

I have run the command, and it asks me for my password, which I enter. after this terminal displays:

sudo ./installer: Command not found.

I am guessing that this is because the terminal is in the incorrect directory?

Edit: Here's the link to the driver if anyone finds it useful:
[http://support.creative.com/downloads/download.aspx?nDownloadId=10530](http://support.creative.com/downloads/download.aspx?nDownloadId=10530)

---

### Post by bobnutfield on 2008-08-05
Where did you unpack the archive (tar.gz file).?  You must be in the same directory that the unpacked files are located.  It's usually best to place them in your home directory for easy access.

---

### Post by northern lights on 2008-08-05
The shell prompt's parent directory is by default /home/USER/ where USER is your username.

You probably downloaded the folder to '/home/USER/' or some downloads subfolder such as '/hime/USER/Downloads/' or the desktop '/home/USER/Desktop/' or the like.

In the terminal, run ```
cd path/to/folder/ && sudo ./installer
```

---

### Post by Delta62 on 2008-08-05
I moved the files to my user folder, the installer works just like it should. Thanks for the info on the context of the cd command too.

---

