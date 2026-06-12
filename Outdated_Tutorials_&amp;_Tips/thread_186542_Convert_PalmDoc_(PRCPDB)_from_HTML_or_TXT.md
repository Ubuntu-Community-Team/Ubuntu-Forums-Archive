---
title: "Convert PalmDoc (PRC/PDB) from HTML or TXT"
date: 2006-06-02
forum: Outdated Tutorials &amp; Tips
---

### Post by barney_1 on 2006-06-02
I'm trying to completely rid myself from using XP and one of the last few apps that I'm reliant upon was AportisDoc Converter.  I use it to convert just about any type of file to a readable format for my Palm Pilot, usually .PDB.

After much searching I have found this work-around that seems to do an excellent job.  It is a very old program called MakeDocW.exe which I learned about at this webpage:
[http://www.handebooks.com/howto/doc.html]("http://www.handebooks.com/howto/doc.html")

The program was written by a person named Mark Pierce ([webpage]("http://www.pierce.de/makedocw.html")) and can be downloaded directly from [this link]("http://www.pierce.de/makedocw.zip").

1. Install Wine:
```
sudo apt-get install wine
```

2. Launch downloaded file using wine:
```
wine MakeDocW.exe
```

I get an error about palm desktop not being properly installed but just click ok and you should be good to go.  I found that once I tweaked the settings I was able to ensure punctuation was being properly encoded (this is why I'm not using txt2pdbdoc) and html tags as well as linefeeds are removed.  It's not a slick solution, but it is a work-around.

Please, if you have a better solution.... or can code a Linux clone of AportisDoc Converter, post it here!

---

### Post by Havoc on 2006-06-02
OpenOffice can save to AportisDoc (pdb) out of the box... ](*,) 

No need for Wine! :cool:

---

### Post by barney_1 on 2006-06-02
I had trouble with OpenOffice incorrectly converting puncutation.  I ended up with extended characters every time an apostraphe was used (among other punctuation problems).

---

### Post by wastrel on 2006-06-06
You might want to look at pyrite publisher.  It's flexible palmdoc creator that reads text, HTML and other formats.  I've used it for years to transfer text to my handheld.  I don't have a lot of experience converting material from HTML, so YMMV.

apt-get install pyrite-publisher
pyrpub file.txt
pilot-xfer -i file.pdb

done!

Here's a little perl script I cooked up to clean up punctuation from windows-sourced text files (pyrpub may do this automatically now, it's been a while since I've used windows-sourced text files...):

-------------------
#!/usr/bin/perl -w

# cleanquotes.pl  get rid of *** microsoft smartquotes & other non ASCII chars
#
# usage:  cat my-textfile.txt | cleanquotes.pl > cleaned-file.txt

$prevblank = "no";

while (<>)
{
        s/\x85/.../g;           # ellipsis (?)
        s/\x91/'/g;             # left apostrophe
        s/\x92/'/g;             # right apostrophe
        s/\x93/"/g;             # left quote
        s/\x94/"/g;             # right quote
        s/\x96/--/g;            # N-dash
        s/\x97/--/g;            # M-dash

        # other fun things

        s/ \. \. \./\.\.\./g;   # . . . ellipsis
        s/^ +//;                # whitespace at the beginning of a line

        # collapse multiple blank lines into one blank line
        if ($_ =~ /^$/)
        {
                if ($prevblank eq "no")
                {
                        $prevblank = "yes";
                        print;
                }
        }
        else
        {
                $prevblank = "no";
        }

        if ($_ !~ /^$/) { print; }
}

---

### Post by jonboy99 on 2006-09-07
Where does the output file go?  Am running the program from my home/Desktop directory on a text file in the same dir, and it seems to run ok, but no output file.

:confused: 

[EDIT] doh, just noticed the autoinstall button - unchecked and works fine now.  :rolleyes: 

> **barney_1 said:**
> I'm trying to completely rid myself from using XP and one of the last few apps that I'm reliant upon was AportisDoc Converter.  I use it to convert just about any type of file to a readable format for my Palm Pilot, usually .PDB.

After much searching I have found this work-around that seems to do an excellent job.  It is a very old program called MakeDocW.exe which I learned about at this webpage:
[http://www.handebooks.com/howto/doc.html]("http://www.handebooks.com/howto/doc.html")

The program was written by a person named Mark Pierce ([webpage]("http://www.pierce.de/makedocw.html")) and can be downloaded directly from [this link]("http://www.pierce.de/makedocw.zip").

1. Install Wine:
```
sudo apt-get install wine
```

2. Launch downloaded file using wine:
```
wine MakeDocW.exe
```

I get an error about palm desktop not being properly installed but just click ok and you should be good to go.  I found that once I tweaked the settings I was able to ensure punctuation was being properly encoded (this is why I'm not using txt2pdbdoc) and html tags as well as linefeeds are removed.  It's not a slick solution, but it is a work-around.

Please, if you have a better solution.... or can code a Linux clone of AportisDoc Converter, post it here!

---

### Post by mclien on 2008-05-18
No luck so far:
Openoffice crashes, when saving  (debian etch repositories)
pyrite does it but without Umlaute (german: ä, ö ü ß...)

any hints?
EDIT:
yes, use encoded text (perhaps. So far I have " instead of ö and simmelar)
I try to find the correct encoding and post here..

OK this way:
Use save as (from OOo) encoded text, with filter type:
Western Europe iso 8859-15/EURO
and convert this with pyrite and everything is fine!

---

