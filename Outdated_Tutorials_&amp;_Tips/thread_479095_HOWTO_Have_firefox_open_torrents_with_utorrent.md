---
title: "HOWTO: Have firefox open torrents with utorrent"
date: 2007-06-20
forum: Outdated Tutorials &amp; Tips
---

### Post by bruenig on 2007-06-20
hmm

---

### Post by stealthbox on 2007-06-28
very good guide, it helped me alot , thank you

---

### Post by rhuarch on 2007-07-02
Thanks for the great guide.  I have only noticed one major problem.  This method works fine as long as utorrent is currently closed.  If you try to open a new torrent file from Firefox with utorrent already open, it kicks back an unknown error.  Anyone else run into this or am I doing something wrong?

---

### Post by bruenig on 2007-07-02
Oh it works for me when I do it even if it is open. You could add a quick test to see if it is running and then if it isn't not to execute the wine "/path/to/utorrent.exe"

```
#!/bin/bash
if [[ ! "$(ps -A | grep utorrent.exe)" ]]; then
   wine "/path/to/utorrent.exe"
fi

```
If it isn't running, it will be launched, if it is, it won't be. But because utorrent monitors /tmp, even though you don't launch it or anything, it will still pick up on the new torrent and add it in theory at least.

---

### Post by kozmic on 2007-07-02
I solved my problem this way:

Instead letting uTorrent check folder for new torrent files, I made a script which makes uTorrent behave in the same way as in Windows.

First, if .torrent files are opened automatically with Firefox, remove this default action here: Edit -> Preferences -> Content -> Manage -> Select the torrent extension, and hit "Remove action".

Create a bash-script which will be the uTorrent launcher you want to open .torrent files with:
```
sudo vim /usr/local/bin/utorrent.sh
```
Inside utorrent.sh:
```
#!/bin/bash
wine "/media/sda1/Program Files/uTorrent/utorrent.exe" $*
```
Remember to change your path to your uTorrent executable in the above step.
Now make it executable:
```
chmod +x /usr/local/bin/utorrent.sh
```

Now when firefox wants to open a .torrent file, select the utorrent.sh file. uTorrent will now, if not started, start and open the torrentfile. If uTorrent is currently running, you will simply get the dialog from uTorrent on where to save the content of the torrent file.

---

### Post by Beatbreaker on 2007-07-07
good guide, i followed the first post and it works for me. - it didn't work so well when utorrent wa already open

kozmics guide worked better for me - you forgot a sudo in your command though:

```
sudo chmod +x /usr/local/bin/utorrent.sh
```

---

### Post by Beatbreaker on 2007-07-08
.

---

### Post by bruenig on 2007-07-09
> **Beatbreaker said:**
> good guide, i followed the first post and it works for me. - it didn't work so well when utorrent wa already open

kozmics guide worked better for me - you forgot a sudo in your command though:

```
sudo chmod +x /usr/local/bin/utorrent.sh
```

Did you try my post above his.

---

### Post by Beatbreaker on 2007-07-15
> **bruenig said:**
> Did you try my post above his.

i tried your way first but i couldnt get it to work when utorrent was already open

---

### Post by misfitpierce on 2007-07-15
Ditch utorrent I heard it was sold to bittorrent which riaa owns or something of the sort. lol

---

### Post by Beatbreaker on 2007-07-15
> **misfitpierce said:**
> Ditch utorrent I heard it was sold to bittorrent which riaa owns or something of the sort. lol

I've actually heard the same thing too - i won't be changing over until i'm sure this is the case though

---

### Post by misfitpierce on 2007-07-15
Well I read part of it somewhere... in any case transmission which can be found on getdeb is a great lightweight program for torrents.

---

### Post by bruenig on 2007-07-24
You guys don't understand the brilliance of that move. The bittorrent corporation who has absolutely no control over anything in terms of what is shared and what isn't, signs a deal with them saying that they won't share any copyrighted material. The get free money from stupid RIAA who doesn't recognize the difference between a bittorrent client or network and the corporation.

---

### Post by ARTO^UK on 2007-07-25
Thanks alot :)

---

### Post by aparigraha on 2007-07-26
Hey.
I've got uTorrent up and running fine through Wine. I've used Opera as a browser for years, and only FF on and off. Connecting Opera with uTorrent was really easy:

Tools->Preferences->Advanced->Downloads->application/x-bittorrent->Edit

```
wine /home/path/to/utorrent.exe
```

No scripts!

The problem is that I haven't been able to get all torrents working with Firefox.
I've tried the script - utorrent.sh

```
#!/bin/bash
wine "/path/to/utorrent.exe" $*
```

I works on and off. Whenever I get torrents with non-english letters like theses íéÈÄåöäÄÖÅ... this script just doesn't handle it. I got an error-can-not-find-file-bla-bla in a small utorrent window.
Asian characters were the same.

So I ripped this guys script from [this thread]("http://ubuntuforums.org/showthread.php?p=1879660#post1879660") and now it works a lot better.

```
#!/bin/sh
LANG=en_US.utf-8
LC_MESSAGES=en_US.utf-8
TORRENT_FILE=`winepath "$1"`
wine "/path/to/utorrent.exe" "$TORRENT_FILE" &
```

Ofcourse... put in the correct /path/to/utorrent.exe

THX Flying_OE

---

### Post by spyros71 on 2007-07-26
Newbie question: why not use Ktorrent instead of u-torrent? In what way is utorrent better so that I should get in trouble installing wine then utorrent and then conecting that to FF? Can someone please explain?

---

### Post by bruenig on 2007-07-28
kde libs slow down the computer.

---

### Post by raonyguimaraes on 2009-09-04
This worked for me :

#!/bin/bash
/home/raony/cxoffice/bin/wine "/home/raony/.cxoffice/winxp/drive_c/Program Files/uTorrent/utorrent.exe" "$*"

*don't forget to use "$*" because sometimes the torrent has strange characters that needs to be escaped

---

### Post by Levo on 2009-09-21
This will work much better and faster:

```

#!/bin/bash
torrent_file="${*##*/}"
wine "/home/YOUR_USER_NAME/.wine/drive_c/Program Files/uTorrent/utorrent.exe" "Z:/tmp/$torrent_file"

```

Assuming "Z:" is configured to be "/" and "/home/YOUR_USER_NAME/.wine/drive_c/Program Files/uTorrent/utorrent.exe" uTorrent's executable full path.

Place this script in "/usr/bin" and point firefox to this.

---

