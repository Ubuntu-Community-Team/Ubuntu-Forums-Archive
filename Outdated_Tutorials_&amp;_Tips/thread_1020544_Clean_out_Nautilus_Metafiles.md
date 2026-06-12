---
title: "Clean out Nautilus Metafiles"
date: 2008-12-24
forum: Outdated Tutorials &amp; Tips
---

### Post by ibuclaw on 2008-12-24
OK, I was looking around the ~/.nautilus directories yesterday (poking round at what configuration files are in place, as I was updating an old script of mine, and went on a hunt to find easier ways to obtain information on things, such as mounted hard drives, etc, etc...)

All of a sudden I came across this folder:
```
~/.nautilus/metafiles/
```
To which there are a few xml files of certain directories.

So I investigated them, and found a rather large file...
```
$ wc -l file:%2F%2F%2Fhome%2Fiain%2FDesktop.xml
2 file:%2F%2F%2Fhome%2Fiain%2FDesktop.xml

```
OK, two lines... seems tiny, but:
```
$ wc -c file:%2F%2F%2Fhome%2Fiain%2FDesktop.xml
9937 file:%2F%2F%2Fhome%2Fiain%2FDesktop.xml

```
But for two lines... It has nearly ten thousand characters in it...

So I checked it out, and it turns out that nautilus keeps records of every file that was ever on your desktop.

I don't know about some, but I'd rather not have data of files that don't exist anymore stored in configuration files, so I wrote a script to clean the crud (removes details of files that no longer exist):
```

#!/usr/bin/perl
# clean.pl
use warnings;
use strict;

use XML::Parser;
use File::stat;

my($path) = "$ENV{HOME}/.nautilus/metafiles/";
my($xmlout) = '';
&listdir;

# Emulate ls
sub listdir {
    local *XML;
    if(!opendir(XML, $path)) {
        print 'Error: cannot access '.$path."\n";
        exit 1;
    }
    for (readdir(XML)) { # Match all files for home folder.
        if(/^file:%2F%2F%2Fhome/) { # Delete xml files for hidden files/folders, and subdirectories of the top home folders.
            if(/(%2F\..*)|(home%2F\w+%2F\w+(%2F.*)+)$/) {
                unlink($path.$_);
                next;
            } # Skip if file checks out and is not for the Desktop.xml config.
            elsif(!/Desktop\.xml$/) {
                next;
            } # Clean out the Desktop.xml config.
            $xmlout = "<?xml version=\"1.0\"?>\n";
            &parse($path.$_);
            open(FILE, '>', $path.$_);
            print FILE $xmlout;
            close FILE;
            next;
        } # Else delete if filename is not /^x-nautilus/
        elsif(!/^x-nautilus/) {
            unlink($path.$_);
            next;
        }
    }
}

# Parse the input file.
sub parse {
    my($file) = @_;
    
    my($parser) = XML::Parser->new();
    $parser->setHandlers(
        Start => \&beginTag,
        End => \&endTag
    );

    $parser->parsefile($file);
}

# Start Element
sub beginTag {
    my($parseinst, $element, %attrs) = @_;
    if($element eq 'directory') {
        $xmlout .= "<$element>";
    } # If the file no longer exists in the Desktop folder, don't add it in to the new file buffer.
    elsif($element eq 'file') {
        my($name) = $attrs{name};
        $name=~s/%([0-9A-Fa-f]{2})/chr(hex($1))/eg;
        if( -e "$ENV{HOME}/Desktop/$name") {
            $xmlout .= "<$element name=\"$attrs{name}\" ";
            $xmlout .= "timestamp=\"$attrs{timestamp}\" ";
            $xmlout .= "icon_position=\"$attrs{icon_position}\"/>";
        }
    }
}

# End Element
sub endTag {
    my($parseinst, $element) = @_;
    $xmlout .= "</$element>" if($element eq 'directory');
}

```

And the results:
```

$ wc -l %2F%2F%2Fhome%2Fiain%2FDesktop.xml
2 file:%2F%2F%2Fhome%2Fiain%2FDesktop.xml


$ wc -c file:%2F%2F%2Fhome%2Fiain%2FDesktop.xml
412 file:%2F%2F%2Fhome%2Fiain%2FDesktop.xml

```
Better?

Regards
Iain

---

### Post by Martje_001 on 2008-12-24
Some people keep surprising me with the things they find out.. ;)

Thank you for the script, I guess I'm gonna run it every once in a while. Is there a reason why Nautilus keeps track of deleted files btw?

---

### Post by ibuclaw on 2008-12-24
To be honest, I really don't know

If you were to look at the file contents of the directory:
```

file:%2F%2F%2Fhome%2Fiain%2FDesktop.xml
file:%2F%2F%2Fhome%2Fiain%2FDownloads.xml
file:%2F%2F%2Fhome%2Fiain%2FMusic.xml
file:%2F%2F%2Fhome%2Fiain%2FPictures.xml
file:%2F%2F%2Fhome%2Fiain.xml
file:%2F%2F%2Fmedia%2Faudio.xml
x-nautilus-desktop:%2F%2F%2F.xml

```
They all appear to keep the data of the contents of the directory as seen through the nautilus browser
(ie: type in **x-nautilus-desktop:///** in your browser textbar).

And more curiously, the following directories seem to keep uptodate with what their linked folder currently looks like (remove a file, and it gets removed from it's corresponding directory metafile):
```

file:///home/iain/Downloads
file:///home/iain/Music
file:///home/iain/Pictures
file:///home/iain
file:///media/audio
x-nautilus-desktop:///

```
That is all except the Desktop metafile.

Maybe I've stumbled upon a bug that lets the file bloat itself, who knows?

I'm on Hardy, by the way...

[EDIT]
This is all what I've found about the matter:
[http://markmail.org/message/jtv3i4j7ofnxlmic#query:.nautilus%2Fmetafiles%20Desktop.xml+page:1+mid:4d4kamp5jyk5poz2+state:results](http://markmail.org/message/jtv3i4j7ofnxlmic#query:.nautilus%2Fmetafiles%20Desktop.xml+page:1+mid:4d4kamp5jyk5poz2+state:results)

[EDIT2]
OK, after some more playing round, it may seem that I don't get this behaviour (at least, not through adding and removing files while in the gnome session). So my hope is that running the script once should be enough to remove anything that may have got left behind by accident, and the rest will work as expected from now on...


Regards
Iain

---

### Post by diskotek on 2008-12-28
how can we run this perl script? should we copy it to a file namely xxxx.sh and hit it?

---

### Post by Martje_001 on 2008-12-28
.pl if I'm not mistaking. Make it executable and 'hit it' ;).

---

### Post by pterosky on 2010-02-10
A simpler solution is to just delete all files in the .nautilus/metafiles folder, except the Desktop settings files. Search for "desktop" to find them. Set the permissions for the owner of the metafiles folder to "Access files". Now you only have the Desktop settings files in the folder, and there wont be generated anymore, since there is no access to the folder any longer.

---

