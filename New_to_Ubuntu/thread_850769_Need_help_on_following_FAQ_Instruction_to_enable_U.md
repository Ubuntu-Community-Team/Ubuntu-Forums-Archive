---
title: "Need help on following FAQ Instruction to enable UTF-8 fonts in Amarok!"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by mashimaro on 2008-07-05
Hi, I've been trying to follow this faq:
[http://amarok.kde.org/wiki/FAQ](http://amarok.kde.org/wiki/FAQ)

to enable UTF-8 fonts in Amarok for the mp3 tags.
Here is the step:
>  Amarok is not displaying my utf-8 id3v2 tags properly!

    * This is because most applications put utf8 data into id3v2 tags but do not specify the encoding as unicode. This perl script will fix that. 


#!/usr/bin/perl
die "File $ARGV[0] doesn't exist" unless -f $ARGV[0];
use MP3::Mplib;
my $mp3 = MP3::Mplib->new($ARGV[0]);
my $v2tag = $mp3->get_v2tag;
print "Error writing tags of $ARGV[0]\n" unless $mp3->set_v2tag($v2tag,&UTF8);

    * Note: This script requires the perl module MP3::Mplib which can be installed by issuing this command 

perl -MCPAN -e 'install MP3::Mplib'


note, I already have installed MP3:Mplib by following that step. Thing is though, it doesn't say what to do with the perl script it gives. Does anyone know? Putting it into a tar bzip file and adding it to the script manager doesn't work just fyi. Enabling permissions and executing it in my music folder doesn't work either (./thescript.pl * and other variations of it).

Thanks!
mashi

---

### Post by phaid on 2008-07-06
It looks like the script is expecting a filename.  Copy one of your mp3s someplace else, then run the script against the copied file and see  if that works.  I wasn't sure what the scripts name was from the post, think it might have been ./thescript.pl   -  if that was it try something like

/path/to/script/thescript.pl your-new.mp3  from the directory that the new copied file is in

where /path/to/script would be the location you save that script file to and your-new.mp3 is the name of the file you want to run it on


You may want to take a quick look at other packages that can take care of utf8.  I believe that easytag can do it - not sure if it can handle all your mp3's at once, does a folder at a time, or just a single file.

Amarok really isn't an ID3 manager, so the script probably isn't going to be the easiest thing to use in the long run.  That is why I mentioned the easytag program.  If easytag doesn't do what you want, look around for another ID3 manager program that does and you might be happier in the long run.

---

