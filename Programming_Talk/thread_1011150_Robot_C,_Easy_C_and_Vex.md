---
title: "Robot C, Easy C and Vex"
date: 2008-12-14
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-12-14
I just recently started robotics with Vex, but I hate using Easy C. And for the Vex compotitions, Vex releases Easy C templates you must follow for the compatition. Robot C is an alternative for Easy C, but it is a windows program and compiler.

If I wanted to write a compiler and loader onto the Vex robot for linux, what would I need to get from Vex and/or have Vex change in their design.

This is just an idea, and it requires cooperation from Vex and Robot C companies

---

### Post by jimi_hendrix on 2008-12-14
wow vex...great kit...to bad i dont know enough to do anything with it...

---

### Post by daltore on 2009-07-06
I've been working with Vex programming for a little over a year and a half, a year of which has been on Linux.  I use the Piklab programming environment (which is a clone of MPLAB), and the C18 v. 2.40 compiler from Microchip running under Wine (for which Piklab has support).

I've now used both WPILib (the library behind EasyC, but without the graphics) and the default code (available on the downloads section of [www.vexrobotics.com](www.vexrobotics.com)), and they both work well.  You set up a project just like you would in MPLAB.

There is a template for the competition included in the default code when you download the library, and the WPILib structure lends itself very easily to the competition layout.  If it was the graphics you didn't like about EasyC, I'd suggest starting with WPILib, as the commands take care of a lot for you and you don't have to worry about registers so much (or pointers).  If you're experienced with code, you can use the default code library, which gives you complete access to the user processor's pins and registers, but is also set up in a well-organized way to facilitate easy coding (as long as you know what you're looking at, the files are fairly cluttered).

To load the files onto the Vex microcontroller, you can use a program called picloader, and to read output, you can use picreader (both included in a package called ifi_pictools).

As of now, there is no way to run RobotC under Linux so that it can communicate with the Vex microcontroller.  You can get RobotC to run under Wine without too many problems, but it will not recognize the serial ports or USB-to-serial adapter, so there's no way to get the code on the robot.

My prognosis:

Piklab IDE (in the standard repositories)
Microchip C18 version 2.40 compiler (search for it, it's in archives)
ifi_pictools (available on SourceForge)

WPILib API (available for free off of the Worchester Polytechnical Institutue website, search for "WPILib Download" on Google)
    OR
Vex default code (available on the Vex Robotics website under Support>Downloads>Default Code).


And read Vex Forums to get help on how to set up projects, write with those API's, etc.

Good luck!

---

### Post by networm on 2009-07-15
Fantastic. Thank you all...

---

