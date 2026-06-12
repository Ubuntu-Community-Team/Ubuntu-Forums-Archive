---
title: "What does this Part of the Perl install scripts mean?"
date: 2006-10-28
forum: Programming Talk
---

### Post by vitamin_c on 2006-10-28
The following chunk of perl script is in virtually all the installation scripts (eg. /user/share/setup-tools-backends/scripts)
There are no comments for it, explaining what its purpose is.

What is the general purpose for it? It looks like it appends .in to to .pl files only under certain circumstances...why would this ever be done?


What is this code for?
Thanks

#############

$SCRIPTSDIR = "/usr/share/setup-tool-backends/scripts";
print /^@scriptsdir[@]/;
if ($SCRIPTSDIR =~ /^@scriptsdir[@]/)
{
    $SCRIPTSDIR = ".";
    $DOTIN = ".in";
}

require "$SCRIPTSDIR/general.pl$DOTIN";
require "$SCRIPTSDIR/file.pl$DOTIN";
require "$SCRIPTSDIR/xml.pl$DOTIN";

---

