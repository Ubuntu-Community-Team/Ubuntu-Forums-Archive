---
title: "Wish to improve clumsy IF/ELSE/IF/ELSE... comments please"
date: 2010-02-27
forum: Programming Talk
---

### Post by Krupski on 2010-02-27
Hi all,

I wrote a small program to change plain text files into HTML format (by, for example, replacing new lines with <br> and spaces with "&nbsp;", etc...)

There is a piece of the code that has nested IF/ELSE decisions and something in the back of my mind tells me that it's clumsy and that there's a better way to do it.

Any suggestions will be greatly appreciated!

Thanks!

-- Roger

Here's the code: (concern in red)

```

///////////////////////////////////////////////////////////////////////////
//
// "htmlfilt.c" - PLAIN TEXT to HTML filter
// Copyright 2010 Roger A. Krupski <krupski@acsu.buffalo.edu>
//
// This program is free software: you can redistribute it and/or modify
// it under the terms of the GNU General Public License as published by
// the Free Software Foundation, either version 3 of the License, or
// (at your option) any later version.
//
// This program is distributed in the hope that it will be useful,
// but WITHOUT ANY WARRANTY; without even the implied warranty of
// MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
// GNU General Public License for more details.
//
// You should have received a copy of the GNU General Public License
// along with this program.  If not, see <http://www.gnu.org/licenses/>.
//
///////////////////////////////////////////////////////////////////////////
//
// To use: htmlfilt < stdin > stdout
//
// This program simply reads the source line by line and transforms
// spaces into non-breaking spaces (&nbsp;) and also replaces tabs
// with the proper number of non-breaking spaces to preserve any
// formatting the file has. It also replaces special characters
// such as "<" and ">", etc...
//
// To include an optional HTML header and/or footer, generate the
// following files: program_name.header.html and program_name.footer.html
// where program_name is htmlfilt (unless you changed it!).
//
// These two optional files are copied to stdout verbatim, so they must
// contain valid HTML code to work properly.
//
///////////////////////////////////////////////////////////////////////////
//
// A typical htmlfilt-header.html might contain the following text:
//
//		<p style=
//		font-family:courier new,courier,monospace;
//		font-weight:normal;
//		background-color:#ffffff;
//		text-align:left;
//		color:#000000;
//		font-size:1.0em;
//		>
//
// and of course the footer would contain:
//
// </p>
//
///////////////////////////////////////////////////////////////////////////


#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>

#undef BUFSIZ
#define BUFSIZ 2048

// file pointer, destination
int readln(FILE*, char*);

// destination, source, delimiter
int bname(char*, const char*, const char*);


int main (int argc, char *argv[])
{
	FILE *infile;

	const char *header = "%s-header.html";
	const char *footer = "%s-footer.html";

	char buffer[BUFSIZ];
	char fname[BUFSIZ];

	int len, c, x, curpos;
	int tabsiz = 8;

	if(argc != 1) {
		bname(buffer, argv[0], "\\/");
		fprintf(stderr, "usage: %s < stdin > stdout\n", buffer);
		return 1;
	}

	bname(buffer, argv[0], "\\/");
	sprintf(fname, header, buffer);

	infile = fopen(fname, "r");
	if(infile != NULL) {
		while(!feof(infile)) {
			readln(infile, buffer);
			fprintf(stdout, "%s\n", buffer);
		}
	fclose(infile);
	}

	while(!feof(stdin))
	{
		curpos = 0;

		len = readln(stdin, buffer);

		for(c = 0; c < len; c++)
		{
[B][COLOR="Red"]			if(buffer[c] == 0x09) {
				for(x = 0; x < tabsiz-(curpos % tabsiz); x++)
				{
					fprintf(stdout, "&nbsp;");
				}
				curpos +=x;
			} else

			if(buffer[c] == ' ')  { fprintf(stdout, "&nbsp;"); curpos++; } else
			if(buffer[c] == '<')  { fprintf(stdout, "&lt;");   curpos++; } else
			if(buffer[c] == '>')  { fprintf(stdout, "&gt;");   curpos++; } else
			if(buffer[c] == '&')  { fprintf(stdout, "&amp;");  curpos++; } else
			if(buffer[c] == 0x22) { fprintf(stdout, "&quot;"); curpos++; } else
			if(buffer[c] == 0x27) { fprintf(stdout, "&apos;"); curpos++; } else
			{ fprintf(stdout, "%c", buffer[c]); curpos++; }[/COLOR][/B]
		}
		fprintf(stdout, "<br>\n");
	}

	bname(buffer, argv[0], "\\/");
	sprintf(fname, footer, buffer);

	infile = fopen(fname, "r");
	if(infile != NULL) {
		while(!feof(infile)) {
			readln(infile, buffer);
			fprintf(stdout, "%s\n", buffer);
		}
	fclose(infile);
	}

	return 0;
}


// file pointer, destination
int readln(FILE *fp, char *str)
{
	char buf[BUFSIZ];
	int len;

	buf[0] = 0;

	fgets(buf, BUFSIZ, fp);

	len = strlen(buf);

	while (len >= 0) {
		if (buf[len] <= 0x20) { buf[len] = 0; len--; }
		else { break; }
	}

	len++;

	buf[len] = 0;

	strncpy(str, buf, BUFSIZ);

	return strlen(str);
}


// destination, source, delimiter
int bname(char* str, const char* p0, const char* delim)
{
    char tmp[BUFSIZ];
	char* p1;
	char* p2;

	strcpy(tmp, p0);

	p2 = strtok(tmp, delim);

	while(p2 != NULL) {
		p1 = p2;
		p2 = strtok(NULL, delim);
	}
	strncpy(str, p1, BUFSIZ);

	return strlen(str);
}

```


Thank you!!

---

### Post by lisati on 2010-02-27
Perhaps a "switch"/"case" block of code?

---

### Post by Krupski on 2010-02-27
> **lisati said:**
> Perhaps a "switch"/"case" block of code?

Hmmm... that does sound cleaner than what I did... and it is indeed a "case" type of thing. I'll try it.

Thanks!

-- Roger

(edit to add); Here is the result... it works.

```

for(c = 0; c < len; c++)
{
	switch(buffer[c])
	{
		case '\t':
			for(x = 0; x < tabsiz-(curpos % tabsiz); x++)
			{
				fprintf(stdout, "&nbsp;");
			}
			curpos +=x;
		break;

		case ' ':
			fprintf(stdout, "&nbsp;");
			curpos++;
		break;

		case '<':
			fprintf(stdout, "&lt;");
			curpos++;
		break;

		case '>':
			fprintf(stdout, "&gt;");
			curpos++;
		break;

		case '&':
			fprintf(stdout, "&amp;");
			curpos++;
		break;

		case '\"':
			fprintf(stdout, "&quot;");
			curpos++;
		break;

		case '\'':
			fprintf(stdout, "&apos;");
			curpos++;
		break;

		default:
			fprintf(stdout, "%c", buffer[c]);
			curpos++;
		break;
	}
}

```

Thanks again!

---

### Post by Hellkeepa on 2010-02-27
HELLo!

I'd create a "htmlescape" function, to get a much cleaner code. Regular expressions might also be of help here, though you'd want to test it first.

Happy codin'!

---

### Post by Krupski on 2010-02-27
> **Hellkeepa said:**
> HELLo!

I'd create a "htmlescape" function, to get a much cleaner code. Regular expressions might also be of help here, though you'd want to test it first.

Happy codin'!

I don't quite understand what you mean. Could you elaborate please?

---

### Post by Hellkeepa on 2010-02-28
HELLo!

Simple: You move all of the code that does the actual escaping of the characters to ISO-entities into a function of its own, make this take the string as an input, and return the HTML-safe string.
Quite like PHP's "[htmlspecialchars ()](http://no.php.net/htmlspecialchars)" function.

As for the point about RegExps; They may be faster, if implemented correctly, and they would most certainly give you a lot less code. That's why I recommend benchmarking them against a switch-case solution, to see which of them performs the best (and then I'm not just talking about speed).

Happy codin'!

---

### Post by Krupski on 2010-02-28
> **Hellkeepa said:**
> HELLo!

Simple: You move all of the code that does the actual escaping of the characters to ISO-entities into a function of its own, make this take the string as an input, and return the HTML-safe string.
Quite like PHP's "[htmlspecialchars ()](http://no.php.net/htmlspecialchars)" function.

As for the point about RegExps; They may be faster, if implemented correctly, and they would most certainly give you a lot less code. That's why I recommend benchmarking them against a switch-case solution, to see which of them performs the best (and then I'm not just talking about speed).

Happy codin'!

Ah I see. Sadly, I am unfamiliar with PHP programming, and complex regular expressions ALWAYS give me a headache! :)

With that said, in a round-about way, you gave me yet another idea. I made a 256 entry constant char array containing either simple ASCII characters or their special HTML replacements (i.e. "&nbsp;" for "space").

I then simply index into the array with the current character and print the array element.

It still uses SWITCH / CASE, but only to handle the special case of tabs which have to be dynamically counted and printed (i.e. can't be static in the array).

It seems to work quite well... and it's certainly fast enough (the whole point of what I'm doing is to generate a dynamic HTML page of my server's system info so that I can look at it without doing an SSH console session and logging in).

Here is the newest version of the program using the 256 element array technique (note I do not handle any UNICODE).

The part that accesses the array is highlighted in red.

Please comment on what I did and tell me if anything can be improved.

Thank you once again!

```

///////////////////////////////////////////////////////////////////////////
//
// "htmlfilt.c" - PLAIN TEXT to HTML filter (28 FEB 2010)
// Copyright 2010 Roger A. Krupski <krupski@acsu.buffalo.edu>
//
// This program is free software: you can redistribute it and/or modify
// it under the terms of the GNU General Public License as published by
// the Free Software Foundation, either version 3 of the License, or
// (at your option) any later version.
//
// This program is distributed in the hope that it will be useful,
// but WITHOUT ANY WARRANTY; without even the implied warranty of
// MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
// GNU General Public License for more details.
//
// You should have received a copy of the GNU General Public License
// along with this program.  If not, see <http://www.gnu.org/licenses/>.
//
///////////////////////////////////////////////////////////////////////////
//
// To use: htmlfilt < stdin > stdout
//
// This program simply reads the source line by line and transforms
// spaces into non-breaking spaces (&nbsp;) and also replaces tabs
// with the proper number of non-breaking spaces to preserve any
// formatting the file has. It also replaces special characters
// such as "<" and ">", etc...
//
// To include an OPTIONAL HTML header and/or footer, generate the
// following files: program_name-header.html and program_name-footer.html
// where program_name is "htmlfilt" (unless you changed it!).
//
// These two OPTIONAL files are copied to stdout verbatim, so they must
// contain valid HTML code to work properly.
//
///////////////////////////////////////////////////////////////////////////
//
// A typical htmlfilt-header.html might contain the following text:
//
//	<html>
//	<head>
//	<style type="text/css">
//	a {
//		font-family:courier new,courier,monospace;
//		font-weight:bold;
//		background-color:#cf0000;
//		text-align:left;
//		color:#ffffff;
//		font-size:1.5em;
//	}
//	</style>
//	</head>
//	<body>
//	<a>
//
// =============================================
// ...then STDIN would be inserted here...
// =============================================
//
// ...and of course the footer would contain:
//
//	</a>
//	</body>
//	</html>
//
///////////////////////////////////////////////////////////////////////////


#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>

#undef BUFSIZ
#define BUFSIZ 2048


// file pointer, destination
int readln(FILE *fp, char *str)
{
	char buf[BUFSIZ];
	int len;

	buf[0] = 0;

	fgets(buf, BUFSIZ, fp);

	len = strlen(buf);

	while (len >= 0) {
		if (buf[len] <= 0x20) { buf[len] = 0; len--; }
		else { break; }
	}

	len++;

	buf[len] = 0;

	strncpy(str, buf, BUFSIZ);

	return strlen(str);
}


// destination, source, delimiter
int bname(char* str, const char* p0, const char* delim)
{
    char tmp[BUFSIZ];
	char* p1;
	char* p2;

	strcpy(tmp, p0);

	p2 = strtok(tmp, delim);

	while(p2 != NULL) {
		p1 = p2;
		p2 = strtok(NULL, delim);
	}

	strncpy(str, p1, BUFSIZ);

	return strlen(str);
}


int main (int argc, char *argv[])
{

	// ASCII to HTML translation table
	const char *codes[256]={

	// "sub-ASCII" will print nothing

	"", "", "", "", "", "", "", "", // 0...7
	"", "", "", "", "", "", "", "", // 8...15
	"", "", "", "", "", "", "", "", // 16...23
	"", "", "", "", "", "", "", "", // 24...31

	// normal ASCII characters

	"&nbsp;", "!", "&quot;", "#", "$", "%", "&amp;", "'",
	"(", ")", "*", "+", ",", "-", ".", "/",

	"0", "1", "2", "3", "4", "5", "6", "7", "8", "9",

	":", ";", "&lt;", "=", "&gt;", "?", "@",

	"A", "B", "C", "D", "E", "F", "G", "H", "I", "J", "K", "L", "M",
	"N", "O", "P", "Q", "R", "S", "T", "U", "V", "W", "X", "Y", "Z",

	"[", "\\", "]", "&circum;", "_", "`",

	"a", "b", "c", "d", "e", "f", "g", "h", "i", "j", "k", "l", "m",
	"n", "o", "p", "q", "r", "s", "t", "u", "v", "w", "x", "y", "z",

	"{", "|", "}", "&tilde;", "",

	// high bit characters

	"€", "&#65533;", "&sbquo;", "ƒ", "&dbquo;", "…", "&dagger;", "&Dagger;",
	"ˆ", "&permil;", "Š", "&lsaquo;", "Œ", "&#65533;", "Ž", "&#65533;",
	"&#65533;", "&lsquo;", "&rsquo;", "&ldquo;", "&rdquo;", "•", "&ndash;", "&mdash;",
	"&tilde", "&trade;", "š", "&rsaquo;", "œ", "&#65533;", "ž", "&Yuml;",
	"&nbsp;", "&iexcl;", "&cent;", "&pound;", "&curren;", "&yen;", "&brvbar;", "&sect;",
	"&uml;", "&copy;", "&ordf;", "&laquo;", "&not;", "*", "&reg;", "&macr;",
	"&deg;", "&plusmn;", "&sup2;", "&sup3;", "´", "&micro;", "&para;", "&middot;",
	"&cedil;", "&sup1;", "&ordm;", "&raquo;", "&frac14;", "&frac12;", "&frac34;", "¿",
	"&Agrave;", "&Aacute;", "&Acirc;", "&Atilde;", "&Auml;", "&Aring;", "&AElig;", "&Ccedil;",
	"&Egrave;", "&Eacute;", "&Ecirc;", "&Euml;", "&Igrave;", "&Iacute;", "&Icirc;", "&Iuml;",
	"&ETH;", "&Ntilde;", "&Ograve;", "&Oacute;", "&Ocirc;", "&Otilde;", "&Ouml;", "&times;",
	"&Oslash;", "&Ugrave;", "&Uacute;", "&Ucirc;", "&Uuml;", "&Yacute;", "&THORN;", "&szlig;",
	"&agrave;", "&aacute;", "&acirc;", "&atilde;", "&auml;", "&aring;", "&aelig;", "&ccedil;",
	"&egrave;", "&eacute;", "&ecirc;", "&euml;", "&igrave;", "&iacute;", "&icirc;", "&iuml;",
	"&eth;", "&ntilde;", "&ograve;", "&oacute;", "&ocirc;", "&otilde;", "&ouml;", "&divide;",
	"&oslash;", "&ugrave;", "&uacute;", "&ucirc;", "&uuml;", "&yacute;", "&thorn;", "&yuml;"
	};

	FILE *infile;

	const char *header = "%s-header.html";
	const char *footer = "%s-footer.html";

	char buffer[BUFSIZ];
	char fname[BUFSIZ];

	int len, c, x, curpos;
	int tabsiz = 8;

	// very simple help
	if(argc != 1) {
		bname(buffer, argv[0], "\\/");
		fprintf(stderr, "usage: %s < stdin > stdout\n", buffer);
		return 1;
	}

	// generate header filename
	bname(buffer, argv[0], "\\/");
	sprintf(fname, header, buffer);

	// open and copy optional header file, insert HTML comments
	infile = fopen(fname, "r");
	if(infile != NULL) {
		fprintf(stdout, "<!-- begin %s -->\n", fname);

		while(!feof(infile)) {
			readln(infile, buffer);
			fprintf(stdout, "%s\n", buffer);
		}

		fclose(infile);
		fprintf(stdout, "<!-- end %s -->\n", fname);
	}
	else
	{
		fprintf(stdout, "<!-- %s not found -->\n", fname);
	}

	// read, translate and copy text to HTML
	fprintf(stdout, "\n<!-- begin translated text -->\n");
	while(1) // run until eof breaks
	{
		curpos = 0;

		len = readln(stdin, buffer);

		if(feof(stdin)) {break ;}

[b][color=red]		for(c = 0; c < len; c++)
		{
			switch(buffer[c])
			{
				case '\t': // tab is a special case
					for(x = 0; x < tabsiz-(curpos % tabsiz); x++)
					{
						fprintf(stdout, "&nbsp;");
					}
					curpos +=x;
				break;

				default: // anything else - translate and print
					fprintf(stdout, "%s", codes[buffer[c]]);
					curpos++;
				break;
			}
		}[/COLOR][/B]
		fprintf(stdout, "<br>\n"); // html newline
	}
	fprintf(stdout, "<!-- end translated text -->\n\n");

	// generate footer filename
	bname(buffer, argv[0], "\\/");
	sprintf(fname, footer, buffer);

	// open and copy optional footer file, insert HTML comments
	infile = fopen(fname, "r");
	if(infile != NULL) {
		fprintf(stdout, "<!-- begin %s -->\n", fname);

		while(!feof(infile)) {
			readln(infile, buffer);
			fprintf(stdout, "%s\n", buffer);
		}

		fclose(infile);
		fprintf(stdout, "<!-- end %s -->\n", fname);
	}
	else
	{
		fprintf(stdout, "<!-- %s not found -->\n", fname);
	}

	return 0;
}

```



And just in case any characters got messed up by the CODE[] window, here's a copy of it in ZIP format: [**[COLOR="Blue"]_ZIPFILE_[/COLOR]**]("http://home.roadrunner.com/~krupski/htmlfilt.zip")


-- Roger

---

