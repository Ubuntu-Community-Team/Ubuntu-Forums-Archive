---
title: "HowTo: Make Custom Shareable BoSwars Maps"
date: 2010-10-18
forum: Outdated Tutorials &amp; Tips
---

### Post by d3v1150m471c on 2010-10-18
1. Find or create a suitable png image for the map you'll be making. The image width and height in pixels will need to be divisible by 32 and the image must be 4096x4096 or smaller.

2. Save the image in boswars-data/patches or within a folder of that directory. IE I use:

~/.boswars-data/patches/custom/

I copied the boswar-data folder from /usr/share/games/boswars/ to my home folder as above so that I can use the editor featured in the game. I strongly suggest you do this as well if you find the editor isn't working post installation and then running boswars as 

```

boswars -d ~/.boswars-data

```3. Run boswars as mentioned above, navigate to the editor and create a new patch. Name the patch something unique. In the image field type
```

patches/yourimagefile.png

```or some variation of this to suit your needs.

for the size fields set the two values according to the height and width of the image divided by 32. IE: a 4096x2048 image will be 128x64 in the size fields. 

Edit the 1x1 sections to how you'd want the map to function, save, and exit. 

4. Return to the editor and create a new map. size the map to be the same as the size fields you chose for the patch. as above it would be 128x64. save your map by pressing F11 and save the map as a .map file.

5. After you've created and saved your map go ahead and exit BoS wars. Go into your home folder and opt to view hidden folders. Nautilus users simply press Ctrl-H and Dolphin users may use Alt-H. Go into the .boswars/patches folder and you'll see a file titled user-whatyounamedyourpatch.lua. Copy that file and place it inside boswars-data/maps/yournewmap.map and rename it as patch.lua .

6. Go into your boswars-data folder and make a copy of that png image you originally placed in there in step 2. Save the copy also in the new map's folder like above.

7. Using a text editor open up the new patch.lua file you copied to the map's folder. You'll only need to edit the first line. It will look like this to work properly:
```

patchType("themapname.map", GetCurrentLuaPath() .. "/yourcustomimage.png", 64, 64, {

```please note the two numbers in the string above are the map dimensions so they may vary based on your map's size.

8. Open up the setup.sms file with your text editor and scroll down to where you get to the patches section of the code. You're going to add a line above the "patch( " line like so:
```

-- patches
Load(GetCurrentLuaPath() .. "/patch.lua")
patch("yournewmap.map", 0, 0)

```your patches section of the code should look identical to this now. save the new file.

9. launch boswars and enjoy your new map :). If you want to share this file for some cool lan gaming send your friend(s) the .map file you custom built and have them save it in the maps folder of their boswars-data. 
[U][COLOR=Red][B]
[Here's an example map I created you can reference]("http://www.mediafire.com/file/s6sbqp2rg80pc50/Twist96.map.tar.gz")

[/B][/COLOR][/U][COLOR=Red][COLOR=Black]==============================================
Also,

After following these instructions, if boswars is saying network out of sync during multiplayer games, chances are you did this wrong. If the maps are not identical among you and the players then it will also give a network out of sync error.
[/COLOR][/COLOR]

---

