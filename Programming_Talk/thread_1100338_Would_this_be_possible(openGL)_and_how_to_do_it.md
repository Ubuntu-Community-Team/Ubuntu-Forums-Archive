---
title: "Would this be possible(openGL) and how to do it"
date: 2009-03-19
forum: Programming Talk
---

### Post by tneva82 on 2009-03-19
So. Trying to get heightmap working. I store them in bunch of sectors with each sector containing only piece of the map. And at the same time there's only part of map pieces in memory(this way I don't have TONS of vertexes in memory. Saves memory when I don't have thousands of vertexes I don't need in memory).

Each sector is basicly self-contained in that vertexes are related to bottom-left corner of that vector.

Now I would need to draw sector the map is in. Only problem is that I'm drawing empty screen. Seems there's co-ordinates available based on printout I do while drawing. Small piece of that:

X: 112.000000 Y: 178.199997 Z: 92.000000
X: 116.000000 Y: 178.199997 Z: 88.000000
X: 116.000000 Y: 178.199997 Z: 92.000000
X: 120.000000 Y: 178.199997 Z: 88.000000
X: 120.000000 Y: 216.000000 Z: 92.000000
X: 124.000000 Y: 216.000000 Z: 88.000000
X: 124.000000 Y: 216.000000 Z: 92.000000

I'm trying to get this drawn in triangle strips as it seems to be fastest considering I have them in nice grid formation to begin with. Draw code is below. It generates above text piece(I removed the file writing text since that's not important. Just write down glVertex3f parameters into file).

```
glBindTexture( GL_TEXTURE_2D, blockTexture );
  glBegin(GL_TRIANGLE_STRIP);  

  for(int z=cutBottomY;z<=cutTopY;z++) {   
    glVertex3f(blockVertexes[cutLeftX+(z*heigth)].x, blockVertexes[cutLeftX+(z*heigth)].y, blockVertexes[cutLeftX+(z*heigth)].z);
     
    glVertex3f(blockVertexes[cutLeftX+((z-1)*heigth)].x, blockVertexes[cutLeftX+((z-1)*heigth)].y, blockVertexes[cutLeftX+((z-1)*heigth)].z);
    
    for (int x=cutLeftX+1;x<=cutRightX;x++) {    
      glVertex3f(blockVertexes[x+((z-1)*heigth)].x, blockVertexes[x+((z-1)*heigth)].y, blockVertexes[x+((z-1)*heigth)].z); 
      
      glVertex3f(blockVertexes[x+((z)*heigth)].x, blockVertexes[x+((z)*heigth)].y, blockVertexes[x+((z)*heigth)].z);   
      
    }
  } 
  glEnd();
```

I figure the issue is related to issue of positioning camera which I do like this(before I draw above):

```
    glRotatef(360.0f-cameraAngleX, 1.0f, 0.0f, 0.0f);
    glRotatef(360.0f-cameraAngleY, 0.0f, 1.0f, 0.0f);
    glRotatef(360.0f-cameraAngleZ, 0.0f, 0.0f, 1.0f);
    glTranslatef( -cameraX, -cameraY, -cameraZ );
```

Angles are 0 ATM. CameraX is 120, cameraY is 179 and cameraZ 5.

Obviously I have screwed somewhere big time :-/ Got this sort of thing working before with individual objects when I had everything in memory but now something's awry. Any pointers where I have gone horribly wrong?

Doesn't feel like it should be hard. What I would need is:

a) regardless of which individual block camera is that block is drawn at 0,0,0 position. Block has co-ordinates like this:

```
x: 0.000000 y: 185.399994 z: 0.000000
x: 4.000000 y: 185.399994 z: 0.000000
x: 8.000000 y: 185.399994 z: 0.000000
x: 12.000000 y: 185.399994 z: 0.000000
.
.
.
x: 252.000000 y: 185.399994 z: 0.000000
x: 0.000000 y: 185.399994 z: 4.000000
x: 4.000000 y: 185.399994 z: 4.000000
x: 8.000000 y: 185.399994 z: 4.000000
x: 12.000000 y: 185.399994 z: 4.000000
.
.
.
```

b) camera needs to be moved within X, Y and Z point within that block and rotated to look where camera is supposed to point.

c) then I need to drawn specific square out of the block(which I have calculated elsewhere) which should be be pretty much the area camera is viewing(plus bit more outside the sideview but nothing's perfect)

I think c) is working so I guess problem lies somewhere in a and b. Humhum.

---

### Post by Gordon Bennett on 2009-03-19
Let me get this straight - you have a large heightmap split into blocks (e.g. 100x100)?

---

### Post by tneva82 on 2009-03-20
> **Gordon Bennett said:**
> Let me get this straight - you have a large heightmap split into blocks (e.g. 100x100)?

That's the basic idea. I have it split it into smaller pieces. This a) makes it easier to texture it all(since one texture can't really cover it all unless I want repeating texture) and b) reduces memory usage when I don't have to store more than I really need.

Then I keep bunch of them in memory array. While moving I then drop blocks that get further than certain distance and load blocks that get within certain distance(load distance is shorter than drop distance. This way if I move one way and turn around and go back I don't drop what I just loaded. Prevents constant load-drop-load if camera moves back and forth between edges). This way atleast in world gets loaded and dropped without user really noticing the effect.

Atleast seemed like a really good solution how to make really big world without taking tons of memory or taking ages to load :D Plus side on client side map could in theory be virtually limitless length. 2 billion x 2 billion sectors each having openGL co-ordinates of float range x float range. Should be more than enough large for any map :D And if it works like I think it works only thing client requires for that is hard disk space(server OTOH which needs whole map would be begging for more memory probably :D. Then again if I would be designing this for huge enviroment I would be doing server to be multi-computer system where multiple servers each handle smaller piece of the world each).

The PROBLEM is getting that thing drawn :-/ I have now scrapped that idea for a while and am trying to get reqular heigthmap that is in one piece to be drawn(and without even limiting area I draw for extra simple feature. Takes more computer power but figured I try to get simplest form working before going further).

---

### Post by Gordon Bennett on 2009-03-20
You pretty much have it figured out :)

I suggest you start from a simpler perspective - have an array of cubes, say 10x10 and use them as a test for the view selection criteria.  One of the main headaches of tile-based map rendering is local versus absolute coordinate handling.

I should point out that there's a technique for sector-based map rendering which uses local coordinate systems. so for example:

[a][b][c][d]
[e][f][g][h]
[i][j][k][l]
[m][n][o][p]

Each of those units has its own local coordinate system (0 to 1023 for example).  This is sometimes referred to as 'zoning'.  With this method your map can be infinite in coordinate range, plus allows for very fast culling of objects outside of the zone (bitmask culling).
So basically you step into another 'world' per cell.  How do they join up?  Edge repetition :)

---

### Post by tneva82 on 2009-03-20
> **Gordon Bennett said:**
> You pretty much have it figured out :)

But how to get the camera move working? As said I tried it like that but all I got was empty screen. Obviously I somehow screwed up somewhere.

Also on related notes any suggestions how to get the texture of ground be bit more interesting? Simply laying up texture will result in one heck of a stretched out texture which results in blurry blops...Bigger textures aren't feasible due to size limits and the size of those sectors...

Should I have small repeating texture for ground? This way I could get more easily grass etc appearance. Then how to do roads? How to define that this area should be drawn with this repeating texture and this one with that :-/ I suppose some sort of blending is required.

(and now if I could figure out why my height map is giving such odd heights. Supposedly second lowest colour index multiplied by 0.3 and height is 10.xxx???)

---

### Post by Gordon Bennett on 2009-03-20
> **tneva82 said:**
> But how to get the camera move working? As said I tried it like that but all I got was empty screen. Obviously I somehow screwed up somewhere.

gluLookAt is your friend :)

> **tneva82 said:**
> Also on related notes any suggestions how to get the texture of ground be bit more interesting? Simply laying up texture will result in one heck of a stretched out texture which results in blurry blops...Bigger textures aren't feasible due to size limits and the size of those sectors...

Should I have small repeating texture for ground? This way I could get more easily grass etc appearance. Then how to do roads? How to define that this area should be drawn with this repeating texture and this one with that :-/ I suppose some sort of blending is required.

Small, repeated, tiled textures is the way to go, and you decal them on - modern GPUs support one-pass multitexturing to at least 4 levels and above.  As for defining what textures go where, that's where designing it in either a custom program or in apps like Blender comes in.

Grass is quite easy - you can use a function base to spam lots of cheap 2-D (or cardboard-cutout-style) template textures on selected regions.  The same goes for trees and other sundry objects.  Lots of games do it this way.

> **tneva82 said:**
> (and now if I could figure out why my height map is giving such odd heights. Supposedly second lowest colour index multiplied by 0.3 and height is 10.xxx???)

It might be rounding errors / conversion casting?  AFAIK double-precision floats for OpenGL vertices are being deprecated.

---

### Post by tneva82 on 2009-03-20
> **Gordon Bennett said:**
>  As for defining what textures go where, that's where designing it in either a custom program or in apps like Blender comes in.

Blender? Please tell me blender allows you to create heightmaps. Been struggling with CREATING those tripple darned heightmaps. Kolourpaint has been program I have been using so far but that sucks. Would be oh so much easier if I could design the area in blender in 3d-space and export it as heightmap.

> Grass is quite easy - you can use a function base to spam lots of cheap 2-D (or cardboard-cutout-style) template textures on selected regions.  The same goes for trees and other sundry objects.  Lots of games do it this way.

You wouldn't know any tutorials on this?

And I don't think rounding issues cause it. 10.xxx height with multiplier of 0.3 means the value is 30+. Since I'm trying to get second lowest index it should be 1...Ie height should be more like 0.3 and not 10.xxx...Hardly rounding issue!

---

### Post by crazyfuturamanoob on 2009-03-20
Here's a nice program for creating heightmaps: [http://hme.sourceforge.net/](http://hme.sourceforge.net/)

Last time I used it I had to compile it from source to get it working right.

---

### Post by tneva82 on 2009-03-20
> **crazyfuturamanoob said:**
> Here's a nice program for creating heightmaps: [http://hme.sourceforge.net/](http://hme.sourceforge.net/)

Last time I used it I had to compile it from source to get it working right.

Hum. Downloaded it, adjusted src so it's not defined to windows, compiled and tried to run. Segmentation fault. DARN!

---

### Post by crazyfuturamanoob on 2009-03-20
I digged up my ancient thread, instructions how to get it working: [http://ubuntuforums.org/showpost.php?p=4735548&postcount=12](http://ubuntuforums.org/showpost.php?p=4735548&postcount=12)

---

### Post by Gordon Bennett on 2009-03-20
> **tneva82 said:**
> Blender? Please tell me blender allows you to create heightmaps. Been struggling with CREATING those tripple darned heightmaps. Kolourpaint has been program I have been using so far but that sucks. Would be oh so much easier if I could design the area in blender in 3d-space and export it as heightmap.



You wouldn't know any tutorials on this?

And I don't think rounding issues cause it. 10.xxx height with multiplier of 0.3 means the value is 30+. Since I'm trying to get second lowest index it should be 1...Ie height should be more like 0.3 and not 10.xxx...Hardly rounding issue!

To add to the source already provided in this thread, this is from the excellent NeHe tutorials on heightmaps:
[http://nehe.gamedev.net/data/lessons/lesson.asp?lesson=34]("http://nehe.gamedev.net/data/lessons/lesson.asp?lesson=34")

As for the weird values - how are you programmatically obtaining the second lowest index?

---

### Post by tneva82 on 2009-03-21
> **Gordon Bennett said:**
> As for the weird values - how are you programmatically obtaining the second lowest index?

Well. I ASSUMED BMP stores index of palette in 256 colour bitmaps to pixel data. So I assumed that if I use 2nd colour of the palette I would be able to read index value 1 from the BMP pixel array.

Of course assumption could be totally wrong and the index values are more or less random and the fact colour I picked from custom palette was second has no bearing. In which case I'm screwed.

---

### Post by crazyfuturamanoob on 2009-03-21
You aren't using grayscale heightmaps are you? Grayscale images got only 255 colors, in one channel.

---

### Post by tneva82 on 2009-03-21
> **crazyfuturamanoob said:**
> You aren't using grayscale heightmaps are you? Grayscale images got only 255 colors, in one channel.

I have tried greyscale images, I have tried non-greyscale images with 256 colours. No luck. Might be me messing up with paint program though.

In anyway after giving this some thought I have decided to scrap the idea of using BMP to generate heightmap. I suck with 2d art(well I suck with 3d-art but from quick tests with blender I can create better terrain there than with BMP heightmaps), code gives me just problems, I would be limited to just 256 levels which aren't even freely defined but are in steps which in turn creates problems like how to make in short space shallow short raise or how to do sharp short raise in same space etc etc etc.

Instead: I'll do my own terrain editor where I can edit terrain WYSIWYG. I also am going to store height flat out. Will take more hard disk space but gives me more freedom. I also don't have to close the client, generate new raw file and start it again every time I want to make change. Why do things hard way when there's easier way?-)

For very basic terrain editor I have things pretty much mapped out. Just need bit of text parsing added(so I can save and load files for example, plus pick up vertex to edit. Later on I'll add in mouse selection. There's this handy selection mode in openGL which should do nicely for that. Hey I managed to get drag&drop working in GUI so why not vertex selection :D) and so on but overall shouldn't be tough job. Later on I can add more features to it like ability to place objects(trees, buildings etc) and spawn points. All in one toolkit therefore ;-)

After this back to figure out how to define the square I'm looking at(so I don't have to draw every single vertex including those behind me! I seem to be having bit of problems with this. I think either because I make logic error with the calculation(the fact 0 angle points forward rather than left is giving me some headaches :D) or because I haven't understood right how the openGL view area works).

After THAT I need to figure out good way to determine which object height should be. I have bad one done but that's too jumpy. Need one that changes height more smoothly.

Edit: Oh and speaking of GUI's. Quick check. I have vector filled with pointer(s). Supposed at some point all of the get .erase()'d(and more specifically first =NULL'ied. Deletion is done separatly elsewhere. I just want to get that pointer out of vector. Not delete the class pointed by vector). Now user does something that's supposed to go through vector like this:

for(vector<GUIObject*>::iterator it=objectList.begin();it!=objectList.end();it++) {}

Now what happens if vector size is 0? Does it STILL go through code within brackets once? Which would cause odd errors seeing as how there's not supposed to be any pointers to access etc.

Just wondering is that reason why it goes all segmentation faulty there. I could swear that if I would do if(int i=0;i<0;i++) it would never be performed but does the above vector loop work differently? Seems so since adding if(objectList.size()>0) before that stopped segmentation faults but just wondering was my reasoning as to why it works correct. Was rather annoying bug to figure out since I thought for a long time it would skip it if size is 0.

---

### Post by Gordon Bennett on 2009-03-22
There are some pretty cool 3D map editors out there - you'll be surprised at how much you could get out of them!  E.g. such programs as Valve's Hammer to design maps then parse the export file.

---

