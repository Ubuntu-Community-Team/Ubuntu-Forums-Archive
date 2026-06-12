---
title: "I need something like pdcurses to display all 256 chars"
date: 2008-11-14
forum: Programming Talk
---

### Post by VinnyBoombatz on 2008-11-14
I'm trying to write a program in C or C++. I need something like pdcurses which I use in MS Windows to display all 256 characters. ncurses does not have any raw functions as in pdcurses like mvaddrawch(), and does not let you display control characters. Well it does, but it sticks a carat plus a letter to represent them. Does anybody know of anything that will let me print all ascii characters to the screen in a console program?

Thanks
:guitar:

---

### Post by Tony Flury on 2008-11-14
The point about the control characters in ASCII is that they don't actually have a visible representation.

I know in MS WIndows that some of the ctrl sequences print fancy graphics, but those graphics do not exist in Unix which uses the ASCII standard.

Instead the Control characters have actual meanings, many of the related to prinetrs and print terminals - if you read the ASCII definitions (for instance Ascii 10 is carriage return and Ascii 12 is newline - i think that is the right way round).

what the caret-Letter sequence means is that that control character can be generated on the keyboard by pressing Ctrl and the same letter.

---

### Post by VinnyBoombatz on 2008-11-14
I appreciate you trying, but that was not helpful.

BTW. Ascii 13 is a Carriage return, Ascii 10 is a Linefeed.

---

### Post by Tony Flury on 2008-11-14
I was telling you the truth, the characters you are trying to print have no standard visible representation apart from ^A, ^B etc. 

I did try to be helpful, and to my mind being told that something will not work can be very helpful, as it prevents further wasted time.

ty for the heads up on CR & LF - i deliberately never remember the minutae like that - i know how leaky my memory is.

---

### Post by VinnyBoombatz on 2008-11-15
I think I've got it. I'm looking into SVGAlib. It has functions that allow access to video memory, and it looks like you can write anything to the screen. 

The reason I wanted this was because a guy I used to work with wrote this fantastic binary file viewer in Dos MS Basic 4.5. Unlike the unix binary file viewers, it showed each of the 256 characters in the PC ROM. I started re-writing it in C on the pc using Dev-Cpp. Then I wanted to bring it over to linux, and could not find a way to get the control characters to print, so I kind of stopped.

On a side note, you can open a text mode window manually. It's similar to the DOS full screen text window by pressing ctl-alt-f1(or f2-f6).

---

### Post by wmcbrine on 2008-11-16
A couple possibilities...

1. Look for Unicode equivalents, and use those instead.

2. PDCurses is also available in Linux -- X11 and SDL ports. The SDL port even uses a PC-like font (i.e. the same character mappings).

---

### Post by VinnyBoombatz on 2008-11-18
> **wmcbrine said:**
> A couple possibilities...

1. Look for Unicode equivalents, and use those instead.

2. PDCurses is also available in Linux -- X11 and SDL ports. The SDL port even uses a PC-like font (i.e. the same character mappings).

I checked out the SVGA lib, and it will definitely work, but I'm afraid it's going to flicker alot when scrolling down through records. Because it's essentially displaying the text as graphics.
The PDCurses function mvaddrawch(), and all the other "raw" functions are the functions I need, and they are not ported to linux.  It specifically says in the PC documentation that PDCurses raw functions are not portable. However, I'll check out the X11 and SDL ports. I'll check out unicode too. 
Thanks.
Vinny

---

### Post by wmcbrine on 2008-11-19
Not portable to other implementations of curses (like ncurses), is what that means.

I'm the PDCurses maintainer, listen to me. :)

---

### Post by VinnyBoombatz on 2008-11-21
> **wmcbrine said:**
> Not portable to other implementations of curses (like ncurses), is what that means.

I'm the PDCurses maintainer, listen to me. :)

Cool. How'd you get that job?

I just found out that you could write directly to any of the video consoles via /dev/vcs or /dev/vcsa devices. It looks like that's the easiest way to go, and a lot faster than the vgalib route.

---

### Post by wmcbrine on 2008-11-22
> **VinnyBoombatz said:**
> It looks like that's the easiest way to go,I seriously doubt it.

---

### Post by VinnyBoombatz on 2008-11-24
> **wmcbrine said:**
> I seriously doubt it.

Really? How so?

---

