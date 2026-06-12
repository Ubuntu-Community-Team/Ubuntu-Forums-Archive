---
title: "Particle Engines - Way of the Future"
date: 2009-09-05
forum: Programming Talk
---

### Post by socool274 on 2009-09-05
I see great potential in particle engines. Each particle being a pixel in size (or bigger, if u wanted). Each particle having it's own physics. It enables pixel perfect collision, easy transformation. Mutilation (in games). It can calculate which particles to be freed from a group. Such as, if you threw a table at some wall, it would calculate at which places the table would break. It enables easy image transformation, and scaling. Even bitmaps could be rotated and transformed in a 3d world. I think particle engines will be the primary method of 3d games in the (not so near) future. I don't thing it will be near, because of the extremely high requirements to run. Each particle could use a half of a kilobyte in ram. Each particle requires various calculations, run every frame. Particle engines are extremely computer intensive, but with the power of computers increasing rapidly, I believe that particle engines are a very important thing to consider.

---

### Post by falconindy on 2009-09-06
Didn't your mother ever tell you that multiplying by a NULL isn't allowed?

---

### Post by socool274 on 2009-09-06
You are right! I really should change that.

---

### Post by socool274 on 2009-09-06
Neither of my parents program. lol

---

### Post by hessiess on 2009-09-06
3D created with pixel-size particles is called a Voxel engine. They were used becouse they can be rendered in software relitavly efficiently before polygon rendering hardware became common. Voxels arnt practical in todays computing environment as they will only work at a specific resolution, i.e. one per pixel, any lower than that and everything starts to look like its made of boxes, any higher and its just wasting resources. For a voxel based game to look sharp on the highly variable monitor resolutions avalaable today everything would have to have an extremely high voxel res and be downsampled on the fly, or when the application starts, which would eather be verry compute intensive or use an absoute tun of memory. The current polygon-based system works well because it can easely render at any resolution.

---

### Post by socool274 on 2009-09-06
But the polygon system does not work well with collision detection. Using the polygon system, the most used method of collision detection is with approximation. Everything in a particle engine, would be pixel perfect. When a screen resolution is change, polygon based systems still cannot draw with things smaller than pixels. The polygon system still consists of pixels. If your resolution is more than half the resolution capable on your computer, it will look fine. Even polygon based systems look ugly at really low level resolutions. It is still best (and most games have this already), to allow the user to change the resolution. I just think the gain of all of these things are far too great to be forever lost because of one programmers laziness. Sure, instead of having only two resolutions in your game, you may have to put in 5, or 6, but I say it's worth it. Also, I made a simple particle engine, with opengl. Each particle is one opengl quad. If the polygon based system can render anything smaller than pixels, then a particle engine can, too. Because of the ability to resize your particle. Essentially, each particle is a polygon itself.

---

### Post by CptPicard on 2009-09-06
Collision detection and such stuff should be handled prior to considering the rasterization step, so "pixels" are not a very useful concept there. How to do that with meshes is a well-understood problem IMO and there is no reason to start doing that with particle clouds...

---

### Post by socool274 on 2009-09-06
What if, say, in a game, you had a sword, and you slashed some wood block. The particle engine would calculate where the sword slashed, and create an exact break, where the sword slashed. Completely exact. I have never seen a demonstration of this, using meshes. I would be glad to see one, though. If you have an example of this, please, show, by all means. Also, particle engines would create an ease of use type of thing. If you had one mesh, and it had to be split, then you would have to create another mesh. It can get hard to keep track of.

---

### Post by CptPicard on 2009-09-06
I am really not sure how a particle engine is going to be of much use in that example compared to a physics/materials system that would understand how to break up stuff. Of course, you will create a new entity from the broken-off piece, but this is surely preferable to maintaining some a cloud of particles down to some kind of infinitesimal resolution and then maintaining the cohesion of that according to the material properties... that sort of down-to-the-molecule simulation won't be possible for a long long time...

---

### Post by socool274 on 2009-09-06
It might be a very long time until particle engines will be of use. But, if it is something that will be used a lot in the future, then it is something to look into now. Sometimes, it is surprising at how fast new technologies are made, but I have no doubt that making a small 3d game out of a particle engine will be possible soon. Maybe not big 3d games, such as half life, or world of warcraft, but small ones. If small ones are possible with this, then the size of games using this method will constantly increase. As of now, computers using a particle engine are only capable of running a somewhat small 2d game. It won't be long before 3d games can be made. I see great potential, mainly in the ease of use. I would think it should be easier to make a table that breaks in the exact spot it was hit, with a particle engine, instead of a 3d mesh. The boxiness of pixels being used is, in my opinion, not a problem, as it is easily fixed. If there was a library that created group automation, such as a read from a .obj file, then it would be even easier.

---

### Post by Lux Perpetua on 2009-09-06
> **socool274 said:**
> ...but I have no doubt that making a small 3d game out of a particle engine will be possible soon. Maybe not big 3d games, such as half life, or world of warcraft, but small ones.What do you have in mind?

---

### Post by soltanis on 2009-09-06
Recently I've researched alternate rendering techniques for 3D. It seems like in the future, real-time ray-tracing engines will become feasible as CPU hardware grows more cores. Voxel-based rendering (like you are describing it) could pretty easily be combined with ray-tracing to create pretty stunningly realistic renders (second only really to photon mapping, which is way far off for real-time rendering).

---

### Post by hessiess on 2009-09-06
> **socool274 said:**
> But the polygon system does not work well with collision detection. Using the polygon system, the most used method of collision detection is with approximation. Everything in a particle engine, would be pixel perfect.

polygons are vector based, which means that they can scale indefinitely by definition. Current raycasting basd colision detection algorithms are `pixel perfect' as far as can actually be desplayed on a modrn monitor. Even if you had an infinate resolution monitor, the human eye is only capable of resolving so much. (the word `resolution' actually refers to the distance at which two objects can be sean to be separate, `resolution' in terms of monitors actually refers to pixel count, and is relay the wrong word to refer to pixel count, `resolution' referring to DPI is a more correct usage of the word). 

What you seam to be describing is not collision detection anyway, but hard/soft body physics simulation.

> 
It is still best (and most games have this already), to allow the user to change the resolution. I just think the gain of all of these things are far too great to be forever lost because of one programmers laziness. Sure, instead of having only two resolutions in your game, you may have to put in 5, or 6, but I say it's worth it.


By definition, vector-based systems, including polygons, Bezier patches and NURBS surfaces are resolution independent, i.e. they can be rasterised at ANY resolution and still look sharp (unless you go to an extremely low res). Modern monitors are by the very nature of how thy work, only capable of displaying at there native resolution, if you feed them video at anything other than the native res it has to be scaled, The quality of the scalers in LCD monitors are highly variable, ranging from Nearest(which looks terrible) to cubic, which is better but more compute intensive. Because of this monitors should only be fead with video at the NATIVE resolution and nothing else. Then there is the issue of aspect ratio, which there is no good answer for, stretching looks garbage and letterboxing/pillerboxing waste screen space, but are the only viable option, unfortunately most wide-screen monitors stretch the display when fead with 4:3 source material. 

Making games resolution independent really isn't that difficult, take a look at the source code of Quad-ren for an example, qr_renderer handles res-independent rendering and its only about 300 lines, most of which is set up.

> 
...but I have no doubt that making a small 3d game out of a particle engine will be possible soon. Maybe not big 3d games, such as half life, or world of warcraft, but small ones.


Its already bean done, meny` early 3D games were voxal based for the reasons described in a earlier post, The Voxlap engine is an example of a Voxal based renderer [http://advsys.net/ken/voxlap.htm](http://advsys.net/ken/voxlap.htm).

---

### Post by socool274 on 2009-09-06
Voxal and polygon are equal in scaling capabilities. For raytracing, you have to know alot of calculus, trigonometry, and algebra 2. For voxal, to get a pixel perfect collision, you would just have to repeat rectangular collision detection. For those that don't know (incase there are people that don't know), rectangular collision consists of a couple if statements, and subtraction. Voxal and raytracing seems like an amazing idea. I support raytracing, but a huge part of voxal is ease of use, and light math (for the non mathematically skilled). By small games, I mean something like those flash 3d racing games. Very small, doesn't need hugely well made graphics, and is light on most other math.

---

### Post by hessiess on 2009-09-07
> would just have to repeat rectangular collision detection

Try implementing sliding collision which works where the two faces colliding are not perfectly horizontal or vertical, or even curved. Implementing this is NOT a matter of simply repeating box collision for each pixel, it requires reverse engineering a collision mesh around the collision area, and using that to calculate the deflection vector to push the colliding object out of the object its colliding with, Its easier to just use a separate vector collision mesh from the start.

---

### Post by nvteighen on 2009-09-07
What I actually don't get is what objective effect will this have on nowadays computers... Ok, maybe such a model could be great for something like Star Trek:TNG's "Holodeck", but not for a PC as we know them, because the images are already "filtered" by the screen and reduced to a pixel-map which is still recognizable by the user.

As a [thought experiment]("http://en.wikipedia.org/wiki/Thought_experiment"), this is a nice idea to direct our development towards to, but it seems overkill for our current situation.

---

