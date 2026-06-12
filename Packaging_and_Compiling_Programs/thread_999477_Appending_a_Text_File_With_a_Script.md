---
title: "Appending a Text File With a Script"
date: 2008-12-01
forum: Packaging and Compiling Programs
---

### Post by TheForkOfJustice on 2008-12-01
I need some help making scripts for a DEB file.

I plan to install a custom dictionary for OpenOffice via it's own DEB package and need to know how to do some things in Bash script for the preinst/postinst/prerm/postrm:

- How to check if a symlink exists and delete it if it is present (and likewise restore it if the package is uninstalled.

- How to append (to just add a line of text) to the end of a text file.

- How to insert a line of text at a certain line of a text file (displacing all other lines of text).

- How to replace a line of text in a text file (without displacing other lines of text)

Also, if someone can tell me of a better way to install a OOo dictionary via DEB package I'd like to hear it :)

---

### Post by lensman3 on 2008-12-11
> **TheForkOfJustice said:**
> I need some help making scripts for a DEB file.

I plan to install a custom dictionary for OpenOffice via it's own DEB package and need to know how to do some things in Bash script for the preinst/postinst/prerm/postrm:

- How to check if a symlink exists and delete it if it is present (and likewise restore it if the package is uninstalled.

from the bash man page:
     -h file
              True if file exists and is a symbolic link.
The restore is trickier.  You will have to write an uninstall script that replaces it later.  Just echo the "ln -s file1 file2" command to the restore script.

if [ -f "file_to_test" ]; then
    do_something ${EXPAND}
fi


- How to append (to just add a line of text) to the end of a text file.

echo "This is a line of text" >>file_to_append to 
The trick is the ">>" which is standard output append.  The first Unix had it and Bill Gates borrowed it for DOS.

- How to insert a line of text at a certain line of a text file (displacing all other lines of text). 

You will have to use the "ed" command and probably "here" documents.  The "here" document will have the "ed" commands to insert a line and then write the command out.  "awk" probably can do it too.

- How to replace a line of text in a text file (without displacing other lines of text)

Using "ed", do something like:

21,21s/old line pattern/new line pattern/

Also, if someone can tell me of a better way to install a OOo dictionary via DEB package I'd like to hear it :)


You might take a look at the .configure scripts that need to be run before you install and compile a system.  There are a lot of shell scripts in there that might give you a hint.

I would stick to /bin/sh as the script engine.  Don't use bash, csh or another shell.  The behavior of the sh-shell if a "standard" (pretty much) and the behavior will be the same over a very wide range of machines and versions.  (This could start a flame war)!!!

---

