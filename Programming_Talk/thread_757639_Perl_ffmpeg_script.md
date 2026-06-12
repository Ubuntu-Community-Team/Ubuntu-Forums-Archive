---
title: "Perl ffmpeg script"
date: 2008-04-17
forum: Programming Talk
---

### Post by theluddite on 2008-04-17
I'm trying to write a simple perl script that'll execute the following ffmpeg command on an .avi file:

ffmpeg -i 00001.avi -r 25 -target vcd 00001.avi.mpg

Here's what I wrote:

#!/usr/bin/perl
#framerate
use warnings;
use strict;
my $i=<>;
open FFMPEG, "ffmpeg -i $i -r 25 -target vcd $i.mpg" or die "Can't open ffmpeg: $!";

I keep getting:

Name "main::FFMPEG" used only once: possible typo at /bin/framerate line 6.
Can't open ffmpeg: No such file or directory at /bin/framerate line 6, <> line 1.

I'm new to programming so I'm probably missing something obvious.  Any suggestions?

---

### Post by ghostdog74 on 2008-04-17
how are you calling the script?[ Other info of interest you can look into]("http://search.cpan.org/~allenday/FFmpeg-6036/FFmpeg.pm").
Also look at these 
# perldoc -q external
# perldoc -f system
# perldoc -f exec
#

---

### Post by slavik on 2008-04-17
> **theluddite said:**
> I'm trying to write a simple perl script that'll execute the following ffmpeg command on an .avi file:

ffmpeg -i 00001.avi -r 25 -target vcd 00001.avi.mpg

Here's what I wrote:

#!/usr/bin/perl
#framerate
use warnings;
use strict;
my $i=<>;
open FFMPEG, "ffmpeg -i $i -r 25 -target vcd $i.mpg" or die "Can't open ffmpeg: $!";

I keep getting:

Name "main::FFMPEG" used only once: possible typo at /bin/framerate line 6.
Can't open ffmpeg: No such file or directory at /bin/framerate line 6, <> line 1.

I'm new to programming so I'm probably missing something obvious.  Any suggestions?

I think what you want to do is the following:
```
for (glob("*.avi)) {
  `ffmpeg -i "$i" -r 25 -target vcd "$i".mpg`;
}
```

---

### Post by grifter13 on 2008-04-17
This is what I do:

my $returncode;
$returncode =  system("ffmpeg blah blah");   # This will return ffmpeg's return code and your script continues.

or

exec("ffmpeg blah blah");  #This will not return from ffmpeg, your script is done.

I hope this helps.

Grift

---

### Post by theluddite on 2008-04-27
Thanks Slavik.  I used this script:

> #!/usr/bin/perl
#framerate
use warnings;
use strict;
for (glob("*.avi")) {
  `ffmpeg -i "$_" -r 25 -target vcd "$_".mpg`;
}

My camera takes .avi movies at 10 fps and I need them to be 25 fps.  I saved the script in /bin/ and made it executable using the command "sudo chmod +x framerate".  Now, I can just go to the directory in which I saved all the films that need to be converted, type the name of the script (framerate), and all of the .avi files in that directory are converted to .mpg with the new framerate of 25 fps.  Ubuntu is awesome!

---

