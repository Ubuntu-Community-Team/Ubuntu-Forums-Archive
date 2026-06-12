---
title: "Python: Bizarre Pet Tricks with XP."
date: 2010-06-08
forum: Programming Talk
---

### Post by McRat on 2010-06-08
I was teaching the kids programming tonight, and one of the examples had you:

print ("\a") 

in Python.

The Win XP sp3 machine (Dell 9300) actually rebooted instantly when asked to do that.  Repeatably.  It's a "beep" sound, or the system bell.

Exactly how is an application instantly rebooting the computer with a simple command?  How are you calling the BIOS reboot command?  Does that mean a Python script can access all the BIOS interrupts?  That's some bad juju.  You can bypass the O/S and read/write anywhere on the HDD with the BIOS interrupts.

IIRC, to reboot, you either need to call interrupt 25, or you need poke a very low memory area with 1234H.  Neither should be accessible by a user program.

It's probably nothing that sinister.

I also told it to print 100,000 lines of text as a kick for the kids, it took less than a second for Linux, but crashed the IDE under Windows with a memory allocation error.

Weird.

---

### Post by Bachstelze on 2010-06-08
It's probably a problem with your IDE because with a standard python distribution (installer from python.org), I don't experience this. Both [font=monospace]print("\a")[/font] and [font=monospace]for i in range(100000): print(i)[/font] behave as expected.

---

### Post by McRat on 2010-06-08
> **Bachstelze said:**
> It's probably a problem with your IDE because with a standard python distribution (installer from python.org), I don't experience this. Both [font=monospace]print("\a")[/font] and [font=monospace]for i in range(100000): print(i)[/font] behave as expected.


I should have been more clear.

The print ("\a") problem happened in normal terminal mode execution on XP Win machine, outside the IDE.  

The Memory Allocation error is from inside IDLE.

print ("This is a test of the emergency broadcast system.\n" *100000)

We did the \a test 3 times with identical results.  It might be a pecularity of that computer's BIOS.  The system bell is not a sound function really, it's BIOS.  

Well, it's certainly not a significant problem for us.  I might test to see if it happens in 2.6 or just in 3.1.


NOTE:  The 100000 print test crash OS X the first time it was ran, but worked the second time.  It appears to construct the string before sending it to the output device.

---

### Post by Axos on 2010-06-08
My hunch is it's a problem with the computer, not Python or its IDE. If you can compile a C or C++ program (not C#), try calling this function to see if it crashes the computer:

[http://msdn.microsoft.com/en-us/library/ms679277(v=VS.85).aspx](http://msdn.microsoft.com/en-us/library/ms679277(v=VS.85).aspx)

---

### Post by Bachstelze on 2010-06-08
> **McRat said:**
> 
NOTE:  The 100000 print test crash OS X the first time it was ran, but worked the second time.  It appears to construct the string before sending it to the output device.

Indeed. What you should do is

```
for i in range(100000):
    print("This is a test of the emergency broadcast system.")
```

---

### Post by McRat on 2010-06-08
> **Bachstelze said:**
> Indeed. What you should do is

```
for i in range(100000):
    print("This is a test of the emergency broadcast system.")
```

Loops are the NEXT chapter!  :)

I took the Linux machine up to 1,000,000 and it didn't flinch.

It didn't beep though, but that could be because the case I used doesn't have a speaker. :P


It's not a biggie, I think there is another computer floating around for her to use.  She thought she broke my computer.  This is the same computer that wore most the letters off the keyboard, not a collector's item.

---

### Post by McRat on 2010-06-08
> **Axos said:**
> My hunch is it's a problem with the computer, not Python or its IDE. If you can compile a C or C++ program (not C#), try calling this function to see if it crashes the computer:

[http://msdn.microsoft.com/en-us/library/ms679277(v=VS.85).aspx](http://msdn.microsoft.com/en-us/library/ms679277(v=VS.85).aspx)

I might give that a shot.

---

### Post by Tony Flury on 2010-06-08
> **McRat said:**
> 
The Memory Allocation error is from inside IDLE.

print ("This is a test of the emergency broadcast system.\n" *100000)


As you suspected the <string>*n is a list comprehension feature that builds a repeated string and it is evaluated before the result is passed as a parameter to the print function.
I think any function call like that would trouble the IDE - as you have to allocate the space for the entire 50 * 100,000 character string - that is 5 million characters, before calling the function.

---

### Post by trent.josephsen on 2010-06-08
> **Tony Flury said:**
> As you suspected the <string>*n is a list comprehension feature that builds a repeated string and it is evaluated before the result is passed as a parameter to the print function.
I think any function call like that would trouble the IDE - as you have to allocate the space for the entire 50 * 100,000 character string - that is 5 million characters, before calling the function.

5 million characters, even with space for overhead, is less than 5 MB (unless you're a hard drive manufacturer, in which case it's more).  I went up to 1600 MB on my 2 GB machine before it started swapping and saw no errors.  Nevertheless, if you were indeed out of memory, the Memory Allocation error class is what you should expect to see.

This sounds like a machine that is very bogged down -- possibly virus-ridden -- and has a few very serious bugs.  It's just waiting to be upgraded to Lucid ;)

---

### Post by wmcbrine on 2010-06-08
Strange indeed, but I wouldn't blame Python. IIRC, I once had a Windows system that reacted rather badly to the old-style system beep in a command window, though it didn't reboot -- it bogged down a bit, and the beep was very drawn out.

I'm not sure I've heard a true system beep since that time -- normally it maps to Windows' alert sound. This is something that happens on the console level, not the Python level.

---

### Post by McRat on 2010-06-08
> **wmcbrine said:**
> Strange indeed, but I wouldn't blame Python. IIRC, I once had a Windows system that reacted rather badly to the old-style system beep in a command window, though it didn't reboot -- it bogged down a bit, and the beep was very drawn out.

I'm not sure I've heard a true system beep since that time -- normally it maps to Windows' alert sound. This is something that happens on the console level, not the Python level.

The original beep was not put in for "sound", but back in the day when BIOS error reporting was very limited.  You would boot your system, and if something was wrong, it would beep out an error, like 5 beeps was a memory fault or something.

AFAIK, you are not allowed direct access to BIOS calls nowadays.  A rogue program could reformat the HDD with ease, you could alter anything you like in the kernel, or even physically damage a HDD by seeking into the end of the disc repeatedly at high speed.

Historical Trivia #2:

IIRC, we used to use BIOS write functions to make copy protection.  We would write a sector on a disk with an invoice number.  A normal copy routine would not copy this code since it wasn't in the directory.  IIRC, we wrote in an area that DOS functions could not access.  Seems we marked a sector as bad first, or lied about the # of tracks? Don't remember much more than that.

---

### Post by wmcbrine on 2010-06-08
> **McRat said:**
> The original beep was not put in for "sound", but back in the day when BIOS error reporting was very limited.Actually no. The original "PC squeaker" long predates dedicated sound cards, so it was used for all kinds of sounds in the olden days, although its capabilities were limited. BIOS error reporting was only the last leftover functionality it had after sound cards displaced the rest.

The PC speaker has nothing particularly to do with the BIOS, and the fact that an attempt to sound a beep crashed your computer does not indicate that anything BIOS-related is happening. (Damned if I know what *is* happening, though.)

---

### Post by McRat on 2010-06-08
> **wmcbrine said:**
> Actually no. The original "PC squeaker" long predates dedicated sound cards, so it was used for all kinds of sounds in the olden days, although its capabilities were limited. BIOS error reporting was only the last leftover functionality it had after sound cards displaced the rest.

The PC speaker has nothing particularly to do with the BIOS, and the fact that an attempt to sound a beep crashed your computer does not indicate that anything BIOS-related is happening. (Damned if I know what *is* happening, though.)

It's been awhile for sure.  But I seem to remember the beep was a BIOS call.  Before BASIC added the SOUND keyword, the only way to access it was from POKE statements or assembly language.

The instructions you got with a new PC/XT? told you what the beeps meant.  There wasn't a BIOS setting screen at first. One long beep was good?

And yes, you could add cheesy music to your games with it.  Sounded like a Pacman machines.  The Commodores and Ataris had good sound.

BUT I COULD BE WRONG.

---

### Post by lavinog on 2010-06-08
I recall something about windows xp doesn't provide a way to beep (to the pc speaker)
I had to get a 3rd party driver once to allow quickbasic to use the play function.

---

