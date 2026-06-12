---
title: "Reading data from the mouse"
date: 2007-10-04
forum: Programming Talk
---

### Post by [h2o] on 2007-10-04
I have a robotproject in which we will use an optical mouse to track the movements of the robot.
The robot will be running Linux and have the mouse connected through a USB-port.

I looked at using gpm, but I am not sure using events like gpm does is the way to go.

What I would like to be able to do is to read from the mouse every few milli/microseconds and get the movements to calculate position.

---

### Post by [h2o] on 2007-10-04
Found a way myself.

It all comes down to reading from "/dev/input/mice" and parsing the data.
The PS/2 protocol specifies that 3 bytes are emitted at each "event" (mouse moved or buttons pressed).
First byte is a bitmap of controlbits. Second and third is the movement since last read in x and y axis respectively.

If you don't want to have blocking reads you need to use open() from unistd.h instead of fopen() and then use fcntl() from fcntlh.h to set the file descriptor to be non blocking.

---

