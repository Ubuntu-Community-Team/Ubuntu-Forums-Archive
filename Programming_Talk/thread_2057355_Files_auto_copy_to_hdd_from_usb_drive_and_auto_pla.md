---
title: "Files auto copy to hdd from usb drive and auto play in vlc"
date: 2012-09-13
forum: Programming Talk
---

### Post by Thomasmcdaniel on 2012-09-13
Can anyone help i need a program to automatically download files from flash drive to the hdd then auto play them in vlc media player  im using ubuntu 10.04 we had a guy right this program but he is no longer here the program was working but now its not and i have no idea how to write code  myself if anyone can help please feel free to contact me or tell me a way i can make this work 
We install a fresh copy of ubuntu the file name with the content is media  if this helps 


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

---

### Post by conradin on 2012-09-13
rsync?
I dont have time to actualy try it, but I think rysnc can do at least part of what you want. The other part could be having vlc play from a specific folder as its que. (I do that on a streaming audio server I setup.)

Are you playing something to begin with and want the new uploads to take presidence? If youre not running a server, Im still pretty sure vlc can take a que from a folder. So just sync the files to that folder and you should be good.

---

### Post by micahpage on 2012-09-13
put the code in code tags to save the indentation in python. Also what is the traceback that you get?

---

