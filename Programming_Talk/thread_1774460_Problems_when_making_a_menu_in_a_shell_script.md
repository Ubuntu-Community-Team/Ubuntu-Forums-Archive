---
title: "Problems when making a menu in a shell script"
date: 2011-06-03
forum: Programming Talk
---

### Post by alexpotter on 2011-06-03
Hello. 
I have recently run into problems creating a menu for my shell script that I am making. It is used to select how much RAM I want to allocate to my Minecraft Server (sorry if i posted it in the wrong place) and it uses Java 6. I think I created it properly, but when I type my choice in the Terminal quits. Any help please?

Here's my script.

```
cd /home/alex/Desktop/Minecraft/Server

echo "Welcome to the Minecraft Server launcher Script! Please enter 1,2,3,4,5 or 6 to select an amount of RAM to be allocated."
echo "--------------------------------------------------------------------------"
echo "Press 1 to allocate 1GB of RAM to the Server with a GUI."
echo "Press 2 to allocate 1.5GB of RAM to the Server with a GUI."
echo "Press 3 to allocate 2GB of RAM to the Server with a GUI."
echo "Press 4 to allocate 1GB of RAM to the Server without a GUI."
echo "Press 5 to allocate 1.5GB of RAM to the Server without a GUI."
echo "Press 6 to allocate 2GB of RAM to the Server without a GUI."

options=("1""2""3""4""5""6")
read choice 

case $choice in 
1)
echo "Starting Minecraft Server with 1GB of RAM."
java -Xms1024M -Xmx1024M -jar minecraft_server.jar
echo "Minecraft Server started with 1GB of RAM."
2)
echo "Starting Minecraft Server with 1.5GB of RAM"
java -Xms1536M -Xmx1536M -jar minecraft_server.jar
echo "Minecraft Server started with 1.5GB of RAM"
3)
echo "Starting Minecraft Server with 2GB of RAM"
java -Xms2048M -Xmx2048M -jar minecraft_server.jar
echo "Minecraft Server started with 2GB of RAM"
4)
echo "Starting Minecraft Server with 1GB of RAM - No GUI"
java -Xms1024M -Xmx1024M -jar minecraft_server.jar nogui
echo "Minecraft Server started with 1GB of RAM - No GUI"
5)
echo "Starting Minecraft Server with 1.5GB of RAM - No GUI"
java -Xms1536M -Xmx1536M -jar minecraft_server.jar nogui
echo "Minecraft Server started with 1.5GB of RAM - No GUI"
6)
echo "Starting Minecraft Server with 2GB of RAM - No GUI"
java -Xms2048M -Xmx2048M -jar minecraft_server.jar nogui
echo "Minecraft Server started with 2GB of RAM - No GUI"

*) 
echo "Please restart this script and press a number between 1 and 6.";;
esac
done

```

Is there anything I am doing wrong? Please help as I am new to bash and shell scripts.

Thanks in Advance,
Alex :popcorn:

---

### Post by slooksterpsv on 2011-06-03
Yes there's 1 problem:

case "$choice" in

not: case $choice in

---

### Post by alexpotter on 2011-06-03
> **slooksterpsv said:**
> Yes there's 1 problem:

case "$choice" in

not: case $choice in

Thanks for your reply. I changed it and it works so thanks  :)
 
Alex

---

