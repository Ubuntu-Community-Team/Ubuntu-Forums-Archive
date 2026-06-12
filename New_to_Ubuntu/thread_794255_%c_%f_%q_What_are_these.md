---
title: "%c %f %q What are these?"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by jessika-kaos on 2008-05-14
%c" %i %m %q %f usually appearing after menu entries and program launchers. What do they do/mean?

---

### Post by plucky on 2008-05-14
Found these on the net
Meaning

%f
	A single file name, even if multiple files are selected. The system reading the desktop entry should recognize that the program in question cannot handle multiple file arguments, and it should should probably spawn and execute multiple copies of a program for each selected file if the program is not able to handle additional file arguments. If files are not on the local file system (i.e. are on HTTP or FTP locations), the files will be copied to the local file system and %f will be expanded to point at the temporary file. Used for programs that do not understand the URL syntax.

%F   -A list of files. Use for apps that can open several local files at once.

%u   -A single URL.

%U   -A list of URLs.

%d  -Directory containing the file that would be passed in a %f field.

%D   -List of directories containing the files that would be passed in to a %F field.

%n   -A single filename (without path).

%N   -A list of filenames (without paths).

%i    -The Icon field of the desktop entry expanded as two parameters, first --icon and then the contents of the Icon field. Should not expand as any parameters if the Icon field is empty or missing.

%c   -The translated Name field associated with the desktop entry.

%k   -The location of the desktop file as either a URI (if for example gotten from the vfolder system) or a local filename or empty if no location is known.

%v   -The name of the Device entry in the desktop file.

:)

---

### Post by jessika-kaos on 2008-05-14
Thanks! I wasn't sure what to search for on Google as it strips out the % symbol.

---

