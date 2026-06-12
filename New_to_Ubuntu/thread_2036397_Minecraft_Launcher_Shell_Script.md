---
title: "Minecraft Launcher Shell Script"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by eshnah4 on 2012-08-01
Hi, I'm trying to write a shell script that basically automates a check and launch of minecraft server files
so far I'm having a few issues with it


```
#!/bin/sh
#BINDIR=$(dirname "$(readlink -fn "$0")")
#cd "$BINDIR"
echo "Welcome to Eshnah's Minecraft Server Launcher"
#Check to see if Minecraft and CraftBukkit are in the folder and such
vanillaserver="minecraft_server.jar"
if [ -e -f -s "$vanillaserver" ]; then
    echo "Minecraft vanilla server is present"
else
    echo "WARNING:: The Minecraft vanilla server has not been detected in this folder"
    wget "https://s3.amazonaws.com/MinecraftDownload/launcher/minecraft_server.jar"
fi
craftbukkit="craftbukkit.jar"
if [ -e -f -s "$craftbukkit" ]; then
    echo "Craftbukkit server is present"
else
    echo -n "WARNING:: CraftBukkit has not been detected in this folder."
    wget "http://dl.bukkit.org/latest-rb/craftbukkit.jar"
fi
echo -n "Which server would you like to launch?
> Press 1 for Minecraft Vanilla
> Press 2 for CraftBukkit
> Press 0 to exit (I'll miss you!)"
read servertype
if [ "$servertype" == "0" ]
    then
    exit
fi
if [ "$servertype" == "1" ]
    then
    vim server.properties
    "java -Xmx3072 -Xms3072 -jar minecraft_server.jar &"
    exit
fi
if [ "$servertype" == "2" ]
    then
    vim server.properties
    "java -Xmx3072 -Xms3072 -jar minecraft_server.jar &"
fi

```1) I suppose I don't fully understand the grammatical rules behind the  "else" function because despite the fact that the vanilla server is  found within my directory, the wget still takes place
2) I would also like to use multiple if statements at once (meaning I'd like to have a conditional within a conditional) but that seems to give me a strange error concerning my placement of the "fi" operand

any help I could get would be appreciated very much

---

