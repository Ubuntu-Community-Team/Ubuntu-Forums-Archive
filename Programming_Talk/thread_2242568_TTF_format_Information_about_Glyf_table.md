---
title: "TTF format: Information about Glyf table"
date: 2014-09-02
forum: Programming Talk
---

### Post by Dr._Valy_G._Rousse on 2014-09-02
Hello,

I'm trying to write a code that extracts the glyph data of a given character from a TTF file. But I have a problem with the 'glyf' table. The information that I found about it is somehow self-contradicting. More precisely here is what I found:

Glyph description

[TABLE]
[TR]
[TD]int16[/TD]
[TD]numberOfContours[/TD]
[TD]If the number of contours is positive or zero, it is a single glyph;
        If the number of contours less than zero, the glyph is compound[/TD]
[/TR]
[TR]
[TD]FWord[/TD]
[TD]xMin[/TD]
[TD="class: description"]Minimum x for coordinate data[/TD]
[/TR]
[TR]
[TD]FWord[/TD]
[TD]yMin[/TD]
[TD="class: description"]Minimum y for coordinate data[/TD]
[/TR]
[TR]
[TD]FWord[/TD]
[TD]xMax[/TD]
[TD="class: description"]Maximum x for coordinate data[/TD]
[/TR]
[TR]
[TD]FWord[/TD]
[TD]yMax[/TD]
[TD="class: description"]Maximum y for coordinate data[/TD]
[/TR]
[TR]
[TD="class: description, colspan: 3"][/TD]
[/TR]
[/TABLE]

Single glyph description

[TABLE]
[TR]
[TD]uint16[/TD]
[TD]endPtsOfContours[n][/TD]
[TD="class: description"]Array of last points of each contour; n is the number of contours; array entries are point indices[/TD]
[/TR]
[TR]
[TD]uint16[/TD]
[TD]instructionLength[/TD]
[TD="class: description"]Total number of bytes needed for instructions[/TD]
[/TR]
[TR]
[TD]uint8[/TD]
[TD]instructions[instructionLength][/TD]
[TD="class: description"]Array of instructions for this glyph[/TD]
[/TR]
[TR]
[TD]uint8[/TD]
[TD]flags[variable][/TD]
[TD="class: description"]Array of flags[/TD]
[/TR]
[TR]
[TD]uint8 or int16[/TD]
[TD]xCoordinates[][/TD]
[TD="class: description"]Array of x-coordinates; the first is relative to (0,0), others are relative to previous point[/TD]
[/TR]
[TR]
[TD]uint8 or int16[/TD]
[TD]yCoordinates[][/TD]
[TD="class: description"]Array of y-coordinates; the first is relative to (0,0), others are relative to previous point[/TD]
[/TR]
[/TABLE]

Flags description

[TABLE]
[TR]
[TD]On Curve[/TD]
[TD]0[/TD]
[TD]If set, the point is on the curve;
        Otherwise, it is off the curve.[/TD]
[/TR]
[TR]
[TD]x-Short Vector[/TD]
[TD]1[/TD]
[TD]If set, the corresponding x-coordinate is 1 byte long;
        Otherwise, the corresponding x-coordinate is 2 bytes long[/TD]
[/TR]
[TR]
[TD]y-Short Vector[/TD]
[TD]2[/TD]
[TD]If set, the corresponding y-coordinate is 1 byte long;
        Otherwise, the corresponding y-coordinate is 2 bytes long[/TD]
[/TR]
[TR]
[TD]Repeat[/TD]
[TD]3[/TD]
[TD="class: description"]If set, the next byte specifies the  number of additional times this set of flags is to be repeated. In this  way, the number of flags listed can be smaller than the number of points  in a character.[/TD]
[/TR]
[TR]
[TD]This x is same (Positive x-Short vector)[/TD]
[TD]4[/TD]
[TD]This flag has one of two meanings, depending on how the x-Short Vector flag is set.
        If the x-Short Vector bit is set, this bit describes the sign of  the value, with a value of 1 equalling positive and a zero value  negative.
        If the x-short Vector bit is not set, and this bit is set, then  the current x-coordinate is the same as the previous x-coordinate.
        If the x-short Vector bit is not set, and this bit is not set,  the current x-coordinate is a signed 16-bit delta vector. In this case,  the delta vector is the change in x[/TD]
[/TR]
[TR]
[TD]This y is same (Positive y-Short vector)[/TD]
[TD]5[/TD]
[TD]This flag has one of two meanings, depending on how the y-Short Vector flag is set.
        If the y-Short Vector bit is set, this bit describes the sign of  the value, with a value of 1 equalling positive and a zero value  negative.
        If the y-short Vector bit is not set, and this bit is set, then  the current y-coordinate is the same as the previous y-coordinate.
        If the y-short Vector bit is not set, and this bit is not set,  the current y-coordinate is a signed 16-bit delta vector. In this case,  the delta vector is the change in y[/TD]
[/TR]
[TR]
[TD]Reserved[/TD]
[TD]6 - 7[/TD]
[TD="class: description"]Set to zero[/TD]
[/TR]
[/TABLE]

It is said that the x and y coordinates are RELATIVE to the previous coordinates (except the first ones that are relative to (0,0)). No problem with that. This means that the x and y coordinates are delta vectors.

My problem is with the bits 4 (and 5) of the flags, where they say that "If the x-short Vector bit is not set, and this bit is not set,  the current x-coordinate is a signed 16-bit delta vector. In this case,  the delta vector is the change in x". In other words, they say that the x-coordinate is a delta vector when both bits 1 and 4 are not set. From this I conclude that the x-coordinate IS NOT a delta vector when either bit 1 or 4 is set, or both, that is to say are absolute vectors... which contradicts what they say before "coordinates are RELATIVE to the previous coordinates".

Can someone explain what I'm missing?

---

### Post by Dr._Valy_G._Rousse on 2014-09-03
Alright, I found the solution: The coordinates are always delta vectors relative to the previous point (or relative to (0,0) for the very first point). It is the description of bits 4 and 5 that was confusing. The sentence "... is a signed 16-bit delta vector..." doesn't mean that we are in a special case where we have a delta vector (we actually always have a delta vector), it simply means that it must be read as signed 16-bit value. This information is redundant since we already know that since the bit 1 is unset.

In other words:

bit 1,   bit 4
0,0          Signed 16-bit value
0,1          Same as previous value
1,0          Negative 8-bit value
1,1          Positive 8-bit value

And once again, these values are ALWAYS delta vectors, that is to say they are DISPLACEMENT, relative to the previous point (or to (0,0) for the first point).

---

