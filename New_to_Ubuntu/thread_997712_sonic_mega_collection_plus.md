---
title: "sonic mega collection plus"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by wubujum on 2008-11-30
well,
     I installed wine (v=1.0.0). I installed directx 9.0c, and dxdiag says everything to do with directx is nice (the fullscreen tests didn't work, but I was not missing any .dlls or anything).


     I would then presume that if I did not run a program in fullscreen, it would be okay.

     The problem: I try to open the executable (after successful installation), the disc drive starts humming nicely ( sonic mega collection disc spinning, idk  why it needs something off the disc, but that is irrelevant), and the a window opens, I can just slightly catch the SEGA logo, and the window closes. Same happens for fullscreen and windowed, with and without emulated desktop.

Could someone possibly give any comprehensive assistance with this?

---

### Post by bhadotia on 2008-11-30
> **wubujum said:**
> well,
     I installed wine (v=1.0.0). I installed directx 9.0c, and dxdiag says everything to do with directx is nice (the fullscreen tests didn't work, but I was not missing any .dlls or anything).


     I would then presume that if I did not run a program in fullscreen, it would be okay.

     The problem: I try to open the executable (after successful installation), the disc drive starts humming nicely ( sonic mega collection disc spinning, idk  why it needs something off the disc, but that is irrelevant), and the a window opens, I can just slightly catch the SEGA logo, and the window closes. Same happens for fullscreen and windowed, with and without emulated desktop.

Could someone possibly give any comprehensive assistance with this?

Just curious:
How did you install DX? I thought it requires validation from the ms website.
About the problem;
Sorry, but I'm not sure about that.

---

### Post by 3rdalbum on 2008-11-30
Checklist:

1. Turn off Compiz temporarily and try again.
2. Check the Wine HQ website to see if there are any special tricks needed to get this program running in Wine.
3. If nobody here can help further, and if the program is listed as unsupported on Wine HQ, and there are no HOWTOs online, then there's probably nothing you can do except try each new release of Wine.

---

### Post by bhadotia on 2008-11-30
> Permanent articles on A Man And His Penguin
 
Great link!

---

### Post by wubujum on 2008-11-30
> Turn off Compiz temporarily and try again
Thank you,3rdalbum, I haven't had any problems with compiz, but I will try that.

I have searched for any quick how tos, and have found none. This is probably because it is not the most popular game in the world.

The game supposedly worked in feisty, but that version doesn't even boot from the live cd on my laptop. It isn't marked either way for hardy (which is what I have installed).


> Just curious:
How did you install DX? I thought it requires validation from the ms website.


I didn't have to verify anything. I followed a guide (just google, they are fairly easy to find), and installed the redistributable package. I know that wine has it's own implementation, but I couldn't even find dxdiag.exe before I installed it. Pretty obvious clue that the current dx has some holes (missing dlls).

---

### Post by DOS4dinner on 2008-11-30
Installing DirectX does not usually work in Wine. The Wine FAQ States this. There are a couple of dlls that are useful, but the install probably did nothing, if not made it worse.

Try different compatibility modes, like XP, Vista, 2000, 98, etc. Sometimes if a program thinks it is running on 98, its installer will not use things that Wine can't handle. 

What's your graphics card, and do you know it is properly configured?

What error messages does it output to the terminal?

Upgrade to Wine 1.1.8 to see if that works. There is a guide for it in the Wine forum, where this question *should* be.

Lastly, is there a demo somewhere we could try?

---

### Post by wubujum on 2008-12-01
> Installing DirectX does not usually work in Wine. The Wine FAQ States this. There are a couple of dlls that are useful, but the install probably did nothing, if not made it worse.


I am aware that it would probably not do anything (or else it would have been included), but I had tried most of your other suggestions. It turned out to be neither beneficial or detrimental. The guide said to configure the dlls as native or built-in. I presumed this was to ensure that the dx installation didn't mess up wine configuration.

My graphics are properly configured because 2 other games are working in wine (peggle, and world of goo; both in hardware acceleration, windowed), not to mention compiz. Nvidia geforce M 7150

I haven't tried the terminal. will post later.

Sorry about not posting in the wine forum. I am an absolute beginner, and so I thought this would be the right forum.

Thank you all for your help so far.

---

