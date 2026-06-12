---
title: "launcher icon size does not reduce"
date: 2012-05-19
forum: New to Ubuntu
---

### Post by Yash Pal on 2012-05-19
After changing from 11.10 to 12.04, I find that the size of icons in launcher is at the maximum, even after reducing the size in compiz configuration settings manager > ubuntu unity plugin > experimental > launcher icon size, to 32 (the lowest).

In 11.10 it was set at 32 and was 32.

Is there any other way to reduce the launcher  icon size in 12.04?

---

### Post by MG&amp;TL on 2012-05-19
...no, it's the same proccess as far as I know.

Are you sure you're not logged in to unity 2D? Post output of:

```
echo $DESKTOP_SESSION
```

so we can tell. 3D may fallback to 2D if there is something wrong.

---

### Post by mvs1207 on 2012-05-19
Try "System Settings" --> Appearance --> Launcher Icon Size...

---

### Post by HunterDX77M on 2012-05-19
I watched a Review of 12.04 on YouTube a few weeks back and they mentioned an application called MyUnity that was available in the software center after installing 12.04. Look that up and try it. The video said it provided options for customizing the launcher. Good luck and hope that helps.

---

### Post by Yash Pal on 2012-05-20
Regarding MG&TL's query, the output is "Unity 2D"
 

 VMUKKAMALA's suggestion is not workable as under System settings> Appearance, neither 'look', nor 'behaviour' have any provision for 'launcher icon size'.
 

 I will look for the video on You tube, as suggested by 'HunterDX77M'
 

 Thanks for all the suggestions and help.

---

### Post by HunterDX77M on 2012-05-20
> **Yash Pal said:**
> I will look for the video on You tube, as suggested by 'HunterDX77M'

There link for the video is:

[http://www.youtube.com/watch?v=5-_yaPof1Vs]("http://www.youtube.com/watch?v=5-_yaPof1Vs")

The part that I was talking about begins at 36:10.

---

### Post by MG&amp;TL on 2012-05-20
> **Yash Pal said:**
> Regarding MG&TL's query, the output is "Unity 2D"


Uh-oh. Congratulations, 3D is broken! :P

Output of:

```
/usr/lib/nux/unity_support_test -p
```
 from a terminal please, so we can debug the problem.

Unless, of course, you like 2d. But you won't be able to change the icon size without some hackery.

---

### Post by vasa1 on 2012-05-20
> **MG&TL said:**
> ...
Unless, of course, you like 2d. But you won't be able to change the icon size without **some hackery**.
And that is described here: [http://ubuntuforums.org/showthread.php?t=1943423](http://ubuntuforums.org/showthread.php?t=1943423)

---

### Post by philinux on 2012-05-20
> **Yash Pal said:**
> After changing from 11.10 to 12.04, I find that the size of icons in launcher is at the maximum, even after reducing the size in compiz configuration settings manager > ubuntu unity plugin > experimental > launcher icon size, to 32 (the lowest).

In 11.10 it was set at 32 and was 32.

Is there any other way to reduce the launcher  icon size in 12.04?
Obviously you could run unity 3d before the upgrade.
From a terminal

unity --reset & exit

---

### Post by Dave_in_MD on 2012-05-20
Hunter,  I was in 2D and could not reduce the icon size.  A member in another thread pointed me in the direction that the Nvidia drivers could be the issue.  I disabled both Nivdia driver and after reboot had 3D and my icons are now a comfortable 34.  I also have the CUBE.  The Live CD functioned for icon size which told me the hardware would handle it.

---

### Post by Yash Pal on 2012-05-20
1.a MG&TL
                                   
 Output of:
  Code:
/usr/lib/nux/unity_support_test -p                          
yashpal@yashpal-Inspiron-M5010:~$ /usr/lib/nux/unity_support_test -p  
 OpenGL vendor string:   ATI Technologies Inc.  
 OpenGL renderer string: ATI Mobility Radeon HD 4650  
 OpenGL version string:  3.3.11627 Compatibility Profile Context  
 

 Not software rendered:    yes  
 Not blacklisted:          yes  
 GLX fbconfig:             yes  
 GLX texture from pixmap:  yes  
 GL npot or rect textures: yes  
 GL vertex program:        yes  
 GL fragment program:      yes  
 GL vertex buffer object:  yes  
 GL framebuffer object:    yes  
 GL version is 1.4+:       yes  
 

 Unity 3D supported:       yes  
 yashpal@yashpal-Inspiron-M5010:~$  
  

1.b I also went through the video on you tube [http://www.youtube.com/watch?v=5-_yaPof1Vs](http://www.youtube.com/watch?v=5-_yaPof1Vs) ( thanks for giving the location of topic -elapsed timewise - which is of my interest ), installed 'MyUnity' from software centre and it tells me that I am in unity 2D and most of adjustments are disabled. They were greyed out.

                                
 2.  As Suggested by [COLOR=Black]**philinux,** I ran the command:[/COLOR]  
  unity --reset & exit
in the terminal. There was no effect even after restarting the machine.

3. vasa1 has suggested some hacking; I went through the literature. I am not capable of doing it. 
I would rather live with big launcher icons till the problem is fixed by the Ubuntu team than risk crashing or worse with my limited knowledge (Hindi/Urdu knowing people will recognise- Neem Hakim Khatra -e -jaan)

Thanks for all the help

---

### Post by MG&amp;TL on 2012-05-20
Have you selected Ubuntu, not Ubuntu2d, from the login screen? Click the ubuntu icon next to your name.

If yes, what happens if you run:

```
unity --replace
```

(this is temporary, not going to break your system).

---

### Post by Yash Pal on 2012-05-21
1. I had posted reply to 'MG&TL' query about output of  * /usr/lib/nux/unity_support_test -p*
I do not know how it was not posted. Any way, the output is:
  
  [COLOR=Blue]yashpal@yashpal-Inspiron-M5010:~$ /usr/lib/nux/unity_support_test -p  [/COLOR]
 [COLOR=Blue]OpenGL vendor string:   ATI Technologies Inc.  [/COLOR]
 [COLOR=Blue]OpenGL renderer string: ATI Mobility Radeon HD 4650  [/COLOR]
 [COLOR=Blue]OpenGL version string:  3.3.11627 Compatibility Profile Context  [/COLOR]
 [COLOR=Blue]
[/COLOR] 
 [COLOR=Blue]Not software rendered:    yes  [/COLOR]
 [COLOR=Blue]Not blacklisted:          yes  [/COLOR]
 [COLOR=Blue]GLX fbconfig:             yes  [/COLOR]
 [COLOR=Blue]GLX texture from pixmap:  yes  [/COLOR]
 [COLOR=Blue]GL npot or rect textures: yes  [/COLOR]
 [COLOR=Blue]GL vertex program:        yes  [/COLOR]
 [COLOR=Blue]GL fragment program:      yes  [/COLOR]
 [COLOR=Blue]GL vertex buffer object:  yes  [/COLOR]
 [COLOR=Blue]GL framebuffer object:    yes  [/COLOR]
 [COLOR=Blue]GL version is 1.4+:       yes  [/COLOR]
 [COLOR=Blue]
[/COLOR] 
 [COLOR=Blue]Unity 3D supported:       yes  [/COLOR]
 [COLOR=Blue]yashpal@yashpal-Inspiron-M5010:~$ 
[/COLOR]


[COLOR=Blue][COLOR=Black]2. I also ran  '[/COLOR][/COLOR]*unity --reset & exit*' in the terminal as suggested by 'philinux' with  no result.

3. I am incapable of making changes in the file as suggested by vasa1.

Any other help will be welcome.


 [COLOR=Blue]
[/COLOR]

---

### Post by MG&amp;TL on 2012-05-21
Have you tried my suggestion two posts up yet?

---

### Post by Yash Pal on 2012-05-21
[COLOR=#000000]MG&TD, I am really sorry that I reposted without seeing your suggestion.[/COLOR]
 

 [COLOR=#000000]I clicked the ubuntu logo near my name in the start up screen.[/COLOR]
 

 [COLOR=#000000]It showed Ubuntu enclosed in a rectangle with rounded edges and Ubuntu 2D below it.[/COLOR]
 

 [COLOR=#000000]Result of running [/COLOR][COLOR=#0000ff]unity –replace[/COLOR]:
 

 [COLOR=#0000ff]yashpal@yashpal-Inspiron-M5010:~$ unity --replace [/COLOR]
 [COLOR=#0000ff]unity-panel-service: no process found [/COLOR]
 [COLOR=#0000ff]Checking if settings need to be migrated ...no [/COLOR]
 [COLOR=#0000ff]Checking if internal files need to be migrated ...no [/COLOR]
 [COLOR=#0000ff]Backend     : gconf [/COLOR]
 [COLOR=#0000ff]Integration : true [/COLOR]
 [COLOR=#0000ff]Profile     : unity [/COLOR]
 [COLOR=#0000ff]Adding plugins [/COLOR]
 [COLOR=#0000ff]Initializing core options...done [/COLOR]
 [COLOR=#0000ff]Initializing composite options...done [/COLOR]
 [COLOR=#0000ff]Initializing opengl options...done [/COLOR]
 [COLOR=#0000ff]Initializing decor options...done [/COLOR]
 [COLOR=#0000ff]Initializing vpswitch options...done [/COLOR]
 [COLOR=#0000ff]Initializing snap options...done [/COLOR]
 [COLOR=#0000ff]Initializing mousepoll options...done [/COLOR]
 [COLOR=#0000ff]Initializing resize options...done [/COLOR]
 [COLOR=#0000ff]Initializing place options...done [/COLOR]
 [COLOR=#0000ff]Initializing move options...done [/COLOR]
 [COLOR=#0000ff]Initializing wall options...done [/COLOR]
 [COLOR=#0000ff]Initializing grid options...done [/COLOR]
 [COLOR=#0000ff]Initializing session options...done [/COLOR]
 [COLOR=#0000ff]Initializing gnomecompat options...done [/COLOR]
 [COLOR=#0000ff]Initializing animation options...done [/COLOR]
 [COLOR=#0000ff]Initializing fade options...done [/COLOR]
 [COLOR=#0000ff]Initializing unitymtgrabhandles options...done [/COLOR]
 [COLOR=#0000ff]Initializing workarounds options...done [/COLOR]
 [COLOR=#0000ff]Initializing scale options...done [/COLOR]
 [COLOR=#0000ff]compiz (expo) - Warn: failed to bind image to texture [/COLOR]
 [COLOR=#0000ff]Initializing expo options...done [/COLOR]
 [COLOR=#0000ff]Initializing ezoom options...done [/COLOR]
 

 [COLOR=#000000]After this, there were about 4 pages listing errors and warnings, which I did not copy. However, I can run it again and send you the complete message (whatever is printed on screen) besides whatever I copied.[/COLOR]

---

### Post by MG&amp;TL on 2012-05-21
No problem at all, sorry I sounded a bit grumpy. :)

Try making sure you select 'Ubuntu' from the login screen.

That would be helpful, although I don't know if it'll be something we can fix. :)

---

### Post by Yash Pal on 2012-05-21
MG&TL, I am happy to report that the launcher icon size can now be reduced.
A little while back, compiz crashed and the software asked if a report is to be sent, which was sent.
I ran compiz after this and adjusted the launcher icon size to 32 (it showed 48) and  the wall against which I had been breaking my head crashed ie, icon size shrank to 32.
Many thanks for the guidance.

---

### Post by MG&amp;TL on 2012-05-21
> **Yash Pal said:**
> MG&TL, I am happy to report that the launcher icon size can now be reduced.
A little while back, compiz crashed and the software asked if a report is to be sent, which was sent.
I ran compiz after this and adjusted the launcher icon size to 32 (it showed 48) and  the wall against which I had been breaking my head crashed ie, icon size shrank to 32.
Many thanks for the guidance.

Not a problem, glad to gt it working. :)

---

### Post by codingman on 2012-05-21
Set this as solved!

sorry if I jumped out of nowhere, but I tend to look a lot at the top post of each forum :P

---

### Post by Yash Pal on 2012-05-22
Thanks 'codingman'. Jumping in for the overall good of the community will be welcome by all.

---

### Post by cscomp3 on 2012-07-13
I am having the same problem.

Here's my output of "/usr/lib/nux/unity_support_test -p"



OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 865G x86/MMX/SSE2
OpenGL version string:  1.3 Mesa 8.0.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       no

Unity 3D supported:       no



I guess that last line tells the tale.  I am O.K. with this if it can't be overcome.

Unless someone knows how I can overcome it?

Thanks.  cscomp3

---

