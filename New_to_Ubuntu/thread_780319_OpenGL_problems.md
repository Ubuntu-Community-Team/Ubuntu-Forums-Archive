---
title: "OpenGL problems?"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by Djbb on 2008-05-03
Something in 8.04 has screwed up my OpenGL, because Urban Terror and WoW refuse to start. Here is my terminal output when trying to open Urban Terror.

ioQ3 1.35urt linux-i386 Dec 20 2007
----- FS_Startup -----
Going through search path...

----------------------
12228 files in pk3 files
execing default.cfg
execing q3config.cfg
execing autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) passed.
Initializing OpenGL display
...setting mode 4: 800 600
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Couldn't get a visual
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Couldn't get a visual
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem

---

### Post by Djbb on 2008-05-03
Nevermind I found the solution, I downloaded winXP

---

### Post by |{urse on 2008-05-03
Good job! Sadly all you needed to do was install xgl and configure x correctly. But that just takes too much thinking i suppose.

---

### Post by |{urse on 2008-05-03
> Section "Screen"
Identifier "Screen0"
Device "Videocard0"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection

Changing DefaultDepth to 24 probably would have fixed your problem just in case you try linux gaming again.

---

### Post by Djbb on 2008-05-03
> **|{urse said:**
> But that just takes too much thinking i suppose.

It does take too much thinking, actually. I've been with Ubuntu since 7.04, and Hardy is a P.O.S. I shouldn't have to configure 1000 different things when I upgrade. But hey, I just might stick around if you tell me why network-manager refuses to remember my WPA key, WicD tells me its unable to obtain an IP address, programs absolutely refuse to open (no, not a system freeze) and I have to manually power off my machine because even the terminal won't start.

Oh, and I love how I post 3 different threads with all of these bugs, and when I finally get a response in one of those threads, its because I hinted I might go back to Windows. When I find another bug, I might just put "WINDOWS ROCKS!!!" as the subject header, probably get 1000 responses.

---

### Post by |{urse on 2008-05-03
I bet you wish you hadn't spent all that money huh? Besides microsoft needs ppl to be all-consuming product loyalists so go, be with your microsoft, makers of windows me!

---

### Post by |{urse on 2008-05-03
and lots of smart people look up their hardware on hcl's before they upgrade. now whose fault is it?

---

### Post by PmDematagoda on 2008-05-03
> **Djbb said:**
> Oh, and I love how I post 3 different threads with all of these bugs, and when I finally get a response in one of those threads, its because I hinted I might go back to Windows. When I find another bug, I might just put "WINDOWS ROCKS!!!" as the subject header, probably get 1000 responses.

Don't lie Djbb, I have had a look at your threads and not in one thread did you hint about moving to Windows and in both of your threads(I had the liberty of counting), there was at least some sort of input. Personally, I just find it to be rather low for someone to get support here just because he/she threatens to go to Windows if that person's problems are not solved; you are using Ubuntu/Linux, so you are more than welcome to move to Windows if you can't handle Ubuntu any more.

Also I realise that the thread concerning the networking problems was put in one of the most unlikeliest sections imaginable which is the Absolute Beginner section, what about the section dedicated for these kinds of problems like the Networking and Wireless section? We don't have dedicated sections for nothing.

The decision is up to you, you can move to Windows as you are threatening to do so or you can try to solve your problems in the right way and try looking around. Also, why not a clean reinstall, I see that clean installs usually clean-up problems created by upgrades.

---

### Post by Djbb on 2008-05-03
> **PmDematagoda said:**
> 
Also I realise that the thread concerning the networking problems was put in one of the most unlikeliest sections imaginable which is the Absolute Beginner section, what about the section dedicated for these kinds of problems like the Networking and Wireless section? We don't have dedicated sections for nothing.

The decision is up to you, you can move to Windows as you are threatening to do so or you can try to solve your problems in the right way and try looking around. Also, why not a clean reinstall, I see that clean installs usually clean-up problems created by upgrades.

Alright, you're right, it was pretty low to mention a switch to windows, but 8.04 has been nothing but frustration after frustration for me. Also, I do search the forums before posting any sort of problem I have. Take for example the problem with network-manager. I'm not the first person to experience this problem, as evidenced here
[http://www.google.com/search?hl=en&q=network+manager+remember+wpa&btnG=Google+Search]("http://www.google.com/search?hl=en&q=network+manager+remember+wpa&btnG=Google+Search")

So obviously, problems with network-manager remembering WPA keys is not an individual case if its happening to other people, but I've yet to see the problem addressed because network-manager shipped with 7.10, it had the problems in 7.10 and it shipped again with 8.04 and it still has the problems in 8.04. The best solution I found on these forums for it was to use WicD instead of network-manager, which actually worked in 7.10, but not in 8.04

Or lets take the issue with Youtube videos framerates becoming extremely choppy after being set to fullscreen.
[http://www.google.com/search?hl=en&safe=off&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=ubuntu+youtube+fullscreen+frame+rate&spell=1]("http://www.google.com/search?hl=en&safe=off&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=ubuntu+youtube+fullscreen+frame+rate&spell=1")
Big problem in 7.10, still happening in 8.04. Searched the forums, can't find anything that fixes it.

Wanna hear something really funny? 7.04 was probably the most stable release I used, after I upgraded to 7.10 things just went downhill.

---

### Post by PmDematagoda on 2008-05-03
> **Djbb said:**
> Wanna hear something really funny? 7.04 was probably the most stable release I used, after I upgraded to 7.10 things just went downhill.

Hmm, I wonder why I didn't find that funny.

Now concerning Network Manager, that maybe something with Network Manager 0.6x which is found in both Hardy and Gutsy, from what I've seen, Network Manager 0.7 has received a complete rework and it's included in Fedora 9, so I suggest you download Fedora 9 and give it a whirl.

About the Flash issues, that is something you should blame on Adobe and not Ubuntu since the Ubuntu devs have no say whatsoever in Adobe Flash development. Did you give Gnash a try as well?

---

### Post by |{urse on 2008-05-03
just because you can't figure out wpa-supplicant and arent using the media player connectivity plugin for firefox (hint) doesn't mean hardy is at fault. I could list numerous improvements of hardy over feisty. Let's not even talk about vista compatibility issues, and then when a few of the showstopping bugs in vista get ironed out here comes win7 (more bugs) and you can no longer purchase xp in a year (fact, you wont be able to). I hate arguments like these because software will always be buggy because hardware keeps changing. It's inevitable. Wouldn't you rather be helping to pioneer a revolutionary os like linux or bsd instead of paying for a huge company to fix your problems then charge you more later as soon as you get in good?

---

### Post by Djbb on 2008-05-03
> **PmDematagoda said:**
> Hmm, I wonder why I didn't find that funny.

Now concerning Network Manager, that maybe something with Network Manager 0.6x which is found in both Hardy and Gutsy, from what I've seen, Network Manager 0.7 has received a complete rework and it's included in Fedora 9, so I suggest you download Fedora 9 and give it a whirl.

About the Flash issues, that is something you should blame on Adobe and not Ubuntu since the Ubuntu devs have no say whatsoever in Adobe Flash development. Did you give Gnash a try as well?

I wasn't trying to be a <bip>, I'm just saying that 7.04 ran flawlessly for me, 7.10 had a few small issues and 8.04 is making me want to throw my computer out the window.

I've never given Fedora a try, my linux experience has been limited to a brief run with Freespire and then Ubuntu.

About the Flash issues, well...screw Adobe then, lets code our own flash player.

---

### Post by Djbb on 2008-05-03
> **|{urse said:**
> just because you can't figure out wpa-supplicant and arent using the media player connectivity plugin for firefox (hint) doesn't mean hardy is at fault. I could list numerous improvements of hardy over feisty. Let's not even talk about vista compatibility issues, and then when a few of the showstopping bugs in vista get ironed out here comes win7 (more bugs) and you can no longer purchase xp in a year (fact, you wont be able to). I hate arguments like these because software will always be buggy because hardware keeps changing. It's inevitable. Wouldn't you rather be helping to pioneer a revolutionary os like linux or bsd instead of paying for a huge company to fix your problems then charge you more later as soon as you get in good?

Bro, Hardy is at fault if I can't figure out wpa-supplicant and the media player connectivity plugin for Firefox. I've never heard of wpa-supplicant, the Ubuntu manual didn't say "If you're experiencing problems with network-manager, try wpa-supplicant". What you're basically telling me is that Ubuntu provides the yogurt, but you'll have to find a spoon on your own. How is that even REMOTELY user-friendly? And stop implying I'd ever pay for anything Microsoft ever came out with, I gotz mad torrentz, yo.

I'm not trying to be a <bip> or start any arguments or troll or anything like that. I'm just asking why can't I click, click, click and boom my wireless is running flawlessly? I can do it in Windows, but I don't want to use Windows because Windows sucks. But if Ubuntu is trying to be better then Windows...basically it all boils down to, why do I have to go hunting through these forums looking for answers to problems that shouldn't be as difficult as they are.

I'd love to be a part of the Ubuntu revolution. But how am I supposed to tell my friends "Hey, you should really give Ubuntu a try, all you have to do is download and install it, then spend the next 5 hours roaming the forums for every little bug you come across".

---

### Post by |{urse on 2008-05-03
> And stop implying I'd ever pay for anything Microsoft ever came out with, I gotz mad torrentz, yo.


perhaps you should steal a computer from someone who knows how to install and configure hardy instead.

edit: lol @ free yogurt, go find a spoon. That should be linux's catchphrase.
edit: no actually it'd be free yougurt, free imperfect spoon, knowledge of how to eat required. =|

---

