---
title: "Need open source developers"
date: 2007-07-30
forum: Programming Talk
---

### Post by capturesteve on 2007-07-30
I am posting this message around places looking for open source developers for a game called Drace, so i thought i might post here also seeing as ubuntu is an open-source community. Well here it goes. The game of course runs on linux, well and windows.

**Brief description:**
The game is a car racing game to be similar to mario kart, but less childish. Similar to Jak X. It will have online play over the internet where individuals host their own game servers, probably supporting about 8-10 players. We also hope to have a single player championship mode, where the player progresses through increasingly harder races. While as progressing upgrades his vehicle with parts or buys a new vehicle all together. 

**Target aim:**
Freeware/Open Source
**Compensation:**
As we are a doing an open source project we will not be paying anything, except recognition in the game credits will be given.

**Technology:**
The game is written in c++. We are using Visual Studios express edition for windows development, and code::blocks for linux. Also here are some of the libraries we are using.
*Ogre3D :)
*Newton ( with OgreNewt wrapper)
*RakNet ( for udp programming) 
*LibCurl (for http stuff for communications with the master server which holds the list of servers)
The game will be cross-platform. 

**Talent needed:**
*Vehicle AI programmer: We need someone who can develop vehicle AI that can be injected into a vehicle via variable input( meaning say for steering the car a variable called steer then calling steer += 1.0f, or steer -=1.0f then for throttle: throttle = 2.0f or throttle = -2.0f, since the vehicle classes are all ready set up, and will handle the driving of the car.)
*Network Lag Destroyer: We currently have the game set up to use raknet and simply have the server send position updates to the clients, of cource this causes major jitter even on lan. We need some one expierenced with network programming in games to implement methods into the code, that will reduce jitter and make the game work currectly on network play. 
*3D/2D artist: We are looking for someone that can make graphics like vehicles and tracks and any other 3d graphics we will need. We are open to let the 3d artist have alot of say in the look and feel of the game, since none of us programmers know art. LOL. The artist needs to know his tools good enough to set up the proper exporters for Ogre3D, and simple supply the exported models.


**Website:**
Our website [here]("http://www.spocore.com")
Our [forums]("http://www.spocore.com/phpbb") which will play a major part in the development communications.
Our [sourceforge page]("https://sourceforge.net/projects/d-race")
Link to code [here]("http://d-race.svn.sourceforge.net/viewvc/d-race/")


**Contacts:**
A link to the forums are above.
My email is capturesteve with the good old @gmail.com ending. I hate spam, i hope you can put those 2 parts together. 

**Additional Info:**
Development Structure: Our aim with this project is to have a active community of developers(and later end gamers) that work and colaborate on the forums, (or discuss team matches, start in game clans, host racing turnaments through their own methods( so they would host a server and regulate themselves the turnament). Since our team will be small 3 or 4 programmers and 1 or 2 artists, we use the patching alot. If you look on the forums you will see we have set up a process for requesting patches under the recruitement section of our forums. 
ScreenShot: Here is a little screenshot of its current stage( it isn't much and the car is not our artwork, and the scene is just something i through togethor in blender)
[img]http://www.spocore.com/gallery2/main.php?g2_view=core.DownloadItem&g2_itemId=52&g2_serialNumber=1[/img]

If you are interested please email me from the contact information above, and i would also suggest that any one interested also sign up on our forums and post to say hi.

**Feedback:**
Give me anything you got, i'm ready! Feedback helps make things better :)

---

### Post by AlexThomson_NZ on 2007-07-30
Hey, it looks cool, I'll be keeping an eye on this.  Sorry, don't have enough time to contribute at the moment, but will keep you in mind.

I really like the way you presented this too, rather than the "I have an idea for a game- need someone to code it for me" type posts that pop up occasionally

---

### Post by capturesteve on 2007-07-30
Yeah, i had to present it good to comply with all the gamedev.net rules, then i just pretty much copied it here. I would suggest that any one presenting should follow the templates for the help wanted on gamedev.net they are good.

---

