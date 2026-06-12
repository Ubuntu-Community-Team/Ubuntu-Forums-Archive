---
title: "AACPlus V2 Encoding using KAudioCreator"
date: 2006-06-27
forum: Outdated Tutorials &amp; Tips
---

### Post by AdrianVeidt on 2006-06-27
Destined to replace Mp3, AACPlus V2 allows for extremely good audio quality at extremely low bitrates (and correspondingly low file sizes).

Currently, there is no way to rip CDs using AACPlus V2 in Linux. Well, if you do what I tell you, when I tell you... ehh, never mind.

Anyway, here's how I did it; you will need wine installed and configured. Basically, it's just:

$ sudo apt-get install wine
$ wineprefixcreate

That's that. Now, make sure you have KAudioCreator, which is the standard KDE CD Ripper (I love the fact that the word "Ripper" has a capital "R"...) which is, *sigh*

$ sudo apt-get install kaudiocreator

Now, a dude I don't know has made up a nice encoder, which you can download here:
[http://home.cwru.edu/~bes7/db_EnhAACPlus_650.zip]("http://home.cwru.edu/~bes7/db_EnhAACPlus_650.zip")

Unpack the thing using the GUI "Extract ==>Here". This will create  a little folder with a few files inside. Take a look, just for the Hell of it.
:-k
Had your fun? Good, let's move on.
Now, open KAudioCreator. Click Settings==>Configure KAudioCreator. Select the 'Encoder' tab. Click 'Add'. Call it AACPlus or whatever you want. Now, in the 'Command' Window, you're going to type a command very similar to this:

wine path/to/enhAacPlusEnc.exe %f %o 48000 s

48000 is the bitrate I have arbitrarily chosen. "s" means stereo. There is a list of possible settings in the Options.txt file. I believe 24000 s would be sufficient if drive space is a very real concern. If not, 64000 s is also available. 8)
Now, this particular encoder names the files .3gp, which produces a confused reaction on your system. One way to de-confuse the system is open Konq, click Settings==>File Associations==>audio==>mp4 (or aac). Add *.3gp to the Filename Patterns section. Another solution is to rename the files .m4a, or Hell, any other media pattern you can damn well think of. The easiest thing to do is the former.
Want to rename the files anyway? run the following Perl script from the directory the files are in:

#!/usr/bin/perl
# Author: Brandon Snider
# Purpose: exercise shell script features
# Date: 20 January 2006


print "script starting\n";

$count = 0;
foreach my $file (glob "*.3gp") {
	my $newfile = $file;
	$newfile =~ s/\.3gp$/.m4a/;
	if (-e $newfile) {
		warn "can't rename $file to $newfile: $newfile exists\n";
	} elsif (rename $file, $newfile) {
	$count++;
	## success, do nothing
	} else {
	warn "rename $file to $newfile failed: $!\n";
	}
}
print "$count files changed.\n";
print "script ending\n"

Well, that's it. Now go off and rip your Pat Boone sings Judy Garland CDs.

PS. UUUHHHH... You do realize that your portable mp3 player doesn't have a clue what these files are and won't anytime soon right? Good. Apparently even the ubiquitous iPod can't play them.

---

### Post by hugmenot on 2006-06-27
This was released as freeware recently:
[http://www.nero.com/nerodigital/eng/Nero_Digital_Audio.html](http://www.nero.com/nerodigital/eng/Nero_Digital_Audio.html)

---

