---
title: "24-bit colour and memory woes"
date: 2008-12-04
forum: Programming Talk
---

### Post by Thesuperchang on 2008-12-04
Hi, I'm trying to make a 24-bit colour palette for a library designed to act as a simplified X11 front end. The problem is that my method making such a palette requires a large amount of memory to be consumed. Unfortunately this is not feasible given the system I am working on. I'd imagine that there is a way to achieve 24-bit colour with minimal memory usage. Would anyone be able to enlighten me please.

Thanks in advance,
-C. Anderson.

[PHP]#include <stdio.h>
#include <stdlib.h>
#include <X11/Xlib.h> 

#define DEPTH 256

typedef struct{
	GC     gc;
	XColor colour;
} _ColourSplurge;

_ColourSplurge ***buildColourSplurge(_ColourSplurge ***colours, Window w, Display *d, Colormap colormap);

_ColourSplurge ***buildColourSplurge(_ColourSplurge ***colours, Window w, Display *d, Colormap colormap) {
	int i, j, k;
	char ****range;

	/*** Setup colour values ***********/
	char dummy[DEPTH][3] = {"00", "01", "02", "03", "04", "05", "06", "07", "08", "09", "0A", "0B", "0C", "0D", "0E", "0F",
			        "10", "11", "12", "13", "14", "15", "16", "17", "18", "19", "1A", "1B", "1C", "1D", "1E", "1F",
			        "20", "21", "22", "23", "24", "25", "26", "27", "28", "29", "2A", "2B", "2C", "2D", "2E", "2F",
			        "30", "31", "32", "33", "34", "35", "36", "37", "38", "39", "3A", "3B", "3C", "3D", "3E", "3F",
			        "40", "41", "42", "43", "44", "45", "46", "47", "48", "49", "4A", "4B", "4C", "4D", "4E", "4F",
			        "50", "51", "52", "53", "54", "55", "56", "57", "58", "59", "5A", "5B", "5C", "5D", "5E", "5F",
			        "60", "61", "62", "63", "64", "65", "66", "67", "68", "69", "6A", "6B", "6C", "6D", "6E", "6F",
			        "70", "71", "72", "73", "74", "75", "76", "77", "78", "79", "7A", "7B", "7C", "7D", "7E", "7F",
			        "80", "81", "82", "83", "84", "85", "86", "87", "88", "89", "8A", "8B", "8C", "8D", "8E", "8F",
			        "90", "91", "92", "93", "94", "95", "96", "97", "98", "99", "9A", "9B", "9C", "9D", "9E", "9F",
			        "A0", "A1", "A2", "A3", "A4", "A5", "A6", "A7", "A8", "A9", "AA", "AB", "AC", "AD", "AE", "AF",
			        "B0", "B1", "B2", "B3", "B4", "B5", "B6", "B7", "B8", "B9", "BA", "BB", "BC", "BD", "BE", "BF",
			        "C0", "C1", "C2", "C3", "C4", "C5", "C6", "C7", "C8", "C9", "CA", "CB", "CC", "CD", "CE", "CF",
			        "D0", "D1", "D2", "D3", "D4", "D5", "D6", "D7", "D8", "D9", "DA", "DB", "DC", "DD", "DE", "DF",
			        "E0", "E1", "E2", "E3", "E4", "E5", "E6", "E7", "E8", "E9", "EA", "EB", "EC", "ED", "EE", "EF",
			        "F0", "F1", "F2", "F3", "F4", "F5", "F6", "F7", "F8", "F9", "FA", "FB", "FC", "FD", "FE", "FF"
                               };

	range = (char ****)malloc(DEPTH * sizeof(char ****));
	for(i = 0; i < DEPTH; i++) {
		range[i] = (char ***)malloc(DEPTH * sizeof(char ***));
		for(j = 0; j < DEPTH; j++) {
			range[i][j] = (char **)malloc(DEPTH * sizeof(char **));
			for(k = 0; k < DEPTH; k++) {
				range[i][j][k] = (char *)malloc(DEPTH * sizeof(char *));			
			}
		}
	}

	for(i = 0; i < DEPTH; i++) {
		for(j = 0; j < DEPTH; j++) {
			for(k = 0; k < DEPTH; k++) {
				range[i][j][k][0] = '#';

				range[i][j][k][1] = dummy[k&0xFF][0];
				range[i][j][k][2] = dummy[k&0xFF][1];

				range[i][j][k][3] = dummy[j&0xFF][0];
				range[i][j][k][4] = dummy[j&0xFF][1];

				range[i][j][k][5] = dummy[i&0xFF][0];
				range[i][j][k][6] = dummy[i&0xFF][1];

				range[i][j][k][7] = dummy[0][2];
			}
		}
	}
	/***********************************/

	/*** Setup palette *****************/
	colours = (_ColourSplurge ***)malloc(DEPTH * sizeof(_ColourSplurge ***));
	for(i = 0; i < DEPTH; i++) {
		colours[i] = (_ColourSplurge **)malloc(DEPTH * sizeof(_ColourSplurge **));
		for(j = 0; j < DEPTH; j++) {
			colours[i][j] = (_ColourSplurge *)malloc(DEPTH * sizeof(_ColourSplurge *));
			for(k = 0; k < DEPTH; k++) {
				colours[i][j][k].gc = XCreateGC(d, w, 0, 0);
				XParseColor(d, colormap, range[i][j][k], &(colours[i][j][k].colour));
				XAllocColor(d, colormap, &(colours[i][j][k].colour));
				XSetForeground(d, colours[i][j][k].gc, colours[i][j][k].colour.pixel);
			}
		}
	}
	/***********************************/

	/*** Release redundant memory ******/
	for(i = 0; i < DEPTH; i++) {
		for(j = 0; j < DEPTH; j++) {
			for(k = 0; k < DEPTH; k++) {
				free(range[i][j][k]);			
			}
			free(range[i][j]);
		}
		free(range[i]);
	}
	free(range);
	/***********************************/

	return colours;
}[/PHP]

---

### Post by jpkotta on 2008-12-05
Do you have to build that table before hand?  Why not just have a temporary variable that is the piece of the table you're interested in at a particular iteration, and use that in place of the table.  In other words, if there is not much speed gain in using the pre-built table, but it uses a ton of memory, dynamically generate whatever data in the table exactly when you need it.  You could replace your table with a function that given an index, spits out the value that would have been in the table.

---

### Post by stroyan on 2008-12-05
X11 24 bit colors don't work like that.  24 bit visuals are always
represented as either TrueColor or DirectColor classes.  TrueColor visuals
have a static mapping of index values to colors.  They cannot modify
the colormap entries at all.  DirectColor visuals can set index to
color mappings, but not in the same way that a PseudoColor visual can.

The mapping from a 24 bit color index to a color is done by first breaking
the 24 bit value down to into the Red, Green, and Blue parts.  The 8 bits
for each channel are masked and shifted.  The color lookup for each channel
is independent of the other channel's values.

You can compute a color index for a particular red, green, and blue
intensity using the data returned from XGetVisualInfo.  Then set the
foreground of a single GC to use that index before using it.  Don't
try to create a different GC for every color you may use.

You can find examples of X11 color computation in the code for
open source programs like ImageMagick.  The code is rather complicated
because there can be much variability between different X servers and
a lot of those details are exposed by the X11 API.

---

