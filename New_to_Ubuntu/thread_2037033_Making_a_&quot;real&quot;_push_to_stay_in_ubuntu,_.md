---
title: "Making a &quot;real&quot; push to stay in ubuntu, need help on Teamspeak"
date: 2012-08-03
forum: New to Ubuntu
---

### Post by Darkhaund on 2012-08-03
Hello guys:

For SEVERAL years I have tried my best to stay stable on ubuntu. I love it, for always for one reason or another i endup going back to windows. Either for certain apps that I use alot like Dreamweaver, or that I have been unable to setup tv video capture cards this or that.

This time, I HAVE a dedicated desktop at work that i will be using mostly libreoffice and "normal_" things thus I am confident that i will survive.

This time howerver I NEED HELP with Teamspeak 3. I have installed it but i dont know (and i dont like) where it was installed. 

So here are my questions

Wjhere should the Teamspeak insatalled folder be palced?
Shouyld there be an icon on my desktop or in my unity toolbar?

I have been using the program so i know it works, I just want to know if it is properly placed and installed. For example when i click on the dash button and i search for teamspeak, it gives me the executable (that once i click on it does NOT work) i have to click on the folder for it to open and then run the executable. This is bugging me

Thanks in advance.

DH

---

### Post by Elfy on 2012-08-03
Once you've got the thing actually working - right click on the icon in the launcher and you can lock it there.

---

### Post by Darkhaund on 2012-08-03
What about the results that the search in the dash home give me?

Why when I click on the executable it does nothing... i need to click on the folder for it to open and only then can I click on the executable file.

Also where should the teamspeak 3 folder be ? Can i drag it anywhere i want or should it be in a specific place....?

I want to have my ubuntu machine organized and not having programs installed here and there scattered in random places..

Thanks in advance

---

### Post by Darkhaund on 2012-08-09
Bump on this plz

any suggestions?

---

### Post by kostkon on 2012-08-10
Actually, it's more easy than you think. There is a very nice application in the software centre, named [*create-launcher*]("https://apps.ubuntu.com/cat/applications/create-launcher/"), which will allow you to create a launcher/dash entry for TeamSpeak. It is very useful when you have applications that you can't install using the software centre or with a deb file. After you create it, just search for Teamspeak in the dash and then drag it to the launcher, for example.

You'll need to supply a nice icon. Here are two I found ([1]("http://psykomong.deviantart.com/art/Teamspeak-dock-Icon-2-77175419") and [2]("http://3xhumed.deviantart.com/art/Teamspeak-Dock-Icon-165244707")), I actually like the first one. Just place the icon file inside the Teamspeak folder, no big deal.

You can place the Teamspeak folder anywhere in your home folder, it doesn't matter. If it bothers you that it's visible, you can hide it. To accomplish this, create in the folder where you have placed the Teamspeak folder a text file named *.hidden* and put inside its name. Afterwards, both the .hidden file and the Teamspeak folder will become hidden. A more fast approach would be to just put a dot (.) in the Teamspeak's folder name (e.g. *.teamspeak*) and that will instantly make it hidden. You can always make it appear by either selecting View &#8594; Show Hidden Files from Nautilu's menu or just pressing CTRL+H.

I have done the same thing for [KAG]("http://kag2d.com/") (btw, a very nice game, you should try it). I needed a good icon for it so I just downloaded its icon from some website (I couldn't find anywhere else, and it doesn't come with the game, neither appears as the window icon in Ubuntu). I scaled it to 256x256 (by default it is only 32x32 I think) without applying any interpolation to it because it has pixelised graphics. I also rounder its corners a bit. And here's the result, I have attached it below for anyone to use.

Hope that helps.

---

### Post by Darkhaund on 2012-08-10
Kostkon!!!

THANK YOU SO VERY MUCH! You nailed it my friend.
Thank you for the time and the excellent and detailed description

I think I got it working

I have some following questions if i may

This process creates a "file" or icon on a folder called applications. Do I leave my newly TS created "file" there?

When I add or try to install apps that are not found in the software centre, do i want to make a "programs or any other name" folder to have them all there?

---

