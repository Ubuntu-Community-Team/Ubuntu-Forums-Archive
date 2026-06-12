---
title: "HOWTO: Really extract here with a nautilus script"
date: 2005-04-21
forum: Outdated Tutorials &amp; Tips
---

### Post by ow50 on 2005-04-21
Want to extract arhives here (/. not /archivename_FILES)?
Want to extract multiple archives at once?
Using File-Roller?

Copy-paste the following to a text editor:
```
#!/usr/bin/env python

import os
import urllib
import urlparse

uris = os.environ['NAUTILUS_SCRIPT_SELECTED_URIS'].split('\n')[:-1]

for uri in uris:
	unquoted_uri = urllib.unquote(uri)
	path = urlparse.urlsplit(unquoted_uri)[2]
	dirname = os.path.dirname(path)
	command = 'file-roller -e "%s" "%s"' % (dirname, path)
	os.system(command)
```

Save the file to ~/.gnome2/nautilus-scripts/.
Give it execute permissions.
Extract your archives by right-click > Scripts > whatever you named it.

**Note**: When extracting multiple archives, you'll see a separate progress dialog for each archive and pressing "stop" in that dialog will only stop the extraction of that one archive. Extraction will **replace** any files you already have **wihout asking**.


In case it doesn't work, the **same thing** in Perl:

You'll need the Perl URI module:
```
sudo apt-get install liburi-perl
```

```
#!/usr/bin/perl

# Extracts all selected archives to current directory using File-Roller.

use strict;
use warnings;

use File::Spec;
use URI::Escape;
use URI::Split qw/uri_split/;

my @uris = split('\n', $ENV{NAUTILUS_SCRIPT_SELECTED_URIS});

foreach (@uris) {
	my $unesc_uri = uri_unescape($_);
	my ($scheme, $auth, $path, $query, $frag) = uri_split($unesc_uri);
	my ($volname, $dirname, $filename) = File::Spec->splitpath($path);
	system("file-roller -e '$dirname' '$path'");
}
```


Edit 2005-04-24:
Added python version.

---

### Post by tanari on 2005-04-21
thank you! 
I don't like new way of extracting files in hoary :(. I always copy file from archivename_FILES to ./, it's very boring.
But now good way came back :)

---

### Post by dafrabbit on 2005-04-22
Excellent! This has been bothering me for a while!

Just a note for anyone who comes across this same problem, when I tried to run the script, I found out that I did not have the URI module for perl. The script complained about a missing "Escape.pm". Googled that and found out how to install the module:

sudo perl -MCPAN -e shell      (Needs sudo or else it will get a permissions error when installing the module)

It will now ask you to do manual or auto configuration. Type "no" so that it will auto-configure. (This worked fine for me) and let it do its thing. You will now be presented with a prompt looking like:

cpan>

Type:
install URI::Escape

To exit out of the shell, type "quit".

---

### Post by ow50 on 2005-04-22
[QUOTE=dafrabbit]when I tried to run the script, I found out that I did not have the URI module for perl.[/QUOTE]

Sorry about not mentioning that. I thought I had about a standard install and that all hoary users would have the URI module.

An easier and more elegant way to get the URI module would be:
```
sudo apt-get install liburi-perl
```

---

### Post by XDevHald on 2005-04-22
WOW!!! this is so much easier than I expected, great work and VERY useful tool!!

---

### Post by dafrabbit on 2005-04-22
[QUOTE=ow50]Sorry about not mentioning that. I thought I had about a standard install and that all hoary users would have the URI module.

An easier and more elegant way to get the URI module would be:
```
sudo apt-get install liburi-perl
```[/QUOTE]
 Ack yea I like your way better! :)

---

### Post by ed_agamemnon on 2005-04-23
should be in the guide :)

---

### Post by jiyuu0 on 2005-04-24
i've tried the instructions above including installing the liburi-perl package... but seems nothing happen when i right click to extract

will put into the guide once i get this right :)

---

### Post by seven on 2005-04-24
wow, thanks!!!
I've been looking this for a long time!
I hate the _FILES thing.
woho


work great, but the scripts menu shows for every type of file.
can I replace the "Extract here" command with the script?

---

### Post by jiyuu0 on 2005-04-24
[QUOTE=seven]wow, thanks!!!
I've been looking this for a long time!
I hate the _FILES thing.
woho[/QUOTE]

did you modify anything to make it work?
nothing seems to happen with the instructions for me :(

---

### Post by seven on 2005-04-24
[QUOTE=jiyuu0]did you modify anything to make it work?
nothing seems to happen with the instructions for me :([/QUOTE]

Did you gave the script an execute permissions?
otherwise it won't work

---

### Post by jiyuu0 on 2005-04-24
1) sudo apt-get install liburi-perl

2) vi ~/.gnome2/nautilus-scripts/Extract\ files\ here

use strict;
use warnings;

use File::Spec;
use URI::Escape;
use URI::Split qw/uri_split/;

my @uris = split('\n', $ENV{NAUTILUS_SCRIPT_SELECTED_URIS});

foreach (@uris) {
        my $unesc_uri = uri_unescape($_);
        my ($scheme, $auth, $path, $query, $frag) = uri_split($unesc_uri);
        my ($volname, $dirname, $filename) = File::Spec->splitpath($path);
        system("file-roller -e '$dirname' '$path'");
}

3) chmod +x ~/.gnome2/nautilus-scripts/Extract\ files\ here

4) Then i try right click on ubuntu5.04.tar -> Scripts -> Extra files here

... Nothing happened

---

### Post by ow50 on 2005-04-24
[QUOTE=jiyuu0]... Nothing happened[/QUOTE]

Do you have all the needed modules?
```
locate File/Spec.pm
locate URI/Escape.pm
locate URI/Split.pm
```
All should return something.

Look at the output in ~/.xsession-errors. There should be some error message.

If that doesn't help, I can add some debugging output to the  script.

---

### Post by ow50 on 2005-04-24
Here's a quickly done debugging version:
```
#!/usr/bin/perl

# Extracts all selected archives to current directory using File-Roller.

use strict;
use warnings;

use File::Spec;
use URI::Escape;
use URI::Split qw/uri_split/;

open(FILE, '>:utf8', '/tmp/extract.txt') or die
	print "Unable to open file: '/tmp/extract.txt' for writing.";

my @uris = split('\n', $ENV{NAUTILUS_SCRIPT_SELECTED_URIS});

print FILE "NAUTILUS_SCRIPT_SELECTED_URIS:\n";
foreach(@uris) { print FILE "$_\n" }

foreach (@uris) {
	print FILE "\nuri: $_\n";
	my $unesc_uri = uri_unescape($_);
	print FILE "unescaped uri: $unesc_uri\n";
	my ($scheme, $auth, $path, $query, $frag) = uri_split($unesc_uri);
	print FILE "filepath: $path\n";
	my ($volname, $dirname, $filename) = File::Spec->splitpath($path);
	print FILE "directory: $dirname\n";
	my $output = `file-roller -e '$dirname' '$path'"`;
	print FILE "file-roller output: $output\n";
	system("file-roller -e '$dirname' '$path'");
}

close(FILE);
system("gedit /tmp/extract.txt");


```

It'll open the debugging output in Gedit after script has been run.

---

### Post by ow50 on 2005-04-24
To make things easier, the python version should work without having to install any additional modules
```
#!/usr/bin/env python

import os
import urllib
import urlparse

uris = os.environ['NAUTILUS_SCRIPT_SELECTED_URIS'].split('\n')[:-1]

for uri in uris:
	unquoted_uri = urllib.unquote(uri)
	path = urlparse.urlsplit(unquoted_uri)[2]
	dirname = os.path.dirname(path)
	command = 'file-roller -e "%s" "%s"' % (dirname, path)
	os.system(command)

```

---

### Post by jiyuu0 on 2005-04-24
[QUOTE=ow50]Do you have all the needed modules?
```
locate File/Spec.pm
locate URI/Escape.pm
locate URI/Split.pm
```
All should return something.

Look at the output in ~/.xsession-errors. There should be some error message.

If that doesn't help, I can add some debugging output to the  script.[/QUOTE]

seems like the 2nd and 3rd aren't showing anything

chua@jiyuu0:~$ locate File/Spec.pm
/usr/share/perl/5.8.4/File/Spec.pm
chua@jiyuu0:~$ locate URI/Escape.pm
chua@jiyuu0:~$ locate URI/Split.pm
chua@jiyuu0:~$

---

### Post by ow50 on 2005-04-24
Did you update your locate database after installing liburi-perl? According to Synaptic, liburi-perl clearly contains '/usr/share/perl5/URI/Escape.pm' and '/usr/share/perl5/URI/Split.pm'.

What about the python script?

---

### Post by jiyuu0 on 2005-04-24
[QUOTE=ow50]Did you update your locate database after installing liburi-perl? According to Synaptic, liburi-perl clearly contains '/usr/share/perl5/URI/Escape.pm' and '/usr/share/perl5/URI/Split.pm'.

What about the python script?[/QUOTE]

my fault... yes... able to find

the python script with debuggin... nothing happened... gedit didn't popup...
maybe i should try reinstall, just in case it's only my prob here

---

### Post by Quest-Master on 2005-04-24
Haha, yes.

I have been waiting for this for so long. <3

---

### Post by Potemkin on 2005-04-25
[QUOTE=tanari]thank you! 
I don't like new way of extracting files in hoary :(. I always copy file from archivename_FILES to ./, it's very boring.
But now good way came back :)[/QUOTE]
I actually prefer the way Ubuntu has set it up. Many archives are badly packaged, in that the files are not contained in a special folder of their own. This means that when you extract them they all spill out into your existing folder and get mixed up with files from other packages. This makes finding and using such files and if necessary deleting them afterwards extremely difficult. Extracting them all into a special archivename_FILES folder keeps things neat, tidy and safe. If you need to, you can just 'cut files' on the archive folder, navigate back up, 'paste files' into your default directory, then delete the archivename_FILES directory. No need for any scripts.

---

### Post by ow50 on 2005-04-25
[QUOTE=Potemkin]I actually prefer the way Ubuntu has set it up. Many archives are badly packaged, in that the files are not contained in a special folder of their own. This means that when you extract them they all spill out into your existing folder and get mixed up with files from other packages. This makes finding and using such files and if necessary deleting them afterwards extremely difficult. Extracting them all into a special archivename_FILES folder keeps things neat, tidy and safe.[/QUOTE]

I guess this depends on how you use your archives. I usually download them to a download directory, extract there and then move. If the archive is badly packed, it won't matter since there's never anything important at my download directory, if there's anything at all.

[QUOTE=Potemkin]If you need to, you can just 'cut files' on the archive folder, navigate back up, 'paste files' into your default directory, then delete the archivename_FILES directory. No need for any scripts.[/QUOTE]

It's a whole lot easier with a script. Let's say you have 5 archives and want to extract them all. With the default file-roller behaviour you'd have to extract 5 times and do that navigate-cut-navigate-paste-delete 5 times. With this script you just select all archives and extract them.

---

### Post by Potemkin on 2005-04-25
[QUOTE=ow50]I guess this depends on how you use your archives. I usually download them to a download directory, extract there and then move. If the archive is badly packed, it won't matter since there's never anything important at my download directory, if there's anything at all.



It's a whole lot easier with a script. Let's say you have 5 archives and want to extract them all. With the default file-roller behaviour you'd have to extract 5 times and do that navigate-cut-navigate-paste-delete 5 times. With this script you just select all archives and extract them.[/QUOTE]That's a good point, but if you're extracting several archives simultaneously and the archives are badly packaged (and many are) all the files will spill out into the same directory. If you're extracting only one archive, then why not just use my method? If you're extracting several simultaneously, then you have the problem I described. It's precisely to avoid such a problem that Ubuntu have set things up the way they have. It's one of those things, like disabling root, which Ubuntu does which seems strange and inconvenient at first, but which actually makes a lot of sense if you think about it. I was initially annoyed about the archivename_FILES thing as well when I first encountered it, but I'm now a convert.

---

