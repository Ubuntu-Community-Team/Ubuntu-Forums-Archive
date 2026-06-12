---
title: "Pcsx"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by bladerunner060 on 2008-05-12
Okay, I'm posting this in absolute beginner talk because I'm sure I'm just being a noob.  I know almost NOTHIGN about linux still, except what the GUI does for me...and I can't for the life of me get PCSX to work.  I own a playstation and i own the game Silent Hill, which was the main reason I wanted the emulator, to play this game.  I put the game in, I start up PCSX, the bios is in the appropriate folder, as far as I can tell everything's set up right, When i try to run a game, or just run the emulator at all, I get the following if i put it through a terminal, nothing it I don't, it just closes.  

user@user-laptop:~$ pcsx

Checking plugin_is_available - libDFXVideo.so

Checking plugin_is_available - libDFSound.so

Checking plugin_is_available - libDFCdrom.so

Checking plugin_is_available - libDFInput.so

Checking plugin_is_available - libDFInput.so

Loading memory card /home/user/.pcsx/memcards/card1.mcr

Loading memory card /home/user/.pcsx/memcards/card2.mcr

Checking plugin_is_available - libDFXVideo.so

Checking plugin_is_available - libDFSound.so

Checking plugin_is_available - libDFCdrom.so

Checking plugin_is_available - libDFInput.so

Checking plugin_is_available - libDFInput.so

The program '<unknown>' received an X Window System error.

This probably reflects a bug in the program.

The error was 'BadMatch (invalid parameter attributes)'.

  (Details: serial 11 error_code 8 request_code 141 minor_code 14)

  (Note to programmers: normally, X errors are reported asynchronously;

   that is, you will receive the error a while after causing it.

   To debug your program, run it with the --sync command line

   option to change this behavior. You can then get a meaningful

   backtrace from your debugger if you break on the gdk_x_error() function.)

user@user-laptop:~$ 


the only thing I changed in that was my user name to 'user'.  

I had originally installed a joystick calibration program because I have a USB controller (the Logitech Dual Pro) that i want to use, but I read somewhere that might cause a problem, so I just uninstalled it and it seemed to have no effect, which was when I gave up and came here.  i've tried uninstalling and reinstalling, epsxe booted the game but no sound and couldn't let me use my controller and wasn't in the application list (had to be started manually) so I didn't like it.  

So, the goal here is a nice, simple, hardy heron walkthrough for setting up the emulator.  For people who know nada.  That, or someone to point out the I'm sure small and stupid thing I did wrong.  Thanks!


Oh, and i did notice there are many many threads on emulators elsewhere on the forums, but they either dont' help me or are a bit over my head.  What's sad is that i know windows pretty well...I'm like an american in a foreign country in Linux, just trying to shout at the thing and maybe then it will understand me.  


I'm running ubuntu 8.04 on an old Compaq Presario V5000, mobile AMD Sempron processor, 1 gb ram.

---

