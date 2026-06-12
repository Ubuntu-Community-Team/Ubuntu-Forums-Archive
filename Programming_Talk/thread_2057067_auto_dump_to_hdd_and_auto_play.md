---
title: "auto dump to hdd and auto play"
date: 2012-09-12
forum: Programming Talk
---

### Post by Thomasmcdaniel on 2012-09-12
Hello if anyone can help im working on a digital advertising kiosk and we are using vlc media player we need it to read from a flash drive and auto download the files to the hdd and play them automatically this is what we have so for  but  still having some problems  if anyone could please help .Thanks 

```

import time
import os
import threading
def wtl(string):
    f = file("/home/revmedia/playerlog.txt","a")
    f.write(string)
    f.close()

f = file("/home/revmedia/playerlog.txt","a")
f.write("starting\n")
f.close()
class player(threading.Thread):
    medir = ""
    def __init__(self, d):
        threading.Thread.__init__(self)
        print d + " this is d"
        player.medir = d
    def run(self):
        print os.popen("pwd").read()+" before error"
        print player.medir
        os.chdir(player.medir)
        l = os.popen("ls").read().split("\n")
        s = ''
        for k in l:
            if k != '':
                s += "\""+ k + "\" "
        wtl("vlc -L -f --noaudio " + s)
        os.system("vlc -L -f --noaudio " + s)
class player2(threading.Thread):
    medir = ""
    def __init__(self, d):
        threading.Thread.__init__(self)
        print d
        player2.medir = d
    def run(self):
        os.chdir(player2.medir)
        l = os.popen("ls").read().split("\n")
        os.system("rm -r /home/revmedia/media")
        os.system("mkdir /home/revmedia/media")
        for k in l:
            f = file("/home/revmedia/playerlog.txt","a")
            f.write(os.popen("sudo cp \""+player2.medir + k + "\" /home/revmedia/media/").read())
            f.write(os.popen("sudo chmod -R 777 /home/revmedia/media").read())
            f.close()
        start = player("/home/revmedia/media")
        start.start()
config = file("/home/revmedia/Desktop/flashdriveplayer.config","r")
options = config.read()
options = options.split("\n")
mode = False
starting = False
if options[0].find("yes") != -1:
    mode = True

os.chdir("/media")
oldfolders = os.popen("ls").read().split("\n")
started = False
os.chdir("/home/revmedia/media")
t = None
x = 0
if os.popen("ls").read() != '':
    time.sleep(30)
    started = True
    t = player("/home/revmedia/media")
    t.start()
while True:
    os.chdir("/media")
    folders = os.popen("ls").read().split("\n")
    newfols = []
    if oldfolders != folders:
        for k in folders:
            found = False
            for kk in oldfolders:
                if k == kk:
                    found = True
            if found == False:
                newfols.append(k)
        for k in newfols:
            os.chdir("/media")
            print os.popen("pwd").read()
            os.chdir(k)
            fols = os.popen("ls").read().split("\n")
            found = False
            for kk in fols:
                if kk == "media":
                    found = True
            if found == True:
                di = "/media/" + k + "/" + "media/"
                if mode == False:
                    t = player(di)
                    t.start()
                    os.chdir("/media")
                    while(os.popen("ls").read().find(k) != -1):
                        time.sleep(3)
                    os.system("sudo pkill vlc")
                else:
                    if mode == True and started == False and starting == False:
                        started = True
                        wtl("****a\n")
                        print x*200
                        x += 1
                        t = player2(di)
                        t.start()
                        starting = True
                    elif mode == True and started == True and starting == False:
                        os.system("sudo pkill vlc")
                        wtl("******b\n")
                        print x*200
                        x += 1
                        t = player2(di)
                        t.start()
                        starting = True
    oldfolders = folders
    time.sleep(30)
    if (os.popen("ps -e").read().find("vlc") == -1 and started == True ) and starting == False:
        started = False
    if os.popen("ps -e").read().find(" cp\n") == -1:
        #wtl("no longer starting \n")
        starting = False

```

---

### Post by opensshd on 2012-09-12
I would try this:

[http://ubuntuforums.org/showthread.php?t=1846642](http://ubuntuforums.org/showthread.php?t=1846642) (Run command at device connection)

Then run a script that uses rsync to copy the files and vlc to execute them.

Is that kinda what you need?

---

### Post by Thomasmcdaniel on 2012-09-13
I think so the guy that was originally working on this had it working and tampered with it now its not working properly .I don't know a lot about coding  but ill give it a shot  it just needs to download the media to the hdd automatically and run in vlc  just by inserting the usb drive into the pc

---

### Post by opensshd on 2012-09-13
You can get usb vendor id by plugging in the device and running:

usb-devices

Then adding a udev rule in here: /etc/udev/rules.d/ (replacing your idvendor values for 0bb4, mode for whatever read/write permissions you want, group is the same on my machine)

SUBSYSTEM=="usb", ATTR{idVendor}=="0bb4", MODE="0666", GROUP="plugdev" RUN+="/path/to/executable/script.sh"

Then a bash script using rsync to copy the files, output of files copied to a tmp text file perhaps that vlc can read and use to enqueue copied files?

Lemme know if you need help with that script :)

You'll have to change the udev rule to work with various devices however...

---

### Post by Thomasmcdaniel on 2012-09-14
Im going to give it a shot but like i said i dont know crap about writing code 
What we have is a digital sign its a motherboard and hdd attached to a video board  if you could  shoot me something over i could just copy and paste into the bin and  see if that would work i dont really know a whole lot of people that do programming locally it would be great if i did but im sol on that 
But thanks for trying to help me ill keep trying what you told me to do but im having to do all types of searching on Google and im still lost
I forgot to mention were running 1920x1080 JPEG or pic so vlc needs to start in full screen mode always no audio

---

### Post by Vaphell on 2012-09-14
how about wrapping that code in [code][/co****de] tags? Python is sensitive to formatting.

---

### Post by mörgæs on 2012-09-14
Fixed that.

---

### Post by Thomasmcdaniel on 2012-09-14
No i need some code that will allow the media on my flash drive to automatically download the to  media folder on the hdd so i can pull out the flash drive and it continue to play the media that i put on the drive  also i use vlc player and it needs to stay in full screen mode at all times because these are advertising kiosk and they are going to continue to run all the time  all this needs to take place once i insert the flash drive into the usb port any suggestions

---

### Post by Thomasmcdaniel on 2012-09-14
The code worked until the guy that was working on it screwed around with it and tried to add all this extra stuff  and he is no longer with us  and i have no clue on where to start  if you could please help me out that would be great

---

