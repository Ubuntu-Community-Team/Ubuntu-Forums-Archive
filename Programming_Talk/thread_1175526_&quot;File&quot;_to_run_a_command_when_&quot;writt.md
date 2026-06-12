---
title: "&quot;File&quot; to run a command when &quot;written&quot; to? symlink?"
date: 2009-06-01
forum: Programming Talk
---

### Post by _AndY on 2009-06-01
Is there any way I can have a "file" in a directory which, when written to, instead of writing to disk, causes a command to be executed with the data written passed to STDIN?

So like a symbolic link except to an executable I guess?

Just to clarify, if a script opens the file for writing, I want a predefined process to be executed which will then receive (via STDIN) whatever is written to the file.

Does anybody know if this is possible?
Thanks


EDIT:
I just read up on FIFOs, seem to act as named pipes. So I have a script reading from the FIFO which simply waits until something is written to it.

If anyone's interested:

Create the FIFO
```
mknod fifo_test p
```

Then run this to listen to writes
```
#!/usr/bin/perl

use strict;

my $fifo;
open($fifo, "+</home/andy/fifo_test") or die $!;

while (my $line = <$fifo>) {
	print "$line\n";
}

close $fifo;
exit(0);

```

The above will act as a normal read whenever something is written to the file.

```
echo test > fifo_test
```

---

### Post by lensman3 on 2009-06-01
I think this does "kinda" what you want->

mkfifo vid.fifo
mkfifo aud.fifo
tcextract -i aud.fifo -t vob -x ac3 -a $track > ofile.ac3 &
tcextract -i vid.fifo -t vob -x mpeg2 > ofile.m2v &
tccat -i $CDROM -T $title,-1 -L | tee aud.fifo vid.fifo > /dev/null &&


Two named pipes are created (mkfifo).  Then tcextract will read the two pipes (and do there stuff in background).. The tccat command reads the CDROM and writes the output (using tee) to the named pipes.  

A very clever way to get the audio and video from a DVD on one read pass.

---

