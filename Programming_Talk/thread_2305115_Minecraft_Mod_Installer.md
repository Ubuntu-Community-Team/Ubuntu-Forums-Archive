---
title: "Minecraft Mod Installer"
date: 2015-12-02
forum: Programming Talk
---

### Post by scoutchorton on 2015-12-02
Hello world!

I was developing a VERY simple Python script to install mods for myself. I have a folder in my downloads to keep them separate, then I copy them to my mods folder in Minecraft. Here is the code:

```
from os import system, listdir
system("clear")
download = "/home/scoutchorton/Downloads"
d = listdir(download)
for i in d:
    if i == "Minecraft.jar":
        print "Skipping Minecraft..."
    elif i[-4:] == ".jar":
        print i
        o = raw_input("Move and copy file?\n  y/n  -> ")
        if o.lower() == "y" or o.lower() == "yes":
            system("mv "+download+"/"+i+" "+download+"/Mods")
            system("cp "+download+"/Mods/"+i+" /home/scoutchorton/.minecraft/profiles/1.7.10Forge/mods/")
        else:
            print "Skipped..."
print "Complete. Thank you and enjoy your lovely day!"

```

If anyone thinks I could make this progam more simpiler or add on to it, that would be great. This is just a program for me to use, but if someone wanted to expand on it and make something better, go ahead. I never plan on really distributing this much.

Good luck! :D

---

