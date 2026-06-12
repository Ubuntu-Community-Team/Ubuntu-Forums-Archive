---
title: "Batch file rename"
date: 2007-01-12
forum: Programming Talk
---

### Post by dca on 2007-01-12
Long story short:  okay, way back when I burned a bunch of music CDs (CDA, not MP3) from an Windows PC that was about ready to fail.  Now I went to import them via sound juicer into my new file server and all the names (file names, title, album, etc) come out looking like gibberish or in some foreign language.  What I need is a CLI script that can batch rename all files in a particular directory from the foreignlanguage.mp3 to something easy like Track*** where the asterisk would indicate 001 through whatever.  Thanks...

---

### Post by mvaniersel on 2007-01-12
Here is a solution in perl:

```
#!/usr/bin/perl

use warnings;
use strict;

my $i = 0;
for my $file (glob ("*.mp3"))
{
	rename $file, "Track$i.mp3";
	$i++;
}
```

It will rename *.mp3 in the current dir to TrackNNN.mp3, where NNN starts at 1 and goes up from there. It doesn't check for duplicate filenames, so be careful with that.

Run it in the same way as any shell script. Save to a text file, chmod +x script and then ./script to run it.

---

### Post by ghostdog74 on 2007-01-12
I did this long time ago, in Python.

```

#!/usr/bin/python
import os,sys,re,glob,string
special = """~!@#$%^&*()_+|}{[]":;\'?><,./"""  ##define special characters
submachine = re.compile(r"[^A-Za-z0-9]").sub  ##substitute special characters if found
              
def dorename(files, patold ,patnew,  listflag):
    '''Function to do sequence substitution
        Input:  files => A list of globbed files to be processed.
                patold => The pattern in the file to be substituted
                patnew => The new pattern to replace the old
                listflag => 1 : Do a listing only
                            0 : Do substitution, and renaming of files
    '''   
    for thefile in files:	
        sequence = ''.join([c for c in patnew if c not in special]) ## get the correct sequence, excluding special chars
        if not sequence.isdigit(): ##check if its considered a digit
            print "%s is not a number sequence" %(patnew)
            sys.exit(1)       
        lengthsub = len(sequence)  ##get the length of the sequence, eg 00001 
        searched = re.search( r"(.*)" + sequence + "(.*)" , patnew) ## find any patterns in front and back of sequence, eg .0001#
        front = searched.group(1) ##going to join them back later for pattern change.
        back = searched.group(2)        
        ind = string.find(thefile,patold)        
        if ind != -1:            
            newname = thefile.replace(patold,str(patnew)) 
            patnew = int(submachine("",patnew)) + 1        ## do the counting of sequence
            patnew = string.zfill(str(patnew),lengthsub) ## fill up with 0's, eg if 11, and len 5, fill until 00011
            patnew = front + str(patnew) + back   ## concate the front and back characters, if any.     
            if listflag == 0:
                os.rename(thefile,newname)
                print "%s changed to %s " %( thefile, newname)
            elif listflag == 1:
                print "%s changed to %s " %( thefile,newname)
               
   
if __name__ == '__main__':
	files = glob.glob("*.mp3")
	print files
	dorename(files, "foreign" ,"001",  1)


```

However, I don't know whether it will work on the foreign language that you mentioned.

---

### Post by dca on 2007-01-15
Great, thanks for the replies...

---

